---
title: "Questions about Ubuntu's default HOME folder encryption"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by venom104 on 2011-11-19
I have a few questions about ubuntu's home folder encryption. In case you don't know what I'm talking about; I'm talking about the default encryption method used when you INSTALL ubuntu and the installer ASKs wither or not you would like to encrypt your home folder.

Question 1) What type of encryption is used; can I chance the encryption method?

Question 2) How can I encrypt my home folder in case I didn't select it at install time; how can I encrypt NEW users that I add to my system.

Question 3) I would like to encrypt my ENTIRE hard drive partition. Is the default encryption method capable of doing this, if so how? If not, would I need to use a program like truecrypt? If so, what's the best one to use for newbies?

Sorry for all the questions but I didn't really know what to type in under a terminal session as a parameter to man.

---

### Post by Miljet on 2011-11-19
Sorry I don't use encryption and can't help with your questions but your last comment led me to introduce you to the apropos command. When you are looking for a command, but are not sure what to search for, you can open a terminal and enter "apropos whatever-you-are-looking-for" and it will return any matching commands.

"apropos encryption" returns one entry called gpg. You can then do man gpg. Or for example the following:
```
jack@jack-laptop:~$ apropos browser
aa-update-browser (8) - update browser profiles with browser abstractions
charmap (1)          - Unicode character picker and font browser
chromium-browser (1) - the web browser from Google
firefox (1)          - a free and open source web browser from Mozilla
gnome-character-map (1) - Unicode character picker and font browser
gucharmap (1)        - Unicode character picker and font browser
infobrowser (1)      - read Info documents
libsmbclient (7)     - An extension library for browsers and that can be use...
sensible-browser (1) - sensible editing, paging, and web browsing
viewres (1)          - graphical class browser for Xt
jack@jack-laptop:~$ 

```

Really a pretty neat command.

---

### Post by tartalo on 2011-11-19
[http://www.linux-mag.com/id/7568/](http://www.linux-mag.com/id/7568/)

---

