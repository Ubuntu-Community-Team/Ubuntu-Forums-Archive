---
title: "How to downgrade to firefox 2?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by rainbowgabs on 2008-05-06
Hi everyone!
Can somebody please help me with a step by step guide on how to downgrade from firefox 3 beta 5 to firefox 2? I'm having way too many problems with it, like 
1. I'll start my computer and the first application I run is firefox (there's nothing else running) and it does that thing like it's going to open but then it doesn't.  :( Then it tells me there's another firefox window opened and I should close it or restart my computer.  

2.The screen goes all grey for no apparent reason and I have to restart just firefox.  

3. I don't know if this is related or not to firefox actually but if I open youtube and watch a video then none of my music players work.  And viceversa if I first listen to music on either amarok, totem, rhytmbox and close it and then try to watch a video it doesn't work.

Thanx y'all.  I know there's info on the downgrading in the forums, I just don't understand it.  That's why a super beginner style step by step guide would be greatly appreciated.

---

### Post by ChompTheMan on 2008-05-06
Open up a terminal(Applications &#8594; Accessories &#8594; Terminal) and type this in:

```
 sudo apt-get remove firefox-3.0 && sudo apt-get update && sudo apt-get install firefox-2
```

then hit enter.  It will ask you for your password.  Type it in and hit enter.

---

### Post by Diki on 2008-05-06
Open up Terminal and paste this in:

```
sudo apt-get remove firefox-3.0 && sudo apt-get update && sudo apt-get install firefox-2
```

---

### Post by rainbowgabs on 2008-05-06
YAY! That's what I'm talking about!! Thank you both SO much!!
Of course now that I'm back to v2 I miss the awesome features of the v3, but I'll wait for a more stable release. Thanx again!!!

---

### Post by marty1011 on 2008-05-06
> **rainbowgabs said:**
> YAY! That's what I'm talking about!! Thank you both SO much!!
Of course now that I'm back to v2 I miss the awesome features of the v3, but I'll wait for a more stable release. Thanx again!!!
Has it fixed the problem with the music players because, I am having the same problem.

---

### Post by vradovic on 2008-05-07
Thanks a lot. Now i can use GSPACE.

---

### Post by gn2 on 2008-05-07
Remember to lock Firefox 3 so it doesn't re-install.

Link in my sig.

---

### Post by miwaypet on 2008-05-07
Why downgrade? You will just have to reinstall it when the final comes out in June. Why not install Swift Weasel. Get it here: [ttp://sourceforge.net/project/showfiles.php?group_id=195473]("ttp://sourceforge.net/project/showfiles.php?group_id=195473")

Find out what your processor type is with SysInfo. Go to add/remove>show:all available applications>Search: hardware.

Select SysInfo from the list and install it. Find it in Applications>System Tools>SysInfo

With the info you can dowload the swift weasel for your box and all your FF add-ons will work with it.

Hope this helps.

---

### Post by angry_johnnie on 2008-05-08
[Here]("http://ubuntuforums.org/showthread.php?t=784628") is a workaround to make sure that extensions and add-ons work in FF2.

---

### Post by gn2 on 2008-05-08
> **angry_johnnie said:**
> [Here]("http://ubuntuforums.org/showthread.php?t=784628") is a workaround to make sure that extensions and add-ons work in FF2.

There is also the option of disabling the version check for add-ons and the Nightly Tester Tools to make FF2 add-ons work in FF3, however even using them not all FF2 add-ons will work with FF3.

---

