---
title: "CPU went to 100% for 2 hours"
date: 2019-11-22
forum: New to Ubuntu
---

### Post by kmax1940 on 2019-11-22
Hello, I am looking for direction on how to track down what happened with my server.
Ubuntu 16.04

I has been up for about 230 days with no issues at all.

This morning through my VPS providers dashboard I see that the CPU spiked to 100% for a couple of hours or so...

I looked in DMESG and dont see any errors.
All I see is warnings where UFW has blocked attempts...
It does not seem to be any more or less than the normal amount.

Any ideas on how I can track down what happened to make the CPU go to 100%?

I never did reboot... it just went back to the normal (low) amount of CPU usage on its own....

---

### Post by TheFu on 2019-11-22
What does the server do?  What are the risks?  Plain ftp?  Any php or node.js webapps?

There have been some crypto-mining malware specifically designed to work on Linux running around the last few months.

230 days of uptime?  Do you ever patch the kernel or libc?  About the longest uptime for an internet server should run that is maintained is 30 days.  That's about how long it is between kernel updates.  I suppose if you pay for landscape, then the kernel can be patched while online, then just the libc changes would require reboots.  

Check for this file: /var/run/reboot-required
if it exists, then a reboot is required.

As for tracking down what caused it, by rebooting you've probably destroyed the necessary logs to figure it out.  Did you look at the process tree?  See what was using the CPU? See which process started it?  Do you have server monitoring and alarming setup?  If so, that should be capturing everything you need to determine when a process eats too much RAM, files, disk, network, or CPU.  There are lots of tools for that. Setting 1 of them up isn't too hard, but it will need to be configured specifically for your server.

---

