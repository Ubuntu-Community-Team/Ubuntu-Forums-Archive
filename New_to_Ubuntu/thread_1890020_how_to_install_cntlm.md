---
title: "how to install cntlm"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by Wilfred Padambo on 2011-12-02
As am having difficulty to work behind proxy server because there has not been any successful method to have apt-get work in my terminal. I found something called Cntlm that can help in configuring proxy settings. Can anyone help me how to install Cntlm in ubuntu 11.10 because am a newbie to linux.
Thanks in advance.
Wilfred

---

### Post by lechien73 on 2011-12-02
You can install cntlm through the Ubuntu Software Centre. Just type:

```
cntlm
```

into the search box and you can install it from there. When you've installed it, the documentation is here: [http://sourceforge.net/apps/mediawiki/cntlm/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/cntlm/index.php?title=Main_Page)

---

### Post by Wilfred Padambo on 2011-12-03
Thanks lechien. However, Ubuntu Software Centre is not working because my proxy settings are not configured right. I can get to internet but I can't install using Terminal any application. When am using direct connection it's fine but not behind proxy server. Do you have any idea what you think I can do to get round to my problem because I can't install anything in Software Center if my proxies are not ok.
Wilfred

---

### Post by pierreyy on 2011-12-03
[http://sourceforge.net/projects/cntlm/files/](http://sourceforge.net/projects/cntlm/files/)

this is the download page for cntlm so download that and install it... this should work... good luck

---

### Post by Wilfred Padambo on 2011-12-04
Please tell me how do you install the CNTLM after downloading. I downloaded the file with .tar.gz and extracted but to actually install it am having difficulty. I know in windows you just click .exe and it installs very different with ubuntu. Please show me how to install this file. It's taking me a month now without installing anything because my terminal can't recognize my proxy server.

---

### Post by lechien73 on 2011-12-05
Ok, firstly can you tell me if you're running 32-bit or 64-bit version of Ubuntu?

You can determine this by typing:

```
uname -m
```

If it says x86_64, then you're running the 64-bit version. If it says i686, then that's the 32-bit.

To download and install the 32-bit version, click [this link]("http://sourceforge.net/projects/cntlm/files/cntlm/cntlm%200.92/cntlm_0.92_i386.deb/download").

To download and install the 64-bit version, click [this link]("http://sourceforge.net/projects/cntlm/files/cntlm/cntlm%200.92/cntlm_0.92_amd64.deb/download").

---

### Post by cuberts on 2011-12-05
> **Wilfred Padambo said:**
> Please tell me how do you install the CNTLM after downloading. I downloaded the file with .tar.gz and extracted but to actually install it am having difficulty. I know in windows you just click .exe and it installs very different with ubuntu. Please show me how to install this file. It's taking me a month now without installing anything because my terminal can't recognize my proxy server.
So this has turned into a completely different issue of opening the actual tarball file itself. In order to open it, you actually have to untar the file in linux. This link that I found should help: [http://www.pendrivelinux.com/how-to-open-a-tar-file-in-unix-or-linux/](http://www.pendrivelinux.com/how-to-open-a-tar-file-in-unix-or-linux/)

Good Luck :D

---

