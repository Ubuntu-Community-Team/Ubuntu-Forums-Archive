---
title: "[SOLVED] Ff 3"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by deadlySniper on 2008-07-03
How do you install FireFox 3.0 not FireFox 3 beta 4

---

### Post by sydbat on 2008-07-03
If you are running Hardy, it is in the repos...and should be updated automatically.

---

### Post by deadlySniper on 2008-07-03
I am running xubuntu, and used synaptic and gave me beta 4

---

### Post by roger_1960 on 2008-07-03
Hi

If you are running Xubuntu 8.04, you probably need to update the repositories lists(update button in synaptic) before searching for FF3 and then installing.

---

### Post by deadlySniper on 2008-07-03
I did and it gave me the beta verison. I have a windows desktop (family) and it has FF 3.0 no beta.

---

### Post by ChameleonDave on 2008-07-04
> **deadlySniper said:**
> I have a windows desktop (family) and it has FF 3.0 no beta.

And I have Kubuntu Hardy Heron, and it has Fx 3.0, not beta.  What's your point?

Here is a link to the Ubuntu repo:
[http://au.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/](http://au.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/)

I can see [http://au.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/](http://au.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/) and it looks good to me.

Are you definitely running Hardy Heron (the latest Ubuntu)?  Is it on a standard i686 PC?

---

### Post by deadlySniper on 2008-07-04
I am running XUBUNTU

---

### Post by ChameleonDave on 2008-07-04
> **deadlySniper said:**
> I am running XUBUNTU

Yes.  "Xubuntu" or "Kubuntu" or "Fluxbuntu" as opposed to just "Ubuntu" is just a fancy way of saying that you log on with Xfce or KDE or Fluxbox instead of GNOME, which is the default for Ubuntu.

But none of that is important.

What version are you using?  The latest is Ubuntu 8.04, codename 'Hardy Heron'.  Before than it was Ubuntu 7.10, codename 'Gutsy Gibbon'.

Open a terminal and enter the following to find out:

```
cat /etc/lsb-release
```

Another issue is whether you have a peculiar sort of computer, such as a 64-bit one. 

Open a terminal and enter the following to find out:

```
uname -m
```

---

### Post by AnarkistNZ on 2008-07-04
> **deadlySniper said:**
> I am running XUBUNTU

Yes, but that's your graphical desktop. It's not which distro you're running.

Edit: Beaten to it.

---

### Post by deadlySniper on 2008-07-04
Xubuntu 7.10 and 32bit

---

### Post by dizee on 2008-07-04
Firefox 3 is not available in the main repos for 7.10.

Here is a guide to installing it: [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by ChameleonDave on 2008-07-04
> **deadlySniper said:**
> Xubuntu 7.10 and 32bit

That's it then.

You are using an old version of (X)Ubuntu.

You could upgrade to 8.04 to enjoy the latest stuff.

If you prefer to stick with 7.10, then you have to stick with the older version of Firefox for now, unless you install it manually.

---

### Post by deadlySniper on 2008-07-04
I just installed it and i have heard that 8.04 will over heat my comp

---

### Post by fidamehran on 2008-07-04
> **deadlySniper said:**
> I just installed it and i have heard that 8.04 will over heat my comp
Not likely that 8.04 will over heat your PC. I've been using it and found no problem. How old a PC are you running? Pentium 2?

---

### Post by ChameleonDave on 2008-07-04
> **deadlySniper said:**
> I just installed it and i have heard that 8.04 will over heat my comp

I hadn't heard that, but it is true that people have been reporting quite a lot of bugginess with 8.04 'Hardy Heron'.  It may indeed be a good idea to stick with 7.10 'Gutsy Gibbon' until 8.10 'Intrepid Ibex' comes out.

---

### Post by deadlySniper on 2008-07-04
I have a Pentium M and its an IBM ThinkPad T41

---

### Post by silkstone on 2008-07-04
If you are happy with what you have, there is no reason to change.

I'm running Hardy on a new desktop PC, a six-year-old PC and a two-year old laptop (Acer 5612) and there are no overheating issues. Right now my CPU is running at 39C and the GPU at 47C. The laptop tends to stabilise at around 42C, but that's no guarantee that your machine will play nicely with Hardy.

As long as it all works for you now, enjoy! :)

---

