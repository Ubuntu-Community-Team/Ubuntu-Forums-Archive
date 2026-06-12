---
title: "secure webdav function absent in hardy"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by ymp on 2008-04-28
i've just upgraded to hardy from 7.10 and I can no longer connect to my organizations server,
i cannot find any option for connecting to secure webdavs in hardy under places> connect to server
how can i get this function working again?

---

### Post by bug80 on 2008-04-30
I have the same problem. Would like to have a solution too :(

---

### Post by HotShotDJ on 2008-05-02
I hate just "me too"-ing, but me too.  No amount of googling has enlightened me on this one.

---

### Post by amukherj on 2008-05-06
Yes, I am having the same problem. I am sure that in Gutsy it did work.

---

### Post by Conan on 2008-05-06
Yeah, I'd really like to be able to use my Shackspace via webdav, too. Workgred great with 7.10, but can't do it on Hardy.

---

### Post by timcredible on 2008-05-06
have you tried using davs://<server> in nautilus?

---

### Post by ymp on 2008-05-06
yes, I have tried using the davs://, but that does not work as no id or pw dialog appears and I just get refused, tried all types of entries into custom too, same problem, the dialog in 7.10 did work well, but is absent in 8.04

---

### Post by HotShotDJ on 2008-05-06
I found a bug that has been filed: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/222532](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/222532)

So, this is a known issue.

---

### Post by Marlou on 2008-05-06
Hello,
I have the same problem than you and I confirm that with the 7.10 version of Ubuntu, the  secure or not  webdav work very well. To be clear only unsecure webdav works with hardy.
After some researches on internet, I have found lot of things but three tools seem good: davfs2, fusedav, cadaver
After lot of tests on each, I just arrived to use correctly cadaver and it works very well. You must know that cadaver should be used in command line almost exactly like ftp.
I hope that the Ubuntu developer will fix this problem of nautilus soon!!!

---

### Post by bug80 on 2008-05-14
In the meantime I use konqueror to transfer files using secure WebDAV, but I hope this gets fixed soon.

---

### Post by GumbyX on 2008-06-17
You guys can add me to the list. I needs webdavs to access my network drive on campus. I don't really want to install konqueror just for that, but looks like I may have to. I am having issues connecting to webdavs through nautilus manually.

Here's hoping it gets fixed soon.

---

### Post by bug80 on 2008-10-14
> **GumbyX said:**
> Here's hoping it gets fixed soon.
...and we're still waiting :(

I wonder what the problem is...

---

### Post by zerubbabel on 2008-10-15
Does anyone know whether this bug is fixed in Intrepid (8.10) ??

---

### Post by AFarris01 on 2008-11-08
I would very much like an answer to this as well...

I've just recently been given the duty/privilege of acting as webmaster for part of my school's website, which can be accessed through webDAV, unfortunately, it also requites a login, which the 'connect to server' tool does not seem capable of handling, for some odd reason.

I've setteled for now using davfs2 which seems to work ok, but i'd sure love to be able to use the nice GUI tool to accomplish this...

[EDIT]
I just checked my Intrepid LiveCD, and no, this feature is not present in Intrepid either.... what the heck?

---

### Post by VvWolverinevV on 2008-11-09
> **bug80 said:**
> In the meantime I use konqueror to transfer files using secure WebDAV, but I hope this gets fixed soon.

It seems like Dolphin doesn't have an option for davs:// either.  How did you get it to work?

---

### Post by sixfthick on 2008-11-11
I've had success with the following.. 

Open 'Connect to Server' and choose..

Connection Type: Custom Location
Location (URI): davs://...

Using 'davs' instead of 'webdavs' seems to work.

Hope this helps

---

### Post by AFarris01 on 2008-11-12
to get this to work to me i followed the instructions found here:

[http://www.howtoforge.org/davfs_ubuntu]("http://www.howtoforge.org/davfs_ubuntu")

basically just install the davfs2 package, add a line in the /etc/fstab file, and mount from a terminal...though i made a little launcher to do the mounting for me...

the only thing i encountered was after the initial mount, the username and group (lines 16 & 18 ) in the ~/.davfs2/davfs2.conf file didnt get set properly when i did the 'dpkg reconfigure'  and the fix on the website didnt work for me.  however, commenting the lines out of the config file makes it work like a charm.

the other methods to mount the server, such as using the 'custom connection' in the "Connect to Server..." tool, and entering the address into a nautilus/konqueror window did not work for me. :(

---

