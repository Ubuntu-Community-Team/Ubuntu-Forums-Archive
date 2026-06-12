---
title: "Install Help! :S  ;)"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by victorsdmp on 2008-07-01
Dear All,

I have an old Compaq Armada E500 laptop (P-III 700Mhz 128Mb RAM and 8Gb HDD) which I refuse to decommission since we have become good friends ;)... Therefore I went for the xbuntu 8.04 alternate CD installation. I have followed these steps:

a) download the iso file
b) extract the iso contents of the file to the HDD
c) burn a CD with the files that came out of the iso file
d) format C: + blank reboot
e) check BIOS (everything OK)
f) blank reboot with CD inserted and...

... nothing happens. Obviously I am doing something badly.
Could you please help me in this issue. The BIOS is OK.
Regards,

Víctor

---

### Post by Marshal0505 on 2008-07-01
> **victorsdmp said:**
> Dear All,

I have an old Compaq Armada E500 laptop (P-III 700Mhz 128Mb RAM and 8Gb HDD) which I refuse to decommission since we have become good friends ;)... Therefore I went for the xbuntu 8.04 alternate CD installation. I have followed these steps:

a) download the iso file
b) extract the iso contents of the file to the HDD
c) burn a CD with the files that came out of the iso file
d) format C: + blank reboot
e) check BIOS (everything OK)
f) blank reboot with CD inserted and...

... nothing happens. Obviously I am doing something badly.
Could you please help me in this issue. The BIOS is OK.
Regards,

Víctor

extract iso ?? that's where it went wrong.U need to burn the iso file to cd.

---

### Post by lisati on 2008-07-01
Normally you would burn the complete ISO file as a disk image, rather than try to extract the files first.
Have a look here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Canis familiaris on 2008-07-01
Does your notebook support booting from CDROM? I think it does but you need to enable it from the BIOS, i.e. select CDROM as first boot device, then insert the CDROM and install.
EDIT: You should burn the ISO to the disk not the extracted files.

---

### Post by victorsdmp on 2008-07-01
wow, that was fast, thanks to all... 

so let's see: I burn the iso file to a CD, place the CD with the iso file in the blank computer and it should self-extract and install alone? don't I need something else?...

Thanks again!

---

### Post by Marshal0505 on 2008-07-01
> **victorsdmp said:**
> wow, that was fast, thanks to all... 

so let's see: I burn the iso file to a CD, place the CD with the iso file in the blank computer and it should self-extract and install alone? don't I need something else?...

Thanks again!

burn it to cd , reboot your computer and make sure you changed your bios settings to 'boot from cd' OR ....press F8 during boot to select your boot device and choose 'cdrom' when this presents a list.

(hope i didn't confuse matters further)

---

### Post by victorsdmp on 2008-07-01
OK got it right, thanks to all: happy surfing mates! :)

---

### Post by Sef on 2008-07-01
> so let's see: I burn the iso file to a CD, place the CD with the iso file in the blank computer and it should self-extract and install alone? don't I need something else?...

Just need to click on a button at times.   I believe 6 for the graphic installer.

---

### Post by Mornedhel on 2008-07-01
Do not just burn the .iso file to the cdrom, ending up with a cdrom with a single .iso file on it... You have to tell your burning application to specifically "burn the ISO image", not just drag'n'drop the .iso file to your CD.

Once this is done, the same files you extracted on your previous attempt should be present on the CD, with the nontrivial difference that the CD will now be bootable (images carry more information than just files, or everyone would just be using .zip or whatever). Then set your BIOS to try to boot from the CDROM before the hard drive. This is not difficult at all, but the exact manipulation varies from BIOS to BIOS.

Then pop in the CD, reboot, and step through the installation process. By the way, all OS installers come equipped with the possibility to reformat drives, so you don't need to do that beforehand.

---

### Post by hyper_ch on 2008-07-01
have a read here for burning:  [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

