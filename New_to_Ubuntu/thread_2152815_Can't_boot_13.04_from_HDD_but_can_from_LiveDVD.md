---
title: "Can't boot 13.04 from HDD but can from LiveDVD"
date: 2013-06-09
forum: New to Ubuntu
---

### Post by Acharn on 2013-06-09
Since I upgraded to 13.04 I've been having problems with my internet connection closing. To restore the connection I had to reboot the computer; rebooting the router didn't help. Then I started getting occasional messages, "Ubuntu encountered an internal error. Do you want to report it?" Then when I rebooted I started seeing a second start and then the grub menu came up. Hit return on the Ubuntu line, no problem, but worrisome. Today after running the computer several hours I lost the internet connection, rebooted, and got nothing. Tried several times to boot, no use. Once got to grub screen, but when hit enter did not finish. Tried booting from 12.04 LiveCD, success. Tried booting from 12.10 LiveDVD, success. Tied booting from 13.04 LiveDVD, success, but got error message, "Ubuntu encountered internal error. Do you want to report it?" Clicked on yes, saw that cron had encountered a memory error. Wish I had written the address down. Anyway, after that was able to run. Have rebooted to 13.04 several times since without error message.

I'm not sure what is the best thing to do next. I reinstalled 12.04 last month for a number of reasons. Reinstalling all the executables and ppa's was tiresome but not a real problem. Everything seemed to be working fine and, because I had set the /Home directory up as a separate partition I wad all my data. I decided to upgrade, and the upgrade to 12.10 went smoothly; so did the upgrade to 13.04. I was a little worried by the dropped internet connections, but it was an annoyance, seemed not to be a big deal.

I am not afraid of reinstalling Ubuntu, but not knowing what the problem is I'm not sure what to do next.

---

### Post by 2F4U on 2013-06-09
While your post has a lot of words, there is not much information in it. How is anybody supposed to help you without specific error message (which you seem to be able to reproduce but refuse to share), log files or something like that? You don't even post your hardware specs.

---

### Post by gordintoronto on 2013-06-09
In 13.04 there is a program called Disks. If your hard drive supports SMART Data, it will tell you if the drive is Healthy.

Many people encounter problems when they go through two rounds of Upgrades. I keep a separate /home partition, and never upgrade, always do a fresh install. So far, so good.

---

### Post by Acharn on 2013-06-09
I keep a separate /home partition, too. How do you do a fresh install without having to reinstall all your programs? When I tried not formatting the Ubuntu partition, I got a message that it was unable to install the boot sector, and I couldn't boot.

---

### Post by gordintoronto on 2013-06-10
You are right, I reinstall any programs which are not defaults. In many cases, I get an updated version. Because of my column in Full Circle Magazine, I tend to install a lot of programs just to play with them, so this is a chance to clean things up. I keep a list of the programs I actually use. I also export my bookmarks and email from Evolution, and back those up along with essential data.

Did you check the SMART data from your hard drive?

---

### Post by Bucky Ball on 2013-06-10
Upgrades, especially two in a row, are known to be occasionally problematic. I would stick with the LTS release myself (I do) and reinstall what worked. Was there a specific reason for the upgrade? If you just want a stable system, stick with the LTS unless you have a specific reason not to. I have spare partitions to diddle about with anything else I fancy. 

PS: I have a separate data partition rather than a /home. When I install an OS I let it install its /home directory in / then delete the directories in /home and make symlinks to the directories on my /data partition, /Documents, /Videos, /Music, etc. there instead. That way, if I have three installs, they are all accessing exactly the same data via their /home directories which contain only symlinks, effectively no valuable data at all. Kill the OS and reinstall, no matter to the personal data on /data.

PPS: This is kinda like having a separate /home partition but not quite ...

---

