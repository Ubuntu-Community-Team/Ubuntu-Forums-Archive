---
title: "Hash doesn't match for CD install"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by ThunderBill on 2012-09-23
Dell Inspiron 5150 w/ Windows XP Pro is running out of steam and has no room to grow. Not a HD problem nor Ram but OS problem. MS says I can't run W7 (and most likely W8 so my only option was try Linux. Ubuntu seemed like a simple upgrade path but, boy, was that wrong!

What is this nonsense about hash checking? I never had to do anything remotely like that with any Windows package. And then the process doesn't work as advertised. This recommended program, winMd5sum, either doesn't know how to count or the online hash list is wrong. After two tries and most of a day and a half it still can't come up with the right number. In nearly a half century of electronics and computer experience I've never had so much trouble with what should be a simple installation.

It would be great if someone could help get this process back on track and tell me what went wrong.

---

### Post by vexorian on 2012-09-23
This "non-sense" about hash checking is there to prevent you from installing a corrupted version of the ISO you download due to a network issue. If you had to download windows ISOs it would be a good idea to do it as well. Also, if you got the ISO from the official torrent, there should be no problem (torrents do hash checking automatically). It might be annoying the first time, but I guess it would be more annoying if you installed a damaged version of the disk and it destroyed your computer or something...

Anyway, since you are not specifying what ubuntu version you are trying to download. I am gonna guess that you downloaded 12.04**.1** but are looking at the hash listings of 12.04 (without .1). Or maybe your network has disconnect issues and you are not being able to download the image completely. (unlikely but has happened). If you give more details (What is the md5sum you get, what is the list you are checking against, etc).


Here's a trick: When you generate a md5 sum. Try putting it in google. And check out what comes up. If the ISO is correct, chances are that the first result is going to be ubuntu.

---

### Post by Peripheral Visionary on 2012-09-23
The hash checksum is a way of ensuring that the downloaded image wasn't corrupted during the download before you burn it to a CD or DVD. If the checksums don't match, just download the iso again and check to make sure the checksums match.  It's a nice little safety feature, that's all.

---

### Post by audiomick on 2012-09-23
Doing the MD5Sum is a good idea, and is in fact a really simple process normally. I have to admit, though, that I have had exactly the problem that Vexorian described, i.e. I couldn't find a checksum to match the iso I had downloaded. It was a LTS, and I came to the conclusion that the image had been updated, but the checksum had not been updated. I went ahead and installed it, and it all worked fine. Just lucky, I suppose.

---

