---
title: "Changing Linux Distribution"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by _jj on 2008-07-09
I currently use an outdated version of Suse Linux on my work computer, having got increasing frustrated with it I have finally decided to switch to Kubuntu Hardy Heron (which I happily use at home).  Have downloaded and burned an install disc but before I take the plunge I have a couple of questions (particularly because it is my work computer).

Am I correct in saying that my home directory should remain untouched or that it is easy to keep it untouched, thus saving my firefox/thunderbird etc. preferences and my work?

Will installing Kubuntu rid my computer of all traces of the Suse installation (preferable).

I am expecting to possibly have to reconfigure my network and printer is there anything in particular I should take note of before installation and can people think of any other general things that may get destroyed in the changeover?

I am expecting to have to reinstall some of the programs I have currently installed.  Several of these have hidden folders within my home directory, (which is the only thing I am attempting to keep in the changeover) I assume that these relate to preferences, is it safe to/should I leave these?

Obviously I am planning on backing up all of my important files.

Thanks in advance for the help and sorry about the multiple questions.

---

### Post by tamoneya on 2008-07-09
your home directory will remain untouched if it is on a separate partition from your root partition.  Otherwise it will be most likely over written along with the rest of the OS.

As for Suse it will be removed if you tell ubuntu to remove its partition.  Otherwise Ubuntu will install itself along side.  Printers will most likely have to be reconfigured as you mentioned.

---

### Post by _jj on 2008-07-09
So, in my case it is probably best to have a partition for my home folder and all my files and another partition (the root one) where all my distribution stuff goes?  Then on installation of Kubuntu if I tell it where the home folder partition is it will allow me access to all my existing data files and program preferences without altering them on installation?

---

### Post by tamoneya on 2008-07-09
yes but whether or not you will be able to do that depends on whether the separate partition was setup when you installed suse.

---

### Post by _jj on 2008-07-09
well I currently it is all in one partition, however I have quite a lot of free space, would it be possible to create a partition?  Alternatively there is currently a windows partition living on my computer which I have never used and could utilize to facilitate the move.

[edit] the source of my woe is that i inherited suse rather than chose it!

---

### Post by eriqjaffe on 2008-07-09
> **_jj said:**
> well I currently it is all in one partition, however I have quite a lot of free space, would it be possible to create a partition?Sure, I did that when I moved from a WUBI install to a command-line install on a dedicated drive.  Just created a partition, copied the contents of the /home directory to it, and then mounted that to /home when I reinstalled.  Worked like a charm.

---

### Post by _jj on 2008-07-15
Suse isn't letting me resize my partitions for reasons best know to itself, it seems I can however format my windows partition, what would be the best format to change this too for a subsequent install of kubuntu, EXT3?

edit: after some looking I am pretty sure I want ext3 and I am going to try and use gparted over SUSE's useless partition editor

---

