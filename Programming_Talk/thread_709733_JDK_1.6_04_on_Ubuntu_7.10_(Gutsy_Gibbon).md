---
title: "JDK 1.6_04 on Ubuntu 7.10 (Gutsy Gibbon)?"
date: 2008-02-27
forum: Programming Talk
---

### Post by giesen2 on 2008-02-27
I would like to install JDK 1.6.0_04 on my Ubuntu 7.10 system, however, Synaptic Package Manager only shows 6-03-0ubuntu2.

I specifically want 1.6_04 (not 1.6_03), because of the JAXB 2.1 fixes. This release has been out on Windows for well over a month. I was hoping that by now, there would be Ubuntu packages for JDK 6.04.

Is JDK 6.04 available for Ubuntu 7.10? If so, how do I get it?

If not, why is it taking so long? It's been out on Windows for over a month.

Is there a bette forum for this question?

---

### Post by pieisgood4589 on 2008-02-27
Sorry, there is no JDK 1.6_04 out on Linux OS yet, I'm waiting for it too!

---

### Post by giesen2 on 2008-02-27
> **pieisgood4589 said:**
> Sorry, there is no JDK 1.6_04 out on Linux OS yet, I'm waiting for it too!

jdk 6u4 is definitely out for Linux. I can download jdk-6u4-linux-i586.bin from java.sun.com. That has been available for over a month.

However, Ubuntu's Synaptic package manager doesn't show something like this. I previously installed jdk 6u3 through Synaptic, I would like to install 6u4 that way as well. I could try manually downloading/running directly, but I'm afraid that won't work correctly.

---

### Post by themusicwave on 2008-02-27
You shouldn't have much trouble installing it from their site.

I have done it in the past and it was pretty simple.  You just need to run the installer and then set your system PATH variable.  Basically, you need to add a listing for the JDK.

There are several ways to add it to the path, you can add it to your .basrc file, your etc/enviroment file or perhaps other ways.

There should be plenty of information on doing this in the forum and on the web.

I'm not sure what the big differences better 6_03 and 6_04 are or if they are worth the trouble.  Why do  you need that minor update so badly?  Is there something I don't know(quite possible)?

---

### Post by giesen2 on 2008-03-01
> **themusicwave said:**
> I'm not sure what the big differences better 6_03 and 6_04 are or if they are worth the trouble.  Why do  you need that minor update so badly?  Is there something I don't know(quite possible)?

I want a specific fix regarding JAXB.

1.6_04 includes JAXB 2.1, which I need, while 1.6_03 includes JAXB 2.0, which isn't working.

---

### Post by ZylGadis on 2008-03-01
The repositories are frozen once a distribution release is made (actually a bit before that, even), so you are out of luck. The only changes made are bug fixes and security patches, there are no version updates to the programs. You can try one of two things:

- try the Hardy Heron backports repository (if it exists). It might contain the version you want, but I doubt it - backports are rarely maintained in any useful state, because it does not make sense from the developers' point of view - the next distro version is just around the corner, so why waste time on the old one?
- install Hardy Heron in its current state (should be pretty steady, it's only a month and a half till release), and use its repositories.

What you should not do is try to use Hardy Heron's repositories on another version (7.10 in your case). There is a huge potential for breakage. I'd recommend installing sun's version of JDK: it is easy to do, it works, and the minor inconvenience of not having it in dpkg is... minor.

---

### Post by jay019 on 2008-03-04
> **ZylGadis said:**
> 
What you should not do is try to use XXX repositories on another version. There is a huge potential for breakage. 

lol. i learnt that the hard way :oops:

---

