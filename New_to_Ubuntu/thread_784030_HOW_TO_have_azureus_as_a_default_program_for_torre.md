---
title: "HOW TO have azureus as a default program for torrents??"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by malaya on 2008-05-06
- please help me, i dont know how to use azureus to download torrents.
- after clicking 'download' in a torrent.. hardy only gives me bit torrent to use and i dont how to locate azureus.. excuse me for my english.

---

### Post by Dougie187 on 2008-05-06
Well, I can't help make it your default as my primary ubuntu box is away from me right now. But to use azureus to download your torrent files, if you right click on your torrent file you should be able to click on "Open With..." and then a box will come up, you should be able to type in "azureus" to the box and hit ok for it to open the torrent file up with azureus. Hope that helps some. I will see if I can get the default thing to work for you and let you know.

---

### Post by malaya on 2008-05-06
> **Dougie187 said:**
> Well, I can't help make it your default as my primary ubuntu box is away from me right now. But to use azureus to download your torrent files, if you right click on your torrent file you should be able to click on "Open With..." and then a box will come up, you should be able to type in "azureus" to the box and hit ok for it to open the torrent file up with azureus. Hope that helps some. I will see if I can get the default thing to work for you and let you know.

ok thanks, hmmm still want it to be the default. thanks

---

### Post by aktiwers on 2008-05-06
> **malaya said:**
> ok thanks, hmmm still want it to be the default. thanks

If you right-click on the file and pick "properties" you can then find the "open with" tab and set it as default there.

I recommend [deluge-torrent]("apt:deluge-torrent") though :)

---

### Post by malaya on 2008-05-06
> **aktiwers said:**
> If you right-click on the file and pick "properties" you can then find the "open with" tab and set it as default there.

I recommend [deluge-torrent]("apt:deluge-torrent") though :)

- is deluge-torrent better(faster) than azureus..
- hehe sorry im new to torrents

---

### Post by aktiwers on 2008-05-06
It's faster in my opinion, but you should try it.
Remember Azureus is written in Java = slow.
Deluge is written in python = fast

and the encryption is better on Deluge. But try it and make your own idea :)

---

### Post by malaya on 2008-05-06
> **aktiwers said:**
> It's faster in my opinion, but you should try it.
Remember Azureus is written in Java = slow.
Deluge is written in python = fast

and the encryption is better on Deluge. But try it and make your own idea :)

hmmm, is that so.. ok ill have deluge instead of azureus. hehe 'python' another 'new' to me.

---

### Post by Joeb454 on 2008-05-06
Python still isn't the fastest of code to execute :) I'm not 100% sure of the speed differences between Java & Python.

But I do know that Python can be quite slow to execute

---

### Post by aktiwers on 2008-05-06
> **Joeb454 said:**
> Python still isn't the fastest of code to execute :) I'm not 100% sure of the speed differences between Java & Python.

But I do know that Python can be quite slow to execute

I know.. but the whole JavaVM thing really slows things down. I wish I learned Python programming instead of Java at my school. :)

---

### Post by malaya on 2008-05-06
:confused::confused: ill just try this both and make a choice..
- hmm.. by the way if ive made my choice, how can i remove one of them??

---

### Post by shifty_powers on 2008-05-06
heh [utorrent](http://www.utorrent.com/) in wine.

don't care about the platform, utorrent is simply my favourite torrent program without exception.

Lightweight, fast and powerful :D

---

### Post by aktiwers on 2008-05-06
> **malaya said:**
> :confused::confused: ill just try this both and make a choice..
- hmm.. by the way if ive made my choice, how can i remove one of them??

Open Synaptic (System =>Administration=>Synaptic) and search for the program you want to remove. Then mark it for uninstall and apply.

Or open Terminal (applications=>accessories=>Terminal)
and type:
 ```
sudo apt-get remove <appname>
```
Where <appname> could be azureus or deluge-torrent.

---

### Post by malaya on 2008-05-06
-thanks...

---

