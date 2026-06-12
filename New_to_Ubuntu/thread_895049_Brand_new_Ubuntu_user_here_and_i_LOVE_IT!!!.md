---
title: "Brand new Ubuntu user here and i LOVE IT!!!"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by dvigue on 2008-08-19
Hi gang.
 
i just ordered my new desktop that i am building and since i did not have a copy of xp, and i was not looking forward to spending the money, i looked into this. I am so happy i did it. i had a problem installing it to my laptop (i need to burn it while in linux i think) but i am running it off the cd.  I am so happy with this. i have not used Linux since Mandrake and i was not happy with that. this is so easy.  I think that Microsoft lost a customer today. i have  a few qustions if i may.

1.  i would love to play Counter strike, battlefield 1942, and tiger woods golf.  Is that possible? i installed wine, but i cant use it on this laptop. i will be building my new pc Friday.  i would like some good information on installing and playing those games.

2.  Where can i get and download a bunch of diffrent themes for ubuntu?

3.  i am downloading things on the desktop, but they never appear? and i added folder on the desktop and named it derek, then i did not see it. so i tried to do it again, and it said that named folder was already in use? huh?

4.  am i safe from viruses? spyware?

5.  can i use emule? i love that program

and last.  i am new to this, so when i download a program How do i install it? what is the best way to insall these files to someone new?


Sorry for all the questions, but i am really excited about this. i hope i learn enough to keep this.  GREAT OS!!!

Thanks so much
Derek from Maine

---

### Post by highlyevolved on 2008-08-19
You should be safe from virus etc :)

Check out here for themes etc
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

I don't think your games will work but I'm not sure.

You sure they are saving to the desktop not your home folder?

---

### Post by halitech on 2008-08-19
> **dvigue said:**
> Hi gang.
 
i just ordered my new desktop that i am building and since i did not have a copy of xp, and i was not looking forward to spending the money, i looked into this. I am so happy i did it. i had a problem installing it to my laptop (i need to burn it while in linux i think) but i am running it off the cd.  I am so happy with this. i have not used Linux since Mandrake and i was not happy with that. this is so easy.  I think that Microsoft lost a customer today. i have  a few qustions if i may.

welcome to the board and Ubuntu :)

> 1.  i would love to play Counter strike, battlefield 1942, and tiger woods golf.  Is that possible? i installed wine, but i cant use it on this laptop. i will be building my new pc Friday.  i would like some good information on installing and playing those games.

not sure on this, I'll leave it for the more hard core gamers

> 2.  Where can i get and download a bunch of diffrent themes for ubuntu?
[http://www.gnome-look.org](http://www.gnome-look.org) has a ton of things

> 3.  i am downloading things on the desktop, but they never appear? and i added folder on the desktop and named it derek, then i did not see it. so i tried to do it again, and it said that named folder was already in use? huh?
if you are on the live cd its hard to actually download things. are you sure they are going to the desktop?

> 4.  am i safe from viruses? spyware?
as safe as any computer can be while turned on. there are a few viruses for linux but not many and most have been patched for in the base system so no real threat from them

> 5.  can i use emule? i love that program
I believe this will run in WINE but why not try the native apps like bittornado and azarus?

> and last.  i am new to this, so when i download a program How do i install it? what is the best way to insall these files to someone new?
most of the time it is safer and easier to just open Synaptic and install programs from there. I think I heard there are around 20,000 programs there for free :D

> Sorry for all the questions, but i am really excited about this. i hope i learn enough to keep this.  GREAT OS!!!

Thanks so much
Derek from Maine
you only learn when you ask questions so if you don't ask you'll never know :)

and as Einstein said (I believe it was him) "I may not know my phone number but I know where to find it"

---

### Post by Separ on 2008-08-19
Welcome to the forums :)

Here are some answers:

1. [http://appdb.winehq.org](http://appdb.winehq.org) should tell you how people got certain games to work in wine.

2. Gnome themes: [http://www.gnome-look.org](http://www.gnome-look.org)
KDE themes: [http://www.kde-look.org](http://www.kde-look.org)

3. I think it is a bug in the Live CD as that happens to me on my persistent USB install. You can work around it by going to "Places >> Desktop" from the main menu.

4. For the most part, yes. There are VERY few linux viruses in the wild and if you did get a virus, it would probably have to be compiled from source code. Since you are not an administrator on your user account, it cannot interfere with the root system unless you use "sudo" on it.

5. The alternative is aMule. It is in the repos. (sudo apt-get install amule)

For your last question: You download programs either using the Synaptic Package Manager (System >> Administration > Synaptic) or through terminal (apt-get). You can double click .deb files to install them. Tarballs (.tar.gz) are usually source code but there is usually a README or INSTALL file inside them that tell you what to do.

Hope this helps :)

---

### Post by SZ07 on 2008-08-19
Its good that you like Ubuntu. Regarding your gaming question, go to [Wine App Database]("http://appdb.winehq.org/") and search for the games to see what their status and how to get them to run.

For installing programs, you should:
1. try the Add/Remove in the Applications menu
2. If you can't find a program there, open Synaptic and search for it in there.
3. If that doesn't work, search for a ".deb" (deb package) of the program and install it.
4. If that doesn't work, you might have to install from source (hope that you don't have to do this).

---

### Post by sharks on 2008-08-19
Please use a descriptive title and title's like "noob here" or "please help wont help u".

4.As far as virus is concerned only a 40 viruses are there for linux. so its not a worry. if u have wine and have windows it is better to install a antivirus for uubntu(Clamav) because it can scan windows files also.

---

### Post by meanburrito920 on 2008-08-19
1. check winehq.org, but most games should run fine in wine. Just stick in the cd. If the autoboot doesnt start up, then open the cd, right click the autostart/install file, and select Open With > Wine.

3. Your desktop may not be configured to show the icons. Check if the file appears in your Desktop folder in your home directory.

As for installing programs, I would suggest using Add/Remove Programs in your Applications menu rather than synaptic, at least at first. Synaptic is a bit disconcerting unless you know what you are looking for.

---

### Post by sharks on 2008-08-19
A helpful thread for a absolute noob:
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by Separ on 2008-08-19
Sharks, I don't see "Noob here" or "Please help" anywhere in the OPs title. I would say it is descriptive enough but could be reworded slightly by adding "a few questions" or something.

---

### Post by sharks on 2008-08-19
> **Brand new Ubuntu user here and i LOVE IT!!!**

It looks like a testimonal. isnt it?

it doesnt look a question topic.

---

### Post by halitech on 2008-08-19
+1
I agree, I was actually expecting just a testimonial on how great Ubuntu is without the questions when I first opened it up :) but yeah, probably should have added 'I have a few questions as well'

---

### Post by sharks on 2008-08-19
it should have been > Brand new Ubuntu user here and i LOVE IT!!! and have some doubts/question

---

### Post by dvigue on 2008-08-20
Sorry guys, i will word that different the next time....

Wow. great information. thanks so much.  I may install xp also as a dual boot so i can use all my games in case wine does not work right.  which would i install first? linux or xp?

also, when i try and install ubuntu, i get a error half way through. is stays it might my my cd and says to burn slower etc. i read somewhere that if i am burning the image in windows i should use a different program to burn with.  is that true? what is the program?

thanks again guys, i cant wait to build my new system and get rocking!!!!

---

### Post by nothingspecial on 2008-08-20
Apparently it is much easier to install Ubuntu after windows,

This page will help you burn your disk.(In fact bookmark that sites home page. It will help you alot)

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by mali2297 on 2008-08-20
As for installing programs, this howto covers most methods:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

