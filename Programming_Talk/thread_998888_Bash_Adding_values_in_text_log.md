---
title: "Bash: Adding values in text log?"
date: 2008-12-01
forum: Programming Talk
---

### Post by cuddles71 on 2008-12-01
Morning all.

Say I have a text file (called overall.log) that looks like this:

```
37 - DJ Kyo's Dance Party
20 - DJ Charlie and (the Chocolate) Kyo
13 - DJ Zim's Invasion Hour
12 - The Smoking Lounge with DJ Rastafari Man
09 - Doctor JohnnyFever, the AutoDJ
08 - Early Twilight with DJ Dark
07 - Get Tanked with DJ Abrahms
06 - The DJ Korith Show
06 - DJ Loco's Sanitarium
06 - DJ Crypto's Music Carousel
05 - Vorac, The Breakfast Cereal
02 - DJ Charlie's Old Time Radio Show
37 - DJ Kyo's Dance Party
20 - DJ Charlie and (the Chocolate) Kyo
13 - DJ Zim's Invasion Hour
12 - The Smoking Lounge with DJ Rastafari Man
09 - Doctor JohnnyFever, the AutoDJ
08 - Early Twilight with DJ Dark
07 - Get Tanked with DJ Abrahms
06 - The DJ Korith Show
06 - DJ Loco's Sanitarium
06 - DJ Crypto's Music Carousel
05 - Vorac, The Breakfast Cereal
02 - DJ Charlie's Old Time Radio Show
```

What I'd like to do is add all the "like" lines in the file together (ex: All the numbers for DJ Kyo's Dance Party) to get something like this:

```
74 - DJ Kyo's Dance Party
40 - DJ Charlie and (the Chocolate) Kyo
26 - DJ Zim's Invasion Hour
24 - The Smoking Lounge with DJ Rastafari Man
18 - Doctor JohnnyFever, the AutoDJ
16 - Early Twilight with DJ Dark
14 - Get Tanked with DJ Abrahms
12 - The DJ Korith Show
12 - DJ Loco's Sanitarium
12 - DJ Crypto's Music Carousel
10 - Vorac, The Breakfast Cereal
04 - DJ Charlie's Old Time Radio Show
```

Is there an easy way to do this?

Thanks in advance!

---

### Post by ghostdog74 on 2008-12-01
sure
```

awk -F"-" '{_[$2]+=$1}END{for(i in _)print _[i],i}' file

```

---

### Post by cuddles71 on 2008-12-01
> **ghostdog74 said:**
> sure
```

awk -F"-" '{_[$2]+=$1}END{for(i in _)print _[i],i}' file

```

That works! Thanks!

---

