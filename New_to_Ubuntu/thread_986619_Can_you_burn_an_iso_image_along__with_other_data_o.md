---
title: "Can you burn an iso image along  with other data on one disc"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by jukingeo on 2008-11-18
Hello,

I would like to know if it is possible to burn an iso image and other data on a single CD.  I am looking to burn FreeDos (which is an operating system), however it only takes up about 155meg and there is plenty room left on a disc.  Since my FreeDos project has other programs that I want to use with it, I would like to know if they can be put on the disk as well. This way I don't have to waste discs.

I have downloaded K3b which supports a multi-session burn and I am wondering if this is possible.

So now my question is this, will the iso image burn properly and function correctly to install the OS?   Can I then access the extra data I put on it?

Thanx,

Geo

---

### Post by ddarsow on 2008-11-18
Sure. You can use ISO Master, or other similar apps to add files to the ISO

---

### Post by aeiah on 2008-11-18
you cant burn data alongside an iso image onto a disk, but you can add files to an iso, or strip files out of an iso, combine them with other data, and write to a new image file. since you're dealing with something that's bootable, it would be wise to investigate whether there's any documentation for doing this sort of thing specifically with freedos, as you may void any automatic integrity checks or other things that could break the booting of the disk at startup.

---

### Post by maybeway36 on 2008-11-18
If that doesn't work, you could also extract the data from the CD, add to it, then run genisoimage again, but that's a little harder to do.

---

### Post by jukingeo on 2008-11-18
> **aeiah said:**
> you cant burn data alongside an iso image onto a disk, but you can add files to an iso, or strip files out of an iso, combine them with other data, and write to a new image file. since you're dealing with something that's bootable, it would be wise to investigate whether there's any documentation for doing this sort of thing specifically with freedos, as you may void any automatic integrity checks or other things that could break the booting of the disk at startup.

Ok, so basically in a nutshell, I would have to "take apart" the iso, then add the files I want to it, then recreate the iso and finally burn it to a disc.

Now, the question is how would the "taking apart" deal affect the iso of FreeDos.  Normally something like this is a self booting disk.  If changing the iso affects this, then I could potentially ruin the booting option of the disc and that would render it useless.  Not a good thing if you ask me.  If that is the case then I guess I just have to bite in the sour apple and burn FreeDos on one disc as is and create another disc for the programs I want to use with it and the support files.

Thanx for the info.

Geo

---

### Post by jukingeo on 2008-11-18
> **ddarsow said:**
> Sure. You can use ISO Master, or other similar apps to add files to the ISO

Would a program like this affect the ISO if it self booting?  The ISO I want to use is FreeDos. It is an operating system and more then likely is set up to self boot for installation.  If my mucking about with the ISO will potentially ruin this...then I am just better off leaving well alone and just have to burn two discs.

Thanx,

Geo

---

### Post by maybeway36 on 2008-11-22
You can extract and rebuild ISOs with Linux command-line tools.
To extract the ISO:
```
mkdir loopdir
sudo mount -o loop something.iso loopdir
cp -rv loopdir newcd
sudo umount loopdir
rmdir loopdir
```
To rebuild it as a boot CD, assuming ISOLINUX bootloader is in the isolinux folder (as it is on FreeDOS):
```
genisoimage -no-emul-boot -boot-load-size 4 -boot-info-table -b isolinux/isolinux.bin -c isolinux/boot.cat -J -r -l -o newcd.iso newcd/
```
You can test to see if it boots in qemu (optional):
```
qemu -cdrom newcd.iso
```

---

### Post by jukingeo on 2008-11-22
And this will work fine?  The disc will boot properly and load up the operating system for install?

This is my main concern.  I don't want to be taking the .iso apart and then I "can't get it back together" properly and end up ruining a disc.  I never took apart an iso before.  But then again most of the past iso burns I had were of operating systems and most took about half to 3/4 of the disc.

This is for a FreeDos project I am working on and there is SO much room left over on the disc that it does make sense to put the entire project on the disc.

Geo

---

### Post by Kellemora on 2008-11-22
Hi Juk

You can BUY small business card sized CD's, but they cost about 4 times more than standard CD's.  So in a sense, it's like cutting off your nose to spite your face!

But you do have a VALID point in your question, especially SINCE it relates to LINUX.

Since ALL DRIVES are only FOLDERS in Linux, my question would be WHY frig with the ISO part, couldn't the CD be divided into Partions, one part being the ISO and the other part being the Data Files area and then burned as an iso and maintain the partitions?????

Sounds doable, on paper anyhow, hi hi.............

TTUL
Gary

---

### Post by maybeway36 on 2008-11-24
You won't ruin a disc using my steps as long as you install qemu and test it first. I've remastered the FreeDOS ISO myself, and as long as you don't move the files that are already there it works.
P.S. The original ISO file will remain untouched.

---

### Post by jukingeo on 2008-11-24
> **maybeway36 said:**
> You won't ruin a disc using my steps as long as you install qemu and test it first. I've remastered the FreeDOS ISO myself, and as long as you don't move the files that are already there it works.
P.S. The original ISO file will remain untouched.

No I don't have any intention on messing with the FreeDOS files.  The main goal was to make use of the VAST space behind it :).

Thanx,

Geo

---

