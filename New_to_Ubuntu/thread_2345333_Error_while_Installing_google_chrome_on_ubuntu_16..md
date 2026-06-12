---
title: "Error while Installing google chrome on ubuntu 16.04 LTS"
date: 2016-12-03
forum: New to Ubuntu
---

### Post by soumyarupchoudhury on 2016-12-03
I have been trying to install Google chrome the GUI way, after I download the google chrome package and open it with software center and click install it shows installing and immediately stops.I have tried multiple times but this always happens. How do I resolve this ?

---

### Post by howefield on 2016-12-03
If you are not afraid of using the terminal, load one up and use the command..

```
sudo apt install ~/Downloads/google-chrome-stable_current_amd64.deb
```

This assumes you have downloaded the chrome .deb package to your ~/Downloads folder and that the file name is google-chrome-stable_current_amd64.deb - if this isn't the case, then change to suit. You'll likely get an idea of the error, if there is any post back here.

Also if this was a new installation make sure that you are up to date with either the Update Manager or the command line..

```
sudo apt update
```
```
sudo apt upgrade
```

---

### Post by soumyarupchoudhury on 2016-12-03
Thank you for your advice. I used the command line and got it perfectly

---

### Post by howefield on 2016-12-03
> **soumyarupchoudhury said:**
> Thank you for your advice. I used the command line and got it perfectly

Cool, glad you got it. Feel free to mark the thread as solved :)

---

