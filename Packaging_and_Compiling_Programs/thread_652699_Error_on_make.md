---
title: "Error on make"
date: 2007-12-29
forum: Packaging and Compiling Programs
---

### Post by SudoKing on 2007-12-29
I used make in a directory, which yielded this output:

make[1]: Entering directory `/home/dude/Desktop/dancer-4.16/src'
make CSPECIAL="-g -DRCS -DDEBUG" ../dancer
make[2]: Entering directory `/home/dude/Desktop/dancer-4.16/src'
gcc -DHAVE_CONFIG_H -g -DRCS -DDEBUG   -c -o dancer.o dancer.c
gcc -DHAVE_CONFIG_H -g -DRCS -DDEBUG   -c -o function.o function.c
gcc -DHAVE_CONFIG_H -g -DRCS -DDEBUG   -c -o server.o server.c
gcc -DHAVE_CONFIG_H -g -DRCS -DDEBUG   -c -o command.o command.c
command.c:4313:1: error: pasting "(" and "topitem" does not give a valid preprocessing token
command.c:4313:1: error: pasting "topitem" and "*" does not give a valid preprocessing token
command.c:4313:1: error: pasting "(" and "topitem" does not give a valid preprocessing token
command.c:4313:1: error: pasting "topitem" and ")" does not give a valid preprocessing token
command.c:4340:1: error: pasting "(" and "topitem" does not give a valid preprocessing token
command.c:4340:1: error: pasting "topitem" and "*" does not give a valid preprocessing token
command.c:4340:1: error: pasting "(" and "topitem" does not give a valid preprocessing token
command.c:4340:1: error: pasting "topitem" and ")" does not give a valid preprocessing token
command.c:4374:1: error: pasting "(" and "topitem" does not give a valid preprocessing token
command.c:4374:1: error: pasting "topitem" and "*" does not give a valid preprocessing token
command.c:4374:1: error: pasting "(" and "topitem" does not give a valid preprocessing token
command.c:4374:1: error: pasting "topitem" and ")" does not give a valid preprocessing token
make[2]: *** [command.o] Error 1
make[2]: Leaving directory `/home/dude/Desktop/dancer-4.16/src'
make[1]: *** [debug] Error 2
make[1]: Leaving directory `/home/dude/Desktop/dancer-4.16/src'
make: *** [all] Error 2



And I didn't understand the error, so I ran *checkinstall* to compile a .deb package, and received no errors, yet of course it said it **FAILED.**  How would I go about correcting this problem?

---

