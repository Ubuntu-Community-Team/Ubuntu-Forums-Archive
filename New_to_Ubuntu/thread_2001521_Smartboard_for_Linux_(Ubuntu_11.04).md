---
title: "Smartboard for Linux (Ubuntu 11.04)"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by digitography on 2012-06-11
I am having a doozy of a problem with the Smartboard install for Linux Ubuntu 11.04.

I have gone to the Smarttech website and downloaded the tar, extracted it, and tried to follow the instructions, which quite frankly read like Mandarin to me.

I have also searched on this forum and found another thread that says that there should be a "package" file, well I can't see that amongst the extracted files.


Any assistance would be appreciated.

---

### Post by Ampi on 2012-06-11
I am not familiar with Smartboard, but it seems like there should be *.deb packages (the so-called Debian packages) available. They should be installable with a double click [smarttech.com]("https://smarttech.com/us/Support/Browse+Support/Download+Software/Software/SMART+Notebook+collaborative+learning+software/SMART+Notebook+software/SMART+Notebook+10_3+for+Linux").

---

### Post by digitography on 2012-06-18
Thanks for the replies so far.
I have downloaded the tar file, which contains the .deb packages, quite a lot of them.
The readme tells me that I need to import the signature into GPG, what is GPG and how do I import this?
any help appreciated.

---

### Post by Ampi on 2012-06-18
It seems to be package you need to install:

"Ensure that the packages dpkg, dpkg-dev, dpkg-deb and binutils are installed. You also need GPG, md5sum, sha1sum, sha256sum and utilities like sed, cut and tr." 

There is an installation guide for the deb packages: [http://downloads01.smarttech.com/media/sitecore/en/support/product/smartnotebook/smartnotebooksoftware10linux/guides/smartnotebookinstallationadminlinuxv15jan11.pdf](http://downloads01.smarttech.com/media/sitecore/en/support/product/smartnotebook/smartnotebooksoftware10linux/guides/smartnotebookinstallationadminlinuxv15jan11.pdf). You might want to check it out, page 7.

---

### Post by digitography on 2012-06-18
Thanks for the reply.

I have got the necessary extra files installed.
My problem was that I could not understand the instructions regarding importing the signature file and signing it. The manual and readme both referred to gpg, which as I understand it has been superseded(if that is the right phrase).  Anyway I was able to import the key, and sign it with seahorse. Then I have been able to install the packages 1 by 1 using 
dpkg -i packagename.deb

The order of the install is important, as I found out, although the instructions do not give any clue as to what the correct order is.
Fairly sure I have it licked now, so many thanks to all.

Once I get this all installed  I'll blog it and post a link, because I am sure there must be others out there who would love to use Linux with their Smartboard.

---

### Post by digitography on 2012-06-25
I finally got this installed, so I wrote a blog, partly for my own reference and to assist others who may want to do the same thing.
[http://digitography.co.uk/digitographyblog/?p=449](http://digitography.co.uk/digitographyblog/?p=449)

I hope that is of help to anyone who finds it.
Many thanks as always to the Ubuntu community for assistance.

---

### Post by Ampi on 2012-06-25
Glad you succeeded and glad you wrote a blog post about, you might 'save' many frustrated lifes! :-)

---

### Post by Dbl1HandR on 2012-10-09
Thanks a million for trudging through and figuring it out. My son's school has 5 of those smart boards and i have converted the majority of the schools computers to linux. One of the big obstacles has been getting the smart boards to work on linux, it feels great to know the school will be windows free soon! Thanks so much again!

---

### Post by digitography on 2012-10-10
Thanks, I am glad you found it useful.
And yet one more nail in the windoze coffin.

---

