---
title: "Trouble Updating Packages"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by zeemanCharmz on 2012-12-18
Hallo Internet!!..
I am having problems updating my Ubuntu. I am on version 12.10. Here is a snap-shot of what its telling me.
[img]http://ubuntuforums.org/attachment.php?attachmentid=228847&stc=1&d=1355842238[/img]

So I want to know a way of eliminating this package from the update package list.
Thanx in advance!!..

---

### Post by ibjsb4 on 2012-12-18
Check this out

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=requires+installation+of+untrusted+packages&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=requires+installation+of+untrusted+packages&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by HarveyRM on 2012-12-18
try updating from terminal
```
$sudo apt-key update
$sudo apt-get update
$sudo apt-get upgrade
```

---

### Post by zeemanCharmz on 2012-12-18
Thanx [ibjsb4]("http://ubuntuforums.org/member.php?u=1729120"), let me check that out!!

---

### Post by zeemanCharmz on 2012-12-18
Oh thank you friends!!..
This is working for me!!..
```
sudo apt-get update && sudo apt-get upgrade
```
I am now downloading!!..

---

### Post by zeemanCharmz on 2012-12-18
One funny thing though is that is that I cant take a screen-shot of a window, I am only able to take a screen-shot for the whole screen as you can see from my ping image I posted. Alt+PrtSc doesnt seem to work anymore for some time now I dont remember when I first noticed. 
Do you friends have a quick solution??..

---

### Post by audiomick on 2012-12-18
Use the screen shot utility. Type "screen shot" in the dash search box and it should show up.

---

### Post by zeemanCharmz on 2012-12-18
Thanx [audiomick]("http://ubuntuforums.org/member.php?u=553389"), it worked just what I wanted!

---

### Post by audiomick on 2012-12-18
Great. Glad I could help

---

