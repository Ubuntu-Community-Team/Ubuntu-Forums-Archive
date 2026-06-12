---
title: "Running WoW (and probably other games)"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by earle117 on 2008-07-03
Hey, I'm Earle, new to using Ubuntu and the forums ^_^

I just installed Ubuntu yesterday, mainly because I was bored and my friends had been telling me to use it for a while now.

Now that I'm using it, I think that it's really cool, and like it a lot better than Vista.

The only thing that I can't do is play World of Warcraft, which is 95% of all of my PC time (I run a guild, not playing or finding a new game isn't exactly an option).

I downloaded Wine, but don't understand how to use it, and most of the stuff I've looked up seemed to confuse me further.

If someone could step by step tell me what to do, that would be great, and while I'm not computer-illiterate, I am Linux-illiterate, and it confuzzles me like you wouldn't believe.

Thanks in advance, I'd rather not end up using Vista again JUST because I couldn't get WoW working, Ubuntu is too awesome so far, and I've gotten everything else working great so far (and the GUI is just amazingly awesome looking once you get it tweaked.)

---

### Post by aktiwers on 2008-07-03
Try either PlayOnLinux or Wine-doors. They both do all the hard work for you, and installs WoW and other Windows games.

PlayonLinux:
[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

Wine-Doors:
[http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/)

Good luck and Welcome! :)

---

### Post by hofa on 2008-07-03
aha, gonna make a backup of my linux installation and see if I can get COD4 running ^^
thanks!

---

### Post by rab2140 on 2008-07-03
Hey Earle, I'm new to forums and the whole Linux experience as well. From what i found out is that once you have installed wine you get an icon in your applications tab to show you that it is installed.

Wine does not have a Control panel, at least i don't think it does. It has a configuration setting but thats it. If installed correctly it starts to work right away. You can open most EXE's.

What i found when i installed call of duty 2 is that when you put the DVD you don't get an auto play. You have to explore the cd until you find the setup.exe and then with any luck Your WOW installer will run and you can install and play the game. 

Hope this helps Happy Gaming !

---

### Post by aktiwers on 2008-07-03
Good idea..  let us know how it goes. (though you really dont need to backup.. you could just remove COD4 and Playonlinux if it did not work out. I have only used it with Steam, and it works great! Even though Steam startup is pretty slow. 

Else there is also Cedega, but it costs money.
[http://www.transgaming.com/](http://www.transgaming.com/)

---

### Post by aktiwers on 2008-07-03
> **rab2140 said:**
> Hey Earle, I'm new to forums and the whole Linux experience as well. From what i found out is that once you have installed wine you get an icon in your applications tab to show you that it is installed.

Wine does not have a Control panel, at least i don't think it does. It has a configuration setting but thats it. If installed correctly it starts to work right away. You can open most EXE's.

What i found when i installed call of duty 2 is that when you put the DVD you don't get an auto play. You have to explore the cd until you find the setup.exe and then with any luck Your WOW installer will run and you can install and play the game. 

Hope this helps Happy Gaming !

The wine controle panel is when you type in:
```
winecfg
```
In terminal ;)

But then you would have to create a new instance every time you need to configure wine for a new app or game. The 2 programs I mentioned before, download the app game, configure wine and installs the games/apps automatically. Thats a lot easyer! (if the app/game is on the list of cause).

---

### Post by hyper_ch on 2008-07-03
[https://wiki.ubuntu.com](https://wiki.ubuntu.com) --> search there for Warcraft and it will present you a nice guide... I used the method where I copied an installation from windows to linux partition. Worked perfectly.

---

### Post by Paraphysicist on 2008-07-03
Earle, I'm a linux noob too and I just recently got the game to work.  World of Warcraft currently works extremely well in Hardy 8.04 with wine (it's at the gold level).

This is the best guide- it says 99% of what to do:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)


The only problem with it for me was that the command to mount the dvd with hidden Installer.exe file didn't work.  These commands work:


To unmount:

> sudo umount /media/cdrom0/  

To mount with hidden files:

> sudo mount /media/cdrom0/ -o unhide


Also, under the Config.wtf section:

I had to create the file wtf/Config.wtf and type in it:

> SET gxApi "opengl"

before it would start at all after installation.  This is covered in the guide, it just says to log in to create the file automatically.  Creating the file *before* logging in got it to work for me.  Hope this helps.

If you have any problems with the install, I'd be happy to help in more detail.

---

### Post by earle117 on 2008-07-03
> **aktiwers said:**
> Try either PlayOnLinux or Wine-doors. They both do all the hard work for you, and installs WoW and other Windows games.

PlayonLinux:
[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

Wine-Doors:
[http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/)

Good luck and Welcome! :)

I installed PlayOnLinux, is there any UI or does it just work in the background? As in, could I just try installing WoW right now?

I tried installing it before I got POL, and I was able to open the .exe but it wouldn't install, so I don't think that Wine alone is enough to do it...

I'm leaving for a few days, back Monday, so I'll try out the other posts then, thanks for all the speedy replies ^_^

