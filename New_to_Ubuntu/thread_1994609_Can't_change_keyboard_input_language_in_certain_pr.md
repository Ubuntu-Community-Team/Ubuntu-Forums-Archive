---
title: "Can't change keyboard input language in certain programs"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by kwanylongy on 2012-06-03
Hi all,

I am a Traditional Chinese user of Ubuntu and I use gcin as my "Keyboard input method system" in Language Support.

I notice Ubuntu only allows me to change the input language in certain programs (or is this gcin's fault?). 
For instance, I am able to change the input language to Chinese in web browsers and LibreOffice, but I am unable to change it in programs such as gedit, emacs or even nautilus.

Anyone knows how to fix this? Thanks! :p

---

### Post by Irihapeti on 2012-06-03
Check that you have all three gcin immodules installed. In addition to the main gcin package, there is a gtk3 immodule and one for qt4.

If any are missing, install them, log out and in again, and you should find Chinese input available in other programs.

---

### Post by kwanylongy on 2012-06-03
Thank you Irihapeti for your reply.

Software centre shows that both the gtk3 and qt4 immodules are installed

---

### Post by Irihapeti on 2012-06-03
I'm not sure what's happening in that case. I don't use gcin, but I installed it on my netbook and I can get it to activate in a variety of programs, so I doubt that gcin itself is the problem. My guess is that it's something in the configuration files.

I'll keep investigating, and post again if I find anything useful.

---

### Post by kwanylongy on 2012-06-03
Thanks Irihapeti!
I'll keep trying to solve it too

---

### Post by kwanylongy on 2012-06-03
I am experiencing a further problem, which is making my Ubuntu virtually unusable

When checking in Software Centre if the gtk3 and qt4 im-modules were installed, I noticed there was another 'add-on package' of gcin named 'im-config'. I was curious to know if installing im-config would solve my problem, and so I installed it. After testing it out, I realised that im-config is simply a replacement for im-switch, and I noticed that im-swtich is required for changing the 'keyboard input method system' option in Language Support, so I uninstalled im-config and re-installed im-switch. 

Afterwards, gcin no longer worked on my system. Specifically, the gcin systray icon has become missing, and Ubuntu sometimes report it experiences an internal server error with gcin on startup (I'll put up a screen cap here next time the error comes up). I can restore the gcin icon by manually turning on gcin through the terminal, however the restored gcin does not allow me to change the input method to Chinese at all.

Not sure if this information would help: I further fiddled with the options of 'keyboard input method system' in Language Support and noticed that Chinese Input with iBus does work. However, the Chinese input provided by iBus is really unusable as it is very limited

Please help!

---

### Post by kwanylongy on 2012-06-05
Solved it! Now I've got gcin back and also got it working in programs that previously did not work!(i.e. gedit, nautilus)

I think the problem due to im-switch, since I installed im-config (which automatically uninstalls and replaces im-switch) and reinstalled gcin and everything just began working again.

Thanks Irihapeti for your support :p

---

### Post by Irihapeti on 2012-06-05
I'm glad you got it working again. I'll make a note of your fix because it may come in useful in the future. I've used scim and iBus (for the small amount of Simplified Chinese that I need) but not gcin.

I was beginning to wonder if a reinstall might be needed, but I'm pleased to see that it didn't come to that.

---

