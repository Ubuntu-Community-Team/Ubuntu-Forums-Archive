---
title: "Intel 855GM Graphics Help Plz"
date: 2012-03-12
forum: New to Ubuntu
---

### Post by bipolaric on 2012-03-12
Hello Everyone,

I have dabbled with Linux 'briefly' over the years, going back and forth from one distro to another, then windoze, then back again, 'you get the picture.  'Thing is, I 'really' like linux, especially Ubuntu and Kubuntu.  I always used to be sh*t scared of the terminal, and even now I am still limited to 'copy' & 'paste', and yet, as always, I have hit a snag.  But rather that tuck my tail between my legs, and run for cover.  I 'WANT' to stick with Ubuntu, besides, my new Laptop is rather crappy, and I really need some help.  I am having a problem with my Graphics driver, (intel) to be exact, and from what I have read online, there are stability issues.  I will give you the Laptop spec..1.4Ghz Celeron M / 736mb RAM / intel855GM 32mb intergrated graphics........Here is the problem....When I go into System/Preferences/Appearance/Visual Effects, The options to choose are: None / Normal / Extra...I am on 'none', when I try to pick 'normal' it seems to do a search, then the screen judders, goes off, then on again and finally lets me know that these Effects can not work, even on normal.  I have searched the internet, and it is all very confusing, basicly I need someone to 'spoon feed' me how to get my intel 855GM graphics to work properly, Someone 'Pleeeeeaaaaaase' help me.

Thanks - Mark - (Ubuntu 10.10 - Maverick Meerkat)

---

### Post by 2F4U on 2012-03-12
Not sure if that helps, but at least the article has some starting points in it:

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

---

### Post by bipolaric on 2012-03-12
Hi, thanks for the Reply.

This may sound really stupid, but I know 'nothing' about linux, but I 'want' to learn.  Do I create launcher, create document, or create file, if none of those things, then what ?  And as for the section 'device', do I have to 'choose' a device from a list somewhere, or do I just write it down in a document 'word for word' and save it somewhere.  I know I may seem really backwards here, but I'm not ignorant, I'm just stupid lol.

I'm afraid I need spoon feeding, sorry.

Thanks Again - Mark

---

### Post by Mark Phelps on 2012-03-12
You will need to create the files indicated, with the content indicated, in the linked thread.  The program you use to do that is known as "gedit", and since the files are system-related, you will need to be super-user to create and edit them.

So, for example, to create the file "contents.txt" and have it saved in the directory /etc/folder1 ... you would enter the command:

sudo gedit /etc/folder1/contents.txt

This will open an editor session, where you type in the contents that were in the linked thread.

After you create and save each file, you need to restart Ubuntu, since it will reread those files during startup.

---

### Post by mastablasta on 2012-03-12
first off you owuld be better of upgrading to latest verison 11.10 as it has newer drivers. if oyu odn't know how to do that then use a PPA to get newer drivers. they are called x org edgers.

next why do you assume your card should support full #D acceleration? and what is wrong if you do not have any special effects? i certainl ydo not need them. the only usefull effect i found in Kubuntu where on mouseover i get the preview of the runnin applicaiton, but that's about it.

---

### Post by bipolaric on 2012-03-12
If I installed 11.10, I would want to remove 'Unity' because I don't like it.  Some love it, some hate it.  It's just not for me, but........

1.4Ghz Celeron M
ONLY 736mb RAM
Poor intel Gfx

Will 11.10 run on my old Laptop ?  And can Unity be removed at all ?

Please let me know - Thanks Again - Mark

---

### Post by UltimateCat on 2012-03-12
Bipolaric:
   Hi:
When you get a chance open a terminal and type:
```
lspci

```
This is a command for displaying info about all PCI buses in the system and all devices connected to them.  Useful when you want to diagnose problems or when you want to report bugs related to PCI devices.

Once you find out what graphic's card you have you may need to download and install a driver specifically for your card to aid it.

The manufacturer that designed your card should have a website and drivers to accommodate your cause.

Also you may want to share if you are working with a laptop or a desktop pc and I say that because the discrete vs. integrated circuitry inside the computer is a little bit different. With the integrated circuitry the adapter shares the RAM and requires the motherboard and chipset's communication with the interface.

These books are very helpful to a Linux user and I recommend them as they have saved me a lot of time and energy.
Reference's
"Upgrading and Reparing Pc's" By: Scott Mueller    (local library)
"Ubuntu Linux Bible" By: Wm. Von Hagon

Hope this helps

---

### Post by anewguy on 2012-03-12
The 855 has always been problematic with Ubuntu, perhaps Linux in general.  There are MANY posts on this if you search the forum.  I've been involved in several of those discussions.  Don't expect much, and you won't be disapointed.......

dave ;)

---

### Post by Mark Phelps on 2012-03-13
> **bipolaric said:**
> If I installed 11.10, I would want to remove 'Unity' because I don't like it.  Some love it, some hate it.  It's just not for me, but........

1.4Ghz Celeron M
ONLY 736mb RAM
Poor intel Gfx

Will 11.10 run on my old Laptop ?  And can Unity be removed at all ?

Please let me know - Thanks Again - Mark

You make valid points ... that folks pressing you to upgrade have missed ...

With that PC, I would not expect good performance with the 11.x Ubuntu versions, primarily due to the graphics demands of Unity.

I don't know about "removing" Unity, but there are ways to get the Gnome Classic desktop back -- which should help you a bit with the performance.

---

### Post by mikewhatever on 2012-03-13
Desktop effects don't work well on old Intel GPUs, and are, therefore, disabled.

Installing Ubuntu 11.10 and then removing Unity is unnecessary work. I'd recommend trying Xubuntu 11.10 instead. It's more lightweight, and doesn't have Unity.
[http://xubuntu.org/](http://xubuntu.org/)

---

