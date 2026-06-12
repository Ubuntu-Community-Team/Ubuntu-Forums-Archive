---
title: "Live CD - will not demo or install"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by TpyKv on 2008-06-26
Good afternoon!

I have been trying to get my work colleagues to try our Hardy Heron. The first person to do so has had problems so I am keen to resolve them, just so other people are not so scared of it..

He has the official CD, on a machine with high enough specs, however when he puts the live CD, boots up, and selects "Demo" - the machine reboots and goes to the exact same page. Trying to install it does the same thing - so he cannot get anyhere.

Has anyone heard of this problem before?

Thank you for reading,

Kevin

---

### Post by Zill on 2008-06-26
Suggest checkout the CD with another PC first - it could just be a corrupted CD.

---

### Post by rockerphil on 2008-06-26
he may have downloaded a bad ISO, did he do an md5sum on it? i'd personally just redownload the ISO and burn a new install disk

---

### Post by phidia on 2008-06-26
He isn't downloading the iso.

> He has the official CD, on a machine with high enough specs, however when he puts the live CD, boots up, and selects "Demo" - the machine reboots and goes to the exact same page. Trying to install it does the same thing - so he cannot get anyhere.

Is there some type of security software set up on these computers? That might cause what you are seeing.

---

### Post by TpyKv on 2008-06-26
Thanks for the replies all!

It was the CD that Canonical send out - Ubuntu gave us loads of them - so you'd assume the MD5 would already be working - but I'll check it with him... 

It just seems to want to loop around and not actually do anything...

---

### Post by avtolle on 2008-06-26
Or, it could be a conflict with a particular graphics card, SATA drives, RAID array; there are a number of potential explanations for this. Boot paramaters might be needed, e.g., all_generic_ide to work around this problem; or, the CD (the "official" one which I presume means obtained from ship-it) may be corrupted in some way.

---

### Post by avtolle on 2008-06-26
From the boot menu, do the CD integrity check (I think it's option 4).

---

### Post by WRDN on 2008-06-26
Have you tried it on another PC, to ensure it is working?
Also, if you change the boot parameters when booting the kernel, and remove the words "quiet splash". That way, text will appear, and it will be easier to find where/ why its stopping.

---

### Post by TpyKv on 2008-06-26
there are no security issues, its a personal pc not connected to the company network...

I'm liking the all_generic_ide suggestion as well as the quiet splash one, will give it a go and post the results back...

I'm going to send my work lot the link to this forum, within minutes I've had loads of great ideas, anyone not wanting to switch to ubuntu would be foolish :) 

have a nice evening!

---

