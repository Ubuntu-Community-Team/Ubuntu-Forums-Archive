---
title: "Opera 9.50 weird Greek fonts rendering"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by fx55 on 2008-06-15
Hello i have a problem with greek fonts using opera 9.50 on a gnome desktop!!!Here is a screenshot of what i mean..[IMG]http://i224.photobucket.com/albums/dd85/kontziklidis/Screenshot.png[/IMG]
Any solution? Thank u very much!!!

---

### Post by the_doc on 2008-06-15
Translate via Google as it's written in Greek?!

EDIT:

Or are you saying that you have Greek fonts downloaded which aren't working?

---

### Post by fx55 on 2008-06-15
Here's a new screenshot taken on the same machine, as i see it on firefox!!!
I have the greek language pack installed
This page is greek and it should be looking like this:
[IMG]http://i224.photobucket.com/albums/dd85/kontziklidis/Screenshot-1.png[/IMG]

---

### Post by the_doc on 2008-06-15
Did it work ok in Opera before the upgrade?

---

### Post by TeoBigusGeekus on 2008-06-15
It's gotta be something with your machine/setup cause here is my screenshot

---

### Post by fx55 on 2008-06-15
I don't know because i installed it directly as Opera 9.50.
I've made some experiments with the fonts or the encoding but nothing changed!!!

---

### Post by the_doc on 2008-06-15
It's an issue with Opera 9.50 as it looks the same in mine, but Firefox rendors it ok.

---

### Post by TeoBigusGeekus on 2008-06-15
> **the_doc said:**
> It's an issue with Opera 9.50

No it's not... I also installed 9.5 from scratch and have no particular problems with font rendering.

---

### Post by the_doc on 2008-06-15
So your 9.50 rendors that page correctly?

---

### Post by TeoBigusGeekus on 2008-06-15
Yeah... See my previous post.

---

### Post by CyberAngel on 2008-06-15
I am on kubuntu Gutsy x86_64 and the font rendering looks nice for me..

---

### Post by the_doc on 2008-06-15
Sorry, missed your previous one!  Weird that FF rendors it ok but not Opera.

---

### Post by TeoBigusGeekus on 2008-06-15
It has to be something with your settings - either gnome or opera. Check the system fonts as well as opera fonts.

---

### Post by fx55 on 2008-06-15
I've removed opera 9.50, also i deleted the profile (rm -rf ~/.opera), and installed opera 9.27, which works fine but when i update to 9.50 i get the same result....bad rendering!!!

---

### Post by CyberAngel on 2008-06-15
Try to install msttcorefonts...
```
sudo apt-get install msttcorefonts
```

---

### Post by Happy_Man on 2008-06-15
My Opera also renders it absolutely beautifully.

---

### Post by fx55 on 2008-06-15
> **CyberAngel said:**
> Try to install msttcorefonts...
```
sudo apt-get install msttcorefonts
```

That worked excellent!!!
That's the sollution!!!
:KS Thanks Cyberangel!!!

---

### Post by Tomatz on 2008-06-15
edit

---

### Post by the_doc on 2008-06-15
> **CyberAngel said:**
> Try to install msttcorefonts...
```
sudo apt-get install msttcorefonts
```

That was good for me too, thanks!

---

### Post by Claus7 on 2008-07-30
Hello,

it is weird because in Dapper it works out of the box (opera 9.5 that is) without having to install anything. I just came accross this post. In case you remember it, fx55 mark your thread as solved.

Regards, &#935;&#945;&#953;&#961;&#949;&#964;&#953;&#963;&#956;&#959;&#973;&#962;!

---

### Post by CyberAngel on 2008-07-30
> **Claus7 said:**
> ...&#935;&#945;&#953;&#961;&#949;&#964;&#953;&#963;&#956;&#959;&#973;&#962;!

Many Greek people at the forum :)
hehe

---

### Post by thodoris1985 on 2008-12-23
> **CyberAngel said:**
> Many Greek people at the forum :)
hehe

+1 with me (just registered)


helpful topic! just installed ubuntu and opera and had the same problem!

thanks for the tip

---

### Post by PreDa on 2009-02-22
Worked for me as well. Thanks for the solution!!!

---

