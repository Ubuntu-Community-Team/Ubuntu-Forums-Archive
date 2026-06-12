---
title: "Burning Ubuntu ISO to DVD bootable"
date: 2009-04-08
forum: Philippine Team
---

### Post by Johnaray on 2009-04-08
Hi guys,

Help naman po! I need to have a DVD bootable copy of Ubuntu. Yung Toshiba Laptop L20 ko kasi ayaw na mag basa ng CD purely DVD lang ang binabasa nya.

I have a UBUNTU CD here but its not booting on my Old laptop. so here is what I already did. 

I have a UBUNTU ISO but when I try burning it on DVD it was read still as a CD thus my old laptop did not recognize it. 

I also tried copying the entire content of UBUNTU CD and burn it on DVD but still not bootable....

I planning to give up since I tried different approach to it such as burning ISO using DEEPBURN, NERO, Etc. just to name a few.

Is there any way to burn a CD ISO To a DVD Bootable.... Thanks in advance....


BTW I already spent wasting 30 DVD just to replicate but all failed... buti na lang mura DVD sa CDRking :p

---

### Post by killer_d76 on 2009-04-08
try a different approach.. does it have a USB port?.. try booting thru USB.. or if you have an external USB DVD that woulb be better since you mentioned you already have CD/DVD.. or try to create a start up bootable USB drive.. perhaps that would help as well.

o and by the way, have you tried testing those CD/DVD on your working desktop or laptop?, just to check if the CD/DVD's are okey.. perhaps it can be the DVD drive of your laptop.. if so try installing ubuntu through USB drive..

another option is to pull-out the HDD of your Toshiba Laptop L20 and plug it on another working laptop and then install ubuntu.. now if your Toshiba laptop is using an IDE HDD and your new laptop is using a SATA HDD, you could get an IDE to USB adaptor (bring the HDD with you when you buy the adaptor, CD-R King have one! ) and install Ubuntu thru USB to IDE adaptor then put it back in your Toshiba Laptop L20 and fire it up!. ;)

---

### Post by Johnaray on 2009-04-08
> **killer_d76 said:**
> try a different approach.. does it have a USB port?.. try booting thru USB.. or if you have an external USB DVD that woulb be better since you mentioned you already have CD/DVD.. or try to create a start up bootable USB drive.. perhaps that would help as well.

o and by the way, have you tried testing those CD/DVD on your working desktop or laptop?, just to check if the CD/DVD's are okey.. perhaps it can be the DVD drive of your laptop.. if so try installing ubuntu through USB drive..

another option is to pull-out the HDD of your Toshiba Laptop L20 and plug it on another working laptop and then install ubuntu.. now if your Toshiba laptop is using an IDE HDD and your new laptop is using a SATA HDD, you could get an IDE to USB adaptor (bring the HDD with you when you buy the adaptor, CD-R King have one! ) and install Ubuntu thru USB to IDE adaptor then put it back in your Toshiba Laptop L20 and fire it up!. ;)

Gee thanks dude! but my old laptop does not have the capacity for booting thru USB...already tried updating the BIOS but no option to boot on USB, Hmmmmm I already tried checking the HDD and its a SATA... do you think will it work if I purchase a SATA to IDE converter then I will just plug my SATA HDD to my desktop and there install UBUNTU then return it back to my Laptop....

But again my main concern is  Burning Ubuntu ISO to DVD bootable so that I can run the LIVE CD or should I say DVD of Ubuntu...

Again Thanks killer_d76 and I will defenitely consider those info. :biggrin:

Anymore Idea guys on Burning Ubuntu ISO to DVD bootable 

Thanks again in advance

---

### Post by killer_d76 on 2009-04-08
> **Johnaray said:**
> I already tried checking the HDD and its a SATA... do you think will it work if I purchase a SATA to IDE converter then I will just plug my SATA HDD to my desktop and there install UBUNTU then return it back to my Laptop....

But again my main concern is  Burning Ubuntu ISO to DVD bootable so that I can run the LIVE CD or should I say DVD of Ubuntu...

installing UBUNTU using SATA to IDE converter will work!.. i have installed Ubuntu on different laptops using this process.. now for you to run live CD /DVD.. perhaps some guys here have a better idea! :)

---

### Post by lisati on 2009-04-08
The first time I installed Ubuntu on my older Toshiba laptop, I had to use the "alternate" installation disk. And don't forget to burn the ISO as a disk image.

---

### Post by loell on 2009-04-08
maybe the writing capabilities of the device is already toast?

you can also try a converter script

