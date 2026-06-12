---
title: "run a script when fw drive is mounted??"
date: 2010-09-23
forum: Programming Talk
---

### Post by bluerabbit4210 on 2010-09-23
Hi all, quick question that google has been unwilling to answer for me.  :/

How do I run a bash script automatically when I mount an external hdd?  to clarify, not just any hdd, but a specific device.  I suppose I could set a cron job to poll the mountpoint, but it seems like there should be a better way to do it.  basically I want a backup script that will run on my headless server when I plug in my firewire hdd.  Any tips, links, etc?

Thanks in advance,
br

---

### Post by SaintDanBert on 2010-09-23
Someone once said that you need to understand how to ask the right questions? (grin)

What you are looking for are "udev rules".  **Udev** (I think it stands for usb devices) is the system component that responds when you connect external parts.  There are distro specific wrinkles and there are even wrinkles within a distro family from one edition to another.
For example, Ubuntu Jaunty (v9.04) is radically different than Ubuntu Lucid (v10.04 LTS).

Here is a Google(tm) starter search [http://www.google.com/search?num=30&hl=en&newwindow=1&safe=off&gbv=2&biw=781&bih=457&q=linux+writing+%22udev+rules%22&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.com/search?num=30&hl=en&newwindow=1&safe=off&gbv=2&biw=781&bih=457&q=linux+writing+%22udev+rules%22&aq=f&aqi=&aql=&oq=&gs_rfai=). You will find many postings about udev and external drives. 

Bonne chance,
~~~ 0;-Dan

---

### Post by bluerabbit4210 on 2010-09-23
yup, that looks like the question I was looking for!  cheers!  :)

---

### Post by SaintDanBert on 2010-09-23
remember to mark your question solved...
... and share your results with the forum.

If all you do is find posting(s) that does exactly what you want to do, add a link(s) to your thread.

de rien,
~~~ 0;-Dan

---

