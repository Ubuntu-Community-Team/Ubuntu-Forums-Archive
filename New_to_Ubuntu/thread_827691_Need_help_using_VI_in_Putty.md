---
title: "Need help using VI in Putty"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by tuproxy on 2008-06-13
I just installed server 8.04 without the GUI and am trying to get used to vi.  I'm used to gedit and now see how spoiled I am. 

The problems that I am having are that the arrow keys don't work correctly, the backspace key doesn't work, I get strange problems with the enter button.  Oh, BTW, I'm using this through putty if that makes a difference. 

Is there another, better editor? I've heard of nano. What are the benefits to each of the editors and are there certain circumstances where one is better than the other?

---

### Post by Oldsoldier2003 on 2008-06-13
> **tuproxy said:**
> I just installed server 8.04 without the GUI and am trying to get used to vi.  I'm used to gedit and now see how spoiled I am. 

The problems that I am having are that the arrow keys don't work correctly, the backspace key doesn't work, I get strange problems with the enter button.  Oh, BTW, I'm using this through putty if that makes a difference. 

Is there another, better editor? I've heard of nano. What are the benefits to each of the editors and are there certain circumstances where one is better than the other?

Vi works better in a standard ssh session than it does in putty. Nano is more than adequate for minor edits of config files on the server.

---

### Post by brallan on 2008-06-13
nano is much more intuitive, so I'd recommend it over vi if you're not going to be spending much time at the terminal. but vi does come with a tutorial.

I think another option is pico but i've never used it.

---

### Post by Oldsoldier2003 on 2008-06-13
> **brallan said:**
> nano is much more intuitive, so I'd recommend it over vi if you're not going to be spending much time at the terminal. but vi does come with a tutorial.

I think another option is pico but i've never used it.

Nano *is* pico, or rather a close cousin of pico that is under a license that is acceptable to Ubuntu. Pico is part of PINE which is licensed in such a manner that its not acceptable for Ubuntu...

---

### Post by acidsolution on 2008-06-13
TRY using vim or if you want your vi to work well 
try installing 
```
 sudo apt-get install vim-full 
```

now try vi it should work accordingly

---

### Post by lostlinuxkiwi on 2008-06-13
why does vi work differently in putty in ubuntu to how it works in vi in fedora. I use putty to log onto a fedora box at school and vi works perfectly. Is it different versions of bash?

---

