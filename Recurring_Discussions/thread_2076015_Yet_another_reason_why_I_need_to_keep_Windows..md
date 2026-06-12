---
title: "Yet another reason why I need to keep Windows."
date: 2012-10-25
forum: Recurring Discussions
---

### Post by Advait on 2012-10-25
Hi All,

So I was working in Ubuntu 12.04 and I needed to format a  4gb USB stik. I clicked on the Home Folder icon and then right clicked  on the stik. Nothing about formatting. Hmm... So I did a google search  and discovered you have to use the Disk Utility to format. OK. I fired  up the Disk Utility and tried again for format. It kept saying "Device  Busy". Hmmm... OK, so I googled this error and did not find any clear  solutions. One person said a reboot fixed the problem. I tried that.  Didn't work. And when I clicked on Format button in Disk Utility, it  didn't say what file system it would use for the format. I needed Fat32  and I couldn't see any way of telling what file system it would use for  the format. I could have googled this problem also but at this point I threw up my  hands and said "The heck with this!" Only one thing to do:

Windows  to The Rescue! Yes, that's right, rather than spending another hour or  more trying to simply format a USB stik using Ubuntu, I fired up Windows  and was able to Fat32 format the stik in about 15 seconds.

Stuff  like this happens *all the time*. This is why I need to keep Windows  around. And is probably why Ubuntu and Linux remain at less than 1% of  desktops.

I love the idea of open source and I totally support it  (and I donate to the Ubuntu Foundation), but for the average user, it's  far far away from ready for Prime Time.

Thank goodness I still have Windows.

OK, I just wanted to vent a little. I feel better now. :smile:  Later on I'll revisit the problem of how to format a stik in Ubuntu.

Kind Regards,

Advait

---

### Post by hal8000 on 2012-10-25
Alternatively you could have asked on Ubuntu Forums and probably get a response in under 1 hour:

Make sure your memory stick is unmounted:

sudo mkfs.vfat /dev/sdc1
 

replace sdc1 (with the partition of your memory stick)

---

### Post by nothingspecial on 2012-10-25
> **Advait said:**
> 



Stuff  like this happens *all the time*. This is why I need to keep Windows  around. And is probably why Ubuntu and Linux remain at less than 1% of  desktops.



*Thread moved to **Recurring Discussions**.*

---

### Post by Docaltmed on 2012-10-25
If you really need Windows because you can't figure how to format a usb in Ubuntu, I would suggest just sticking with Windows. You will likely find Ubuntu to be just too frustrating.

---

### Post by jrog on 2012-10-25
> **Advait said:**
> Hi All,

So I was working in Ubuntu 12.04 and I needed to format a  4gb USB stik. I clicked on the Home Folder icon and then right clicked  on the stik. Nothing about formatting. Hmm... So I did a google search  and discovered you have to use the Disk Utility to format. OK. I fired  up the Disk Utility and tried again for format. It kept saying "Device  Busy".
I'm sorry to be blunt -- I really don't intend for it to come across this way, but don't know how else to say it -- but someone already told you what this error means a bit over a year ago, and it seemed to solve this issue (you marked the thread as solved): [http://ubuntuforums.org/showthread.php?t=1807599](http://ubuntuforums.org/showthread.php?t=1807599). The drive appears to have been mounted. You can't format a mounted drive.

> Hmmm... OK, so I googled this error and did not find any clear  solutions. One person said a reboot fixed the problem. I tried that.  Didn't work. And when I clicked on Format button in Disk Utility, it  didn't say what file system it would use for the format. I needed Fat32  and I couldn't see any way of telling what file system it would use for  the format. I could have googled this problem also but at this point I threw up my  hands and said "The heck with this!" Only one thing to do:

Windows  to The Rescue! Yes, that's right, rather than spending another hour or  more trying to simply format a USB stik using Ubuntu, I fired up Windows  and was able to Fat32 format the stik in about 15 seconds.Sorry that you had problems in Ubuntu. However, if you encounter the issue again, the instructions here (in the very first answer) might help: [http://askubuntu.com/questions/22381/how-to-format-a-usb-flash-drive](http://askubuntu.com/questions/22381/how-to-format-a-usb-flash-drive). As they indicate, you should be able to format a USB stick as FAT32 in about 15 seconds on Ubuntu, too.

Maybe it is not quite as intuitive as it is in Windows, though I'm not sure about that.

---

### Post by MadmanRB on 2012-10-25
I always had issues with quick format in linux, this is why I use Gparted.
Install gparted, issue solved

---

### Post by mamamia88 on 2012-10-25
> **MadmanRB said:**
> I always had issues with quick format in linux, this is why I use Gparted.
Install gparted, issue solved

+1 million.   no need for windows make sure device isn't mounted chose your usb drive from drop down menu and format it.  pretty dang simple

---

### Post by thatguruguy on 2012-10-25
The OP had been helped before on this exact same issue. I doubt that trying to give her help now will be any more successful than it was then.

---

