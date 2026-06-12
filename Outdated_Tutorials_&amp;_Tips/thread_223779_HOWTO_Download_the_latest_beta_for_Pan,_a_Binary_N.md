---
title: "HOWTO: Download the latest beta for Pan, a Binary NewsReader (NNTP)"
date: 2006-07-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Darrena on 2006-07-26
Pan [http://pan.rebelbase.com](http://pan.rebelbase.com) is a Binary newsreader for Gnome (will run on Mac OS and Windows as well and in KDE as long as the gtk libraries are installed) similar to Forte Agent or Gravity.  The newsreader is GNKSA compliant and supports all the features a modern newsreader should such as inline images, NZB's, advanced filtering, multiple servers, multiple connections, queuing and more.

A couple of years ago it looked like Pan went into hibernation with the author not releasing any updates in a significant period of time.  It turns out the author was working hard in the background on a complete rewrite of Pan in C++.

Starting April 2nd Charles has been releasing weekly beta's of this new version.  Charles is now at the 16th release and it is reached a very stable level that he considers a release candidate and he is inviting extensive testing.  This version is A LOT more memory efficient and I am finally able to download the headers for even the largest groups.  

If you are currently using Pan 0.14.92 found in the Ubuntu repositories pan will maintain all your settings if you revert back but there is no easy way to import your old settings except your filters which should be picked up by pan automatically.

You can download the pan weekly beta's from [http://pan.rebelbase.com/download](http://pan.rebelbase.com/download)

If you would like to maintain your old version of pan and just test the new beta you can download the source code from the link above and compile it with the steps below.  Alternately if you don't mind replacing the current version of Pan on your system or if you don't currently have Pan installed there is a Deb package available on the Pan site.
[U]
Instructions for building pan for testing without replacing your current install of Pan[/U]

1) Download the required dependencies:
```
sudo apt-get install libpcre3-dev libgtk2.0-dev libgmime2.1-dev intltool automake1.7 autoconf libaspell15 libatk1.0-0 libc6 libglib2.0-0 libgtk2.0-0 libgtkspell0 libpango1.0-0 libpcre3 libxml2 zlib1g libpango1.0-common libgmime2.1 libgnome2-0 

```

2) Extract the tarball and change to the directory (Replace the name of the file with what you download and the directory name with the correct version, for example if you download version 0.107 make sure you cd to pan-0.107)
```
tar xfz pan_0.105.tar.gz
cd pan-0.105

```

3) Configure and build the application
```
./configure
make
```

4) Once Pan successfully compiles you now have the ability to run pan from here and keep both versions installed at the same time.  To do this type (Again replacing pan0-105 with the correct version ```
./$home/pan-0.105/pan/gui/pan
```

NOTE:  I did not have you do a make install here on purpose, if you do a make install it will replace your installed version of pan but not update the package database.  If you want to replace the current version of Pan on your system using the package available from the Pan website or rolling your own package would be a better idea.

Once you are satisfied that the new version of Pan meets your requirements or if you want to just jump straight to Pan there is a deb file linked from the Pan website (I maintain this package unofficially during testing so if you find any issues with it and not Pan itself please let me know).

If you find any bugs please report them at bugzilla.gnome.org, make sure you search for an existing bug report and that you pick pan pre-1.0 as the product when filing the bug.  If you are uncomfortable filing a bug post here and I will file it for you.

---

### Post by Thund3rstruck on 2006-07-27
This is interesting. I'll certainly be trying this out. 

The version of Pan in the repositories is just not usable for binary groups since it freezes and crashes while loading any group with more than 100,000 headers (such as alt.binaries.sounds.mp3.complete_cd).

---

### Post by Darrena on 2006-07-27
> **Thund3rstruck said:**
> This is interesting. I'll certainly be trying this out. 

The version of Pan in the repositories is just not usable for binary groups since it freezes and crashes while loading any group with more than 100,000 headers (such as alt.binaries.sounds.mp3.complete_cd).

Yeah and that was too bad since PAN is my favorite newsreader.  I was very happy to see that Charles started this rewrite and the results have been great.  I have been able to load even the largest groups ( > 200,000 headers) with no issues.

---

### Post by Pitmairen on 2006-07-27
I just use this package: [http://darrenalbers.com/Pan/](http://darrenalbers.com/Pan/) and everything works great.

---

### Post by Darrena on 2006-07-27
> **Pitmairen said:**
> I just use this package: [http://darrenalbers.com/Pan/](http://darrenalbers.com/Pan/) and everything works great.

Those are the packages I maintain :)  I just wanted to give people the option to run both in parallel before they switch since the new version dropped some features from the 0.14 series but as you see the new version should have all the features that 99% of the current Pan users need.

---

### Post by gurgle on 2006-08-02
on amd64:

pan: error while loading shared libraries: libgnome-2.so.0: cannot open shared object file: No such file or directory

---

### Post by BIGtrouble77 on 2006-08-03
gurgle, I'm guessing you need this package:```
sudo apt-get install libgnome2-dev
```

So far it seems pretty stable.  There are some minor delays when I try to get new headers that made me think the group didn't have any.  Not too big of a deal at this point.  

The only thing I really miss is that there's no 'Refresh Article Count' feature.  My compiled version is also really fast compared to the repo version.  I never did have a crash with any version of pan, tho.

---

### Post by Darrena on 2006-08-05
> **BIGtrouble77 said:**
> gurgle, I'm guessing you need this package:```
sudo apt-get install libgnome2-dev
```

So far it seems pretty stable.  There are some minor delays when I try to get new headers that made me think the group didn't have any.  Not too big of a deal at this point.  

The only thing I really miss is that there's no 'Refresh Article Count' feature.  My compiled version is also really fast compared to the repo version.  I never did have a crash with any version of pan, tho.

Please open a feature enhancement at bugzilla.gnome.org or post on the pan-users mailing list.  Charles wants to get a list of all the features people want so that he can at worst get them in by 1.1.

---

### Post by ricardisimo on 2007-03-30
Does this apply equally to an upgrade as to a fresh install? I've got .120 currently, and would like to try the latest release. Is it just download, dubba-click and go?

Also, do the repositories get updated regularly, or is "Plate of Shrimp" going to be the default Feisty Pan for good?

---

### Post by Darrena on 2007-06-03
> **ricardisimo said:**
> Does this apply equally to an upgrade as to a fresh install? I've got .120 currently, and would like to try the latest release. Is it just download, dubba-click and go?

Also, do the repositories get updated regularly, or is "Plate of Shrimp" going to be the default Feisty Pan for good?

You should be able to just download the new package and install it with no issues.  I suspect that Feisty will stay with .120 however newer versions may be available via backports when Gutsy becomes more stable.

---

