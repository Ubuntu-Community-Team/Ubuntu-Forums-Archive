---
title: "phone card problem"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by xieu90 on 2008-09-12
hi everyone
I have a phone and it has a memory card. normally I just connect my phonet o computer and can share/delete and do anything with things inside the card
but this time i can not do anything with it. and when ubuntu recognize my phone card it open rythmbox music player and use up 100% of my CPU
it is a bit strange for me I wonder if it is because I am using hardy 

my problem is: how can i delete and copy things to my phone card ?
I use tricks like in this link
[http://ubuntuforums.org/showthread.php?t=851923](http://ubuntuforums.org/showthread.php?t=851923)
but it wont work.

---

### Post by DFlame on 2008-09-12
Looks like the permissions are shot. You need read-write access and for the files to belong to you.

Open the terminal and type this command:

```
sudo chown -hR yourusername:yourusername /media/PHONE\ CARD/
```

Substitute "yourusername" with your username in both places (dont forget the colon in the middle) and enter your password when asked.

You should then be able to access the files normally. No promises though, I'm fairly new myself.

EDIT: You may have to open the permissions normally afterwards and specify read/write access for yourself

DFlame

---

### Post by xieu90 on 2008-09-12
it doesnt work

---

### Post by DFlame on 2008-09-12
Bit of a long shot, but is there a lock switch on the memory card in question? It may have been slipped into the lock or read only position resulting in the problem. Slide it back if there is and try accessing it normally again.

DFlame

---

### Post by philinux on 2008-09-12
Try using 

```
gksudo  nautilus

```
Use the command from the terminal.

Browse to the folder as before and see if you can change the permissions.

---

### Post by xieu90 on 2008-09-12
it doesnt work, 
i cannot find any lock or anything on that card (MS2 [http://base1.googlehosted.com/base_media?q=http://www.bestpriceaudiovideo.com/img/items/120066655036796400.jpg&size=2&dhm=1bde8783&hl=en](http://base1.googlehosted.com/base_media?q=http://www.bestpriceaudiovideo.com/img/items/120066655036796400.jpg&size=2&dhm=1bde8783&hl=en) )

well even in windows i can not format the card and ting goes strange even with my computer when i try to del/copy/ format. windows/my computer wants to freeze 

what can be the problem ?

---

