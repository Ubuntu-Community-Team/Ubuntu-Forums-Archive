---
title: "Recovering files from inaccessible BSOD on windows 8"
date: 2014-01-15
forum: New to Ubuntu
---

### Post by spencercampo on 2014-01-15
Hi!
I'm trying to recover my files after my windows 8 [crashed and burned]("http://www.eightforums.com/bsod-crashes-debugging/38669-confusing-bsod-several-errors-error-code-0xc000000f.html#post327524"). I've successfully booted ubuntu from a usb drive and now I'm trying to find my files to copy to an external. Ubuntu automatically recognized my windows drive and it's partitions but no files are visible when I try and use Nautilus to navigate to them. I tried the steps in this [wikihow]("http://www.wikihow.com/Access-Windows-Files-in-Ubuntu") even though it seemed to me that it was already mounted just for fun. At this command: mount -t ntfs /dev/sda5 /mnt/windows -o "unmask=022" I get back:

Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

I assume that is because it was automatically mounted by Ubuntu already, but I'm not familiar with linux at all.

[http://imgur.com/qQzcNnR](http://imgur.com/qQzcNnR)
[http://imgur.com/6c6KPuY](http://imgur.com/6c6KPuY)

---

### Post by Dave_L on 2014-01-15
What's the output from:
```
mount
```

---

### Post by Habitual on 2014-01-16
> **spencercampo said:**
> /dev/sda5 /mnt/windows ...

Mount is denied because the NTFS volume is already exclusively opened.
while it is supposedly mounted, open a terminal  and issue
```
lsof +D /mnt/windows
```

output please.

---

### Post by spencercampo on 2014-01-16
```
mount
```
output: [http://imgur.com/JTGUs9B](http://imgur.com/JTGUs9B)

```
lsof +D /mnt/windows
```
output: [http://imgur.com/xckOkGV](http://imgur.com/xckOkGV)

sorry for having to take pictures of my screen, hope that's not too annoying. Thanks for your help!

---

### Post by spencercampo on 2014-01-21
any help? what are the outputs of those commands telling ya'll? Should I move on to trying to put my HDD in an external enclosure?

---

### Post by Habitual on 2014-01-21
Imgur is over capacity!

I'll check those links later...

---

### Post by Habitual on 2014-01-21
ok. I'd try ```
sudo umount /media/ubuntu/B69 <[COLOR=#ff0000]press tab for completion[/COLOR] here>
```
and then remount it with

```
sudo mount -a
```

and then navigate to the volume and attempt file recovery.

---

### Post by spencercampo on 2014-01-22
> **Habitual said:**
> ok. I'd try ```
sudo umount /media/ubuntu/B69 <[COLOR=#ff0000]press tab for completion[/COLOR] here>
```
All I'm getting is "command not found" bounce backs, am i doing something wrong?
[http://imgur.com/inFeoMN](http://imgur.com/inFeoMN)

If it makes a difference:
After getting the "command not found" bounce backs from ```
sudo unmount
``` I opened GParted and unmounted the volume by right clicking and selecting "unmount." I then tried remounting it with ```
mount -t ntfs /dev/sda5 /mnt/windows -o "unmask=022"
``` That mounted the volume but when I went to the /mnt/windows folder via Nautilus there was only the "Windows" folder and "Logs" as before. I then unmounted it again with GParted in the same way and remounted using ```
sudo mount -a
``` This also remounted the drive under Devices but still only the "Windows" and "Logs" folder. :?

---

### Post by Habitual on 2014-01-22
"unmount" is not umount

---

### Post by spencercampo on 2014-01-22
haha, that's true...:oops:=D>

Using the correct commands still no improvement, can't seem to see anything but /Windows/Logs/PBR

also looking at Gparted again it's strange that it recognizes the 289GB volume but says only 131MB is used. That's definitely not true unless everything was wiped.

---

### Post by westie457 on 2014-01-22
@ spencercampo

Could you start Gparted and post a screen shot of the partition layout of the HDD that contains Windows please.
Your issue sounds similar to the one in this thread. [http://ubuntuforums.org/showthread.php?t=2200198](http://ubuntuforums.org/showthread.php?t=2200198)

If I am wrong it might be quicker to repair Windows with a repair CD. If you do not have one, this link might help you.

---

### Post by spencercampo on 2014-01-22
> **westie457 said:**
> @ spencercampo

Could you start Gparted and post a screen shot of the partition layout of the HDD that contains Windows please.
Your issue sounds similar to the one in this thread. [http://ubuntuforums.org/showthread.php?t=2200198](http://ubuntuforums.org/showthread.php?t=2200198)

If I am wrong it might be quicker to repair Windows with a repair CD. If you do not have one, this link might help you.

Is this all you're asking for? Sorry if it isn't, I'm not sure if there is a more detailed partition layout. [http://imgur.com/G25Q18J](http://imgur.com/G25Q18J)

Also it didn't seem relevant but whenever GParted starts I recieve an error "The backup GPT table is corrupt, but the primary appears OK, so that will be used."

I don't think I have the same problem regarding using a Wubi system. I am using a Live USB stick and when prompted to "Install" or "Trial" I just click the trial to run off the USB because I didn't want to risk overwriting the files I'm trying to recover. I also don't see a "File System" icon on the left panel of Nautilus or a /host folder, but that might be cuz I'm a linux noob.

And I don't have a legit Windows repair CD, I got one off a torrent that I might try and use via USB but I thought I'd try this first before messing with Windows. Thanks ya'll again for all your help! <3

---

