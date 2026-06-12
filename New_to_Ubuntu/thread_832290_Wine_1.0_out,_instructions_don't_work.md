---
title: "Wine 1.0 out, instructions don't work"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by zaivala on 2008-06-17
I just received an announcement on Slashdot that Wine 1.0 has just been released.  After paging through stuff, the page for Ubuntu is found at [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) .  The problem is, the person who wrote the instructions apparently doesn't know what he's doing, or I didn't type them correctly (since I tried several times, probably the former).  Does anyone know how to help me?

Moss

---

### Post by renfrew on 2008-06-17
I might recommend that you try copy/pasting the instructions from the site, rather than typing them out, before you throw in the towel...  I'm at work right now on a windows box and not able to try it myself, but in just looking, it seems likes its valid syntax. Spaces can really trip you up when copying it out by hand;)

You mention that it isn't working but where exactly is it failing?  at what step does it fail?

---

### Post by zaivala on 2008-06-17
> **renfrew said:**
> I might recommend that you try copy/pasting the instructions from the site, rather than typing them out, before you throw in the towel...  I'm at work right now on a windows box and not able to try it myself, but in just looking, it seems likes its valid syntax. Spaces can really trip you up when copying it out by hand;)

You mention that it isn't working but where exactly is it failing?  at what step does it fail?

Ya know, I tried that, and my Terminal won't accept paste.

The first step fails at the -0- .  The second step tells me I'm using an incorrect switch.

---

### Post by eriqjaffe on 2008-06-17
The instructions for adding those repos has been there a while.

If it's giving you trouble, you can also just download the .deb directly on the "[deb archive](http://wine.budgetdedicated.com/archive/index.html)" page.

---

### Post by Nythain on 2008-06-17
try "shift+insert" to paste into your terminal

---

### Post by cariboo on 2008-06-17
To paste in a terminal, if you've got a wheel mouse, press the wheel to paste. If you got a two button mouse press both keys at the same time.

Just highlight the text you want to paste and do one of the above and you should be good to go.

Jim

---

### Post by bodhi.zazen on 2008-06-17
To be honest, if all else fails, you can skip that step. All that will happen is apt-get will complain about untrusted repos / missing keys but wine will still install.

---

### Post by zaivala on 2008-06-17
OK, the first step worked using my wheel paste.

The second step resulted in a LOT of updates being loaded, not just Wine, but when it got to Wine, it said the signature could not be verified because the PUBKEY was not available...

Then, when I tried the other two recommended steps ("Click This Link" and Use Add/Remove Programs), it said Wine was already installed.

???

Moss

---

### Post by bodhi.zazen on 2008-06-17
> **zaivala said:**
> OK, the first step worked using my wheel paste.

The second step resulted in a LOT of updates being loaded, not just Wine, but when it got to Wine, it said the signature could not be verified because the PUBKEY was not available...

Then, when I tried the other two recommended steps ("Click This Link" and Use Add/Remove Programs), it said Wine was already installed.

???

Moss

LOL

You can ignore that error. It is telling you you did not import the key. You can ignore it and install anyways.

---

### Post by zaivala on 2008-06-17
> **bodhi.zazen said:**
> To be honest, if all else fails, you can skip that step. All that will happen is apt-get will complain about untrusted repos / missing keys but wine will still install.

Yup, it did that, and I guess it installed.

Thanks.

---

### Post by The Cog on 2008-06-17
I may be wrong, but I seem to remember that those instructions didn't work for me first time. It may help if you "prime" your terminal first by doing "sudo ls" or some such, so it doesn't ask for the password partway through the command. Or maybe I did "sudo -i" and then pasted the commands without the sudo in front - I don't remember. But I have seen an issue something along those lines.

---

