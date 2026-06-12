---
title: "can't login on iMac G3 - new install"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by peterkeltie on 2008-06-28
Hello everybody!

Am new to Ubuntu, and although my old iMac G3 233 computer has got Ubuntu installed on it, the screen goes blank when it boots up. I am aware of the xorg.conf issues, but my trouble is that I can't login to make the changes.

It says "G3 login:" whenever I try to enter the "sudo..." commands, and then asks me for a password, which never works.

I've tried using ubuntu for a username and password, or blank, or any combinations of those for either the username or password, but having no luck.

I've been searching for hours for a solution, so if anybody knows how to solve it, I would be really really grateful. Otherwise, I will just have to install ubuntu all over again (or Xubuntu as other people have recommended) which took just over 2 days.

Thanks in advance for any help which may come my way.

Cheers,

Pete

---

### Post by 3rdalbum on 2008-06-28
How did you install Ubuntu? Through the Alternate Disc, or the Desktop CD?

With the Alternate Disc, you must use a normal basic installtion - don't choose "Advanced Settings". If you get asked to set a root password, then you've chosen the Advanced settings. Sorry I can't remember exactly how this is determined or what the actual name is - it's been a good two years since I've done it.

If you were given the option to set a root password in the alternate disc, then all commands beginning with "sudo" will fail in the installed system.

No matter which way you installed Ubuntu, you will always be asked to set up a username and password for your normal user account. At the "G3 login:", type the username and press Return. When it asks for the password, type the password (it will not appear as you're typing it) and press enter. THEN put in your sudo command.

---

### Post by peterkeltie on 2008-06-28
Thanks for quick reply!

I used the alternate disc, and just did the basic settings (not the advanced). I did create a username and password (which it specifies is just a normal non-admin account) but these aren't working. The password isn't a hang-up from the previous Mac OS password is it?

A few lines up from where it says "G3 login" it has Ubuntu 8.04 G3 tty1. Does this mean anything?

If this doesn't work, then I will just try reinstalling completely from scratch. And try Xubuntu this time.....

Cheers again.
/Pete

---

### Post by 3rdalbum on 2008-06-28
The password has nothing to do with the Mac OS password.  I really don't have any idea why your username wouldn't work. I know that some people get confused when they start typing their password and nothing comes up; that's all perfectly normal.

The string you've just told me about only tells me that you're running 8.04, that your computer's name (hostname) is G3, and you pressed Control-Option-F1 to get to the terminal :-)

How much RAM does your computer have? Xubuntu requires 128 megabytes of RAM and Ubuntu requires 256; I know those computers came with 32 megs, so you'd have to have had a RAM upgrade at some point in time to even get this far.

I'm not entirely sure, but I think there should be an option with the Xubuntu Desktop CD to boot directly into the graphical installer. At the yaboot prompt, press Tab, and that should hopefully show you an option you can type to do this. This might be quicker and easier, and hopefully might work where your previous installation has failed :-)

---

### Post by peterkeltie on 2008-06-29
Am reinstalling everything again, and will make sure this time that I don't do the expert install (although I don't think I did last time either). If that doesn't work, then will try Xubuntu, along with your other suggestions.

Not entirely sure about the RAM. I saved it from being thrown out to have a little test-drive of linux before making the switch on my normal XP machine. I thought that using the alternate CD would get around the low memory possibility. If it does only have 32MB, any suggestions of a distro that could work?

And many thanks again for your helpful replies!

---

### Post by Elfy on 2008-06-29
While I haven't actually used it myself so can't vouch for it - there appear to be a lot of recommendations for dsl 
[http://distrowatch.com/table.php?distribution=damnsmall](http://distrowatch.com/table.php?distribution=damnsmall)

This page might also be worth a look
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

