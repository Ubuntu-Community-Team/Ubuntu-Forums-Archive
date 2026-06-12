---
title: "Virtual Moon Atlas Installation?"
date: 2015-05-10
forum: New to Ubuntu
---

### Post by Daveski17 on 2015-05-10
Hello, I downloaded and unzipped the tar and ran the Terminal commands as directed on the site.

[http://www.ap-i.net/avl/en/download](http://www.ap-i.net/avl/en/download)

tar xf virtualmoon-6.0-linux.tar

sudo ./vmapro_install.sh

[ATTACH=CONFIG]261906[/ATTACH]

It asks me to select the installation directory. Do I have to make one?

Thanks

---

### Post by sandyd on 2015-05-10
Most likely you won't have to.

I suggest using a separate folder (e.x. /opt/virtualmoon or /usr/local/virtualmoon), as installing into /usr/local makes it extremely complicated and difficult to remove if you have to. It can also accidentally replace files with the same name when installing into /usr/local

---

### Post by Daveski17 on 2015-05-11
> **sandyd said:**
> Most likely you won't have to.

I suggest using a separate folder (e.x. /opt/virtualmoon or /usr/local/virtualmoon), as installing into /usr/local makes it extremely complicated and difficult to remove if you have to. It can also accidentally replace files with the same name when installing into /usr/local

OK, thanks for your reply. I installed Cartes du Ciel (an astronomical program from the same site) and it runs fine. I don't seem to be able to enter my sudo password now. I suspect some borking as this is my old notebook. :(

---

### Post by oatcruncher on 2015-09-25
Hi all, updating this thread. I've got exactly the same problem, and am new to Ubuntu/Linux. I think I've tried just about every combination of commands I can think of to make this work but no go. Has something changed in the latest version of Ubuntu to stop this working, or is it just me?When I (successfully) installed it to usr/local: Prog (when asked) I then tried running it as instructed with export LD_LIBRARY_PATH=Prog/lib && Prog/bin/atlun I get various errors, but mainly Could not load library libvma404.so Please try to reinstall the program. This is absolutely driving me mad, particularly when I was able to install it on Windows7 without a hitch. Here's the download page: [http://www.ap-i.net/avl/en/download](http://www.ap-i.net/avl/en/download). Any help for a beginner appreciated, and I will answer any questions as soon as I find them. Cheers 
Max

---

### Post by Daveski17 on 2015-10-11
> **oatcruncher said:**
> Hi all, updating this thread. I've got exactly the same problem, and am new to Ubuntu/Linux. I think I've tried just about every combination of commands I can think of to make this work but no go. Has something changed in the latest version of Ubuntu to stop this working, or is it just me?When I (successfully) installed it to usr/local: Prog (when asked) I then tried running it as instructed with export LD_LIBRARY_PATH=Prog/lib && Prog/bin/atlun I get various errors, but mainly Could not load library libvma404.so Please try to reinstall the program. This is absolutely driving me mad, particularly when I was able to install it on Windows7 without a hitch. Here's the download page: [http://www.ap-i.net/avl/en/download](http://www.ap-i.net/avl/en/download). Any help for a beginner appreciated, and I will answer any questions as soon as I find them. Cheers 
Max

Apparently it can be installed on Mint without any problems.

---

### Post by aturnwald on 2016-02-07
Hello to all,
I've got exact the same trouble, right now I'm using UBUNTU 16.04 and it crashed, with the error libvma404.so is missing. But it's right there where it is.
But, when I open it via Terminal, it works, just enter ./atlun and that's all

cheerio Toni

---

