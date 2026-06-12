---
title: "How would I open a program from terminal?"
date: 2014-08-17
forum: New to Ubuntu
---

### Post by Demiizev2 on 2014-08-17
I'm extremely new to this and would just like to know the command to open a program from the terminal. Thanks!

---

### Post by nerdtron on 2014-08-17
Open the terminal, then type the program name (ex: firefox). Hit enter.

---

### Post by Bashing-om on 2014-08-17
Demiizev2; Hi ! Welcome to the forum.

All one has to do to open an application in terminal is to type 'that' name into the terminal .. be aware, however, some applications require authentication to open -> say "sudo" for non GUI, or a GUI ap; "gksudo".
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://mywiki.wooledge.org/Permissions](http://mywiki.wooledge.org/Permissions)


Do you have a particular application in mind, or one to use as a direct reference ?

As good places to start this journey.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]all things a re possible
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Frogs Hair on 2014-08-17
Hello and Welcome 

The program name typed in lower-case usually works unless there is an error that keeps the program from opening. If the name is incomplete the result will be command not found.  

Example: ```
unity-tweak-tool
```

---

### Post by Demiizev2 on 2014-08-17
Thanks guys!

Yeah, I was just trying to open up Skype from the terminal.

What does "sudo" mean and what do you mean by nonGUI?

---

### Post by nerdtron on 2014-08-17
sudo, think of it as "Run as Admin" for command line only programs.
gksudo for "Run as Admin" of GUI programs.

---

### Post by Demiizev2 on 2014-08-17
Thanks!

I have another question regarding drivers if you could help. I've downloaded the correct drivers from Nvidia directly from the website and now I'm wondering how to set it up on Ubuntu.

---

### Post by nerdtron on 2014-08-17
> **Demiizev2 said:**
> Thanks!

I have another question regarding drivers if you could help. I've downloaded the correct drivers from Nvidia directly from the website and now I'm wondering how to set it up on Ubuntu.

I guess this needs a new thread and details such as your video card driver, the file that you downloaded and the location where the file is saved like /home/username/Downloads/nvdia-installer-something

Does the nvidia website have instructions on how to install the driver?

More importantly have you tried looking on the "Additional Drivers"? Type driver on the dash and your see "Additional Drivers" from there select the nvidia. This is fastest way.

---

### Post by Demiizev2 on 2014-08-17
Oh, oops. Yeah I did it the second way you said, I thought it didn't work. guess I just had to restart it!

Haha, thanks so much you guys are awesome.

---

### Post by nerdtron on 2014-08-17
It worked after a restart? Good for you, I haven't installed any proprietary driver for a long time now, and last time I tried it, it messed up my display. At least now it's good.

---

### Post by yancek on 2014-08-17
You're usually better off downloading software from the system repository and Nvidia drivers are definitely available.  If you are using 14.04, open System Settings, go to Software and Upgrades and there will be a tab in the window "Additional Driver".  Click on it and wait and it should show what is available and recommended.  If you are not using 14.04, the method is different but you didn't indicate what you were using.

---

### Post by AstroLlama on 2014-08-18
Hi Demiizev, you can open a program in the terminal simply by typing its name in the terminal. Opening graphical programs like internet browsers and other big programs can sometimes be more complex... Programs like firefox, libreoffice, gimp, etc are easier to launch with the launch icons, the application menu, or alt + f2...

On the other hand terminal programs for example: top, custom shell scripts, or the numerous other command-line utilities are best used in the terminal. What program are you trying to open, specifically?

---

