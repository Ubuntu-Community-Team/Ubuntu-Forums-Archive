---
title: "Saving ubuntu settings from wubi install"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by bikinguy77388 on 2008-06-15
Hi All,

I have ubuntu setup using wubi on a win2000 machine.
Have done alot of work getting it all running great.

I am getting a new machine and would like to setup ubuntu in its own partition. Is there any way I can save my virtual install and copy it to a dedicated partition on my new machine?

Thanks in advance,
bikinguy

---

### Post by shifty_powers on 2008-06-15
how big was your home folder?

---

### Post by WinterMadness on 2008-06-15
> **bikinguy77388 said:**
> Hi All,

I have ubuntu setup using wubi on a win2000 machine.
Have done alot of work getting it all running great.

I am getting a new machine and would like to setup ubuntu in its own partition. Is there any way I can save my virtual install and copy it to a dedicated partition on my new machine?

Thanks in advance,
bikinguy


if im not mistaken i think you have to save the ISO file and burn it to a disc.

---

### Post by Dougie187 on 2008-06-15
> **WinterMadness said:**
> if im not mistaken i think you have to save the ISO file and burn it to a disc.

That will not help him move his settings over. But he will do that to install ubuntu.

It could be difficult to get *ALL* of his settings over, but most of them are stored in your home directory (/home/username) if you copy that over (especially all the .filename files) you will get the majority if not all of your settings back with you.

---

### Post by shifty_powers on 2008-06-15
> **WinterMadness said:**
> if im not mistaken i think you have to save the ISO file and burn it to a disc.

think you might be mistaked. he has used wubi to run ubuntu in a 'side-along' partition that sits within windows. he now wants to go to a proper dual boot, but keep his settings etc..

basically, i'd get hold of a spare hd, spend £5 on a basic hd enclosure and copy your home folder over. just set up the new install with the same user account and details and you'll be fine... (well, might be one or two things to sort out, but nothing too hard ;))

---

### Post by bikinguy77388 on 2008-06-15
Thanks guys,

I have a 100 gig usb hardrive and I keep a second hardrive on hand with my windows cloned to it.

I can get plenty of storage no problem..should I attempt to copy the entire install ?

bikinguy

---

### Post by hyper_ch on 2008-06-15
just tar.gz your home folder, and make a list of teh additional installed packages... then install ubuntu in its own partition, untar the home folder accordingly and let apt-get run through that list of installed packages.... et voilà

---

### Post by eldragon on 2008-06-15
i wouldnt move the entire install. will probably not work.

i would copy the entire home partition, and the entire /etc folder

/etc holds system wide config files.

you could then create a new partition for your /home in the new computer, and move all homes from the wubi install there.

for /etc/, if you have configured software and you wish to keep its settings, then move the pertinent files from your old etc folder to the new place.
***DO NOT*** OVERWRITE THE ENTIRE /ETC FOLDER DIRECTLY.

good luck

---

### Post by bikinguy77388 on 2008-06-15
Thanks guys for all the helpful input. *S*

hyper_ch...very elegant solution..will give it a try...the worst that can happen is I hose it all but no big deal...like starting from scratch to. 

Won't be doing this for another week or so will keep you posted on how it went.

bikinguy 
keep2up

---

### Post by hyper_ch on 2008-06-15
you can generate a list of the installed packages in synaptic.... then just run them as
```

sudo apt-get install PACKAGE1 PACKAGE2 PACKAGE3 .....

```

---

### Post by Dougie187 on 2008-06-15
Also, I dont know that you want to copy your entire /etc directory. Just because some of the settings might be wubi specific (im not sure how wubi works with hardware and stuff) but if you just over write your installations /etc directory with the one your wubi install made, you could cause a lot of issues. You could always back up your /etc and slecetivly replace or reference files in there for preferences, but for the most part just replace your home dir. Also, for a list of additional packages you installed, you might check /var/log and see if there is an apt-get log or something that details all of the apt-get install calls you have made.

For your tar, you can just type
```
tar cvzf home.tgz ~/*
```

Then after you get your new installation ready, you can move home.tgz to your home directory, and type
```
tar xvzf home.tgz
```

---

### Post by shifty_powers on 2008-06-15
or use this method ;)

[http://ubuntuforums.org/showthread.php?t=261366&highlight=rsync](http://ubuntuforums.org/showthread.php?t=261366&highlight=rsync)

---

### Post by Dougie187 on 2008-06-15
> **shifty_powers said:**
> or use this method ;)

[http://ubuntuforums.org/showthread.php?t=261366&highlight=rsync](http://ubuntuforums.org/showthread.php?t=261366&highlight=rsync)

Thats pretty slick.

---

### Post by shifty_powers on 2008-06-16
heh, yeah, i have a big list of very useful threads and whatnots bookmarked. might get round to posting them later ;)

---

### Post by hyper_ch on 2008-06-16
> **shifty_powers said:**
> heh, yeah, i have a big list of very useful threads and whatnots bookmarked. might get round to posting them later ;)

I'd recommend you to make a wiki or blog and post there all the stuff yo learn... I think it's much better than to keep endless bookmarks :)

---

### Post by shifty_powers on 2008-06-16
well i posted some here:

[http://ubuntuforums.org/showthread.php?t=831222](http://ubuntuforums.org/showthread.php?t=831222)

if anyone is interested ;)

and maybe a blog when i have enough time... being a student psychiatric nurse is not easy :D

---

### Post by hyper_ch on 2008-06-17
well, I run it privately for me... it's a knowledge base for myself ;)

---

