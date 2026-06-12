---
title: "how do i install adob flash?"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by nhyrum on 2012-07-07
so i downloaded the .YUM file from adobes website, and im not finding how i install it so i can use flash. maybe i downloaded the wrong file type. i was reading things about having to log in as root, i dont know how to do that and couldnt understand how to. how do i get flash working?
 p.s.  have ubuntu

---

### Post by Cheesemill on 2012-07-07
Don't download anything from a website, just open a terminal and type:
```
sudo apt-get install flashplugin-installer
```

---

### Post by Frogs Hair on 2012-07-07
If you use Firefox search for install flash from the Ubuntu software center. The add-on at the link will also work . Ubuntu uses Debian aka .deb packages. [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) 

For media codecs and needed plugins including flash install the Ubuntu restricted extras from the software center.

---

### Post by Sigma1 on 2012-07-07
If you've installed the ubuntu-restricted-extras package, you should have flash with it, I think. In a terminal: ```
sudo apt-get install ubuntu-restricted-extras
``` Followed by your password when prompted. This will install bits and pieces enabling you to read dvds, mp3 format and use a selection of microsoft fonts, as well as flash.
There are one or two other issues with flash and firefox 13, but they don't seem to affect many of us.
One last option, if this doesn't work: install an extension called Flash Aid, via the Tools menu in Firefox, and then let it do the necessary.
Good luck.

---

### Post by nhyrum on 2012-07-09
thanks for all the help!
i do think its cool that linux(ubuntu atleast) doesnt require that you download stuff from websites.

one more question semi related, how do i get it so the "rythmbox" can play things like mp3's and such? are those included in the ubuntu restricted extras?

---

### Post by AnotherMuggle on 2012-07-09
> **nhyrum said:**
> thanks for all the help!
i do think its cool that linux(ubuntu atleast) doesnt require that you download stuff from websites.

one more question semi related, how do i get it so the "rythmbox" can play things like mp3's and such? are those included in the ubuntu restricted extras?

Yes. ubuntu-restricted-extras is one of the first things I install on a fresh installation and it covers most (all?) audio video formats you will want.

---

### Post by Frogs Hair on 2012-07-09
Yes :)

---

### Post by nhyrum on 2012-07-12
how about divx? the ubuntu restricted extras or the firefox add on didnt do that. how do i install divx?

---

### Post by alphacrucis2 on 2012-07-12
If you just want to play divx, install VLC.

---

