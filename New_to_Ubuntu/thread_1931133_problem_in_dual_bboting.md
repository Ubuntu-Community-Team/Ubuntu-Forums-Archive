---
title: "problem in dual bboting"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by ejjomi1 on 2012-02-24
i just installed ubundu on cumputer which already has windows 7. but during start up the option menu doesnt appear ,it directely goes to 7 only.please advice

---

### Post by ejjomi1 on 2012-02-24
:> **ejjomi1 said:**
> i just installed ubundu on cumputer which already has windows 7. but during start up the option menu doesnt appear ,it directely goes to 7 only.please advice

---

### Post by HeroOfCanton on 2012-02-24
You probably need to rebuild grub.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by presence1960 on 2012-02-24
I don't like probably. Let's see exactly what you have on that machine:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Boot to the desktop, come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded unzip & move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by Rubi1200 on 2012-02-25
+1 to giving us the results of the boot info script; it will help us determine the problem and enable us to offer solutions.

---

