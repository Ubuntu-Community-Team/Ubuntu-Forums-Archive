---
title: "Ubuntu 18.04 freezing often"
date: 2019-06-03
forum: New to Ubuntu
---

### Post by jpsullaz on 2019-06-03
I have a Zotac Nano box with Ubuntu I've been using for a short while and have been having a freezing issue since I bought it (used). Seems to work great but locks up hard (no amount of waiting helps and will not respond). Thought it might be my external hard drive but just froze with it unplugged. Third time today, will work for a few hours then freeze with nothing major running. 

Log excerpt when it froze at 15:53:

Jun  3 15:38:05 jp-ZBOX-CI320NANO-series systemd[1]: Starting Hostname Service...
Jun  3 15:38:05 jp-ZBOX-CI320NANO-series dbus-daemon[805]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jun  3 15:38:05 jp-ZBOX-CI320NANO-series systemd[1]: Started Hostname Service.
Jun  3 15:38:05 jp-ZBOX-CI320NANO-series nautilus[3791]: Called "net usershare info" but it failed: Failed to execute child process “net” (No such file or directory)
Jun  3 15:38:33 jp-ZBOX-CI320NANO-series kernel: [ 3897.926617] perf: interrupt took too long (3275 > 3258), lowering kernel.perf_event_max_sample_rate to 61000
Jun  3 15:56:51 jp-ZBOX-CI320NANO-series systemd-modules-load[356]: Inserted module 'lp'
Jun  3 15:56:51 jp-ZBOX-CI320NANO-series systemd-modules-load[356]: Inserted module 'ppdev'
Jun  3 15:56:51 jp-ZBOX-CI320NANO-series systemd[1]: Starting Flush Journal to Persistent Storage...
Jun  3 15:56:51 jp-ZBOX-CI320NANO-series lvm[361]:   1 logical volume(s) in volume group "ubuntu-vg" monitored
Jun  3 15:56:51 jp-ZBOX-CI320NANO-series systemd[1]: Started udev Coldplug all Devices.

Any advice would help thanks!

JP

---

### Post by kurt18947 on 2019-06-03
I'm not familiar with that box but would it be possible to 'expose the innards' and set a fan to blow on it? Try to eliminate overheating as a cause.

---

### Post by crip720 on 2019-06-03
Think you are affected by the intel baytrail bug.  Here the fix, but first check the cpu you have is baytrail.  [https://askubuntu.com/questions/749349/how-to-set-intel-idle-max-cstate-1](https://askubuntu.com/questions/749349/how-to-set-intel-idle-max-cstate-1)

---

### Post by jpsullaz on 2019-06-03
Thanks, mine says product: Intel(R) Celeron(R) CPU  N2930  @ 1.83GHz
so I'm not sure. The link doesn't really mention baytrail.

---

### Post by jpsullaz on 2019-06-03
These are SSD boxes, overheating shouldn't be a problem though my room is warm (Phoenix). Would think the log files would show something like that.

---

### Post by crip720 on 2019-06-04
A link talking about your cpu specs [https://www.notebookcheck.net/Intel-Celeron-N2930-Notebook-Processor.112088.0.html](https://www.notebookcheck.net/Intel-Celeron-N2930-Notebook-Processor.112088.0.html) . Follow instructions in link for fixing from my first post, and the freezing should not happen as much.  Depending on your set up you might get days to months of it not freezing.  It is the cpu you have to worry about overheating, does not matter if hard drive or ssd.  Having a can of compressed air and blowing thru box vents a couple times every few months or once a year won't hurt.

---

### Post by jpsullaz on 2019-06-05
Thanks I will try to eliminate overheating as a cause. I found and installed PSensor so I will monitor it though at this time it does not seems to be the issue. Hasn't froze yet today :guitar:

Edit: spoke too soon (of course) froze right after. I think I found the correct solution (thanks to that link) which called out my specific processor (and even the ZOTAC Zbox!) which is this:

[h=3]Affected processors AFAIK:[/h]  Atom Z3735F (Asus X205TA, Acer Aspire Switch 10, Lenovo MIIX 3 1030) 
Atom Z3735G
Celeron J1900 (Asus ET2325IUK, shuttle XS35V4)
Celeron N2940 (Acer Aspire ES1-711, Chromebook)
Celeron N2840 (Acer Aspire ES1-311)
Celeron N2930 (Jetway JBC311U93, Zotac Nano CI320)
Pentium N3520 
Pentium N3530 (Acer V3-111P)
Pentium N3540 (Dell Inspiron 15 3000, Lenovo G50, ASUS X550MJ)
  (please (suggest an) edit to add your own device if affected)
  [Complete list of Bay Trail processors may be found here]("http://ark.intel.com/products/codename/55844/Bay-Trail?q=bay%20trail#@All")
  [h=3]There is a simple workaround for this until it gets properly fixed upstream.[/h]  You just need to pass a [kernel boot parameter]("https://wiki.ubuntu.com/Kernel/KernelBootParameters")  and the random freezing stops completely. The parameter may increase  battery consumption slightly, but it will give you a usable system.

  You do this by editing the configuration file for GRUB:
  Boot Ubuntu and open a terminal by pressing Ctrl+Alt+T then type
  sudo nano /etc/default/grub
  Find the line that starts GRUB_CMDLINE_LINUX_DEFAULT=

  This needs to be changed to include intel_idle.max_cstate=1
  So after your edit it reads something like 
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1"
  quiet and splash are default parameters for Ubuntu Desktop - no need to change them, or any other pre-existing parameters

  Now save the file by pressing ctrl+o then enter and exit by pressing ctrl+x
  Now run

  sudo update-grub
  Then reboot.


Will reboot now and see how it goes thanks for the help!

JP

---

