---
title: "Why can't I get the latest version of Opera? Or just something newer?"
date: 2015-06-22
forum: New to Ubuntu
---

### Post by lucy5 on 2015-06-22
I recently found out that I'm using a very old version of Opera (12.16). As a web developer, I'd like to update it (especially since the only reason I use it is to test compatibility). I can't seem to get a newer version, though. Their own website redirects me to the old version when I try to download anything newer and the software centre isn't much help. Maybe I need to uninstall the version I have first? Any ideas?

Thanks.

---

### Post by wildmanne39 on 2015-06-22
I do not know, I downloaded it from here just now without issue.
[http://www.opera.com/](http://www.opera.com/)

---

### Post by Frogs Hair on 2015-06-22
You can download the most recent Chromium based version of opera 30 , but it is  very different from the Presto engine based 12.16. 
 [http://www.opera.com/computer](http://www.opera.com/computer)

The repository may already be on you system so the following may work as well. ```
sudo apt-get install opera-stable 
```

---

### Post by lucy5 on 2015-06-22
Their website just redirects me to a page to download 12.16 :( If I manually try to pick a newer version, the moment I click download it changes the page. The terminal command doesn't work either. 

This isn't a normal problem, then?

It can't be because I have an old laptop, can it? It manages just fine with the latest version of Firefox though...

---

### Post by Frogs Hair on 2015-06-22
Try selecting the latest version from the following page if you are running 64 bit. There is 32 bit version of the latest for windows but I get directed to thr 64 bit download page because that's what I'm running.

 **Edit:** 32 bit is available only in the developer version which I was using prior to the stable release.
[http://blogs.opera.com/desktop/2015/04/opera-developer-30-now-available-32-bit-linux/](http://blogs.opera.com/desktop/2015/04/opera-developer-30-now-available-32-bit-linux/)

  


 [URL="http://www.opera.com/download/guide/?os=linux-x86-64&list=all"]http://www.opera.com/download/guide/?os=linux-x86-64&list=all






[/URL]

---

### Post by lucy5 on 2015-06-22
That's what I've tried - it redirects to the 12.16 version download.

Edit - 'About this computer' says '32-bit' by 'OS type'... it's probably that, then.

Edit 2 - Right, I've downloaded the latest version of Opera Developer instead. Here's hoping it's practically the same browser.

---

### Post by leunam12 on 2015-06-23
Have you tried the ftp server? I could login anonymously with username anonymous and no password @ ftp.opera.com

---

### Post by fyfe54 on 2015-06-23
For the adventurous ones among us, try this:  [http://ftp.opera.com/pub/opera-developer/](http://ftp.opera.com/pub/opera-developer/)
I am running 32.0.1899.0

I do have to update manually as newer versions are made available.

---

### Post by CantankRus on 2015-06-23
> **fyfe54 said:**
> For the adventurous ones among us, try this:  [http://ftp.opera.com/pub/opera-developer/](http://ftp.opera.com/pub/opera-developer/)
I am running 32.0.1899.0

I do have to update manually as newer versions are made available.
You shouldn't need to update manually unless you opted out of 
adding the opera repository during install.
[ATTACH=CONFIG]262826[/ATTACH]
Check your sources....
```
software-properties-gtk --open-tab=1
```

If you did opt out you can [**_[COLOR="#B22222"]add the opera ppa[/COLOR]_**]("http://www.ubuntuupdates.org/ppa/opera").
From the ppa you can install the old opera, opera-stable, opera-beta or opera-developer.
[ATTACH=CONFIG]262827[/ATTACH]

---

### Post by monkeybrain20122 on 2015-06-24
New Opera only supports 64 bit. It sends you to the very old version because you have 32 bit OS.

---

