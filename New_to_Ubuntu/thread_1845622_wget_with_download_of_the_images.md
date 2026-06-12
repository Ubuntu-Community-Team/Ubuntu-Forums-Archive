---
title: "wget with download of the images?"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by honeybear on 2011-09-17
Hello 

save as of firefox can make a folder with the images. Could wget or curl do the sample please?

thank you !

---

### Post by josephmills on 2011-09-17
are you asking how to have wget put a certian picture that you are downloading into a certain dir ? if so just us the cd and && like so 

say I want this picture in my /usr/share/wallpapers


[img]http://kde-look.org/CONTENT/content-pre1/145309-1.jpeg[/img]

```
cd /usr/share/wallpapers && wget http://kde-look.org/CONTENT/content-pre1/145309-1.jpeg
```

or because wget saves everything by default after the last  /  in this case /145309-1.jpeg  we could also do a 
```
wget http://kde-look.org/CONTENT/content-pre1/145309-1.jpeg; wget http://kde-look.org/CONTENT/content-pre1/145309-1.jpeg; sudo mv 14*  /usr/share/wallpapers/ 
```
hope that this helps

---

### Post by honeybear on 2011-09-17
you do not understand ... 

I would like save as with wget restult

something like this : [http://imageshack.us/photo/my-images/4/firefoxsaveas.png/](http://imageshack.us/photo/my-images/4/firefoxsaveas.png/)

with the images of a given page into the folder

---

### Post by Lisiano on 2011-09-17
You mean you want to download the page?
```
mkdir New\ Folder; cd New\ Folder; wget -nc -c -k -p http://example.com/link/page.html 
```
-nc - No clobber
-c - continue
-k - convert so the page is locally browsable
-p - download everything needed to see the page

Hope this helped.

EDIT: josephmills nice picture

EDIT 2: Looking at the man page a bit more, the author recommends using this instead ```
wget -E -H -k -K -p http://<site>/<document>
```

---

### Post by honeybear on 2011-09-18
> **Lisiano said:**
> You mean you want to download the page?
```
mkdir New\ Folder; cd New\ Folder; wget -nc -c -k -p http://example.com/link/page.html 
```
-nc - No clobber
-c - continue
-k - convert so the page is locally browsable
-p - download everything needed to see the page

Hope this helped.

EDIT: josephmills nice picture

EDIT 2: Looking at the man page a bit more, the author recommends using this instead ```
wget -E -H -k -K -p http://<site>/<document>
```


thank you. Pretty cool :)
However it is like a wget -r -l1 with the images from the page. However it could be rather the mess, since the main html file is into the folder of downlaod. 

then the html file is into ubuntuforums.org, and I would be glad to have it in the ch2 folder instead, if possible
```
mkdir ch2 ; cd ch2
 wget -E -H -k -K -p "http://ubuntuforums.org/showthread.php?t=1845622" 
```

---

### Post by texaswriter on 2011-09-18
> **honeybear said:**
> thank you. Pretty cool :)
However it is like a wget -r -l1 with the images from the page. However it could be rather the mess, since the main html file is into the folder of downlaod. 

then the html file is into ubuntuforums.org, and I would be glad to have it in the ch2 folder instead, if possible
```
mkdir ch2 ; cd ch2
 wget -E -H -k -K -p "http://ubuntuforums.org/showthread.php?t=1845622" 
```

If this is solved, could you mark the thread as solved.

---

### Post by honeybear on 2011-10-30
> **texaswriter said:**
> If this is solved, could you mark the thread as solved.

thx. It is not really solved since the proposed solution is slightly different to the desired output of wget.

I am still studying the possible ways or alternatives... Maybe a very similar behavior as firefox save as might be eventually possible... 

I keep you informed, anytime.

not so good result:
```

mkdir ch2 ; cd ch2
 wget -E -H -k -K -p "http://ubuntuforums.org/showthread.php?t=1845622"

```



If you do save as with firefox:
cd ; mkdir ch4 
# then save as with firefox
> ls -1 ch4
showthread.php_files   <--- folder with the files. it contains much lighter and better, narrower and more specific
showthread.php.html

---

### Post by honeybear on 2012-10-07
It does not work actually since it has robots.

Does this below solution better?

 wget --user-agent="Mozilla/5.0 (Linux; U; Linux x86; fr-FR; rv:1.7.5) Gecko/20041202 Firefox/1.0"  -E -H -k -K -p "http://ubuntuforums.org/showthread.php?t=1845622"

---

### Post by proviron on 2013-01-11
This article on code.sh is bookmark worthy in my opinion. It's worth saving for future reference. It's fascinating reading with many valid points for contemplation. I have to concur on almost every point made within this article.

---

### Post by howefield on 2013-01-11
Old thread closed.

---

