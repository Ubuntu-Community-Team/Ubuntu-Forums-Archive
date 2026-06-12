---
title: "[SOLVED] Partimage, how to use it?"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by ctoaun on 2008-06-08
How on earth is one supposed to use to the Partimage backup program?
>
 First, I couldn't launch  it to save my life. Yes, I went to the website. Apparently, it's theme is, "The antithetical relationship between our documenation and precise, concise user friendly writing." I was expecting writing on par with Symantec's ghost or Acronis. Can someone please help?

Thanks,

---

### Post by avtolle on 2008-06-08
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage) may help you out.

---

### Post by |{urse on 2008-06-08
Partimage is great ^^ check out sysresccd. It provides partimage and a bunch of other easy to use hd management apps.

[http://www.google.com/search?q=sysrescuecd&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=sysrescuecd&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

If you want something easy like ghost try g4l (ghost for linux)

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

or read the partimage manual

[http://www.partimage.org/Partimage-manual](http://www.partimage.org/Partimage-manual)

---

### Post by ctoaun on 2008-06-08
> **avtolle said:**
> [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage) may help you out.

This was working until I arrived at the part where one is to type a backup destination. Partimage refuses any typing.
Thanks anyway

---

### Post by ctoaun on 2008-06-08
> **|{urse said:**
> Partimage is great ^^ check out sysresccd. It provides partimage and a bunch of other easy to use hd management apps.

[http://www.google.com/search?q=sysrescuecd&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=sysrescuecd&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

If you want something easy like ghost try g4l (ghost for linux)

[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

or read the partimage manual

[http://www.partimage.org/Partimage-manual](http://www.partimage.org/Partimage-manual)

I previously looked at system rescue. Besides having the efect of overkill with respect to my goals, it unfortunately, has partimage, which does not work as advertised, see above. I am going to try g4l. I'll keep everyone posted. Grazi for pointing me in a new direction

---

### Post by pjnsmb on 2008-06-08
[http://quickstart.phpbb.net/index.php](http://quickstart.phpbb.net/index.php)

have a look at this great little programme...........

---

### Post by |{urse on 2008-06-09
> **ctoaun said:**
> I previously looked at system rescue. Besides having the efect of overkill with respect to my goals, it unfortunately, has partimage, which does not work as advertised, see above. I am going to try g4l. I'll keep everyone posted. Grazi for pointing me in a new direction

LOL it surely does work, and well. I use a few programs when i create image-on-disc system recovery dvd's for our customers and it wouldn't be possible without partimage. Just because you can't figure it out doesn't mean it doesn't work ^^ keep trying! And stick with gzip compression, bz2 is to slow to be worth the trouble.

---

### Post by mgranet on 2008-06-09
You might also try CloneZilla, which uses partimage. It's available as a LiveCD, and I find it quite straight forward.

@**"sparior"**: Classy.

---

### Post by ctoaun on 2008-07-12
> **mgranet said:**
> You might also try CloneZilla, which uses partimage. It's available as a LiveCD, and I find it quite straight forward.

@**"sparior"**: Classy.

Thanks for the recommendation and thanks to the Taiwanese, the originators of Clonezilla. Correct? 

Anyway,people like me deeply resent it when Linux gurus say that new people like myself are afraid of the terminal and or need GUIs. The truth is that people like me love to learn and to tinker. The frustration comes from instructions that include but are not limited to one or more of the following: Misplaced/dangling modifiers and or step 2 omits steps 2a-2m before going to step3.

For windows users, 70% of the challenge of Linux is not Linux; it's the quality of documentation, which when compared to windows, is often times substandard. I hate spending two hours to do 20 minutes worth of work.

Partimage documentation is terrible and needs to be rewritten

---

### Post by ctoaun on 2008-07-12
> **|{urse said:**
> LOL it surely does work, and well. I use a few programs when i create image-on-disc system recovery dvd's for our customers and it wouldn't be possible without partimage. Just because you can't figure it out doesn't mean it doesn't work ^^ keep trying! And stick with gzip compression, bz2 is to slow to be worth the trouble.

Thanks, I did not mean for you to infer that I believe that "partimage" does not work. While I am sure that it does work, my issue is with the poor writing of the documentation, not the program's actual functionality. The greatest challenge of Linux is not Linux terminal; it's the documentation!! :)

---

### Post by magump on 2008-07-12
I had the same problem understanding Partimage.  Check out the instructions in Full Circle magazine, issue #12 at:[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
I now use Parted Magic v2.2  Download it and burn an iso image.  To make things faster I burned the iso image to a DVD.

Find a drive where the backup is to be restored and make a directory to back up to that you can find.

Once the program loads into memory, if backing up to a USB drive, reload the disk.  This way it will access files to connect to the usb.   

On the right hand side of bottom, find the tree that includes Parted Image.  Click on it, let it find your drives, highlight the drive, hit tab to go to the open line and put in the path, beginning with /
Hope this helps.
Magump

---

### Post by arpanaut on 2008-07-12
After struggling with "learning" how to use Partimage, I have to agree somewhat that the documentation is inadequate/incomplete.

BUT, the program and documentation was/is created by linux users for linux users, thus presuming knowledge of use of the OS and how to navigate and accomplish tasks within the system. Thus they do not attempt to offer you these basics.  Therefore making ti a PIA for a newbie to linux to accomplish alot... but if persistant you can learn quite a bit eventually.

For editing fields in Partimage, as you asked, I found that selecting the field then hitting tab allowed editing... 

As for the documentation in linux, yes it often is difficult and obscure, I agree, but as I look on using linux a learning experience, each roadblock offers me another learning opportunity... different strokes for different folks.

Good Luck in finding what you are looking for.

---

### Post by ctoaun on 2008-07-13
> **magump said:**
> I had the same problem understanding Partimage.  Check out the instructions in Full Circle magazine, issue #12 at:[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
I now use Parted Magic v2.2  Download it and burn an iso image.  To make things faster I burned the iso image to a DVD.

Find a drive where the backup is to be restored and make a directory to back up to that you can find.

Once the program loads into memory, if backing up to a USB drive, reload the disk.  This way it will access files to connect to the usb.   

On the right hand side of bottom, find the tree that includes Parted Image.  Click on it, let it find your drives, highlight the drive, hit tab to go to the open line and put in the path, beginning with /
Hope this helps.
Magump
Having visited the website, as I understand it, “Parted magic v2.2” is an advanced partitioning, and data recovery program, which features a disk testing utility. The “Parted magic v2.2” website claims that it is suitable for all levels of experience.

Note: I would not suggest that one acquire the ISO from these sites:
1)bbs.betabbs.com/lofiversion/index.php?t96399.html - 17k
2)so.enet.com.cn/cgi-bin/eget?query=%B7%D6%C7%F8%C4%A7%CA%F5%CA%A6 - 30k 

The sites have been identified by “Mcafee site advisor” as being linked to sites, which produce software that some might consider to be malware, spyware etc.

Thanks for answering my unanswered question. As a fan of G-parted, I want to play with what I presume will be a little gem. 

As for circle magazine on partimage, well... :)

---

### Post by forger on 2008-07-13
Why not use rsync ??

rsync checks the files with a really good algorithm for fast transfers and file updating.

If you know how to mount a partition, it's as easy as 1 2 3.
The manual of rsync is a "tutorial" filled with examples!
> man rsync
[http://rsync.samba.org/ftp/rsync/rsync.html](http://rsync.samba.org/ftp/rsync/rsync.html)

---

### Post by ctoaun on 2008-07-13
**Mr Arpanaut,**
Thanks for responding, but with all due respect, sir, I must vehemently disagree with you for the following two reasons:

**You wrote:**
> > **arpanaut said:**
> After struggling with "learning" how to use Partimage, I have to agree somewhat that the documentation is inadequate/incomplete.
[QUOTE]BUT, the program and documentation was/is created by linux users for linux users, thus presuming knowledge of use of the OS and how to navigate and accomplish tasks within the system. Thus they do not attempt to offer you these basics.  Therefore making ti a PIA for a newbie to linux to accomplish alot... but if persistant you can learn quite a bit eventually.

**Reason #1 of 2: Why I disagree with you.**

Well consider this: **If the Linux community says&#8221;This documentation is for other Linux users only. Please do not contact us with beginner questions.&#8221; I would not have a complaint. However, as soon as the Linux community states that it wants to grow and it also wants 'windows users to give Linux a try, then the Linux community obligates itself to understand and to effectively communicate with windows users. **
Some would disagree with me but my rationale is simple. If an American company or group wants to establish a mutually beneficial business relationship with Romanian people, then said  American company or group obligates itself to acquiring a perfunctory understanding of Romanian language, customs & traditions.  If American company or group or cannot acquire this understanding, then it must liaison with those in possession of this understanding. 

**The bottom line is that when the Linux community fails to adequately communicate with with potential "windows to Linux converts," it shoot itself in the foot and hinders it's own growth. While Linux documentation writers might not have the degrees in &#8220;technical writing,&#8221; &#8220;marketing psychology,&#8221; or education administration enjoyed by the documentation writers employed by larger windows software companies such as Symantec, it can none the less liaison with those who can write.**

Instead, the Linux community often takes the &#8220;cop out&#8221; approach: create a GUI so it does not have to worry about quality documentation. However, even a GUI needs good documentation and so the problem continues. 

**Reason 2 of 2 of why I disagree with you**

You wrote

>  for the documentation in linux, yes it often is difficult and obscure, I agree, but as I look on using linux a learning experience, each roadblock offers me another learning opportunity... different strokes for different folks.

**My rebuttal**
Your stated that.. &#8220;each roadblock offers me another learning opportunity...&#8221; This is not true. Sir, it is impossible for all roadblocks to be positive. In example, some &#8220;Roadblocks&#8221; will provide info that you will never need or the info will be forgotten and or out dated by the time it is needed. 

Sir, I presume that you are retired or unemployed as judged by your writing.
If a company hires someone to accomplish certain tasks and that someone only accomplishes tasks which are only peripherally related to the tasks for which they were hired, that someone will be fired.
 
If one is not young or in college, if one is not married; kids career & mortgage, then one has the luxury of the time needed to have your views. Your view is that Linux documentation id often times bad, but hey, if you struggle unnecessarily, you might learn something


> Good Luck in finding what you are looking for.

Thanks! Found it! Clonezilla

---

### Post by ctoaun on 2008-07-13
To Forger Thanks! I'll keep this around for another time!

---

### Post by ctoaun on 2008-07-27
[SIZE="6"]**Clonezilla**[/SIZE]

Thanks to the taiwanese! 
In spite of the fact that English is a second language for many Taiwanese people, they still manage to generate documentation that is superior to partimage

---

