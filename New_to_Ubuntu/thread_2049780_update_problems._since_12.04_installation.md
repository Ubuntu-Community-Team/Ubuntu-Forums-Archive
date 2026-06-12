---
title: "update problems. since 12.04 installation"
date: 2012-08-29
forum: New to Ubuntu
---

### Post by Peter J Cooke on 2012-08-29
Since updating to 12.04 my pc has a mind of its own shuts down on its own I have to re boot to get any action from the pc.
Everything locks up after a few minuites it is getting to be a pain I have to use my laptop to access anything.





:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.':lolflag:

---

### Post by MoebusNet on 2012-08-29
Hmmm...If I understand you correctly, I may have had a similar issue. I think what I would do is boot the computer from a 12.04 CD or USB flash drive (whichever version you have installed - Ubuntu, Kubuntu, Xubuntu etc.) then use GParted to check and repair the hard drive partition you have Ubuntu installed in.

As far as the updates issue this worked for me:

In Terminal type the following code, pressing "enter" after each line of code:

```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update
```

---

### Post by Peter J Cooke on 2012-08-29
Thank you for that it worked so far when I tried to use update manager I got the following message.The connection is fine.


W:Failed to fetch gzip:/var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_precise_main_source_Sources  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by MoebusNet on 2012-08-30
I think this may straighten out the bad-sig problem:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59
```

Then this:

```
sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

I got this advice from here:
[http://ubuntuforums.org/showthread.php?t=1983220](http://ubuntuforums.org/showthread.php?t=1983220)

---

### Post by Peter J Cooke on 2012-09-02
I am now getting this message and the system is going error mad



E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.

---

### Post by MoebusNet on 2012-09-04
I think I'm getting beyond my depth on this one; I failed to notice that you are using repositories from Great Britain rather than the U.S.

If you haven't already done so, back up your data in case everything goes bad.

Then, if you are willing to risk breaking your system you could try:

[http://ubuntuforums.org/showpost.php?p=6700382&postcount=66](http://ubuntuforums.org/showpost.php?p=6700382&postcount=66)

I have not used this, but it sounds like it might work. Again, this could lead to system breakage so an alternative might be to wait for someone with better skills than myself.

Sorry if I haven't been of more help.

If worst comes to worst, I guess you could always do a fresh install of 12.04.1 then restore the data you previously backed up.

---

### Post by MoebusNet on 2012-09-04
Have you seen this thread?

[http://ubuntuforums.org/showthread.php?t=2052822](http://ubuntuforums.org/showthread.php?t=2052822)

The OP had the same error message and post #2 gave the recommended solution which is a little different than the code I posted:

```
sudo apt-get clean

sudo rm /var/lib/apt/lists/*

sudo rm /var/lib/apt/lists/partial/*

sudo apt-get clean

sudo apt-get update
```

which removes rather than renames the /var/lib/apt/lists then cleans and does an update. Might be worth a try...

---

