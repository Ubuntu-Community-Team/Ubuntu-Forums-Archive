---
title: "keyboard problems"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by ozbolt on 2008-07-29
I was using my home-town slovenian keyboard configuration, but it got blown up and now... OMG
QWERTZ still works (instead QWERTY, witch we don't use), and most of other options, but some of others like j ; &#269; ; ž ; š ; @ and some others.
I went into preferences -> keyboard but there is nothing I can do. I think somethinge in here is wrong and how can I fix this.
And the picture:
[[img]http://shrani.si/t/2L/kL/gkGsGrE/screenshot.jpg[/img]](http://shrani.si/?2L/kL/gkGsGrE/screenshot.png)

---

### Post by Het Irv on 2008-07-29
You can try editing your xorg.conf file,

```
gksudo gedit /etc/X11/xorg.conf
```

In the part that has the keyboard configuration there should be a line that says ```
Option		"XkbLayout"	"us"
```
Try changing the us to your countries two letter code.  That might fix your problem.

---

### Post by ozbolt on 2008-07-29
Doesn't work, becouse the two letters (si in this case) are already at place. Is there posibility that cause for this is installing and configuring VirtualBox?

---

### Post by ozbolt on 2008-07-29
Anybody?

---

### Post by ozbolt on 2008-07-29
I am sorry for spamming, but I really need this to work, so if any idea rather then reinstall ubuntu is in place I would be thrilled to hear it.

---

### Post by ozbolt on 2008-07-29
Ok, I am spamming again but i figured out somethinge.
For everyone: The only thing to do is to run this:
```
sudo xmodmap /usr/share/xmodmap/xmodmap.uk
```
And change last two letters into what you need for your language. Well this is second time I saved somethinge whitout help of yours so congrats to me:).

---

### Post by Het Irv on 2008-07-30
Sorry about that ozbolt, had get offline.  Glad you got it fixed.  Please mark your thread as solved, so that others can benifit from this thread.

---

### Post by agave on 2008-08-11
Great, thank you.

What are we doing with that command? I like to know what I do :)

Is there a way to have this as a permanent solution, without having to do the terminal command every time?

I tried with sessions putting the command you give us, but it will not work starting the session.

Thank you again.

update: I took away the sudo before the command line in session startup script and it worked.

---

