---
title: "A fistful of begginners questions"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by ProPyro on 2008-05-01
Hello, I recently started using Linux after being raised on windows.  Now I have a handful of questions that I'm kind of stuck on and would greatly appreciate some help on.  First off I'll point out that I stopped pretending to know anything about computers after I dropped out of Computer Engineering in college years ago, so I'll need explanations to be given to me in simple terms if you don't mind.  Also I'd like to apologize if you guys have been getting these exact questions thrown at you all the time, thanks for any help you can give me.

1. How do you format a disk?  Sadly I'm used to the whole "right click/format" method of formatting a disk with windows, Linux has me totally lost on this.  I have an external hard drive thats formatted in NTSF and I'd like to make it some format that both Linux and windows can read and write to so it can be swapped around between computers in my house when needed.

2. Currently I'm using version 7.04, but I was told that with 7.10 there was a problem with the auto updater and that you can't update.  Is this true or has this issue been corrected?

3. I use Thunderbird to check my email because it's what I used to use when I was on windows and because it had the Lightning 0.8 add on that allowed it to function as a calendar.  I tried to install the Linux version of Lightning and it won't allow me to because the version of Thunderbird available for Ubuntu is only 1.50.14.  Lightning 0.8 needs version 2 or higher to work, is this something that will be corrected if I upgrade to version 7.10 of Ubuntu or are we stuck with a lower version of Thunderbird?  If I could get Evolution Mail to work with my gmail account I'd use that, but it doesn't seem to let me specify ports with the mail servers.

4. I use an iPod and I'm wondering what you guys would recommend as a good program to edit content on it.  I like to keep a meticulous level of detail with the file organization on that thing so I'd need to be able to edit all the information on the ID3 tag as well as support adding album art to the files much like how iTunes worked.  I know Rythmbox supports iPods but I'm having a bit of difficulty figuring out how to use it.

---

### Post by agim on 2008-05-01
ntfs can be read by both.

haven't heard of this problem in 7.10, which I used until last month.

You will be able to use Thunderbird 2.0 in Ubuntu 8.04, I would suggest running the livecd to see how it will work. There have been reported problems, as is has just been released, but I haven't had any.

Can't help you with the ipod though. I hear amarok is pretty good with it.

---

### Post by Gepetto on 2008-05-01
> **ProPyro said:**
> 

1. How do you format a disk?  Sadly I'm used to the whole "right click/format" method of formatting a disk with windows, Linux has me totally lost on this.  I have an external hard drive thats formatted in NTSF and I'd like to make it some format that both Linux and windows can read and write to so it can be swapped around between computers in my house when needed.
Linux can read NTFS natively, so you shouldn't need to format it. If you do reformat it, Windows can't read ext3 natively, so your best bet is to stick with NTFS

> 2. Currently I'm using version 7.04, but I was told that with 7.10 there was a problem with the auto updater and that you can't update.  Is this true or has this issue been corrected?
If you mean 8.04, then I haven't heard that there's any issue with the auto updater (it's been working for me fine). It may just be that the servers were really slow since everybody is trying to update at the same time.

> 3. I use Thunderbird to check my email because it's what I used to use when I was on windows and because it had the Lightning 0.8 add on that allowed it to function as a calendar.  I tried to install the Linux version of Lightning and it won't allow me to because the version of Thunderbird available for Ubuntu is only 1.50.14.  Lightning 0.8 needs version 2 or higher to work, is this something that will be corrected if I upgrade to version 7.10 of Ubuntu or are we stuck with a lower version of Thunderbird?  If I could get Evolution Mail to work with my gmail account I'd use that, but it doesn't seem to let me specify ports with the mail servers.
Eruh, The Thunderbird available from the repositories is 2.0.0.12, I'm running it right now.

> 4. I use an iPod and I'm wondering what you guys would recommend as a good program to edit content on it.  I like to keep a meticulous level of detail with the file organization on that thing so I'd need to be able to edit all the information on the ID3 tag as well as support adding album art to the files much like how iTunes worked.  I know Rythmbox supports iPods but I'm having a bit of difficulty figuring out how to use it.
I'm currently using Amarok to work with all my media. I'm not sure how meticulous you need to be, but Amarok seems to provide all necessary options and such.

---

### Post by ProPyro on 2008-05-01
Thanks a lot, but the problem I was having was that I can't write to NTFS.  I want to be able to use this hard drive to back up things from my computer and all I can do is read.

> **Gepetto said:**
> Eruh, The Thunderbird available from the repositories is 2.0.0.12, I'm running it right now.
Ok, because I'm using 7.04 and all it lets me download from the add programs list was version 1.5 so I guess if I update that will fix that.

---

### Post by cartisdm on 2008-05-01
> **ProPyro said:**
> Thanks a lot, but the problem I was having was that I can't write to NTFS.  I want to be able to use this hard drive to back up things from my computer and all I can do is read.

What error are you getting when you try to write to NTFS?

---

### Post by linuxjuicer on 2008-05-01
itunes can be installed in ubuntu :)

---

### Post by iSplicer on 2008-05-01
There are plenty of guides relating to ipods and Ubuntu, and formatting using the Ubuntu install CD is nothing but right click and format anyway =)

Good Luck!

---

### Post by ProPyro on 2008-05-01
> **cartisdm said:**
> What error are you getting when you try to write to NTFS?

"**Error while copying to "/media/External HD".**
You do not have permissions to write to this folder."

and I can't change any of the permissions, their all grayed out.  I was told that Linux just can't write to NTSF because it's a copy written windows algorithm or something.

> **linuxjuicer said:**
> itunes can be installed in ubuntu :)
Do you mean running it with wine or something?

---

### Post by Tatty on 2008-05-01
If you are using 7.04 (feisty fawn) then you might need to install the NTFS3G driver to use an ntfs drive, see this link [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Later versions come with this driver pre-installed.

---

### Post by iSplicer on 2008-05-01
> **ProPyro said:**
> "**Error while copying to "/media/External HD".**
You do not have permissions to write to this folder."

and I can't change any of the permissions, their all grayed out.  I was told that Linux just can't write to NTSF because it's a copy written windows algorithm or something.

What version are you using?

Try this in a terminal;

```

sudo apt-get install ntfs-3g
```

---

### Post by ProPyro on 2008-05-01
I'm using 7.04, Fiesty Fawn.  I used the terminal command to get the NTFS driver and it didn't take effect immediatly and it didn't ask me to restart, so I either did something wrong or I have to look into this "FUSE" user group it mentioned that can now mount NTFS drives as the terminal mentioned it.

---

### Post by captkit on 2008-05-02
You can format your external drive to the fat32 file system using either ubuntu or windows. With ubuntu use the partition editor, which is "gparted" if you have to get it from synaptic. In the upper right hand corner of the editor's window is a selector to pick out the external from your other drives. Make sure you have the right one. You don't want to partition a drive with your data on it. The editor gives you controls to set the file system and the size of the partitions. Play with it until you see how it works. You might want to put up more than one partition with different file systems on them. To format in windows, I believe you find your drive in My Computer then click on "format" in properties. fat32 is a file system that works with both windows and linux. I have a similar disk that I use to move data between the two OS's. It's been working fine from Dapper 6.06 right on through. Sorry I can't walk you through it. I'm a rank beginner too.

---

