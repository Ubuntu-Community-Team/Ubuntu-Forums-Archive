---
title: "burning dual layer disks"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by Matt26 on 2008-09-28
is there any particular reason why i would not be able to burn a dual layer dvd in ubuntu 8.04?  i don't know if i'm doing something wrong or if there is an issue in ubuntu that is preventing me from burning the disc.  all i get when i try burning the disc is a message that states there was error recording...

EDIT: i just tried burning the dvd under K3b and this failed as well (fatal input/output error) so i am thinking that maybe there is something missing on my ubuntu system that is not allowing me to burn the dual layer discs?

any suggestions would be greatly appreciated.

thanks.

---

### Post by crjackson on 2008-09-30
> **Matt26 said:**
> is there any particular reason why i would not be able to burn a dual layer dvd in ubuntu 8.04?  i don't know if i'm doing something wrong or if there is an issue in ubuntu that is preventing me from burning the disc.  all i get when i try burning the disc is a message that states there was error recording...

EDIT: i just tried burning the dvd under K3b and this failed as well (fatal input/output error) so i am thinking that maybe there is something missing on my ubuntu system that is not allowing me to burn the dual layer discs?

any suggestions would be greatly appreciated.

thanks.

Does it work under any other OSs for you?

---

### Post by Therion on 2008-09-30
Is it a dual-layer capable burner?

---

### Post by Matt26 on 2008-10-01
Yes, this is dual layer capable burner.

And yes i have used this burner many times in the past to burn dual layer discs under Windows XP.

Further to the info i provided below, i have done some research on what ubuntu requires to burn dual layer discs- from what i have read thus far, i have all the required packages installed on my system, so i am confused by this- what could i be missing here?

---

### Post by halitech on 2008-10-01
Have you checked to see if maybe there is a firmware update for the burner? the other option I can think of is the burner is on its way out (hope not but they do die)

will it still burn single layer dvds?

---

### Post by Matt26 on 2008-10-01
i'll check for the firmware update... i can burn single layer dvds and cds fine so i'm not sure that the drive would be failing..

---

### Post by Matt26 on 2008-10-01
is there a way to view hardware information in ubuntu?  i'd rather not pull my drive out of the case just to see the model number written on it...

---

### Post by halitech on 2008-10-01
I use gutsy so might be different in hardy if you have it but if I got to System - Preferences - hardware info I was able to find the model and firmware versions on the advanced tab

---

### Post by ricardisimo on 2008-10-01
I had a problem with them as well, and was led to believe that it had something to do with the type of blanks I was using... DVD-R as opposed to DVD+R, or some such nuance. I'd love to find out what the deal is. Thanks for posting.

---

### Post by Forbees on 2008-10-01
you could try Nero for Linux

i like it, havent tried a dual layer yet but it should work

you can get the free trial off their site somewhere

or torrent the full version :)

---

### Post by Matt26 on 2008-10-01
> **ricardisimo said:**
> I had a problem with them as well, and was led to believe that it had something to do with the type of blanks I was using... DVD-R as opposed to DVD+R, or some such nuance. I'd love to find out what the deal is. Thanks for posting.

that was one of the first things i checked out- i have dvd+r dual layer discs... k3b says my drive supports these discs and not the -r variety so i think i'm safe there..

---

### Post by Matt26 on 2008-10-01
> **Forbees said:**
> you could try Nero for Linux

i like it, havent tried a dual layer yet but it should work

you can get the free trial off their site somewhere

or torrent the full version :)

well i have tried at least 3 or 4 separate burning applications and so far they have all crashed when i try to burn these discs.

---

### Post by Forbees on 2008-10-01
but nero is god of burning :-p

---

### Post by ricardisimo on 2008-10-01
> **Forbees said:**
> but nero is god of burning :-p

Nero lost me a year or two before I switched to Ubuntu. I forget the details now, but the version they offered back five or so years ago was great. I think k3b matches up favorably. Does Nero still offer the applet to print disc covers? That was a nice detail.

---

### Post by Matt26 on 2008-10-01
> **Matt26 said:**
> is there a way to view hardware information in ubuntu?  i'd rather not pull my drive out of the case just to see the model number written on it...

