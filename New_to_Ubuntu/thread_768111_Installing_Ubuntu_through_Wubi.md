---
title: "Installing Ubuntu through Wubi"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by h8uthemost on 2008-04-26
Hey guys,

This is my first experience with Ubuntu. So please keep in mind that I have absolute NO knowledge with this OS yet. So if you can explain things to me as clearly and detailed as possible, then that would be great.

So, yesterday I installed Ubuntu 8.04 through Wubi. Or with Wubi(still not exactly sure what Wubi is). Now, I installed Ubuntu through Wubi because I was told that it would be an easier install for a first timer. Which it was extremely easy.

But...I cannot access any of my files on Windows(I have Windows XP Home). The tutorial that I read that told me how to install Ubuntu through Wubi, told me that they could not access all their Windows folders and files too. But, whoever wrote that tutorial was doing an install of Ubuntu 7.10, so I was hoping this problem would have been fixed for 8.04. But it wasn't. I can't access anything on my Windows side.

So, is there a fix for this? Or, am I going to have to un-install Ubuntu and re-install through a dual boot configuration?

I first checked out Ubuntu through a Live CD, to see if I would like it. And through that Live CD I was able to see and access all the files on Windows. So would I be able to see and access all the file on Windows through a dual boot config?

I have no problem with doing a dual boot config. I only did the installation through Wubi because it was suppose to be easier. But, if it's better to do a dual boot config, then I would rather do that.

So yeah, that's about all my problems. Besides that, I'm loving Ubuntu, and I definitely want to keep on using it.

There is one more small question though. I would like to install Compiz Fusion also. But, when I got to the Compiz Fusion website, and click on Ubuntu as my OS, a bunch of Compiz Fusion downloads pop up. And I have no idea which one to get. So if anyone could shed a little light on this, that would be a huge help.

Well, thank you for any info or help. I will greatly appreciate it.

Thank you.

Oh...one more thing. When I installed Ubuntu through Wubi, the Ubuntu folder on my C: drive(Windows side) took up a whopping 15GB of space. Is this correct? I thought I've read that Ubuntu only needs about 4GB or so of space. So why did it take up 15GB?

Ok, that's all of my questions. Thank you for any and all help

EDIT: Ok, so I'm following the tutorial here for Compiz Fusion. And I'm starting to get some cube effects. I'm not all the way through the tutorial yet. But I think this pretty much answers my questions for Compiz Fusion.

---

### Post by c4v3m4n on 2008-04-26
The last time you logged out of windows did you let it shut down properly?  Sometimes if you shut it down improperly linux isn't able to access it.  Try booting up in windows and shutting down safely.  Other than that I can't think of any other reason you wouldn't be able to get to your windows files.

---

### Post by h8uthemost on 2008-04-26
Oh yeah, I always get out of Windows properly. Or at least I think I do. When I get out of Windows to get into Ubuntu, I click on Turn Off Computer then click Restart. Then I let the computer reboot then I pick Ubuntu.

Somebody told me to access my Windows files I need ntfs-3g:

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

So I'll try that. Thank you for the help.

What about Ubuntu taking up 15 gigs of space though. Is that normal?

Thanks.

---

### Post by h8uthemost on 2008-04-26
Sorry for the double post. But I'm going to go ahead and do the dual boot, but I needed to ask a quick question.

I'm using the ubuntu-8.04-desktop-i386.iso file. This is the same file I used to install Ubuntu through Wubi. So, I can also use it to do a dual boot install too, right?

Once I pop the disk into the drive, and the options menu comes up, instead of pressing the Install inside Windows option, I should choose the Demo and Full Installation option? Then just follow [_this_](https://help.ubuntu.com/community/WindowsDualBoot) tutorial from after that?

Thank you for any help.

---

### Post by eriqjaffe on 2008-04-26
Assuming you installed Wubi on your C: drive, just look at /host in your file manager.  Other drives should be automatically mounted in /media.

---

### Post by h8uthemost on 2008-04-26
I did install on my C: drive. And I'll look where you mentioned to see if I can access my files.

But I still gotta do a dual boot since Wubi took up 15gb's of space. And I keep getting told that's not normal. So would you recommend uninstalling and doing another install with Wubi, or uninstalling and doing a dual boot?

Thank you.

---

### Post by eriqjaffe on 2008-04-27
I don't **think** 15gb is abnormal, I'm running through Wubi right now, and it's taking up 30gb on my C: drive.

---

### Post by madjr on 2008-04-27
> **h8uthemost said:**
> I did install on my C: drive. And I'll look where you mentioned to see if I can access my files.

But I still gotta do a dual boot since Wubi took up 15gb's of space. And I keep getting told that's not normal. So would you recommend uninstalling and doing another install with Wubi, or uninstalling and doing a dual boot?

Thank you.

[IMG]http://wubi-installer.org/images/wubi.png[/IMG]

how many space did you typed in for ubuntu.

I typed in 10 gb and it only took exactly 10

---

### Post by h8uthemost on 2008-04-27
I left the Installation Size as default. And I don't remember how much the default was set at.

I was just reading the Wubi Wiki, and it said the minimum size requirement is 5gb. Now that I would like. So I would be ok with setting the Installtion Size to 8gb?

Does a dual boot require less space?

Thanks for the help guys.

EDIT: By the way, thank you for letting me know about /host and /media. I found all my Windows files now.

---

### Post by eriqjaffe on 2008-04-27
A dual-boot won't take up any less space than a Wubi install, but you need to partition your hard drive instead of just having a big virtual disk file hanging around.

---

### Post by h8uthemost on 2008-04-27
Yeah, I know about partioning the hard drive for a dual boot. You mentioned that you're Ubuntu is taking up 30gb. Don't you think that's huge for an OS?

I'm really tweaking Ubuntu now to make it my own. So I would kind of hate uninstall and see if I can lower the Installation Size, to see if it will take up less space, and lose all my customizations. But 15gb is huge to me. 

But if this what others are saying that Ubuntu is taking up for them, then I guess there's nothing I can do about it. Just a friend told me that Ubuntu is taking about 4gb for him. And I would love to get it down to that. Of course, he only uses Ubuntu. No Windows, no dual boot, nothing like that. It's his one and only OS. So I wonder if that has something to do with it?

---

### Post by eriqjaffe on 2008-04-29
Well, it's not like Ubuntu is **using** all 30gb of the Wubi file, there's plenty of blank space.  Wubi needs to create a loopback "virtual partition" of a fixed size, and that's where that 30gb figure comes in.  Right now, my setup is uing 8.14 gb out of 26.58gb usable space (the rest of the 30gb is being used by boot & swap).

My laptop's is using about 4gb because it was a command-line install, so there's a lot less stuff there.

---

