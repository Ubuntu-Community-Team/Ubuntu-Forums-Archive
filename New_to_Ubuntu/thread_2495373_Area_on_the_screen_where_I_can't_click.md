---
title: "Area on the screen where I can't click"
date: 2024-02-16
forum: New to Ubuntu
---

### Post by vizuetemp on 2024-02-16
Good night. I am new to using Linux. I have Ubuntu 20.04 installed on an Acer Aspire One laptop. And I have a problem. In some applications (Google Chrome, Spotify, Anydesk, for example), in the upper right area of the screen I cannot click with the mouse nor with the laptop touchpad. I've searched but haven't found any clues on what to do. Any help or guidance? Thank you so much.

---

### Post by MAFoElffen on 2024-02-17
First make sure you are runnng Xorg, becaseu the utility I am suggesting you use to help track this down does not work with Wayland... Then I would do this
```

xinput --test-xi2 --root | tee xorg-input.log.txt

```
Do what you have been doing when it doesn't work. When through, stop it via pressing keys <Cntrl><C>, then <Cntrl><D>.

Upload that file as a text attachment to your next post.

---

### Post by him610 on 2024-02-17
> Ubuntu 20.04 installed on an Acer Aspire One laptop
An Acer Aspire One (AAO) was a basic netbook powered by an Atom N270 processor, intel 945 graphics, and 1 GB RAM. Using Ubuntu 20.04 on such a limited machine may have over stressed its resources. 
Having an AAO ZG5 (Bios Date: 2008) myself, I fully well know its limitations. It is a 32bit machine and Ubuntu last 32bit release was 18.04. I have since switched to using Debian, Crunchbang++, and BunsenLabs for 32bit OS. There is also a version of Raspbian OS available for i86 (32bit)  machines.

---

### Post by ajgreeny on 2024-02-18
> **him610 said:**
> An Acer Aspire One (AAO) was a basic netbook powered by an Atom N270 processor, intel 945 graphics, and 1 GB RAM. Using Ubuntu 20.04 on such a limited machine may have over stressed its resources. 
Having an AAO ZG5 (Bios Date: 2008) myself, I fully well know its limitations. It is a 32bit machine and Ubuntu last 32bit release was 18.04. I have since switched to using Debian, Crunchbang++, and BunsenLabs for 32bit OS. There is also a version of Raspbian OS available for i86 (32bit)  machines.
+1
That sounds spot on to me!
I have a similar machine here which I used to take o holidays with me; small, light, and ran well on the earlier gnome2 versions of Ubuntu.
Now I don't bother with any of the 'buntu family as there's no 32 bit systems available so I put Debian on it using openbox only, no full DE, which makes it usable (just!) though still very slow and useless with modern web-browsers.
Try that on your machine, or perhaps something even smaller eg Puppy or Bodhisattva which you may find run better.

---

### Post by MAFoElffen on 2024-02-18
??? How is a 32bit computer running Ubuntu 20.04?

I see some had a Intel Celeron Processor N4500 CPU in them. That is 64bit...

---

