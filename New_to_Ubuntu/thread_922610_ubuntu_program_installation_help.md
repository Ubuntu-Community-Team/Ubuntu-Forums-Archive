---
title: "ubuntu program installation help"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by brian123321 on 2008-09-17
ok so i have ubuntu running as my operating system.  I want to download fulltiltpoker.exe and run it.  when i d/l and double click it in the download section from mozilla firefox it says the link needs to be opened with an application.  does anyone know what application i need to use to open it and where i can find said application?

---

### Post by snowpine on 2008-09-17
.exe files are Windows applications.

---

### Post by Ericthegreat on 2008-09-17
Anyone know if that works in Wine?

---

### Post by Ryadt on 2008-09-17
.exe files does not open in ubuntu. You can try installing it through wine.
Install wine ```
sudo apt-get install wine
```

---

### Post by karlr42 on 2008-09-17
Bit of advice- that's not how software installation in Linux works, finding .exe's online and installing them. You get the programs you need from repositories via apt-get. 
But if you must install it, it's a Windows program, so you need Wine.
```

sudo apt-get install wine
``` in a terminal
(See how I don't go searching for that?)
Once that's installed, try double clicking on the exe file you mentioned. No guarantee it'll work, though, it's a Windows program, not a Linux program!

---

### Post by brian123321 on 2008-09-17
ok so after i get wine what is the command to try and use it to install my fulltilt poker . . .  also if anyone else is familure with poker clients . . . does fulltilt or stars offer linux versions? ill will algo google this but i thought if someone knew off the top of their head they could post.  thanks for the help so far

---

### Post by jbrown96 on 2008-09-17
You cannot run *.exe programs in Linux. They are a different format. There is a program called wine that allows you to run some windows applications in Linux. I checked and wine does support fulltiltpoker. You will need to install wine. Open synatic (System-->Administration-->Synaptic Package Manager). Search for wine and choose to install it (not wine-dev or any of the other packages, unless it automatically selects them). Once wine is installed, you should be able to open the fulltiltpoker.exe and install it the same way you do in windows.

---

### Post by fatality_uk on 2008-09-17
You can't just run Windows application on Ubuntu. To run them you need to install an application called WINE first. Be warned, while WINE will allow you to run some Windows apps, it wont run all.

---

### Post by brian123321 on 2008-09-17
guys thanks a lot. wine worked i installed both fulltilt poker and poker stars. again, thanks for the help.

---

### Post by karlr42 on 2008-09-17
Please mark the thread as [SOLVED] with the "Thread Tools" button at the top right of the page

---

### Post by brian123321 on 2008-09-17
ran into a problem. so i had ftp running and then it froze. i shut down ubuntu and tried to boot it up again and now it will not boot up . . .  just sits at a blank black screen with blinking dot . . . . any ideas?

---

