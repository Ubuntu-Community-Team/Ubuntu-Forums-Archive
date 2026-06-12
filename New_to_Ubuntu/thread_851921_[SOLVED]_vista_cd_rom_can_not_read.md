---
title: "[SOLVED] vista cd rom can not read"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by reahjw6 on 2008-07-07
Hey all 
I am new to ubuntu and all is going well.
The only problem i have is that i use a cdrom for study purposes that is written for vista.
the drive shows the files on the cdrom but i am not able to read any of the files or open them.
Please any help.

---

### Post by pedro_orange on 2008-07-07
Did you make this CD in Vista yourself?

If so, did you finalize the burning process? Cause by default Vista writes CDs with a live streaming thing that allows you to write more, but it's only readable on Vista (Citation needed!)

Alternatively; if it's a UDF DVD you should read up on it and follow a guide like: [http://ascending.wordpress.com/2008/06/14/howto-read-vista-burnt-udf-dvds-on-ubuntu-linux/](http://ascending.wordpress.com/2008/06/14/howto-read-vista-burnt-udf-dvds-on-ubuntu-linux/)

---

### Post by reahjw6 on 2008-07-07
no it is a bought cdrom
The content is used for my studies and is used everyday

---

### Post by rogier.de.groot on 2008-07-07
So, if I understand correctly ubuntu does read the cdrom?
That would probably mean a problem with the type of files you're trying to open; what type of files are they? If you're trying to run an .exe file (windows executable) that won't work. If it's a Word document or HTML file or something it should work though.
Could you check if you can read the files themselves, by right-clicking on one and using the "Open with" menu to open them in a text editor or something?
If you can do that, you're simply missing the right software to open the files with; otherwise it's something fishier.

---

### Post by derred on 2008-07-07
What kind of files are they (for example filename.docx). Maybe they are in a format not supported by the programs installed by default in Ubuntu.

__
2 slow

---

### Post by reahjw6 on 2008-07-07
The files are exe.files
when i try to open unable to read comes up.

---

### Post by rogier.de.groot on 2008-07-07
.exe files a Windows executables, Linux can't open them by default. Depending on the type of exe files (.NET or not) you could try with wine (install the latest version from winehq) or mono. Try opening one on the command line with "mono some.exe".
Generally speaking though, you'll probably want to open these in Windows since it won't really work well on Ubuntu.

---

### Post by reahjw6 on 2008-07-07
thanks ill give that a go first.
raeh

---

### Post by hyper_ch on 2008-07-07
why do people keep thinking that applications written for windows just work on linux? Do they also think applications written for windows will also just work on Macs?

I bet most people do not think that PSP 3 games run on Wii....

---

### Post by reahjw6 on 2008-07-07
> **hyper_ch said:**
> why do people keep thinking that applications written for windows just work on linux? Do they also think applications written for windows will also just work on Macs?

I bet most people do not think that PSP 3 games run on Wii....

We all have to start somewhere i thought that was the idea of this forum to offer help.
I posted on the beginners site
 because im new to linux  and needed help not degregation.

---

### Post by pedro_orange on 2008-07-07
This thread will tell you how to install WINE: [http://ubuntuforums.org/showthread.php?t=624644](http://ubuntuforums.org/showthread.php?t=624644)

Once you've installed WINE you can try and open an.exe file with it. (i.e. Right-click it and choose Open with another Application... and then choose WINE.

You can check to see if that software has already been tested on WINE at the AppDB of the WINE website located here: [http://appdb.winehq.org/](http://appdb.winehq.org/)

Good luck

---

### Post by rogier.de.groot on 2008-07-07
Not many people are actually aware of the difference in executable formats used by different operating systems, or the different instruction sets used by different processor types.
And why should they? I bet there's plenty of similar situations in other areas we geeks are not aware of.
My father works for a bank and claims americans are unaware of the existence of other kinds of currency than the dollar; I hope he was joking about that, but after seeing Bush on TV I'm not to sure...

---

### Post by Flimm on 2008-07-07
> **reahjw6 said:**
> We all have to start somewhere i thought that was the idea of this forum to offer help.
I posted on the beginners site
 because im new to linux  and needed help not degregation.
Don't worry reahjw6, we'll help, this is the Ubuntu community after all, Ubuntu is for human beings. I don't think hyper_ch was trying to accuse you, he was just thinking aloud, wondering why people in general understand that PS3 and Wii need different types of games but not Windows and Linux.

---

### Post by reahjw6 on 2008-07-07
Thanks all will keep trying to find a solution.
will have a look at wine.
Agian thanks
 reahjw6

---

