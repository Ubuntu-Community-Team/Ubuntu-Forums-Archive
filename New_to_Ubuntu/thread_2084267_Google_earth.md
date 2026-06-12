---
title: "Google earth"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by acimi66 on 2012-11-14
Hi Guys,
I am trying to install google earth on Ubuntu 12 and have had absolutely no luck.

I have used a couple of methods in the command line and I also tried a version from the software center.

Does anyone know of a working version of this. Or better yet an open source replacement for it?
Thanks

---

### Post by Abhinav Kumar on 2012-11-15
> **acimi66 said:**
> Hi Guys,
I am trying to install google earth on Ubuntu 12 and have had absolutely no luck.

I have used a couple of methods in the command line and I also tried a version from the software center.

Does anyone know of a working version of this. Or better yet an open source replacement for it?
Thanks
Hi acimi66,

Just download  the deb file from 
[http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)
Make sure you download the correct deb package depending on your OS (out of 32 and 64 bit versions).

Say you downloaded this file to Desktop and say this file name is googleEarth.deb
Open a terminal
```

sudo dpkg -i ~/Desktop/googleEarth.deb

```

Regards,
Abhinav

---

### Post by acimi66 on 2012-11-15
Thanks for the reply.

Here is the error message I get after following those instruction as well as all the other times I tried to install the program


"   	 	 	 	 	 	   Selecting previously unselected package google-earth-stable.  
 (Reading database ... 513152 files and directories currently installed.)  
 Unpacking google-earth-stable (from .../google-earth-stable_current_i386.deb) ...  
 Setting up google-earth-stable (7.0.1.8244-r0) ...  
 Processing triggers for bamfdaemon ...  
 Rebuilding /usr/share/applications/bamf.index...  
 Processing triggers for desktop-file-utils ...  
 Processing triggers for gnome-menus ... 
 Processing triggers for man-db ...  
 Processing triggers for menu ...  
 me@my-Satellite-L650:~$ google-earth  
 Google Earth has caught signal 11.  
 

 

 

 We apologize for the inconvenience, but Google Earth has crashed.  
  This is a bug in the program, and should never happen under normal  
  circumstances. A bug report and debugging data have been written  
  to this text file:  
 

     /home/me/.googleearth/crashlogs/crashlog-50a5228f.txt  
 

 Please include this file if you submit a bug report to Google. "



That log says this:


Major Version 7
Minor Version 0
Build Number 0001
Build Date Oct 29 2012
Build Time 19:13:39
OS Type 3
OS Major Version 3
OS Minor Version 2
OS Build Version 0
OS Patch Version 0
Crash Signal 11
Crash Time 1352951349
Up Time 0.918068

Stacktrace from glibc:
./libgoogleearth_free.so(+0x1e9cfb)[0xb7613cfb]
./libgoogleearth_free.so(+0x1e9f43)[0xb7613f43]
[0xb77bd400]


Any ideas?

---

### Post by acimi66 on 2012-11-17
So, when I type google earth into DASH it shows up, i click on it, i get that first google earth image than it disappears, no error nothing, it just disappears.

I tried removing it through command line but it says it cant find it.

Any Ideas?
I love to sort this out

---

### Post by acimi66 on 2012-11-18
For anyone who is interested I have found two alternatives to that wonderful software google puts out (1 : Marble it actually in the software center
(2 NASA's World Wind

I am trying both, i'll get back to you with results if I remember.

Cheers

---

### Post by dwpbike on 2012-11-19
tanks for the post.  i'm real tired of getting disgusted with that pos.  i tried marble again.  just doesn't seem to be much there.  would be a good spot for apple.  maybe they could use mac earth as a tax write off.

---

### Post by aliddell on 2012-11-19
You should know that dpkg -i doesn't handle dependencies but something like, say, gdebi does. When I run

```
sudo gdebi google-earth-stable_current_amd64.deb
```

I get:

[FONT=Fixedsys]Requires the installation of the following packages: 
alien  heirloom-mailx  librpm3  librpmbuild3  librpmio3  librpmsign1  lsb-core  lsb-invalid-mta  ncurses-term  pax  rpm  rpm-common  rpm2cpio[/FONT]

Try it with gdebi.

---

### Post by acimi66 on 2012-11-20
Hey Thanks aliddell, I tried this got the same signal 11 error.

Yeah, i hear ya dwpbike, to add, the nasa world wind didn't really deliver either.

I am keeping marble but yes it does seem to have some work to do...

I will keep on looking.

---

### Post by aliddell on 2012-11-20
I found [this]("http://productforums.google.com/d/msg/earth/qNXOkluskdQ/meyS3EbESAQJ") in the Google product forums. It seems to have worked a couple weeks ago for someone running Fedora 17.

---

### Post by oldos2er on 2012-11-20
Moved to Absolute Beginners.

---

### Post by Francewhoa on 2013-02-24
Recommended installation methods at [https://help.ubuntu.com/community/GoogleEarth#Recommended_installation_methods](https://help.ubuntu.com/community/GoogleEarth#Recommended_installation_methods)

---

### Post by acimi66 on 2013-02-24
when I tried to open the .deb file with the SC I got this error warning

"The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details beneath."

It could just be over reacting/protective of  an unfamiliar file but I think I'll wait.

Cheers

---

### Post by rewyllys on 2013-02-27
> **acimi66 said:**
> Hi Guys,
I am trying to install google earth on Ubuntu 12 and have had absolutely no luck.

I have used a couple of methods in the command line and I also tried a version from the software center.

Does anyone know of a working version of this. Or better yet an open source replacement for it?
Thanks
Google Earth v. 6.0.3.2197-r0 was installed on my desktop, but it insisted on working erratically, sometimes OK, but more times not OK. (I'm running Linux Mint Maya, which is based on Ubuntu 12.04.)

I used the Synaptic Package Manager to remove version 6.0.3.2197-r0 completely. Next I went to 

[http://www.google.com/earth/download/ge/agree.html]("http://www.google.com/earth/download/ge/agree.html")

where I clicked on "Advanced setup", and then selected "Latest version (7.0)" and the 64-bit Debian package.

When the download had completed, I opened Nautilus, right-clicked on the Google Earth package, and chose "Open With GDebi Package installer".

The result is that Google Earth (v. 7.0.2.8415, build date 12/13/2012) appears to be working perfectly on my desktop.

---

