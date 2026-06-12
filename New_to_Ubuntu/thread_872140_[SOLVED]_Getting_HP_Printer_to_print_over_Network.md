---
title: "[SOLVED] Getting HP Printer to print over Network"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by 44tr on 2008-07-27
OK, I'm converting my son to Ubuntu.  I have Ubuntu on desktop with HP2550 printer plugged in and shared on my wireless network.  I can't seem to figure out how to get the printer detected from my son's machine over the wireless network and installed.  Both are running Ubuntu.  The included Ubuntu docs are not to helpful here.  Can anybody point me at a step by step process ?  or write one here ??:)

---

### Post by halitech on 2008-07-27
first important question, how is the machine hooked up? is it USB to 1 machine or is it hooked to the network as well? (sorry, don't know the printer) If it is USB to 1 machine, does it work on that computer?

---

### Post by anewguy on 2008-07-27
Try the following:

[http://ubuntuforums.org/showthread.php?t=34795]("http://ubuntuforums.org/showthread.php?t=34795")

[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/187724]("https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/187724")

[https://help.ubuntu.com/community/Printers]("https://help.ubuntu.com/community/Printers")

There are many more if you do a Google or Yahoo search using the following:

ubuntu sharing usb printer


How some of it helps. :)

---

### Post by 44tr on 2008-07-27
Thanks for the replies so far.  The printer is an HP laser printer hooked up by USB interface.  My desktop (printer plugged in locally and shared) is plugged directly into my router.

My son's computer is wirelessly connected to router via a USB interface adapter.

Though I can ping other windows machines on my network from my Ubuntu desktop, I can't ping my son's computer running Ubuntu (8.04 on both), though no problem using internet on his machine; also can't ping my desktop from his machine.

Will try to follow links provided while wait for answer.  Thanks.

---

### Post by halitech on 2008-07-27
assuming that you can print from your computer with no issues as first step :)

if you can't ping him and he can't ping you then sharing is going to be an issue. open a terminal and do
```
ifconfig
```
on both computers and check the IP addresses. since he is on wireless, he *may* have grabbed an IP from another wireless router which would put him on a different network and prevent you from pinging and thus sharing the printer.

---

### Post by gjoellee on 2008-07-27
try this:

DOWNLOAD:
[http://sourceforge.net/project/downloading.php?groupname=hplip&filename=hplip-2.8.6b.run&use_mirror=osdn](http://sourceforge.net/project/downloading.php?groupname=hplip&filename=hplip-2.8.6b.run&use_mirror=osdn)

COMMAND:
> sh hplip-2.8.6.run  NOTE: The version of HPLIP may have changes since this post and therefore you may also change the version in the command

Now follow the instructions... need more help go to the official HPLIP install tutorial: [http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

---

### Post by 44tr on 2008-07-27
OK, the first link above talks about manually editing the cups configuration file; it may come to that, but seems crazy that this should be necessary for common task.
2nd link doesn't seem to address my problem exactly.
3rd link is instructions that say you should just plug it in and it is autodetected and works; I wish.

I'll look at ifconfig, but I can say that I have configured all my machines with static IP addresses, so I'm pretty confident the machines aren't picking up strange IPs:)

I'll do google searches for threads if it comes to that, but it takes a while for me to sort and read through to find relevant hints that may or may not solve problem.  It seems like this should be so easy for so common a task; so many other bigger challenges were autoconfigured and worked like magic.

---

### Post by 44tr on 2008-07-27
One more thing, given the pinging issue, the network issue may be the roadblock; if that is solved, maybe there won't be another roadblock :)

---

### Post by halitech on 2008-07-27
> **44tr said:**
> OK, the first link above talks about manually editing the cups configuration file; it may come to that, but seems crazy that this should be necessary for common task.
2nd link doesn't seem to address my problem exactly.
3rd link is instructions that say you should just plug it in and it is autodetected and works; I wish.

I'll look at ifconfig, but I can say that I have configured all my machines with static IP addresses, so I'm pretty confident the machines aren't picking up strange IPs:)

I'll do google searches for threads if it comes to that, but it takes a while for me to sort and read through to find relevant hints that may or may not solve problem.  It seems like this should be so easy for so common a task; so many other bigger challenges were autoconfigured and worked like magic.
shouldn't have to do any manual configurations to get it to work

far as autodetection goes, that is only for the main machine that the printer is connected to. It will not autodetect a printer on a network.

other option is if you both have firewalls on that are preventing you from pinging one another.

---

### Post by 44tr on 2008-07-27
Umm, what is HPLIP and why will it solve my problem?

---

### Post by halitech on 2008-07-27
HPLIP is the driver package for HP printers. It will install the drivers so you can use the printer but the first step is seeing the other computer that you want to install the printer on.

---

### Post by 44tr on 2008-07-27
No firewalls on either machine right now; the DSL modem uses NAT then goes through router.  I'm sure some genious could break me but seems unlikely they will try.

This link:  [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

does SAY that cups publishes shared printers to network so that other Ubuntu machines should just be able to see them and then you just pick it off the list when you install.  Doesn't it?  Do they not know what they are talking about, or was this feature disabled in 8.04 (sounds nuts)?

---

### Post by halitech on 2008-07-27
so we are back to the lack of connectivity between the 2 machiens. have you checked the IPs just to make sure they are on the same network? (not doubting your word but there has to be some reason if there are no firewalls involved)

---

### Post by 44tr on 2008-07-27
Ah, the HP printer driver package.  The printer seems to work fine (admittedly limited testing) when plugged in locally.  I used the same install on my son's machine.  It doesn't have the same driver?  It can't even ping my desktop, so it seems we need to get that fixed before worrying about the right driver, yes?

---

### Post by halitech on 2008-07-27
it would have a local driver but you are right, we need to resolve the no ping issue before we worry about the drivers

---

### Post by jimrz on 2008-07-27
just for grins, on the wifi connected box 

1- right click on the network ico > connection information and insure that is, in fact, connected to your AP. (Sure does not sound like it is). If not, left on the icon and select your ESSID. If it is ...

2- Check your /etc/samba/smb.conf on both boxes and make sure youe "Workgroup" name is identical on both.

3- Again on both boxes go to System > Administration > Printing > Server Settings and make sure the first 3 check boxes ("show printers shared by other systems", "share published printers connected to this system" and "allow printing from the internet" are all checked. Once this is all done click "Refresh" in Printing on the wifi box and you should see your printer listed.

---

### Post by 44tr on 2008-07-27
OK, I can ping the desktop now.  All I did was open the network connection properties and look at them to make sure they are what I thought and closed it.  Now it pings fine; that worries me - problem solved after no fix.

Now I try going to System - Admin - Printing 
Add IPP printer; what do I type for HOST?  the name of my desktop with the printer attached?  Tried that and a search did not see any printers, though the shared box is checked on the properties of the printer at my desktop.
Stuck again.

---

### Post by 44tr on 2008-07-27
Not running Samba.  Just two Ubuntu machines having problems at moment.

---

### Post by 44tr on 2008-07-27
Umm, what is AP?  If adapter, it has to be connected if I can now ping, yeah, and was having no trouble in internet before.  No other way to connect.

---

### Post by halitech on 2008-07-27
if it is hooked up with USB to the desktop you don't want IPP printing, there should be an option for Windows Shared printer, slect that and then you should be able to browse the network to the printer. Also there will be a place for a username and password (if required)

---

### Post by halitech on 2008-07-27
> **44tr said:**
> Umm, what is AP?  If adapter, it has to be connected if I can now ping, yeah, and was having no trouble in internet before.  No other way to connect.

AP = Access Point (ie. your router)

---

### Post by jimrz on 2008-07-27
Do this:

 Again on both boxes go to System > Administration > Printing > [COLOR="Red"]**Server Settings**[/COLOR] and make sure the first 3 check boxes ("show printers shared by other systems", "share published printers connected to this system" and "allow printing from the internet" are all checked. Once this is all done click "Refresh" in Printing on the wifi box and you should see your printer listed.

At least on my Ubuntu boxes (6 of them), it seems to make a difference that all these boxes are checked on each machine, not just the host.

AP = wireless access point. In your case it is located in your router.

---

### Post by 44tr on 2008-07-27
Neither machine is running SAMBA so why use Windows printer option?  It seems like it shouldn't be necessary to run SAMBA and emulate Windows workgroup for two Ubuntu computers.  If so, is very peculiar.

---

### Post by halitech on 2008-07-27
if you aren't using SAMBA then how are you sharing the printer?

---

### Post by 44tr on 2008-07-27
I did check all three boxes on both machines, refreshed, tried to add Windows printer, don't see it (not big surprise since it isn't running SAMBA right?).  Tried to add IPP printer (isn't that the protocol best supported by CUPS?), but adding the name of computer printer is on to HOST doesn't find anything either.  ??  Seems like I'm overlooking something obvious, but can't for life of me figure out what.

Linux still seems to be a little frustrating in that when something works, it works better than anything else around by a mile, but when it doesn't work, it seems to take forever to fix if you aren't command line genius.  Will keep at it though :)

---

### Post by halitech on 2008-07-27
IPP assumes your printer is connected directly to a network and has its own IP address so it won't connect if it is using USB. I think you need to install SAMBA at least on the machine that has the printer attached to it and enable sharing of the printer there.

---

### Post by anewguy on 2008-07-28
Was hoping from the 1st link in my previous reply, where you complain about editing the cups configuration (if that is even needed) that you would have seen Samba there.  Next time I guess I need to be a little more specific with my answers.  Sorry.  At any rate, as already has been suggested, install Samba 1st and get it to the point where you can share folders if you want to (e.g., know that it is working), then move on to the printer sharing.  IF needed, you could always do the cups config.

Also, when setting this all up, I would think by default you still have iptables which in itself acts as a firewall.  You may need to reset/flush the rules on both boxes to get them in sync again.

---

### Post by 44tr on 2008-07-29
Thanks ANewGuy.  I guess I will have to investigate SAMBA more carefully.  I was under the impression that Samba was only used for Windows file sharing such as acting as a file server for Windows clients to avoid the $1K or so for a Windows server license.  It seemed that this function might be resource intensive so I didn't want it bogging down the performance of my desktop by keeping it running in the background just so my family could use my printer now and then.  Perhaps it is not as resource intensive as I thought; will give it a try.  Does Samba need to be running on all the Ubuntu machines that want to use the printer or just the "print server"?

That said, is there a non-Samba way around this?  My printer doesn't have its own NIC, but can I buy some sort of cheap print server that I can plug it into and connect it to my network?  The just add IPP printer?  How much would a decent one be that would reliably work with GNU/Linux?  Suggestions?

Thanks for help.

---

### Post by 44tr on 2008-07-29
OK, I installed SAMBA using Synaptic.  Now what?  It doesn't appear in any menus that I can see; no tool under system - admin to configure it with; is it running?  How do you tell?  if not, how do you start it? automatic at bootup?  I did type 'info samba' at prompt and it told me that samba was a program used to .... configured using smb.conf ... So I typed 'info smb.conf' and there was 7000 lines describing all of the esoteric features of the file; none of the first few pages I looked at looked useful, but it did say the file was designed to be configured by the swat program... So 'info swat', not installed.  Look at Synaptic...swat is program used for web administration of file and print server.

This is the easy way to enable printing over a home network?  I am getting headache.  Does Linux/Ubuntu deliberately make this harder than it has to be?  Sorry for venting; I am just of the opinion that a desktop system for non-junkies should be able to allow installation, configuration and do every common task without ever opening a terminal or manually editing a config file.  I'm more of a junkie than most, so please help me, but I also want to see Linux get beyond 1% market share to get better vendor support; that won't happen when experiences like this are the norm, even on compatible hardware.

Thanks in advance for any more kind help.

---

### Post by kerryhall on 2008-08-05
Hey, I am having the exact same problem. I have all the boxes checks, no printers show up on any of my ubuntu machines. I have no windows machines on my network, so no need to use SAMBA, right? They all ping and ssh to each other fine. The printer works fine locally. I am getting sick of using scp to the printer machine to print :(

All I want to do is share one printer.

Please help!!

---

### Post by st33med on 2008-08-05
Hah. Why is everybody giving really complex solutions?

Usually, he sets an option somewhere in the Printers GUI (Samba) to share the printer that is wired over the connection. Then, the client end is setup to detect and enable it as the default printer.

To do this, go to System>Administration>Printing, click New Printer up in the corner. Click Windows Printers via Samba and click Browse. Select the printer and hit forward.

---

### Post by 44tr on 2008-09-15
That last post is right.  I also had to choose a more generic hp driver since the specific one downloaded from HP wouldn't work.  Now I can print from any computer in the house, Windows or Ubuntu.  Thanks for all the effort.

---

