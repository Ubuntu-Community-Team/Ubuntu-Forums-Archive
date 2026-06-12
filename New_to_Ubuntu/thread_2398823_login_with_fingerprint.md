---
title: "login with fingerprint"
date: 2018-08-17
forum: New to Ubuntu
---

### Post by nirst on 2018-08-17
Hey, I just got a new Lenovo Ideapad 530s and installed Ubuntu 18.04 on it.
It has a fingerprint scanner so I was looking for a way of logging in to my account with it instead of typing my password every time and found this: [https://help.ubuntu.com/stable/ubuntu-help/session-fingerprint.html.en](https://help.ubuntu.com/stable/ubuntu-help/session-fingerprint.html.en)

Though when I go into user settings I don't have any fingerprint option to turn on or off..
Do I need to install anything to get this option?
Thanks..

---

### Post by NM5TF on 2018-08-17
> **nirst said:**
> Hey, I just got a new Lenovo Ideapad 530s and installed Ubuntu 18.04 on it.
It has a fingerprint scanner so I was looking for a way of logging in to my account with it instead of typing my password every time and found this: [https://help.ubuntu.com/stable/ubuntu-help/session-fingerprint.html.en](https://help.ubuntu.com/stable/ubuntu-help/session-fingerprint.html.en)

[COLOR="#FF0000"]Though when I go into user settings I don't have any fingerprint option to turn on or off..[/COLOR]
Do I need to install anything to get this option?
Thanks..

the link you referenced says to go to [COLOR="#FF0000"]Activities[/COLOR] and type in Users....it does not mention user settings.....or are you calling Activities "user settings" ???

it looks like you need to install the reader first  [http://freelinuxtutorials.com/quick-tips-and-tricks/quick-tip-install-fingerprint-scanner-fprint-ubuntu-16-04-linux/]("http://freelinuxtutorials.com/quick-tips-and-tricks/quick-tip-install-fingerprint-scanner-fprint-ubuntu-16-04-linux/")  this was written for 16.04, but says it will work with 18.04

tommy

---

### Post by nirst on 2018-08-18
I open Activities type users and in that window I don't have any fingerprint options.. Only password automatic login and Last Login.

I tried running the commands from your link, the first one finished successfully but when I run the other one I get this message:
list_devices failed: No devices available

---

### Post by NM5TF on 2018-08-18
your fingerprint scanner may not be supported.....

we need to find out if it is....

run this command & see if it is listed

```
lsusb
```

the ID will be shown...see if it matches any of the following:  

```
Supported readers:
     045e:00bb    08ff:1683    08ff:2660    08ff:268f    147e:2020
     045e:00bc    08ff:1684    08ff:2680    08ff:2691    147e:3001
     045e:00bd    08ff:1685    08ff:2681    08ff:2810    1c7a:0603
     045e:00ca    08ff:1686    08ff:2682    08ff:5501
     0483:2015    08ff:1687    08ff:2683    08ff:5731
     0483:2016    08ff:1688    08ff:2684    138a:0001
     04f3:0907    08ff:1689    08ff:2685    138a:0005
     05ba:0007    08ff:168a    08ff:2686    138a:0008
     05ba:0008    08ff:168b    08ff:2687    138a:0010
     05ba:000a    08ff:168c    08ff:2688    138a:0011
     061a:0110    08ff:168d    08ff:2689    138a:0017
     08ff:1600    08ff:168e    08ff:268a    138a:0018
     08ff:1660    08ff:168f    08ff:268b    138a:0050
     08ff:1680    08ff:2500    08ff:268c    147e:1000
     08ff:1681    08ff:2550    08ff:268d    147e:1001
     08ff:1682    08ff:2580    08ff:268e    147e:2016     
     147e:1003    147e:3000
     147e:2015    147e:3001
     147e:1000    147e:2016    147e:5002
     147e:1001    147e:2020    147e:5003
     147e:1002
```

if not listed here, it won't work with Linux

tommy

---

