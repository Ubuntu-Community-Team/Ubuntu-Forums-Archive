---
title: "Flash in Firefox 3.0"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Lao_Tzu on 2008-06-23
I'm running Ubuntu Hardy Heron and Firefox 3.0. I've struggled with all sorts of solutions for my Flash player during Firefox 3's beta phases, never with full success, and I think the various 'fixes' have left my /usr/lib/ section a complete mess as it pertains to flash.

My friend is using exactly the same software and hardware setup as me (i.e. Hardy and Firefox 3) but his is working perfectly! I would like to get mine running perfectly too, and if anyone could help I would be most appreciative. This may prove to be a long and arduous process, however. Do hide your rusty razorblades.

Is there a way to completely remove everything to do with flash from my system and start again from scratch, without hurting anything else?

---

### Post by stchman on 2008-06-23
> **Lao_Tzu said:**
> I'm running Ubuntu Hardy Heron and Firefox 3.0. I've struggled with all sorts of solutions for my Flash player during Firefox 3's beta phases, never with full success, and I think the various 'fixes' have left my /usr/lib/ section a complete mess as it pertains to flash.

My friend is using exactly the same software and hardware setup as me (i.e. Hardy and Firefox 3) but his is working perfectly! I would like to get mine running perfectly too, and if anyone could help I would be most appreciative. This may prove to be a long and arduous process, however. Do hide your rusty razorblades.

Is there a way to completely remove everything to do with flash from my system and start again from scratch, without hurting anything else?

All you need to do is install the flashplugin-nonfree package.

```
sudo apt-get install flashplugin-nonfree
```

I watch YouTube all the time no problems even running 64 bit Hardy.

Before you do that go into synaptic and type Flasha nd remove any other Flash packages.

Also delete any Flash in your ~/.mozilla/plugins folder.

---

### Post by Lao_Tzu on 2008-06-23
Thanks, stchman. I've done that a couple of times, but I am told that flashplugin-nonfree is already the newest version.

The video on YouTube will play, but there's no sound: it seems that's the only problem at present. The same is true of Starcraft2.com (a very flash-heavy site).

---

### Post by Lao_Tzu on 2008-06-23
Scratch that! That worked.

Many thanks, stchman.

---

### Post by stchman on 2008-06-24
> **Lao_Tzu said:**
> Scratch that! That worked.

Many thanks, stchman.

Glad to be of help.

---

