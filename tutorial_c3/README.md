# c3c version

```bash
$ c3c --version
C3 Compiler Version:       0.6.6 (Pre-release, Jan 14 2025 22:07:24)
Installed directory:       /Users/gy/utilities/c3_compiler/
Backends:                  LLVM
LLVM version:              17.0.6
LLVM default target:       arm64-apple-darwin23.4.0
```

# 260105) **[C3 프로그래밍 언어](<https://news.hada.io/topic?id=25553&utm_source=discord&utm_medium=bot&utm_campaign=1480>)**
- **C 언어의 문법과 의미를 계승하면서 안전성과 사용성을 강화한 진화형 언어**로, 기존 C 개발자에게 익숙한 환경을 유지  
- **완전한 C ABI 호환성**을 제공해 C/C++ 프로젝트에 바로 통합 가능하며, vkQuake 일부 코드가 C3로 변환되어 c3c 컴파일러로 빌드된 사례 존재  
- **모듈 시스템**, **연산자 오버로딩**…

# 260415) They Released C 3.0! | Avey Dev
- https://youtu.be/nlt52b5kH7Y?si=UZVvmKekgGtVeab8

- https://gitlab.com/avey.dev/c3

```c3
module helloworld;
import std::io;
import std::io::file;

extern fn int printf(char *format, ...);

fn void? readFile(String filename) {
  File? file = file::open(filename, "r")!;

  defer (void)file.close();

  while (try line = io::treadline(&file)) {
    io::printn(line);
  }
}

//fn int main() {}
fn int main(String[] args) {
  printf("Hello %s\n", "world!");

  //foreach (arg : args) {
  //  io::printn(arg);
  //}

    //io::printn("Hello, World!");

  // struct { *type, ulong len}
  //if (args.len < 2) {
  //  io::printn("Usage: HelloWorld <filename>");
  //  return -1;
  //}
  //io::printfn("filename: %s", args[1]);
  //String filename = args[1];

  io::print("enter the file name: ");
  String? filename = io::treadline();
  if (catch error = filename) {
    io::printfn("error invalid input: %s", error);
    return -1;
  }
  if (catch error = readFile(filename)) {
    io::printfn("error opening file: %s", error);
  }
  
    return 0;
}
```
