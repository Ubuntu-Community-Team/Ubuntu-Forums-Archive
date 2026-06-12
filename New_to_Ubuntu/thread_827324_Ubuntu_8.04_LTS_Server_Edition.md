---
title: "Ubuntu 8.04 LTS Server Edition"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Tern67 on 2008-06-12
i'm trying to install on a compaq proliant ML370 server and it gets to checking the cd and tells me there is an issue with the disk... i have tried 3 different disk and a new cd rom drive and still get the error can someone give me an idea of what may be going on???

Terry

---

### Post by Vivaldi Gloria on 2008-06-12
Have you checked the md5 of the disk image?

There is no point of burning a corrupted .iso file over and over again.

---

### Post by gr4nf on 2008-06-12
Are you trying it with the amd64 version? If so, your processor may not be 64 bit. Try the 32 bit version. Also, maybe try the alternate install cd.

---

### Post by Tern67 on 2008-06-12
i downloaded a different iso from a different site... same issue .. and iam using the 32 bit version of the software..

---

### Post by gr4nf on 2008-06-12
As said, maybe try the alternate install cd.
link that might not work:
[http://www.ubuntu.com/getubuntu/downloading?release=server-lts&arch=i386&mirror=http%3A%2F%2Fmirror.u-soft.dk%2Fubuntu-releases%2F&debug=&download-button=&alternatecd=alternate](http://www.ubuntu.com/getubuntu/downloading?release=server-lts&arch=i386&mirror=http%3A%2F%2Fmirror.u-soft.dk%2Fubuntu-releases%2F&debug=&download-button=&alternatecd=alternate)

---

### Post by Nythain on 2008-06-12
download via bittorrent if at all possible
if they have an alternate install for teh server iso (wich i dont think they do) get it
burn slower than slow... im talkin sloooooooooowest speed possible, like 1-4x
verify written data after burn with the burning software (usually an option available before starting the burn)

thats about all i got... you could, after downloading before burning, download the md5 of the image from the exact some location and make sure its exactly the same after being downloaded (ie no errors), most people dont do this, but downloading large files via ftp or http can sometimes cause errors, wich is why its also advised to download via bittorrent, as most bittorrent clients will hash check and whatnot (though i've heard arguments that this is a totally incorrect and lame statement/assumption)

either way, it seriously sounds like somethings wrong between the getting it process and the burning it process...

also, not so make you sound retarded but you'd be amazed how many times this has come up, you are burning the image right, not just burning the iso file itself onto the cd

---

### Post by Tern67 on 2008-06-16
the cd works fine on a normal box ... and as i said i downloaded the iso from 2 different locations with the same error messages .. and not to be rude either but if i didnt burn the disk right it wouldnt have started the install and then give me the error .. thanx for the info so far...

---

### Post by SgtMopar on 2008-07-09
Did you ever get this figured out. I have a HP Proliant ML570G2 and cannot get it to load either. The CD always checks bad (if it will even boot from CD).

I have tried to download from several different servers including the BitTorrent. Tried to burn with a different computer. Tried a different burning program. 

After half a dozen CDs I even replaced my CD drive in the server. I still did not have any luck so I tried to download an older version from the archive.

Does anyone have any other ideas?


Chris

---

### Post by ibizatunes on 2008-07-09
I had a simlar problem, i had download from ubuntu site, the cannoical servers, burnt it at x1 speed, and had to use a different CD drive to get it to boot..... that seem to work, i think my cd burner is starting to break!

Do you know your new cd drive work? Have you successfully burnt on it before!?

---

### Post by Vivaldi Gloria on 2008-07-09
You can try the minimal cd:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It's a 10 MB install cd which downloads everything from the net as it installs. It works most of the time even if the regular cd fails.

You need to have a decent connection to use it. Also the installation takes much longer than a regular installation.

---

### Post by Cadmus on 2008-07-09
Do a memory test on the server, I'm thinking that slightyl off memory could cause checksums to fail and for the install to fail as a result.

---

