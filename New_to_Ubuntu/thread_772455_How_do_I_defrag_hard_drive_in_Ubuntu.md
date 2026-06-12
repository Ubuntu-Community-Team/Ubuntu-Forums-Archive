---
title: "How do I defrag hard drive in Ubuntu"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by thomastt37 on 2008-04-28
Are there any Disc Tools included in Ubuntu and where do i FIND THEM?:KS

---

### Post by soxs on 2008-04-28
As far as I know, there is no need for manual defragmentation. Whenever you move data from one place to another ext3 fs will trigger defragmentation itself.

---

### Post by hyper_ch on 2008-04-28
you don't there's no need to :)

---

### Post by smile-its-smiley on 2008-04-28
it used to be the case that after 30 start up ubuntu will automaticly do a defrag

---

### Post by Steveway on 2008-04-28
Defragmentation is not needed for most File-systems used in Linux.
Why do you want to defragment your drive? You know, this is Linux and not Windows.
> **smile-its-smiley said:**
> it used to be the case that after 30 start up ubuntu will automaticly do a defrag

No. It doesn't defragment your drive it checks the drives for errors that could occour.

---

### Post by scientist1971 on 2008-04-28
steveway be easy on new users it takes time to appreciate the myriad advantages of linux:)

---

### Post by tango_ninja on 2008-04-28
regular defragging is really something that needs to be done in M$ (not Linux).

---

### Post by tribaal on 2008-04-28
The long answer:

Linux uses sparse allocation, so when adding data to an already existing file there is a very high probability that there will be empty space next to the file's blocks.

Hope this makes sense.

- Trib'

PS: What's happening every 30 mounts is not a defrag - it's an integrity check. You computer checks that your disk is coherent between what's on the disk and the journal, to detect bad sectors and write errors.

---

### Post by Oldsoldier2003 on 2008-04-28
Usually the only thing that will heavily fragment Linux file systems is doing a lot of torrenting. 

Thats why I like to keep a separate partition for data, and even a separate partition for torrent downloads., its easy enough to just blow the partition and recreate it real fast- instant defrag :)

---

### Post by noynac on 2008-04-28
There is no defrag tool in Hardy. The following thread in the *recurring discussions forum* explains why: 

[http://ubuntuforums.org/showthread.php?t=754900](http://ubuntuforums.org/showthread.php?t=754900)

---

### Post by SlappyPappy on 2008-04-28
How cool is that? 

Score another one for Linux over Windows.  :lolflag:

---

### Post by chewit on 2008-04-28
There is SCRUB!

[http://edhewitt.co.uk/2008/04/23/scrub/](http://edhewitt.co.uk/2008/04/23/scrub/)

---

### Post by GoCool on 2008-04-28
...a noob question then....why is my HDD making so much noise? I used to have XP before and when ever it used to make so much noise I just did a defrag and it quitened. But now I have made it pure Ubuntu (gutsy), but the noise remains. 
Any idea on how to get the noise away?

---

### Post by Calash on 2008-04-28
What kind of noise?  If you are getting excessive noise due to the head movement...your drive may be going bad and defragging was just masking a larger problem.

---

### Post by GoCool on 2008-04-28
> **Calash said:**
> What kind of noise?  If you are getting excessive noise due to the head movement...your drive may be going bad and defragging was just masking a larger problem.

I think its the head movement. Boy...so am I headed to another crash? Any tools to diagnose it in Ubuntu? :confused:

---

### Post by Steveway on 2008-04-29
> **GoCool said:**
> I think its the head movement. Boy...so am I headed to another crash? Any tools to diagnose it in Ubuntu? :confused:

It could be tracker indexing your Hardrive.
Check if it that, just let it finish (could take some time on big disks) or remove tracker.

---

### Post by GoCool on 2008-04-29
> **Steveway said:**
> It could be tracker indexing your Hardrive.
Check if it that, just let it finish (could take some time on big disks) or remove tracker.

:confused: What is a tracker?
If it's something good happenning then better I let it run.

---

### Post by Steveway on 2008-04-29
Tracker is a pretty nifty search-utility.
It indexes your Harddrives and then allows you to do really fast searches.

---

### Post by scorp123 on 2008-04-29
> **thomastt37 said:**
> Are there any Disc Tools included in Ubuntu and where do i FIND THEM?:KS
"Why doesn't Linux need defragmenting?"
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by Ichido on 2008-05-01
My new Dell Inspiron 1525n came with Gusty Gibbon 7.10 installed.
The 36th time I booted, a "File Check" stared automatically.

---

### Post by JoyceBabu on 2008-05-01
If you are not a geek, then this page will explain to you why you don't need defragmenter for Linux.
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

