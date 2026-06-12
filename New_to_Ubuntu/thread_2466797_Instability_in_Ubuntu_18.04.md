---
title: "Instability in Ubuntu 18.04"
date: 2021-09-06
forum: New to Ubuntu
---

### Post by heatopher2 on 2021-09-06
Hi, I don't think that I'm a complete beginner any more - maybe pre-intermediate! - but I need serious advice just now.

I installed 18.04 on this dual-booting desktop a couple of months ago. I had put 20.04 on there, but was having problems getting a graphical add-on to work (Cairo Dock, to be specific), so reverted back to 18, where I knew at least that it worked. Things were mostly fine to start with, but in the last couple of weeks I've been seeing some quite frustrating behaviour. I see the "problem detected" popup quite a lot, especially just after restarting, but don't know exactly what the problem(s) is/are. I guess that I would like to know where to look in order to investigate properly myself.

It's not just minor annoyances - there's serious instability there. Quite often the screen freezes in the middle of doing things, and there's no response to mouse or keyboard, so all I can do is hit the power button. And nobody likes doing that. Other dodgy behaviour: certain apps have been failing to open sometimes - most commonly Spotify and Skype, but it also happened to Chromium for a while (in fact I've now got two instances of Chromium installed because of that, which is a bit confusing). Most disturbingly, though, I'm getting failed starts where I have to run fsck on the drive to check for errors. Thankfully I'm learning a bit from all this, and am able to get back to the login screen, but of course I don't want it to be doing that all the time (well, it's happened at least a few times already).

So - what do I do about this? Where do I go to check log files, and which needle will I be looking for in that haystack? And is it all worth it? That is to say - should I just accept that I'm going to have to upgrade to more recent versions if this particular system is so unstable? And if so, is the upgrade process guaranteed to go smoothly given what has been happening? I've seen problems with upgrades in the past. In the worst case, I've got the home directory backed up, plus a package list.

Enough for now. Thanks very much for any help ):P

---

### Post by yancek on 2021-09-06
When you see the problem detected popup, you should see Details on the left side of that window with a drop down arrow which should give you some information.  Have you checked that?   Log files are under the /var/log directory.  What results do you get from running fsck on your partitions?

>  so all I can do is hit the power button. 

Don't do that, you are likely causing additional problems.  Try the method below:

>  Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB will get you safely restarted.  

>    And if so, is the upgrade process guaranteed to go smoothly given what has been happening? 

You're kidding of course?  You don't get guarantees like that for software you pay for so you certainly won't get it for free software.

---

### Post by heatopher2 on 2021-09-06
Hi, thanks very much for the swift reply :~)

> **yancek said:**
> When you see the problem detected popup, you should see Details on the left side of that window with a drop down arrow which should give you some information.  Have you checked that?   Log files are under the /var/log directory.  

Yes, I sometimes look at those messages, but haven't been taking screenshots, or writing anything down. I'll try to do that the next two or three times, and will come back with that.

> **yancek said:**
> What results do you get from running fsck on your partitions?

Not quite sure what you mean there. I've only run fsck when I was stuck at startup and desperate to get things going again, and didn't write anything down. 

I just tried running fsck on the terminal, but got scary warning messages about causing severe filesystem damage, so of course I didn't execute anything.

> **yancek said:**
> 
Don't do that, you are likely causing additional problems.  Try the method below:

Yes, OK. I've never heard about any of that. Of course I wasn't happy hitting the power button. 

Thanks anyway. Is this info all correct? 

[https://www.thegeekstuff.com/2008/12/safe-reboot-of-linux-using-magic-sysrq-key/](https://www.thegeekstuff.com/2008/12/safe-reboot-of-linux-using-magic-sysrq-key/)

They're saying "REKSUB". I guess that was just a typo from you? I don't quite know what they mean about enabling the SysRq key. I don't  see it on my keyboard, which is designed for Windows of course. Should I  assume that it will be on the PrintScreen key once it's enabled?

> **yancek said:**
> 
You're kidding of course?  You don't get guarantees like that for software you pay for so you certainly won't get it for free software.

Ha, OK, fair enough :~) I guess I was kidding *myself, and hoping, in the face of evidence that I've already seen to the contrary.

---

