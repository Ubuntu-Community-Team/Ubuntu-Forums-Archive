---
title: "I have a few questions"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by Physika on 2012-06-28
Hello I installed Ubuntu 12.04 last night alongside my Windows 7 OS and I have a few questions. 

1) In windows there is a program I used to take a screen shot of the screen, crop it right then and there, then it uploads it to an image hosting website. I think i found a script for Linux that accomplishes this for Imgur, but I am not sure how to use it. Can you help me figure out how? 
[http://sirupsen.com/a-simple-imgur-bash-screenshot-utility/](http://sirupsen.com/a-simple-imgur-bash-screenshot-utility/)

2) I really like the software center for Linux, it is awesome, but there I have a question about it. When i go to the history tab of the software center it shows all the files that have been installed. Is there a way to separate these to show which apps these components belong to? I have no idea what some of them are. I thought the history would show the apps i installed only, not the components for the apps.

3) Is there a resource you would recommend for learning the shell terminal? I have used a few commands for installing software that i found on the internet and I think it's amazing you can do that, I just don't know how to use it. I got pretty familiar with the command prompt in windows. 

4) I found an App called Wine to run windows programs/games. Does it work well? I have a few games I want to play on here. I tried linux on virtualbox and it was much crisper than windows. I really like it. 

5)I tried installing my  graphics drivers for linux, but i got an error. Can you help me understand how to fix it?
[IMG]http://i.imgur.com/oRHFr.png[/IMG]

6) When I go to dash home all the icons are big and it is annoying. Is there a way to organize these in a list, or at least smaller icons so I can browse them easier? Also will the "apps available for download" be all the results that would appear in the software center? It is really laggy as well, but I'm hoping the graphics driver will fix that. 

7) When I press Alt, a little thing comes out that says to type in a command. Is this the equivalent to the Run function in windows, if so what type of things do you type in there since usually you run .exe or .msc files in windows through there. 

thank you

---

### Post by benj23673 on 2012-06-29
I can answer some of the super easy questions, First wine is supposed to be very good at running most games (I have never used it much and don't game much). Second you can hide and unhide technical details in the bottom left corner of the "installed" programs in the software center. And last cinnamon is a kind of windows look alike menu you can use and download if you dont like the unity dash that much. I hope this helped a little and it will at least give you a bump if nothing more

---

### Post by Physika on 2012-06-29
Thanks for responding. 
I guess once I try out wine I will rate the program based on how well it works.
The technical details option is only available for apps that are already installed. I wasn't talking about the installed apps. If you go over to the history tab of the software center, that option isn't available. 
I don't dislike Unity, in fact I like it. I just want to customize it a little.

---

### Post by lrcaballero on 2012-06-29
sudo apt-get Update = To update your system
sudo apt-get install "name of software" = To install new software
sudo apt-get remove "name of software" = To remove new software

Try this link for basic terminal commands, I also recommend this book "Visual QuikStart Guide Unix & Linux" by Deborah S. Ray Eric J. Ray

Cheers

---

### Post by frame45 on 2012-06-29
To anwser or point in a direction that I can...

3) commandline resources a compiled list is on the sticky. 

[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

7) Alt key that brings up the HUD it's a search box, when I have Firefox open and press alt then I can start searching all of the bookmarks, menu items, etc inside Firefox. If you use the alt key then it searches per the active application. If you use the super (win) key then it will search globally, (and with other lenses, even the net)

Hope that helps a little. Enjoy!

---

### Post by mastablasta on 2012-06-29
> **Physika said:**
> 
2) I really like the software center for Linux, it is awesome, but there I have a question about it. When i go to the history tab of the software center it shows all the files that have been installed. Is there a way to separate these to show which apps these components belong to? I have no idea what some of them are. I thought the history would show the apps i installed only, not the components for the apps.
don't worry about them. in linux the components are (usually) shared between programmes. which makes programmes much smaller on installation than in windows. in windows porgrammes always bring plenty of libraries with them since they do not knwo if users have them or not. 
both approaches have their pluses and minuses.
in linux package managers are taking care of components so you have the right one pulled down for the programme you installed.

> 
3) Is there a resource you would recommend for learning the shell terminal? I have used a few commands for installing software that i found on the internet and I think it's amazing you can do that, I just don't know how to use it. I got pretty familiar with the command prompt in windows. 

there is a free ebook available at linuxcommand.org. Also ubuntu manual has some basics explained.
additionally running command with "man" command in front will explain the command in detail (man = manual for the command)

e.g. you can try

```
man ls
```

> 
4) I found an App called Wine to run windows programs/games. Does it work well? I have a few games I want to play on here. I tried linux on virtualbox and it was much crisper than windows. I really like it.

wine can run only some porgrammes and game and that is to various degree of success. if you have troubel configuring with wine you can use play on linux (which is a GUI interface for wine and has some presets made).  Crossover is another option but that one costs a bit.

to see what works, how well it works and if there is anythign speciall needed for install you can see here: [http://appdb.winehq.org/](http://appdb.winehq.org/) 
> 
5)I tried installing my  graphics drivers for linux, but i got an error. Can you help me understand how to fix it?

have you tried to install it first with hardware drivers applicaiton? it will install proprietry drivers.

otherwise if you realyl want to do thing manually have a lok here: 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

> 
7) When I press Alt, a little thing comes out that says to type in a command. Is this the equivalent to the Run function in windows, if so what type of things do you type in there since usually you run .exe or .msc files in windows through there. 


yes you type in commands or launch porgrammes. for example try to type in  "firefox".

---

### Post by Physika on 2012-06-29
Thank you i have all my questions answered now

1) I figured out how to use the script. All the dependencies the person listed are apparently little "programs" that are required to use the script. I searched for all of them in the software center and installed the ones that I didn't already have. Once i did that i put in the curl command to download his script to my bin folder. After that I hotkeyed his script onto my f12 key and it worked perfectly! I press it, select a part of my screen, then it gives me a notification that the link is my keyboard after it uploads. 

2) I understand now why the components are shown thanks to mastablasta. 
3) Good resources from everyone, will check them out. Also "man" is an amazing command. Thanks
4) I downloaded a software based on wine called playonlinux and it has all the games i wanted to play there
5) I figured out in order to open a .run file I need to do the "sh" command in the terminal. I also figured out what sudo was and learned how to use it. I had previously installed the amd drivers right when i installed ubuntu. I don't remember exactly when, but i was just copying and pasting stuff into the terminal. I completely uninstalled the files i downloaded using this guide [http://askubuntu.com/questions/98827/ati-driver-re-install-fail](http://askubuntu.com/questions/98827/ati-driver-re-install-fail) and installed the .run file i downloaded.


6) I still haven't looked into making the icons smaller, but the lag went away so i don't mind it as much now. I will do it tomorrow probably.

7) thanks frame45 for the great explanation for the alt key

I have the answers to all my questions now so no more need to reply to this thread

---

