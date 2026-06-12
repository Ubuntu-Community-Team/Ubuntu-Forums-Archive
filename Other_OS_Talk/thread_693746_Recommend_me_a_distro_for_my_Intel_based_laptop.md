---
title: "Recommend me a distro for my Intel based laptop"
date: 2008-02-11
forum: Other OS Talk
---

### Post by Zdravko on 2008-02-11
Hi there!
Since I am disappointed by the hardware instability of Ubuntu, I'd like to give another distro a try.
What I am searching for:[LIST=1]
[*]Good to very good hardware support - intel 965gm, x3100 video card, etc.
[*]It must fit in 11 GB partition, since this is what I have as empty space, after I wipe hardy.
[*]GTK environment (GNOME resp.) would be preffered since I plan to program in gtkmm, but not obligatory!
[*]wireless, sound, multimedia - not important!
[*]Frequent upgrade (like Ubuntu!)[/LIST]What I don't want:[LIST=1]
[*]ArchLinux - too complicated to set up.
[*]Gentoo - even more.
[*]Ubuntu - it is simply refusing to understand that Compiz is not working with my intel hardware.[/LIST]I'd appreciate any of your suggestions.

---

### Post by LaRoza on 2008-02-11
Wow, a tall order here.

Try Fedora, openSuSE, or another *buntu like OS.

Pardus is very good with hardware also.

---

### Post by Zdravko on 2008-02-11
I can't try them all. I would choose one and just try to use it forever. What would be most suitable for me? Note that I am not a professional Linux user.

---

### Post by smartboyathome on 2008-02-11
Just to let you know, I don't think Compiz will work with your video card, as intel cards are crap with Compiz.

---

### Post by PmDematagoda on 2008-02-11
Try Fedora or OpenSUSE, I personally find them both to be very good.

---

### Post by LaRoza on 2008-02-11
> **Zdravko said:**
> I can't try them all. I would choose one and just try to use it forever. What would be most suitable for me? Note that I am not a professional Linux user.

Well, of those, I would say OpenSuSE or Pardus. Read up on both.

I am not a professional either, in fact, I have been using computers for around a year.

What is suitable for you seems to be an OEM install of Windows.

---

### Post by Zdravko on 2008-02-11
> **smartboyathome said:**
> Just to let you know, I don't think Compiz will work with your video card, as intel cards are crap with Compiz.
You must be joking?

> **PmDematagoda said:**
> Try Fedora or OpenSUSE, I personally find them to be very good.
Hmm, Fedora sounds good to me. Does it recognize the mentioned hardware properly?

---

### Post by LaRoza on 2008-02-11
> **smartboyathome said:**
> Just to let you know, I don't think Compiz will work with your video card, as intel cards are crap with Compiz.

I use Intel video only, and Compiz works fine. I am not saying everyone will have this experience with every Intel video, but they are good enough for me.

---

### Post by LaRoza on 2008-02-11
> **Zdravko said:**
> 
Hmm, Fedora sounds good to me. Does it recognize the mentioned hardware properly?

Try it.

I never had hardware problems with Ubuntu, in fact, it works perfectly on my new laptop. Since you say you have hardware problems with Ubuntu, it means one of us is not telling the truth, or (more likely) the wide range of hardware makes our experiences different.

---

### Post by cookieofdoom on 2008-02-11
I would say Fedora might be best. I don't know much about it's hardware support for your specific machine, but it's more designed around gnome than OpenSUSE. If you wanted to give KDE a try, I'd go with OpenSUSE.

Fedora has the 6 month release cycle from what I understand now, too. It's better with sound than Ubuntu because of the system it uses, when I tried it I also had no complaints about it's hardware support. I also much preferred it's method of installing applications. I had a lot of dependency issues with OpenSUSE.

I don't know anything about Pardus, sorry.

---

### Post by LaRoza on 2008-02-11
[http://www.pardus.org.tr/eng/](http://www.pardus.org.tr/eng/)

Pardus is a KDE distro, but it has good hardware support, some say it has the best, but I haven't tried it on a wide ranger of machines.

---

### Post by Zdravko on 2008-02-11
The latter. The x3100 is not blacklisted anymore, but the OpenGl performance (see my recent thread about the screenshot in glxgears) is far from what I need. I need something comparable in size to Ubuntu. Something that will just work, instead of forcing me to change a couple of scripts...

---

### Post by Zdravko on 2008-02-11
I will research Fedora for a while.

---

### Post by smartboyathome on 2008-02-11
My opinions on Intel and Compiz are from my experience and the fact that when I was looking for my new computer, you had to do stuff to get it working with compiz

---

### Post by LaRoza on 2008-02-11
> **Zdravko said:**
> The latter. The x3100 is not blacklisted anymore, but the OpenGl performance (see my recent thread about the screenshot in glxgears) is far from what I need. I need something comparable in size to Ubuntu. Something that will just work, instead of forcing me to change a couple of scripts...

Try waiting until Hardy comes out, if you know how to fix it (as you seemed to imply) you will only have to do it once.

---

### Post by LaRoza on 2008-02-11
> **smartboyathome said:**
> My opinions on Intel and Compiz are from my experience and the fact that when I was looking for my new computer, you had to do stuff to get it working with compiz

Intel video is the only one supported out of the box (Compiz works on a live disk). I don't know about all Intel cards though.

---

### Post by notwen on 2008-02-11
The X3100 chipset is blacklisted by Compiz. =]  I had to acknowledge this early on w/ my new Inspiron 1420n.  So I'm guessing using metacity is not an option?  If not, you could try this workaround:

```
sudo gedit /etc/xdg/compiz/compiz-manager
```

Then add this line to it and save.

```
SKIP_CHECKS="yes"
```

Restart GDM(Alt+Ctrl+Del)

Doing this kills video playback until you change your video playback to use X.  Maybe this will help you stick w/ Ubuntu, otherwise happy distro hunting. =]

---

### Post by Zdravko on 2008-02-11
Yeah, nice work around. It worked for me, btw.
Now, let's see what can Fedora offer to me...

---

### Post by Zdravko on 2008-02-11
I am downloading it... I will start a new thread in the Fedore subforum here. Or is there a similar nice forum for Fedora?

---

### Post by LaRoza on 2008-02-11
> **Zdravko said:**
> I am downloading it... I will start a new thread in the Fedore subforum here. Or is there a similar nice forum for Fedora?

Try it first, then post any problems you have in the Fedora forum here. No point in joining another forum for a distro you might not like.

---

### Post by Changturkey on 2008-02-11
+1 for Pardus.

---

### Post by kamaboko on 2008-02-11
> **Zdravko said:**
> I can't try them all. I would choose one and just try to use it forever..

LOL.  Is that even possible?  I think I've messed with at least 10 different distros.

---

### Post by Zdravko on 2008-02-12
> **LaRoza said:**
> Try it first, then post any problems you have in the Fedora forum here. No point in joining another forum for a distro you might not like.
Ops. I already registered there. Anyway. I am downloading Fedora now. I read the install guide. Looks good to me. I hope that it works for me.

---

