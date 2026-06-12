---
title: "install Zotero 3.013"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by aspergerian on 2013-02-09
Zotero has released 3.0.13, which I prefer as a standalone. I downloaded from [http://download.zotero.org/standalone/3.0.13/Zotero-3.0.13_linux-x86_64.tar.bz2](http://download.zotero.org/standalone/3.0.13/Zotero-3.0.13_linux-x86_64.tar.bz2) Then I created a folder Zotero3013, into which I placed the downloaded file. Then, I used Archive Manager to unpack the file. I don't see a Read Me file and don't know how to proceed. 

An image of unpacked folder is attached.

How do I proceed so as to install Zotero 3.0.13?

---

### Post by ibjsb4 on 2013-02-09
I tried it once and didn't like it, I do have the FF version installed.

As I recall, unpacking was all that is needed and should now appear in your context menu when using your browser.

---

### Post by aspergerian on 2013-02-09
Thnx for the reply. I prefer the standalone version.

---

### Post by tgalati4 on 2013-02-09
If doubleclicking on the zotero icon doesn't bring it up, you may need to add executable privilege to it:

Open a terminal, change directory to where "zotero" is located:

```
cd
cd Downloads/Zotero3013/Zot*(tab)*
sudo chmod +x zotero
```

I just tested it, and zotero is already marked executable, so ignore the above. Just double click the *zotero* icon and it will come up.

---

### Post by ibjsb4 on 2013-02-09
If that doesn't work for you I found the zotero forums to be fast and friendly.

---

### Post by aspergerian on 2013-02-09
> **tgalati4 said:**
> I just tested it, and zotero is already marked executable, so ignore the above. Joubust double click the *zotero* icon and it will come up.

Thank you. Clicking on the Zotero icon within the unpacked folder worked.

---

### Post by aspergerian on 2013-02-10
This morning, Zotero would not open, could not find /opt/zotero/zotero.

The following seems to have worked a few minutes ago:

sudo add-apt-repository ppa:smathot/cogscinl
sudo apt-get update
sudo apt-get install zotero-standalone

Those three lines from:
[http://forums.zotero.org/discussion/25317/install-zotero-standalone-from-ubuntu-linux-mint-ppa/#Item_1](http://forums.zotero.org/discussion/25317/install-zotero-standalone-from-ubuntu-linux-mint-ppa/#Item_1)

---

