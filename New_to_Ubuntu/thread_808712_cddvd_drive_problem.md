---
title: "cd/dvd drive problem"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by King Buttons I on 2008-05-26
I am having issues doing many things:
1) reading dvds, it reads cds ok
2) creating iso files using the cd/dvd drive, I was able to do this at one time
3) when I start computer it has four different cd/dvd drives listed but I only have two drives attached.
Can anyone help me? I am running ubuntu feisty. And have all the multimedia packages that are needed installed.
Buttons

---

### Post by Sarah L on 2008-05-27
Okay, let's go through this one step at a time:

1) Many commercial DVDs are encrypted and the decryption keys are not "free", unrestricted software -- thus they don't come pre-installed in ubuntu. To gain access to these "nonfree" features, run this command in a terminal: ```
sudo apt-get install ubuntu-restricted-extras
```

2) There are command line utilities that can easily create .iso files for you; however there are also nice GUI available :)
Try out k3b: ```
sudo apt-get install k3b
```

3) Sometimes the directories listed under /media/ are just links; figure out which ones point to which drives and you should be okay.

Hope this helps,
Sarah

---

### Post by King Buttons I on 2008-05-28
Ubuntu-restricted-extras is already installed and it does not read any dvds.
k3b is a KDE program, will it still run even though I am running gnome. And once I find out which links in media point to where to I just delete them.
BUttons

---

