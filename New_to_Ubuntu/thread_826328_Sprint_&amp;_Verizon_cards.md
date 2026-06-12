---
title: "Sprint &amp; Verizon cards"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Reddoug on 2008-06-11
Hi all.

   I am new to Unbuntu. I have 2 questions. First, does Unbuntu support Sprint & Verizon wireless PCMCIA cards? Am thinking about installing on a laptop. 
   Second is, I am not able to update my ClamAV. It says I have to be logged in as root. I am set up as the Administrator. I tried to enable root in authorizations but that did not help. Any suggestions.

Thanks, Doug

---

### Post by Het Irv on 2008-06-11
1. Not sure

2. Try using ```
gksudo clamav
```

Sudo (or gksudo) elevates the current user to root privileges temporarily.  Its done like that as a security feature.

---

### Post by NetworkGuy on 2008-06-11
Verizon and Sprint Wireless Internet cards are supported in the kernel.  After loading a usbserial module, and creating a couple of files you can get it working.   Look here: [http://kenkinder.com/evdo-pc5740/](http://kenkinder.com/evdo-pc5740/)    This should work for even the newer cards since I actually have a 5750.

Be warned that you must activate the card in windows since the client unlocks the cards and sets it up for first time use.  After that, you are good to go for using it in Linux.   Some people do report less speed in Linux than Windows however.

---

### Post by Reddoug on 2008-06-11
Thanks for the quick reply's. I was able to update my ClamAV.  Will have to try the Sprint card.

Thanks,  Doug

---