### Post by heatopher2 on 2021-09-06
Update (plus one thing that I hadn't mentioned)

This is the popup that I get. Very limited - no arrow to check details (I do remember that that is what is supposed to happen, but that's not what I'm getting :~/ )
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289126&stc=1[/IMG]

Apart from that, I just had a system freeze, and did the ALT+SysRq thing, which caused the system to restart (only at the last letter, I think). After restarting, I got a total black screen responsive to nothing at all, but with the computer still on, so all I could do was turn the thing off :(

I forgot to mention, by the way, one other important thing that has been happening. When I restart (not only when there's a screen freeze) it takes FOREVER, telling me that there are all kinds of stop jobs and processes that need ages to sort themselves out. Of course I can't wait half an hour for this every time, and so if there isn't a fix that I can find by looking through those logs, which are of course overwhelming for someone at my level, I think I'm going to have to reinstall, am I not??? Probably not with this version if it's so unreliable :~/

---

### Post by monkeybrain20122 on 2021-09-06
If you click "report problem ..." it will show exactly what problem that is.

---

### Post by heatopher2 on 2021-09-06
> **monkeybrain20122 said:**
> If you click "report problem ..." it will show exactly what problem that is.

I do, and it doesn't. Unless I'm supposed to be looking somewhere? In which case, please tell me where. Thank you.

---

### Post by yancek on 2021-09-07
>  
They're saying "REKSUB". I guess that was just a typo from you?

No, it is REISUB and is explained in more detail at the link below.

[http://blog.kember.net/articles/reisub-the-gentle-linux-restart/](http://blog.kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by heatopher2 on 2021-09-07
> **yancek said:**
> No, it is REISUB and is explained in more detail at the link below.

[http://blog.kember.net/articles/reisub-the-gentle-linux-restart/](http://blog.kember.net/articles/reisub-the-gentle-linux-restart/)

OK, thanks. Well, I can confirm that that doesn't work. I had a massive system freeze a few minutes ago, and none of that worked, so I had no choice but to turn the whole thing off. Of course I don't want to do that, but what else can I do? I can also confirm that that **should** have worked. I tried it while there was no kernel panic or whatever it is, and it did indeed work - made the computer restart in the normal way. I can only assume that means that the system loses any contact with the USB ports when this freeze happens. But what do I know - I'm the beginner here.

Anyway, look..... This thing is totally messed up for me. I currently can't get into Ubuntu at all. Getting this:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289130&stc=1[/IMG]

I tried running fsck -yf nvme0n1p3 (ie on the drive in question), and nothing happens apart from getting this message:

fsck from util-linux 2.31.1

Of course I have no idea what I'm supposed to do about that.

Anyway, it's just getting worse all the time. Shortly before this happened, I got a message upon logging on, telling me that the root filesystem is almost full. The root system is on a separate partition from home, so it's not my files or downloads clogging it up. I don't have **that** much heavy stuff installed on there either, so I don't know what that's all about. The partition is 60GB, which should be ample, shouldn't it?

Currently back on Windows, and not happy at all to be here, as I was in the middle of a load of jobs and learning. Please advise!

---

### Post by ActionParsnip on 2021-09-07
Why 18.04 ? Why did you not go for 20.04 which is also LTS...?

---

### Post by heatopher2 on 2021-09-07
> **ActionParsnip said:**
> Why 18.04 ? Why did you not go for 20.04 which is also LTS...?
I could indeed, and if you read my first post in full you will see that I explained why I installed 18.04, and then that of course I am considering giving up on it and going to 20.04, because this current state of affairs is getting pretty tiresome, besides obviously being unproductive. However, I'm afraid that your question doesn't really help me with my immediate problem :~)

---

### Post by mIk3_08 on 2021-09-07
> **heatopher2 said:**
> Hi, I don't think that I'm a complete beginner any more - maybe pre-intermediate! - but I need serious advice just now.

I installed 18.04 on this dual-booting desktop a couple of months ago. I had put 20.04 on there, but was having problems getting a graphical add-on to work (Cairo Dock, to be specific), so reverted back to 18, where I knew at least that it worked. Things were mostly fine to start with, but in the last couple of weeks I've been seeing some quite frustrating behaviour. I see the "problem detected" popup quite a lot, especially just after restarting, but don't know exactly what the problem(s) is/are. I guess that I would like to know where to look in order to investigate properly myself.

It's not just minor annoyances - there's serious instability there. Quite often the screen freezes in the middle of doing things, and there's no response to mouse or keyboard, so all I can do is hit the power button. And nobody likes doing that. Other dodgy behaviour: certain apps have been failing to open sometimes - most commonly Spotify and Skype, but it also happened to Chromium for a while (in fact I've now got two instances of Chromium installed because of that, which is a bit confusing). Most disturbingly, though, I'm getting failed starts where I have to run fsck on the drive to check for errors. Thankfully I'm learning a bit from all this, and am able to get back to the login screen, but of course I don't want it to be doing that all the time (well, it's happened at least a few times already).

So - what do I do about this? Where do I go to check log files, and which needle will I be looking for in that haystack? And is it all worth it? That is to say - should I just accept that I'm going to have to upgrade to more recent versions if this particular system is so unstable? And if so, is the upgrade process guaranteed to go smoothly given what has been happening? I've seen problems with upgrades in the past. In the worst case, I've got the home directory backed up, plus a package list.

Enough for now. Thanks very much for any help ):P

I am using Linux Ubuntu 18.04 until now but so far I haven't encountered any problem in my Linux Ubuntu Operating System.
I'm just confused what kind of 18.04 did you install? you must specify then, because maybe you have downloaded the wrong one. 
And Just wanted to know about where did you download you Linux Ubuntu 18.04 Operating System. This might be the reason why 
you have encountered errors in your Linux Ubuntu Operating System. For your info: I have installed Linux Ubuntu 18.04 LTS 
(Long Term Support) Operating System in my machine. That is why you have to specify your Linux Ubuntu Operating System.
Thanks and regards.

---

### Post by heatopher2 on 2021-09-07
> **mIk3_08 said:**
> 
I'm just confused what kind of 18.04 did you install? you must specify then, because maybe you have downloaded the wrong one. 
And Just wanted to know about where did you download you Linux Ubuntu 18.04 Operating System. This might be the reason why 
you have encountered errors in your Linux Ubuntu Operating System. For your info: I have installed Linux Ubuntu 18.04 LTS 
(Long Term Support) Operating System in my machine. That is why you have to specify your Linux Ubuntu Operating System.
Thanks and regards.

Hi, and thanks. That's a helpful question. I can't tell you now where I downloaded from, but probably from the main Ubuntu download portal, I guess. Whatever was top of the Google search, so no doubt it should have been that, with a likelihood of 99%. Anyway, the .iso file that I have on the PC (and presumably the one that I used) is: 

                 ubuntu-18.04.4-desktop-amd64.iso

What are we saying about all this mess that I'm dealing with now? Too complicated? Give up and reinstall? Like I said, I do have the home directory backed up, plus a regular package list backup that I can easily plug back in (if that's safe to do????). I found a procedure that easily automates that from the package list txt file. OK, there are a few more tedious tweaks that I'll have to do, but I suppose it's less hastle than all of this. I'm partly sticking it out just because I'm stubborn about wanting to understand what's going on. That's why I made the final decision to move over to Linux, and have no intention of going back now.

