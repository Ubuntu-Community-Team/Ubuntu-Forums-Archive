---
title: "Re using downloaded packages on other machines?"
date: 2005-02-01
forum: Repositories &amp; Backports
---

### Post by paul cooke on 2005-02-01
OK, I've come from the Suse world, where I was able to save security update packages from being deleted and thus make them available to other machines on my network... now my question is this: How can I do something similar with Ubuntu, ie get packages I've downloaded or upgraded via synaptic to be made available for my other machines without having to redownload them from the web on each machine? Is this easy, or do I have to make a local mirror of the repositories on one machine on my network and set that as a source for my other machines.

---

### Post by mendicant on 2005-02-01
I'm not sure about synaptic, but with aptitude, it leaves the downloaded packages in /var/cache/apt/archives, unless you do an aptitude clean.   So you can just have each machine use those files (NFS mount, or copy the files or use apt-move to maintain an archive).

---

### Post by paul cooke on 2005-02-01
yep, synaptic has stuck them there (/var/cache/apt/archives)

Hmmm, time to start reading some man pages... :) YAST made this rather easy...

and must remember to do the original updating/upgrading using the machine with plenty of space on it's drives... the box I'm playing with is an old cyrix mII 300 MHz machine that I've got spare to experiment with before committing to installing Ubuntu on the rest of my machines.

---

### Post by az on 2005-02-01
Synaptic and aptitude all use apt.  It is the same thing.

---

### Post by mendicant on 2005-02-01
[QUOTE=azz]Synaptic and aptitude all use apt.  It is the same thing.[/QUOTE]

Right--what I wasn't sure of was if synaptic erased those files, like dselect used to do.

---

### Post by mendicant on 2005-02-01
If you do this for a lot of machines, and install Ubuntu a lot, you may find it worthwhile to set up a full blown internal mirror.

You could also just limit the mirror to warty-security.

You could also automate things by putting a file in /etc/apt/apt.conf.d to copy the files over for you (or call apt-move, or start the update process on other machines).

---

