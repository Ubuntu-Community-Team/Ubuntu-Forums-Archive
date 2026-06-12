---
title: "Python: fetch a page, parse links and wget"
date: 2010-07-31
forum: Programming Talk
---

### Post by kyleabaker on 2010-07-31
I'm trying to create a script that will fetch the contents of the following page..
[http://www.last.fm/music/+free-music-downloads?page=1](http://www.last.fm/music/+free-music-downloads?page=1)

Then store all of the Free Downloads links in an array. Then fetch the next linked page (this could be parsed by the pagination at the bottom of the page) and do the same.

After all the links are stored in the array, I'd like to have this script download all the links in the array via wget or something like that. Does anyone know how I can do this? Or can someone get me started with some code? Thanks!

---

### Post by DaithiF on 2010-07-31
Hi,
I'm not entirely sure how ethical this is, but I suppose free downloads must mean free downloads.

anyway, this python script will grab the urls and filenames and write them to a file ('links').  and then the bash script at the bottom would wget them.

```
import urllib, re

def do_page(url):
    f = urllib.urlopen(url)
    html = f.read()
    pattern = r'title="Download free MP3: (.*?) \(.*?\)" href="(.*?)"'
    hits = re.findall(pattern, html)
    return hits

if __name__ == '__main__':
    hits = []
    for i in range(1, 26):
        url = 'http://www.last.fm/music/+free-music-downloads?page=%d' % i
        hits.extend(do_page(url))

    fh = open('links', 'wb')
    for hit in hits:
        fh.write('%s\t%s\n' % (hit[1], hit[0]))
    fh.close()

``````
while read url title
do
  wget "$url" -O "$title".mp3
done < links

```

---

### Post by ghostdog74 on 2010-07-31
```

#!/bin/bash

url='http://www.last.fm/music/+free-music-downloads?page=1'
num=$(wget -O- -q "$url" | awk -vRS="</[aA]>" '/class=\"lastpage\"/ {gsub(/.*>/,""); print}')
for((i=1;i<=$num;i++))
do
 url="http://www.last.fm/music/+free-music-downloads?page=$i"
 wget -O- -q $url | awk 'BEGIN{ RS="</[aA]>" }
 /http:\/\/freedownloads.last/{
  gsub(/.*href=[\047\042]/,"")
  gsub(/\042><span>.*/,"")
  print
 }'
done | while read -r URL
do
  echo wget "$URL"
done


```

---

### Post by kyleabaker on 2010-08-01
Wow, thanks! You guys are quick!

One other thing, I noticed the the source files only have the songs labeled by the song title, excluding the artist. Would it be difficult to save the song as "Artist - Title" from either the url anchor tag..
```
<a class="lfmButton lfmBigButton lfmFreeDownloadButton" title="Download free MP3: Fanfarlo - I'm A Pilot (4.1 MB)" href="http://freedownloads.last.fm/download/182052320/I%2527m%2BA%2BPilot.mp3"><span>Free MP3</span></a>
```
..or from the text in the anchors following the download link?
```
</a><a href="/music/Fanfarlo/_/I%27m+A+Pilot" class="trackTitle">I'm A Pilot</a> <span class="trackDuration" dir="ltr">(4:30)</span><br />
                            <a href="/music/Fanfarlo" class="trackArtist">Fanfarlo</a>
```

[quote=DaithiF]I'm not entirely sure how ethical this is, but I suppose free downloads must mean free downloads.[/quote]
That thought crossed my mind as well, but if they are offering these songs for free then they know some people will grab them all. If you have a way/tool to make this process simpler, where's the foul? :P

I love the shortness and simplicity of these examples! Awesome!

---

### Post by DaithiF on 2010-08-01
> **kyleabaker said:**
> Would it be difficult to save the song as "Artist - Title" from either the url anchor tag..

thats what my script does actually. thats why the regex grabs 2 things rather than 1, ie. the url and the artist - title piece, and thats why the wgets have a -O parameter, to save the download with that name.

---

### Post by kyleabaker on 2010-08-01
> **DaithiF said:**
> thats what my script does actually. thats why the regex grabs 2 things rather than 1, ie. the url and the artist - title piece, and thats why the wgets have a -O parameter, to save the download with that name.

Oh cool, I didn't test it yet since I thought I would download them all titled wrong. Thanks, I'll let you know how it works!

---

### Post by fchevitarese on 2010-11-04
> **DaithiF said:**
> Hi,
I'm not entirely sure how ethical this is, but I suppose free downloads must mean free downloads.

anyway, this python script will grab the urls and filenames and write them to a file ('links').  and then the bash script at the bottom would wget them.

```
import urllib, re

def do_page(url):
    f = urllib.urlopen(url)
    html = f.read()
    pattern = r'title="Download free MP3: (.*?) \(.*?\)" href="(.*?)"'
    hits = re.findall(pattern, html)
    return hits

if __name__ == '__main__':
    hits = []
    for i in range(1, 26):
        url = 'http://www.last.fm/music/+free-music-downloads?page=%d' % i
        hits.extend(do_page(url))

    fh = open('links', 'wb')
    for hit in hits:
        fh.write('%s\t%s\n' % (hit[1], hit[0]))
    fh.close()

``````
while read url title
do
  wget "$url" -O "$title".mp3
done < links

```


Hey man!!! 

Thanks ... This helped me a lot ;)

---

### Post by ssam on 2010-11-04
you could also look at the beautiful soup library. makes it very easy to grab elements out of html (even if its a bit broken)

---

