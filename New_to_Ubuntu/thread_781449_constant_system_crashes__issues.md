---
title: "constant system crashes / issues"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by grazed on 2008-05-04
I'm not really sure where to begin, so lets start here...

Firstly, this is somewhat directed towards linux in general so bare with me.

I own a HP dv6000 series notebook. VERY common hardware. The exact model number is dv6210us.

I cannot boot the linux mint cd. all options suggestions tried
I cannot boot the openSUSE cd (both gnome and kde configurations) all boot options known tried.
I cannot boot Mandriva 2008 gnome edition by cd. same deal.
God knows, if I try more I'm sure I will have similar results.

All of the above will hang at random points during the boot sequence, never at the same spot, just randomly. If I have a usb device plugged in, forget about it, I can't even get past the initial kernel boot.

All of the above were burned multiple times, multiple speeds, multiple drives. This is not a burning error.

Now on to distro's I can actually install...

Ubuntu: Been trying to use it for years now over multiple notebooks. EVERY SINGLE release since the 6.4 release and on will randomly decide to crash my system, typically every 20-60 minutes. Hard locks, with no entries into the logs.

This happens 3 different ways. The most prominent being while I have flash open on a website. (hard system crash, no logs) Secondly being while I try to run ANY virtual machine. (again, hard lock, no logs) And thirdly, the one time that I can read the logs, I get a random crash, whenever Ubuntu feels like it. I usually get a wireless LAN / bluetooth readout in the logs. (hard  lock)

Really freaking frustrating. 

Mandriva: Installed today, same exact issues as described with Ubuntu. Yet the crashes seem to be more frequent, not needing flash to be open.

So, 2 out of 6 very common distros will even boot on my system. Kinda sad.

The 2 that I have found refuse to run in any stable manner.

Is linux not for me? I'm really just not sure how this is supposed to be such a viable alternative when someone like me comes along with a good amount of computer knowledge, and hits a brick wall like this.

Any suggestions, or something I may be oblivious to is welcome.

I would provide system logs, but like I said... I don't get any.

Thanks.

---

### Post by HereInOz on 2008-05-04
I would think that if you were attempting to run 6 different distros, and 4 of the 6 would not install, and the other 2 were unstable, you should look at the hardware on which you are running them.  

Is there an issue with the particular hardware? Or is the particular laptop faulty.  I know that the laptop is a common machine, and probably there should not be any compatibility issues, but have you checked?

There are many instances of machines having a fault which manifests in Windows but not Linux, and the other way around, so do not discount the fact that the machine could have a problem.

Are you sure that you are installing it correctly.  You probably are but the question needs to be asked.  I encountered one bloke who was driving himself nuts trying to install Linux of various breeds, and could not get it to work, until someone told him that if he was going to partition the disk manually, he really did need a swap partition.

This last question takes on extra validity when you say that you have tried multiple releases over multiple laptops.  Either you are the unluckiest person in the world, or you are doing something which is causing problems.  Not what you wanted to hear, but given the history, it is something which needs to be considered.

---

### Post by grazed on 2008-05-04
I totally agree with everything you said. 

The only thing faulty with the laptop is a crapped out wireless card. Which was a common issue with the series. I opened up the laptop a while ago and manually disconnected it to rule that out. My ram / hdd / cd-dvd writer are all in tip-top shape. My graphics are integrated. 

As far as swap, I always have a 2 gig partition for it. Though I have yet to ever see it be used. =/

I really think I am that unlucky guy you speak of.

---

### Post by thiebaude on 2008-05-04
Hey, Grazed check this out, it's from a another ubuntu forum.Hope it works.The person that was having trouble got his problem fixed and he uses a HP dv6000 series notebook, good luck.

[http://ubuntuforums.org/archive/index.php/t-557162.html](http://ubuntuforums.org/archive/index.php/t-557162.html)

---

### Post by grazed on 2008-05-05
thanks for the link, checked it out to no avail though. =/

Here's an update.

Totally disassembled my laptop, physically removing my bluetooth card. took a can of air and cleaned it thoroughly. Switched out my wireless usb dongle, and swapped in a different set of ram.

Checked my cpu, ram, and hdd with a benchmarking tool, all is well. This is certainly not an issue with my hardware.

partitioned, and installed a fresh copy of 8.04. Installed only ndiswrapper and flash.

Total uptime after first boot? A Whopping 28 minutes. Awesome. 

Again I have no real entries in the logs, yet I will post the last few before the reboot. Note the crash occured around 6:17-18

syslog is as follows:

May  5 05:13:56 insomnia-laptop NetworkManager: <debug> [1209978836.724811] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVDRAM_GMA_4082N'). 
May  5 05:17:01 insomnia-laptop /USR/SBIN/CRON[6541]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  5 05:20:21 insomnia-laptop anacron[5711]: Job `cron.weekly' started
May  5 05:20:22 insomnia-laptop anacron[6549]: Updated timestamp for job `cron.weekly' to 2008-05-05
May  5 05:20:26 insomnia-laptop syslogd 1.5.0#1ubuntu1: restart.
May  5 05:20:26 insomnia-laptop anacron[5711]: Job `cron.weekly' terminated
May  5 05:25:21 insomnia-laptop anacron[5711]: Job `cron.monthly' started
May  5 05:25:21 insomnia-laptop anacron[7408]: Updated timestamp for job `cron.monthly' to 2008-05-05
May  5 05:31:16 insomnia-laptop anacron[5711]: Job `cron.monthly' terminated (mailing output)
May  5 05:31:16 insomnia-laptop anacron[5711]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
May  5 05:31:16 insomnia-laptop anacron[5711]: Normal exit (2 jobs run)
May  5 05:44:51 insomnia-laptop -- MARK --
May  5 06:04:51 insomnia-laptop -- MARK --
May  5 06:19:55 insomnia-laptop syslogd 1.5.0#1ubuntu1: restart.

I could use some help, thank you.

---

### Post by grazed on 2008-05-05
another hard lock just minutes after my post, crash at 6:56-57

total uptime 26~ minutes.

May  5 06:20:41 insomnia-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
May  5 06:20:41 insomnia-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
May  5 06:20:41 insomnia-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated. 
May  5 06:20:41 insomnia-laptop NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
May  5 06:20:41 insomnia-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
May  5 06:20:42 insomnia-laptop kernel: [  113.103929] wlan0: duplicate address detected!
May  5 06:20:42 insomnia-laptop ntpdate[6053]: step time server 91.189.94.4 offset 0.714765 sec
May  5 06:25:01 insomnia-laptop /USR/SBIN/CRON[6125]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
May  5 06:39:56 insomnia-laptop -- MARK --
May  5 06:57:44 insomnia-laptop syslogd 1.5.0#1ubuntu1: restart.

---

### Post by billgoldberg on 2008-05-05
It's obvious ubuntu (and other linux distro's) have problems with your hardware.

