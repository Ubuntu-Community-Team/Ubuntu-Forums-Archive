---
title: "sed or awk to filter name out of magnet link?"
date: 2012-03-08
forum: Programming Talk
---

### Post by illumilore on 2012-03-08
[noparse]How would one filter out the name field from a magnet link url? The basic url seems to go something like: "magnet:?xt=JIO3490DFGBLI394&dn=NAME&tr=TRACKERS" so I basically want to filter out everything between the &dn= and the next &, but I am not very familiar with sed or awk so most of what I have tried has failed (ie  sed '/^^/,/*\&dn=/s/*//' does not work)[/noparse]

---

### Post by papibe on 2012-03-09
Hi illumilore.

Try this:
```
sed 's/&dn.*&//'
```
Explanation:
- s for replace
- &dn.*& means 'an string that starts with &dn, then some characters (maybe none) and stop matching when a & appears'

Hope that helps.
Regards.

---

### Post by illumilore on 2012-03-09
> **papibe said:**
> Hi illumilore.

Try this:
```
sed 's/&dn.*&//'
```Explanation:
- s for replace
- &dn.*& means 'an string that starts with &dn, then some characters (maybe none) and stop matching when a & appears'

Hope that helps.
Regards.

Sorry, I think I was using the word filter wrong. What I want is everything outside of the name field excluded and the name field left over. And there can actually be more than one ampersand following the name field. So I would expect something like ```
sed 's/*.&dn//'
``` to remove everything before and including the &dn, but it doesn't seem to do anything, using the following as a raw example magnet url: ```
magnet:?xt=urn:btih:6E2CD8C228EA4790542CA441C2E92E793BCBA45E&dn=The.Daily.Show.2012.03.08.(HDTV-FQM)&tr=http://eztv.tracker.prq.to/announce&tr=http://tracker.ccc.de/announce&tr=udp://tracker.ccc.de:80/announce&tr=http://tracker.istole.it:80/announce&tr=http://tracker.publicbt.com:80/announce&tr=http://publicbt.ath.cx/announce&tr=udp://tracker.openbittorrent.com/announce&tr=http://nemesis.1337x.org/announce&tr=http://tracker-1.podmailing.com/announce&tr=http://atrack.pow7.com/announce
```

---

### Post by papibe on 2012-03-09
For removing all before '&dn=':
```
sed 's/[^&]*&dn=//'
```
The trick is instead of using . (any character), use [^&] that means "any character but &"

To get the field between '&dn=' and the first &:
```
sed 's/[^&]*&dn=\([^&]*\)&.*$/\1/'
```
Note that the expression between \( and \) can be referenced later as \1

To get the field between '&dn=' and the last &:
```
 sed 's/[^&]*&dn=\(.*\)&.*$/\1/'
```
Hope it helps.
Regards.

---

### Post by illumilore on 2012-03-09
Thanks. That worked. The regular expressions for that were a bit over my head.

---

### Post by papibe on 2012-03-09
Great :D Mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance.
Regards.

---

