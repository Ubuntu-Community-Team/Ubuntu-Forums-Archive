---
title: "Upgrade Difficulties: I don't appreciate"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by rossjman1 on 2008-11-05
I recently updated from 8.04 to 8.10. I wish I would have not upgraded, as nothing good came with it and a cart load of bad things did.
1) "Upgrading" from 8.04 to 8.10 got rid of my boot screen, now all I get is a text boot up.
2) I don't appreciate Ubuntu deleting my ThinkFinger profile... now my finger scanner no longer works.
3) I don't appreciate Ubuntu deleting my Compiz configuration. Now I don't remember my previous configuration and now working on my computer seems foreign. Also, some animations have been removed from Compiz. Where is the explode animation I used for closing applications?
4) "Upgrading" completely messed up my dual monitor setup. Why did it delete AMD Catalyst Control Center in the first place? I had to redownload it. I cannot get dual monitors working at all. CCC can't even detect my other monitor anymore.
5) I don't appreciate the new GNOME freezing about half the time when I try to log in.
6) I don't appreciate these new borders around my conky stuff on my desktop.
7) I don't appreciate Ubuntu rewriting my sound configuration.

I'll add more later. Any advice as to how to fix these problems are appreciated.

---

### Post by steveneddy on 2008-11-05
The preferred way to "upgrade" is to back up your /home directory and perform a total reinstall.

Upgrading through Update Manager or apt-get dist-upgrade will almost always give you problems. I've never had a totally sucessful "upgrade" using either or these two methods.

Just take it in the chin like the rest of us did when we were learning Ubuntu and just do a reinstall.

You will be much happier.

Good Luck.

---

### Post by rossjman1 on 2008-11-05
Awesome, I love to format my computer every 6 months just to keep it up to date. </sarcasm>

This is one of the major reasons why Ubuntu is not currently a respectable alternative to Windows or Mac

---

### Post by Cypher on 2008-11-05
Ubuntu 8.04 is a LTS release of Ubuntu that will be supported for a few years, if things were working perfectly for you there, there was really no reason to upgrade to 8.10 which is a regular release and will be replaced by the next release in 6 months.

Sometimes it's safer to keep the version you're running, especially if you've customized it to your liking as with any full distrobution upgrade, you might have to re-do a few things.

---

### Post by Paqman on 2008-11-05
> **steveneddy said:**
> 
Upgrading through Update Manager or apt-get dist-upgrade will almost always give you problems. I've never had a totally sucessful "upgrade" using either or these two methods.


Well, i've never had an unsuccessful one, personally. You get a lot of people moaning on the forums about borked upgrades, but that's probably because all the people who have uneventful upgrades don't post about it.

rossjman1: There's a few different ways you could make life easier for yourself:
[list]
[*] Install the LTS and use the backports repo to keep your apps up to date.
[*] OR create a seperate /home partition. Reisntalling will take about 30mins and all your settings will be retained like magic. The system can even automatically reinstall all your apps in one step. Try that on Windows/Mac!
[*] OR switch to a distro that either has a rolling release, or one that has a longer release cycle than Ubuntu
[/list]

---

### Post by brandoncolorado on 2008-11-05
> **rossjman1 said:**
> Awesome, I love to format my computer every 6 months just to keep it up to date. </sarcasm>

This is one of the major reasons why Ubuntu is not currently a respectable alternative to Windows or Mac

Maybe you should take a break from the computer, go outside a bit.  People are here to help, but sarcasm is unecessary.

Upgrading works find for lots of us, it worked great for me.

---

### Post by ubnewbie2 on 2008-11-05
> **Paqman said:**
>  The system can even automatically reinstall all your apps in one step. 


Just wondering how I can do that?

---

### Post by hornetster on 2008-11-05
Try upgrading from XP to Vista with no problems... :lolflag:

