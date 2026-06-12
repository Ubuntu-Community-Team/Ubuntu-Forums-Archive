---
title: "A few gui questions"
date: 2009-02-25
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-02-25
for the following questions, answers my be for C, C++, or python.  i would like the answers to be cross platform if possible but i realize i will probably need conio or ncurses

1) how do i output colored text?

2) how would i do a gui like top or nethack?

---

### Post by geirha on 2009-02-25
top and nethack does not have [GUI](http://en.wikipedia.org/wiki/Graphical_user_interface)s (well, there are some GUI versions of nethack, but not the original) so I'm assuming you are really asking [CLI](http://en.wikipedia.org/wiki/Command-line_interface) questions.

1) You can use ansi escape codes to get colors [http://en.wikipedia.org/wiki/ANSI_escape_code](http://en.wikipedia.org/wiki/ANSI_escape_code)
```
echo -e '\033[01;34mblue\033[0m'
```
2) 
```
$ ldd /usr/bin/top /usr/lib/games/nethack/nethack-console
/usr/bin/top:
	linux-gate.so.1 =>  (0xb7f95000)
	libproc-3.2.7.so => /lib/libproc-3.2.7.so (0xb7f44000)
[COLOR="Blue"]	libncurses.so.5 => /lib/libncurses.so.5 (0xb7f14000)[/COLOR]
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7db5000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7db1000)
	/lib/ld-linux.so.2 (0xb7f7b000)
/usr/lib/games/nethack/nethack-console:
	linux-gate.so.1 =>  (0xb7f20000)
[COLOR="Blue"]	libncurses.so.5 => /lib/libncurses.so.5 (0xb7edc000)[/COLOR]
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d7e000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7d79000)
	/lib/ld-linux.so.2 (0xb7f21000)

```
I'd say ncurses.

---

### Post by .Maleficus. on 2009-02-25
1.  Bash color codes work just fine in any of those languages.  I don't know the technical term for them but "Bash color codes" in Google should yeild some results.

2.  Curses/Ncurses would probably be the easiest way, other than writing your own framework.

---

