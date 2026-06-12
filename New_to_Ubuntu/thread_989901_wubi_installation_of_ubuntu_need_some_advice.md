---
title: "wubi installation of ubuntu need some advice"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by damagedmafia on 2008-11-22
i have successfully installed the ubuntu desktop using wubi in windows vista

i have norton anti virus on the vista partition and i want this slipped streamed into ubuntu so i can scan for virus etc and have a firewall

i know there are tips to harden Ubuntu but i just want to use it like i use vista where i have my files in the vista partition accessed on the ubuntu OS

i think i can access the files but they dont run

what can i do

---

### Post by stalkingwolf on 2008-11-22
First as far as I know Norton will not work in Ubuntu.  There are 2
AV that I know have ubuntu native apps. Avast and ClamAV both available in synaptic.

Again your Win Apps will have to be run under Wine,Cedega, or Crossover.
Windows of any version will not recognize any Ubuntu files with out the addition of extra software.  Maybe not at all.  At least as far as XP Ubuntu
can read and write to files. As for Vista I just dont know.  I have heard that even Vista can't read and write to Vista formats.:)

---

### Post by philinux on 2008-11-22
To read ubuntu ext2/3 file system from vista you'll need this.

[http://www.fs-driver.org/](http://www.fs-driver.org/)
You can read windows files from ubuntu but only wine can run .exe files (sometimes). Best to find alternative linux software.

for ubuntu security read this.

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Good info site too. Happy reading.

---

### Post by shifty_powers on 2008-11-22
ubuntu and windows are two different os's with completely differing architecures, kernels etc...

although it is possible to run some windows applications in ubuntu with wine, (a "windows application layer", or basically an emulator in a way), what you want is not possible.

norton inetrfaces with windows on a kernel level, having ring 0 access, meaning everything. You cannot do that with ubuntu, as it operates on a different model.

ubuntu has a firewall built in, ip-tables, which is incidentally one of the most secure available. you can install graphical front ends for it, to configure it, but you don't need to do any more.

ubuntu, for all intents and purposes, does not suffer from viruses/ad-ware. You can install something like clam-win, as already mentioned, but all this does is scan for windows viruses. As you already have anti-virus on vista, not convinced that this is needed.

there is no need to harden ubuntu any more. it is not perfect no, but it would take somone a LOT of hard work and a lot of time to compromise your ubunut installation...

---

### Post by shifty_powers on 2008-11-22
[http://www.zdnet.com.au/news/software/soa/Ubuntu-more-secure-than-Leopard-Windows-Vista-/0,130061733,339287864,00.htm?feed=pt_windows](http://www.zdnet.com.au/news/software/soa/Ubuntu-more-secure-than-Leopard-Windows-Vista-/0,130061733,339287864,00.htm?feed=pt_windows)

this was a hacking challenge, where mac osx lasted a few hours, vista three days and ubuntu was never succesfully cracked...

---

### Post by stalkingwolf on 2008-11-23
> **shifty_powers said:**
> [http://www.zdnet.com.au/news/software/soa/Ubuntu-more-secure-than-Leopard-Windows-Vista-/0,130061733,339287864,00.htm?feed=pt_windows](http://www.zdnet.com.au/news/software/soa/Ubuntu-more-secure-than-Leopard-Windows-Vista-/0,130061733,339287864,00.htm?feed=pt_windows)

this was a hacking challenge, where mac osx lasted a few hours, vista three days and ubuntu was never succesfully cracked...

It is also instructive that the version used for this challenge used
7.10 a version that is 2 generations old.

---

### Post by Paqman on 2008-11-23
> **damagedmafia said:**
> 
i think i can access the files but they dont run


Can you be a bit more specific? Does your Vista partition show up as the Host under "Places"? Are you able to browse the files on it?

---