(Couldn't resist....)

---

### Post by Tom.Servo on 2008-11-05
> **rossjman1 said:**
> Awesome, I love to format my computer every 6 months just to keep it up to date. </sarcasm>

This is one of the major reasons why Ubuntu is not currently a respectable alternative to Windows or Mac

You should demand a refund. /sarcasm

---

### Post by brandoncolorado on 2008-11-05
> **Tom.Servo said:**
> You should demand a refund. /sarcasm

:lolflag:

---

### Post by lovinglinux on 2008-11-05
> **rossjman1 said:**
> Awesome, I love to format my computer every 6 months just to keep it up to date. </sarcasm>

This is one of the major reasons why Ubuntu is not currently a respectable alternative to Windows or Mac

Are you serious? What about formatting Windows every 6 months just keep it running, otherwise it behaves like a lagging turtle?

If you did you homework you...

1 - would know that Hardy is LTS, so it will be supported for a few years. You don't have to upgrade.

2 - would test all your hardware with a Live CD first.

3 - would know that compiz can backup your profile

4 - would backup your /home before upgrading

5 - would make a clean install instead of upgrading

6 - would keep your /home on a separate partition so you could downgrade to Hardy if something goes wrong without loosing your configuration

I tried Intrepid Beta with a fresh install but didn't liked the result, so just did a fresh install of Hardy again, keeping my /home directory and re-installing all applications with a backup script. So, everything is just like before testing Intrepid. The entire process of backing up, upgrading and downgrading again took less than 3 hours, which is far less than what I usually spent re-installing a single Windows release.

This makes me remember when I installed Vista and couldn't re-install XP after that because Vista file system messed up the hd so badly, that not even XP was able to write into it. I had to use some application that completely wiped the hd using a DoD method to securely erase data. What about that?

---

### Post by Paqman on 2008-11-05
> **ubnewbie2 said:**
> Just wondering how I can do that?

[Like this!](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by rossjman1 on 2008-11-05
Haha. Well, 8.04 didn't work properly really. 8.10 actually amplified the problems that I had with 8.04.

I'm woking on a research paper right now. In Open Office if I selected a picture with Compiz running (in 8.04) then it would bring all other open windows to the top. In 8.10, however it just crashes Open Office, wich is about 100x worse.

The reason why I posted this (and I was expecting a lot of the unhelpful responses "demand a refund", etc.) is that there were some fixes availiable. A lot of the stuff is easily fixable (redoing the TinkFinger stuff, Compiz configuration, reinstalling amdcccle), but it is rediculous that I have to, and that the upgrade didn't keep a lot of my settings (I'm still at a loss why the control center was uninstalled. Other problems, however, are my severe (GNOME freezing).

I was just trying to bring attention to the fact that the upgrade deleted some of my settings (which is unnecessary) and something like that should be brought to the attention of the developers and easily fixed for the next version. Please don't tell me to file bug reports, as no one even looks at the ones I submit.

---

### Post by lovinglinux on 2008-11-05
> **ubnewbie2 said:**
> Just wondering how I can do that?

To replicate your packages selection on another machine (or restore it if re-installing), you can type 

dpkg --get-selections > ~/my-packages 

move the file "my-packages" to the other machine, and there type 

sudo dpkg --set-selections < my-packages && apt-get dselect-upgrade

---

### Post by rossjman1 on 2008-11-05
> **lovinglinux said:**
> Are you serious? What about formatting Windows every 6 months just keep it running, otherwise it behaves like a lagging turtle?

If you did you homework you...

1 - would know that Hardy is LTS, so it will be supported for a few years. You don't have to upgrade.

2 - would test all your hardware with a Live CD first.

3 - would know that compiz can backup your profile

4 - would backup your /home before upgrading

5 - would make a clean install instead of upgrading

6 - would keep your /home on a separate partition so you could downgrade to Hardy if something goes wrong without loosing your configuration

I tried Intrepid Beta with a fresh install but didn't liked the result, so just did a fresh install of Hardy again, keeping my /home directory and re-installing all applications with a backup script. So, everything is just like before testing Intrepid. The entire process of backing up, upgrading and downgrading again took less than 3 hours, which is far less than what I usually spent re-installing a single Windows release.

This makes me remember when I installed Vista and couldn't re-install XP after that because Vista file system messed up the hd so badly, that not even XP was able to write into it. I had to use some application that completely wiped the hd using a DoD method to securely erase data. What about that?

1 - I know that, but I figured the problems that I had with 8.04 would be fixed, not made worse.
2 - I know that all my hardware works, so why waste a cd on that?
3 - I figured that it was supposed to keep the config of all my apps, obviously I was wrong.
4 - there is nothing wrong with my /home directory and (see above about keeping settings)
5 - I thought one of the advantages to Linux was there was no need to reinstall. Ubuntu was supposed to keep my settings (for the most part it did)
6 - I've heard this before, but I already had /home on the same partition as everything else. So I figured, probably rightly so, that upgrading would have a less chance of data loss than repartitioning my drive.

---

### Post by lovinglinux on 2008-11-05
> **rossjman1 said:**
> 6 - I've heard this before, but I already had /home on the same partition as everything else. So I figured, probably rightly so, that upgrading would have a less chance of data loss than repartitioning my drive.

As far as I understand, when you do an upgrade, Ubuntu will remove "old programs", so I guess the configuration files are also removed.

The safest way to keep your settings is to have a separate /home partition, so when you re-install you create the new /home mounting point without formatting the partition. This way, the partitioner will format other partitions, but will keep /home intact and will mount it for you in the right place. If something goes wrong, all you have to do is re-install the previous release without formatting the /home again. Nevertheless, backing up your /home is always a good idea.

If you want to move your /home to a new partition, follow [[COLOR="Red"]**this**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=46866")

---

### Post by rossjman1 on 2008-11-06
I am replying to this topic incase someone else has the same problems that I solved. There are also some things I'm still looking for solutions for.
**Solved**
2) ThinkFinger issue: Ubuntu didn't delete my profile, but there is an issue with Xorg and needed to press enter after swiping my finger. Solution is posted here: [https://bugs.edge.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429](https://bugs.edge.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429)
Adding these sources and updating fixed the problem (these are unofficial sources):
deb [http://ppa.launchpad.net/jon-oberheide/ubuntu](http://ppa.launchpad.net/jon-oberheide/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/jon-oberheide/ubuntu](http://ppa.launchpad.net/jon-oberheide/ubuntu) intrepid main
3) Compiz settings issue: Compiz saved some of my settings, but some were changed for either no reason or the feature or annimation was removed. I don't know why annimations were removed...
4) Dual monitor issue: The new amdccle is less intuitive than the older version when it comes to dual monitor set up, but it still works, and relieved a small glitch that caused a black bar at the top of my 2nd screen. It's now working great.
5) GNOME doesn't seem to be freezing anymore - I took no action.
7) Sound issue: simple to fix, just annoying that I had to.
**Unsolved**
1) Boot issue: Back when I set this up in 8.04 I used startup-manager and downloaded a custom splash screen. The settings in startup-manager were the same as I left them. Changing back to the default Ubuntu-slash still doesn't work.
**Keeping the Way it is**
6) Conky - There is now a glowing boarder around all my conky scripts. I will probably look into this in the future, but I currently thinks it gives Conky more character.

