---
title: "problem with firefox"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by klqd on 2012-04-24
running very slow and unable to delete history etc..

tried removing firefox with apt-get remove and it said i did but when i tried to reinstall it it froze at 0% downloaded. then i tried installing thru the software centre but it said it already existed. tried removing it thru the software centre but can't because it crashes.


thanks for any help.

---

### Post by klqd on 2012-04-24
managed to reinstall firefox but it's still running v slow. not so on my macbook...

---

### Post by NikTh on 2012-04-24
> **klqd said:**
>  when i tried to reinstall it it froze at 0% downloaded. .
Hi , 
maybe something wrong with your internet connection ? I mean slow internet connection. Did you try other browser to confirm that this happened only on Firefox ? 

Try this from terminal 
```
sudo apt-get purge firefox 
sudo apt-get autoremove 
sudo apt-get install firefox
```

---

### Post by ph4nt0m117 on 2012-04-24
Its firefox.  What do you want.

---

### Post by lovinglinux on 2012-04-24
> **klqd said:**
> running very slow and unable to delete history etc..

tried removing firefox with apt-get remove and it said i did but when i tried to reinstall it it froze at 0% downloaded. then i tried installing thru the software centre but it said it already existed. tried removing it thru the software centre but can't because it crashes.


thanks for any help.

Close Firefox. Open your profile folder, located under ~/.mozilla/firefox/xxxx.default/, locate the file places.sqlite and rename it to something else. Start Firefox, open the the bookmark manager and restore a bookmark backup.

---

### Post by Peripheral Visionary on 2012-04-25
Firefox is slow on Xubu 10.04 as well. I switched to Seamonkey (compatible with most Firefox add-ons, Seamonkey is another Mozilla project based on Netscape). Seamonkey is agile and quick compared to Firefox on my Xubu Lucid box.

---

### Post by lovinglinux on 2012-04-25
> **Peripheral Visionary said:**
> Firefox is slow on Xubu 10.04 as well. I switched to Seamonkey (compatible with most Firefox add-ons, Seamonkey is another Mozilla project based on Netscape). Seamonkey is agile and quick compared to Firefox on my Xubu Lucid box.

Perhaps what you are experiencing is because your new Seamonkey installation has a clean profile. Have you tried to start Firefox with a clean profile as well?

---

### Post by Peripheral Visionary on 2012-04-25
> **lovinglinux said:**
> Perhaps what you are experiencing is because your new Seamonkey installation has a clean profile. Have you tried to start Firefox with a clean profile as well?

Good question, and the answer is yes. I did all the "speed up Firefox" things like disabling ipv6 and such, but it's still sluggish compared to Seamonkey.

I really like Midori too, except that it crashes every 6th or 7th page load on my Xubu Lucid. Perhaps it'll fly on 12.04 (hoping)!

---

