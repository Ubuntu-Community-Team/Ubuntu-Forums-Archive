---
title: "Can I run .exe files in Ubuntu HH?"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by TopFan on 2008-11-11
Is there any way to run a .exe file using Ubuntu HH?

---

### Post by SunnyRabbiera on 2008-11-11
Yes, its possible to run most windows applications under ubuntu.
There is a application called WINE, it will work on a good majority of your windows applications.
You can find it under add/remove and search for wine.
Just remember not all .exe will work, wine is still considered experimental by many as it can only do so much

---

### Post by mapes12 on 2008-11-11
In my experience there is always a native Linux application for any task that an .exe applications can perform. If you can't find what you want then post what you're trying to do on these forums and someone will point you in the right direction.

---

### Post by CLomax on 2008-11-11
```
sudo apt-get install wine
```

---

### Post by SunnyRabbiera on 2008-11-11
> **mapes12 said:**
> In my experience there is always a native Linux application for any task that an .exe applications can perform. If you can't find what you want then post what you're trying to do on these forums and someone will point you in the right direction.

Yeh though if he does use stuff like photoshop he might be let down by the gimp.
Alternatives are always good to look at though, but say if he needs MS office or something for his work.
Open office does a great job but because of businesses being buddies with microsoft sometimes its hard to use the alternatives.

---

### Post by ericmc783 on 2008-11-11
Agree with those who tell you to try wine, as well as finding an equivalent linux package.

To get to your windows files on the hard disk, go to the places menu, and there should be an option there, that says something upon the lines of "100.00 GB Media". That's your windows C: Drive.

---

### Post by TopFan on 2008-11-11
Everyone,

Thank you for your speedy responses! I have downloaded WINE and made some progress, but the .exe file still won't run.

There's no alternative software available - the file is an airline [therefore, company specific] annual Safety, Equipment and Procedures exam.

It's a bizarre process: you download and install the 'empty' shell (21.7mb) that is the framework for the exam. You then download the annual 'Question Bank' [This element changes every year]. Both are .exe files. You then run the first file and it grabs the actual Qs from the second to give you the exam. 

Don't ask me why my airline does it like this - I can think of 1 x 10^6 better ways of doing it! I'm sure you can too.

With WINE I can now download and install the shell, but can't run the exam.

Ah, well. It was a long shot anyway. I'll just have to go to work early (anathema to an airline employee :grin: ) and do the test there.

Thanks for your help. Much appreciated.

---

### Post by SunnyRabbiera on 2008-11-11
Yeh that is how things are with crap like that, they have no consideration I tell you

---

### Post by Kellemora on 2008-11-11
Hi Top Fan

You may need to do some tweaking to get it to run, but in this case I think it should run for you, as others have had that same issue or issues like it and have succeeded in doing so.

What WINE can't run can be pretty much summarized in one word API.
If a program makes a call to an API function, it won't run in wine.
About the only programs that do this are heavy graphics games that require weird things to make them work and humongous programs such as Quickbooks.  Sorta like the old Peeks, Pokes and Calls in Apples BASIC programming language where they are actually looking at the CPU's registers from within a program.

In the disk that you installed this from, are there folders containing .dlls or something that you can copy into a folder on the wine drive_C for the program.  Sometimes that makes things start working when they wouldn't before too.  Wine does not include ALL the .dll's found on windows machines.

Good Luck

TTUL
Gary

---

### Post by lakersforce on 2008-11-11
Perhaps your file is made with C#? If, then it is not really a exe file but an image file. To run that in linux you'll have to install the mono framework (sudo apt-get install mono), make sure the exe file is executeable under linux, and then run it under linux like you normally would (./<yourfile.exe>).

---

### Post by directhex on 2008-11-11
> **lakersforce said:**
> Perhaps your file is made with C#? If, then it is not really a exe file but an image file. To run that in linux you'll have to install the mono framework (sudo apt-get install mono), make sure the exe file is executeable under linux, and then run it under linux like you normally would (./<yourfile.exe>).

We killed the "mono" package a while ago. Try mono-runtime

And using ./foo.exe requires installing the binfmt-support package

---

### Post by TopFan on 2008-11-13
I've just upgraded to 8.10, and can't find the WINE application. Is it included in Ubuntu 8.10 by default?

Does running 8.10 make it easier / possible to run the .exe file?

PS - I like 8.10 so far. Seems more stable and user-friendly. Suspend also works at last!

---

