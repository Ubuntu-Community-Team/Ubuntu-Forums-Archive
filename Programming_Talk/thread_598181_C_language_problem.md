---
title: "C language problem"
date: 2007-10-31
forum: Programming Talk
---

### Post by parijathakumar on 2007-10-31
Hai !
         When I am trying to include 'conio.h' header file in C/C++ programs, the compiler flashes error that it could not find the specified file. I am a beginner to C-language. Can anyone clarify me where the file is located, what path shall I have to include ? I am using the latest 7.10 release.

    Second one: During booting, after the grub screen and after the "starting up" message, suddenly my monitor goes blank and there is a " sync out of range" message roaming over the screen for some time. After a few seconds, it automatically resumes and I am allowed to log into the graphical desktop as usual. The same thing happens at the time of shutting down the machine also.

- Parijatha Kumar

---

### Post by 23meg on 2007-10-31
Moved to Programming Talk. Please post the exact error you're getting.

---

### Post by paul.matthijsse on 2007-10-31
Hello,
conio.h is a non-standard library, try to use stdio.h instead

---

### Post by Compyx on 2007-10-31
> **paul.matthijsse said:**
> Hello,
conio.h is a non-standard library, try to use stdio.h instead

The standard library doesn't provide the functionality conio does, if you want to do stuff like clear the screen, move the cursor to a specific location, etc, you should look into (n)curses.

This will make your program as non-portable as using conio, but at least (n)curses is available on many Unix-like operating systems.

---

### Post by slavik on 2007-10-31
the screen problem has to do with usplash :)

---

### Post by parijathakumar on 2007-11-01
> **Compyx said:**
> The standard library doesn't provide the functionality conio does, if you want to do stuff like clear the screen, move the cursor to a specific location, etc, you should look into (n)curses.

This will make your program as non-portable as using conio, but at least (n)curses is available on many Unix-like operating systems.
Thanks for the reply.  I have just downloaded the ncurses library package from 'Softpedia'. I will check and reply.

---

