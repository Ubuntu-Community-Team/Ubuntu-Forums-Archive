---
title: "thinking of (getting back into) Linux"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by punkbohemian on 2008-09-01
I'm not exactly a tech-oriented person. I used to use Linux a little (about 10 years ago), but for the most part have pretty much only used computers to surf the web, play games, and write papers.

I recently got a new computer, and went with a PC, but I'm not impressed with Vista, and was never impressed with Mac OS. What I'm considering doing is making a change to Linux. However, I still have to play nice with Windows because I use it for work. As a result, I'm plan to partition my HD and install both.

One thing I'm wondering, above all things, is if a 160GB HD is going to be enough for both. I'm assuming that Linux is still as elegant and streamlined as it was ten years ago, but Vista is a resource hog (20GB just for the OS, I heard) and I have to put a few other software packages on the Vista side. Anyway, I'm not sure how much space is needed to give Linux enough breathing room.

Also, I'm wondering about cross-OS compatibility of various file formats, particularly word documents. I'd like to do my work on the Linux side, but my documents have to be recognizable by MSWord for work. Is this going to be a problem?

Thanks for any advice.

---

### Post by mellowd on 2008-09-01
> **punkbohemian said:**
>  
Also, I'm wondering about cross-OS compatibility of various file formats, particularly word documents. I'd like to do my work on the Linux side, but my documents have to be recognizable by MSWord for work. Is this going to be a problem?

Thanks for any advice.

No, OOo can read word files. Just one thing, if you're using office 2007 at work be sure to save in the older .doc; .xls format and not the newer .xlsx; .docx etc format

---

### Post by dai_vernon on 2008-09-01
At least not until the new OOo comes out that can process XML standard files from Office.

---

### Post by ctswhole on 2008-09-01
I'm not sure what your hard drive space requirements are, but 160 gigs is still a lot of room.  Ubuntu has really come a long ways in the ease of installation and you can easily partition your hard drive to accomodate both in the Ubuntu installer.

---

### Post by Swenghk on 2008-09-01
I have to use Windows applications for school, OpenOffice is great! I'm actually writing a report in it tonight :)! The joys of Linux

---

### Post by tuxxy on 2008-09-01
If your last experience with linux was 10 years ago and you have yet to try Ubuntu, I think your in for quite a shock by just how far it has developed.  

I dont think youll be wanting to run Vista again, especially if you not a fan now :lolflag:

---

### Post by Trav1s on 2008-09-01
Have you consider Wubi as an option to dabble in ubuntu?

---

### Post by knattlhuber on 2008-09-01
> **punkbohemian said:**
> Also, I'm wondering about cross-OS compatibility of various file formats, particularly word documents. I'd like to do my work on the Linux side, but my documents have to be recognizable by MSWord for work. Is this going to be a problem?

I use OOo and exchange .doc and .docx with Windows users every day. Nobody complained so far.. If push comes to shove, you can always install Crossover and run M$ Office 2007 but you probably won't need to.

---

### Post by jemate18 on 2008-09-01
AbiWord is also great. You can also try it..........

Well for the most part, Ubuntu is targeted for desktop use and that you will find it easy. Shift from Win to Lin NOW!!!!!

---

### Post by punkbohemian on 2008-09-02
First of all, thanks for all the quick responses. When doing research on Linux, I read that the community is very helpful, and you all certainly are. I got about a half dozen responses within 10 minutes. That's pretty fast.

Second, there were a few terms used in your replies that I didn't understand. What is OOo? Is it that Open Office thing I heard about? And what is Wubi?

This next bit could be totally irrelevant. As it's been quite a while since I've been really involved with computers, I might have no idea what I'm talking about here. Just a fair warning. :)

Lastly, my plan is to set up three partitions. One for Linux, one for Vista (I still have to keep it, at least for now), and one as a shared space that both Linux and Vista can access (in case I want to move files between the two). I've read that this is possible, but I'm trying to figure out how I should partition the drives. It almost seems like an arbitrary choice to me.

