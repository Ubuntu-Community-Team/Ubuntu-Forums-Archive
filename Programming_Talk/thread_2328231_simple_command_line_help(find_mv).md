---
title: "simple command line help(find mv)"
date: 2016-06-19
forum: Programming Talk
---

### Post by gognos on 2016-06-19
Hi i was wondering if anyone could help 


I want to find all .mp3 .mp4 files in certain directories then move them all to a directory named sort
So i try 

```
find Desktop Documents Downloads Videos Pictures -name '*.mp3' -o -name '*.mp4'
```

Cool This finds all my .mp3/.mp4 files 

So i try 

```
find Desktop Documents Downloads Videos Pictures -name '*.mp3' -exec mv -t /home/damien/Downloads/Sort {} + 
```

Cool this moves all the found .mp3 files to the sort directory

So i try 

```
find Desktop Documents Downloads Videos Pictures -name '*.mp3' -o -name '*.mp4' -exec mv -t /home/damien/Downloads/Sort {} + 
```

FAIL this only moves the mp4 files not the mp3 files so how do i change that command to move all mp4 and mp3 files to sort?

---

### Post by papibe on 2016-06-19
Hi gognos,

You need to group the name matching expressions:
```
find Desktop Documents Downloads Videos Pictures **[COLOR="#FF0000"]\([/COLOR]** -name '*.mp3' -o -name '*.mp4'[COLOR="#FF0000"]** \)**[/COLOR] -exec mv -t /home/damien/Downloads/Sort {} +
```
Explanation [here]("http://ubuntuforums.org/showthread.php?t=2264596&p=13224719#post13224719").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by steeldriver on 2016-06-19
oops ninja'd ...

---

### Post by gognos on 2016-06-19
> **papibe said:**
> Hi gognos,

You need to group the name matching expressions:
```
find Desktop Documents Downloads Videos Pictures **[COLOR=#FF0000]\([/COLOR]** -name '*.mp3' -o -name '*.mp4'[COLOR=#FF0000]** \)**[/COLOR] -exec mv -t /home/damien/Downloads/Sort {} +
```
Explanation [here]("http://ubuntuforums.org/showthread.php?t=2264596&p=13224719#post13224719").

Hope it helps. Let us know how it goes.
Regards.

Thank you very much  that worked

---

