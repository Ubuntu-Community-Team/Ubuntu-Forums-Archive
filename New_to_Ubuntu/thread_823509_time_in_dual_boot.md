---
title: "time in dual boot"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by vamsibethapudy on 2008-06-09
I have a dualboot hardy & xp {sp3} laptop.
the probem is that the time in these two os's never get tallied.
If I change the time in hardy the time in xp gets changed too to something wrong.If i change it in xp to the right time then ubuntu time is wrong. I searched the forums for the solution but they all say about some UTC.Can anyone explain to me what that is all about??
& can anyone tell me how an offline computer keep time even if its shut down??

---

### Post by nebu on 2008-06-09
> **vamsibethapudy said:**
> I have a dualboot hardy & xp {sp3} laptop.
the probem is that the time in these two os's never get tallied.
If I change the time in hardy the time in xp gets changed too to something wrong.If i change it in xp to the right time then ubuntu time is wrong. I searched the forums for the solution but they all say about some UTC.Can anyone explain to me what that is all about??
& can anyone tell me how an offline computer keep time even if its shut down??



your motherboard has a cmos where it saves current time.... this cmos runs of the computers power supply when the pc is on.... however when it is not.... a battery which is fixed on the mother board powers up the clock.... hence your computer is able to show u accurate time even after your pc has been switched off....

if u are loosing the current time everytime u are restarting.... u may need to replace your cmos battery....

---

### Post by RSingh on 2008-06-09
Actually this was happening with me also and my system is less then a year old. It turns out when time is edited in XP it, it changes your system time somehow and this was affecting my Ubuntu's time if your ubuntu's time is set to manual and your timezone is set to be +/- something GMT. It turns out that if your time in bios is set as for example 8 PM then if you install a OS with your timezone setting as 2+ GMT, the clock in the OS automatically adds 2hrs to the system time and shows it as 10 PM. So what I did was I enabled the time in ubuntu to be automatically synchronized with online servers by editing the time settings so this removed the hassle by removing the dependency on my system time.

---

