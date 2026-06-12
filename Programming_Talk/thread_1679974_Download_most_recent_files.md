---
title: "Download most recent files"
date: 2011-02-01
forum: Programming Talk
---

### Post by xtjacob on 2011-02-01
I need to write a script in Bash to download the 6 most recent jpg files off of a server. Is there anyway to do this?

---

### Post by papibe on 2011-02-01
Ideas:
[LIST]
[*]The easiest way would be to mount the remote directory into the local host (using nfs or smbfs).
[*]If you can ssh to the server you can sync the remote dir locally and then pick the new files (using rsync).
[*]If you really just need to get the newest files, you can do it in two steps using rsync over ssh: First get the list of the 6 newest files, and then copy them to your local host.
[/LIST]

I hope it helps.

---

### Post by xtjacob on 2011-02-01
I should've probably clarified. :P I cannot ssh into the server only gain http access, although I might be able to modify and use wget instead of rsync. How can I only list the most recent files on the server?

---

### Post by Vaphell on 2011-02-01
and how do you access these pictures in a normal way? because you can't really access things you have no idea what name they have. Is there a predictable name format? are they listed on some webpage?

---

### Post by xtjacob on 2011-02-01
Sorry for being so vague, the pictures are on here: [http://radar.weather.gov/ridge/RadarImg/N0R/EWX/](http://radar.weather.gov/ridge/RadarImg/N0R/EWX/). I normally access them on this page and though wget. The "EWX" is the station ID, the "20110202" is the date, and the "0322" is the time.

---

### Post by papibe on 2011-02-01
I would recommend python + [Beautiful Soup]("http://www.crummy.com/software/BeautifulSoup/"). They are a very good combo to parse html.

Regards.

---

### Post by Vaphell on 2011-02-02
```
#!/bin/bash

url="http://radar.weather.gov/ridge/RadarImg/N0R/EWX/"
n=6

rm index.html*
wget --cache=off --proxy=off $url

gifs=$( grep -E 'EWX.*gif' index.html | sed -r 's:.*(EWX.*?gif).*:\1:g' | sort | tail -n $n )
for gif in $gifs
do
  echo $gif
  wget $url$gif
done

```

test if it's ok, i had problems with wget downloading outdated version of image index without newest gifs (caching).

---

### Post by xtjacob on 2011-02-02
It works! Thanks for the help!

---

