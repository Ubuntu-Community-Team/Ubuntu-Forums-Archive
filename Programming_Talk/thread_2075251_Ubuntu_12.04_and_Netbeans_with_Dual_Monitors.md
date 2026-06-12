---
title: "Ubuntu 12.04 and Netbeans with Dual Monitors"
date: 2012-10-23
forum: Programming Talk
---

### Post by LumbeeNDN on 2012-10-23
I have installed netbeans 7.0.1. It runs find on my laptop if I don't have an external monitor installed. But with an external monitor, the application starts, and its like its open (shows up in the laucher), but it ain't on the screen. Whats even weirder if I do ctrl+alt+arrow keys, you can see the IDE in the little 4 spare icon in the middle of the screen. Uncle Google found a bunch of threads about dual monitor issues with Netbeans, but nothing that is similar to what I am seeing.

---

### Post by dwhitney67 on 2012-10-23
I can run Netbeans 7.1 with my Kubuntu 12.04 system using an external monitor.  I do not use a dual-monitor since I tend to keep my laptop's display closed.

I suspect your system issues are due to either a bad installation of Netbeans (perhaps consider upgrading), or you are using a version of Java (perhaps OpenJDK) that Netbeans may not be happy with.

If you decide to upgrade Netbeans, it might be worthwhile to remove the folder in your home directory called .netbeans.

---

### Post by LumbeeNDN on 2012-10-23
...thanx for the response Ddub.

I uninstalled 7.01 (which is what was in the repo) and install 7.2.1, and got the same result.

However I did fix my problem by booting up with both monitors, and starting Netbeans. Again I was back where I started where Netbeans was open, but I could not see it. So I went into the display setup and disabled my external monitor. When my laptop screen refreshed, I could see Netbeans. I then resized the netbeans when, and made it about half the size, and then re-enabled my 2nd monitor. All seems find now, I have closed and restarted Netbeans and it opens OK. I think what was Netbeans was trying to open on my second monitor, and the window was to big to fit based on the monitor resolution.

---

