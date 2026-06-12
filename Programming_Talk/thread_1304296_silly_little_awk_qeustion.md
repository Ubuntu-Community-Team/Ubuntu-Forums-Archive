---
title: "silly little awk qeustion"
date: 2009-10-29
forum: Programming Talk
---

### Post by docetes on 2009-10-29
I have the following text
```
<p><a href="http://www.blahblah.com/blah">bigeoino</a> posted a photo:</p>
<p><a href="http://www.www.blahblah.com/fdf/" title="test"><img src="http://www.blahblah.com/blah/3528/image93b_m.jpg" width="240" height="157" alt="nice" /></a></p>
```

When i run the following awk statement

```
awk 'BEGIN{FS="<img src=";RS="\/>"}/</{print $2}' 
```


i get 

```
"http://www.blahblah.com/blah/3528/image93b_m.jpg" width="240" height="157" alt="nice"
```

but i would like the code to stay enclosed in the <img and />

How would I go about this?

---

### Post by ghostdog74 on 2009-10-29
```

# awk '/img/{gsub(/.*img/,"");print "<img"$0}' file
<img src="http://www.blahblah.com/blah/3528/image93b_m.jpg" width="240" height="157" alt="nice" /></a></p>


```

---

### Post by docetes on 2009-10-29
Cheers

---

