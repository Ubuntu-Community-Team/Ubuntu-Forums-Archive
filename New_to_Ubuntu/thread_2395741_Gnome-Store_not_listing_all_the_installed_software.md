---
title: "Gnome-Store not listing all the installed software"
date: 2018-07-06
forum: New to Ubuntu
---

### Post by imgeka on 2018-07-06
For the last month or so, my Gnome-Store is listing only 5-6 of the installed software (OS version: Xubuntu 16.04). Purging and reinstalling the store made no difference. There seems to be a bug here; is the problem being looked into?

---

### Post by PaulW2U on 2018-07-06
The list of outstanding bugs for the Software Center can be found [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bugs?orderby=-id&start=0").

I couldn't see anything that specifically matched the information that you gave us but please take a closer look.

Have you tried to refresh your repository information outside of the Software Center? With the Software Center closed, in a terminal run:
```
sudo apt-get update
sudo apt upgrade

```
Does that change the applications that the Software Center now shows?

---

### Post by imgeka on 2018-07-06
Hi, a few days ago I did implement the solution suggested by you, but it didn't make any difference at all.

---

### Post by monkeybrain20122 on 2018-07-08
The gnome store doesn't even list all software available ( only a small fraction actually). It is a buggy and useless piece of junk as far as I am concerned. To get a much more featureful and functional package manager (though without the nice pictures) install synaptic

```
sudo apt install synaptic
```

From synaptic you can browse by category, origin and status, it is very easy to use after you take 5 minutes to get familiar with the gui (sudo apt update = clicking "reload" in synaptic)

Then you can forget about the store.

P.S maybe xubuntu already comes with synaptic by default. Check your menu for installed applications. Not sure why a supposedly lightweight distro would want the gnome store instead.

---

### Post by rickdiaz on 2018-07-10
[COLOR=#111111][FONT=Ubuntu]This is a known [/FONT][/COLOR][bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1589970")[COLOR=#111111][FONT=Ubuntu], have to wait until it is resolved.[/FONT][/COLOR]

---

### Post by imgeka on 2018-10-18
Bumping this thread to underline the fact that this matter has not resolved since 2016.

---

### Post by monkeybrain20122 on 2018-10-18
> **imgeka said:**
> Bumping this thread to underline the fact that this matter has not resolved since 2016.

Already told you to use synaptic.

---

### Post by imgeka on 2018-10-19
I do use Synaptic, but I would like to see a properly functioning gnome store as I find it more app-store like. I find it disconcerting that they cannot resolve a issue that was addressed to them back in 2016.

---

### Post by monkeybrain20122 on 2018-10-20
> **imgeka said:**
> I do use Synaptic, but I would like to see a properly functioning gnome store as I find it more app-store like. I find it disconcerting that they cannot resolve a issue that was addressed to them back in 2016.

It seems to be intended. [https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1553211](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1553211)

---

### Post by coffeecat on 2018-10-20
> **imgeka said:**
> Bumping this thread to underline the fact that this matter has not resolved since 2016.

Which will make absolutely no difference at all. This is a forum of end-users, none of whom are employed by Canonical, forum staff included. We have no way of influencing how quickly or whether launchpad bugs are resolved.

---

### Post by boqsc on 2018-10-20
If you are using latest [Gnome Software]("https://wiki.gnome.org/Apps/Software") version, then you can try to [apply an issue in the Gnome Community Gitlab]("https://gitlab.gnome.org/GNOME/gnome-software/issues/new?issue%5Bassignee_id%5D=&issue%5Bmilestone_id%5D="). 
It's their new platform, kind of had some success while applying it and receiving the fix.
It all depends on the developer's mood.

---