---

### Post by mIk3_08 on 2021-09-08
Have you already paste your system logs in the Ubuntu pastebin? There are a lot in this community that are willing to help you. 
If you already have done this just paste the link here in thread. So they review your system logs.
If you would like to share the information about your system hardware  just run this code below in your terminal 
```
sudo lshw 
```
and paste the result here in thread wrap with code so, they may see if your system hardware is in need of additional driver
for it to run smoothly. Because the Linux Ubuntu Operating System is not Microsoft Windows. Good Luck and Regards.

---

### Post by heatopher2 on 2021-09-08
> **mIk3_08 said:**
> Have you already paste your system logs in the Ubuntu pastebin? There are a lot in this community that are willing to help you. 
If you already have done this just paste the link here in thread. So they review your system logs.
If you would like to share the information about your system hardware  just run this code below in your terminal 
```
sudo lshw 
```
and paste the result here in thread wrap with code.

I would if I could! If someone had given me that simple instruction yesterday, I would have done so, but now (you need to see my later posts) I can't get in the system at all, and need help getting in again, if it's possible at all.

So, like I said, if no one can tell me how to get back in, I'm just going to have to reinstall.

Anyway, thanks for your help! I hope you'll hang around for a couple more posts :~)

---

### Post by heatopher2 on 2021-09-08
I'm referring to this post, specifically. Completely shut out just now.

> **heatopher2 said:**
> OK, thanks. Well, I can confirm that that doesn't work. I had a massive system freeze a few minutes ago, and none of that worked, so I had no choice but to turn the whole thing off. Of course I don't want to do that, but what else can I do? I can also confirm that that **should** have worked. I tried it while there was no kernel panic or whatever it is, and it did indeed work - made the computer restart in the normal way. I can only assume that means that the system loses any contact with the USB ports when this freeze happens. But what do I know - I'm the beginner here.

Anyway, look..... This thing is totally messed up for me. I currently can't get into Ubuntu at all. Getting this:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289130&stc=1[/IMG]

I tried running fsck -yf nvme0n1p3 (ie on the drive in question), and nothing happens apart from getting this message:

fsck from util-linux 2.31.1

Of course I have no idea what I'm supposed to do about that.

