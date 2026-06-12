---
title: "How to replace Ubuntu with Kbuntu"
date: 2018-12-28
forum: New to Ubuntu
---

### Post by krikorr on 2018-12-28
I'm a 78 yr old refugee from Win 10 and find ubuntu difficult to adjust to.  For me, a casual user, it's like early versions of windows where I had to go to DOS command line  to get anything done.
I would like to replace ubuntu w Kbuntu which I understand has a more window-like interface.
How would I go about doing that?  
Is there a simple way to create a USB install stick and boot the PC from the USB port?
Once kbuntu is installed, how do i remove ubuntu?

Sorry for the basic questions.
Grateful for any help.

Happy New Year

---

### Post by yetimon_64 on 2018-12-28
You could replace ubuntu fully from a usb, but if you already have ubuntu installed adding kubuntu is as simple as one command in the terminal
```
sudo apt install kubuntu-desktop
```
Doing this will add a session for kubuntu that can be accessed from the log in screen.

Once you install kubuntu desktop, at the log in screen there is an icon beside where you would enter your password, if I recall correctly it is a "cog" symbol. Click it and change the desktop session to kubuntu. The log in screen will remember this selection for all future boots and will log you into kubuntu.

I don't use kde/kubuntu here but have many desktop environments on this particular install for eg.
```
yetiman:~ $ ls -C1 /usr/share/xsessions/
cairo-dock.desktop
gnome-classic.desktop
gnome.desktop
gnome-fallback-compiz.desktop
gnome-fallback.desktop
i3.desktop
i3-with-shmlog.desktop
mate.desktop
openbox.desktop
ubuntu.desktop
ubuntustudio.desktop
xfce.desktop
xubuntu.desktop
```
My preference generally is to use the xubuntu session but on occasions I will choose to boot into unity, gnome, i3 or mate, but also have the option to use much lighter desktop environments like openbox or cairo dock etc.

If as your post here suggests you are new to ubuntu and linux I'd suggest you only install one extra DE, KDE, and switch to logging into it and leave ubuntu as is. Be careful adding too many DEs as they can mess up your menus and cause some confusion with the many options each DE can add. Adding only the one extra DE should not cause too many problems for you.

> Once kbuntu is installed, how do i remove ubuntu?
I would suggest you leave it in place, there is no need to remove it if you use this option of adding a Kubuntu session. Trying to remove it can cause serious problems or leave your install in a mess. You will be able to choose either Kubuntu or Ubuntu (you may wish to learn ubuntu later on as you become more familiar with your Linux system).

If you must remove ubuntu totally do a completely fresh install of kubuntu from a usb stick and overwrite your previous ubuntu installation with the Kubuntu installer.

---

### Post by Topsiho on 2018-12-29
I agree fully with yetimon_64's answer. It's a bit complicated by mentioning all kinds of desktops, but the instructions are clear.
This answer also makes clear that the command line is not a setback for Linux, it's a very powerful tool, making Linux far superior to some other operating systems that teach you not to use it.
But it's true. There are very easy calculators, with which you can only do some basic stuff, as +, -, / and x. And there are wonderful, powerful calculators, using RPN, with which you can do the most expert calculations, but need some time to get used to. But you need not do these expert calculations. You can still do the basic stuff.
But having RPN is already a big boost to doing calculations the easy, less error prone way!
I am almost 80 years old :)

Topsiho

---

### Post by SeijiSensei on 2018-12-30
I would install Kubuntu from scratch.  

If your hard drive has a reasonable amount of free space, I'd create a new partition for Kubuntu. Then you can choose between the flavors at boot.

---

### Post by Topsiho on 2018-12-30
Yes, that's OK. For a final install.

I think however that installing several desktops (flavours?) first is a good idea just to try them, and see what is the best one for you (the OP I mean :) ).
And after that install the one you like best. Might not be Kubuntu.

My twopence,
Topsiho.

---

### Post by jdeca57 on 2018-12-30
Reading this thread I wonder if adding desktops like kubuntu or xubuntu have any impact on stability or speed. OK, there is more disk space used and security updates may be more frequent but once you boot into a flavor you only use the resources of the variant selected. Unless you remove software there seem to be no obvious negative consequences. An interesting tip, or am I missing something?

---

### Post by Topsiho on 2018-12-30
Hi jdecas57,

It's not a great Idea to run several desktops on the same computer, especially a mix of Kubuntu and Gnome desktops. So I've read.
In my experimental years I did nothing else, with no adverse effects, only I was more often than not put up with the logscreen of the last install in othe desktops.

But when you are experimenting this is not so bad, and it is the reason that I wrote to install the one you like best. Probably I was not clear enough that I meant: as the only desktop.

