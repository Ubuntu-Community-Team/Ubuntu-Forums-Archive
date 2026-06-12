---
title: "Scull module and I/O devices"
date: 2009-06-08
forum: Programming Talk
---

### Post by HolmesTech on 2009-06-08
Hi, 

I need help because I am having the weirdest problem ever. Im currently taking a class at university call device programming, which consists of programming small device modules for linux. I had to write a char driver (scull), where I had to write a module that would act like a FIFO Pipe which would hold a maximum of 1024 characters in a circular buffer. 

Last thing I was doing was working on that, which I never really managed to achieve, I maybe spent a few hours on it. When I rebooted my machine, (DELL m1330 with ubuntu 9.04 64 bits), keyboard and mouse werent working. USB mouse and use keyboard also. Ubuntu loads normaly, I get to the user screen, the cursor is blinking, but all input devices dont work. 

I figured it might be a hardware problem, but my keyboard works fine in recovery mode and my mouse works when I load ubuntu from the CD, so i know my hardware is fine. 

Is it possible I messed up my kernel or my drivers somehow? I know everything would get unloaded and removed when I would reboot (like a rmmod). Is there a log file that would give me details of the error or is there a way to reinstall drivers without logging in ubuntu..

The commands i used mostly in my module were copy_to_user, copy_from_user, memset, put_user... stuff like that. Any help would be greatly appreciated.

Thanks,
Rafael

---

