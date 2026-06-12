---
title: "[Tutorial] Zend Studio 5.5 on Jaunty"
date: 2009-05-31
forum: Outdated Tutorials &amp; Tips
---

### Post by MadnessRed on 2009-05-31
I have Zend Studio and the installer by default doesn't work so here is how I got it to work for me.

Download the Zend Installer from the Zend Website
[http://www.zend.com/products/studio/downloads-prev](http://www.zend.com/products/studio/downloads-prev) Obviously you want Studio 5.5 and Linux version.

For ease of use downlaod to the "Home" folder. It really doesn't matter where but home folder makes the rest a lot easier.

Right click on the tar.gzfile you downloaded and select extract here.

Now we do the terminal stuff. So open terminal, and enter.
```
cp ZendStudio5_5_1.bin ZendStudio5_5_1.bak
``` This jsut makes a backup.

```
cat ZendStudio5_5_1.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > ZendStudio5_5_1.bin
``` Do our magic to make the installer work.

```
rm ZendStudio5_5_1.bak
``` Remove the backup.

Now we just need to run the install
```
./ZendStudio5_5_1.bin
```

Install it were you like, how you like.

You can run it From {Home}/ZendStudio-5.5.1/Zend_Development_Environment

Now when it runs it may just be a grey screen, if it is don't panick. Zned have posted their own sollutions which I have tested and it works. Link below
[http://www.zend.com/support/knowledgebase.php?kbid=241]("http://www.zend.com/support/knowledgebase.php?kbid=241")

---