```

#!/bin/bash

# by Chris Kloiber <ckloiber@redhat.com>

# A quick hack that will create a bootable DVD iso of a Red Hat Linux
# Distribution. Feed it either a directory containing the downloaded
# iso files of a distribution, or point it at a directory containing
# the "RedHat", "isolinux", and "images" directories.

# This version only works with "isolinux" based Red Hat Linux versions.

# Lots of disk space required to work, 3X the distribution size at least.

# GPL version 2 applies. No warranties, yadda, yadda. Have fun.


if [ $# -lt 2 ]; then
echo "Usage: `basename $0` source /destination/DVD.iso"
echo ""
echo " The 'source' can be either a directory containing a single"
echo " set of isos, or an exploded tree like an ftp site."
exit 1
fi

cleanup() {
[ ${LOOP:=/tmp/loop} = "/" ] && echo "LOOP mount point = \/, dying!" && exit
[ -d $LOOP ] && rm -rf $LOOP
[ ${DVD:=~/mkrhdvd} = "/" ] && echo "DVD data location is \/, dying!" && exit
[ -d $DVD ] && rm -rf $DVD
}

cleanup
mkdir -p $LOOP
mkdir -p $DVD

if [ !`ls $1/*.iso 2>&1>/dev/null ; echo $?` ]; then
echo "Found ISO CD images..."
CDS=`expr 0`
DISKS="1"

for f in `ls $1/*.iso`; do
mount -o loop $f $LOOP
cp -av $LOOP/* $DVD
if [ -f $LOOP/.discinfo ]; then
cp -av $LOOP/.discinfo $DVD
CDS=`expr $CDS + 1`
if [ $CDS != 1 ] ; then
DISKS=`echo ${DISKS},${CDS}`
fi
fi
umount $LOOP
done
if [ -e $DVD/.discinfo ]; then
awk '{ if ( NR == 4 ) { print disks } else { print ; } }' disks="$DISKS" $DVD/.discinfo > $DVD/.discinfo.new
mv $DVD/.discinfo.new $DVD/.discinfo
fi
else
echo "Found FTP-like tree..."
cp -av $1/* $DVD
[ -e $1/.discinfo ] && cp -av $1/.discinfo $DVD
fi

rm -rf $DVD/isolinux/boot.cat
find $DVD -name TRANS.TBL | xargs rm -f

cd $DVD
mkisofs -J -R -v -T -o $2 -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table .
/usr/lib/anaconda-runtime/implantisomd5 --force $2

cleanup
echo ""
echo "Process Complete!"
echo ""
```

---

### Post by Johnaray on 2009-04-08
Thanks Loell...

but is there a laymans term that is much easier...I know its challenging but... *NOSE BLEED*

To be honest, I even don't know how to execute them huhuhuhuhu...
Im still tied with my windows XP here some I'm clueless...

again thanks dude... now there is something I'm looking forward to review specially how to run those codes.

---

### Post by loell on 2009-04-08
you still have XP? might be easier with nero.

anyway in ubuntu to execute this script,
copy paste the script on a text editor (gedit) , save it as convert.sh
then put the script to the directory where the ISO file is located, then execute the converter.

```
sh converter.sh
```

---

### Post by Ticketoride on 2009-04-08
> **Johnaray said:**
> I planning to give up since I tried different approach to it such as burning ISO using DEEPBURN, NERO, Etc. just to name a few.

Is there any way to burn a CD ISO To a DVD Bootable.... Thanks in advance....
Nero 8/9, as well as UltraISO have a DVD Checkbox when you want to burn a CD ISO to DVD-R.

Just associate either Programs with ISO, then just click on the ISO Image, check the DVD Box, stick in your blank Disk and burn away.

Since you would have at least 3.5 GBs of DVD-Disk Space left, UltraISO lets you pack in other Files of your Choice too to fill up the rest of the Disk.

---

### Post by Johnaray on 2009-04-09
> you still have XP? might be easier with nero.

anyway in ubuntu to execute this script,
copy paste the script on a text editor (gedit) , save it as convert.sh
then put the script to the directory where the ISO file is located, then execute the converter.


Thanks Loell, may bago nanaman akong kaalaman! :KS mukhang magiging suking tagatanong mo ako dito ah hehehehe :lolflag: Thanks thanks thanks again.

> Nero 8/9, as well as UltraISO have a DVD Checkbox when you want to burn a CD ISO to DVD-R.

Just associate either Programs with ISO, then just click on the ISO Image, check the DVD Box, stick in your blank Disk and burn away.

Since you would have at least 3.5 GBs of DVD-Disk Space left, UltraISO lets you pack in other Files of your Choice too to fill up the rest of the Disk.

@Ticketoride, Thanks for the information... mukhang ito na nga hanap ko! :p (I guess I need to have a trip to my friends at QUIPO or GREENHILLS to buy those software :lolflag: )

AGAIN THANKS THANKS THANKS TO ALL!!!

I'll be posting the result once I was able to replicate the processes! :KS:KS:KS

---

