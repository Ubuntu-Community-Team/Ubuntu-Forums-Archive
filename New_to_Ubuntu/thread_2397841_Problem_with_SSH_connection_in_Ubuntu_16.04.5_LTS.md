---
title: "Problem with SSH connection in Ubuntu 16.04.5 LTS"
date: 2018-08-04
forum: New to Ubuntu
---

### Post by svj2 on 2018-08-04
Hello,

I am using Ubuntu 16.04.5 LTS (with ROS Kinetic) in my laptop. I am able to establish an SSH connection between my laptop and a Raspberry Pi through WiFi. But when I try to execute something (node, launch file)  in the RPi, it is not running (nothing happens, until I press Ctrl + C). When I press Ctrl +C , it shows **"ERROR: unable to contact ROS master at [[http://localhost_ip_address:11311]](http://localhost_ip_address:11311])****The traceback for the exception was written to the log file."**, eventhough **roscore** is already running. 
I have rechecked my ~/.bashrc and made sure that the IP Addresses of host and Master are correctly exported.  Also, when I ran **rosnode list **in my laptop, it shows only **/rosout.**

Using other laptops, I am able to successfully establish serial connection and run programs in the RPi. Only with my laptop I have this problem. I have also tried with different WiFi connection.

Could someone help me with this regard? Could this be a problem with Ubuntu or ROS?

Thanks in advance.

---

### Post by TheFu on 2018-08-05
Run ssh in verbose mode.
Also, run the sshd on the pi in debug mode. Check the log files.

But I've never heard of ROS Kinetic.  If you can manually connect via ssh, then I suspect the issue is with the startup for the other application or some misunderstanding.

What does a serial connection have to do with ssh? Those are completely different physical and logical methods.

---

