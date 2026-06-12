---
title: "HOWTO: Channel Icons in MythTV"
date: 2007-01-05
forum: Outdated Tutorials &amp; Tips
---

### Post by plb on 2007-01-05
**Please Note, this howto assume you already have MythTV setup and running**
[B]
First things first, we will need xmltv installed:[/B]
> *sudo apt-get install xmltv*

**Next, we will need a script to make the iconmap**
> *wget [http://svn.mythtv.org/trac/browser/trunk/mythtv/contrib/mkiconmap.pl?format=raw](http://svn.mythtv.org/trac/browser/trunk/mythtv/contrib/mkiconmap.pl?format=raw)*

**For clarity's sake:**
> *mv mkiconmap.pl\?format\=raw mkiconmap.pl*

**Next:**
> *perl mkiconmap.pl*

**And finally:**
> *mythfilldatabase --import-icon-map iconmap.xml --update-icon-map*

Once that is done, you should have channel icons throughout your program guide.

---

### Post by mtron on 2007-01-07
Seems to work only for North America :(

Is there a way to grab the icons for us at the other side of the pond?

---

### Post by sparky06 on 2007-01-16
Here's a guide for getting UK Freeview icons and the Radio Times schedules in mythtv

[http://parker1.co.uk/mythtv_id.php](http://parker1.co.uk/mythtv_id.php)

---

### Post by Dubstar_04 on 2007-01-16
What I did was actually ad them myself. it does take a while but you have the option of using higher quality icons.

If you down load the icons from the following link, and store then in a folder out of the way:

[http://forum.team-mediaportal.com/showthread.php?t=2172&page=8](http://forum.team-mediaportal.com/showthread.php?t=2172&page=8)

When you have the icons unzipped open the mythtv backend and go to the channel editor (option 5) and in the channel list click on each channel and edit the location of the icon.

Like I say this is a long process but it will achieve the required result and with better icons than the xmltv method.
 
I would also recommend using a small font in the tv guide and using only the channel name. these options are configured in the frontend.

I hope this helps.

---

### Post by Titus A Duxass on 2007-01-16
Here in Germany I get my icons when I do myththfilldatabase --manual, but it takes a bloody age to complete the task.

---

### Post by superm1 on 2007-01-16
Very nice howto.  I've added it to the community documentation (and credited plb of course)

Here is the direct link:
[https://help.ubuntu.com/community/MythTV/Install/WhatNext/channel_icons](https://help.ubuntu.com/community/MythTV/Install/WhatNext/channel_icons)

It shows up inline with several of the larger howtos in the What Next section as well

---

### Post by lingenfr on 2007-04-25
Having done this once manually, I really would like for this to work. Unfortunately, the link to download the script is broken. I tried to figure out what it should be, but I can't read the text explaining why they changed the link. Help.

---

### Post by newlinux on 2007-04-26
It doesn't seem to recognize my postal code or any that I put in... something broken?

---

### Post by disruptor108 on 2007-04-27
I tried looking at [http://svn.mythtv.org/trac/browser/trunk/mythtv/contrib/master_iconmap]("http://svn.mythtv.org/trac/browser/trunk/mythtv/contrib/master_iconmap") and downloaded the .xml file from there.  I then performed mythfilldatabase on that .xml file, but it didn't appear to work.  Anyone have any suggestions on this one?

---

### Post by majoridiot on 2007-04-27
try:

```
$ wget "http://svn.mythtv.org/trac/browser/trunk/mythtv/contrib/master_iconmap/master_iconmap.xml?format=txt" -O master_iconmap.xml
$ mythfilldatabase --import-icon-map master_iconmap.xml --update-icon-map
```

---

### Post by lingenfr on 2007-05-27
That works. Thanks. It pulled about 80-90% of the icons. Can I manually get the others and get them to appear?

---

### Post by cmcginty on 2007-06-14
Does it matter if the commands are run on frontend or backend machine?

---

### Post by dyslexicbunny on 2007-08-06
> **majoridiot said:**
> try:

```
$ wget "http://svn.mythtv.org/trac/browser/trunk/mythtv/contrib/master_iconmap/master_iconmap.xml?format=txt" -O master_iconmap.xml
$ mythfilldatabase --import-icon-map master_iconmap.xml --update-icon-map
```

So I tried this approach but I only have a quarter of the icons when you include all the PPV and music channels. Everything that would be considered available under analog has 1 icon and 3 titles. How would I go about adding these other channel icons and information? I think it requires me to change the master_iconmap script but I'm not quite sure.

Additionally when I run mythfilldatabase by itself, it locks up after downloading a day of material (four hours past midnight) and then deleting the whole day starting at midnight. But it might be due to the icons not working properly.

Thanks.

---

### Post by mjezell on 2007-12-18
Very nice Howto.  I've been trying to install the channel icons for a while now and this is the post that actually had all the elements needed to get it done.  Thanks so much.

---

