---
title: "Linux -m32 gcc compiling now working"
date: 2018-02-06
forum: Programming Talk
---

### Post by jc0724 on 2018-02-06
[COLOR=#2C2C2C][FONT=&quot]I keep trying to compile a program I am running in linux using -m32.[/FONT][/COLOR]


[COLOR=#2C2C2C][FONT=&quot]I keep getting this error.[/FONT][/COLOR]

[COLOR=#2C2C2C][FONT=&quot]gcc -g -m32 encrypt.c -o encrypt[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=&quot]/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/6/libgcc.a when searching for -lgcc[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=&quot]/usr/bin/ld: cannot find -lgcc[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=&quot]/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/6/libgcc.a when searching for -lgcc[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=&quot]/usr/bin/ld: cannot find -lgcc[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=&quot]collect2: error: ld returned 1 exit status[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=&quot]Makefile:3: recipe for target 'all' failed[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=&quot]make: *** [all] Error 1[/FONT][/COLOR]

[COLOR=#2C2C2C][FONT=&quot]I googled and learned that running this command should fix it.[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=&quot]sudo apt-get install gcc-multilib g++-multilib[/FONT][/COLOR]

[COLOR=#2C2C2C][FONT=&quot]but I am still getting the same errors.[/FONT][/COLOR][COLOR=#000000][FONT=&quot]

I also did a gcc and g++ upgrade following these instructions to see if that would fix it[/FONT]

[/COLOR][[COLOR=#000000]https://www.youtube.com/watch?v=vVzshfYSgRk[/COLOR]]("https://www.youtube.com/watch?v=vVzshfYSgRk")[COLOR=#000000]

[FONT=&quot]but I am still getting the same errors.[/FONT][/COLOR]

---

### Post by steeldriver on 2018-02-07
Hello and welcome to the forums

What version of Ubuntu are you using? The compatible version of the library is likely in package `gcc-6-multilib`; if `gcc-6` is the default gcc compiler for your system, then that should have been installed as a dependency of `gcc-multilib` however if your system's default gcc is gcc-5 or lower and you installed gcc-6 via a PPA for example then you may need to add gcc-6-multilib explicitly

---

