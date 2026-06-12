---
title: "Ubuntu 20.04 can't install Chrome - File Not Supported"
date: 2020-06-29
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2020-06-29
Hi Guys,

After being away from Linux for about a year, I downloaded the latest LTS version of Ubuntu to a USB drive and installed it on a decent computer I had in the basement.
When I try to install file:///home/john/Downloads/google-chrome-stable_current_amd64.deb I get a strange error message that I have never seen before. I am told the file is not supported. 
Now the truly weird part; Google chrome does seem to be installed as I can launch it.

Any ideas?
Has anyone else seen this happen?

GG

---

### Post by ActionParsnip on 2020-06-29
Run:
```
 
sudo dpkg -i /home/john/Downloads/google-chrome-stable_current_amd64.deb
sudo apt-get -f install

```

Should do it

---

### Post by GrouchyGaijin on 2020-06-30
Thank you - any idea **why** I received the file not supported message?
Other deb files, such as Steam, installed without incident.

/GG

---

### Post by ActionParsnip on 2020-07-02
Not sure myself. I don't use gdebi and install all packages in CLI as well as do nearly everything in CLI
Maybe others can advise.

---

### Post by GrouchyGaijin on 2020-07-04
I did not find a solution, but I did notice that despite the error message Chrome was actually installed. When I press the Windows key to bring up the list of installed applications and started typing Chrome it appeared in my list of installed applications. By the way, I received the uninstallable error message when I tried to install Chrome via the command line as well.

---

### Post by ramxan87 on 2021-03-14
Thanks, GG.

I am new to  Ubuntu... Actually to Linux.

Thanks Again, 
Zan

---

### Post by grahammechanical on 2021-03-14
This link gives two methods for installing the chrome web browser. The second method has always worked for me.

[https://www.omgubuntu.co.uk/how-to-install-google-chrome-on-ubuntu](https://www.omgubuntu.co.uk/how-to-install-google-chrome-on-ubuntu)

Regards

---

### Post by asemabdo on 2021-04-04
The second method has worked with me too..
Thanks Alot!

---

### Post by ActionParsnip on 2021-04-04
Please mark as solved if this is no longer an issue

---

### Post by bluegirlfan on 2021-08-10
The same error occurred when I requested to download the .deb file from the official Google Chrome site. Instead of saving the file, I chose "Open with: Software install" (this is selected by default). It seems that the software installer doesn't know how to process temp files. If you save it first, it works.

---

