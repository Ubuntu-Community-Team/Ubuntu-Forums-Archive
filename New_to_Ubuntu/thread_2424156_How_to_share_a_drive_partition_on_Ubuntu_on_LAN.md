---
title: "How to share a drive partition on Ubuntu on LAN"
date: 2019-08-04
forum: New to Ubuntu
---

### Post by forkyfork2 on 2019-08-04
A bit of background so my request seems clear enough. I had some major trouble with my hard drive that caused my windows OS to end up being corrupted. I decided to use a spare USB stick that had Ubuntu loaded up to see if I can access my hard drive in order to move my files in an attempt to salvage what I can before getting a new hard drive. Before Ubuntu, I had my drive separated into two partitions. One is the C partition and the other is the D partition which has pretty much everything personal. I completely removed the C partition and installed Ubuntu by following through a simple tutorial. After installing Ubuntu I was extremely relieved to see that I can still access my 'D partition'. I moved the most critical files to a flash stick but I also need to move everything else to a friend's laptop running Windows 7. I fiddled around and found 'Local Network Share' and after setting that up, I found out that I couldn't access the now shared partition on my windows laptop. Apparently it doesn't have permission. I tried a couple of fixes that I found here but it didn't seem to do anything. 

Just now I decided to see if this is a problem on just my 'D partition' or everything. I used Local Network Share on Documents and for some reason it worked perfectly fine. I am now wondering if its just a limitation of some sort due to my peculiar circumstances or am I missing something and my ignorance is just at play here. I do hope that its the latter because when I installed Ubuntu, I made it so my /home partition is 18GB and I have just shy of 400GB of files I need to move from that 'D partition'.

I also want to note that I'm by no means a frequent Ubuntu user and my knowledge is extremely limited. I do thank each and everyone of you for your time helping and educating me regarding my issue.

With kindest regards,
A fork

---

### Post by mastablasta on 2019-08-05
well permissions have to be set up properly. it could be that NTFS file system is interfering here because ti doesn't know the linux permissions. i assume you gave full permission to the folder? linux uses samba server to connect to share files with windows. 

if it doesn't work one way, just share a folder on windows (in the windows network) with linux and move the files from D like that.

both PC have to be in same computer group (i think it defaults to name "workgroup" in windows) for sharing to work. 

also if you set any passwords you would need to enter those before gaining access.

---

### Post by Morbius1 on 2019-08-05
Having a hard time following your post. I did see "Local Network Share" in there somewhere so I'm guessing this is a samba question.

Please post the output of the following commands so we all can deal with some concrete facts:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by Impavidus on 2019-08-05
If you want to do this just once, it may be easier to use usb. Connect an external hard drive via usb, copy all files. I normally use one of those for backups. You may also be able to take the hard drive out of the computer, put it in an enclosure (sata to usb adapter) and plug it into a different computer. I recently did that to save files from my dad's laptop after it died; just took my backup drive out of the enclosure, put the drive from the old laptop in, connected it to a different computer via usb.

BTW: There was no need to install Ubuntu on the hard drive. You could access the D partition from the live disk without installing.

---

### Post by forkyfork2 on 2019-08-06
> **mastablasta said:**
> well permissions have to be set up properly.   it could be that NTFS file system is interfering here because ti   doesn't know the linux permissions. i assume you gave full permission to   the folder? linux uses samba server to connect to share files with   windows. 

if it doesn't work one way, just share a folder on windows (in the   windows network) with linux and move the files from D like that.

both PC have to be in same computer group (i think it defaults to name "workgroup" in windows) for sharing to work. 

also if you set any passwords you would need to enter those before gaining access.

I do believe I gave full permission to the folder per a tutorial  that  told me to. I will try to follow your suggestion of sharing a  folder on  windows and copying the files from Ubuntu to that. Hopefully  that  works. Will update.



> **Morbius1 said:**
> Having a hard time following your post. I did  see "Local Network Share" in there somewhere so I'm guessing this is a  samba question.

Please post the output of the following commands so we all can deal with some concrete facts:
```
testparm -s
```
```
net usershare info --long
```

My bad if I didn't explain my case clearly enough. Basically I'm trying  to share files from an NTFS partition through Ubuntu and I can't get it  to work for some reason.
[testparam -s]("https://pastebin.com/L9zvUHk3")
[net usershare info --long]("https://pastebin.com/5p7bXQ4Y")



> **Impavidus said:**
> If you want to do this just once, it may be easier to use usb. Connect an external hard drive via usb, copy all files. I normally use one of those for backups. You may also be able to take the hard drive out of the computer, put it in an enclosure (sata to usb adapter) and plug it into a different computer. I recently did that to save files from my dad's laptop after it died; just took my backup drive out of the enclosure, put the drive from the old laptop in, connected it to a different computer via usb.

BTW: There was no need to install Ubuntu on the hard drive. You could access the D partition from the live disk without installing.
Appreciate your input. Unfortuantely I don't have a SATA to USB adapter on hand right now nor do I have an external hard drive. I only have a 32 and 16GB flash sticks and although I can use them if I can't come up with a solution, I'm incentivized to find a solution because of how inconvenient it would be to keep using 2 flash sticks to transfer more than 200GB of data. Mind you this computer doesn't even have USB3.0

---

### Post by Morbius1 on 2019-08-06
You have no shares defined. The output of net usershare is this:
> info_fn: file /var/lib/samba/usershares/d25e0ea75e0e8507 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
What you tried to share doesn't exist.

Or it did exist when you created the share but it doesn't exist - or it's not mounted - now.

---

### Post by mastablasta on 2019-08-07
automount: [https://www.binarytides.com/ubuntu-automatically-mount-partition-startup/](https://www.binarytides.com/ubuntu-automatically-mount-partition-startup/)
automount ubuntu docs: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

then share it - give full permission at first, then restrict it, if it's not LAN server and there are multiple users accessing. if oyu have desktop installed this can be done in file manager by right clicking the drive.

---

