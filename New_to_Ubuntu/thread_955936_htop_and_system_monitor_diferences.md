---
title: "htop and system monitor diferences"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by duruttye on 2008-10-22
Hello!

I've been meaning to ask this a long time ago.

I have added to the top panel the system monitor thing and it doesn't show the cpu according to htop, or top, or the regular system monitor.
Although when I run htop, the CPU usage is high, but it doesn't show what's using it up, so does the system monitor.

I will try to attach a screenshot.
Look for the lines at the top of the terminal and the list, which is sorted by cpu usage.

What is the difference and why is there any difference? I thought the htop, top, and the system monitor (all precesses activated) should show all processes there are.

Thanx guys!

Using a dell inspiron 1501 and ubuntu 8.10

---

### Post by duruttye on 2008-10-24
BUMP:guitar:

---

### Post by duruttye on 2008-10-29
having the same problem since then...

no ideas?

---

### Post by junglism on 2008-11-06
Yep I've been having exactly the same problem.. 
discrepancy between what's shown on the graph and the cpu usage that's show in the process list below.

most of the time i think it's when i've been using firefox or vmware workstation. 

can anybody help?

---

### Post by duruttye on 2008-11-18
Well, after all, this isn't such a big thing, I was just wondering what's up with that. It can be annoying some times.

It looks like we are there are two people bothered by this.

I keep the thread opened :)

---

### Post by rubbsdecvik on 2008-11-18
I'm not an expert, and I might be wrong, but I think the difference between htop and the system monitor application is that some software packages like firefox actually spawn several processes.  htop and top will display each of these processes as individual processes (some of them will even be named the same).

System Monitor will attempt to "group" all the processes together.  IE all Firefox processes are shown as one. (Edit: I meant i.e. as in "For example" not Internet Explorer)

That's why things like memory usage in Linux can be hard to monitor, because some packages use the same libraries and the memory usage is sometime counted twice.

---

