---
title: "runing cmd from C"
date: 2005-12-05
forum: Programming Talk
---

### Post by rock freak on 2005-12-05
hi there guys how would you run a external program in C lets take the windows cmd cos all windows machines sud have tht!!!

any ideas??

---

### Post by JamesA on 2005-12-05
What do u mean? Do you mean sending direct commands to the OS using C?

system(); should work, such as in windows system("dir"); would send the command dir to cmd and return the results. for linux it would be system("ls"); etc.

I hope this is what your asking, if not, sorry for the waste of time.:D

---

### Post by rock freak on 2005-12-05
i was more thinking of getting C to open another program, i wasnt to clear on what i ment there sorry

---

### Post by JamesA on 2005-12-05
im not sure if there is another function in C to do this, but system should be able to work. It must also be said im not the most competant C coder, havn't programmed in it in a long time.

However, lets say the other program you want to run is in the directory 
"C:\rockfreak\anotherprogram.exe"

then to run that in a C program would be system("C:\rockfreak\anotherprogram.exe");

i..think.. give it a try.

---

### Post by jerome bettis on 2005-12-05
when did this become a windows forum lol ...


you'll need to use fork() and excevp()

this thread should help you get what you need:  [http://www.ubuntuforums.org/showthread.php?t=43562&highlight=fork](http://www.ubuntuforums.org/showthread.php?t=43562&highlight=fork)

---

### Post by wmcbrine on 2005-12-05
system() works almost everywhere (it's ANSI). It's not as sophisticated as fork()/exec(), but you probably don't need it to be.

popen() is also nice.

---

### Post by gord on 2005-12-05
[http://www.ubuntuforums.org/showthread.php?t=95533](http://www.ubuntuforums.org/showthread.php?t=95533) has a nice simple version of howto do it, there are quite a few ways to skin a cat ;)

---