found out how to access the hardware via the post below in case anyone is wondering where that screen disappeared to...
[http://ubuntuforums.org/showthread.php?p=4762233](http://ubuntuforums.org/showthread.php?p=4762233)

---

### Post by Forbees on 2008-10-01
> **ricardisimo said:**
> Nero lost me a year or two before I switched to Ubuntu. I forget the details now, but the version they offered back five or so years ago was great. I think k3b matches up favorably. Does Nero still offer the applet to print disc covers? That was a nice detail.

not in the linux version

the linux version is alot like their nero 6

the disk conver/lightscribe didn't come around till 7 :(

---

### Post by Matt26 on 2008-10-01
> **halitech said:**
> Have you checked to see if maybe there is a firmware update for the burner? the other option I can think of is the burner is on its way out (hope not but they do die)

will it still burn single layer dvds?

no luck thus far on a firmware upgrade for the drive... i'll keep searching but if anyone has any other suggestions in the meantime please let me know!

---

### Post by ricardisimo on 2008-10-01
What does "sudo lshw" tell you about the burner?

---

### Post by Matt26 on 2008-10-01
> **ricardisimo said:**
> What does "sudo lshw" tell you about the burner?

here is the output from that command for my dvd drive:

cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-4120B
                vendor: HL-DT-ST
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: A115
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open


the device manager screen provides much of the same details.

so i guess ubuntu isn't recognizing this drive as dual layer capable- funny thing is, k3b lists dvd+r dl as supported media for this device, which are the discs that i have been trying to use with no success.

help?

---

### Post by Matt26 on 2008-10-02
> **Forbees said:**
> but nero is god of burning :-p

well unfortunately nero failed me- however it also (like k3b) indicates that my burner supports the dvd+r dl media...

are there any related system settings or packages that i should be checking for that may not be set correctly or present?  i'm not sure what else to check.

---

### Post by markbuntu on 2008-10-02
Are these memorex disks?

Many people have reported problems using memorex disks in Ubuntu with their burners though they work in windoze. I had this problem amd thought my burner was broken but I got a TDK disk and that worked. Verbatim disks also work.

---

### Post by halitech on 2008-10-02
have you tried a different brand of dvds? maybe its not the burner but the actual dvds

---

### Post by Matt26 on 2008-10-02
> **markbuntu said:**
> Are these memorex disks?

Many people have reported problems using memorex disks in Ubuntu with their burners though they work in windoze. I had this problem amd thought my burner was broken but I got a TDK disk and that worked. Verbatim disks also work.

interesting you ask- they are indeed memorex disks... i will get some new ones and see what happens..

---

### Post by richg on 2008-10-03
I

---

### Post by ricardisimo on 2008-10-03
> **Matt26 said:**
> interesting you ask- they are indeed memorex disks... i will get some new ones and see what happens..

Awaiting with baited breath...

---

### Post by Matt26 on 2008-10-06
well i learned something new that i wasn't aware was possible- an OS that doesn't like a certain brand of DVDs... weird.

i bought a pack of Verbatim dual layer DVDs and sure enough, they worked...

thanks for the suggestion!

---

### Post by Matt26 on 2008-10-06
i also learned that Nero does appear to top k3b- at least in this case anyways... i tried recording the dvd in k3b first as a standard dvd video disc- burn process completed successfully (although the verification process crapped out because the desk was ejected after writing was finished) but my dvd player wouldn't read it as a dvd... went through the same process with nero (which completed both the burning and verify process successfully) and my dvd player read the disc fine...

maybe the verification process being aborted had something to do with the k3b-produced disk not working...?  in any event, nero prevailed.

---

### Post by ricardisimo on 2008-10-07
> **Matt26 said:**
> well i learned something new that i wasn't aware was possible- an OS that doesn't like a certain brand of DVDs... weird.

i bought a pack of Verbatim dual layer DVDs and sure enough, they worked...

thanks for the suggestion!

That sucks big-time. i just spent bank on a pack of lightscribe Memorex DVDs. Uggh!

---

### Post by Matt26 on 2008-10-07
> **ricardisimo said:**
> That sucks big-time. i just spent bank on a pack of lightscribe Memorex DVDs. Uggh!

i'm guessing that you already opened them?  if not you could always try returning them...

---

### Post by ricardisimo on 2008-10-10
Hmmm... mine are behaving a bit differently. The lightscribe 4.4s worked just fine, by the way, although no lightscribing yet. Installing LaCie is a bit too much work for me. I'm going to wait until a complete utility is in the ubuntu repositories.

The Dual-layers were recognized just fine by whatever utility I tried, but the resulting DVDs won't read in any players I've tried. At least I won't have to toss the LS disks.

---

