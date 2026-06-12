---
title: "Trojan"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by gunner ra on 2008-07-31
Hi Guys. I have vista and ubuntu on an dual boot. I enabled wine to use some program's, one of the program's was Spybot SD it informed me that I have an trojan ( Win32. Small. FB <Winsock> IP } on ubuntu I did a virus scan and Spybot on Vista and it comes up clean. Could this be a false positive?; and if not how do I fix this please Your's Gunner

---

### Post by neurostu on 2008-07-31
Spybot SD is designed to scan WINDOWS files and look for problems, I'm not suprised it gave you a false positive as it isn't really designed to scan a linux system...

---

### Post by gunner ra on 2008-07-31
Hi Neurostu. I enabled Wine, that allow's you to use Windows program's does it not? Gunner

---

### Post by arpanaut on 2008-07-31
Where does Spybot say the Trojan is located on your file system?

If you have brought files from windows into Ubuntu they could have this attached or maybe in email files?

Is it in your Wine folder? Never the less I doubt it could have any effect on your core Ubuntu system.

Unusual find/situation anyway????

---

### Post by neurostu on 2008-07-31
Yes, Wine allows you to RUN windows programs in LINUX. Wine is not an emulator or a Virtual Machine, it essentially provides the libraries windows programs need to run and allows them to run natively in linux.

Spybot SD is designed to scan files and find traces of malware. However, the way that malware works is going to be different in linux and windows as windows and linux are completely different and have differing ways of doing things.  So what may look like malware in windows could be completely fine code in linux.

So while you may be able to get Spybot to run in Wine it is a waste of time.  For example Spybot scans the system Registery looking for fishy entries... linux doesn't use a registery like windows so Spybot wont have a registery to scan and will probably register and error because of that.

Trust me... you don't want to run Spybot under linux.  You can run it in windows... but running it under wine in linux is really a waste of time and resources.

If you want to install virus scan software for your linux OS you can but a windows based virus scanner just won't work.

---

### Post by gjoellee on 2008-07-31
check out AVG for Linux: [http://free.avg.com/ww.download?prd=afl](http://free.avg.com/ww.download?prd=afl)

---

### Post by Darkade on 2008-07-31
It might be detecting a wine library as virus, since the wine libraries en ~/.wine are not the official windows ones. Thus Spybot might think it is not secure. if you want to install antivirus/antimalware in linux install clamav.
> 
check out AVG for Linux: [http://free.avg.com/ww.download?prd=afl](http://free.avg.com/ww.download?prd=afl)

I don't know, AVG has failed me a lot of times before :lolflag:

---

### Post by neurostu on 2008-07-31
I just noticed that Spybot is reported at WineHQ as an app that works... I have no clue why they do this b/c there is absolutely no reason to wine Spybot with Wine in Linux.

---

### Post by Paqman on 2008-07-31
> **gunner ra said:**
> Hi Neurostu. I enabled Wine, that allow's you to use Windows program's does it not? Gunner

Wine might be able to get Spybot to run, but it won't work properly. Spybot is designed to inspect and check a Windows system, not a Linux one.

If you stick to installing software from the repositories (and don't add untrusted repos) there's no chance of Ubuntu getting any kind of spyware. So you don't need Spybot anyway.

As for other malware (such as viruses), you don't need any special software. Keeping up-to-date with your security updates takes care of the risk completely. Virus scans, like defrags, are one of those annoying Windows maintenance tasks that you won't miss after you've been using Linux for a while.

---

### Post by Paqman on 2008-07-31
> **neurostu said:**
> I just noticed that Spybot is reported at WineHQ as an app that works... I have no clue why they do this b/c there is absolutely no reason to wine Spybot with Wine in Linux.

Possibly to check a Windows partition. Not sure how well that would work. Might be interesting to try, though.

I recently had to deal with a severe infection on a Windows PC. Luckily it was a dual-boot so that I could do enough repair work from within Ubuntu that it would boot into Win and run it's own scanning tools. Linux can be a very handy tool for fixing Windows system. I know Windows power users who keep LiveCD distros like the System Rescue CD around for that reason.

---

### Post by gunner ra on 2008-08-01
Wow Thank you Guys for all your input. I understand a lot more now. I have uninstalled all the programs in Wine, which I misunderstood to be an emulator. And installed Clam.  Being an windows user, you can understand my paranoia concerning **Viruses** and **Trojans**! Yours Gunner

---

### Post by mikewhatever on 2008-08-01
Out of curiosity, where was the infected file or trojan in the file system?

---

### Post by Paqman on 2008-08-01
> **gunner ra said:**
> Wow Thank you Guys for all your input. I understand a lot more now. I have uninstalled all the programs in Wine, which I misunderstood to be an emulator. And installed Clam.  Being an windows user, you can understand my paranoia concerning **Viruses** and **Trojans**! Yours Gunner

That's fine, we get this a lot from people switching from Windows.

Just one point: ClamAV only searches for Windows viruses, so it doesn't actually protect Ubuntu. It's really designed for servers.

For more information about security in Ubuntu:
[Psychocats security page](http://www.psychocats.net/ubuntu/security)
[Ubuntu Security on this forum](http://ubuntuforums.org/showthread.php?t=765421)

Short version: you don't need to take any special action to be secure provided you:
- Keep up-to-date with updates
- Haven't configured your machine as a server
- Only use trusted repos
- Don't do anything dumb

---

### Post by forger on 2008-08-01
I'm curious as well, what was the detected file? :P

---

### Post by dca on 2008-08-01
Wait a minute, this isn't all that far fetched.  Are you able to use Internet Explorer in Wine?  If so, and you currently use that as your default browser you could've picked up a hitch-hiker the put itself in Wine's equivalent of C:\DocsSettings\%yourprofile%\~local settings\Temp directories...

---

### Post by gjoellee on 2008-08-01
> **Darkade said:**
> It might be detecting a wine library as virus, since the wine libraries en ~/.wine are not the official windows ones. Thus Spybot might think it is not secure. if you want to install antivirus/antimalware in linux install clamav.

I don't know, AVG has failed me a lot of times before :lolflag:
AVG have actually never failed me, not even in Windows...

---

### Post by Sydius on 2008-08-01
If I were a Virus who came to an Ubuntu machine and looked around, I'd be very confused. But I imagine it's still possible to infect Wine with some (probably not a lot) of Windows viruses.

---

### Post by gjoellee on 2008-08-01
there as also a virus scanner available from Add/Remove, but anyway if you locate the virus it should be fear enough to delete the folder...:confused:

---

### Post by mikewhatever on 2008-08-01
The OP claimed the trojan was on Ubuntu, so it's interesting where in the file system. You don't see such things every day, and it's worthwhile verifying.

---

### Post by gunner ra on 2008-08-01
Hi Guys This is what Spybot stated. ( Win32. Small. FB <Winsock> IP } Trojan. This is from google roj/RuinDl-L is a Trojan for the Windows platform.

When first run Troj/RuinDl-L copies itself to &ltSystem>\&ltbasename&gt.exe where &ltbasename.exe> is a randomly generated five letter filename. Yours Gunner

---

