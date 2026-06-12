---
title: "Problem with WINE"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by alarson82 on 2008-05-06
I Installed WINE so i could use Slacker media player (best internet radio stations i've ever found).

After I installed the exe. and run the program I get an error.

"Debug Assertion Failed!

Program : C:\Program Files\Slacker\Software PLayer\slacker.jukebox.exe
File : .\MiniDump.cpp
Line : 333
Expression :  ((HANDLE)(LONG_PTR)-1)!= hFile
Last Error (0x00000020) : Sharing violation"

--Abort--  --Retry--  --Ignore--

Any ideas what this means? please help!

---

### Post by nowshining on 2008-05-06
more than likely it won't work in WINE, not all apps work and or work correctly in WINE, it's doesn't 100% percently run window type programs.

---

### Post by alarson82 on 2008-05-06
I did find a crash.rpt file  

here it is
--------------------------------------------------
Tue May 06 21:52:55 2008



Exception Stack: 

	module: C:\windows\system32\KERNEL32.dll

	code: 80000003 BREAKPOINT, addr: 7B8407A3, flag: 10, parm: (0)



Registers:

EAX:00000001

EBX:00000001

ECX:5df33aba

EDX:7f7e004c

ESI:00000000

EDI:00000029

CS:EIP:0073:7b8407a3

SS:ESP:007b:7f22e508  EBP:7f22e508

DS:007b  ES:007b  FS:0033  GS:003b  

Flags:00000202



Call Stack:

Address   Frame     Logical addr  Module

7b8407a3  7F22E508  0001:0001f7a3 C:\windows\system32\KERNEL32.dll

60008bc8  7F22E53C  0001:00007bc8 C:\Program Files\Slacker\Software Player\slacker.bsu.dll

7f2d5638  7F22E55C  0001:00024638 C:\Program Files\Slacker\Software Player\slacker.shared.dll

7f2bc671  7F22E6B8  0001:0000b671 C:\Program Files\Slacker\Software Player\slacker.shared.dll

7b84444f  7F22E9F8  0001:0002344f C:\windows\system32\KERNEL32.dll

78138b5e  7F22EA18  0001:00007b5e C:\windows\winsxs\x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.42_x-ww_0de06acd\MSVCR80.dll

0043c9ee  7F22FF08  0001:0003b9ee C:\Program Files\Slacker\Software Player\slacker.jukebox.exe

7b875be7  7F22FFE8  0001:00054be7 C:\windows\system32\KERNEL32.dll


Does that mean anything to anyone???

---

### Post by dark_harmonics on 2008-05-06
Im not sure i know which software you're talking about but is it located here? [http://www.slacker.com/products/software/](http://www.slacker.com/products/software/)
You would need all the components working under wine that it says below the picture there for it to work. 

Remember wine really isnt full support. Its a really nice tool that sometimes gives results, but in my experience those odd programs with 1000 requirements almost never work. 

I did get office 2003, magic iso, pc anywhere, portal and many other programs to work easily. Its better if the program is more common and you can find a winehq entry about it, especially if you are new to ubuntu. Dont let wine make you wine i always say :)

---

### Post by nowshining on 2008-05-06
"Dont let wine make you wine i always say"

hehe, i'm gong to rem. that one. :)

---

### Post by alarson82 on 2008-05-06
> **dark_harmonics said:**
> Im not sure i know which software you're talking about but is it located here? [http://www.slacker.com/products/software/](http://www.slacker.com/products/software/)


Yes, that is the one.

I tried installing MS core fonts, and i can't even get IE open in wine.  It opens up to just a blank white screen.  I'm such a noob at this.

---

### Post by dark_harmonics on 2008-05-06
> **alarson82 said:**
> Yes, that is the one.

I tried installing MS core fonts, and i can't even get IE open in wine.  It opens up to just a blank white screen.  I'm such a noob at this.

oh you need to specify a webpage to open ie (although i dont know why you would) and it opens up kinda hacky. try wine iexplore.exe [www.google.com](www.google.com) if you really want (not much point other than to confirm it works). Im sorry i couldnt offer any deeper thoughts but i've been scanning around with no results for like 10 minutes here and im just not at guru level yet :(

---

### Post by alarson82 on 2008-05-06
when i open up iexplore.exe i get a window that opens

in the 'orange part' it says "Wine Internet Explorer"

and its just all white in the inside. no buttons, address bar.. nothing

---

### Post by Xiong Chiamiov on 2008-05-07
> **dark_harmonics said:**
> oh you need to specify a webpage to open ie (although i dont know why you would)

I have IE 6 installed for web development, though I actually use it occasionally for flash sites that don't work with adobe's crap they give us.

Try installing IE through [ies4linux]("http://www.tatanka.com.br/").

---

### Post by dark_harmonics on 2008-05-07
Yea thats what i meant by hacky. If you want to use IE6 for real you need ies4linux like the above poster stated. I dont know why you would though.

---

### Post by linuxlizard on 2008-05-07
I don't know anything about slacker because I've never tried it, but you might try streamtuner with audacious in the repositories for internet radio.

---

### Post by clairegrrl on 2008-05-07
I have to say that ies4linux will make your life easier.  I have one website for school that needs IE to work, and this solved all my probs.

---

### Post by alarson82 on 2008-05-07
Hey thanks for the help to everyone

I'm going to give up on WINE for my windows stuff, both slacker and quicken '07 don't work with it.

I'll be researching virtualization and probably loading up a virtual xp inside ubuntu to run those applications.

Thanks again

---

