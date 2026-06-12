---
title: "Trying to install a new theme"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by philby on 2008-04-24
Hi Everyone - I have just installed Hardy and have managed to get all the packages down etc with the Nvidia drivers working, and have downloaded a few themes but they won't intall.

Have unpackaged the file with the index.theme file which should install the theme but nothing happens after I run the file. Have also now got the compizconfig settings manager running but want to also try the emerald themes which are down but can't figure out how to switch between Emerald and Compiz

So any help would be great - it's probably simple but hard when there does not seem to be a simple way to do it.... - thanks Phil

---

### Post by Bodsda on 2008-04-24
Hey, can you upload the readme file for one of the themes you wont to install,. we should be able to fiugre it out from that

---

### Post by philby on 2008-04-24
Hi Bodsda - there is no readme file in the downloaded theme just the install file and the folders containing the buttons etc - have tried dragging into the compiz themes and emerald but none seem to like it, compiz says it's installed but it's not present as a theme within the file options

---

### Post by svriderpokey on 2008-04-24
I'm having the same issue.  I just upgraded to 8.4 from 7.10.  Compiz-fusion works great, but emerald broke.  I can only switch between the Gnome themes.  None of my emerald themes will load.

---

### Post by philby on 2008-04-24
> **svriderpokey said:**
> I'm having the same issue.  I just upgraded to 8.4 from 7.10.  Compiz-fusion works great, but emerald broke.  I can only switch between the Gnome themes.  None of my emerald themes will load.

Yes - can't even get emerald to run - but none of the themes will load also really driving me nuts - I thinks I'll take a break, the server's are overloaded and am finding it difficult to get packages - oh well.

---

### Post by svriderpokey on 2008-04-24
This gets my themes working for as long as the terminal window stays open.

[I]Applications>Accessories>Terminal
emerald --replace[/I]

As soon as I close the terminal window it reverts to the Gnome theme.  Is there a .conf file where I should pot this command?

---

### Post by qamelian on 2008-04-24
> **svriderpokey said:**
> This gets my themes working for as long as the terminal window stays open.

[I]Applications>Accessories>Terminal
emerald --replace[/I]

As soon as I close the terminal window it reverts to the Gnome theme.  Is there a .conf file where I should pot this command?
To detach the command from the terminal, follow it with &, and surround the command with parentheses, like so:
```
(emerald --replace &)
```

---

### Post by svriderpokey on 2008-04-25
Thank you, qamelian.  Your suggestion worked beautifully until I logged off, but at login it was back to the Gnome theme.  So I took a WAG tried entering the command into the CompizConfig Settings GUI, and it seems to have worked.

If someone who knows better than I do could check my work, I would really appreciate it.  Maybe if it's an acceptable solution, philby could use it too.  Here's what I did.

1- System>Preferences>Advanced Desktop Effects Settings
2- Make sure "Window Decoration" is checked.  
3- Click "Window Decoration" for settings
4- Change the "Command" entry from ```
/usr/bin/compiz-decorator
``` to ```
/usr/bin/emerald --replace
```
5- Applications>Accessories>Terminal
6- Type ```
(emerald --replace &)
```

---

### Post by qamelian on 2008-04-26
That's the rght way to do it. I should have mentioned that change in CCSM. If you install the simple settings manager or the fusion-icon utility, you can flip back & forth between decorators. Not always useful, but convenient when you are mixing & matching themes while looking to put together a new look for your desktop!:)

---

### Post by RyanthePenguin on 2008-04-28
I installed Emerald with Hardy and it is missing the Get Themes buttons it used to have.  I am pretty new to Linux and I have no idea where to get those themes from.  Can anyone enlighten me?

---

