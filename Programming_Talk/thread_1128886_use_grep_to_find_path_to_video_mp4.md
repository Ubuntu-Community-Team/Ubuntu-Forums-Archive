---
title: "use grep to find path to video mp4"
date: 2009-04-18
forum: Programming Talk
---

### Post by p.becks on 2009-04-18
Hello, 

I am trying to write a script that wil download the latest video's from Chris Pirillo to my desktop. I use the following commands:

wget [http://feeds.pirillo.com/ChrisPirilloShow](http://feeds.pirillo.com/ChrisPirilloShow)
[http://feeds.pirillo.com/ChrisPirilloShow](http://feeds.pirillo.com/ChrisPirilloShow) 

(which gives me a file that can search in)

grep -e [http://blip.tv/file/get/L0ckergn0me-](http://blip.tv/file/get/L0ckergn0me-) ChrisPirilloShow > result1.txt 

(searching for the line that contain the pathes to the videos)


Now my objective is to end up with the correct paths to the videos (ex: "http://blip.tv/file/get/L0ckergn0me-WhatsABrowserUserAgentString734.mp4")

Below a part of the file "ChrisPirilloShow"

********************************************************

Beginner</a></li>

	</ul>
</p>
<p>Want to embed this video on your own site, blog, or forum? Use this code or <a href="http://blip.tv/file/get/L0ckergn0me-WhatsABrowserUserAgentString734.mp4">download the video</a>: </p>
<p><textarea style="width: 460px; height:60px;">&#60;object width=&#34;425&#34; height=&#34;350&#34;&#62;&#60;param 

**********************************************************

Can someone help me?

---

### Post by ghostdog74 on 2009-04-18
```

perl -ne 'print if s/.*href=\"(.*?)\".*/\1/ms;' file 

```

---

### Post by lloyd_b on 2009-04-18
```
grep -o "http://.*mp4" file
```will give you everything that starts with "http://" and ends with "mp4".

Lloyd B.

---

### Post by Arndt on 2009-04-18
> **lloyd_b said:**
> ```
grep -o "http://.*mp4" file
```will give you everything that starts with "http://" and ends with "mp4".

Lloyd B.

True, but that may result in this:

```
$ echo "http://foo.html and http://foo.mp4 and more" | grep -o 'http://.*mp4'
http://foo.html and http://foo.mp4

```

Perl has regexps which match the smallest expression rather than the largest, as classical regexps do. I don't know if some variant of grep supports them.

---

### Post by lloyd_b on 2009-04-19
> **Arndt said:**
> True, but that may result in this:

```
$ echo "http://foo.html and http://foo.mp4 and more" | grep -o 'http://.*mp4'
http://foo.html and http://foo.mp4

```

Perl has regexps which match the smallest expression rather than the largest, as classical regexps do. I don't know if some variant of grep supports them.

Yes.  The grep pattern I posted presumes the data looks like what the OP posted for the problem.

The pattern could be narrowed:```
grep -o "http://blip.tv/file/get/L0ckergn0me-.*mp4" file
```to further reduce the chances of a false positive, but depending on the actual data involved, it may not be possible to completely eliminate the chances of a false positive.

Lloyd B.

---

### Post by Arndt on 2009-04-19
> **lloyd_b said:**
> Yes.  The grep pattern I posted presumes the data looks like what the OP posted for the problem.

The pattern could be narrowed:```
grep -o "http://blip.tv/file/get/L0ckergn0me-.*mp4" file
```to further reduce the chances of a false positive, but depending on the actual data involved, it may not be possible to completely eliminate the chances of a false positive.

Lloyd B.

Perhaps it would be enough to assume there isn't a : in the URL; then this works:

```
grep -o "http://[^:]*mp4" file
```

Or use the facilities for actually parsing HTML correctly. I know Perl has those; Python etc. probably do too. Something which simply collected all URLs in a text of whatever format would be useful, but I don't know if there are such things available.

---

### Post by p.becks on 2009-04-19
Hello y'all,

Thanks for all the input!

A have a confession to make: I am scripting from within Windows Xp :-( 

I use sed/awk/grep/wget (win32).

This is the (Dos) script i make thanks to you guys:


***************************************
c:
cd c:\downloads\wgetwin-1_5_3_1-binary\
mkdir video
cd video
del ChrisPirilloShow*.*
del down*.*

..\wget [http://feeds.pirillo.com/ChrisPirilloShow](http://feeds.pirillo.com/ChrisPirilloShow)

cd "c:\program files\gnuwin32\bin\"

grep -o "http://.*mp4" "c:\downloads\wgetwin-1_5_3_1-binary\video\ChrisPirilloShow" > "c:\downloads\wgetwin-1_5_3_1-binary\video\down.txt"

sed -i "s/http/wget http/g" "c:\downloads\wgetwin-1_5_3_1-binary\video\down.txt"

cd c:\downloads\wgetwin-1_5_3_1-binary\video\

path = %PATH%;c:\downloads\wgetwin-1_5_3_1-binary\

ren down.txt down.bat
call down.bat
del *.?
exit

*****************************************************

As far as i can see, the script works all the time!

Thanks again for all the input!

---

