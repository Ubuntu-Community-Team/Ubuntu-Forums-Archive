---
title: "gwibber"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by protpisys on 2011-10-21
how the hell do I turn this #$&$*@! thing off? please make it stop! Thanks

---

### Post by Rex Bouwense on 2011-10-21
What are you trying to turn off in Gwibber (facebook, twitter)?

---

### Post by LinuxFan999 on 2011-10-21
Open the terminal and type this:

```
sudo apt-get purge gwibber
```

---

### Post by protpisys on 2011-10-22
> **Rex Bouwense said:**
> What are you trying to turn off in Gwibber (facebook, twitter)?

both, but twitter is the main pita

---

### Post by choclatboy on 2011-10-22
> **LinuxFan999 said:**
> Open the terminal and type this:

```
sudo apt-get purge gwibber
```

apt-get says:
> 
The following packages will be REMOVED:
  gwibber* ubuntu-desktop*


can't remove gwibber without touching the desktop.

any idea?

---

### Post by Rasa1111 on 2011-10-22
I also went to remove gwibber the other day..
and it also told me it would remove ubuntu-desktop. So I stopped. 

Really? Can't remove this gwibber rubbish without removing my whole desktop?

d'oh!

I want gwibber gone!
never been a problem to remove it before.

---

### Post by killswitchguy on 2011-10-22
u can uninstall the facebook , twitter plugins using synaptic package manager. i had the same problems too.

---

### Post by Rasa1111 on 2011-10-22
but I don't want just the plugins gone..
I want gwibber gone, for good.

Is this no longer possible?

What is this, like MS with IE? 
(sorry, can't remove it, you're stuck with it!) lol

---

### Post by markbl on 2011-10-22
You can uninstall or purge gwibber if you want. ubuntu-desktop is just a dummy pseudo package which wraps all the standard ubuntu stuff so you can let it get uninstalled also and it won't affect anything.

I think gwibber is hopelessly immature also but there is no need to remove the package. Just don't use it! Make sure you start it once and then disable the "start service at login" preference. At your next login there won't be any gwibber software running.

---

### Post by Rasa1111 on 2011-10-22
well that is good to know, thanks mark. 

Now I'll just wait until someone else does it first, just to make sure. lol :P
and if Im never, ever going to use an application, I see no need for it to be installed, period. 
While it takes up only a minimal amount of space.. it's still taking up space, for no reason at all.
So id just rather trash it completely.

---

### Post by protpisys on 2011-10-22
> **markbl said:**
> You can uninstall or purge gwibber if you want. ubuntu-desktop is just a dummy pseudo package which wraps all the standard ubuntu stuff so you can let it get uninstalled also and it won't affect anything.

I think gwibber is hopelessly immature also but there is no need to remove the package. Just don't use it! Make sure you start it once and then disable the "start service at login" preference. At your next login there won't be any gwibber software running.

So if I uncheck "start service at login" it won't constantly be on my screen...I don't mind it being there I just wanted to shut it off, I find it annoying and distracting...well that seemed to do the  trick, thank you for the help

---

### Post by Shazaam on 2011-10-22
The only time you have to worry about removing ubuntu-desktop is if you want to do an upgrade, say to upgrade from Oneric Ocelot to Precice Penguin (next version). Then it's just a matter of reinstalling ubuntu-desktop.

---

### Post by protpisys on 2011-10-23
thanks, I just wanted to get rid of those constant twitter updates on my screen, I just turned it off from the preference menu

---

