---
title: "[SOLVED] Ubuntu Server, upgrade to LTS"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by batfastad on 2008-10-01
Hi everyone
I'm relatively new to Linux, but very new to Ubuntu and especially the server edition

I set up a test NAS device a few months back using Ubuntu Server 8.04

I notice now that the LTS version is available - do I need to do anything to change me 8.04 Server into 8.04 Server LTS?
Or am I actually already running the LTS version?

Thanks, B

---

### Post by rybaxs on 2008-10-01
hi batfastad

is your ubuntu server edition have GUI?

---

### Post by Archmage on 2008-10-01
If you have 8.04 you are automatical LTS.

---

### Post by batfastad on 2008-10-01
Yeah I installed gnome onto the test server (not recommended I know) so I could mess around and get the configuration right.
I do a great deal through the terminal instead now

This is what I did to install the basic GUI packages:
```
sudo apt-get update
sudo apt-get install xorg
sudo apt-get install gnome-core synaptic
```

---

### Post by Joeb454 on 2008-10-01
Ubuntu 8.04 is the LTS version.

The next LTS version is still unconfirmed. I'd imagine it'll be sometime 2010 though

---

### Post by batfastad on 2008-10-01
Oh right, ok.
I didn't know if there was a difference in the actual version.

So my Ubuntu Server 8.04 ISO I downloaded, should be identical to the current LTS one?

I'm about to set up another test server and install Zimbra which is pretty picky about Linux versions. So I didn't know if the internal Linux version headers were different and I'd end up having problems.
Don't want to download & burn another ISO if I don't need to! :D

Thanks, B

---

### Post by Archmage on 2008-10-02
> **batfastad said:**
> So my Ubuntu Server 8.04 ISO I downloaded, should be identical to the current LTS one?

Both a different, because one is a Live-CD and both will install different software packages, but you can install/deinstall exactly the same software, so at the end it didn't matter what you use for installing.

---

### Post by batfastad on 2008-10-03
Ok that's all good news then!
Just wanted to make sure my installation of Zimbra would be ok using the disc I've already got.

Thanks, B

---

### Post by pheckmann on 2008-10-03
> **batfastad said:**
> Yeah I installed gnome onto the test server (not recommended I know) so I could mess around and get the configuration right.
I do a great deal through the terminal instead now

This is what I did to install the basic GUI packages:
```
sudo apt-get update
sudo apt-get install xorg
sudo apt-get install gnome-core synaptic
```

Are there other GUI's that are recommended?

---

### Post by hyper_ch on 2008-10-03
on a server you should not run any gui at all ;)

---

### Post by Joeb454 on 2008-10-03
You can if you so choose - if you're new to servers, and the server is powerful enough, I don't see the harm in running an XFCE desktop or something (maybe *box)

---

### Post by pheckmann on 2008-10-03
> **Joeb454 said:**
> You can if you so choose - if you're new to servers, and the server is powerful enough, I don't see the harm in running an XFCE desktop or something (maybe *box)

New to Ubuntu - too damn old in Windows...

BTW - it's a 2950 Dell with quad core plus 12G RAM

---

### Post by batfastad on 2008-10-03
> **hyper_ch said:**
> on a server you should not run any gui at all ;)

I agree, even though I am doing so at the moment. Very useful for learning!
And I never leave the machine logged in/GUI running.
Once It's fully up and running though I'll re-install without gnome and replicate the various configuration files.

---

