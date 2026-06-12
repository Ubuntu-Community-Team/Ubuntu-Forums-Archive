---
title: "KDE applications in Ubuntu"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by gerben1 on 2008-05-08
Hi,

I am using a normal install of the normal Ubuntu, so with a Gnome desktop. I use two KDE applications, namely Kate and K3b. 

Now and then I see a Knotify window pop-up on the lower Gmone menu bar, I guess Knotify was installed because it is necessary for either Kate or K3b. When I look in the system monitor is see four KDE processes, namely these:
- kdeinit
- kded
- klauncher
- knotify

Now, my question is do these processes need to be loaded always, even when I am not using Kate or K3b?

I would especially like to not have Knotify loaded, as it occasionally appears to come up out of nothing, stalling my system for a few seconds before it goes back to sleep again, seemingly not having done anything.

---

### Post by Joeb454 on 2008-05-08
I would assume they are intended to be there. You may try closing them from the System Monitor, though I'm unsure what that would do.

You'll find that they are probably sleeping & not taking up much system resources (a small amount of RAM perhaps)

---

### Post by gerben1 on 2008-05-08
> **Joeb454 said:**
> I would assume they are intended to be there. You may try closing them from the System Monitor, though I'm unsure what that would do.

You'll find that they are probably sleeping & not taking up much system resources (a small amount of RAM perhaps)

Yes, they are no big problem at all, they are indeed sleeping most of the time and they only take about 3MB RAM together. It is just that Knotify is a little annoying.

---

### Post by Joeb454 on 2008-05-08
You say Knotify pops up a lot for you? I've never noticed it. It does occasionally if I click the wrong thing in Amarok and it can't start Knotify ;)

---

### Post by gerben1 on 2008-05-08
Well, not very often, but I see it a few times everyday when I am working on this laptop. No big deal, but I'd rather not have it.

Apparently Knotify is a process in on the KDE desktop that you can configure to Notify you about certain events, but I did not configure any events that I want to be notified about, and still it wants to notify me now and then, not that I really get a notification about anything, it just wakes up for a while and then goes back to sleep.

---

### Post by Joeb454 on 2008-05-08
You'll have to see if you can launch some sort of Knotify settings manager or something. I don't think it would be installed into a Gnome environment unless you did so explicitly. I'll have a look

---

