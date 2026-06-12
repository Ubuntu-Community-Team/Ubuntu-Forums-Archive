---
title: "[SOLVED] Running a .NET program under Mono"
date: 2007-09-27
forum: Programming Talk
---

### Post by AmazingAnt on 2007-09-27
So, the big problem would be something like, I can't get it to compile things, or I brought a program over from windows and it won't work, or something like that, right? Wrong... The console app that came with all these Mono packages I just installed did a grand job of compiling the code from a C# program I built ages ago on a windows machine.

The problem is, I can't seem to find out how to run the program. It gave me the program as a .exe file, which is normal to me from windows development, but no matter how much right-clicking I do, I can't seem to get it to even try to start. Now, this may have to do with the fact that I have WINE on here, and thus it may/may not be trying and failing to run it through that instead of Mono, but I'm not sure.

Anyone have any thoughts or obvious comments to give/throw at me?:confused:

---

### Post by yabbadabbadont on 2007-09-27
Open a terminal window and run:
```
mono YourProgramNameHere.exe
```

---

### Post by AmazingAnt on 2007-09-27
Well, at least that wasn't too obvious a thing to have missed. :P

Thanks! This is just..... awesome...

---

### Post by emperon on 2007-09-29
you don't have to write mono xxxx
just run it as if it is a normal program like ./xxx 
and make sure you have execute permission

---

### Post by Lankster on 2012-04-15
Ok I want to open the mono file in a file ie: 

cd /home/user/system/bakgrds/fil/lib/bin/

mono ABC.exe

how do I get the file to start this on a click, so I dont have to goto a termal window and then type that all in and then start the mono abc.exe file then tell it to just Run.... 

Is there a better way... any help TY
this is what my ABC text file looks like that.
```

echo -e
cd /home/user/system/bakgrds/fil/lib/bin/
echo -e
mono ABC.exe

```

ty

---