### Post by Advait on 2012-10-26
> **hal8000 said:**
> Alternatively you could have asked on Ubuntu Forums and probably get a response in under 1 hour:
Make sure your memory stick is unmounted:  sudo mkfs.vfat /dev/sdc1
 replace sdc1 (with the partition of your memory stick)

OK, thanks for the info. I'll make a note of this next time I need to format a stik (which is only about once every month or 2). Cheers,

---

### Post by Advait on 2012-10-26
> **Docaltmed said:**
> If you really need Windows because you can't figure how to format a usb in Ubuntu, I would suggest just sticking with Windows. You will likely find Ubuntu to be just too frustrating.

Ubuntu is often frustrating. But I definitely need it. It's one of the few ways I can browse safely and securely to my online financial accounts. I'm actually having fun learning the basics of Linux. I'm even starting to appreciate the command line. :)

---

### Post by Advait on 2012-10-26
> **jrog said:**
>  -- but someone already told you what this error means a bit over a year ago, and it seemed to solve this issue (you marked the thread as solved): [http://ubuntuforums.org/showthread.php?t=1807599](http://ubuntuforums.org/showthread.php?t=1807599). The drive appears to have been mounted. You can't format a mounted drive.

Maybe it is not quite as intuitive as it is in Windows, though I'm not sure about that.

OK, thanks! Like I said, I did a google search on the problem and my earlier post did not appear near the top of the search list. If I could easily remember all the posts I've ever made, I'd be a PhD and a rich person by now! :P It's definitely not as intuitive as Windows. In Windows you don't have to think about "mounted" or "unmounted" for doing a format. But I'm guessing in some scenarios it's very useful to mount and unmount drives without physically removing them.

---

### Post by Advait on 2012-10-26
> **MadmanRB said:**
> I always had issues with quick format in linux, this is why I use Gparted.
Install gparted, issue solved

Ahh... Now that's helpful. I'll download gparted and keep it in mind for formatting. Thanks! :P

---

### Post by Herby Pepper on 2012-10-26
In Disk Utility that you use there is option Unmount Volume. (Look where it is on attached picture, please).  Do it first then Format Driver.

---

### Post by coldraven on 2012-10-26
Run gparted and select the drive from the drop down in the top right corner, you can select whatever drives are attached.
When you right click a mounted drive the only option that appears is to unmount it.
Try clicking on the graphic and on the description below to see what options there are.
After unmounting you can choose many options of formatting.
The whole process takes seconds.
Just make sure that you choose the correct drive.

---

### Post by Advait on 2012-10-26
> **thatguruguy said:**
> The OP had been helped before on this exact same issue. I doubt that trying to give her help now will be any more successful than it was then.

The replies have been helpful and revealed different ways to format a stik, which is good information. Thanks to all for your responses. :) I'm trying to remember how to do all these tasks in Linux, but it's a little more difficult when I only do the task once every 5 or 6 months. Makes it harder to sink into my old and creaky brain cells.

Kind Regards,

---

### Post by Lemuriano on 2012-10-26
The issue that you mention has a name (learning curve) Gnu/Linux is just different.:)

---

### Post by stinkeye on 2012-10-26
> **Advait said:**
> The replies have been helpful and revealed different ways to format a stik, which is good information. Thanks to all for your responses. :) I'm trying to remember how to do all these tasks in Linux, but it's a little more difficult when I only do the task once every 5 or 6 months. Makes it harder to sink into my old and creaky brain cells.

Kind Regards,
Maybe keeping notes on any fixes or tweaks you find may help.
eg I use gnote solely for this and have found solutions to problems that I couldn't even remember adding.
Been keeping notes since feb 2009.

---

### Post by stinkeye on 2012-10-26
> **jrog said:**
> I'm sorry to be blunt -- I really don't intend for it to come across this way, but don't know how else to say it -- but someone already told you what this error means a bit over a year ago, and it seemed to solve this issue (you marked the thread as solved): [http://ubuntuforums.org/showthread.php?t=1807599](http://ubuntuforums.org/showthread.php?t=1807599). The drive appears to have been mounted. You can't format a mounted drive.
.........


Nice work Sherlock. :P

---

### Post by Advait on 2012-10-26
> **stinkeye said:**
> Maybe keeping notes on any fixes or tweaks you find may help.  eg I use gnote solely for this and have found solutions to problems that I couldn't even remember adding. Been keeping notes since feb 2009.

Great idea. I'm using the notes features in my trusty old Palm Treo Pro, so I'm definitely tied to that for the time being. I'll see the best way to create a "Linux Lessons Learned" file and start adding to it. After my Treo dies and I get an Android, I may be able to switch completely to Ubuntu.

---

### Post by mamamia88 on 2012-10-28
> **Advait said:**
> Great idea. I'm using the notes features in my trusty old Palm Treo Pro, so I'm definitely tied to that for the time being. I'll see the best way to create a "Linux Lessons Learned" file and start adding to it. After my Treo dies and I get an Android, I may be able to switch completely to Ubuntu.

or you could just bookmark it and use google chrome.   that way if you format your drive all you have to do is log right back in and all your settings are stored for you

---

