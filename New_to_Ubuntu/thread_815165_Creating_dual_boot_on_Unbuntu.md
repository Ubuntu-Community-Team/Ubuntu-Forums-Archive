---
title: "Creating dual boot on Unbuntu?"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by niceguy123 on 2008-06-01
I have no ms windows on this machine only Ubuntu 7.04, It seems that I'll need to have windows too in order to access bank accounts and some other  "services" that only work on ms internet explorer. 

I've put in loads of time and effort into trying to find other solutions ies4linux and other browsers. I normally work with Firefox. 

In short, how can I install windows as a dual boot here? And what would be the way to install the smallest \ least resource hungry windows? (i only need it for the IE for a few minutes here and there?

---

### Post by shifty_powers on 2008-06-01
have you tried the user agent switcher add on for firefox?

it tricks the webstes into thinking you are using ie instead of ff, and it works for many websites for me...

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

might be an easier way than dual booting ;) many websites WILL work in ff, they just refuse to as they can't be bothered to provide support ...

plus, what happened with ies4linux?

---

### Post by SunnyRabbiera on 2008-06-01
try IE under wine or ie4linux?

---

### Post by sayakb on 2008-06-01
Install Winedoors from [http://getdeb.net](http://getdeb.net)
It has an IE6 installer. It might work for you.

---

### Post by shifty_powers on 2008-06-01
found winedoors to be very flakey.

tbh, he might well find that user agent switcher will do the job, and it is certainly the simplest way...

---

### Post by kansasnoob on 2008-06-01
If you decide to dual-boot this APC guide is simple and it works:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Every computer I have is dual booted for those times that I just must have Windows or IE, etc. I wouldn't touch Vista with a 10 foot pole. I've noticed both Clubit and Newegg have XP Home OEM for slightly over $80.00 (US). And unless Windows has changed their mind XP will be off the shelves next month! (Still supported for a few more years, at which time everyone will have Ubuntu :))

To keep things on the cheap side I just use AVG free anti-virus and Zone Alarms free firewall .............. and most importantly I only use Windows when absolutely necessary to decrease the risk of a virus, trojan, etc.

I now find myself booting windows once a week just to update the AV :)

But, it's there when I absolutely must have it.

---

### Post by niceguy123 on 2008-06-02
> **LinuxIsInnovation said:**
> Install Winedoors from [http://getdeb.net](http://getdeb.net)
It has an IE6 installer. It might work for you.

This one looks interesting. I've tried all or most of the other ideas here. I tried the link at getdeb and found winedoors for hardy and gutsy but I'm using fiesty, what should I do? (Last time I tried upgrading to hardy I lost all of my data and couldn't hook up to the internet).

---

### Post by rraj.be on 2008-06-02
If you just want a windows working environment then you can just get into 


VIRTUAL ENVIRONMENTS.


You can use VMWARE or VIRTUAL BOX to install Windows inside your ubuntu.

Else if you want to install windows seperately just make a free partition and then install windows in it normally.

The next step is you should reinstall your GRUB boot loader because windows will overwrite it.

to reinstall GRUB

```
1--> boot into live CD

2--> open terminal.

3--> Type sudo grub

4-->type find /boot/grub/stage1

5--> if it returned like (hd x,y)

   type root (x,y)
   setup (x,y) 


```


this will restore your GRUB

now you can dual boot your windows along with your ubuntu.

---

### Post by sayakb on 2008-06-02
I guess they removed it. I don't know whether 0.1.1 works in Feisty. Please verify before installing.
[http://www.wine-doors.org/wordpress/?page_id=3](http://www.wine-doors.org/wordpress/?page_id=3)

Feisty is supported till Oct 08 I guess.. Try to download Hardy image and do a clean install instead of upgrading.

---

### Post by niceguy123 on 2008-06-02
> **LinuxIsInnovation said:**
> I guess they removed it. I don't know whether 0.1.1 works in Feisty. Please verify before installing.
[http://www.wine-doors.org/wordpress/?page_id=3](http://www.wine-doors.org/wordpress/?page_id=3)

Feisty is supported till Oct 08 I guess.. Try to download Hardy image and do a clean install instead of upgrading.

I'm considering upgrading to Hardy, but a little wary from the last experience I had trying to upgrade to Gutsy and losing all of my data not being able to connect to the internet until finally re-installing fetsy again.  

Makes me think of the saying that goes: "If it not broken, don't fix it".

---

### Post by bumanie on 2008-06-02
There have been a few users who have had trouble with hardy, but overall, the vast majority of users, including myself, find it better than gutsy. I was like you  and used feisty for a long time, due to gutsy's less than stellar performance. When i got a new computer, I tried gutsy again, but is was still poor, so I moved to hardy beta. I've been using hardy since beta 6 and not had any major issues. Nothing's guaranteed, but the chances are hardy will perform well. Also the internet connection issues (at least cable or dsl) seem to have been solved.

---

### Post by durand on 2008-06-02
It will probably be easier to support you if you were on hardy. Backup all your data and just try upgrading...

---

