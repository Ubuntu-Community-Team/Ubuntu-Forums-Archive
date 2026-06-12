---
title: "iso download trouble"
date: 2014-05-25
forum: New to Ubuntu
---

### Post by jaxom98 on 2014-05-25
Using brassero to download iso's ie ubuntu 12.04 and now 14.04 and edubuntu14.04 I often get a corrupt download. When I try to burn an iso I often get an error message to the effect "Unable to continue, files corrupt.Why are things going wrong routinely?
I am running edubuntu 12.04.1 64 bit  
I want to do a clean install, not an upgrade as while 12.04.1 works well, updates 12.04.3 and 12.04.4 result in a system lock up and a reinstall of 12.04.1 is the only way out.
What I want is a system as reliable and updatable as ubuntu 8.04
Is any one able to help?

---

### Post by LastDino on 2014-05-25
From what I know, brassero is used to ''burn'' the CD/DVD and not downloading. Have you checked checksum? Maybe ISO you downloaded is corrupted? 

Also, what exactly do you mean by system lock-up? Describe it well with your system config and people here might able to help.

---

### Post by jaxom98 on 2014-05-30
Hello LastDino, sorry for the delay in replying.
Yes , brassero is the dvd burning program,poor terminology on my part.
Checksum I know of ,but don't know how to find or use.
system is asus p5k mobo, core 2 duo @2.6Ghz, 4Gb ram , 1Tb hdd
system lockup is the OS, edubuntu 12.04 and 12.04.1 worked. I am running 12.04.1 as that is the last reliable version. There does not seem to be a 12.04.2 version, at least not in what I have seen in avalible downloads. 12.04.3 and 12.04.4 both cause the system to lock up,ie freeze solid. The freeze starts at 2 min run time (on first startup), then rapidly drops to about 30/40 seconds after start up(6-10 starts, number is variable).At each restart or cold start the run time gets less. To stop takes a hard shut down. Nothing will run,mouse,key board ,command line, everything freezes.
The only cure has been a reinstallation of 12.04, or 12.04.1. 
At worst the system will lockup while updating and then you need to reinstall as  a restart or cold start will freeze during boot up.
I have not managed to install from a 12.04.3 or 12.04.4 disk due to freeze during install.
This is 64 bit not 32 bit.
I have looked at the forums and nobody else seem to have my problem so I think it is at my end.
Please keep explainations simple as my knowledge is very limited.
It will be june 3rd before I am back.

---

### Post by Harsh_Parikh on 2014-05-30
> **jaxom98 said:**
> 

Checksum I know of ,but don't know how to find or use.


Checksum is to find the clarity of your iso image file.....it is attached with your downloaded file or can see the link just after the iso file on the site from where you download the iso...
and for complete information about checksum,you should visit [http://help.ubuntu.com/community/HowToMD5SUM](http://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Rob Sayer on 2014-05-30
Definitely read the above md5sum link, and if possible download via torrent.  It's more reliable.

But I wouldn't be too quick to say that 12.04.2 on are buggy.

12.04.1, .2 etc are not different *versions* really.  They do that so that when you install you don't have to do as many 6 months worth of updates.  The reason you're having problems when updating 12.04.1 is that you're essentially updating to the same thing as if you had installed 12.04.4, plus any newer updates too.

I'm certainly not as knowledgeable as some people on this forum but I'd suspect a hardware support issue if it's not a corrupt iso download.  Some setting or driver may have worked before but you'd need a different one now.

I had a similar issue with my old Compaq laptop, though less severe.  It has an older AMD gpu and AMD cut way back on their Linux support team.

Try booting off the 12.04.1 CD or USB stick ... the latter is faster, if possible.  Then open the terminal and enter 

```
lspci
```

and

```
lsusb
```

into terminal and post the results here, embedded in code tags.  That's important.  This forum has excellent support but it's free.  You want it to be as readable as possible.

There is, I'm sure, more intelligent and pertinent advice here but that's where I'd start.

---

### Post by Impavidus on 2014-05-30
> **Rob Sayer said:**
> 12.04.1, .2 etc are not different *versions* really.  They do that so that when you install you don't have to do as many 6 months worth of updates.  The reason you're having problems when updating 12.04.1 is that you're essentially updating to the same thing as if you had installed 12.04.4, plus any newer updates too.
Actually, there is one difference between a fully updated 12.04.1 and a fully updated 12.04.4, and the difference could be relevant here. A fully updated 12.04.1 still uses a 3.2 kernel, where 12.04.4 comes with the 3.10(?) kernel.

---

### Post by kansasnoob on 2014-05-30
> **Impavidus said:**
> Actually, there is one difference between a fully updated 12.04.1 and a fully updated 12.04.4, and the difference could be relevant here. A fully updated 12.04.1 still uses a 3.2 kernel, where 12.04.4 comes with the 3.10(?) kernel.

Right, it all has to do with the LTS hardware enablement stack:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Only 12.04 and 12.04.1 shipped with the Precise kernel and X-stack, they are archived here:

[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

---

### Post by whitesmith on 2014-05-30
To get the version of your kernel, do this in a terminal (Ctrl-Alt-t)```
uname -a
```

---

### Post by jaxom98 on 2014-06-04
Hello whitesmith,re  uname -a , nogo, error message: "Option -a requires an argument" what is an argument???
Impavidous ,kernal version shown at start up on dual boot page is 3.8.0-29-generic is this what you wanted?
kansasnoob I followed your links. The first one is confusing.

---

### Post by mörgæs on 2014-06-04
If you download from a mirror close to you there's less risk of a failed transfer.
[https://launchpad.net/ubuntu/+cdmirrors](https://launchpad.net/ubuntu/+cdmirrors)

---

### Post by mastablasta on 2014-06-04
also if oyu use torrent for download the download checksum is checked while it "downloads".

---

### Post by sandyd on 2014-06-04
> **mastablasta said:**
> also if oyu use torrent for download the download checksum is checked while it "downloads".

this.

---

### Post by jaxom98 on 2014-06-05
mogaes, I followed your links, very usful, bookmarked. thank you

---

### Post by jaxom98 on 2014-06-07
Thank you everyone for your help.
 It is taking a while to nut things out.
Please consider this thread closed.

---

### Post by Impavidus on 2014-06-07
> **jaxom98 said:**
> 
Then please mark this thread as solved: Tread tools (near top of the page) -> mark as solved.

---

### Post by jaxom98 on 2014-06-14
Up date, the trouble was tracked down to "update manager". Afriend of a friend had similar trouble and did updates via command line. This bypassed "update manager" and the updates to 12.04.4 went textbook perfect.

---

