---
title: "Does Kubuntu read previous user profile upon fresh install (?)"
date: 2020-01-19
forum: New to Ubuntu
---

### Post by ubname on 2020-01-19
Hi,

I had install ubuntu and firefox had some personal settings (bookmarks etc.),
wanting to try out how kubuntu works I did a fresh Kubuntu install overwriting
the previous ubuntu install; to my great surprise all firefox settings were already
set in the new kubuntu.

Is this a normal Kubuntu feature to read previous user profile and auto configure
firefox? Otherwise is it a new firefox feature (I do not and never used a firefox account)?

thanks!

---

### Post by deadflowr on 2020-01-19
Did you use the Something else/manual/other option when selecting where to install it on the disk?
If you use that option in any 'buntu and don't check the format option it'll not remove user data.

In this case, since the data wasn't removed, Firefox has the old profile settings already in place and is set to use them.

---

### Post by ubname on 2020-01-19
yes I indeed used a custom partition set, i'm pretty sure i deleted all partitions a recreated during the install process.
If the partitions were not removed is maybe a bug, or is it an intended behaviour?

---

### Post by guiverc on 2020-01-19
If you wanted to re-install but keep settings etc. you needed to use something else & **not format** or not re-create your partitions.

That choice will cause the installer to
 
[LIST]
[*]note your additional added packages
[*] system directories are wiped
[*]new system installed
[*]additional packages noted earlier (from prior install) are re-installed  (if you were using GNOME and thus had ubuntu-desktop installed; and your install is now kubuntu-desktop, packages that got installed as required for ubuntu-desktop (eg. gedit) won't be re-installed, packages need to be user/individually installed (not because of a depends rule)
[/LIST]

User directories are not touched so settings remain; however if you format or re-create partitions it's a new install and user settings don't survive.  

Of note: any system wide settings placed in system directories will be lost, but as most (esp. desktop) configuration files are located in $HOME (or user directories) they survive unless partition is formatted.

It sounds like you 'started fresh' because you formatted or re-created your partitions.

---

### Post by ubname on 2020-01-19
I'm sorry but you got it the other way around and maybe I was not clear in my OP.

What I wanted was a fresh clean install of Kubuntu and ended up with firefox settings from previous install,
despite having completely removed all previous existing partitions and recreated afresh using the "manual" partition option.

What I am trying to understand is: is this normal and indended behaviour or is it a kubuntu bug (kubuntu 19.10).

Thanks!

---

### Post by CelticWarrior on 2020-01-19
Let's use some reason here.

If you actually did what you're saying you did then it has nothing to do with bugs. The only possible cause is the use of a **Firefox account to sync the user profile** which is completely independent of partitions. But, this being the case, you would remember using it, I think...

---

### Post by ubname on 2020-01-19
It's probable I did not format the home dir, where I think all the firefox settings are stored.

---

### Post by CelticWarrior on 2020-01-19
So we're moving from > i'm pretty sure i deleted all partitions to > It's probable I did not format the home dir... Good, Occam's razor is something to keep in mind, always, not bugs.

---

### Post by ubname on 2020-01-20
As deadflowr suggested, it seems to me the most logical cause; thanks everybody for your help!

---