Anyway, it's just getting worse all the time. Shortly before this happened, I got a message upon logging on, telling me that the root filesystem is almost full. The root system is on a separate partition from home, so it's not my files or downloads clogging it up. I don't have **that** much heavy stuff installed on there either, so I don't know what that's all about. The partition is 60GB, which should be ample, shouldn't it?

Currently back on Windows, and not happy at all to be here, as I was in the middle of a load of jobs and learning. Please advise!

---

### Post by heatopher2 on 2021-09-08
Well, for some reason this picture disappeared from the original post, and I can't reinsert it by editing the file :~/


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289151&stc=1[/IMG]

---

### Post by mIk3_08 on 2021-09-09
If you can still run the  fsck then just follow the instructions of the fsck.
Then just locate the disk you want to scan using fsck. 
sample to run fsck in your system. 
```
sudo fsck /dev/sdb
```
fsck can check your system disk and can do repair it until you get 
login to your Linux Ubuntu Operating System Desktop.
locate first the Linux Ubuntu Operating System disk you want to scan 
where /dev/sdb is your Linux Ubuntu Operating System is installed.

---

### Post by heatopher2 on 2021-09-09
Hi again :~) 

Well, I tried running fsck (specifically fsck -yf ....... on the drive in question). This had saved me before, but the problem this time was that that didn't have the same effect this time. I just got this message:

"fsck from util-linux 2.31.1"

And here I'm stuck. I just don't know where I'm supposed to go. Is "util-linux 2.31.1" a directory that I need to run the command from? Sorry, I haven't been back in since yesterday. I needed a break from it :~/

---

### Post by mIk3_08 on 2021-09-10
> **heatopher2 said:**
> fsck -yf 
I think when executing filesystem check you need to specify the filesystem itself in to the command line. 
```
sudo fsck -f /dev/sdb
```
Did you try to do a Dry Run with fsck? If you are doing to force scan,
Try Run fsck on all your filesystem at once. follow the command below.
```
sudo fsck -AR
```
To avoid the prompts, add the -y option.
To fix detected errors automatically with fsck run the command below:
```
sudo fsck -y /dev/sdb
```

---

### Post by heatopher2 on 2021-09-10
Hi, of course I had run the fsck command on the partition in question. You can see that I wrote the full command in one of my previous posts. 

I have no idea why, but I've just now managed to get back into Ubuntu. The only thing that I did differently (I think!) is that I removed the -f option. Anyway, I'm here now, but of course not complacent that everything is OK. 

So I have run:

```
sudo lshw
```

The output is linked to here (too long to go in a post, apparently)

[HTML]https://paste.ubuntu.com/p/4PTvVQ84Fm/[/HTML]

Also, I'm still getting the now familiar disk usage warning on startup. Here are the maps. I guess that they don't show everything, right? The whole partition is about 55GB.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289162&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289165&stc=1[/IMG]

---

### Post by mIk3_08 on 2021-09-11
How about your system logs? Did you already paste it into the Ubuntu pastebin?
If you haven't done it yet. Please try to do it before your Linux Ubuntu Operating
System gets crazy it get more worst. And try to install also a Linux Ubuntu Operating
System canonical live-patch. It has a big help when you have installed it in your
Linux Ubuntu Operating System. Good Luck and regards.

---

### Post by heatopher2 on 2021-09-11
> **mIk3_08 said:**
> How about your system logs? Did you already paste it into the Ubuntu pastebin?.

I put the link in my last post, but here it is again anyway :~)


[HTML]https://paste.ubuntu.com/p/4PTvVQ84Fm/[/HTML]

---

### Post by mIk3_08 on 2021-09-12
> **heatopher2 said:**
> I put the link in my last post, but here it is again anyway :~)
[HTML]https://paste.ubuntu.com/p/4PTvVQ84Fm/[/HTML]

I have review all your post to this thread many times. But I haven't seen any links of your 
Linux Ubuntu Operating System logs and I saw only two links on your previews post 
to this thread and its only the link of your system hardware information.
Again, I haven't seen any links of your Linux Ubuntu Operating System logs. Regards.

---

### Post by heatopher2 on 2021-09-12
> **mIk3_08 said:**
> I have review all your post to this thread many times. But I haven't seen any links of your 
Linux Ubuntu Operating System logs and I saw only two links on your previews post 
to this thread and its only the link of your system hardware information.
Again, I haven't seen any links of your Linux Ubuntu Operating System logs. Regards.

Sorry, I don't understand. You ony told me to run that command:
```
sudo lshw
```

That's what is pasted in that link. I already said in previous posts that I don't know where to look among all the logs. Please advise :~)

---

### Post by monkeybrain20122 on 2021-09-12
> **heatopher2 said:**
> Sorry, I don't understand. You ony told me to run that command:
```
sudo lshw
```