**Great New Stuff**
The upgrade did have some good points. Finally Synaptic has a quick search! Also, the Pidgin/GNOME quit applet is really cool and convenient.

---

### Post by WirelessMike on 2008-11-06
I may have a solution for the splash screen on your boot menu.  When you upgraded, grub boot menu likely got rewritten.  When you upgrade to a new release, it gets seriously rewritten.

Use a text editor, or simply open a console and edit your menu.lst file to include a splash screen.  Here is how I did mine:

Store the image you want in a directory local to grub.  I stored mine in /boot/grub/bootsplash/image.xpm.gz (bootsplash being a new directory I created in /boot/grub/)

Now that the splash image is where I want it, I need to edit grub to recognize it, find it and use it.

> sudo nano /boot/grub/menu.lst

Go down a few lines to enter some new info.  I put mine between hiddenmenu and Pretty colours.  Enter the following info:

> # Menu Background Art
splashimage (hd0,1)/boot/grub/bootsplash/image.xpm.gz

Like I mentioned before, this shows up here in my menu.lst:

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Menu Background Art
splashimage (hd0,1)/boot/grub/bootsplash/image.xpm.gz

# Pretty colours
#color cyan/blue white/blue

Now if your Linux root partition isn't at (hd0,1), you'll want to change that of course.  The correct name for the location of your root partition can be found further down the menu.lst


