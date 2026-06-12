---
title: "Can I take over a 14.04 LTS install?"
date: 2015-03-08
forum: New to Ubuntu
---

### Post by jack127 on 2015-03-08
I recently acquired an Acer Aspire One with 14.04 LTS installed and working fine. 

I have never used Linux or Ubuntu, I am a old and long time Windows user and comfortable with using DOS if I have to.  

Ubuntu has one user that I do not know the password for and I would like to remove that user.  

And I want to add a new user for myself.  I can log in a a guest now.  

I can't add or remove a user from the Settings > Users menu, it is lightly grayed out as I look at it.  

If there is a thread or tutorial for doing this I cannot seem to find it, any help is appreciated.  

[COLOR=#ff0000]Added note - 10 March 2015[/COLOR]

To cut to the end of this thread, I was convinced by the experts here that it is probably not a good idea to take over an existing linux instalk but to do a new install instead.    So in the end I installed kbuntu 14.04 LTS and have a that up and running now!  

Jack

---

### Post by Bashing-om on 2015-03-08
jack127; Hi ! Welcome to the forum.

It is not so easy to make up a new user with the required administrative abilities. The admin of the system is set when the operating system is installed. Though a new admin account can be done, it is no easy feat.
Would you settle for changing the password so "you" have access ?
see:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Then as you learn the system, you can make any changes you desire.

[INDENT][INDENT]it is a thing
[/INDENT][/INDENT]

---

### Post by danne33 on 2015-03-08
> **jack127 said:**
> I recently acquired an Acer Aspire One with 14.04 LTS installed and working fine. 

I have never used Linux or Ubuntu, I am a old and long time Windows user and comfortable with using DOS if I have to.  

Ubuntu has one user that I do not know the password for and I would like to remove that user.  

And I want to add a new user for myself.  I can log in a a guest now.  

I can't add or remove a user from the Settings > Users menu, it is lightly grayed out as I look at it.  

If there is a thread or tutorial for doing this I cannot seem to find it, any help is appreciated.  

Jack

I strongly recommend you to make a fresh install. You will learn a lot from that.
It is really easy! Here is a good guide and the installation is done in no time:
[https://elabualg.wordpress.com/2013/10/22/dual-boot-ubuntu-and-windows-8-uefi/](https://elabualg.wordpress.com/2013/10/22/dual-boot-ubuntu-and-windows-8-uefi/)
Just jump to Ubuntu Installation, if you don't want to have dual boot.

---

### Post by sammiev on 2015-03-08
I would do a fresh install as you have no idea what was left behind from the other owner. It would be a great learning curb or it may just work with the new install right out of the box.

---

### Post by dino99 on 2015-03-08
if your laptop have an usb port, then do an install via an usb stick an the mini.iso (you might want to format the whole disk first (with gparted for example)

note: find all the help you need by clicking then browsing the link below.

---

### Post by newb85 on 2015-03-08
As has been said, a fresh installation is strongly recommended.  The tutorial for resetting a password by Psychocats will work, but only if the last user didn't encrypt their /home directory.

You can't add or remove accounts unless you're logged in to an account with admin privileges.  Also, without admin privileges, you can't install or remove software or updates.

If you're looking at Ubuntu as the sole OS, then reinstalling should be very easy.  (The tutorial linked by dane33 isn't the best reference in this case.)

1. First, go to ubuntu.com/download/desktop and download the iso image.  (If you prefer to use torrents, the options are there, and Ubuntu has a bittorrent client installed by default.)

2.  Use Startup Disk Creator (also installed in Ubuntu by default) to create bootable install media from the .iso you just downloaded.  It will need to be a DVD or empty USB drive with at least 1GB space.

3.  Boot from the installation media.  Usually there's a function key (liike F2, F11, F12) you have to hit at your machine's splash screen (yours probably says acer) to select the boot device. The splash screen should tell you what key it is, but if you're like me, you'll have to try a few times, because it's too fast to read it and respond in time.

4.  Follow the wizard to install Ubuntu.  You will be using the entire disk.  You don't need to do anything fancy or complicated.

5. Post any questions you have to the forums. :)

---

### Post by jack127 on 2015-03-08
OK, I've fumbled around with the password reset thing from here:

I forgot my password! - [https://help.ubuntu.com/14.10/ubuntu-help/user-forgottenpassword.html](https://help.ubuntu.com/14.10/ubuntu-help/user-forgottenpassword.html)

and I tried the one from Bashing-om's link too, it is a better and more informative link for sure.  

How to reset your password in Ubuntu - [www.psychocats.net/ubuntu/resetpassword](www.psychocats.net/ubuntu/resetpassword)

But I can't seem to get that to work either.  I am getting to the recovery command prompt mode with a prompt that starts with ~# but it does not seem to like most of the command entries and either does nothing or regugitates the help screen for the commands.  

So I'm going to give up on saving it and try the USB stick install.   

Thanks again, I'll leave this thread active for now and still monitor it though.  

Thanks for the help!

Jack

---

### Post by sammiev on 2015-03-08
> **jack127 said:**
> OK, I've fumbled around with the password reset thing from here:

I forgot my password! - [https://help.ubuntu.com/14.10/ubuntu-help/user-forgottenpassword.html](https://help.ubuntu.com/14.10/ubuntu-help/user-forgottenpassword.html)

and I tried the one from Bashing-om's link too, it is a better and more informative link for sure.  

How to reset your password in Ubuntu - [www.psychocats.net/ubuntu/resetpassword](www.psychocats.net/ubuntu/resetpassword)

But I can't seem to get that to work either.  I am getting to the recovery command prompt mode with a prompt that starts with ~# but it does not seem to like most of the command entries and either does nothing or regugitates the help screen for the commands.  

So I'm going to give up on saving it and try the USB stick install.   

Thanks again, I'll leave this thread active for now and still monitor it though.  

Thanks for the help!

Jack

Make sure you post back with the results of a fresh install. :)

---

### Post by newb85 on 2015-03-08
> **jack127 said:**
> I am getting to the recovery command prompt mode with a prompt that starts with ~# but it does not seem to like most of the command entries and either does nothing or regugitates the help screen for the commands. 

That's another problem with not doing a fresh install.  You don't really know what all customizations the last user put into it.  If they changed shells, and added/removed a lot of command line utilities, you're left with a system that doesn't respond the same when you're trying to follow tutorials like that.

---

### Post by jack127 on 2015-03-08
> **sammiev said:**
> Make sure you post back with the results of a fresh install. :)

Wow!  The reinstall was pretty much a no brainer all things considered.  

In the course of fumbling around to get booted from a USB slot for a new install.  I had some trouble with figuring that out and getting it to boot from the micro SD card reader in one of the USB slots.  Eventually I found this page and created what is called, I think, a Linux Live USB Key.  

 [http://www.linuxliveusb.com/help/guide/using-lili](http://www.linuxliveusb.com/help/guide/using-lili)

I got the Aspire One booted off of the USB Key then used that to reformat the drive and install 14.04 LTS.  I got the wi fi connected for the install and the Linux Live USB key found all the drivers and got every thing working all by it self.  

Now I just have to study this a little bit and figure out what and where everything is.  I am happiest with XP and the Windows Classic menus and desktop.  I just need to figure out how similar things can be made to happen with this GUI.  

Thanks again for the help and encouragement!  

Jack

---

### Post by Bashing-om on 2015-03-08
jack127; Great !

spice is nice and viva le difference for different desktops.
> 
Now I just have to study this a little bit and figure out what and where everything is. I am happiest with XP and the Windows Classic menus and desktop. I just need to figure out how similar things can be made to happen with this GUI. 

for an XP equivalent check out the mate desktop.

[INDENT][INDENT]welcome to our world
[/INDENT][/INDENT]

---

### Post by sammiev on 2015-03-08
> **jack127 said:**
> Wow!  The reinstall was pretty much a no brainer all things considered.  

In the course of fumbling around to get booted from a USB slot for a new install.  I had some trouble with figuring that out and getting it to boot from the micro SD card reader in one of the USB slots.  Eventually I found this page and created what is called, I think, a Linux Live USB Key.  

 [http://www.linuxliveusb.com/help/guide/using-lili](http://www.linuxliveusb.com/help/guide/using-lili)

I got the Aspire One booted off of the USB Key then used that to reformat the drive and install 14.04 LTS.  I got the wi fi connected for the install and the Linux Live USB key found all the drivers and got every thing working all by it self.  

Now I just have to study this a little bit and figure out what and where everything is.  I am happiest with XP and the Windows Classic menus and desktop.  I just need to figure out how similar things can be made to happen with this GUI.  

Thanks again for the help and encouragement!  

Jack

You can try a few flavors using a USB to find the right one for you. As posted by Bashing-om there is Mate as well.

---

### Post by jack127 on 2015-03-09
The Mate desktop looks like the one I want to use for sure.  I have downloaded an iso file, ubuntu-mate-14.10-desktop-i386.iso, and now I just have to figure out how to make the changeover.  

If I understand it right, I am using the Unity desktop now and want to change that to the Mate desktop?  Is that right?

This is a little bit complex for a newbie, is there an easier way to do it?  

[http://wiki.mate-desktop.org/replace_unity_by_mate](http://wiki.mate-desktop.org/replace_unity_by_mate)

If there is a ubuntu install package with Mate already incorporated into it, I can always do the install again...  

Jack

---

### Post by dino99 on 2015-03-09
one of my favorite app is 'synaptic' for installing and getting info (changelog) about the packages. Install it then use it.

sudo apt-get install synaptic  && sudo synaptic

then you will find (search top field) mate-desktop; install it and thats all (search for previous install ubuntu-desktop in case , and purge it (right-click)

---

### Post by SeijiSensei on 2015-03-09
I'd just install Mate from scratch rather than trying to add it to an existing Ubuntu version.

You might want to give [Kubuntu]("http://www.kubuntu.net/") a look as well; it's more "Windows-like" than some other desktop environments.  ISOs are here: [http://cdimage.ubuntu.com/kubuntu/releases/14.04.2/release/](http://cdimage.ubuntu.com/kubuntu/releases/14.04.2/release/)

---

### Post by MrSteve on 2015-03-09
if you are looking for a system that looks similar to windows please try kubuntu 

its a member of the Ubuntu family but uses the KDE desktop environment 
the LTS (long term support) has 5 years of support

[http://www.kubuntu.org/getkubuntu](http://www.kubuntu.org/getkubuntu)

---

### Post by jack127 on 2015-03-09
Dang!  You guys keep coming up with more and better ideas!   

But I am thankful for that!  

I think Kubuntu is the best choice for me now!

Jack

---

### Post by sammiev on 2015-03-09
> **jack127 said:**
> Dang!  You guys keep coming up with more and better ideas!   

But I am thankful for that!  

I think Kubuntu is the best choice for me now!

Jack

You will be a Dist hopper here soon. LOL

---

### Post by Bashing-om on 2015-03-09
jack127; Big smiley .

> **jack127 said:**
> Dang!  You guys keep coming up with more and better ideas!   

But I am thankful for that!  

I think Kubuntu is the best choice for me now!

Jack
As you are beginning to perceive there are lots of options;
Hang in there, get your feet wet, and in time you will know what your options are.

This is 'buntu
[INDENT][INDENT][INDENT]it is all about choice
[/INDENT][/INDENT][/INDENT]

---

### Post by jack127 on 2015-03-10
OK, I now have kbuntu 14.04 LTS up and running.  I'm going to describe that process for doing that briefly just in case it might help someone else...  

1 - From Windows XP I [downloaded the Linux Live USB Creator]("http://www.linuxliveusb.com/en/help/guide/preparation") (LiLi for short) app and installed that.  

2 - I put a USB memory stick in a USB port, ran the LiLi app and it created a bootable USB key.  As I created the key I choose for it to use a previously [downloaded kubuntu-14.04-desktop-i386.iso image file]("http://cdimage.ubuntu.com/kubuntu/releases/14.04.2/release/kubuntu-14.04-desktop-i386.iso").  

So  that is the version of Linux that the key will boot to.  And the key will install that version too if you choose to have it do that.  

3 - I set the Aspire One to boot from USB HDD and booted to a kbuntu desktop from the LiLI USB key.   

4 - From the kbuntu desktop I enabled the Aspire's wifi connection.  

5 - Then I chose to install that kubuntu version I had booted to the Aspire One hard drive.  I  

had the option of play with the partitions and but elected to just overwrite the entire drive and give the kubuntu the entire drive.  

6 - After the install was complete I shut down the Aspire One, removed the LiLi USB key, and restarted to find kbuntu 14.04 LTS alive and well.  

When I got to the kbuntu desktop I got a notice about updates and kbuntu then commenced to start updating itself and virtually all of the installed along with it apps.  That has been going on for some time now and I'll just let it go until it finishes.  

So now I'm ready to begin as a kbuntu linux user.  It won't be too hard I think, I am already a user of firefox and thunderbird and some of the other apps there.  But I have to say that the kontact app (email, contacts, and a lot more) sounds like it will be worth trying.  

Is the use of an anti-virus app recommended with linux?   I don't seem to hear much about that here.  I have been using a Norton AV and/or IS app for some years so those being abset here has been noted

Jack

---

### Post by SeijiSensei on 2015-03-10
Anti-virus is pretty useless on a Linux box.  Most viruses are written for Windows.  There are a few "viruses" for Linux, but they are rare and not widely disseminated. You might take a look at:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

I use [ClamAV]("http://www.clamav.net/") on servers, but that's largely to scan incoming email for attached malware.  I haven't used an anti-virus program of any sort on a Linux desktop for two decades with no ill effects.

---

### Post by mikodo on 2015-03-11
Hi Jack. Welcome!

Since you asked about anti-virus apps, and that has been covered, I won't mention it again.

It is a good idea, to manage a firewall with any 'buntu, (your case Kubuntu). 

Follow[ this link]("https://help.ubuntu.com/community/Firewall"), to read about Firewalls in 'buntu. It looks intimidating but, really it can be very easy for newer/casual users too, using Gufw. There is a link on that page for it.

As you have questions on what rules to set in your firewall, start another thread about it, and I am sure the experts here, will help you with that too.

Addendum. Oh, Jack ... I just remembered that with my older install of 'buntu 12.04, I have had some problems setting and changing rules with Gufw, and have had to use ufw to do that. I don't remember if that is a common problem or not, or, if it has been corrected now for users of the 14.04 and later releases or not. Nevertheless, ufw is easy enough to use, if you have to, and the people here, are certainly well enough versed with it, to help you with that too. (just a little heads up for you).

---

### Post by SeijiSensei on 2015-03-11
Out of the box, Ubuntu desktops don't really need a firewall.  They have no open "ports" and no listening services that an intruder could connect to.  If you run an [nmap]("http://www.insecure.org/nmap") scan against a new Ubuntu desktop machine, you won't find any open ports.  If you install server programs like MySQL, you'll discover they are bound only to the "localhost" address of 127.0.0.1, which means they are accessible from the machine itself but not from outside.

---

### Post by mikodo on 2015-03-11
> **SeijiSensei said:**
> Out of the box, Ubuntu desktops don't really need a firewall.  They have no open "ports" and no listening services that an intruder could connect to.  If you run an [nmap]("http://www.insecure.org/nmap") scan against a new Ubuntu desktop machine, you won't find any open ports.  If you install server programs like MySQL, you'll discover they are bound only to the "localhost" address of 127.0.0.1, which means they are accessible from the machine itself but not from outside.
I apologize Jack!

The last thing I want is to do is start a flame-war, on this subject. I bow to SeijiSensei's experience and knowledge.

I do seem to hear, from experienced users, suggesting both a firewall and not.

I think, I will keep my mouth shut with support threads. There are lots of more knowledgeable people than I, to help out others.

---

### Post by SeijiSensei on 2015-03-11
That's just my opinion.  For a contrary view, read [http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177).

In terms of the issues that thread raises, I'm not very concerned about blocking outbound connections from my machine because I'm careful enough to know what's running and why.  I'm also not so concerned about browser compromises because the array of websites I visit is pretty mainstream.  I've been running Linux desktops from a variety of distros for years without a firewall on the machine itself.  I'd be a lot more concerned if I spent my time in random cafes and airline terminals where I'd be sharing a connection with many others some of whom may not have the best intentions.  At home where my desktop machine is behind two routers I don't feel the need for another firewall on the machine itself.

---

### Post by Bashing-om on 2015-03-11
My 2 pounds worth.
I migrated to (k)ubuntu in '04 from the horrors of XP, viruses and other malware, and the time and expense of dealing with them.
I took others advise at that time with some reservation in the realm of virus protection that none was needed in linux. So overwrought from the exertion of keeping that Windows machine clean, (k)ubuntu was a breath of fresh air. Yep in all this time running desktops with no thought what-so-ever about malware OR enabling any type of protection -> I have never once experienced a problem.

Now-a-days I do not even give it any consideration. Ports are closed, linux security policies are there, and they work !

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]life is good
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jack127 on 2015-03-15
OK, I am going to mark this question as solved.  And, for the record, the solution is to not try to take over a linux install but to install a new from version of linux instead.  

For me the final install was Kubuntu 14.04 and to run with the Kickstart desktop.  It has enough of the classic XP style look and feel and I am very comfortable with it.  

So thanks again for all the help I got here!  

Jack

---

### Post by Bashing-om on 2015-03-15
jack127; Outstanding !

Pleased that ya got here.

May I wish
[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

