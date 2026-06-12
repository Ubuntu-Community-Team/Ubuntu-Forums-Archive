---
title: "I get    'sudo: make: command not found'"
date: 2019-03-29
forum: New to Ubuntu
---

### Post by billy3xs on 2019-03-29
The directions for installing Anki have failed me!  :P
If I try installing from Synaptic, the shortcut for Anki appears but does not seem to run Anki.
I did a complete remove of Anki in Synaptic.

The from the Anki directions in Terminal:
tar xjf Downloads/anki-2.1.11-linux-amd64.tar.bz2
cd anki-2.1.11-linux-amd64
sudo make install

I get     ' sudo: make: command not found'

./bin/anki fires up Anki and the shortcut appears in the tool tray, but disappears after closing with no shortcut in applications.

So, two ways of installing, each yielding half a result.

Is there a typo in the 'sudo make install' command?
Any help would be greatly appreciated. I had it running last install, but my install sucked, so this is my second Ubuntu install.
thanks...

billy2xs@billy2xs-W150ER:~/anki-2.1.11-linux-amd64$ sudo apt install make
E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavailable)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?

---

### Post by SeijiSensei on 2019-03-29
You need to install the build-essential package.

---

### Post by billy3xs on 2019-03-29
Woo Hoo, it worked, you da man!
and thanks for the rec
Anki works! :popcorn:

---

### Post by thenailedone on 2019-03-29
> **SeijiSensei said:**
> You need to install the build-essential package.

Wonder how many forum posts and frustration would be spared if this was installed by default :-k

---

### Post by SeijiSensei on 2019-03-29
The vast majority of Ubuntu users never have a need to compile anything, so I'm not surprised it's not included in desktop distributions. I don't recall if it is packaged with the server editions; I use CentOS on servers.

---

### Post by oldrocker99 on 2019-03-30
And Synaptic isn't installed by default either, it's a more useful program, and millions want to know ***WHY?***

---