Hope this helps! :)

mike

---

### Post by igknighted on 2008-11-06
> **rossjman1 said:**
> Awesome, I love to format my computer every 6 months just to keep it up to date. </sarcasm>

This is one of the major reasons why Ubuntu is not currently a respectable alternative to Windows or Mac

How is this different from windows/mac at all?  You're insane if you would do an upgrade with either of them also.  If you want to stay "just as up to date", then upgrade every LTS.

Also, there are linux distributions that have no "versions" per se, and just constantly update packages.  Most of these are not the most "new user friendly", but if you really don't want to upgrade versions try using Debian Testing, Arch, Gentoo, Sidux, or one of a few others that i am forgetting at the moment.

PS: If you really want the most pain-free, no update approach, try using OpenSuse.  They have repo's to keep common applications at the latest versions, but keep system files the same so you don't need a full upgrade.

EDIT: I hate having a separate /home.  You will eventually waste space, as you can never accurately predict how much each will need.  IMHO, the best solution is to keep a backup of /home on some other media (I use an external HD, but another internal HD would work too, or also a flash drive or optical media would work with some limitations).  This way you just backup and can restore data as needed.  Plus you are safe in case of a disk failure of some sort.

As for partitioning these days, it really is a trivial task.  I wouldn't worry about data loss.  Even if the absolute worst were to happen, so long as you don't panic you can save the partition tables.  Just remember to always do it from the liveCD, because you cannot modify a partion that is actively in use.

---

### Post by rossjman1 on 2008-11-06
I used startup-manager and imported the splash image. Does startup-manager automatically save the image somewhere? There is no /boot/grub/bootsplash directory. I also have a custom background image for the grub menu that still works. If what I think happened actually happened why did it delete my splash image but keep my background. I'm going to try to find the image again (gnomelook) and try to reimport it with startup-manager. If that doesn't work then I will have to use the old fashioned way.
Also, I just noticed a bunch of topics about this very problem...

**edit:** I didn't have to redownload the theme. It was already sitting in /root/Desktop :) I removed the theme then readded it - restarting my computer now to test *fingers crossed*
**edit2:** Well, custom themes no longer work, but the regular Ubuntu one does. Bug: [https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/235615](https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/235615) I'm trying the sudo startupmanager in the terminal and see if that works for me like it worked for the poster.

---

### Post by rossjman1 on 2008-11-06
> **igknighted said:**
> How is this different from windows/mac at all?  You're insane if you would do an upgrade with either of them also.  If you want to stay "just as up to date", then upgrade every LTS.

Also, there are linux distributions that have no "versions" per se, and just constantly update packages.  Most of these are not the most "new user friendly", but if you really don't want to upgrade versions try using Debian Testing, Arch, Gentoo, Sidux, or one of a few others that i am forgetting at the moment.

PS: If you really want the most pain-free, no update approach, try using OpenSuse.  They have repo's to keep common applications at the latest versions, but keep system files the same so you don't need a full upgrade.

The thing is, I used to use Debian (a while back - before Ubuntu came out). I just like Ubuntu, and this is my only computer - it's where I get all my work done. I know it was probably a dumb idea to update, but I almost got all my problems solved now. After the fact, I'm glad I updated. It's just all the stupid little things that got me all worked up ;)

