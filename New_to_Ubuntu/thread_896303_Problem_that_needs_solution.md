---
title: "Problem that needs solution"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by swapan2525 on 2008-08-21
I had installed a bulk email sending software. It was fine till I clicked the the new message button. This appeared: An unhandled exception has occurred in your application. If you click Continue, the application will ignore this error and attempt to continue.If you click Quit, the application will be shut down immediately. Class not registered. 

I also found this: When JIT debugging is enabled, any unhandled exception will be sent to the JIT debugger registered on the machine rather than being handled by this dialog.

Well, after I click Continue, nothing happens. Can anyone out there solved this problem? :(

---

### Post by icecloud on 2008-08-21
what is the current software that you are trying to use aka the bulk email sending software...is it a linux software? or is it windows. if it is windows did you install wine on the pc?

---

### Post by swapan2525 on 2008-08-21
I use windows. I am not an expert in this field. What is wine?

---

### Post by icecloud on 2008-08-21
Wine is a linux program that is basically like a windows emulator. it creates its own c:/ drive inside your linux box and allows you to install windows programs (not all work or work correctly) into your linux/unix pc. so basically if your used to running windows and the program your trying to use is designed for windows and your now using a version of linux (ubunto,kubunto,etc) goto your system drop down window then to administration then click synaptic packate manager. when that opens select all on the left hand side then click in the top right scroll box and type wine. it will take you to the program and just right click it and say that you want to install. then just apply those settings and vuala! you now have wine and when you try to reinstall said windows program right click it first and choose wine as the program to open it and it should work or work better than it is now WOW that was a mouthful. sorry.

---

### Post by swapan2525 on 2008-08-21
Sorry icecloud to bother you. Where do I find 'system drop down window ...'?

---

### Post by icecloud on 2008-08-21
not a bother. up at the top left of your monitor should be a bar there will be the ubunto insignia next to applications. next to that is places. next to that is System! that is your system drop down menu. click system and there ya go :D

---

### Post by sherin on 2008-08-21
just curious... is this application written in java or .net?  

icecloud, how well wine support .net runtime ? do we need to install mono ?

---

### Post by swapan2525 on 2008-08-21
Thanks icecloud:)

---

### Post by icecloud on 2008-08-21
sherin i honestly dont know. um i've run ventrilo, world of warcraft, utorrent, opera all on wine so far and havent really had any issues (still working out kinks on WOW but thats mainly my graphics card.

---

### Post by prshah on 2008-08-21
> **sherin said:**
>  how well wine support .net runtime ? do we need to install mono ?

Sorry to jump in:

Yes you can install mono in Wine if you like, but it's a long and painful process. Mono is also available for linux (After all, .net is _supposed_ to be cross-platform), but some implementations can be handled only in WINE's mono.

If you would like to try a mono app in linux, just prefix the name of your mono program with "mono" at the prompt. Eg: In a terminal (Applications-Accessories-Terminal)```

mono someprogram.exe
#to run the same in WINE mono
wine mono someprogram.exe
#or just
wine someprogram.exe
```

Note that mono needs to be installed seperately, irrespective of wether you use WINE or Ubuntu; AFAIK, only Novell's OpenSUSE comes with mono (linux version) preinstalled.

---

### Post by prshah on 2008-08-21
> **swapan2525 said:**
> I use windows. I am not an expert in this field. What is wine?

Are you using Windows, or Linux (Ubuntu)? If you're using Windows, you should request this thread to be moved to the Windows forum, so that you can get more relevant replies.

---

### Post by prshah on 2008-08-21
> **sherin said:**
>  how well wine support .net runtime ? do we need to install mono ?

Yes you can install mono in Wine if you like, but it's a long and painful process. Mono is also available for linux (After all, .net is _supposed_ to be cross-platform), but some implementations can be handled only in WINE's mono.

If you would like to try a mono app in linux, just prefix the name of your mono program with "mono" at the prompt. Eg: In a terminal (Applications-Accessories-Terminal)```

mono someprogram.exe
#to run the same in WINE mono
wine mono someprogram.exe
#or just
wine someprogram.exe
```

Note that mono needs to be installed seperately, irrespective of wether you use WINE or Ubuntu; AFAIK, only Novell's OpenSUSE comes with mono (linux version) preinstalled.

EDIT: Double post, don't know how that happened.

---

### Post by sherin on 2008-08-29
nothing like . i was just curious about that . im am not a WOW guy :)  anyways thanks for the reply .

---

### Post by t0p on 2008-08-29
> **swapan2525 said:**
> I had installed a bulk email sending software.


I'm sorry if this is OT... but "bulk email sending software"?  Isn't that a **spamming** app?  And isn't helping someone to send spam against the rules?  Or have I completely misunderstood what's going on?

---

