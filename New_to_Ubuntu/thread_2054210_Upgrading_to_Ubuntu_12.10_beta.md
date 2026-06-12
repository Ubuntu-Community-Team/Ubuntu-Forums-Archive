---
title: "Upgrading to Ubuntu 12.10 beta"
date: 2012-09-06
forum: New to Ubuntu
---

### Post by Ninjalinux on 2012-09-06
):PSorry, I am new here and I have just recently installed Ubuntu 12.04 LTS . So today I found out that Ubuntu 12.10 Beta 1 has been released and I want to try it out and I checked in Update manager for the new version but it wasn't there. How do I upgrade to the beta?

---

### Post by sandyd on 2012-09-06
Firstly, 12.10 is a beta release, and is still full of weird bugs that may or may not affect you. The best thing to do if you want a stable system is to stay at 12.04.

Else:
Unity Dash: Type in "terminal" and open it.
Type in "update-manager 0d"

It doesnt work with the ALT key here. I dunno why. Might be a 12.10 bug.

---

### Post by Epodx64 on 2012-09-07
I'd recommend doing a fresh install of Ubuntu 12.10 Beta 1 it's not a real good idea to upgrade distros as it is and upgrading to a beta may not be well advised however if you insist on it I recommend killing X and dropping to a console and running

sudo apt-get update && sudo apt-get dist-upgrade -d (i think)

---

### Post by NikTh on 2012-09-07
> **Epodx64 said:**
> if you insist on it I recommend killing X and dropping to a console and running

sudo apt-get update && sudo apt-get dist-upgrade -d (i think)

Hello ([again]("http://ubuntuforums.org/showpost.php?p=12223009&postcount=4"))

Above commands will not upgrade the release . I suggest to read this : [http://askubuntu.com/questions/110477/how-do-i-upgrade-from-10-04-or-11-10-to-12-04](http://askubuntu.com/questions/110477/how-do-i-upgrade-from-10-04-or-11-10-to-12-04)

But neither ```
sudo do-release-upgrade
``` will upgrade the release to 12.10

cuz here we "speak" for a** beta release**

If you want to** force such upgrade** must run from terminal 

```
sudo do-release-upgrade -d
``` pass the -d parameter . -d = --devel-release .

Thanks

---

### Post by muteXe on 2012-09-07
> **sandyd said:**
> Firstly, 12.10 is a beta release, and is still full of weird bugs that may or may not affect you. The best thing to do if you want a stable system is to stay at 12.04.



If you want a stable system get 10.04.

---

### Post by zombifier25 on 2012-09-07
> **muteXe said:**
> If you want a stable system get 10.04.

That can be debated, but let's choose not to.

---

### Post by muteXe on 2012-09-07
Indeed. I realised I probably shouldn't have typed anything :)

---

### Post by Mark Phelps on 2012-09-07
Also, understand that IF you upgrade, there is no easy way to go back to what you have now.  There is no "roll back" capability.  So, if you run into problems, which you probably WILL, you will be stuck having to fix them in order to have a working system.

---