---

### Post by aktiwers on 2008-07-03
yeah go to Applications = Games = PlayOnLinux

And use the GUI. (click "install", go to Games and pick World of Warcraft) :)

---

### Post by earle117 on 2008-07-04
> **aktiwers said:**
> yeah go to Applications = Games = PlayOnLinux

And use the GUI. (click "install", go to Games and pick World of Warcraft) :)

Alright, I did all of that, it installed, and I see it on the "My Applications" list, but when I select it and click "Run", nothing happens, I'm not sure if I did something wrong or whatever.

Thanks again.

---

### Post by earle117 on 2008-07-07
Bump.

I really could use help with it, I'm not sure if the error was my fault or what...

---

### Post by hyper_ch on 2008-07-07
(1) make a full windows install
(2) copy the files over according to the alternate method

--> that works

---

### Post by aktiwers on 2008-07-07
Does it show up in your Wine menu?
I mean did the installer run and install the game and all?

---

### Post by earle117 on 2008-07-07
> **hyper_ch said:**
> (1) make a full windows install
(2) copy the files over according to the alternate method

--> that works

I already have it installed on my Vista, how would I move it over? I have both OS's on my same HDD, just with a partition.

> **aktiwers said:**
> Does it show up in your Wine menu?
I mean did the installer run and install the game and all?

Yeah, it shows up on my menus and stuff, but when I click on it from my "Applications" menu, or from the PlayOnLinux UI, nothing happens.

---

### Post by hyper_ch on 2008-07-08
> **earle117 said:**
> I already have it installed on my Vista, how would I move it over? I have both OS's on my same HDD, just with a partition.

ntfs-3g

---

### Post by earle117 on 2008-07-09
> **hyper_ch said:**
> ntfs-3g

NTFS-3G?

Is it a file moving program or something?...

---

### Post by aktiwers on 2008-07-09
```
sudo apt-get install ntfs-3g
```Will install ntfs read/write support on ntfs drives. This way you can see your windows partition and copy from it

---

### Post by earle117 on 2008-08-03
Sorry, been away on trips and such, been a while since I've check the forums.



> **aktiwers said:**
> ```
sudo apt-get install ntfs-3g
```Will install ntfs read/write support on ntfs drives. This way you can see your windows partition and copy from it

So, it will let me see my Windows partition, and I can just copy it and paste it over?

---

### Post by aktiwers on 2008-08-03
I guess it will automount then yes. Sorry I have not used NTFS for almost 2 years so I cant remember.

But after you install ntfs-3g we can eitherway mount the drive manually if it does not automatically .

---

### Post by hyper_ch on 2008-08-04
just mount the ntfs drive... not even necessary to isntall ntfs-3g (although it's installed by default I think now) and then just copy it over.

---

### Post by earle117 on 2008-08-12
Ok, I have NTFS-3G, and I can see all of my Vista partition, including my World of Warcraft folders. Where do I want to copy the files to? As in, where on my Ubuntu partition should I put the folder at?

---

### Post by hyper_ch on 2008-08-12
did you setup wine yet?

---

### Post by earle117 on 2008-08-12
> **hyper_ch said:**
> did you setup wine yet?

I have Wine installed...

---

### Post by hyper_ch on 2008-08-13
then copy the wow installation from your ntfs drive into ~/.wine/drive_c/...... somewhere and do all the registry settings that are described in the Ubuntu wiki.

---

### Post by earle117 on 2008-08-13
Ok, I'm copying it over right now, and I found those registry changes and I'll apply those once it's done copying.

I'll post later once I get to check it out to fill you in on how it's running.

BTW, thanks guys for all the help so far.

---

### Post by metasolaris on 2008-08-13
> **earle117 said:**
> I installed PlayOnLinux, is there any UI or does it just work in the background? As in, could I just try installing WoW right now?

I tried installing it before I got POL, and I was able to open the .exe but it wouldn't install, so I don't think that Wine alone is enough to do it...

I'm leaving for a few days, back Monday, so I'll try out the other posts then, thanks for all the speedy replies ^_^

Hi Earle,

I had a similar problem only I really couldn't part with Half Life 2 and, now, Bioshock. 

While these windows emulators are getting better, I found it much much easier and cheaper to simply patch in a second hard drive and to install XP on it for occasional gameplay - something XP does marvelously well!

meTa

---

### Post by earle117 on 2008-08-13
> **metasolaris said:**
> Hi Earle,

I had a similar problem only I really couldn't part with Half Life 2 and, now, Bioshock. 

While these windows emulators are getting better, I found it much much easier and cheaper to simply patch in a second hard drive and to install XP on it for occasional gameplay - something XP does marvelously well!

meTa

The only problem with that is that I don't occasionally play World of Warcraft, I play it daily, sometimes for a few hours or more. I use it as a way to keep in touch with friends, and I manage a guild, so I can't really be absent for long periods of time.

So, if I did that, I would end up only using my Windows and never using Ubuntu. And then I would be sadface.

---