I run hardy on a pavilion dv4000 without any problems.

---

### Post by grazed on 2008-05-05
> **billgoldberg said:**
> It's obvious ubuntu (and other linux distro's) have problems with your hardware.

I run hardy on a pavilion dv4000 without any problems.

It's reported by ubuntu as fully supported. Actually, just about all debian releases seem to support my system.

EDIT: Also, if that was the case, I'm sure the 4-5ish million people that own one of these systems would have spoken up by now saying linux just will not work. (the v6000 is/has been the most popular laptop series in the past 2 years)

Couldn't find anything on openSUSE or mandriva on it though.

I'm leaning more towards the fact that it's a software issue. As far as the lockups with flash go, I switched browsers to epiphany. And have had an uptime of over an hour now, with flash going in the background.

Also found a few threads regarding the same issue, all referring to Firefox beta 3 as the source. This is what lead me to try another browser.

So in conclusion, at least the flash/lockup issue, was caused by a software problem. 

Even if this was not affecting me in any way, I still think it's pretty tacky to include beta software in an official release. Let alone a LTS edition.

---

### Post by grazed on 2008-05-05
I guess it was too good to be true, a few minutes after making this post, walking away to get some OJ. I was pleasently greeted by another hard lock.

uptime: 1:20~

May  5 07:30:01 insomnia-laptop anacron[6621]: Anacron 2.3 started on 2008-05-05
May  5 07:30:01 insomnia-laptop anacron[6621]: Normal exit (0 jobs run)
May  5 07:57:44 insomnia-laptop -- MARK --
May  5 08:17:01 insomnia-laptop /USR/SBIN/CRON[6726]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

one recurring entry I see every time is this cron report thing. Is there any way to disable that?

---

### Post by grazed on 2008-05-05
I suppose I found the issue. With compiz off everything is peachy.

Any ideas on what could be causing it to act badly with flash?

---

### Post by Tatty on 2008-05-05
> **grazed said:**
> I suppose I found the issue. With compiz off everything is peachy.

Any ideas on what could be causing it to act badly with flash?

I had problems on my laptop with graphics on hardy, i often got locked black screens and couldnt switch to a tty console.  

I discovered it was a problem with the latest nvidia driver, so i used envyng (in the repos) to install the 96.xx.xx driver and all worked much smoother from there on.

Also the proprietry adobe flash reader is known to be rather buggy

---

### Post by grazed on 2008-05-05
> **Tatty said:**
> I had problems on my laptop with graphics on hardy, i often got locked black screens and couldnt switch to a tty console.  

I discovered it was a problem with the latest nvidia driver, so i used envyng (in the repos) to install the 96.xx.xx driver and all worked much smoother from there on.

Also the proprietry adobe flash reader is known to be rather buggy

thanks^ I tried but no dice. =/ crashed within 30 minutes again. It's worth mentioning that I am now getting crashes without flash playing. Just completely ranadom.

May  5 14:11:47 insomnia-laptop -- MARK --
May  5 14:17:02 insomnia-laptop /USR/SBIN/CRON[10020]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  5 14:30:07 insomnia-laptop syslogd 1.5.0#1ubuntu1: restart.

so, I've only posted about half of my logs. Ubuntu has hard locked on me about 11 times today in a 6 hour period.

Anyway, the only thing that is showing up in my logs is this cron report stuff. 

again...help would be appreciated. I know this isn't hardware failure, and I'm almost positive that this can be remedied.

Please help. =/

---

### Post by grazed on 2008-05-05
Tried the third nvidia driver. I'm still locking up, twice since my last post. Same last messages in my log.

This is getting beyond frustrating. I could really use some help.

If not, I really believe they need to remove my laptop series from the supported list.

thanks.

EDIT: I also wanted to sum everything up. These lockups occur with effects on and off. With flash playing or not, and with all 3 nvidia drivers.

I also thought it was worth mentioning that I have never crashed while using the live cd.

---