I use Ubuntu, now with the Gnome desktop, and some KDE software, such as KStars. Which runs perfectly. I could go back to Unity, which is much more refined, though that maybe the effect of having used that for years.

Hoop dat ik uw vraag hiermee heb beantwoord :)  (hope this is the answer you want).

Topsiho

---

### Post by jdeca57 on 2018-12-30
Hi Topsiho,

It's obvious that less software means more stability but I see that t (he second reply to this thread (yetimon_64) seems to have no problem mixing desktops (but he uses no KDE). Since I have the opportunity to use more than one (cheap) laptop I will do some experimentation, but of course I won't report failure. One can always reinstall... :-)

Bedankt voor je antwoord. (thanks)

jdeca57

---

### Post by vidtek on 2018-12-31
> **krikorr said:**
> I'm a 78 yr old refugee from Win 10 and find ubuntu difficult to adjust to.  For me, a casual user, it's like early versions of windows where I had to go to DOS command line  to get anything done.
I would like to replace ubuntu w Kbuntu which I understand has a more window-like interface.
How would I go about doing that?  
Is there a simple way to create a USB install stick and boot the PC from the USB port?
Once kbuntu is installed, how do i remove ubuntu?

Sorry for the basic questions.
Grateful for any help.

Happy New Year
Krikorr-  from a youngster of 68 years-

The post from SeijiSensei post number 4 is what I would recommend.
You want the most windaz like experience?  Then KDE with the plasma shell is windaz plus plus.  It is more resource-hungry than most other distros, but with modern hardware should not be a problem.  I have been using kde for years now and it does everything windaz does and more.
The only things windaz trumps it at are some adobe apps, such as video editing and gaming.  If you don't care about those, then you need have no fear of changing.

Do NOT install multiple desktops as others have suggested, therin lie dragons!  As a newbie you will get burned if you do.

A clean fresh install of Kubuntu is what you need, then add your apps as required.  You can create a bootable install usb stick from windows, use a programme called Rufus to do it.  
You will need to access your machine's bios to disable secure boot (for windows) and enable booting from a usb stick.  I would choose an efi boot for future-proofing.
Use a separate physical boot and operating system drive, cheap ssd's are around for $30 or so, you only need a max 250gb drive get 2 to make it easy to pop the other in when you stuff up (and you will again and again, we all do).
When partitioning your drive, do a manual one, and create a root / partition of about 70gb and a ~/ home partition with most of the rest.  That way you will still have all your settings preserved across multiple installs.  ENSURE THE BOOT DRIVE IS THE SAME ONE AS THESE TWO.  The nomenclature linux uses is slightly different to Windaz.  eg. sda, sdb, sdc etc instead of hd0, hd1 etc.

One thing to remember everything in linux is a file, literally.  There are no databases with registry settings that are difficult to access, it is totally file based.

I have a dual-port sata disc duplicator/clone device, it clones drives really fast and when I bork my machine I have the other on hand to replace it.  Then I just clone the good one again for when I do my next stuff-up!

I installed a quick-release 2 1/2 inch bay to my machine to make this very easy.  If you are on a laptop, forget the hardware suggestions.

This may sound like a lot of messing about, but once you get in the swing of it, you will have endless fun with it.  Keep coming back here for more help.

Tony.

---

### Post by CatKiller on 2018-12-31
> **jdeca57 said:**
> Reading this thread I wonder if adding desktops like kubuntu or xubuntu have any impact on stability or speed. OK, there is more disk space used and security updates may be more frequent but once you boot into a flavor you only use the resources of the variant selected. Unless you remove software there seem to be no obvious negative consequences. An interesting tip, or am I missing something?

There's no impact on stability or speed. You may end up with a text editor, music player, and file manager for each desktop environment you've got installed, which can get confusing. That's fine, though: you can have as many of those as you want. The only real issue is that the different desktop environments may fight over which one gets to show you the login window, since only one of those can be used at a time.

For experimental purposes it's fine to have lots of desktop environments installed. Once you've picked your favourite it is best to streamline that back by just installing the one you want to use, as already mentioned.

---

### Post by yetimon_64 on 2018-12-31
> **CatKiller said:**
> ...The only real issue is that the different desktop environments may fight over which one gets to show you the login window, since only one of those can be used at a time....
I'd forgotten that kde uses its own login manager when answering earlier; this complicates the issue a bit more than I'd first thought about. Especially as the OP seems to be a fairly new starter in Linux.

@ OP, I now think the suggestion from SeijiSensei is the way to go for you; A fresh install from scratch. You then won't have to deal with extra programs from each DE showing in the menus and other such issues with multiple DEs.

---

