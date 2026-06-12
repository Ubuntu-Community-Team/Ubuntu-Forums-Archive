---
title: "SD Card issue with Compaq mini 110c after Ubuntu 14.04 LTS"
date: 2015-11-16
forum: New to Ubuntu
---

### Post by christos9 on 2015-11-16
Hello and good evening ;)

Sorry If i posted this in the whrong section, I am kinda new to these forums and I feel like a new to ubuntu community(I do use debian for my server for a while now)... Well... To get to the point...

I installed Ubuntu 14.04 LTS on an SD Card, which worked quite nicely for quite a while -around two/three months+ or so since it's install- 
On the netbook said in the title (Compaq mini 110c). 

I did install ubuntu into an SD card(Transcent 8GB) because I wanted to make sure it wouldn't mix the system/harddrive I used to have... A few weeks later(around 2 weeks ago), I had to remove the laptop's harddrive in order to help a friend with some backup. I gave him my harddrive for a few days which worked perfectly and keeps working properly for my "home" pc (Windows 7, SATA II) aswell now.

Everything worked perfectly fine with the netbook aswell without the harddrive for around 4 or so weeks, as the system was installed into the SD Card. 

The whole problem showed up yesterday night... Which was kinda confusing... I was working on the netbook *Just because sometimes we love ubuntu more than windows*... Anyway... I saved all my work(mostly php files at that time) and left it on as I went to eat(around 10 minutes). When I returned, it was in "sleep mode" (not sure how it's called in ubuntu, sorry) I was like "I'll just finish that spesific script and then quit for the night".

I pressed spacebar(to wake it up) and logged into my account, as usually... The strange part was that I couldn't write anything to the "disk" aka(read only permissions) while around 20 minutes ago everything was working properly... and I was like, "I'll restart it..." Well, it shutdown properly(no issues nor taking too much time), but when it tried starting, I got "stuck" into the Compaq logo screen(boot screen). And it keeps doing so...

What I worked out; is. The pc boots properly from a live USB into ubuntu(if the SD card isn't "plugged in"), but it stucks if it boots with the SD card "plugged in". Also if the card is plugged in, and it gets stuck into the Boot Screen I can't seem to be able to access BIOS aswell. If I try to connect the card while I run the system with live CD i don't even see it connecting

This is the first time this happened to me, and am not sure what to do. I also tried to mount the SD card in an SD camera with no results viewing files... or any responce at all... Which is kinda strange(maybe it-camera- doesn't *understand* the filesystem). I didn't try plugging it into a windows pc, because I don't have an external SD card reader... And I am kinda lost...

Any help is welcome! I would like to thank you in advance just for reading the post! If you need any further info, feel free to reply and I'll post as soon as possible(I am online in the evenings)

---

### Post by christos9 on 2015-11-18
Anyone...? I don't want to have a wasted SD card...

---

### Post by QIII on 2015-11-18
My first suspicion would be that the SD card (SD cards are not robust and have a very limited number of read/write cycles) simply "wore out" at some important location where a lot of read/write cycles ocurred just in the course of operation.

---

### Post by sudodus on 2015-11-18
If you are lucky, it is 'only' a damage of the file system, and it can be repaired from a live Ubuntu system

```
sudo e2fsck -f /dev/sdxy
```

where x is the drive letter and y is the partition number (of the partition of Ubuntu in the SD card), for example /dev/sdb1

Otherwise, there might be a hardware (physical or electronic) damage of the SD card. See also this link (about pendrives, but the flash memory in memory cards are similar to the memory hardware and electronics in pendrives).

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

---

### Post by christos9 on 2015-11-18
Interesting link and info in the "sub-links"... I learned a lot! Seems like it indeed "wore out".

I executed the command for the SD card(in my case "sdb") which failed, I didn't think of copy paste the whole text... Altho I wrote down this line(I am replying with my win7 pc)

[COLOR=#555555][FONT=Verdana]"Superblock could not be read or does not describe a valid ext2/ext3/ext4 filesystem"[/FONT][/COLOR]

I also executed the commands it suggested(didn't include the part of the commands and so on) resulting to the same error... I am assuming that the card has come to it's end... pitty.
I guess I'll have to reinstall ubuntu on it's harddrive now. 

Anyway ^^ I really appreciate your help and info! Learned quite a lot! ;)

---

### Post by sudodus on 2015-11-18
You are welcome and good luck with the re-install on the hard disk drive :-)

---

