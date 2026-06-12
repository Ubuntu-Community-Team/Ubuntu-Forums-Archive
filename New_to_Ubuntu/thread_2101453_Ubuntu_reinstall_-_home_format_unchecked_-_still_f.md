---
title: "Ubuntu reinstall - /home format unchecked - still formatted"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2013-01-04
Hey there!

I just did a fresh re-install due to some upgrade issues. 
My partitions were as follows /home - / - /swap
I checked to format the / partition. /home partition was NOT set to format but it did anyway.

Most of the files are just normal files that I can get again with time, so that's not really a problem. But there was some documents that were really important. Is there any possible way - or any program that might be able to get me some of my documents back?? 

Thanking you

K.m

---

### Post by audiomick on 2013-01-04
It is very possible that you can get a lot of stuff back. I can't tell you how exactly. I think the program dd can do it, but I am not sure.

What is really important is to stop using the drive immediately. Every write operation to the drive reduces your chances of getting things back.

If this is your only computer, you have the option of booting into the live environment to get into the internet and discuss the problem here. You must have an install CD or USB if you just did a re-install. You should be able to unplug the drive and still boot the computer from the live CD or USB. I have done this with my desktop.

---

### Post by kabukiM0n0 on 2013-01-04
> **audiomick said:**
> It is very possible that you can get a lot of stuff back. I can't tell you how exactly. I think the program dd can do it, but I am not sure.

What is really important is to stop using the drive immediately. Every write operation to the drive reduces your chances of getting things back.

If this is your only computer, you have the option of booting into the live environment to get into the internet and discuss the problem here. You must have an install CD or USB if you just did a re-install. You should be able to unplug the drive and still boot the computer from the live CD or USB. I have done this with my desktop.

I'm using a netbook, that's one of the main reasons why I had nowhere to put the documents. I do though have a 4GB Mp3
How does dd work? I see it's command based, and has no GUI
To be more precise, I just want the information that was in my Documents folder.
K.m

---

### Post by sudodus on 2013-01-04
Two other tools are ***testdisk*** and*** photorec***

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

But as audiomick already wrote: don't run the computer booted from this internal drive. ***Shut it down as soon as possible*** and boot a live session from a CD/DVD/USB drive, if it's your only computer.

---

### Post by sudodus on 2013-01-04
> **kabukiM0n0 said:**
> I'm using a netbook, that's one of the main reasons why I had nowhere to put the documents. I do though have a 4GB Mp3
How does dd work? I see it's command based, and has no GUI
To be more precise, I just want the information that was in my Documents folder.
K.m

I think photorec might do the job. Do you remember what file format it was? odt, doc, ... ? But it is a bit messy. odt files are actually zipped, so I think you find them looking for zip files.

---

### Post by kabukiM0n0 on 2013-01-04
> **sudodus said:**
> I think photorec might do the job. Do you remember what file format it was? odt, doc, ... ? But it is a bit messy. odt files are actually zipped, so I think you find them looking for zip files.

There .odt .doc and .jpg 
I'm currently superblocking with testdisk - see if this gives any results.

---

### Post by sudodus on 2013-01-04
> **kabukiM0n0 said:**
> There .odt .doc and .jpg 
I'm currently superblocking with testdisk - see if this gives any results.

Good luck with testdisk!

And if no luck, use the last resort, photorec. It works as long as the data is there on the drive. It needs no file system, but recognizes where files begin and end using typical byte sequences in the data. Recovery of .odt .doc and .jpg is included in photorec, but you have problems if a file is fragmented.

---

### Post by robsoles on 2013-01-04
having preserved /home (and other) partitions on many systems, including a few at work, while re-installing through having the /home folder on its own partition or drive I am rather curious how your reinstallation lost yours this time you did it.

One quick way I can see to ditch your home folder is if it was encrypted before and you took none of the necessary steps to preserve it or if you chose for it to be encrypted this time.

Sorry I don't think of any better solution than those already offered to you at this point but would you mind telling me if encryption is involved in your current loss? If you were previously using an encrypted folder then without the recovery key the data is extremely likely lost with **extreme** difficulty for recovery.

---

### Post by kabukiM0n0 on 2013-01-04
> **sudodus said:**
> I think photorec might do the job. Do you remember what file format it was? odt, doc, ... ? But it is a bit messy. odt files are actually zipped, so I think you find them looking for zip files.

.Zip files are starting to appear! one question though, PhotoRec is creating hundreds of  recup_dir. folders, not even half way through and there's over 150 mainly full of junk. Is there a quick way to sort them? or is that where the painstaking forensic work comes into play?


Thank ever so much anyway. To you and the first guy as well! :popcorn:

K.m

---

### Post by robsoles on 2013-01-04
> **urwhtiwnt said:**
> hello, this is my 1st time in this forum.  i just have a question.  is it easy to move from ubuntu to linux mint?   i like ubuntu 10.10 and i have KDE, LXCE XCFE, kubuntu openbox, and someother weird stuff but i can no longer get updates since it is no longer supported by the ubuntu community.    OR is anyone willing to help me protect it from viruses and all that cuz i believe it is not accepting clamtk or the clamav  or else.  we can even use team viewer.  im sorry, im still trying to learn LINUX

(1) considered Ubuntu 10.04 or 12.04? - both are long term support releases.

(2) Starting your own thread with an even more relevant title to your problem will serve you heaps better.

---

### Post by kabukiM0n0 on 2013-01-04
> **robsoles said:**
> having preserved /home (and other) partitions on many systems, including a few at work, while re-installing through having the /home folder on its own partition or drive I am rather curious how your reinstallation lost yours this time you did it.

One quick way I can see to ditch your home folder is if it was encrypted before and you took none of the necessary steps to preserve it or if you chose for it to be encrypted this time.

Sorry I don't think of any better solution than those already offered to you at this point but would you mind telling me if encryption is involved in your current loss? If you were previously using an encrypted folder then without the recovery key the data is extremely likely lost with **extreme** difficulty for recovery.

Nope, nothing was encrypted. Just a normal /home partition and neither was the format box clicked. 
Some files were password protected, But basic Libre password protected, not with folder encryption.
To be honest - I kind of assumed by now that everything was lost, so everything that comes out of this is just a bonus.

---

### Post by robsoles on 2013-01-04
thanks for the info, I wish it was easier to know why the installer apparently failed/disobeyed.

---

### Post by sudodus on 2013-01-04
> **kabukiM0n0 said:**
> .Zip files are starting to appear! one question though, PhotoRec is creating hundreds of  recup_dir. folders, not even half way through and there's over 150 mainly full of junk. Is there a quick way to sort them? or is that where the painstaking forensic work comes into play?


Thank ever so much anyway. To you and the first guy as well! :popcorn:

K.m

The problem is that the directories and the file names are lost. Maybe you can find some tip browsing the internet. I hope there isn't an enormous amount of zip files.

If I remember correctly there might be some help program, that can use internal file names (some programs save the file name inside the file).

---

### Post by oldfred on 2013-01-05
I had to use photorec once. It takes a long time to sort thru files. I really only wanted text files back, but if found all the old copies also & I had many. So I had to compare old files and was never sure if I found the last saved version. I also now include the file name inside every text file I create.

       Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by cmcanulty on 2013-01-05
I think it maybe wasn't formatted but this happened to me once. You have to not only make sure format is unchecked which I think you did. But also you have to click the partition and select change then click use this partition and select /home ,the default is do not use this partition. This is not clear to everyone when they try a new install, otherwise it is still there somewhere but not as home. You could try the install again and do that and see if it isn't all there

---

