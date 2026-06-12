---
title: "BOINC Show Graphics not working"
date: 2018-11-21
forum: New to Ubuntu
---

### Post by marathon2 on 2018-11-21
I've been running BOINC for years. I used the BOINC Manager "advanced view" setting, which has "Tasks" tab. If a task in in the "Running" state,  I am supposed to be able to select it, and then click on "Show Graphics." This is supposed to result in a new window opening, which shows the graphics for the selected task. 

Before switching to Kubuntu, I was using OpenSuSE. On about 1/2 the versions of OpenSuSE, the "show graphics" feature didn't work. This is now happening on Kubuntu 18.04.1. It also  happened on Kubuntu 17.10. 

When I click on "Show Graphics", for a fraction of a second, a rectangle might appear on the screen. But, if it does, promptly disappears. I believe the window is created, but is very quickly closed due to some error. When no rectangle appears, it might be the case that it does appear and disappear faster than the eye can see. 

I am currently using BOINC 7.9.3, installed using Synaptic package manager.

What I would like to complain about is the port of the BOINC manager to Ubuntu made some changes that  make it  harder to resolve this issue than it was on OpenSuSE. When I had this problem with the other distro, I could use Konsole to start the BOINC task manager. Then, when I clicked on "Show Graphics" in the task manager, I could look at the Konsole window and see some error messages. With KUbuntu, 

I hope those who port the BOINC software to Ubuntu will take this into consideration.

In the meantime, how can I get "Show Graphics" in BOINC working?

---

### Post by marathon2 on 2018-11-23
I found a partial solution. It looks like I need to add my user to a boinc group. That allows graphics to work for Seti@home and several, but not all, World Community Grid projects.

---

### Post by wildmanne39 on 2018-11-23
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by marathon2 on 2018-12-16
I found installing another package allowed me to get the "Show Graphics" feature working for the rest of the World Community Grid projects. Everything is working now.

But, I hope developers who port BOINC to Ubuntu will make it easier to solve this type of problem in the future.

---

### Post by oldos2er on 2018-12-16
> **marathon2 said:**
> I found installing another package allowed me to get the "Show Graphics" feature working 

Would you share which package solved this for you?

---

### Post by marathon2 on 2018-12-18
I forgot to record that. But, looking at my Synaptic history, I think it was [COLOR=#0000ff][FONT=courier new]libjpeg62[/FONT][/COLOR] .

It may be useful to note how I found out what to do:

I opened the menu or destop icon for the BOINC manager to find the working directory is[COLOR=#0000ff][FONT=courier new] /var/lib/boinc-client[/FONT][/COLOR] 

Opening Dolphin, I opened that directory and browsed to [FONT=courier new][COLOR=#0000ff]/var/lib/boinc-client/projects/www.worldcommunitygrid.org/ 

[/COLOR][/FONT]Once there, I sorted the files by "type".  For each executable, I ran  [COLOR=#0000ff][FONT=courier new]ldd <filename> [/FONT][/COLOR]

---

### Post by oldos2er on 2018-12-18
Thank you, I'll try this later today. I've been unsuccessful getting boinc graphics to work for a long time.

Later that same day:

Well I'll be darned, it worked! @marathon2, would you please mark this thread 'Solved' under Thread Tools at the top of the page? It'll help others like me know there is a solution to this long-running problem. Thank you.

Edit: Marked this thread solved.

---

