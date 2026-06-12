---
title: "question about running .exe files and programs"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by Majeh on 2008-10-27
Ok, I'll admit I'm a total noob here, but what would i have to enter into the terminal to activate a .exe file.  I click on it and it says that there is no application for a file of that type.  Any apps that would help me out and make this situation in the future easier?

---

### Post by sepz on 2008-10-27
exe files are windows executable files and will not run 'natively' in Linux, you will need an emulator such as wine to run these sorts of programs. To get wine you'll need to do;

```
sudo apt-get install wine
```

Then once installed do winecfg at the prompt.
Then "wine program.exe" in a terminal.

Mileage will vary depending on what you're trying to run.

---

### Post by Soulcage on 2008-10-27
Have you been to [http://www.winehq.org/](http://www.winehq.org/) ???

---

### Post by roger_1960 on 2008-10-27
Hi Majeh

Where to start!?  Linux does not run the same file types as windows, so you cannot just 'run' a .exe file.  Generally applications are written for windows OR mac OR linux and you need a suitable aplication for the operating system you use.  Windows apps generally end in .exe  Linux(ubuntu) apps (and files generally) do not often have file extensions. (ie the .exe bit)

There is a way to run windows applications under ubuntu using a program called 'Wine' but it may be a bit much to take on yet.  Have a look at the 'wine' forum.

---

### Post by aeiah on 2008-10-27
what are you trying to run? linux has alternatives to almost anything you would want to do, although if you really must run a specific program (and not just a program to achieve a specific task) then you'll need wine. most of the time, this isnt necessary though.

---

### Post by Majeh on 2008-10-27
Thanks for the quick answers everyone, I'll take a look at Wine and it's forums and take things from there.  Again, thanks.

---

### Post by reg4c on 2008-10-27
After you install Wine, then right click on the .EXE file, go to Properties and then go to Open With and choose Wine so that Wine handles all the EXE files.

Cheers

---

