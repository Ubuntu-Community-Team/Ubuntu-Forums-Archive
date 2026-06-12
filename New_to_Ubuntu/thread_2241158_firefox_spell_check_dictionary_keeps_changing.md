---
title: "firefox spell check dictionary keeps changing"
date: 2014-08-24
forum: New to Ubuntu
---

### Post by Saffo on 2014-08-24
i'm sorry if this has already been posted about somewhere else...

i am new to ubuntu. i am using firefox and for some reason, the spell check dictionary keeps defaulting to Jordanian Arabic. i am not sure why. (i do have Arabic text entry enabled along with several other languages, but my primary language is English.) 

it will underline everything in red as i type. i keep changing it in the contextual menu. it will do this weird thing where i click "English (US)" in the drop-down menu, when i right-click on a word. but then it won't change. when i change it a SECOND time, it will usually stay for a while, but eventually, (maybe it's when i reopen firefox) it will snap back again. i've even changed it manually in the about:config, but that only seems to fix it for so long before it snaps back to Jordanian Arabic. 

maybe there is a setting somewhere i am not aware of?

thanks!

---

### Post by Butthead on 2014-08-24
I was personally wondering myself why I (apparently? :confused: ) have the South African English language pack installed automagically for me in Firefox?

---

### Post by Saffo on 2014-08-24
i have several language packs installed. but that doesn't explain why or how firefox decided to make Jordanian Arabic the default.

---

### Post by Vladlenin5000 on 2014-08-25
I cannot explain it either... I also have many languages packs installed and in my case at first it defaulted to *French* and now to *Spanish (Cuba)*!!! Of course, all south-American Spanish variations are installed but neither any of those nor French are the default OS language.

---

### Post by RangerK on 2014-12-07
Bump

---

### Post by GrouchyGaijin on 2014-12-07
I have both English and Swedish installed and for some reason Firefox keeps setting English to Canada instead of the US. (Not a big deal as I read Canadian English too, eh) :lolflag:

---

### Post by bapoumba on 2014-12-09
I have English and French installed and FF keeps on choosing none at all whatever I do. When I change from the right click menu, it sticks for this session only. Once closed and restarted (or the computer rebooted), i have to do it all over again.

I just saw an "Add Dictionary" link at the bottom of the Language menu. Installed French and English and will see :)

---

### Post by sandyd on 2014-12-10
What locale do you guys have installed for firefox?

```

dpkg -l | grep firefox-locale-
```

Might be that a few are installed and firefox is playing musical chairs with them.

---

### Post by GrouchyGaijin on 2014-12-10
```

ii  firefox-locale-en                                     34.0+build2-0ubuntu0.14.04.1                        amd64        English language pack for Firefox
ii  firefox-locale-ja                                     34.0+build2-0ubuntu0.14.04.1                        amd64        Japanese language pack for Firefox
ii  firefox-locale-sv                                     34.0+build2-0ubuntu0.14.04.1                        amd64        Swedish language pack for Firefox


```

---

### Post by bapoumba on 2014-12-10
```
dpkg -l | grep firefox-locale
ii  firefox-locale-en                          34.0+build2-0ubuntu0.14.10.2             i386         English language pack for Firefox
ii  firefox-locale-fr                          34.0+build2-0ubuntu0.14.10.2             i386         French language pack for Firefox

```

---

### Post by sandyd on 2014-12-10
> **bapoumba said:**
> ```
dpkg -l | grep firefox-locale
ii  firefox-locale-en                          34.0+build2-0ubuntu0.14.10.2             i386         English language pack for Firefox
ii  firefox-locale-fr                          34.0+build2-0ubuntu0.14.10.2             i386         French language pack for Firefox

```

If you remove either of them, does the language stick?

If it does, this could be a bug that should be reported in LP

---

### Post by bapoumba on 2014-12-10
Removed the fr locale, will see :)
Thanks sandyd.

---

### Post by coldraven on 2014-12-10
All that I know is that if you right click in any text box (like this one) that has more than two lines you will see "Languages". The one that has a little black dot next to it is the default language. I have four, English Australia, South Africa, US and UK. For me it does not change from UK.

---

### Post by bapoumba on 2014-12-12
Well, you got it sandyd :)
Did not want to exit FF the other day and log back in different places over again. So I just waited to get back to this machine and it's working after removing the fr locale. Thanks much !

@coldraven : that is how I had it with fr and en locales, but it would not pick on my first choice, I had to do it by right click every time I started a new FF session..

---