This actually might end up being more of a Vista question. My main concern with the shared space is more due to what Vista does than what Linux does. Originally, I was going to allocate a conservative amount to space to both Vista and Linux (i.e. 40GB to each OS and 80GB shared space). This way, each system would technically have 120GB of "play" room. However, I'm not sure I should be comfortable with Vista (with all its spyware and inefficient glory) having that much of an overlap with my "workspace" for Linux.

Then I thought I would allocate more generously to the OS partitions, and minimize the shared space. This might look like 60GB for Vista, 80GB for Linux, and 20GB of shared space.

But like I said, this all seems like an arbitrary choice (barring my wariness of Vista). How does one make this decision? Or, is there anything else I should be considering?

Thanks again.

---

### Post by LittleKoy on 2008-09-02
Yes, OO is OpenOffice, a very good opensource Office Suite, very compatible with MS's one ;)

Are you aware of the fact that Linux can read/write into NTFS (Windows) partitions? And what would you use your shared partition for?

---

### Post by punkbohemian on 2008-09-02
> Are you aware of the fact that Linux can read/write into NTFS (Windows) partitions? And what would you use your shared partition for?

To be honest, I'm not entirely sure. I just figured that I'm better off having the ability to move data/files back and forth between the two systems (without dealing with flash drives) than not. Perhaps, in the process of learning, I'll have some kind of catastrophic problem with Linux, have to switch to Vista to get online and find help, and then have to dl a patch/app/etc., which I'll then have to run under Linux. I totally made that up, though, I don't really know.

So Linux could r/w to the partition with Vista? Is the opposite true? Or, more importantly, is there way I can ensure that Vista does <i>not</i> recognize my Linux partition? As you can probably tell, I really don't trust Vista and see it as a necessary evil...at least for now.

---

### Post by LittleKoy on 2008-09-02
By default, Ubuntu can r/w to the Win partition, while Win cannot.
Maybe that 3rd partition is unnecessary? Since Ubuntu can read your Win, you can use the Win partition itself as a swap...

---

