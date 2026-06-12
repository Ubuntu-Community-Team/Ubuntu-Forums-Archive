---
title: "Purge pcmanfm - lubuntu-core*"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-03-16
Will I damage my system if I purge PCManFM?

I searched the titles in the forum for "purge lubuntu-core" but nothing came up.

When I run the command 
```
sudo apt-get purge pcmanfm
```

I get the following warnings. I'm not sure what the * means either.

```
The following packages will be REMOVED:
  lubuntu-core* lubuntu-default-settings* lubuntu-desktop* lxde-core* pcmanfm*
```

Somehow I'm a bit nervous if core packages are being removed.

I've installed Dolphin as a file manager and want to purge PCManFM because it's too slow.

Any help would be greatly appreciated.

---

### Post by Kevin McCready on 2012-03-16
I've been searching the internet since I posted, but no luck. I'm worried I will I damage my Lubuntu system if I do
```
sudo apt-get purge pcmanfm
```

---

### Post by Kevin McCready on 2012-03-16
3 Hours later and 96 views.
Does anyone know the answer?
I suspect from my reading and experiments in the last few hours that PCManFM is integral to the Lubuntu installation and I can't get rid of it.
I'm sure other people have had the same problem.

---

### Post by Peripheral Visionary on 2012-03-16
PCManFM manages the desktop in Lubuntu. You can certainly use any other file manager you wish, but leave PCManFM installed, as it manages the desktop.

That said, you don't *have* to let PCManFM manage the desktop. But for a lot of folks it's simpler to leave it that way.

It's funny... I use Xubuntu and absolutely love the PCManFM file manager. For me it's much simpler and lighter than Thunar, the Xfce file manager.  But I don't *purge* Thunar, despite not using it, since I think other things in Xfce kind of depend on Thunar.

---

### Post by Kevin McCready on 2012-03-17
thanks for your answer. Much appreciated. The problem is that whenever I put in a USB stick the ONLY option is PCManFM to open it. And lots of other file manager problems arise too. I'd rather just make Dolphin my default.

---

### Post by ankspo71 on 2012-03-17
Hi,
I agree, removing pcmanfm could harm Lubuntu.

Edit: Ignore the following because I was able to try this and it doesn't work in Lubuntu or LXDE sessions:

I am away from Lubuntu at the moment, but I happen to be using Linux so I see that these certain files exist. I can't guarantee this will work while inserting usb drives, but it should help for the most part. Search for a file called "defaults.list". These are the system wide files that control which applications handle each file association (mime type).

```

sudo updatedb
locate defaults.list
```

You are going to find a few of these files, and in at least one of them (probably the one in the /etc/xdg/lubuntu? directory), you are bound to see an entry called:
x-directory/normal=pcmanfm.desktop

Change it to the appropriate *.desktop file, probably "dolphin.desktop".
x-directory/normal=dolphin.desktop

**If you would rather not do this system wide for all users**, you could try adding the line "x-directory/normal=pcmanfm.desktop" to
~/.local/share/applications/mimeapps.list

Reference:
[http://www.libre-software.net/change-the-default-application-linux-mint-ubuntu](http://www.libre-software.net/change-the-default-application-linux-mint-ubuntu)

Hope this helps.

---

### Post by Kevin McCready on 2012-03-18
Hey thanks for that, but it didn't quite work. PCManFM still comes up as the default. I'll just have to live with it or else go for another flavour of ubuntu.

And unfortunately before I got your post I did the purge thing and it made my whole system unuseable so I had to reinstall. Sigh.

So  BIG warning to anyone else reading this post. DO NOT try to purge PCManFM from Lubuntu.

---

### Post by Zill on 2012-03-18
> **Kevin McCready said:**
> ... I'd rather just make Dolphin my default.
As you presumably installed Lubuntu because you wanted/needed a "lighter" system, I suggest that installing Dolphin may be counter-productive.  Although I no longer use KDE, my experience suggests that installing Dolphin will drag in a large number of KDE dependencies, making your system no longer light but bloated!

As already suggested, I would retain PCManFM, even if you choose not to use it as your primary file manager.  You may find that the problems you have experienced can be resolved if you post details on these forums.

You may also like to consider installing other file managers, such as [Thunar]("http://thunar.xfce.org/") or [emelFM2]("http://emelfm2.net/").  However, I would check to ensure that too many dependencies are not also being installed. ;-)

---

### Post by Zill on 2012-03-18
> **Kevin McCready said:**
> ...The problem is that whenever I put in a USB stick the ONLY option is PCManFM to open it...
I am curious to know exactly which other options you would like to see?
> **Kevin McCready said:**
> ...And lots of other file manager problems arise too. I'd rather just make Dolphin my default.
Similarly, if you advise which problems you have seen then we may be able to offer solutions.

Having said that, it may be best to start a new thread (or threads!) with a more appropriate title(s), then add a quick link here to cross-reference to the new thread.

---

