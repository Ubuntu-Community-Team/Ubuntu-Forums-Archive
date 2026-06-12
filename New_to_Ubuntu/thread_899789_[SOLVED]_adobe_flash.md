---
title: "[SOLVED] adobe flash"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-08-24
okay, so I'm surfing the net and end up on youtube, and it says to get latest flash player, So I click on the link, download, the .gz file, but now I am stuck as to what to do now... Help?

THANK YOU!:KS

---

### Post by nothingspecial on 2008-08-24
Click on Accessories > Terminal and copy and paste -

```
sudo apt-get install flashplugin-nonfree
```

Type your password - you wont see it

Restart fire fox.

---

### Post by tuxxy on 2008-08-24
Or you could install the ubuntu-restrcited-extras package, this will include flash, mp3, dvd playback etc

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Search for ubuntu-restrcited-extras in synaptic or open a terminal and type

```
sudo apt-get install ubuntu-restrcited-extras
```

---

### Post by Joeb454 on 2008-08-24
I think [ubuntu-restricted-extras]("apt://ubuntu-restricted-extras") may be a little over kill if the user only wants [flash]("apt://flashplugin-nonfree") ;)

I love apt links :D

---

### Post by hyperhopper on 2008-08-24
I have restricted-exrtas already... hmmm.... Ill try what nothing special says

---

### Post by hyperhopper on 2008-08-24
uh oh, i got this
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by nothingspecial on 2008-08-24
Do what it says - in your terminal type
```

dpkg --configure -a
```

---

### Post by hyperhopper on 2008-08-24
dpkg: requested operation requires superuser privilege

is what i got, but im on the account i created with all privledges during installation of ubuntu from liveCD

---

### Post by tuxxy on 2008-08-24
> **Joeb454 said:**
> I think [ubuntu-restricted-extras]("apt://ubuntu-restricted-extras") may be a little over kill if the user only wants [flash]("apt://flashplugin-nonfree") ;)

I love apt links :D

Im sure he would want dvd, mp3 playback at some point

ye apt links are good for the lazy ;)

---

### Post by hyperhopper on 2008-08-24
> **tuxxy said:**
> Im sure he would want dvd, mp3 playback at some point

ye apt links are good for the lazy ;)

Yes, I will need those at some point, and what is an apt link?

---

### Post by nothingspecial on 2008-08-24
> **hyperhopper said:**
> dpkg: requested operation requires superuser privilege

is what i got, but im on the account i created with all privledges during installation of ubuntu from liveCD

Then you gotta sudo it 
```

sudo dpkg --configure -a
```

---

### Post by tdrusk on 2008-08-24
> **hyperhopper said:**
> dpkg: requested operation requires superuser privilege

is what i got, but im on the account i created with all privledges during installation of ubuntu from liveCD
```
sudo dpkg --configure -a
```

EDIT: nothingspecial beat me to it.

---

### Post by hyperhopper on 2008-08-24
WOOW two post in less than 30 secs from my post. Scary!!!

---

### Post by Joeb454 on 2008-08-24
You'll get used to it ;)

---

### Post by nothingspecial on 2008-08-24
Then you`ll wait for weeks for a simple problem to be resolved.

And then some obscure problem with some obscure hardware only you and 10 other people in the world own will be fixed in about four and a half minutes - it`s the way it works.\\:D/

---

### Post by hyperhopper on 2008-08-25
> **nothingspecial said:**
> Then you`ll wait for weeks for a simple problem to be resolved.

And then some obscure problem with some obscure hardware only you and 10 other people in the world own will be fixed in about four and a half minutes - it`s the way it works.\\:D/


I disagree on that, Ill show you my internetless games problem thread that ill bump in a second because nobody knows....

but as to the original problem,.... it just said it couldn't retrieve archives, after 7 hours of loading, and now, after i closed the terminal, my copy and paste decided to reset on me so i don't have the exact message...

---

### Post by nothingspecial on 2008-08-25
> **hyperhopper said:**
> I disagree on that, Ill show you my internetless games problem thread that ill bump in a second because nobody knows....
That`s just what I`m saying. Sometimes these forums are amazing, sometimes thet`re sooo frustrating.

> **hyperhopper said:**
> but as to the original problem,.... it just said it couldn't retrieve archives, after 7 hours of loading, and now, after i closed the terminal, my copy and paste decided to reset on me so i don't have the exact message...

It sounds like you have some broken packages. This is beyond my scope but check  that you didn`t have another package manager open at the same time - synaptic, add/remove, (I think software sources also).

If that doesn`t help I`m just happy to bump your thread. :?

---