That's what is pasted in that link. I already said in previous posts that I don't know where to look among all the logs. Please advise :~)



```
cat /var/log/syslog
```

and

```
sudo dmesg
```

---

### Post by heatopher2 on 2021-09-12
> **monkeybrain20122 said:**
> ```
cat /var/log/syslog
```

and

```
sudo dmesg
```

OK, thanks. Will do tomorrow :~)

---

### Post by mIk3_08 on 2021-09-13
> **heatopher2 said:**
> Sorry, I don't understand. You ony told me to run that command:
```
sudo lshw
```
That's what is pasted in that link. I already said in previous posts that I don't know where to look among all the logs. Please advise :~)
Sorry I wasn't able to elaborate more about my post I thought you knew already.
> **monkeybrain20122 said:**
> ```
cat /var/log/syslog
```
and
```
sudo dmesg
```
Thanks to monkeybrain20122 for the quick response.
Thanks for the help.

---

### Post by heatopher2 on 2021-09-13
> Sorry I wasn't able to elaborate more about my post I thought you knew already.

No worries. Like I said, not a beginner, but still only pre-intermediate at the most :~)

OK. Here we go. Again, I can't get into the Ubuntu GUI, but I was able to get on the system as root and used my still limited command line skills to get those two commands into files that I then smuggled out of the system with an Ubuntu Live USB (so I'm definitely not a complete beginner at least, which makes me feel quite a lot better :~). Now, here's the syslog:

[HTML]https://paste.ubuntu.com/p/MwvZNhPrmT/[/HTML]

and dmesg:

[HTML]https://paste.ubuntu.com/p/MV4Cd2YZCt/[/HTML]

Well, there's a lot to look at there! Hope it all makes sense to someone :~)

---

### Post by mIk3_08 on 2021-09-14
> **heatopher2 said:**
> No worries. Like I said, not a beginner, but still only pre-intermediate at the most :~)
OK. Here we go. Again, I can't get into the Ubuntu GUI, but I was able to get on the system as root and used my still limited command line skills to get those two commands into files that I then smuggled out of the system with an Ubuntu Live USB (so I'm definitely not a complete beginner at least, which makes me feel quite a lot better :~). Now, here's the syslog:
[HTML]https://paste.ubuntu.com/p/MwvZNhPrmT/[/HTML]
and dmesg:
[HTML]https://paste.ubuntu.com/p/MV4Cd2YZCt/[/HTML]
Well, there's a lot to look at there! Hope it all makes sense to someone :~)

I will try to review your system logs. This will be a lot to review. I will explain to you on what will I see in your system logs.
We will be more lucky if someone in the community will also try to help us and review your system logs on your Linux Ubuntu Operating System situation.
Stay cool and regards.

---

### Post by heatopher2 on 2021-09-14
> **mIk3_08 said:**
> I will try to review your system logs. This will be a lot to review. I will explain to you on what will I see in your system logs.
We will be more lucky if someone in the community will also try to help us and review your system logs on your Linux Ubuntu Operating System situation.
Stay cool and regards.

Sure, no worries and no massive rush. I'm surviving on Windows for the time being, and learning new Linux stuff as and when I want to on a VM. Still, I have to admit that I get really annoyed by all the stupid things that Windows does, of course, and keen to get back on the main Linux drag sooner rather than later :~/

Speaking of VMs, I checked the syslog on the Ubuntu VM that I'm running on Windows, and there seemed to be a ****LOT**** less going on there than on the log that I've pasted. I suppose maybe it's not surprising, since I have hardly any applications installed on the VM. Nevertheless, I guess the question that I have in my mind is whether it's normal (if such a thing as "normal" even exists) for a system log at startup to be as long as the one that I've submitted.

And thanks for your attention, of course :KS

