---
title: "How to open a link in a website!?"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by taraneyebipayan on 2013-03-07
I am new to ubuntu (unfortunately) and am trying to open a  link in a website. The link can be opened in windows but not in ubuntu  lucid. Is there any restriction in ubuntu for opening a link that may  have codes and packages to install? this is the link of the site: [http://gmplib.org/](http://gmplib.org/) and I need to click on "download benchmark sources"
  thanks

---

### Post by DuckHook on 2013-03-07
Welcome to the forums.

My memory doesn't even go back as far as Lucid, so that is your first issue. You are running a version of Ubuntu that is years out of date and no longer supported, which means that you will be wide open to whatever malicious exploits have been discovered in the intervening years. You need to install at least 12.04 (Precise).

Your inability to download may be a related issue. I can't remember if the browser version that came with Lucid will support FTP downloads. If not, then the link which you are trying to invoke will not work (it is an FTP link).

In any case, you should upgrade to a current fully supported version of the 'buntu family. If your HW is too old to run Ubuntu, try Xubuntu or the lightest of the 'buntu flavours, Lubuntu.

<edit>
Apologies. Thought for some reason that "Lucid" is "Jackalope". Don't know what came over me. Lucid is supported for one more month and runs Firefox, so FTP should definitely be supported. In which case, I'm stumped and renders original comments nonsense.
</edit>

<2nd edit>
Are you sure that it did not, in fact, download? An FTP file would simply download and would not open a new link. The file would be in your *Downloads* folder. If I recall correctly, it would also show in the footer bar at the bottom of your browser (though my recall is clearly shoddy at best).
</edit>

---

### Post by taraneyebipayan on 2013-03-07
thanks for your answer. Actually I am installing source codes for my research. during the installation it requires the site from the gmlib.org and tries to get the file but it gets nothing and will fall in a loop of trying and getting nothing. :)
I am just wondering maybe it is related to repositories ?!

---

### Post by steeldriver on 2013-03-07
If it's a browser limitation you could open a terminal and try wget

```
wget ftp://ftp.gmplib.org/pub/gmp-5.1.1/gmp-5.1.1.tar.lz
```

---

