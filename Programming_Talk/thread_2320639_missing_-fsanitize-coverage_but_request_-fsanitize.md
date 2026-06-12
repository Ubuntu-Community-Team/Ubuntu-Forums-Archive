---
title: "missing -fsanitize-coverage but request -fsanitize-coverage"
date: 2016-04-16
forum: Programming Talk
---

### Post by zerop2 on 2016-04-16
when follow toy example
[http://llvm.org/docs/LibFuzzer.html](http://llvm.org/docs/LibFuzzer.html)

martin@ubuntu:~/fuzzer$ clang++ -fsanitize=address test_fuzzer.cc libFuzzer.amartin@ubuntu:~/fuzzer$ ./a.out
INFO: Seed: 3709720807
ERROR: __sanitizer_set_death_callback is not defined. Exiting.
Did you use -fsanitize-coverage=... to build your code?
martin@ubuntu:~/fuzzer$ clang++ -fsanitize=address -fsanitize-coverage=edge test_fuzzer.cc libFuzzer.a
clang: error: unknown argument: '-fsanitize-coverage=edge'
martin@ubuntu:~/fuzzer$ clang++ --help | grep fsan
  -fsanitize-blacklist=<value>
  -fsanitize-memory-track-origins=<value>
  -fsanitize-memory-track-origins
  -fsanitize=<check>      Enable runtime instrumentation for bug detection: address (memory errors) | thread (race detection) | undefined (miscellaneous undefined behavior)

---

