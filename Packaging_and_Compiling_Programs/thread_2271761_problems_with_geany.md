---
title: "problems with geany"
date: 2015-04-01
forum: Packaging and Compiling Programs
---

### Post by alessandro.noferi on 2015-04-01
hi all! I have started to programming (C language) with geany, but I have some problems:

1) If a try to execute a program that is not on desktop geany say: 
```
./geany_run_script.sh: 5: ./geany_run_script.sh: ./verifica_di_caratteri_in1_un_testo: Permission denied
```
I have all programs in the USB drive and it is very boring save them every time on desktop

2) Often when I modify the programs, after the recompile and build, the programs show the previous configuration. I think that I haven't been clear, for example: if I modify ```
printf("hi linux");
``` and I run it, is ok, but if I change the test ```
printf("hi \n linux!!);"
``` (after F8 and F9) when i run again the terminal show me  hi linux. why?? :mad:
Sorry for my bad english, for every clarification I am here! :p

---

### Post by steeldriver on 2015-04-01
Hello and welcome to the forums

1) you would need to mount the USB with a suitable umask (and possibly exec option), or re-format it to a filesystem that natively supports Unix-style permission bits

2) because of the syntax error, re-compilation will fail, leaving the previously compiled executable file unmodified

---

### Post by alessandro.noferi on 2015-04-01
thank you for the quick answer. I made a mistake writing the post (edited). In my program the syntax is good, when I compile the modified program I haven't got errors.

---

