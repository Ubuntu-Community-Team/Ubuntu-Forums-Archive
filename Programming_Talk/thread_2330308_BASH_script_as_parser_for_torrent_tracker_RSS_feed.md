---
title: "BASH script as parser for torrent tracker RSS feed."
date: 2016-07-10
forum: Programming Talk
---

### Post by CrewDK on 2016-07-10
Hallo. 

Using couple of guides I want to create simple parser for RSS feed which doesn't have direct links to *.torrent files. 

Finally I got something like this: 
```


for i in $(curl -s http://tr.anidub.com/rss.xml | grep -iA 2 'Unhappy' | grep -i 'isPermaLink' | grep -ioe 'http.*.html'); do
  tor_file=$(curl -sb "dle_user_id=477289; dle_password=d0e5b499e551a4a873ed9751f085ae82" $i | grep -iA 2 tv720 | grep -ie '&#1057;&#1082;&#1072;&#1095;&#1072;&#1090;&#1100; &#1090;&#1086;&#1088;&#1088;&#1077;&#1085;&#1090;' | grep --max-count 1 -ioE '/engine/download\.php\?id=[0-9]{1,5}| tail -n 1)
  tor_name=$(curl -sb "dle_user_id=477289; dle_password=d0e5b499e551a4a873ed9751f085ae82" $i | grep -ie '&#1048;&#1084;&#1103; &#1092;&#1072;&#1081;&#1083;&#1072;' | grep -i '720' | grep -ioE 'title=\"[AniDub].*.torrent\"' | recode html..ascii | grep -ioe '\[.*.torrent')
done

wget -nc http://tr.anidub.com${tor_file} -O ~/torrents/${tor_name} --load-cookies=/root/cookies.txt

```

But wget time after time got only 302 redirect and downloading index page instead of my torrent file. Did I missed something or this is simply impossible to download torrent file like this?

UPD: Just in case, if someone wants to help me I added cookies info...

---

### Post by CrewDK on 2016-07-15
NVM, just finished it myself :)

---

