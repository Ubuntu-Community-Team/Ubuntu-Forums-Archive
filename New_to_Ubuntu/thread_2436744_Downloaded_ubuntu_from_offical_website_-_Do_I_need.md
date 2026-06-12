---
title: "Downloaded ubuntu from offical website - Do I need to verify my download?"
date: 2020-02-12
forum: New to Ubuntu
---

### Post by lasse64 on 2020-02-12
Hey,

I just started using ubuntu and I'm really loving it! Very userfriendly.
I downloaded it from ubuntu.com. I noticed it said "how to verify your ubuntu download" on the download page. Is this neccesary to do if I downloaded the iso image from the offical website?
I am an older gentleman (not tech savy), the instructions were very confusing.

Thanks beforehand!

---

### Post by SeijiSensei on 2020-02-12
It's generally considered a good idea to verify the download. That said, I haven't done so in years, and I have installed at least half-a-dozen versions of Ubuntu from their ISO images.

If you're curious, and you have the ISO image for your version of Ubuntu available, you can calculate its checksums using simple [terminal]("https://ubuntu.com/tutorials/command-line-for-beginners#1-overview") commands.
```

$ sha1sum < kubuntu-19.10-desktop-amd64.iso 
6e8c356a593c87a0fed8ce319d54e3e97a7fbc16  

$ sha256sum < kubuntu-19.10-desktop-amd64.iso 
e56388512a0610bd991192b197a13f1496c107377d9c96d332939c08e305b028 

```
These values are identical to those reported in the files SHA1SUMS and SHA256SUMS at [http://cdimage.ubuntu.com/kubuntu/releases/19.10/release/](http://cdimage.ubuntu.com/kubuntu/releases/19.10/release/).  (These programs take a bit of time to finish.)

If you use [BitTorrent]("https://help.ubuntu.com/community/BitTorrent") to download Ubuntu images, the BitTorrent algorithm computes checksums for each "chunk" of a file it transfers. So if you use BitTorrent, the resulting copy should be intact and without error.

---

### Post by Bashing-om on 2020-02-12
lasse64; Hello - Welcome to the forum

As to checking the .iso download integrity, while it is not "strictly" necessary it is a good thing to do. Data corruption can happen in the transfer, Doing the test is simple and quick.

Let's say the .iso file is in the Downloads folder and has the "name" ubuntu-19.10-desktop-amd64.iso -
Change your presently working directory to the location:
```

cd Downloads

```

The tool to check is already installed by default so next is run the tool in terminal:
```

md5sum ubuntu-19.10-desktop-amd64.iso

```
which will generate a hash value for the .iso file that is on your system; and display the value in the terminal. Compare this value to that of the hash given in the download page,

Peace of mind is a good thing, and additionally I always verify the burn to the medium:
Boot the installer to the boot menu and select "check disk for defects".

Now I feel confident to proceed with the install to the hard drive.

[INDENT][INDENT]confidence is a wonderful thing
[/INDENT][/INDENT]

---

### Post by lasse64 on 2020-02-12
> **Bashing-om said:**
> lasse64; Hello - Welcome to the forum

As to checking the .iso download integrity, while it is not "strictly" necessary it is a good thing to do. Data corruption can happen in the transfer, Doing the test is simple and quick.

Let's say the .iso file is in the Downloads folder and has the "name" ubuntu-19.10-desktop-amd64.iso -
Change your presently working directory to the location:
```

cd Downloads

```

The tool to check is already installed by default so next is run the tool in terminal:
```

md5sum ubuntu-19.10-desktop-amd64.iso

```
which will generate a hash value for the .iso file that is on your system; and display the value in the terminal. Compare this value to that of the hash given in the download page,

Peace of mind is a good thing, and additionally I always verify the burn to the medium:
Boot the installer to the boot menu and select "check disk for defects".

Now I feel confident to proceed with the install to the hard drive.

[INDENT][INDENT]confidence is a wonderful thing
[/INDENT][/INDENT]

> **SeijiSensei said:**
> It's generally considered a good idea to verify the download. That said, I haven't done so in years, and I have installed at least half-a-dozen versions of Ubuntu from their ISO images.

If you're curious, and you have the ISO image for your version of Ubuntu available, you can calculate its checksums using simple [terminal]("https://ubuntu.com/tutorials/command-line-for-beginners#1-overview") commands.
```

$ sha1sum < kubuntu-19.10-desktop-amd64.iso 
6e8c356a593c87a0fed8ce319d54e3e97a7fbc16  

$ sha256sum < kubuntu-19.10-desktop-amd64.iso 
e56388512a0610bd991192b197a13f1496c107377d9c96d332939c08e305b028 

```
These values are identical to those reported in the files SHA1SUMS and SHA256SUMS at [http://cdimage.ubuntu.com/kubuntu/releases/19.10/release/](http://cdimage.ubuntu.com/kubuntu/releases/19.10/release/).  (These programs take a bit of time to finish.)

If you use [BitTorrent]("https://help.ubuntu.com/community/BitTorrent") to download Ubuntu images, the BitTorrent algorithm computes checksums for each "chunk" of a file it transfers. So if you use BitTorrent, the resulting copy should be intact and without error.

Thank you for the quick replies!
I don't have the iso file anymore as I put it on a flash drive using rufus.
I did an "check cd for defects" instead and it came out "check finished: no errors found".

I was mostly thinking in terms of safety. If there could be any malicious files (spyware, malware, virus etc) from the download. But I assume this is only to check if there are corrupted files? As i said i downloaded it from the offical website.

Hope I don't come of as too paranoid but my old brain just want to make sure I can put pictures/log onto website without it being jeopordized

---

### Post by Bashing-om on 2020-02-12
lasse64; hey - hey

> 
Hope I don't come of as too paranoid 

web of trust: [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

[INDENT]hope this helps
[/INDENT]

---

### Post by yancek on 2020-02-12
> As i said i downloaded it from the offical website. 

I doubt there was any problem with the iso on the Ubuntu site but you do understand that it needs to get from that site to your computer and in that process could be corrupted for any number of reasons.

---

