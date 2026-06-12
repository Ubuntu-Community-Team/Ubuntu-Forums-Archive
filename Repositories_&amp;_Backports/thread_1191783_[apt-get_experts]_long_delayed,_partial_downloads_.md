---
title: "[apt-get experts] long delayed, partial downloads keep resetting"
date: 2009-06-19
forum: Repositories &amp; Backports
---

### Post by Vhann on 2009-06-19
Hi,

My lil' story (so people can help me better):
Since I only have 56kbits/sec Internet bandwidth at my parents' place
and still want to keep the Kubuntu systems there up-to-date,
I add the following idea:
My Linksys WRT54GS running DD-WRT wakes on lan (cron job) one of the
computer at 22:30 each night. At 23:00 (let a lot of time to boot in
case the system decides it must fsck the 70 GiB PATA + 250 GiB SATA drives),
the cron daemon dials up on the Internet using a custom-made BASH script 
nd, upon successful completion, ```
apt-get -dy update && apt-get -dy upgrade
```. I then upgrade manually to avoid the system resolving package conflicts itself (since '-d' is 'download-only').

Then, each morning, the cron daemon stops the update, apt-cacher-import the downloaded packages (because I have 2 computers running Kubuntu Linux) then disconnects the computer from the Internet.

The setup works perfect, except for extra huge packages (such as openarena-data and/or alienarena-data), which are 280MiB each (which, at my current Internet connection is around 30 hours each...). Still, there wouldn't be any problem since apt-get seems to be able to resume partial downloads. But the thing is I found, by inspecting /var/cache/apt/partial that the package starts downloading the first night, resumes where it was stopped the second... then restarts all over the third.

By looking at 'apt-get' manpage, I saw there's an option archive::maxAge or something like that, but it seems to only concern index files.

Finally, please don't try to suggest me alternative ways if you don't know how to have the download continue, in the current situation nothing else will do (I don't live at my parents place so can't bring huge package updates on a USB key, debmirror is an already tried workaround but I want to have an "autarchic" solution).

Thanks in advance,
Vhann

---

