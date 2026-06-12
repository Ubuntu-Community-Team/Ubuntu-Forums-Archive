---
title: "problem accessing directories with cd command"
date: 2014-02-13
forum: New to Ubuntu
---

### Post by devlin3 on 2014-02-13
I have ubuntu 13.10. I'm trying to get my hp laserjet p110w to sync. I have the latest version of hplip, and i'm downloading a specific driver from hpip found here: [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

when running the cd command
```
 cd desktop
```

i get
```
bash: cd: desktop: No such file or directory
```

when i attempt to run the command
```
cd downloads
```

i get
```
bash: cd: downloads: No such file or directory
```

since the installer was put in the downloads file, i ultimately need to access that through the cd command. what am i doing wrong?

---

### Post by steeldriver on 2014-02-13
**D**ownloads - Linux filenames are case sensitive

---

### Post by devlin3 on 2014-02-13
thanks. i realized just before you posted

---

### Post by Vaphell on 2014-02-13
use [tab] for suggestions and autocompletion to avoid typos entirely. It's a blessing in case of space-filled names as autocompletion escapes them.

---

### Post by asus-user on 2014-02-13
like what [**[COLOR=#000000]steeldriver[/COLOR]**]("http://ubuntuforums.org/member.php?u=1627500") said, bash is case sensitive.

a better way always to check your directory names with the command:
```
ls
```
before typing in, and use the TAB auto-completion feature to help you.

---

### Post by cogier2 on 2014-02-15
Try the following
**cd ~/Desktop**
The **~** indicates the home directory
Notice the CAPITAL "D" in desktop
**cd ~/Downloads**
or
**cd /home/**<Your sign in name>[B]/Downloads 
[/B]in my case that would be
cd /home/charlie/Downloads
There needs to be a space after cd

Hope that helps.

---

### Post by linux4me on 2014-02-15
This is a little off the folder-access topic, but if you're trying to install your HP to use HPLIP, you may not need to download anything. For HP printers, you can usually find instructions for installing in Ubuntu [here]("http://hplipopensource.com/hplip-web/models/index.html") by printer model.

You may not even need that link except to see if your printer is supported. To install it if it is supported, you can just run the following in Terminal:
```
sudo hp-setup -i
```
It has been a while since I've used it, but it usually walks you through selecting the printer via interface (USB, Wi-fi, etc.) then tells you what you need in the way of plugins and grabs them automatically.

---

### Post by Psil0cybin on 2014-02-15
> **Vaphell said:**
> use [tab] for suggestions and autocompletion to avoid typos entirely. It's a blessing in case of space-filled names as autocompletion escapes them.

thanks you just taught me something new, reading this guide. 1up

---

