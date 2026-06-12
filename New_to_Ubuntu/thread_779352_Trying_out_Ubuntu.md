---
title: "Trying out Ubuntu"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by I[AM]SMRT on 2008-05-02
I plan on reformatting my computer tonight and installing both XP and Ubuntu on it. If I like Ubuntu, I'll probably totally switch over (using Wine to run my XP only programs). However, I'm worried about a few things:

1) Installing drivers, I've got a Lenovo V100 laptop. They've got a driver page ([http://www-307.ibm.com/pc/support/site.wss/MIGR-64290.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-64290.html)). Will it be difficult to install these? And how would I do it?

2) Firefox profiles. I'm backing up my profile and I know how to reload my data for XP but how would I go about doing it for Ubuntu?

---

### Post by jken146 on 2008-05-02
> **'I[AM]SMRT said:**
> 1) Installing drivers, I've got a Lenovo V100 laptop. They've got a driver page ([http://www-307.ibm.com/pc/support/site.wss/MIGR-64290.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-64290.html)). Will it be difficult to install these? And how would I do it?
Very unlikely you'll need to do anything regarding drivers.  See what works straight away and go from there.

> 2) Firefox profiles. I'm backing up my profile and I know how to reload my data for XP but how would I go about doing it for Ubuntu?
I'm not too sure about this one, but if it's the bookmarks you're concerned with, you can just export them to a file and then import them back in Firefox in Ubuntu.


Oh, and install Windows first.

---

### Post by Sef on 2008-05-02
> 1) Installing drivers, I've got a Lenovo V100 laptop. They've got a driver page ([http://www-307.ibm.com/pc/support/si...IGR-64290.html](http://www-307.ibm.com/pc/support/si...IGR-64290.html)). Will it be difficult to install these? And how would I do it?

Except for the BIOS, all the drivers are for various versions of Windows.  None of them will work on Ubuntu.

---

### Post by wermeulen on 2008-05-02
Hiya, before you wipe anything--have you tried the Ubuntu LiveCD on your laptop? Then you'll know up front what hardware might be a problem for which you'll need to get back here :)

And indeed, for question 1 don't worry. Ubuntu doesn't use the Windows drivers (the website only has Windows drivers) and Windows XP probably doesn't need them. If you do not have a backup computer with internet access, you could download the WLAN and LAN drivers in advance--just in case something is needed to get internet access again in XP, although very unlikely.

---

### Post by I[AM]SMRT on 2008-05-02
> **jken146 said:**
> I'm not too sure about this one, but if it's the bookmarks you're concerned with, you can just export them to a file and then import them back in Firefox in Ubuntu.
It's mainly the passwords/add-ons that I'm worried about.

That reminds me, will the same add-ons fore Firefox I use on XP be usable on Ubuntu?

---

### Post by Tsurugi13 on 2008-05-02
Ubuntu comes with the Firefox 3 beta 5, so only the ones that are updated to accommodate that, unless you downgrade to ff 2. As for passwords, I suggest writing them down in a notepad or word document and just bringing them into Ubuntu.

---

### Post by Moop on 2008-05-02
Reloading your firefox profile will work the same as XP but the location is different. In Ubuntu the firefox profile is in a hidden folder named .mozilla in your home directory. 

Go to Places-Home Folder. Use ctrl-h to enable viewing of hidden folders. Locate and open the .mozilla folder. Inside that folder is the Firefox folder that contains your profile. Copy your backed up profile into the firefox folder and you should be all set.

Ubuntu 8.04 uses Firefox 3.0b5 as default so if your coming from a 2.xx version of firefox, all your extensions may not work. Older versions of firefox are available.

---

### Post by Average Joe on 2008-05-02
Alternatively to Moop's suggestions you can copy your backup profile anywhere, and start Firefox in a terminal with:```
firefox -profilemanager
```and create your profile such that it points to where your have put your Firefox backup profile. (This trick works in MS Windows as well, I have used it a lot to share a single Firefox profile within different operating systems on a multi-boot computer.)

---

### Post by jken146 on 2008-05-02
> **'I[AM]SMRT said:**
> That reminds me, will the same add-ons fore Firefox I use on XP be usable on Ubuntu?

Perhaps not all.  More of an issue might be incompatibility with Firefox 3 (FF3 beta 5 comes with Hardy Heron).  Firefox 2 is still available though, if you need it.

edit:  Oops!  That's already been said.

---

### Post by I[AM]SMRT on 2008-05-02
> **wermeulen said:**
> Hiya, before you wipe anything--have you tried the Ubuntu LiveCD on your laptop? Then you'll know up front what hardware might be a problem for which you'll need to get back here :)
I'm backing up stuff right now so I'll be sure to do that before I reformat anything.

Thanks so much guys, I've heard that the Ubuntu community is awesome and you guys really show it :). I'm really looking forward to trying out this new OS (I actually have some linux experience prior to this from school, so it won't be *totally* new).

P.S. What's the deal with 3 partitions for Ubuntu (one for /, one for /home and a 2 gb one)? I've read a bit about it but don't quite understand.

EDIT: Nevermind, found a bit about partitioning ([http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)).

---

### Post by Tom--d on 2008-05-02
I only have one partition for Ubuntu, / 

With a normal install.. (use whole disk) it will create another partition. this is called swap. 

Swap is where if your ram becomes all used up.. it will then start to use your hard drive. 

For me, I have 2GB of RAM. I'm never going to use it up so I never made a partition for swap. (Do this by manual in install)

With /home. You can put that on a serperte partition. /home is where all your files are. music, videos etc. (/home/tom/Music/blah blah blah/)

Many people put it on another partition.

---

### Post by GooblyWoobly on 2008-05-02
I strongly suggest creating /home as a separate partition. Create it adjacent to the / partition, so that you can re-size them into each other later.

Why create a separate /home partition? Just to save you the headache of backing up everything, and re-doing your settings all over when you do a fresh install ever. When you re-install/do a clean upgrade, you can just install it in the / partition, keeping /home intact.

---

### Post by I[AM]SMRT on 2008-05-02
> **GooblyWoobly said:**
> I strongly suggest creating /home as a separate partition. Create it adjacent to the / partition, so that you can re-size them into each other later.

Why create a separate /home partition? Just to save you the headache of backing up everything, and re-doing your settings all over when you do a fresh install ever. When you re-install/do a clean upgrade, you can just install it in the / partition, keeping /home intact.
Should the /home partition come before the / partition or does it not matter? Also, where should I put the swap partition? I've read that it does best closer to the start of the HD.

EDIT: Also, does anyone know how much I should partition for my XP install?

---

### Post by I[AM]SMRT on 2008-05-02
Ok, so I just finished up installing XP and I'm about to partition my hard drive.

I'm using the gnome partition editor but I don't know what to do. I booted the computer with the CD in and it's giving me a ton of options that I don't know what to do with. Can someone refer me to a tutorial or something, I've looked and can't find one =/.

---