---

### Post by rossjman1 on 2008-11-06
Ok. So the solution of running startupmanager in the terminal with sudo didn't work. Output:
```
jeff@jeff-laptop:~$ sudo startupmanager
Password or swipe finger: 
/usr/share/startupmanager/gtk_frontend.py:159: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.glade_xml = gtk.glade.XML(GLADE_FILE, None ,APP_NAME)
Grub2 not detected
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: (hd0,0)/boot/grub/splashimages/77266-rays2.xpm.gz

Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Grub Legacy detected
Usplash detected
Splashy not detected
Using '/usr/lib/usplash/usplash-theme-ubuntu.so' to provide 'usplash-artwork.so'.
**Using '/usr/lib/usplash/elvux-theme.so' to provide 'usplash-artwork.so'.**
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
```

I also have 1 more quick question. Back in 8.04 there was a small graphical glitch when I tried to run a root program it would darken the screen and ask me for my password. However, sometimes the screen would stay dark even though I had already entered the password. There was a setting somewhere that I changed that made the gksudo (password prompt) act like a normal window. Now, I think they changed it and I would like to change it back. Does anyone know where this setting is? I already looked in gconf > applications > gksudo.
**edit:** Just found it in Assistive Technologies.

---

### Post by ubnewbie2 on 2008-11-06
> **Paqman said:**
> [Like this!](http://ubuntuforums.org/showthread.php?t=261366)

much appreciated

---

### Post by handydan918 on 2008-11-06
> **rossjman1 said:**
> 1 - I know that, but I figured the problems that I had with 8.04 would be fixed, not made worse.
2 - I know that all my hardware works, so why waste a cd on that?
3 - I figured that it was supposed to keep the config of all my apps, obviously I was wrong.
4 - there is nothing wrong with my /home directory and (see above about keeping settings)
5 - I thought one of the advantages to Linux was there was no need to reinstall. Ubuntu was supposed to keep my settings (for the most part it did)
6 - I've heard this before, but I already had /home on the same partition as everything else. So I figured, probably rightly so, that upgrading would have a less chance of data loss than repartitioning my drive.

Common denominator: "I figured" and "I thought".


But this is the developers problem?


OOOOkay....

---

### Post by Neobuntu on 2008-11-11
Well now, everyone is basically right. Perhaps we shouldn't get too emotional and sarcastic. On the other hand, we are human. Why are we having to fix the same basic things; over and over (with different techniques), every time we do a best and recommended, (K)(X)ubuntu clean install? Sure, some things can **not** be avoided. Some can.

I'm not talking about who's at fault. I'm asking what are we going to do about it? 

I hope you don't think theses things are promoting open software while compared to the lesser of (worse non-open) evils, otherwise. People tend to go with the devil they know. It matters. What is it about these problems that encourages a (major paradigm shifting) change from the status quo? These cons must be stopped; like a cancer. They can not be left to their own way or we will die. We may have to take extraordinary actions.

Of course I agree too. Windows has many other cons and they are all too easy to forget. People better serve themselves when they research, weigh **all** real pros and cons and compare(for themselves). **That's why a really easy dual boot installer(on same hardware), is important. Also, why our comparative (to XP tweaked) memory requirements should always be less.** Guess what? 75% of all mankind is not technical. Thus, they are not going to do that. They will not likely become computer nerds. Of us that are technical, it still wastes our time. We are **WAY** past geek elitism. I respectfully suggest, we tread lightly.

**When** we do get a larger amount of the non-technical population to use open software and after all the FUD is exposed, time savings will be the (wise and honest) judge and measure, from their experiences. Business users, especially. Time saving computing, is the universal and paramount positive that almost every newbie and guru alike, share. I kinda' though that's what (K)Ubuntu is all about?

So march on. Yet do so, respecting other peoples time.

---