(P.S. please don't hesitate to tell me if you think that it's all too complicated, and the best thing would be to do a new clean install, using the live-patch from the start this time. I'm partly just pursuing all this as part of my general Linux learning :~)

---

### Post by mIk3_08 on 2021-09-15
> **heatopher2 said:**
> Sure, no worries and no massive rush. I'm surviving on Windows for the time being, and learning new Linux stuff as and when I want to on a VM. But I get really annoyed by all the stupid things that Windows does, of course, and keen to get back on the main Linux drag sooner rather than later :~/
Speaking of VMs, I checked the syslog on the Ubuntu VM that I'm running on Windows, and there seemed to be a ****LOT**** less going on there than on the log that I've pasted. I suppose maybe it's not surprising, since I have hardly any applications installed on the VM. Nevertheless, I guess the question that I have in my mind is whether it's normal (if such a thing as "normal" even exists) for a system log at startup to be as long as the one that I've submitted.
And thanks for your attention, of course :KS
(P.S. please don't hesitate to tell me if you think that it's all too complicated, and the best thing would be to do a new clean install, using the live-patch from the start this time. I'm partly just pursuing all this as part of my general Linux learning :~)

Thanks a lot for understanding. I just review a little part of it in the upper part of the system logs. I saw some errors and some disabled parts. 
But don't worry about this part because it is just a minor thing I think. And I wasn't able to resume my review due to some interruptions. Its
just a personal thing. Other important matters. Don't worry I will be updating you when I completely review all the logs in your system. Regards.

---

### Post by heatopher2 on 2021-09-16
> **mIk3_08 said:**
> Thanks a lot for understanding. I just review a little part of it in the upper part of the system logs. I saw some errors and some disabled parts. 
But don't worry about this part because it is just a minor thing I think. And I wasn't able to resume my review due to some interruptions. Its
just a personal thing. Other important matters. Don't worry I will be updating you when I completely review all the logs in your system. Regards.

No worries at all. Talk soon ):P

---

### Post by mIk3_08 on 2021-09-17
I have started a few scan in your system logs and found out this
```
Sep 10 10:17:01 HEATOPHER gnome-shell[8271]: Object Meta.Background  (0x5605c20d7c70), has been already deallocated - impossible to access  it. This might be caused by the object having been destroyed from C code  using something such as destroy(), dispose(), or remove() vfuncs

```
and this; 
```
Sep 10 10:15:47 HEATOPHER variety.desktop[10473]: FileNotFoundError:  [Errno 2] No such file or directory:  '/home/kizza/.config/variety/Downloaded/Unsplash/photo-1630837045253-a9bf26e51f02.jpg.metadata.json'
Sep 10 10:15:47 HEATOPHER variety.desktop[10473]: ERROR: 2021-09-10  10:15:47,771: safe_unlink() 'Could not delete  /home/kizza/.config/variety/Downloaded/wallhaven_abstract/wallhaven-4dk69j.jpg.metadata.json,  ignoring'
Sep 10 10:15:47 HEATOPHER variety.desktop[10473]: Traceback (most recent call last):
Sep 10 10:15:47 HEATOPHER variety.desktop[10473]:   File  "/usr/lib/python3/dist-packages/variety/Util.py", line 886, in  safe_unlink
Sep 10 10:15:47 HEATOPHER variety.desktop[10473]:     os.unlink(filepath)
```
This errors keeps repeating in your system.
Maybe this is one of the few things that causes the corruption of your system that make it unstable
That's the only few that I checked and I'm not finish yet but I am planning to continue to review it when have some availability
so we can find out the root cause of your unstable system.

---

### Post by heatopher2 on 2021-09-17
Well, I had quite a lot of trouble getting Variety to work properly, so it makes sense that that is showing up.  Really a big shame, as it's such a nice app. I had a whole thread  about it, here:

[https://ubuntuforums.org/showthread.php?t=2465658](https://ubuntuforums.org/showthread.php?t=2465658)

I marked it as "solved" because I did get it working the way it was supposed to in the end, but maybe it's no  coincidence that things collapsed completely around that time. I say  "maybe", because there were already plenty of noticeable problems before  I fixed that. I kind of doubt that it's only about Variety, though, eh.

Let me mention one other thing that I think might have caused instability. Shortly after installing, back in July, I wanted to get Ubuntu to hibernate nicely, the way that Windows does, and followed a few links which got me to that point (I'll dig up the links if you think it's relevant). It worked, but less than 50% of the time, from the beginning, and more often than not I ended up needing to shut down or restart (and then getting those "stop jobs" preventing the system from shutting down for long periods). But hey, I don't know what things are related to what, and that is why I'm here :~)

---

### Post by heatopher2 on 2021-09-22
Let's be honest. This really isn't much of a "community" these days, is it? People on here were much more helpful when I first started experimenting with Linux a few years ago. One person has properly offered to help, and of course disappeared because it's too much for only one person to help out with the issue that I've got. I'm not especially upset about it, but just wish to point out that it's not very encouraging or welcoming as a gateway to the Linux community, is it? 

Well, I shall persevere despite these feelings, because I'm determined to get to where I want to be, but I think that if my experience of this forum back at the beginning had been similar to how it's been recently, I would never have even got to where I am now. I may decide to look at a distro that has a more responsive community.

---

### Post by QIII on 2021-09-22
Perhaps the person "disappeared" because they have a real life to attend to and that is more important to them sometimes than volunteering here?  Might they be sick, or traveling or on a business trip?  Taking time off with a new child?  Smelling life's roses?

How was the community more helpful a few years ago?

---

### Post by tea for one on 2021-09-23
> **heatopher2 said:**
> Let's be honest. This really isn't much of a "community" these days, is it? 

A community would function better if community members responded in such a way that others would benefit.

For example, have a look at this thread where a fix was suggested and, to all intents and purposes, the solution was acceptable.

Yet, the OP did not mark the thread as solved, therefore denying the community of a searchable solution.

[https://ubuntuforums.org/showthread.php?t=2465655](https://ubuntuforums.org/showthread.php?t=2465655)

It takes two to tango.

---

### Post by heatopher2 on 2021-09-24
> **tea for one said:**
> A community would function better if community members responded in such a way that others would benefit.

For example, have a look at this thread where a fix was suggested and, to all intents and purposes, the solution was acceptable.

Yet, the OP did not mark the thread as solved, therefore denying the community of a searchable solution.

[https://ubuntuforums.org/showthread.php?t=2465655](https://ubuntuforums.org/showthread.php?t=2465655)

It takes two to tango.

Well, look, if you want to go down that road, if you examine that thread once again you will notice that I did in fact say that the problem was fixed. I was not aware at the time that there was **such a thing** as marking the problem solved. Are you saying that you expect inexperienced members to be aware from the start of every convention on this forum? I don't remember anyone pulling me up on such a thing when I first came on this forum a few years back. I assume that those people understood that novices already have enough to get their heads around.

This only serves to reinforce what I'm saying - there are lots of assumptions that new people should immediately slot right in, and it only adds to the stress and confusion. I'm sure that there are plenty of people who are trying to switch over from Windows, but who give up due to that sometimes unwelcoming (and in this case, sarcastic) tone. I'm in quite a blunt mood today, sorry.

I have experienced this attitude on more than one Linux forum, by the way, so apparently it is not exclusive to this place. I always try to find things out before I ask questions, in order to make them not too stupid. I try to write my questions in a friendly and polite manner, and don't especially think that I've deserved the snarky comments that I've received on occasions. It may be that I write too much sometimes (and yes, I've been flamed for that), but that's only because I don't understand what's going on, and so feel the need to elaborate. If people don't have the time to listen/read properly, I don't really think that they should be volunteering on a forum which is a crucial gateway from Windows to Linux. Of course Linux is not for everyone, but with a more open-hearted welcome at the starting post it is certain that more people would transition successfully.

---

### Post by heatopher2 on 2021-09-24
> **QIII said:**
> Perhaps the person "disappeared" because they have a real life to attend to and that is more important to them sometimes than volunteering here?  Might they be sick, or traveling or on a business trip?  Taking time off with a new child?  Smelling life's roses?

Did I say that I didn't understand that that person might have good  reasons for disappearing? No, I didn't, because of course that is understood. Thanks to that person for being  the only one who has made a genuine attempt to help me through. 

> **QIII said:**
> How was the community more helpful a few years ago?

When I first installed Ubuntu, about five years ago, I of course had several problems getting things to work, and there were a couple of guys who hung around as long as was necessary to talk me through the issues. I was very grateful to them, and impressed by their dedication. Then a couple of years later I had a massive crash when I was trying to update, and just couldn't get the system back at all. There was some problem with GRUB (maybe - no idea, because I never got to the bottom of it) I wrote posts on here, one person started helping, and then disappeared. I wrote a couple more times, and no-one picked up. I subsequently gave up on Linux for the next couple of years, until coming back recently. 

Since coming back here some people have been helpful, of course, but I'm just finding the tone from others sometimes quite aggressive. I try to make my questions friendly/polite and not too stupid. That is to say, I try to research a bit before I ask, but sometimes I just get really glib and frankly impolite messages which don't help all that much, and so at this point I'm just saying what I think about that, because I think it's something that some of you should be thinking about. It's a very uncomfortable feeling when you have the sense that you're appearing really clueless in front of people, and IT is the worst of worlds for inducing that feeling. God knows - I've made my poor old mother suffer enough times with that feeling, and maybe this is my payback. I'm only saying that a few people here could learn to be a bit more sensitive about that, and avoid becoming defensive over a little criticism. This forum has been feeling to me a bit more like an exclusive members' club than an open and welcoming community. 

"Ubuntu" - "humanity towards others", right? "New to Ubuntu" should surely be the place where that pholosophy is most obviously practised. The most frustrating thing is when people tell you to do something  without explaining how to do it. If someone is "New to Ubuntu" that must  surely mean that they probably need walking through things. Better to  risk sounding condescending (in a nice way) than just leave people scratching their heads. 

Specifically on the topic that I originally posted about, I have said at least once that it's fine to tell me that the problem is too complicated (clearly it is complex) and that the best thing for me to do would be to reinstall (I do have the home directory backed up, plus a package list). The only shame of it is that I've really been trying my best to turn this into an opportunity to understand more deeply how things work, and not feeling much acknowledgement of that effort.

So be it. You can think what you like about what I've said. Maybe I could have expressed myself better in some places, but there's no point going back to cross every "t". I'm only human, and so are all of you.

---

### Post by mIk3_08 on 2021-09-24
> **heatopher2 said:**
> Well, I had quite a lot of trouble getting  Variety to work properly, so it makes sense that that is showing up.   Really a big shame, as it's such a nice app. I had a whole thread  about  it, here:
[https://ubuntuforums.org/showthread.php?t=2465658](https://ubuntuforums.org/showthread.php?t=2465658)

I marked it as "solved" because I did get it working the way it was  supposed to in the end, but maybe it's no  coincidence that things  collapsed completely around that time. I say  "maybe", because there  were already plenty of noticeable problems before  I fixed that. I kind  of doubt that it's only about Variety, though, eh.
Let me mention one other thing that I think might have caused  instability. Shortly after installing, back in July, I wanted to get  Ubuntu to hibernate nicely, the way that Windows does, and followed a  few links which got me to that point (I'll dig up the links if you think  it's relevant). It worked, but less than 50% of the time, from the  beginning, and more often than not I ended up needing to shut down or  restart (and then getting those "stop jobs" preventing the system from  shutting down for long periods). But hey, I don't know what things are  related to what, and that is why I'm here :~)

Actually, I  don't really know now for where I am to start with this situation  again. The problem you had in your logs are from September only. I don't  have any log records from from you in July. But I still find ways to  make a solution to the issue. Its just that, I have some personal issue  that I have to attend too.

> **heatopher2 said:**
> Let's be honest. This really isn't much of a  "community" these days, is it? People on here were much more helpful  when I first started experimenting with Linux a few years ago. One  person has properly offered to help, and of course disappeared because  it's too much for only one person to help out with the issue that I've  got. I'm not especially upset about it, but just wish to point out that  it's not very encouraging or welcoming as a gateway to the Linux  community, is it? 

Well, I shall persevere despite these feelings, because I'm determined  to get to where I want to be, but I think that if my experience of this  forum back at the beginning had been similar to how it's been recently, I  would never have even got to where I am now. I may decide to look at a  distro that has a more responsive community.

Actually, I'm still here looking some possibilities to the issue you had in your Linux Ubuntu Operating System.

---

### Post by heatopher2 on 2021-09-24
> **mIk3_08 said:**
> Actually, I  don't really know now for where I am to start with this situation  again. The problem you had in your logs are from September only. I don't  have any log records from from you in July. But I still find ways to  make a solution to the issue. Its just that, I have some personal issue  that I have to attend too.



Actually, I'm still here looking some possibilities to the issue you had in your Linux Ubuntu Operating System.

Hi again. Sorry, please understand that I really wasn't having a go at you at all. I really appreciate your help. All I was saying was that one person can't do this kind of thing on their own, and well.... there was just a load of frustration with other experiences on forums recently and in the more distant past.

Anyway, like I said, if it's all too much, please tell me, and I'll just reinstall from scratch. I'll also understand if you actually want to persist in order to understand the problem just as a matter of curiosity, because that's mainly what's driving me :~)

By the way, I have no idea how I'm supposed to get logs from July. I just ran the commands that I was told to :~)

---

### Post by vmpx on 2021-10-13
Try disable in browser "use hardware acceleration".

I have changed the Unattended-Upgrade on Ubuntu from every day to 14 days:

/etc/apt/apt.conf.d/10periodic
/etc/apt/apt.conf.d/20auto-upgrades

```
APT::Periodic::Unattended-Upgrade "14";
```

"0": means is disabled

---

### Post by vmpx on 2021-10-17
**How to fix Ubuntu 18.04 freeze after boot when NVIDIA card installed**

Replace in GRUB menu for 18.04 &#8221;quiet splash&#8221; with &#8221;quiet splash nomodeset&#8221; (On the grub screen click select &#8216;*Ubuntu&#8217; and press &#8216;e&#8217;)
After that freeze should be gone.

---

### Post by heatopher2 on 2021-10-18
Oh, hi. I had pretty much given up on hearing anything again, so haven't looked on here for a while. As it happens, I hadn't got around to starting over as yet, so I will have a look at this tomorrow (or more likely Wednesday :~)

---

