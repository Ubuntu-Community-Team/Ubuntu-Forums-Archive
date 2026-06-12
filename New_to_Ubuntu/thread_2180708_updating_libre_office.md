---
title: "updating libre office"
date: 2013-10-14
forum: New to Ubuntu
---

### Post by zaanta2 on 2013-10-14
Hi,
jsut installed 12.04....totally happy!
Just curious: I have used Libre Office for some time - even on my old w8 os - and I notice the one that comes with ubuntu is Libre Office 3.
Now there's Libre Office 4, which has been out for some time......How can I update to that? Or should I just go to their site & download like I would on w8?
Many thanks,
david
Sorry, 1 more thing: I built a website on w8 & now with Ubuntu it all looks a little different? Is that normal?

---

### Post by harrypotter7 on 2013-10-14
sudo add-apt-repository ppa:libreoffice/libreoffice-4-0
sudo apt-get update
sudo apt-get dist-upgrade

use that in terminal but i wont suggest u updating or adding ppa's even though it is highly stable........

---

### Post by zaanta2 on 2013-10-14
Hmmmm. OK, thanks.
Re your message about my site - perhaps I should have been more clear_
I built a site using Page Plus on my w8 os (Page Plus is of course exclusive to MS!!)
Everythng looked fine - I was using Firefox (as I am now)
I just took a look at it after I changed to Ubuntu and there is text missing and it's as if the page isn't big enough sometimes???
any ideas?

---

### Post by grahammechanical on 2013-10-14
Your web site would have used Windows fonts. May be. Which Ubuntu does not have as a default. Did you put in the CSS file alternative fonts or generic fonts? Also the character encoding may be a Windows encoding - Western (Windows-1252) and not Unicode (UTF-8).

Regards.

---

### Post by harrypotter7 on 2013-10-14
If fonts is ur problem search for ms core fonts in software center..........

---

