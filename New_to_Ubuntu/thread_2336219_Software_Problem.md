---
title: "Software Problem"
date: 2016-09-06
forum: New to Ubuntu
---

### Post by goreless on 2016-09-06
I wanted to download Google Chrome but the "Ubuntu Software" program will stick on a rotating loading icon after I double click on the .deb file for Google Chrome. I've tried to reinstall Ubuntu Software by using a command but now I get "E: Package 'software-center' has no installation candidate". I've been searching for a solution for hours, but I'm new to Ubuntu; this is only my 3rd time using it since the end of last week. I'm using Ubuntu 16.04.1 LTS

---

### Post by howefield on 2016-09-06
To install the Chrome .deb package try opening a terminal and using..

```
sudo apt install ~/Downloads/google-chrome-stable_current_amd64.deb
```

assuming that the package is in the Downloads folder and the name is google-chrome-stable_current_amd64.deb, change to suit if it isn't.

For the Software Centre problem, have you updated since installing Ubuntu ?

```
sudo apt update
```
```
sudo apt upgrade
```

---

### Post by goreless on 2016-09-06
Thank you very much! That first command installed Google Chrome for me. For the second and third command, I don't need to use them, since Chrome is installed now and I don't need to install any other software (I'm just using Ubuntu to fix laptop since I can't access WIndows) You're great!!

---

### Post by howefield on 2016-09-06
Cool, you are welcome.

---

