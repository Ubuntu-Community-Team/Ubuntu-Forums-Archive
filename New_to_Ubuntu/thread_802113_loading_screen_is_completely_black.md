---
title: "loading screen is completely black"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2008-05-21
when I load ubuntu on my Micron Transport GX3 laptop (500 mb, 1.8 ghz). the screen will go completely black after grub loads but you can tell the back light is still on. Just before the login screen appears, the black light turns off for a brief second followed by the login screen.

I have partly fixed this problem by going into grub. clicking down once and deleteing the hide splash (I think) at the end of the command line. Which shows no problems and loads properly. What the hell is going on? (I also usually get some crazy text when shuting down or restarting, don't know if thats normal though.)

---

### Post by candtalan on 2008-05-21
Are you saying that following the login screen, the display is normal then?

---

### Post by LunaticHiatus on 2008-05-21
yes, in fact, I'm responding to you on it now. I should also mentioned I tried it with the last three versions of ubuntu and all three loaded the same.

---

### Post by pdtpatrick on 2008-05-21
how many OSes have you installed on your current HDD? since when you partition your drive, the files are not completely deleted so sometimes you get these crazy fast screen when you shutdown or restart.. I get that at home on one of my test machines.. 

But your current problem is, you want to see the boot loader? did you edit or delete anything else in the grub conf file?

---

### Post by perillux on 2008-05-21
I used to get this problem in gutsy.  It was due to the splash screen not displaying correctly.  Here's how I fixed it:

open a terminal (Applications > Accessories > Terminal) and type:
**gksudo gedit /etc/usplash.conf**   *<--edited, it should work now*

you should see 2 lines in the file that look like this:
[i]xres=???
yres=???[/i]

change it to fit your screens default resolution, so if your resolution is 1024x768 then you would make the file look like this:
[i]xres=1024
yres=768[/i]

Save and close the file.
Then you need to type this in a terminal to finalize the process:
**gksudo update-initramfs -u**

That should do it hopefully.

---

### Post by LunaticHiatus on 2008-05-22
everything went well until I tried to finalize it and press it. It says "user -k does not exist"

---

### Post by perillux on 2008-05-22
ok, sorry.  I couldn't remember the command so I googled it and that was the first one I found.

This one should work though:
**sudo update-initramfs -u**

---

### Post by cpetercarter on 2008-05-22
I have this "problem" too. I have Hardy Heron on both my laptop and my desktop. When I power up the laptop, after the grub business at the start, the Ubuntu logo appears with the little orange bar that moves backwards and forwards, and then the login screen appears. On the desktop, there is a blank black screen after the grub stuff, and then, after a pause, the login screen. I have checked the usplash.conf file. The values in it already correspond to the default screen resolution, so I doubt if that is the problem.
It doesn't really matter, I suppose, since the desktop boots without problem. But I *like*the splash screen stuff and wonder how to get it to work.

---

### Post by LunaticHiatus on 2008-05-23
I typed gksudo gedit /etc/usplash.conf in the terminal
changed my resolution to my screen, saved and closed it
then I typed in sudo update-initramfs -u in the terminal, it updated and....

It worked!!! my laptop loads properly now :) thank ya very much

---

