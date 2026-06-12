---
title: "Photorec - Testdisk"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by catalytic on 2008-10-15
I think I've manage to loose my files while trying unsuccessfully to re install windows. Somehow the ubuntu partitioner changed the whole partition to ext3 instead of just resizing..anyway I've then gone and installed ubuntu over the top of it. I would like to try and recover the photo's of my daughter from birth that were on there. 

Sigh....I got the program working finally....but I don't understand how to use it. To me it looks like its all gone and all thats left is linux partitions...all I need is for someone to tell me if the files are still there and what options I need to select. 

 2 E extended              1958   0  1  2969 254 63   16257780
 3 * Linux                 2970   0  1  9728 254 63  108583335
Invalid NTFS boot
 5 L HPFS - NTFS           1958   1  1  2781 254 63   13237497
 5 L HPFS - NTFS           1958   1  1  2781 254 63   13237497
   X extended              2782   0  1  2969 254 63    3020220
 6 L Linux Swap            2782   1  1  2969 254 63    3020157

If I select number 5 which I'm pretty sure is where my files were, I get this screen

     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  1957 254 63   31455207
L Linux                 1958   1  1  2781 254 63   13237497
L Linux Swap            2782   1  1  2969 254 63    3020157
P Linux                 2970   0  1  9728 254 63  108583335

Sort of figured it out, I've listed the files, but don't see the ones I'm looking for, is there another function in the program to recover the lost files?

---

### Post by bryncoles on 2008-10-16
have you followed the guide on the photorec website?

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

i think its pretty straightforward, but then ive never really used photorec for anything! i know you need a separate hard disc of at least equal size to the one you're trying to recover from though. photorec needs somewhere to put the files its retrieving - otherwise it'll just write over the files as its recovering them, if you see what i mean. 

if you installed ubuntu over the data though, it might be hard to recover stuff... have you considered using a professional service? depends how important the data is, and how disposable your income is i suppose...

sorry i cant be more help! good luck with your data recovery though...

---

### Post by bumanie on 2008-10-16
I have used testdisk a few times, but not photorec. From within ubuntu you could try to use ntfsprogs, specifically ntfsundelete. Again, as said above you need to save the data to a different disk/partition that is of at least equal size with partition you are trying to recover. > sudo apt-get install ntfsprogsHere is the [man page]("http://manpages.ubuntu.com/manpages/hardy/man8/ntfsundelete.html") for ntfsundelete - hope it helps.
As far as photorec goes, I think you have to firstly choose the partition you want to recover from and then choose file types to search for ie jpeg, png etc.

---

