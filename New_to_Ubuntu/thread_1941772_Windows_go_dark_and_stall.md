---
title: "Windows go dark and stall"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by Acharn on 2012-03-16
I'm sure this is a common problem, but I couldn't find it. I have a failing hard drive. In fact it has basically failed and I'm running off a 10.10 Maverick Meerkat Live CD using an 8GB USB drive to have persistent sessions. After getting persistent sessions set up I installed the available security upgrades for Maverick, which may have been a mistake as it used up about half my available space. My computer is an Acer Aspire 1600 with only 1 GB of RAM.

One reason I installed the upgrades was because updates to Firefox are distributed as security upgrades. So I am now able to run Firefox 10.0.2, with Flash. The trouble is the program window frequently goes dark and seems to stall. If I am running another program, such as Image Viewer, it gets even worse.

I think this must have something to do with available memory, and paging in and out of virtual memory, but I haven't been able to find any info on how Ubuntu handles virtual memory. I found some advice on the recommended size for the swap partition, but that seemed to indicate the swap partition is only used for hibernating or suspending, which I don't do.

The thing which annoys me most is that while I was using Firefox 3.6 it was much faster and never showed this behavior, but of course I couldn't install Flash.

Suggestions would be welcome.

---

### Post by Jon Monreal on 2012-03-17
> After getting persistent sessions set up I installed the available security upgrades

Since you've updated Firefox, I have to wonder if the difference in performance is not due to the upgrades themselves but instead the fact that you are not running the Firefox from the CD but instead from the persistent USB installation.

In this case, performance might be improved by actually installing Ubuntu to the USB drive, although you then have to deal with even more limited space.

---

### Post by 2F4U on 2012-03-17
> **Acharn said:**
> I think this must have something to do with available memory, and paging in and out of virtual memory, but I haven't been able to find any info on how Ubuntu handles virtual memory. I found some advice on the recommended size for the swap partition, but that seemed to indicate the swap partition is only used for hibernating or suspending, which I don't do.

You are wrong if you think that swap is only used for suspend or hibernate.

[https://www.linux.com/news/software/applications/8208-all-about-linux-swap-space](https://www.linux.com/news/software/applications/8208-all-about-linux-swap-space)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by chipbuster on 2012-03-17
With 1GB of RAM, your computer is going to get swappy pretty fast.

---

### Post by coldraven on 2012-03-17
I was having the same problem. It was caused by FireFox's inability to run certain javascript. It always happened if there was a slideshow on the web-page.
The cure is to install and use Chromium or get the latest Firefox 11 (it appeared as an update yesterday)

---

### Post by Acharn on 2012-03-17
> **coldraven said:**
> I was having the same problem. It was caused by FireFox's inability to run certain javascript. It always happened if there was a slideshow on the web-page.
The cure is to install and use Chromium or get the latest Firefox 11 (it appeared as an update yesterday)
Well, it's certainly true that I've had these problems since about Firefox 6.3, and it's certainly true that it's connected with scripts which I expect are written in javascript, but it happens with other programs as well. Since I rarely have other programs open and NOT a web browser I can't say for sure that it's not being caused by the browser, so I'll try it, but I had Chromium for a while (still not comfortable with it) and had lots of problems with Flash crashing.

I really have to get a new hard drive installed -- hopefully the beginning of next month.

An alternative I've been thinking about: my BIOS doesn't allow for booting from a USB device, so there's no point installing to the USB drive, but I have an old, old, old 40GB hard drive that I had set up as an external drive. I have some data saved on it from years ago that I really, really don't want to lose, but there's about 18GB free space. I could use Gparted to make two separate partitions, one for swap space and 15GB for the installation, and install to that. It should work well enough for a couple of weeks.

---

### Post by Acharn on 2012-03-27
OK, I simply cannot boot from a USB device on this computer (Acer Aspire M1610). I reformatted the USB stick and set up a new persistent session; this time I did not install the updates, but I did install Chromium (which I'm now using), uninstalled Firefox 3.6 (hated to, it was so fast) and installed Firefox 11.0 so I could install Flash (completely unusable). The fault may be with one of my extensions -- I have LastPass, XMarks, ReadItLater, and AdBlock Plus installed. Probably I should uninstall AdBlock -- it's been the culprit in a lot of problems -- but the other three have become absolutely essential to me, and I have a form of AdBlock installed in Chromium which doesn't have the same problem.

Please note, this does not only happen with the browser. All programs I've tried running, Movie Player, RhythmBox, Mah-Jong, even the terminal, show it to some extent. I've wondered if it has something to do with my swap partition being farkled, but there's no swap at all shown in the persistent session. Also, I've got 1MB of RAM. Now I know that's less than the current standard, but I started out on the 8-bit Z-80 microprocessor, and I still feel like 640KB of RAM is more than anyone should ever need. Anyway, I've never read that Firefox needs more than 1GB, although I do know they've had problems with memory leaks in the past.

Well, I hope I can buy a new hard drive next week and do a proper installation so Firefox can run with the current kernel and supporting files and a proper swap partition.

---

