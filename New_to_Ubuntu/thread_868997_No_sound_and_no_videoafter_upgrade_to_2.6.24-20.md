---
title: "No sound and no videoafter upgrade to 2.6.24-20"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by gerben1 on 2008-07-24
Hi,

After today's update to the new kernel version 2.6.24-20-generic I cannot play any sound anymore. If i try playing an mp3 audacious just freezes, other programs either freeze or crash... 

I haven't tweaked around with xorg.conf so perhaps I can solve the video problem myself with an evening of putting in and taking out options until i have something workable. For the soundproblem however I have no idea where to start looking.

Does anybody else have this problem? 

(for now I am just choosing kernel 2.6.24-19-generic from the Grub boot menu, which works fine)

---

### Post by avtolle on 2008-07-24
There are several threads on the Forum today about the latest kernel update, which came from the proposed repository. There is a known bug with it; I'd advise you continue to boot from the -19 kernel until the bug is fixed, and save yourself time and trouble.

---

### Post by gerben1 on 2008-07-24
Ah okay, thank you very much.

---

### Post by kbuel on 2008-07-24
I personally wouldn't add the proposed repository to my sources.list because for the reason that they are proposed and not confirmed as working properly.

---

### Post by avtolle on 2008-07-24
> **kbuel said:**
> I personally wouldn't add the proposed repository to my sources.list because for the reason that they are proposed and not confirmed as working properly.
+1.

I'm given to understand that the proposed repository is there to allow those who are interested to aid in testing the proposed package; if this is correct, there will be instances, such as this, where there are bugs, which will then be reported and fixed. One should not enable this repository for use on a production machine where more stability is needed.

---

### Post by philinux on 2008-07-24
> **avtolle said:**
> +1.

I'm given to understand that the proposed repository is there to allow those who are interested to aid in testing the proposed package; if this is correct, there will be instances, such as this, where there are bugs, which will then be reported and fixed. One should not enable this repository for use on a production machine where more stability is needed.

++1
[https://help.ubuntu.com/community/UbuntuBackports#-backports%20vs%20-proposed/-updates/-security](https://help.ubuntu.com/community/UbuntuBackports#-backports%20vs%20-proposed/-updates/-security)

---

### Post by gerben1 on 2008-07-24
lol, okay I have turned it off 

Thanks all

(I turned it on some time ago, when I needed a package that was only in that repository.)

---

### Post by markbuntu on 2008-07-24
You should file a bug report at Launchpad. They don't read these forums much and they will never know about your problem unless you tell them. You can look at some other bug reports to get an idea of what info you should give them and you can do a search to see if someone else has the same bug and you can join that thread and reinforce and verify their report.

If you need to get something fixed, you have to tell the people who can fix it.

---

### Post by avtolle on 2008-07-24
There's already a bug report filed on Launchpad (oops, lost the link; sorry) which you could join with the details of your problem. Search the Forum (I'd try to find it but I'm already late leaving) for similar threads dealing with the kernel upgrade, and in at least two of them, the link is given. Good luck.

---

