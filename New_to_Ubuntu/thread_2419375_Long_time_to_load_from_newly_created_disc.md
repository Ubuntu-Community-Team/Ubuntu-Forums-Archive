---
title: "Long time to load from newly created disc"
date: 2019-05-21
forum: New to Ubuntu
---

### Post by simonf2 on 2019-05-21
I am still using W7 but looking to move eventually to Linux.

I created a disc and then booted from same.  The DVD drive spent some 10 minutes chuntering away and during this time I got a black screen with a great deal of data.  On this it said that it had "failed to start dispatcher daemon for systemd-networkd." 

Eventually Ubuntu loaded as a live version (if that is correct term) and seemed to work ok.  I just wondered if anyone had any thoughts on whether this is normal beginning and whether it is safe to install from this disc.

Also, I have already created a partition.  I understand that I can install alongside W7 but as I go through the installation process will it give me the opportunity to say I want to use this partition?

Many thanks.

---

### Post by Rubi1200 on 2019-05-21
Hi,

Well, booting from a live medium is usually always going to be slower than once installed to the HD but of course it can also depend on the computer specs., quality of the optical drive etc.

There are often messages that flash across the screen during booting both live and installed. Most of them can usually be ignored especially if you reached the desktop.

The Ubuntu installer will offer a number of options for installing but in your case you would choose the Install Alongside or Something Else.

Install Alongside means it will make space and boot together with Windows (or other operating systems). Practically speaking, it might mean it will shrink Windows further depending on how much space you had to begin with.

Something Else means you manually choose where to install, what mount points to use, what file system etc.

In terms of comfort level I suggest using the Install Alongside option.

Before you proceed, please post here the make and model, specifications like graphics card, RAM etc. of the computer.

And, also post how much space you created on the drive. If possible, a screenshot would help.

Once we have more information we can advise you on the best way to proceed.

Thanks.

---

### Post by simonf2 on 2019-05-21
Thank you for responding so quickly.

I have "played" with Linux before but by making my laptop dual boot I hope to make a true transition away from Windows (eventually).

The DVD does play up (freezes occasionally when playing DVDs) but as you say, I did reach the desktop and everything seemed to work ok.

I have booted from a USB before now so could do that again - I just didn't have a memory stick so used a disc.

I would like to do everything I can to make the installation as stable as possible so that I can make a true judgement of whether Ubuntu is for me.

The laptop is a Dell Latitude 3540 with Intel I5 processor.

Graphics card - under device manager it lists both AMD Radeon HD 8850M and Intel (R) HD Graphics Family.  I am not sure if this is the right information.

I have 12 MB of Ram.

In terms of partitions I have:

39 MB Healthy (OEM)
12.25 GB Healthy (System, Active, Primary)
404.65 GB Healthy (Boot, Page File, Crash Dump, Primary)
48.83 GB (Unallocated)

Once again, many thanks.

---

### Post by Rubi1200 on 2019-05-21
The specifications look fine to me as is the amount of space you allocated for Ubuntu.

But, here is the thing, I always only use manual partitioning even when erasing and using the entire disk. What that means is that I am a bit wary about recommending the Install Alongside option in case Ubuntu decides to shrink your Windows partition further.

Two options: either using manual partitioning by selecting Something Else or wait for others who have used the Install Alongside feature to comment on whether that will work right now with your setup.

If you choose manual I can guide you through the process.

---

### Post by oldrocker99 on 2019-05-21
It is **MUCH** faster to burn the image to a USB thumb drive. Here's the official Microsoft USB burner: [https://www.microsoft.com/en-us/download/windows-usb-dvd-download-tool](https://www.microsoft.com/en-us/download/windows-usb-dvd-download-tool).

Just burn the .iso to the USB the same way you did the DVD.

Good luck with THAT, and certainly pay close attention to the above advice. When installing, selecting "Something Else" when it offers to install. Then, if you are distching Windows, which I definitely recommend, create a 32-64 system / partition. Format ext4, and then make a second partition, then mount it as /home. Keep it backed up, of course, and subsequent installations will be a breeze.

Good luck!

And search for solved problems, and ask away if you can't find one. The Ubuntu community is very helpful, as are all Linux communities. 

And don't be shy. Every one of us was a clueless n00b when we started, and it is a pleasure to help someone new all of us.

---

### Post by simonf2 on 2019-05-21
Thanks both for all the help.  I am going to replace my memory stick which has failed and will install from that noting comments re partition et al.  Will do a post when I am up and running.

I really appreciate that help is forthcoming, I am sure I will need it as I go forward with this.

---

### Post by oldrocker99 on 2019-05-22
BTW, when you're burning a USB, format it as **FAT** only, otherwise, it will fail.

---

### Post by simonf2 on 2019-05-24
Thanks for that.  Re USB drive - I seem to only have the option to format as FAT32 not FAT - is this the same please?  (I am using Windows 7).  Thanks.

---

### Post by Rubi1200 on 2019-05-24
FAT32 is fine for the USB stick, should not be a problem.

---

### Post by simonf2 on 2019-05-25
Many thanks - have now installed Ubuntu so thanks again to all.

---

