---
title: "Downgrading back to Gutsy"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by shacamin on 2008-05-08
So my computer apparently can't handle Hardy.

Is there some way to downgrade back to Gutsy without wiping my drive? For instance, faking the computer into thinking it's upgrading to the next version, when it's really a version down?

Anything will work, but Hardy is killing my CPU.

---

### Post by bumanie on 2008-05-08
Unfortunately, the only way to downgrade is to reinstall gutsy. If you you could detail more than hardy is killing my cpu, someone may be able to help you sort out the issues. Include as much information as possible ie exactly what's happening, system specs. etc.

---

### Post by macaholic on 2008-05-08
> **bumanie said:**
> If you you could detail more than hardy is killing my cpu, someone may be able to help you sort out the issues. Include as much information as possible ie exactly what's happening, system specs. etc.
I think what he is basically saying is that his computer in general can't handle hardy. I find this somewhat hard to believe since I was under the impression that hardy and gutsy required relatively the same resources. You could try disabling desktop effects, that should free up resources.

---

### Post by shacamin on 2008-05-08
Well, I did an apt-get upgrade install of Hardy. The first issue I noticed was that most of my Firefox extensions didn't work with 3b5. So, I spent a lot of my time reinstalling 2.0.0.14. And now that works fine. However, after I stopped concentrating on Firefox, I noticed my CPU was at a constant 100%. Every once in a while it would dip down to a normal level, but then it would just rise right back up again.

I did a ps -ax in terminal, and no large programs were running. I uninstalled some programs (evolution, some games) and did a sudo apt-get autoremove. But still, even now, my CPU is up really high and I can't get it to come down, even with a restart. I'm on my laptop right now, so it's not a problem, but I just really need to get that fixed.

---

### Post by Sef on 2008-05-08
> I find this somewhat hard to believe since I was under the impression that hardy and gutsy required relatively the same resources.

They do.  Sometimes certain packages have either been upgraded or added, and those can cause problems.

---

### Post by shacamin on 2008-05-09
> **macaholic said:**
> You could try disabling desktop effects, that should free up resources.

That never worked for me in the first place. I've always had them disabled.

---

### Post by mpince on 2008-05-09
> **shacamin said:**
> However, after I stopped concentrating on Firefox, I noticed my CPU was at a constant 100%. Every once in a while it would dip down to a normal level, but then it would just rise right back up again.


If you are using System Monitor for those CPU usage readings. I think there is a bug in it that is giving inflated CPU readings. Notice under the processes tab that the utility itself draws 10% CPU use.

You can get a more accurate CPU reading by typing "top" in terminal.

---

### Post by shacamin on 2008-05-09
> **mpince said:**
> If you are using System Monitor for those CPU usage readings. I think there is a bug in it that is giving inflated CPU readings. Notice under the processes tab that the utility itself draws 10% CPU use.

You can get a more accurate CPU reading by typing "top" in terminal.

I'll try that, but it's not just the reading. My computer is drastically slower. It takes forever for anything to load.

---

### Post by corevette on 2008-05-09
you could always install a lighter weight window manager like fluxbox, or many others
```
sudo apt-get install fluxbox
```
and then you just go back to login window and switch sessions to fluxbox

---

### Post by hyper_ch on 2008-05-09
```

sudo apt-get install htop

```

```

htop

```

and check what process is using so much cpu

As for firefox, most extensions can easily be made running on v3 with the Nightly Builder Tools addon.

---

### Post by shacamin on 2008-05-10
I got htop, and it says the same thing the system manager said. There is no process running that should be taking up that much space.

I'm perplexed.

Edit:

So I just did a regular top check, and found out that there was a process running on the root user that was taking up between 45 and 62% of the CPU. I killed it and now things seem to be fine. I can't really tell for sure because I'm running some updates, but I think it should be fine.

Thank you!

---

