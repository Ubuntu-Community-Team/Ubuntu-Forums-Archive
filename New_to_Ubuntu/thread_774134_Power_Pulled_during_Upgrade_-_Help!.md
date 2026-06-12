---
title: "Power Pulled during Upgrade - Help!"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by brucewagner on 2008-04-29
Here's a real challenge...

On my partner's computer, I clicked on Upgrade...  to upgrade it from 7.10 to 8.04.

When he came in, he got hysterical that I was upgrading his computer..., and in a childish temper tantrum, he hard powered it OFF.

Does anyone have any idea if this process can be recovered without losing what's in his Home directory...?

---

### Post by howlingmadhowie on 2008-04-29
my suggestion would be to use a live cd (for example the standard install cd) and chroot into the old environment:
1/ open a terminal

2/ enter the following, making sure to change /dev/sda1 to the path of your old / drive (you can find possible paths by entering ```
cat /proc/partitions
```)

```
mkdir /olddrive
sudo mount /dev/sda1 /olddrive
sudo chroot /olddrive
sudo apt-get dist-upgrade

```

then you should be able to continue the update. it would however still be a good idea to back up the data using the live cd as well

---

### Post by clairegrrl on 2008-04-29
...and next time, dont be messin' with your guy's computer :)

---

### Post by brucewagner on 2008-04-29
> **clairegrrl said:**
> ...and next time, dont be messin' with your guy's computer :)

:)   Well...  We've just been having a go-round about that.

It's MY job to maintain it.  I am the one he calls when any little thing goes wrong.   But I have no say in WHEN to upgrade to version 8.04.

My side of the story is...  If I have to maintain it, and support it, then it's MY job to take your desires into consideration ("I want everything to Just Work Perfectly Always."), and then it's MY job to determine what gets upgraded and when.

He says he wants to stick with 7.10 until it's "been out for at least 3 months".  But I've been using it for more than 3 months already (in beta).  And by the end of July, the NEXT version will be out in only 3 months more...  I don't like having to maintain two systems that are on different upgrade schedules.

Who's right?    :)

---

### Post by phr0ze on 2008-04-29
As a free maintainer he should give you the call to do an upgrade. I would guess he has nothing to base his 'wait three months' logic. But you have something to base your upgrade to the latest version on. However, although baseless, I'd grant him at least 1 week after the release, then check the forums for any major complaints before upgrading.

I've seen some dual monitor complaints. And maybe you don't use dual monitors during your beta testing, but he does on his system. This is hypothetical of course.

BTW: pulling the cord is just a bad idea all the way around. The damage was already done once the patches started applying.

---

### Post by clairegrrl on 2008-04-29
ummm???...you're both right?  Life's the school and Love's the lesson so we need to be respectful of each other and while you are Mr Upgrade, your guy needs to be able to have some input.  Yes?

---

### Post by brucewagner on 2008-04-29
> **howlingmadhowie said:**
> my suggestion would be to use a live cd (for example the standard install cd) and chroot into the old environment:
1/ open a terminal

2/ enter the following, making sure to change /dev/sda1 to the path of your old / drive (you can find possible paths by entering ```
cat /proc/partitions
```)

```
mkdir /olddrive
sudo mount /dev/sda1 /olddrive
sudo chroot /olddrive
sudo apt-get dist-upgrade

```

then you should be able to continue the update. it would however still be a good idea to back up the data using the live cd as well

Thanks for your help!

Unfortunately, when I get to "sudo apt-get dist-upgrade", I get...

```
root@ubuntu/# sudo apt-get dist-upgrade
sudo: unable to resolve host ubuntu
```

---

### Post by howlingmadhowie on 2008-04-29
> **brucewagner said:**
> Thanks for your help!

Unfortunately, when I get to "sudo apt-get dist-upgrade", I get...

```
root@ubuntu/# sudo apt-get dist-upgrade
sudo: unable to resolve host ubuntu
```

that sounds like it isn't connected to the net. can you use firefox on the live cd?

---

### Post by brucewagner on 2008-04-29
> **howlingmadhowie said:**
> that sounds like it isn't connected to the net. can you use firefox on the live cd?

Yes.   I can use Firefox and I am live on the net on that machine.

Is "ubuntu" a complete enough name for it to find the upgrade repositories...?

---

### Post by brucewagner on 2008-04-29
I have now been able to back-up his entire Home directory to a portable USB drive...

So, maybe the best thing would be to do a fresh install from the Live CD, at this point...  instead of an Upgrade...?   Then, just copy his HOME folder contents back in...?

---

### Post by phr0ze on 2008-04-29
That will pretty much work except for additional applications, and final touches on his system.

---

### Post by howlingmadhowie on 2008-04-29
installing new and copying the data across would certainly do the trick. i wonder where this "not able to resolve ubuntu" came from. the name is certainly to short. is that an entry in the /etc/hosts of the original installation? and if so, why would apt-get want to contact it?

---

### Post by brucewagner on 2008-04-29
For some odd reason...  His GNUCash data file did NOT copy along with the rest of the data.

To say...  He is VERY P-O'ed.   ....would be the understatement of the year.

He's acting like...  It's world war three.

He never made any sort of backup of it.

---

### Post by kansasnoob on 2008-04-29
I experienced a power outage during one upgrade. It was early in the process so when I rebooted GRUB still showed 7.10 during boot (I'm dual booted so GRUB shows up for 10 seconds), so I was able to select recovery mode and get everything back.

My one hang up was knowing what to type in after recovery had completed and I DIDN"T WRITE IT DOWN!!!!!!!!!!! Like the dumb *** I am, I expected to be able to find it on line forever, but I can't.

Anyway I got back to 7.10 with no major flaws and then did the upgrade successfully with no data loss.

Hint ......... do nothing with someone else's computer unless you have permission!

A hint for your roomy: never, ever just hit the power button or pull the plug! DUH!

Screaming and yelling works! Powering off in the middle of anything is BAD!

---

### Post by howlingmadhowie on 2008-04-30
is the GNUCash datafile in a hidden directory? you have to explicitly copy those...

---

