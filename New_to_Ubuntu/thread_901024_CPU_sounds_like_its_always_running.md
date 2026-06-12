---
title: "CPU sounds like its always running"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by jethier on 2008-08-26
Hi:My CPU sounds like it's constantly running and it makes quite a racket. I can't concentrate on what I'm trying to read.

System monitor says CPU1 is running 15% and CPU2 running 15 - 20%. All I'm doing is reading a web page, nothing else. 

Anyone know how I can stop it?

---

### Post by Jr. on 2008-08-26
BIOS? It's the fan making the sound, right? Edit your BIOS, it may be set to not allow dynamic fan control pending CPU temp.

---

### Post by jethier on 2008-08-26
> **Jr. said:**
> BIOS? It's the fan making the sound, right? Edit your BIOS, it may be set to not allow dynamic fan control pending CPU temp.

Don't sound like the fan. The fan is sort of a low hum but the sound that's bothering me is louder. Can't explain it any better than that at the moment.

Maybe it's the hard drive?

---

### Post by Jr. on 2008-08-26
Take the side of your case of a find exactly where the sound is coming from. 3 things make sound:

1.Fan
2.HDD
3.CD/DVD Drive

---

### Post by xeth_delta on 2008-08-26
> **jethier said:**
> Don't sound like the fan. The fan is sort of a low hum but the sound that's bothering me is louder. Can't explain it any better than that at the moment.

Maybe it's the hard drive?

Could you be referring to a high-pitch whine? A lot of computers produce this sound under certain conditions, but that one is not very loud. It is not limited to Linux.

---

### Post by jethier on 2008-08-26
> **Jr. said:**
> Take the side of your case of a find exactly where the sound is coming from. 3 things make sound:

1.Fan
2.HDD
3.CD/DVD Drive

It's definately 2. Hard drive. making a hell of a racket. Now that I have that figured out, why is it so loud/anything I can do about it?

---

### Post by jethier on 2008-08-26
Now that I've thought about it the sound is ticking sound. tick tick tick tick tick pause tick tick tick pause tick tick.

Really annoying.

---

### Post by Jr. on 2008-08-26
Sounds like a hardware issue maybe??? Is it a new HDD? Was it in another system, old, dropped on the floor?

---

### Post by xeth_delta on 2008-08-26
> **jethier said:**
> Now that I've thought about it the sound is ticking sound. tick tick tick tick tick pause tick tick tick pause tick tick.

Really annoying.

Does that sound like a regular sound of HDD heads moving to a different position to read/write?

---

### Post by jethier on 2008-08-26
> **Jr. said:**
> Sounds like a hardware issue maybe??? Is it a new HDD? Was it in another system, old, dropped on the floor?

I've had HDD problems in the recent past with this computer (computer freezing) when I was running Windows. I took the computer back and they changed the HDD out (or so they say, I never looked), it worked good for a while then all the same errors I had were recurring. I took it back again and they said it's fine (will never buy a computer at this place again). Worked fine for awhile then same problems again. 

Then I loaded UBUNTU and it's worked fine for a few months. No freezing problems at all but now this noise. Might have to buy a new HDD.

---

### Post by jethier on 2008-08-26
> **xeth_delta said:**
> Does that sound like a regular sound of HDD heads moving to a different position to read/write?

Yes it does, but going constantly.

---

### Post by Gone fishing on 2008-08-26
Are you running beagle - if so the noise could be caused by beagle building an index. If you turn Beagle off does the noise go away.

If your not using an indexing program I'd suggest a hardware problem if its very noisy a hardware problem.

---

### Post by jethier on 2008-08-26
> **Gone fishing said:**
> Are you running beagle - if so the noise could be caused by beagle building an index. If you turn Beagle off does the noise go away.

If your using an indexing program I'd suggest a hardware problem if its very noisy a hardware problem.

From what I can see in Add/remove programs I do not have beagle installed.

---

### Post by Jr. on 2008-08-26
Ahhh, indexing. Could be that... When did it start? What did you do just before it started? And how long has it been happening?...


However, If you had issues with it in Windows and Linux, I'd say it's not software but hardware. Although they are different issues (errors/weird sounds) they could be related. New HDD might be in order... I always say broken parts is just a chance to upgrade :D

---

### Post by prshah on 2008-08-26
> **jethier said:**
>  tick tick tick tick tick pause tick tick tick pause tick tick.


My money is on HDD. 

Here's how you can confirm; both methods require a live CD.

Method 1) Simple and fast; disable the HDD in the BIOS; then boot off the live CD and work a while; do you still get the "tick..tick.."?

Method 2) Complex and long, but definative: Enable HDD in the BIOS, but boot off the live CD; unmount all mounted partitions from the hdd; now check the hdd for bad sectors (this is a safe, read-only test):```

sudo umount /dev/sda1
#Assuming /dev/sda is your hdd; unmount all partitions (sda1, sda2, etc) except swap
sudo badblocks -v /dev/sda1
#repeat the above command for each sda1, sda2, etc except swap.

```