### Post by theredcross on 2008-09-02
It is very easy to set up linux with read/write permissions to vista, or any other version of windows. Recently the ext2 drivers for windows were updated for vista, so if you do a pretty easy installation of [http://www.fs-driver.org/](http://www.fs-driver.org/) you should have no problem doing the same thing from vista --> linux.

Cheers

---

### Post by t0p on 2008-09-02
> **punkbohemian said:**
> 
So Linux could r/w to the partition with Vista? Is the opposite true? Or, more importantly, is there way I can ensure that Vista does <i>not</i> recognize my Linux partition? As you can probably tell, I really don't trust Vista and see it as a necessary evil...at least for now.

Linux can read/write to a Windoze (NTFS) partition no problem.  I don't think Windoze can read the Linux partition - at least, not without help.  I believe there's some software available that will enable Windoze to see Linux.  But I used to dual boot (XP and ubuntu) and XP always acted like my hard disk had miraculously shrunk - it never seemed to know it cohabited with another os!

---

### Post by punkbohemian on 2008-09-02
> 
Recently the ext2 drivers for windows were updated for vista, so if you do a pretty easy installation of ... you should have no problem doing the same thing from vista --> linux.


I definitely don't want that. In fact, if I need to disable anything in Vista so it doesn't even know I have Linux, that's what I want to do.

> 
But I used to dual boot (XP and ubuntu) and XP always acted like my hard disk had miraculously shrunk - it never seemed to know it cohabited with another os! 


I hope it works the same way for Vista.

---

### Post by LittleKoy on 2008-09-02
I tried WinXP/Ubuntu too, and 99% Vista is the same..

---

### Post by theredcross on 2008-09-02
Just as a point of interest, I'ved used the ext2 drivers for a while, and I've never had a single problem with windows corrupting my linux drive. I know people who set up a third partition for swapping files, I've just never seen that to be necessary or even desirable.

That being said, windows will not recognize that you have a linux partition at all, and will see it as missing hard drive space. 

Just make sure that if you are going to be doing a fresh install of either, you need to install windows before there are any linux partitions on the whole hard drive. I think I successfully got vista to install on a hard drive with a linux partition on it once, but I haven't been able to repeat it. I am also pretty sure it is impossible with XP, at least I've never seen it.

---

### Post by ugm6hr on 2008-09-02
> But like I said, this all seems like an arbitrary choice (barring my wariness of Vista). How does one make this decision? Or, is there anything else I should be considering?
Yes - it is arbitrary.

It is dependent on:
1. Your views on risk of data corruption.
2. Which OS you plan to make most use of.
3. What you want the data partition for.

To explain:

1. fs-driver allows Vista to read / write to an ext2/3 (Linux) partition;  ntfs-3g allows Ubuntu to read / write to a Vista NTFS partition.  However, both these technologies have a degree of risk, and potentially could cause problems.  I have used both, and routinely use fs-driver with no problems.  If you want 100% native support from both Vista and Ubuntu, a fat32 partition is probably your best bet for the data partition, although it has the disadvantage of no support for 4+GB files.

2. It would be sensible to use a data partition most compatible with the OS you are intending to use most.

3. Using a data partition purely for transfer of files between OS is probably unnecessary, since there is (as far as I know) no real risk in reading data across OS (only potential risk in writing).  Nevertheless, a small partition would suffice for this.  If you want to use it as a true data partition (i.e. as a "My Documents" available from both OS),  then a (much) larger partition would obviously be appropriate.

Vista cannot survive without at least 25-30GB.  Ubuntu (including the default office & drawing apps) will cope with 10GB with plenty of space for applications.  Take this into account - it may be appropriate to allocate more room to Vista if you are intending to use it frequently.

As an example - I dual-boot with XP / Ubuntu (which is essentially identical to Vista / Ubuntu from a partitioning viewpoint in the current ntfs-3g / fs-driver era).  I only boot into Windows once every 3 months or so (if that).  Hence I created a separate /home partition (essentially an Ubuntu equivalent to My Documents), so all Ubuntu files are saved there as default.  I use fs-driver in XP to access those files.

So - in summary - the choices to be made are essentially arbitrary, albeit with a sensible framework available, it can seem more rational.

---

### Post by alzie on 2008-09-02
When you partition your drive, I'd recommend (personally)
1 Vista Drive
2 Common Drive
3 Ubuntu Drive
The common drive can also be used as storage for windows downloads and items that you can't afford to lose in case of an OS meltdown.

That way you can safely reformat C: and not lose your data and downloads.  Been there, done that.

Otherwise I defer to ugm6hr.

---

### Post by punkbohemian on 2008-09-02
> To explain:...

That was pretty comprehensive. Thanks for spelling it out.

Ideally, I would like to eventually be using Vista as little as possible, though I'm going to have to rely on it more at first while I'm learning the ins and outs of Linux. The reason for the smaller partition for Vista is because I intend to (eventually) use Linux for everything I can. Vista will merely be around just in case I happen to need it for something.

> 
...a fat32 partition is probably your best bet for the data partition, although it has the disadvantage of no support for 4+GB files.


I'm not sure how concerned I should be about this. I don't think I even have any files that are that size or bigger. However, I had also considered using this extra partition as a space to back up important personal documents and whatnot (20Gb should be plenty for that). I figure a zipped up folder could possibly exceed 4GB. OTOH, using a NTFS partition could result in in the archive being improperly written. Either way, there's (potential) problems, right?

All in all, I don't mind if Linux can access everything, but I want to keep Vista on a short leash.

---

### Post by kansasnoob on 2008-09-02
IMHO you're making this much more complicated than it needs to be. First of all pick an Ubuntu based live CD distro, OK I'm prejudiced, I simply find Ubuntu to surpass all other Linux distros in so far as simplicity and, well, just being able to get things working!

Run the Live CD, and then run the Live CD, and then run the Live CD some more! Then when you're ready to give it a real try use a guide like this:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

to dual boot. I've tried Wubi and Vmware and I still prefer a dual boot. But it's all a matter of choice. Now the guide I posted is for dual booting w/Vista, don't try that with XP!

But if you have as little as 6gb to spare on your hard drive I'd try a dual boot. I suggest more space ......... at least 10gb, and given todays drives 20gb is reasonable, but this is not a huge deal.

Just be prepared! For instance if you hate it you're going to want to restore Vista's mbr:

> If you have no disc you can get one here:

[http://neosmart.net/blog/2008/window...disc-download/](http://neosmart.net/blog/2008/window...disc-download/)

Instructions here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You want to "fix boot" and "fix mbr"!

But first of all try the Live CD and then do some system specific research!

---

### Post by ugm6hr on 2008-09-02
> Either way, there's (potential) problems, right?
There is no perfect answer - otherwise you'd have easily found it yourself.

Remember, fs-driver and ntfs-3g are widely used without problems by the vast majority. I may have inadvertently over-emphasised the risk involved.

---

### Post by hopkinsjeni on 2008-09-02
I use an external hard-drive for files I save in .doc (microsoft word) format and that seems to work pretty well. I know it may be a pain to have that extra bit of kit with you but as you eventually switch over your documents you'll need it less and less. It's just a thought.

---

### Post by The Cog on 2008-09-02
Don't forget that you also want a swap partition for Linux - a couple of gigs should do. And you might want to consider using a separate home partition so you can upgrade/reinstall linux without trashing your data. I actually use 3 partitions - one /home partition and two / partitions for different Linux versions - I try out the next release before wiping the previous one. You need 5G-10G for the system partitions, a default install fills around 3G.

If you really want to ensure that Vista can't read your Linux partition you could use a filesystem windows can't read such as JFS. But an intruder is unlikely to install ext2 drivers, and Vista could always just overwrite the Linux partitions regardless of whether or not it can understand their contents.

---

### Post by punkbohemian on 2008-09-04
Considering these recent replies, I looked up some stuff on swaps and partitions.

> Don't forget that you also want a swap partition for Linux

Some of what I read said that swap partitions are unnecessary with the newer distros and that swap space can be created with swap file. What I didn't see any info about are the benefits of one method over another. Does it matter?

> 
I actually use 3 partitions - one /home partition and two / partitions for different Linux versions.


I want to make sure I understand. How this works is that there are two partitions, each about 5-10GB in size, which house just your OSs. Then there's the /home partition (ext2/3 format I assume), which stores all your apps, personal stuff, etc. Finally, there's a couple gigs of a swap partition (also ext2/3 format?). Additionally, in my case, I'd also have a partition that would be housing Vista (at least until I get really cozy with Linux). Does that sound about right?

Thanks.

---

### Post by The Cog on 2008-09-04
Swap partition is the normal way to do it with Linux. Swap file is possible, but I gather performance isn't as good - swap partition layout is optimised for use as swap, not storing multiple files. You can run without a swap area at all, but why restrict your machine? A couple of gigs of disk space won't be missed. 

You got it - two system partitions and a /home for data/docs etc. that they can both share. In Linux, your program settings etc also go in your home folder so you can safely wipe and reinstall the / system and retain all your settings etc. I only configure a new system to use the separate /home once I have tested it for a while and am happy. For the initial install I let it use a home folder on its root partition, all quarantined.

 I forgot to mention the swap partition but you are right, it's there. The swap partiton is formatted as a swap partition, not ext3. My desktop also has a Windows partition (my wife sometimes wants ot use windows, I don't). Total 4 partitions, also unused sapce held in reserve. I suggest putting all but the Windows partiton inside an extended partition for greatest flexibility. Actually, my laptop also has a manufacturers utilities partition ans a windows partition so it has 5 partitions.

---

### Post by dmurat on 2008-09-04
i dont know what you really use for work. but if the only thing you need is MS Office and such programs i would say dont go for Vista at all. (i dont know if photoshop and autocad and such programs have alternatives for linux)

i was using Windows for 10 years (98/XP/Vista) and switched to linux yesterday. i was really afraid that i might not cope with linux and took the risk of formatting again and switching back to vista. but i now see that the only thing you need to get used to linux is the Ubuntu forums =)) you already have firefox so the only thing you have to do is ask what you want to learn here.

i am really surprised of how posts are replied quickly here and the problems are solved really fast. so i guess there is no reason for Vista...
i am now happy with ubuntu and at least for now, not thinking of switching to anything else =))

just wanted to share my experience of switching from win to linux recently =))

---

