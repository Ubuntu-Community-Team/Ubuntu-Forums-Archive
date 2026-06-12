---
title: "Doesn't always complete shutdown process - hangs and leaves the power on"
date: 2016-03-06
forum: New to Ubuntu
---

### Post by david494 on 2016-03-06
When I shutdown (14.04), it sometimes doesn't completely shutdown and leaves the computer on. It's intermittent - very frustrating.

When using dash, it gets to a new screen that has 5 (I think ) dots that show the progress. It will then get stuck here - the dots no longer change color.

When using the cli, I issue the command "sudo shutdown -P now". 

In either case, the final state is such that I can't ssh into it, and it shows as disconnected in my dhcp server. 

Just to be clear, it's not all the time, just some.  Maybe half the time.

-david

---

### Post by DuckHook on 2016-03-07
It's a recurring problem and difficult to diagnose because it has many potential causes. You are shutting down properly. The -P switch tells the system to not just halt but power down. Therefore, the problem is likely a hung process that makes the kernel wait interminably and stops it from proceeding to a proper powerdown.

These issues can be caused by anything, but some of the more common culprits are rogue network drivers (esp WIFI), disk drives that can't be unmounted, or bad acpi translations/implementations.

For now, you can force a safe shutdown by using system-requests which is sometimes referred to as the REISUB technique (please Google for particulars). If you substitute the letter "O" for "B" in the last step of REISUB (so it becomes REISUO), you will force poweroff instead of reboot. This is a temporary measure, so don't rely on it as an ongoing standard practice. It is meant only to get you to a relatively clean poweroff while your problem is diagnosed.

As for diagnosis, it is impossible to start without knowing your HW specs: type, brand, model, CPU, RAM, GPU, etc. Please provide everything you can in your reply.

Please post back to this thread the output of:```
sudo lshw -C display,network,multimedia,power && df -h && sudo blkid && cat fstab
```...the output will be a lot, so be sure to enclose it in code brackets before posting.

As a first step, try adding the acpi=off switch to your kernel parameters in grub, as follows:```
sudo nano /etc/default/grub
```Find the line that says:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```...and change it to look like:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
```Then:```
sudo update-grub
```...and reboot. You will likely still have poweroff issues, so use the REISUB technique if necessary.

I doubt if adding this parameter will solve your problems, but it's a starting point. The real diagnoses can't start until you post your HW and driver specs.

---

