---
title: "Chromium Form Recovery"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by TooFreppaT on 2013-06-24
I wrote a lengthy post and submit but I lost it, I can't see it anywhere and it's gone. But while I was typing I noticed a little yellow "Auto-Save" feature so I'm hoping it was Chromium saving it somewhere I can get it now, Firefox also has the little yellow "Auto-Save".

I haven't closed Chromium or Firefox.

---

### Post by MidnightGrey on 2013-06-24
your lengthy post is most definitely lost in the ether.

---

### Post by TooFreppaT on 2013-06-24
But I found this [http://superuser.com/questions/236390/how-do-i-recover-a-form-in-firefox-without-installing-a-plugin](http://superuser.com/questions/236390/how-do-i-recover-a-form-in-firefox-without-installing-a-plugin) but it's for Firefox and I don't understand where to start.

---

### Post by Bashing-om on 2013-06-24
[COLOR=#000000]TooFreppaT; Hey !

If you are in reference to  submitting a post on this form to the "little yellow auto-save".
Try this:
Quick links (top of forum) -> find all my post -> Do you see your post ? -> open it -> choose  reply (hopefully your post opens) -> click on lower left yellow "restore file" or some such.
[/COLOR][INDENT=2][COLOR=#000000]
saved my efforts more than once

[/COLOR][/INDENT]

---

### Post by TooFreppaT on 2013-06-24
I already tried that and couldn't find it after I submitted I couldn't find it anywhere.

---

### Post by Bashing-om on 2013-06-24
[COLOR=#000000]TooFreppaT;
Not good !.. ok Have you tried "advanced search"; search on your login_name ? See what it returns .
[/COLOR][INDENT=3][COLOR=#000000]
good luck

[/COLOR][/INDENT]

---

### Post by TooFreppaT on 2013-06-24
No it's definitely gone. Is there a chance this will work for Chromium? [http://superuser.com/questions/236390/how-do-i-recover-a-form-in-firefox-without-installing-a-plugin](http://superuser.com/questions/236390/how-do-i-recover-a-form-in-firefox-without-installing-a-plugin)
I found gdb already installed but can't find the gcore utility, it isn't even in the Ubuntu Software Center.

---

### Post by Bashing-om on 2013-06-25
[COLOR=#000000]TooFreppaT;
Sorry, I also draw a null on "gcore' ...Over my level perhaps one of the real gurus here will pick up on this thread and offer a shred of hope.
[/COLOR][INDENT][COLOR=#000000]
good luck

[/COLOR][/INDENT]

---

### Post by TooFreppaT on 2013-06-25
I tried ```
ps -e | grep chromium
``` and my result was ```
 3691 ?        00:15:34 chromium-browse
 3695 ?        00:00:07 chromium-browse
 3696 ?        00:00:00 chromium-browse
 3697 ?        00:00:00 chromium-browse
 3701 ?        00:00:00 chromium-browse
 3738 ?        00:01:18 chromium-browse
 3746 ?        00:00:00 chromium-browse
 6040 ?        00:00:04 chromium-browse
 6050 ?        00:00:03 chromium-browse
 6100 ?        00:00:02 chromium-browse
 7973 ?        00:11:36 chromium-browse
 8265 ?        00:00:05 chromium-browse
 9977 ?        00:00:22 chromium-browse
10084 ?        00:00:12 chromium-browse
10152 ?        00:00:02 chromium-browse
10180 ?        00:00:36 chromium-browse
10190 ?        00:04:00 chromium-browse
10896 ?        00:00:01 chromium-browse
12161 ?        00:00:19 chromium-browse
12183 ?        00:00:15 chromium-browse
12190 ?        00:00:09 chromium-browse
12197 ?        00:00:02 chromium-browse
12208 ?        00:02:06 chromium-browse
```

but when I tried the gcore part for all of them it said failed to create file ](*,)

---

