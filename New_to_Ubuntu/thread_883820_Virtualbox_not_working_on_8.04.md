---
title: "Virtualbox not working on 8.04"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by 7raTEYdCql on 2008-08-08
The virtual box that is included in the add/remove program list doesn't seem to work on ubuntu 8.04. I downloaded a deb file from the sun website and installed it. 

However i can't share any file with the guest operating system even after installing the guest additions.

---

### Post by Ryadt on 2008-08-08
To which guest operating system you want to share file with?

---

### Post by tuxxy on 2008-08-08
Did you setup your share folders in the VB's settings

---

### Post by 7raTEYdCql on 2008-08-08
I want to share it with xp. And i have setup the shared folder in settings

---

### Post by SunnyRabbiera on 2008-08-08
Well in any case the virtualbox in the repositories is a little out of date, I suggest going to the virtualbox website [http://www.virtualbox.org/](http://www.virtualbox.org/)
go to "dwonloads"
go to the link that says "binaries"
in the next page under "platform" select 8.04 for your platform (as I dont know your processor type"
agree to the terms and you should have virtualbox in no time.
it will give you a installer .deb file, installing it is very easy.
Refer to this guide:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Also keep in mind that add/remove is not usually the best way to install things in your system, its a very basic app with not many features.
A better option is to use synaptic package manager located under system > administration > synaptic package manager.

---

### Post by Ryadt on 2008-08-08
check this site
[http://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/](http://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/)

---

