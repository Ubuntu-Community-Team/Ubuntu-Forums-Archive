---
title: "problem in clipgrab"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by m7md.osma on 2011-12-15
hi dears,
I tried to install Clipgrab and I got alot of problems


it said :-
Cannot install 'libavcodec-extra-52'

and after I download 'libavcodec-extra-52' manually it says

Dependency is not satisfiable: libavutil-extra-49 (>= 4:0.5.1)

anyone can help me or give me a guide:(

---

### Post by lechien73 on 2011-12-15
Hello and welcome to the forums,

What version of Ubuntu are you running? Did you download libavcodec-extra-52 or did you install using apt-get?

If you just downloaded it, then the libavcodec-extra-52 library is available in the multiverse repositories, so you'll need to enable them. Go to the Ubuntu Software Centre, click the Edit menu, choose Software Sources, and check the "Software restricted by copyright or legal issues (multiverse)" box.

Then open a terminal window and type:

```
sudo apt-get install libavcodec-extras-52
```

It will install the package, complete with all dependencies.

---

### Post by m7md.osma on 2011-12-15
Hello Friend,

Thanx very muchand I am happy to join you and very pleased of your answer

My ubuntu version is 11.04 or Natty Narwhal, and I download it and then try to install it, the file I download is "libavcodec-extra-52_0.5.1-1ubuntu1.2_i386.deb".



I do as you said and I found that the "Software restricted by copyright or legal issues (multiverse)" box is already checked.I also tried to write the command you give me in terminal and it give me this error:
```
E: Unable to locate package libavcodec-extras-52
```

thanx again for your help I hope not to annoy you.

Mohamad Osama

---

### Post by m7md.osma on 2011-12-15
Hi friend,

I have a question.
what is the difference between these sources:
apt
.rpm
.tar.gz
YUM

thanx for helping

yours,

---

### Post by lechien73 on 2011-12-15
I'm very sorry, but I made a mistake and included an extra 's' when I typed the command.

Please could you try:

```
sudo apt-get install libavcodec-extra-52
```

In answer to your question, apt is the name of a collection of package management tools for Debian-based Linux distributions; .rpm files are packages for use by the RPM package management system, which is primarily used by RedHat; .tar.gz files are compressed archives (tar does the archiving and gzip compresses); and YUM is the Yellowdog Updater, Modified, which is a package manager for RPM-compatible systems.

The ones you will most likely use with Ubuntu are apt (.deb files) and .tar.gz.

---

### Post by m7md.osma on 2011-12-18
thanx alot for your help

and for the information :D:D

yours,
Mohamad Osama

---

### Post by lechien73 on 2011-12-19
You're welcome. If this your problem is fixed, could you please mark it as [SOLVED] using the **Thread Tools** menu at the top of the page?

Thanks

---

### Post by m7md.osma on 2011-12-23
thanx dear friend,
The problem was solved by re-installing the Ubuntu.:D :D :D
but thanks very much to you and your help really you was helpful.
thanx again
yours,
Mohamad Osama

---

