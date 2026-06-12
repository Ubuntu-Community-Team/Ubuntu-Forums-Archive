---
title: "[PHP] preg_replace : clean up a URL ising a regular expression"
date: 2008-04-30
forum: Programming Talk
---

### Post by brazzmonkey on 2008-04-30
hello there,
i'm no programmer, but i happen to code php as a hobby. i have basic skills and lately i've been playing with regexp. however i'm a bit stuck when it comes to slightly difficult regexp.

i need to parse a URL that may look like (for instance)
```
http://brazzmonkey.sytes.net/blog/url?br=F&rc=fz/7-8&bd=T&url=http://www.3rdpartysite.com/test/article/13187/other_page_url.html&id=1232399685&li=oRwYSLG4Bp2oxAHLjpDpCw&msg=AFrqEzffSddQNLD5qGSot-7fbhU6X9Ex0Q
```
or
```
http://toph.is-a-geek.com/blog/url?pr=F&rc=fx/4-9&br=T&url=http://www.another3rdpartysite.com/article/1315187/_yet_another_page_url.html&id=12323998899685&li=oRwYSLG4453Bp2oxAHLjpDpCw&msg=AFrqEzffSddQNLD98465qGSot986X9Ex0Q
```
 i'd like to extract the url argument that's between "&url=" and "&id" but i can't figure out how to do it in a simple way.

i guess one of you might know of a way that's straightforward enough, so i thought i'd ask.

thanks in advance.

---

### Post by brazzmonkey on 2008-04-30
ok, in fact my problem came from "&" actually being "&amp;"
i guess i'm not to bad in regex, then.

---

