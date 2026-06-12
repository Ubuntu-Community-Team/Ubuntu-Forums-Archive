---
title: "Unmet Dependencies Error While Installing KDE"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by BlacklightHalo on 2013-06-19
I tried installing KDE Desktop through the terminal as instructed on [this website]("http://www.noobslab.com/2013/02/install-kde-410-in-ubuntu-12101204linux.html"). I was given the following error when I entered ```
sudo apt-get install kubuntu-desktop
```...

"Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 kubuntu-desktop : Depends: xorg but it is not going to be installed
E: Unable to correct problems, you have held broken packages."

I wondered if the solution might be as simple as separately entering "sudo apt-get install xorg" but typing in the terminal when I don't know what something will do makes me antsy. Would someone with experience please tell me how to resolve this issue?

---

### Post by newb85 on 2013-06-19
I would try
```
 sudo apt-get -f install kubuntu-desktop 
```
first.

---

### Post by oldos2er on 2013-06-19
That's odd. What distro/version are you running? Can you show the output of ```
apt-cache policy xorg
``` ?

---

### Post by BlacklightHalo on 2013-06-20
```
apt-cache policy xorg
```

gets me...

```
xorg:
  Installed: 1:7.6+12ubuntu2
  Candidate: 1:7.6+12ubuntu2
  Version table:
 *** 1:7.6+12ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1:7.6+12ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
```

---

### Post by oldos2er on 2013-06-20
Try ```
sudo apt-get update && sudo apt-get install kubuntu-desktop
``` If it shows errors please copy and paste them here.

---

### Post by SeijiSensei on 2013-06-20
deleted; see below

---

### Post by SeijiSensei on 2013-06-20
I had this problem as well on one of my 13.04 machines today.  There were 100 packages that had been "kept back," and all of them related to KDE.  After I added the [ppa:kubuntu-ppa/ppa]("https://launchpad.net/~kubuntu-ppa/+archive/ppa") repository, everything installed correctly.  I wondered if some of the new packages in the standard repository depend on more recent versions in the PPA.  Most of the problems concerned versioning, with kubuntu-desktop requiring some 4.4.10.4 libraries that were not in the standard repository.

I think I encountered this problem once before with Kubuntu where some of the packages in the standard repository were ahead of others not yet moved there.

Edit:  I had to update twice to get everything back in order.

---

### Post by BlacklightHalo on 2013-06-20
"sudo apt-get update && sudo apt-get install kubuntu-desktop"

You mean enter that entire thing verbatim? (just making sure)

---

### Post by newb85 on 2013-06-20
> **BlacklightHalo said:**
> "sudo apt-get update && sudo apt-get install kubuntu-desktop"

You mean enter that entire thing verbatim? (just making sure)

Precisely.  The double-ampersand (&&) means the two commands will be executed consecutively.  (A single ampersand would run them simultaneously, which isn't the goal here.)

---

### Post by oldos2er on 2013-06-20
> **BlacklightHalo said:**
> "sudo apt-get update && sudo apt-get install kubuntu-desktop"

You mean enter that entire thing verbatim? (just making sure)

Yes, you can copy and paste it into a terminal.

---

### Post by newb85 on 2013-06-21
Oh, yes, sorry.  Copying and pasting is a better idea than manually typing it.  Less room for error that way.

Note that the keyboard shortcut for paste in the terminal is Ctrl+Shift+V, not just Ctrl+V.  You should also be able to simply highlight the command and drag it into the terminal.

---

### Post by BlacklightHalo on 2013-07-11
Okay, I tried that. After restarting the computer, I am down to a root shell prompt/terminal and cannot get a GUI at all (hence my having not replied to this in a long time.) Is there something I can enter to revert to the last stable configuration? Or is there another route I should take?

---

### Post by oldos2er on 2013-07-11
Were there any errors from that command? Did you try SeijiSensei's suggestion?

What are your hardware specs, particularly your video card?

---

### Post by oldos2er on 2013-07-11
Were there any errors from that command? Did you try SeijiSensei's suggestion?

What are your hardware specs, particularly your video card?

---

### Post by BlacklightHalo on 2013-07-11
> **oldos2er said:**
> Were there any errors from that command? Did you try SeijiSensei's suggestion?

What are your hardware specs, particularly your video card?

I don't recall if there were errors since it happened awhile ago. I don't think there were. I know the computer in question is a Dell Inspiron 1525 laptop. Its video card is unknown to me, but I know it has 4GB RAM and somewhere over 200GB hard drive space with a dual-core processor. It's about six years old. If you know a command to diagnose what went wrong or any of the need-to-know specifications, I would love to know it/them as well. I don't think I tried SeijiSensei's suggestion. The "&&" code is very new to me and I feel as though I would remember if I had ever tried using it.

---

### Post by oldos2er on 2013-07-11
"&&" is just a way to string two or more commands together in a fail-safe way, if the first command fails for some reason, it'll stop without executing the second one.

You can see which video card you have with ```
lspci | grep VGA
```

---

### Post by BlacklightHalo on 2013-07-12
The output of 

```
 lspci | grep VGA 
```

is

```
00:02.0 VGA compatible controller: intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
```

---