### Post by jrog on 2012-09-23
> **vexorian said:**
> Anyway, since you are not specifying what ubuntu version you are trying to download. I am gonna guess that you downloaded 12.04**.1** but are looking at the hash listings of 12.04 (without .1).
I'm guessing this is the source of the problem. It's happened to me in the past, and, from what I recall, it was a bit more difficult to find the checksums for 12.04.1 -- I think some of the links on the Ubuntu website (can't find them now) link to 12.04 rather than 12.04.1.

> **vexorian said:**
> Here's a trick: When you generate a md5 sum. Try putting it in google. And check out what comes up. If the ISO is correct, chances are that the first result is going to be ubuntu.
Good advice. Googling for "Ubuntu checksums" might help, too; I think that's how I've had to find 12.04.1 before.

---

### Post by ThunderBill on 2012-09-25
Dell Inspiron 5150 w/ Windows XP Pro is running out of steam and has no room to grow. Not a HD problem nor Ram but OS problem. MS says I can't run Win7 (and most likely W8 ) so my only option was try Linux. Ubuntu seemed like a simple upgrade path but, boy, was that wrong!

What is this nonsense about hash checking? I never had to do anyting remotely like that with any Windows package. And then the process doesn't work as advertised. This recommended program, winMd5sum, either doesn't know how to count or the online hash list is wrong. After two tries and most of a day and a half it still can't come up with the right number. In nearly a half century of electronics and computer experience I've never had so much trouble with what should be a simple installation.

It would be great if someone could help get this process back on track and tell me what went wrong.

---

### Post by einonm on 2012-09-25
Hi,

Some pasting of the commands you are using and output (including the hashes) would be most useful.

The hash basically checks all the bytes of a download and ensures that the downloaded image is not corrupted. If the hashes are different, chances are that the download is corrupted in some way (either during the transfer or writing to disk). 
Exactly the same thing can happen for any file (including windows files), but with hash checking you get to find out about it sooner before you try and install a corrupted OS - and that's a good thing, right? :)

---

### Post by coffeecat on 2012-09-25
Threads merged.

@ThunderBill, please do not post duplicate threads. This dilutes community effort.

---

### Post by Wim Sturkenboom on 2012-09-25
If the hash verification fails, your download (more than likely) is corrupt. Or you're verifying the wrong version.

For reference (not specific for OP):
[http://ubuntu.virginmedia.com/releases/](http://ubuntu.virginmedia.com/releases/), scroll a little down to where you see the directory tree, click your Ubuntu version, scroll again down and click the file 'MD5SUMS'

For a standard 12.04.1 (64bit) desktop, you will find (in that file) that the md5sum is 06472ddf11382c8da1f32e9487435c3d

---

### Post by jrog on 2012-09-25
> **ThunderBill said:**
> What is this nonsense about hash checking? I never had to do anyting remotely like that with any Windows package. And then the process doesn't work as advertised. This recommended program, winMd5sum, either doesn't know how to count or the online hash list is wrong. After two tries and most of a day and a half it still can't come up with the right number. In nearly a half century of electronics and computer experience I've never had so much trouble with what should be a simple installation.
Even though this is a double-post and I'm mostly echoing what others have already said...

First, just because something is different does not mean that it is "nonsense." This isn't nonsense; it's a type of check that increases your security to some degree. The real "nonsense" is that this *hasn't* been done for other packages you've downloaded.

Second, others have tried to help you here. Have you tried their suggestions?

---

### Post by Cheesemill on 2012-09-25
I'm surprised that no-one has pointed you to the official 'How to check Ubuntu MD5SUM' page yet so here it is:

[https://help.ubuntu.com/community/HowToMD5SUM/](https://help.ubuntu.com/community/HowToMD5SUM/)

---

### Post by ThunderBill on 2012-09-25
Many thanks for all the helpful hints. To elaborate somewhat: I've downloaded and installed literally hundreds of Windows programs with NO failures of installations. That's not to say there have been no problems; Some trial packages have proven less than useful and even incompatible with my configuration and desires. None have had the benefit of hash checking nor needed it. 'Nuff said.

The hash that MD5sum generated was: e235b63c02644e219b7bf3668f479c9e. I checked this with Google Search and, as expected, it pointed to the 12.04**.1** release. Someone offered a link for the 64-bit version which obviously would not help for my ancient 5150 P4. The missing link, unless I missed it, seems to be the page containing the codes for 12.04.1. They were not on the page referred to in the installation guide under UbuntuHashes the last time I looked.

I've now burned more than two days on this exercise with little gain. :-(

I'm inclined to scrap the whole hash routine and just burn the CD and install. My only hesitation is prompted by the apparent paranoia of this community. Disturbing to say the least.

---

### Post by Peripheral Visionary on 2012-09-25
> **ThunderBill said:**
> My only hesitation is prompted by the apparent paranoia of this community. Disturbing to say the least.

Well, you asked. If you don't like the answer, go ahead and do as you please. If/when it all falls apart (and it just might work perfectly anyway), don't bother us paranoid community members for help again.

---

### Post by vexorian on 2012-09-25
> 
Many thanks for all the helpful hints. To elaborate somewhat: I've downloaded and installed literally hundreds of Windows programs with NO failures of installations. 
 The same with me and thousands of ubuntu programs. What's your point? 

Really, if you don't like this extra assurance, please go away. I beg you for your own sanity and everyone else's, stick to windows 7. You are complaining of a feature that only improves things and that is not mandatory. I would not want to know what happens when you discover ubuntu has a different user interface.

---

### Post by jrog on 2012-09-25
> **ThunderBill said:**
> Many thanks for all the helpful hints. To elaborate somewhat: I've downloaded and installed literally hundreds of Windows programs with NO failures of installations.
And this is also not a failure of installation. The md5sum check is optional, and it is not a part of installing Ubuntu itself. The installation itself would have succeeded without the md5sum check (assuming no unrelated problems).

Another thing worth thinking about is this. When you installed those Windows programs with "NO failures," did you even try to run an md5sum check on them in those cases? I'm guessing not. So, the fact that you were able to install Windows programs without failures is irrelevant to your failure in this case, because your failure in this case is an md5sum check that you simply skipped in Windows. Since you skipped it, *of course* you never failed at it. If you skipped it here, you wouldn't have failed either. So, the cases seem basically the same.

> **ThunderBill said:**
> None have had the benefit of hash checking nor needed it. 'Nuff said.
Again, checking the hash is not *needed* here -- it is optional. Are you sure that you fully understand what a hash check does? (Here is a link with a brief overview, and a descripton of the sort of case where it is helpful, if you are interested: [http://www.guidingtech.com/9800/what-is-md5-checksum-how-to-verify-it/](http://www.guidingtech.com/9800/what-is-md5-checksum-how-to-verify-it/).) Those Windows programs you installed actually *did* have hashes, whether you were aware of them or not (and so they actually *could* have benefited from hash checking!). Of course, installing those programs didn't *require* hash checking -- but neither does installing Ubuntu. So, basically, both have the capability, neither require it, and only one offers the option.

> **ThunderBill said:**
> The hash that MD5sum generated was: e235b63c02644e219b7bf3668f479c9e. I checked this with Google Search and, as expected, it pointed to the 12.04**.1** release.
This is exactly the solution that was suggested to you in the very first reply to your first post. I'm glad to hear that it worked!

> **ThunderBill said:**
> The missing link, unless I missed it, seems to be the page containing the codes for 12.04.1. They were not on the page referred to in the installation guide under UbuntuHashes the last time I looked.
Could you please provide a link to the installation guide that told you to check the hashes in the first place? I've been reviewing the installation instructions that are linked to from the main download page on ubuntu.com and I can't find that recommendation anywhere, and someone should update any erroneous pages.

> **ThunderBill said:**
> I'm inclined to scrap the whole hash routine and just burn the CD and install. My only hesitation is prompted by the apparent paranoia of this community. Disturbing to say the least.
What do you mean, exactly? (These sorts of suggestions are not very polite, it seems to me.)

---

### Post by critin on 2012-09-26
> **ThunderBill said:**
> Many thanks for all the helpful hints. To elaborate somewhat: I've downloaded and installed literally hundreds of Windows programs with NO failures of installations. That's not to say there have been no problems; Some trial packages have proven less than useful and even incompatible with my configuration and desires. None have had the benefit of hash checking nor needed it. 'Nuff said.

The hash that MD5sum generated was: e235b63c02644e219b7bf3668f479c9e. I checked this with Google Search and, as expected, it pointed to the 12.04**.1** release. Someone offered a link for the 64-bit version which obviously would not help for my ancient 5150 P4. The missing link, unless I missed it, seems to be the page containing the codes for 12.04.1. They were not on the page referred to in the installation guide under UbuntuHashes the last time I looked.

I've now burned more than two days on this exercise with little gain. :-(

I'm inclined to scrap the whole hash routine and just burn the CD and install. My only hesitation is prompted by the apparent paranoia of this community. Disturbing to say the least.

If you use a torrent to download, it should check the sum automatically.  No problems.

Don't get discouraged, a bit of trouble can be worth it.

[ubuntu-12.04.1-desktop-i386.iso.torrent]("http://releases.ubuntu.com/12.04/ubuntu-12.04.1-desktop-i386.iso.torrent")


[]("http://releases.ubuntu.com/12.04/ubuntu-12.04.1-alternate-i386.iso.torrent")

---

### Post by Wim Sturkenboom on 2012-09-26
> **ThunderBill said:**
> Many thanks for all the helpful hints. To elaborate somewhat: I've downloaded and installed literally hundreds of Windows programs with NO failures of installations. That's not to say there have been no problems; Some trial packages have proven less than useful and even incompatible with my configuration and desires. None have had the benefit of hash checking nor needed it. 'Nuff said.
You're lucky :) I've had hundreds of programs failing to download. Sometimes it's obvious (filesize, corrupted zip), sometimes less so.


> **ThunderBill said:**
> 
The hash that MD5sum generated was: e235b63c02644e219b7bf3668f479c9e. I checked this with Google Search and, as expected, it pointed to the 12.04**.1** release. Someone offered a link for the 64-bit version which obviously would not help for my ancient 5150 P4. The missing link, unless I missed it, seems to be the page containing the codes for 12.04.1. They were not on the page referred to in the installation guide under UbuntuHashes the last time I looked.
Your checksum is correct for the 32bit i386 version (see [http://ubuntu.virginmedia.com/releases/12.04.1/MD5SUMS](http://ubuntu.virginmedia.com/releases/12.04.1/MD5SUMS) ). So it's safe to continue.

---

