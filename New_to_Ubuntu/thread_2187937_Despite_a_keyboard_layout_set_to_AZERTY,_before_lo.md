---
title: "Despite a keyboard layout set to AZERTY, before logging in, it's still QWERTY O_o"
date: 2013-11-14
forum: New to Ubuntu
---

### Post by beuaravousaussi on 2013-11-14
Hello !

First time visitor, I hope everyone is well :)

I'm experimenting with linux distros to prepare for my wife's aunt, an old lady who wants to switch to "the open source" when her seven-year old windowsXP machine eventually reaches the OS's end of life cycle. Personally, I'm more fluent with the commandline server-side of linux (I manage a dedicated server with debian squeeze, for my websites), my last graphical experience with Linux was in 2005.

I've been running plenty of tests with VMWare Player, and I think I'll settle for Xubuntu, this is lightweight enough for the aunt's laptop (hopefully... because, else, the other distros will be much less user-friendly, and I want to install something with a LTS life cycle, if the lady stuck with XP, this is because she favours stability and functionality over glitter, as long as it works and suits her neds, she's fine with what she has.

However, there's one last issue for me, I don't find how to solve it for the moment, could I ask you, please ?

See that screenshot : [http://imgur.com/2P5tSQg](http://imgur.com/2P5tSQg)

I should have typed ABCDEFGHIJKLMNOPQRSTUVWXYZ, however, something else came up.

I configured the OS's locale to be the French language, I made the numeric values the French-used ones, I chose France's local layout, called AZERTY. While Xubuntu is already running, all is fine with it (hmm, except the default folders, Pictures, Music, Downloads, still in English, unlike Ubuntu by default who does rename them when switching locale... I'll have to see how to get it configured).
This is only before logging in, that the keyboard is, still, in English locale, QWERTY.

I see nightmares for the aunt coming from this ^^

Would you know how to fix that issue, and have the keyboard be in French even before logging in ?
Thank you if you know :)

*(And sorry for the looong post, I figured background information would be potentially relevant or useful !)*

---

### Post by grahammechanical on 2013-11-14
Hi and welcome to the forums.

I am not using Xubuntu but Ubuntu and it is the latest (13.10) so things might be different in Xubuntu 12.04. But as a test I have just set a French keyboard layout and I get an icon in the top panel that lets me switch keyboard layouts and choosing French changes qwerty to azerty. But what is important from your point of view that the same keyboard icon appears in the top panel at the login screen. You should be able to set the keyboard layout for the login at the login screen. I am not sure if this is available on Xubuntu 12.04 LTS. But it is where I would look.

Regards.

---

### Post by newb85 on 2013-11-14
If I'm not mistaken, one major difference between the two systems is that Xubuntu uses GDM, whereas Ubuntu uses LightDM.

---

### Post by beuaravousaussi on 2013-11-28
Oops, I was forgetting to reply.

Thank you very much for your answers !

Though, they didn't miraculously fix my issue ;)

This is strange, I had the issue no matter how many times I tried inside VMWare Player (which emulates an apparently English machine), telilng the system to be in French in all regards, except the username/password step stuck in qwerty.
And when I finally installed Xubunto on an actual laptop, and not a virtual machine, the system ran perfectly well and, once told to be in French, had everything in French, properly, including the pre-logged-in step.

"Why ?"
"Who cares, it worked !"

So, all in all, all has been good. I converted successfully my aunt, she doesnt even remotely miss her windowsXP, the addition of Whisker to the "like Start" menu helped (I'm mentioning in case it may help other persons in the same situation), so I guess I can call this a good ending :)

---

