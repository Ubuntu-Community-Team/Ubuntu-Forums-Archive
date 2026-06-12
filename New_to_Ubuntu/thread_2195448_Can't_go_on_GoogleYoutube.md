---
title: "Can't go on Google/Youtube"
date: 2013-12-24
forum: New to Ubuntu
---

### Post by fxnj on 2013-12-24
I can access these sites perfectly fine on my Windows/iOS devices, but can't on my Ubuntu computer. When I try to go to them it just instantly tells me it can't load them, as if it isn't even trying to do so. Help?

---

### Post by oldos2er on 2013-12-24
What browser are you using? Which version of Ubuntu? Is this your own computer, and/or are you using a proxy or behind a firewall?

---

### Post by Petro Dawg on 2013-12-24
Just to clear something up, can you connect to any other web sites while on Ubuntu?  Also be sure to answer **oldos2er**'s questions.

---

### Post by fxnj on 2013-12-24
Yeah, I can connect to every page except Google-related products, which is really annoying since I have my email on it.

I'm using Firefox on Ubuntu 13.10. Not sure if it's a proxy or firewall stopping me. How would I check?

---

### Post by Petro Dawg on 2013-12-25
I am assuming you are on your own personal home network.  What is the computer history?...  Did you install Ubuntu yourself on your own computer or was the computer obtained elsewhere with Ubuntu already installed?  Did you knowingly set up a firewall yourself, if so which one (UFW, firestarter, etc..).

You can find info about the default Ubuntu firewall (ufw) here... ([https://help.ubuntu.com/12.10/serverguide/firewall.html](https://help.ubuntu.com/12.10/serverguide/firewall.html))

If using ufw, I would try disabling the firewall first and see if it helps...

```

[COLOR=#333333][FONT=monospace]sudo ufw disable[/FONT][/COLOR]

```

If using firestarter, look at the following documentation to figure out how to disable ([https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter))

If none of those apply, then we'll try something else.

---

