---
title: "Coming Back to Ubuntu what to install, do, what not to do"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by rgotten on 2012-10-27
On 2008 i installed ubuntu and then i place this question on ubuntu: [http://ubuntuforums.org/showthread.php?t=788493](http://ubuntuforums.org/showthread.php?t=788493) after having the server working for 4 years, last week, i had one hard drive failing (which i had during the 4 years and replace with no problem) but when i try to replace it i have a power outrage and it screw up my complete server. So now i am about to reinstall and even though have being 4 years, i still consider myself very new and would like some advise...So this are my questions:
since I have to do everything again I would like to know what has change and I have to do it the same way or differently.

1)I had  install ubuntu server 8.04, it was raid 1 (100mb) for /boot, raid 1 (2gb) for swap, Raid 5 (10gb) for / (system) and raid 5 (980 gb) for /home. this was done using 3 500 GB hard drive. My question here is if should i do the sama or do something different; ie: ext4 instead of ext3. LVM on top of the raids, or anyhting different that you will be suggest

2)In my first post on 2008 i was talking about a database, what i know and have being using is really a backuo of my windows computer into my server, do i need to install lamp or just samba..or is there anything new?...What i would like is to have maybe some main files that can be access from my 4 windows computer from the server (like forms and word documents), and also, any files that my staff has saved under there computer with client names or photos) to be backup into my server. 

3) i use until recently webmin (which is not supported by ubunutu), and it was a nive interface to mnanage the server as well as putty..Anything new on installing does??


Let me stop here for now..Thanks to anybody who can help

rgotten

---

### Post by mardybear on 2012-10-27
Hi rogtten...

Having just posted a 'rant' about the tiring cycle of upgrades and new versions...why not just reload 8.04 as it seemed to have worked well for you in the past. Old versions are still available on the site and although not offically supported the packages still get updated as needed.

I still use 8.04 (desktop not server) on a daily basis and it works better than any OS i've ever installed. You wouldn't need to relearn anything and could basically reinstall/setup just like you had it/liked it.

Just my thoughts...sorry i didn't answer any of your questions.

mardybear

---

### Post by gordintoronto on 2012-10-28
If all you need is a file server, Samba will do fine. LAMP is for creating a Web server.

I will disagree with Mardybear and suggest that the latest long-term release is the best way to go, which is 12.04. It will be supported for five years.

My personal feeling is that RAID is just one more thing which can go wrong. You still need to have good backup, since people will delete files and then decide they need them. There are several new  options to protect against hardware failure, such as Ubuntu One, Dropbox, Google Drive and even Skydrive. But you still need good local backup.

---

### Post by rgotten on 2012-10-31
> **gordintoronto said:**
> If all you need is a file server, Samba will do fine. LAMP is for creating a Web server.

I will disagree with Mardybear and suggest that the latest long-term release is the best way to go, which is 12.04. It will be supported for five years.

My personal feeling is that RAID is just one more thing which can go wrong. You still need to have good backup, since people will delete files and then decide they need them. There are several new  options to protect against hardware failure, such as Ubuntu One, Dropbox, Google Drive and even Skydrive. But you still need good local backup.
i agree with you on the backups, the thing i see a benefit with raid is that if a disk fail, (as has happen to me in the past) you change it with little or no downtime..but i agree that backups are a must always

---

### Post by newb85 on 2012-10-31
> **mardybear said:**
> ...why not just reload 8.04 as it seemed to have worked well for you in the past. Old versions are still available on the site and although not offically supported the packages still get updated as needed.

Really?  And when was the last time you installed any updates to 8.04?

---

### Post by mardybear on 2012-11-16
> **newb85 said:**
> Really?  And when was the last time you installed any updates to 8.04?
My father would have called you a smartmouth, i can think of a few other choice words.

Just today actually, many months after long term support 'officially' ended. Here are today's apt-get bug, security and enhancement updates:

The following packages will be upgraded: libtiff-tools libtiff4 linux-headers-2.6.24-32 linux-headers-2.6.24-32-386 linux-image-2.6.24-32-386

Running an old version of Ubuntu is great. There are minimal updates so the system runs very stable system. All of the major bugs have long been fixed. The old Ubuntus run great on older/lower spec hardware and, if necessary, there is lots of archived help available on this forum. Plus much of the 'new' software can still be installed manually or via deb packages if not listed in the good old repositories.

mardybear

---

### Post by Paqman on 2012-11-16
> **mardybear said:**
> 
Just today actually, many months after long term support 'officially' ended. Here are today's apt-get bug, security and enhancement updates:

The following packages will be upgraded: libtiff-tools libtiff4 linux-headers-2.6.24-32 linux-headers-2.6.24-32-386 linux-image-2.6.24-32-386


I'm very surprised by this, seems like the kernel team might be throwing the occasional bone out there?

However, it can't really be recommended as a good way to run an internet-facing server. You can't guarantee how much longer you're going to get security updates. Run an unsupported version for long enough and you'll get pwned by some script kiddie. 

If the OP wants a system they can rely on for years to come, they should install 12.04 LTS.

---

### Post by newb85 on 2012-11-16
> **mardybear said:**
> My father would have called you a smartmouth, i can think of a few other choice words.

Okay, so I should have been more respectful when I wrote that.  Apologies.  I'm not overly impressed with your ability to cogitate on "choice words", but provided the red doesn't prevent you from seeing your screen, cogitate away.

I guess I also should have admitted in my last post that I wasn't speaking from experience.  I don't run EOL systems.  Canonical says they don't actively support them, and from that I just assume that means they're not making sure EOL systems receive updates "as needed".  Apparently, in assuming, I've fulfilled the old adage.  You know what happens when we assume...  (I guess you can fill in your own choice words.)

---

### Post by newb85 on 2012-11-19
It occurs to me, those updates should come as no surprise to any of us, since 8.04 Server Ed. doesn't hit EOL until next April.

](*,)

---

### Post by coffeecat on 2012-11-19
A couple of thoughts.

> **newb85 said:**
> It occurs to me, those updates should come as no surprise to any of us, since 8.04 Server Ed. doesn't hit EOL until next April.

Indeed - 8.04 server edition is supported until next April and will get updates until then, hence the kernel updates.

> **mardybear said:**
> I still use 8.04 (desktop not server) on a daily basis 

But you won't be getting updates for the GUI components. Your web-browser in particular will not have had an update or security patch since May 2011. That is a security risk for your system.

---

