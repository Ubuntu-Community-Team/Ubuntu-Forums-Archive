---
title: "disk imaging and back-up"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by navic101 on 2008-11-08
Hi all,

Thanks for your on-going help with my journey through linux.
My question surrounds backing up linux. Unbuntu hardy heron. Specifically using an image software..norton ghost or similar to back up my precious linux system as it is working so well at present.

1. Is there a suitable suggestion for a linux based image software that would so the same. I am unsure if ghost would work. 

 Can you create a compressed driver base/restore point via unbuntu in case of drive failure or corruption?

2. Does the HDD ever need defraging? This is a mute point regarding the community i know. I have`nt seen ANY software that would defrag in linux.

3. Is it possible to do a "clean up" of all used packages that have been installed previously via the automatic update to maximise HDD space?

Many thanks as always

regards

---

### Post by bumanie on 2008-11-08
1. There are multiple tools available - ghost4linux, partimage, clonezilla or my favourite dd commands. Suggest you look at them all and see which you feel more comfortable with. dd is command line only, but is the most simple IMO.

2. There is no need to defrag ext3 - there is very little fragmentation unless the filesystem is nearly full.

3.Using > sudo apt-get autocleancleans up quite a bit of stuff. On 8.10 there is a new tool called cruft removal tool that lists things on a GUI.

---

### Post by bumanie on 2008-11-08
1. There are multiple tools available - ghost4linux, partimage, clonezilla or my favourite dd commands. Suggest you look at them all and see which you feel more comfortable with. dd is command line only, but is the most simple IMO.

2. There is no need to defrag ext3 - there is very little fragmentation unless the filesystem is nearly full.

3.Using > sudo apt-get autocleancleans up quite a bit of stuff. On 8.10 there is a new tool called cruft removal tool that lists things on a GUI. Look [here]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html") for other cleaning tips

---

### Post by Sealbhach on 2008-11-08
Have a look at QuickStart. It might meet your backup needs. It also has other handy utilities as well.

[http://lifehacker.com/5064373/quickstart-configures-your-ubuntu-system-without-terminal-work](http://lifehacker.com/5064373/quickstart-configures-your-ubuntu-system-without-terminal-work)

No need to defrag.

As well as autoclean, you can autoremove as well:

```
sudo apt-get autoremove
```

Clears up old packages that are no longer needed.


.

---

### Post by buccaneere on 2008-11-08
What about plain old system restore, for an update that jammed your machine and some configurations?

---

