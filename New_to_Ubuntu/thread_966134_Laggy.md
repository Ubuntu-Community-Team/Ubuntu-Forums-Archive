---
title: "Laggy"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by zvyx on 2008-11-01
Hello,

I recently switched over from WinXP to Xubuntu on my ageing laptop, to solve the lag of WinXP. I had heard great things about Xubuntu's ability to run on low-RAM machines, so I grabbed the Alternate install for Xubuntu. Here are the main laptop specs:

* Centrino (P4-M 1.7ghz 400mhz FSB, 2mb L2 cache + 802.11b/g)
* Intel GMA 900
* 256mb DDR2-400
* 40gb hdd (5400rpm)

I added a 1gb swap file partition on the drive, left 20gb as fat32, and 18.6gb as ext3. Otherwise it was a standard install.
I was impressed that wi-fi worked out of the box with Xubuntu, as well as the complete-OS feel, with all the apps included. However, I transferred to Xubuntu for performance, and wasn't as impressed. Once running Pidgin IM with 2 chat windows open and Firefox with 3 tabs, things really started to lag. And with Amarok playing and Firefox with 1 tab, it took about 15 seconds to type the URL, and another minute for the page to load, while audio was stuttering.

Maybe I was expecting too much, but under WinXP, it could still run Winamp + Firefox with 2 tabs + MSN Messenger with no probs, plus Avast's On-Access Scanner (basically, a real-time antivirus shield), and it only started to die once I switched from Winamp to play a movie. I've heard Xubuntu runs "very well" on 128mb ram, so I'm kind of puzzled as to why its not running as well on 256mb. On start up it uses 190mb ram, and about 150mb on the swap file partition.

How could I increase performance / decrease response times?

Cheers for any help :)

---

### Post by Kevbert on 2008-11-01
Welcome to Ubuntu.
A common way of speeding up Xubuntu is to install [[COLOR="Red"]fluxbox[/COLOR]]("http://www.howtogeek.com/howto/ubuntu/installing-fluxbox-on-ubuntu-linux/").  The other thing would be to add more ram if possible.

---

### Post by diablo75 on 2008-11-01
Firefox is a little bit of a RAM hog... well, at least that much can be said when you are running in on a computer with only 256MB of ram.

What I would do if I were you is open up your System Monitor (I don't remember the exactly location of the menu item, but I think it's under Applications>System>System Monitor) and check to see how much memory is currently being used by processes that are active, and then use this information to adjust your usage habits).  Your computer has the CPU horsepower to do quite a bit, but with only 256 MB of RAM, you are going to have to expect some drawbacks.

While Windows XP alone would do much better under the given constraints, I would argue that Windows fails in providing you peace of mind in the department of security out of the box.  Would you dare pay for, install and run Norton Antivirus on a Windows machine with only 256 MB of ram, or Zone Alarm, Spysweeper, etc.?  I wouldn't if I were seeking snappy performance.  If you want to do a fair comparison, install all of those programs in Windows with the given RAM you have, and then compare XP's performance to Xubuntu's.  I recently installed Xubuntu on a 400Mhz laptop with 192 MB's of RAM and I was happy about the fact that it could run an OS that was actually supported and up-to-date (albeit very slow) without worry about viruses or other security issues (the thing originally ran Windows 98, a joke of an OS by today's standards).

I would consider purchasing more RAM if I were you.  It's not expensive.

---

### Post by m_l17 on 2008-11-01
I use Xubuntu on a Ibm T21:

Pentium III 1.2ghz
60gb hard drive
768mb of ram
S3 for graphics

It's runs great :D What you need is to add as much ram as you can and it will run much better. If not try fluxbox or openbox. And welcome.

---

### Post by ugm6hr on 2008-11-01
> **zvyx said:**
> I had heard great things about Xubuntu's ability to run on low-RAM machines, so I grabbed the Alternate install for Xubuntu. Here are the main laptop specs:

* Centrino (P4-M 1.7ghz 400mhz FSB, 2mb L2 cache + 802.11b/g)
* Intel GMA 900
* 256mb DDR2-400

I think you may have been misled.

Xubuntu is by no means the lightest XFCE Linux distro.  And since Gutsy (7.10) has been little different than Ubuntu with XFCE (with multiple Gnome dependencies).

If you like Ubuntu (and it's support), the options are:
1. Persevere with Xubuntu, and remove some of the heavier startup apps.
2. Install an alternative Window Manager / desktop (e.g. fluxbox, openbox or LXDE)

This may be of interest: [http://ubuntulite.tuxfamily.org/](http://ubuntulite.tuxfamily.org/)

Other things to consider:
Swap Firefox for Opera
Remove Network Manager (and replace with Wicd)

---

### Post by zvyx on 2008-11-01
cheers all i'll try the fluxbox and removing/swapping some programs :)

---

### Post by lisati on 2008-11-01
Thanks for the suggestions. I recently updated to 8.10 on my 2-year old laptop (256Mb ram) via a fresh install and had noticed it was a bit laggy compared to Feisty - switching to Xubuntu did help a bit, and now fluxbox is another thing for me to check out......

---

### Post by zvyx on 2008-11-04
well I installed fluxbox... wow what a difference :O
interface is nice and neat, and loads up really quick - love it ^^
the amarok/firefox/pidgin seems to be pulled off very well now :)

thanks all for the help :)

---