the output will be a counting progress of blocks being checked. If any blocks are found bad, the block number will be printed on a line by itself, and the progress counting will continue.

If you suspect any badblocks are found, post the output here, for a permanent solution.

If this isn't it, you may want to read about [linux laptop bug]("http://ubuntuforums.org/showthread.php?t=795327") The title is slightly misleading, but the post contains more details, including checking, solution, etc. 

Note that neither of the two above may be your problem; but it's a starting point.

---

### Post by jethier on 2008-08-26
> **prshah said:**
> My money is on HDD. 

Here's how you can confirm; both methods require a live CD.

Method 1) Simple and fast; disable the HDD in the BIOS; then boot off the live CD and work a while; do you still get the "tick..tick.."?

Method 2) Complex and long, but definative: Enable HDD in the BIOS, but boot off the live CD; unmount all mounted partitions from the hdd; now check the hdd for bad sectors (this is a safe, read-only test):```

sudo umount /dev/sda1
#Assuming /dev/sda is your hdd; unmount all partitions (sda1, sda2, etc) except swap
sudo badblocks -v /dev/sda1
#repeat the above command for each sda1, sda2, etc except swap.

```

the output will be a counting progress of blocks being checked. If any blocks are found bad, the block number will be printed on a line by itself, and the progress counting will continue.

If you suspect any badblocks are found, post the output here, for a permanent solution.

If this isn't it, you may want to read about [linux laptop bug]("http://ubuntuforums.org/showthread.php?t=795327") The title is slightly misleading, but the post contains more details, including checking, solution, etc. 

Note that neither of the two above may be your problem; but it's a starting point.

Thanks, I will try both tomorrow, have to goto bed.

I appreciate the help from everybody!!

---

### Post by xeth_delta on 2008-08-26
> **jethier said:**
> Yes it does, but going constantly.

I know the sound. I believe I managed to get rid of it a couple of times in the past (even if the current HDD on my laptop is really quiet and cannot here it almost at all). I will try to remember how I did it, but right now I am really to tired and need some sleep.

Maybe something new has appeared in the forums, perform a search for the problem.
Anyway, here is a couple of old threads discussing this:
[http://ubuntuforums.org/showthread.php?t=331418](http://ubuntuforums.org/showthread.php?t=331418)
[http://ubuntuforums.org/showthread.php?t=484941&highlight=harddisk+activity](http://ubuntuforums.org/showthread.php?t=484941&highlight=harddisk+activity)

Don't know how up to date they are anymore.

---

### Post by xeth_delta on 2008-08-26
[EDIT] before following this suggstion in 8.04, please read posts #19 and #20

Hmm, one more thing you could try, from an old post of mine. In that case it was targeting power consumption, but it might do the trick here, too.

First of all, make a back-up of /etc/fstab. Open a terminal and
```
sudo cp /etc/fstab /etc/fstab-backup
```

Open with root privileges and edit /etc/fstab with any text editor of your preference. For example:

For gedit
```
gksudo gedit /etc/fstab
```
For nano
```
sudo nano /etc/fstab
```

Search for the line associated with the partition mounted as "/". For example:

```
UUID=some_uuid_generated    /    ext3     defaults,errors=remount-ro     0 1
```

In that line "/" specifies the partition with the respective uuid is mounted as "/", it is formatted in ext3. The fourth column, starts with "defaults". Add noatime after "defaults", so that the line will look like:

```
UUID=some_uuid_generated    /    ext3     defaults,noatime,errors=remount-ro     0 1
```

Changes will be valid starting from the next time the partition is mounted, in the case of the / partition, it will be next time you boot.

This taken from [http://ubuntuforums.org/showthread.php?t=800770](http://ubuntuforums.org/showthread.php?t=800770) post #16

---

### Post by prshah on 2008-08-26
> **xeth_delta said:**
> Add noatime after "defaults", so that the line will look like:

Hardy comes with partitions mounted with "relatime" by default. Using "noatime" has issues with (some) mail service clients not being able to see correctly when new mail has arrived. (Though admittedly, that seems to be relevant only in a server environment.)

However, the performance/power saving between "atime" and "relatime" is minor; on hardy, it's better off to leave it at "defaults".

---

### Post by xeth_delta on 2008-08-26
> **prshah said:**
> Hardy comes with partitions mounted with "relatime" by default. Using "noatime" has issues with (some) mail service clients not being able to see correctly when new mail has arrived. (Though admittedly, that seems to be relevant only in a server environment.)

However, the performance/power saving between "atime" and "relatime" is minor; on hardy, it's better off to leave it at "defaults".

Fair enough, I did not know that, as I use the option and haven't had any problems of that kind. That said I do not use my computer as a mail server. I have added a small note to my original post.

Indeed, it's quite unlikely that's the reason in his case for the frequent disk access, but I think it was worth a try. The main reason for me to use that was merely improving battery life (as it is suggested in powertop).

---

