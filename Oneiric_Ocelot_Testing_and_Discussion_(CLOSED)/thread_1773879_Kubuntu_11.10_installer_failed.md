---
title: "Kubuntu 11.10 installer failed"
date: 2011-06-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by floydsp on 2011-06-02
Traceback (most recent call last):
  File "/usr/lib/ubiquity/plugins/ubi-prepare.py", line 242, in check_returncode
    if not super(PageKde, self).check_returncode(args):
  File "/usr/lib/ubiquity/ubiquity/plugin.py", line 44, in wrapper
    return target(self, *args, **kwargs)
  File "/usr/lib/ubiquity/plugins/ubi-prepare.py", line 93, in check_returncode
    self.prepare_download_updates.set_sensitive(state)
AttributeError: 'QCheckBox' object has no attribute 'set_sensitive'

I get this when it says installer failed..using Live cd and it works just fine

floydsp

---

### Post by kevpan815 on 2011-06-02
Since you are new here I would just like 2 let you know that most of the Ubuntu Development Staff do NOT usually read these Forums, so it is usually recommended that in addition 2 posting your problem here, that you file a Bug Report as well. Just FYI.

P.S. Welcome to the Party and have fun Testing!

---

### Post by PaulW2U on 2011-06-02
> **floydsp said:**
> Traceback (most recent call last):
  File "/usr/lib/ubiquity/plugins/ubi-prepare.py", line 242, in check_returncode
    if not super(PageKde, self).check_returncode(args):
  File "/usr/lib/ubiquity/ubiquity/plugin.py", line 44, in wrapper
    return target(self, *args, **kwargs)
  File "/usr/lib/ubiquity/plugins/ubi-prepare.py", line 93, in check_returncode
    self.prepare_download_updates.set_sensitive(state)
AttributeError: 'QCheckBox' object has no attribute 'set_sensitive'

I get this when it says installer failed..using Live cd and it works just fine

floydsp

That bug has already been reported - [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/791446](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/791446)

---

### Post by kevpan815 on 2011-06-02
> **PaulW2U said:**
> That bug has already been reported - [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/791446](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/791446)

So then what he needs 2 do is click on your hyperlink (which will take him 2 the bug report it self) sign in to the bug reporting mechanism and subscribe to the existing bug report.

---

### Post by floydsp on 2011-06-02
I am here so you can talk to me not he do this or that.
I did try and subscribe but did register so maybe I can file a report next time....Thanks all:P

floydsp

---

### Post by kansasnoob on 2011-06-02
> **floydsp said:**
> **I am here so you can talk to me not he do this or that.**
I did try and subscribe but did register so maybe I can file a report next time....Thanks all:P

floydsp

Rather touchy aren't we?

Everything we post here is public so it's hardly as though anyone was disrespecting you or talking behind your back ;)

---

### Post by VanR on 2011-06-02
Lol!

---

### Post by xebian on 2011-06-02
Not worth the trouble as KDE 4.7B? is not in yet.  KDE 4.6.3 is barely in.

---

### Post by el_koraco on 2011-06-02
And the beautiful Network Manager doesn't recognize my networks, although ifconfig shows wlan up. So I'm backing out on my promise to jump in early :-({|=

---

### Post by floydsp on 2011-06-02
> **kansasnoob said:**
> Rather touchy aren't we?

Everything we post here is public so it's hardly as though anyone was disrespecting you or talking behind your back ;)

Sorry for that reply....should of engaged my 78 year old brain before typing

floydsp

---

### Post by MrRtd on 2011-06-15
I found if you use the alternate CD image, it will install with no problems, but it is text based (so not as visually appealing).

Also I thought maybe the newer KDE 4.7 would be available to install but it doesn't seem to be there yet :(

---

### Post by jalmargyyk on 2011-06-15
You could add neon ppa ([link]("http://kyofel.wordpress.com/category/kde/")) to your repos if you want the latest kde stuff.

---

### Post by iClouseau88 on 2011-06-16
Hi,

I installed the June 15 alternate CD of Kubuntu 11.10.  Hash and disk integrity checks are OK, installation went smoothly at first, until the installer hung after the root and home partitions were selected. Screen shows "Loading the partitioner...52%....Please wait". During partitioning, I was not asked to choose the location of the boot loader.

---

### Post by floydsp on 2011-06-16
Just my luck I tried to install the June 15 alt ISO and the same thing happened to me.

Guess I will wait, seen the bug report on this. I used up several cd's trying to install this:D

floydsp

---

