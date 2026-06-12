---
title: "Misc CMake Questions"
date: 2009-05-25
forum: Programming Talk
---

### Post by kerryhall on 2009-05-25
I have a few more questions about CMake, if anyone would be so kind! :)

1. How do you execute post build commands, such as copying a bin somewhere?

2. How do you detect libraries?

---

### Post by mart_k on 2009-05-25
> **kerryhall said:**
> I have a few more questions about CMake, if anyone would be so kind! :)

1. How do you execute post build commands, such as copying a bin somewhere?You can use the [install](http://www.cmake.org/cmake/help/cmake2.6docs.html#command:install) command to install targets after they are compiled. To add custom commands during "make install", you can add [install(code )](http://www.cmake.org/cmake/help/cmake2.6docs.html#command:install) commands.

> **kerryhall said:**
> 2. How do you detect libraries?It depends a bit on the library. Some libraries can be found with build-in commands. You can use the [find_package](http://www.cmake.org/cmake/help/cmake2.6docs.html#command:find_package) command for those. In some cases, you have to write the method to find a package yourself.

For libraries, there also is the [find_library](http://www.cmake.org/cmake/help/cmake2.6docs.html#command:find_library) command.

---

