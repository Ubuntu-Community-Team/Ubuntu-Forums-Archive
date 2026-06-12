---
title: "AWN: trying to install applets"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by m_ad on 2008-05-28
I saw some screenshots of AWN and I liked the looks of it, so I decided to give it a try.


I saw it in Applications->Add/Remove.. so I marked it for installation and clicked apply. I immediately started it, and installed some themes from the AWN website. It looks nice :)

After browsing through some of the applets that were listed, I realized that AWN could be a total replacement for the gnome panel (does anyone NOT recommend this?) I added the appropriate lines in my sources.list (through System->Administration->Software Sources, following [these instructions]("http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive")) from AWN website (I am running Hardy). From terminal, I tried
```
sudo apt-get install awn-extras-applets-trunk
```
(what does '-trunk' mean?) I got an error, 
```
Unmet dependencies. awn-extras-applets-trunk Depends: libawn0-trunk
```
so I did
```
sudo apt-get install libawn0-trunk
```
followed by
```
sudo apt-get install awn-extras-applets-trunk
```
Then, I got another error
```
Unmet dependences. awn-manager Depends: avant-window-navigator
```
Then, AWN became unusable, and Add/Remove Applications showed it as not installed. Couldn't reinstall it because of some error, I forget what. This is when I uninstalled both libawn0-trunk and awn-extras-applets-trunk and reinstalled AWN through Add/Remove Applications. Here I am now.. :lolflag:

any help on how to get applets working would be appreciated. Or if someone has a really good reason why I shouldn't even bother, I'll take that into consideration also :)

Thanks.

---

### Post by overdrank on 2008-05-28
HI and you may look here
[http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

---

### Post by m_ad on 2008-05-28
Thanks.. what are the common complaints for awn?

---

### Post by starcannon on 2008-05-28
Under Hardy it can be a bit wiggy with FF and Terminal, I solved my issues by deleting all awn config files and then resetting it up again. If this is your first awn install it may go clean for you.

---

