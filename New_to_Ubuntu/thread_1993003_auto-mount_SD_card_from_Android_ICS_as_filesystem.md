---
title: "auto-mount SD card from Android ICS as filesystem"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by RikoW on 2012-06-01
Dear all,

when I used to plug-in my Android phone via USB, the SD card of the phone would just be mounted as a filesystem under /media/some-cryptic-id. This was under 11.10 and version 2.4 (I believe) of Android. I used to just rsync directories.

Now (unfortunately after double update) under 12.04 and Android ICS, this is not the default. I don't seem to be able to access the file system as such anymore.

The card is mount somehow, because it appears as "MT11i" on the desktop, however /media is empty (as is /mnt). It seems like, Ubuntu things the card is a camera, because in the properties Nautilus lists the file system as "gphoto2" 

Any hints, how I can access this device from the CLI?

Thanks and cheers,

              Riko

---

### Post by Plueonic on 2012-06-02
Take a look in /run/media/$USER/

---

### Post by RikoW on 2012-06-02
Hi,

thanks for the suggestion, however, I don have a /run/media directory. I have a /run/mount but that doesn't seem to contain anything related.

In the mean time I figured out, it's actually a ICS problem, since the USB mass storage capability was removed by Google. I managed to mount the card/phone using mtpfs, but it is soooooo sloooow that rsync'ing larger dir structure is just not feasible.

What I did now is to take the SD card out of the phone and stick in the computer. Not very convenient, but so far the only think that worked.

I also installed sshDroid on the phone and mounted it via sshfs. That works in principle, but sshDroid keeps on dropping teh connection after the rsync is running for a short time (~1 min).

I'm not pleased with the situation as you guys can image.

Cheers,
    Riko

---

### Post by Plueonic on 2012-06-02
I remember reading somewhere that only devices without a SD card slot had the USB mass storage option removed. Mine still gives a pop-up when connected by a cable.

Perhaps the guys at xda-developers can provide a solution..

Edit: [http://www.reddit.com/r/Android/comments/mg14z/whoa_whoa_ics_doesnt_support_usb_mass_storage/](http://www.reddit.com/r/Android/comments/mg14z/whoa_whoa_ics_doesnt_support_usb_mass_storage/)
1st comment by Dan Morill

---

### Post by RikoW on 2012-06-03
Maybe is a vendor specific configuration of ICS that I don't have USB storage support. This is on a Sony Ericsson Neo (with an removable SD card).

So far, everything I found about mounting he SD card was using mtpfs, which as I mentioned, is terribly slow ...

Thanks and cheers,

    Riko

PS: at least, you can remove the SD card from the phone without having to turn the phone off. That helps at least :)

---

### Post by Plueonic on 2012-06-03
That's why I usually don't bother with ROMs from manufacturers. They  always do one thing or another that doesn't make any sense at all..

> **RikoW said:**
> PS: at least, you can remove the SD card from the phone without having to turn the phone off. That helps at least :)
;-)

---

### Post by harun3d on 2012-10-03
still not possible to read sd card in android 4 from ubuntu 12.04?  android 2 asked for making contact between ubuntu and android and it worked.  Now ubuntu enters the sd card directly when connecting the phone to ubuntu computer but it shows only the main folders, not the files under these folders.

---

### Post by gaga654321 on 2012-11-21
Hi!
I had the same issue, after I updated my android 2.3.7 to 4.0.4.
I found one part of the solution:
go to the settings, then xperia, then connecting, then usb-connecting mod
there are two options there:
Media mode and storage mode.
Select the stoage mode. This way you can access to your external uSD card at least.

This way we don't have to take out the external memory card from the phone.
gaga654321

---

### Post by harun3d on 2012-12-11
of course I tried that option of storage mode. I see the upper files but the files under the main files are not visible.

sharing internet connection (tethering) sometimes works sometimes not

---

### Post by Mark Phelps on 2012-12-12
Android ICS removed the ability to mount in USB Mass Storage mode -- for ALL devices running that version of the OS.

---

### Post by skrap on 2013-05-01
Brilliant on someones part

---

