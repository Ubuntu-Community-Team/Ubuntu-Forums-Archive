---
title: "Wget  help in rage"
date: 2011-06-20
forum: Programming Talk
---

### Post by yeikel on 2011-06-20
Hi comunity , I have a little question with wget...


Well I want this : 

1)Enter to my website that have a dir wtih 100 photos (1.jpg - 100.jpg)
2)Download a directory that only have jpg

For example wget site.com/folder/1.jpg

The thing that I want is download from 1 to 100 .

---

### Post by Petrolea on 2011-06-20
Did you try using '*'? Like *.jpg, which means everything with jpg extension. Can't try it atm because I'm not at home.

---

### Post by yeikel on 2011-06-20
Yes for example : 

Download every image(*jpg) in [www.site.com/images/1.jpg](www.site.com/images/1.jpg) to [www.site.com/images/100.jpg](www.site.com/images/100.jpg)

Making it manually should be : 

wget site.com/images/1.jpg
wget site.com/images/2.jpg
wget site.com/images/3.jpg
....................
...........
wget site.com/images/100.jpg

---

### Post by Vaphell on 2011-06-20
```
for pic in site.com/images/{1..100}.jpg; do wget $pic; done
```

---

### Post by Lars Noodén on 2011-06-20
> **yeikel said:**
> Hi comunity , I have a little question with wget...


Well I want this : 

1)Enter to my website that have a dir wtih 100 photos (1.jpg - 100.jpg)
2)Download a directory that only have jpg

For example wget site.com/folder/1.jpg

The thing that I want is download from 1 to 100 .

You could do something like this:
```

for i in `seq 1 100`;
 do echo wget http://site.com/folder/$i.jpg;
done

```

Once that's working the way you like it, take out the 'echo' before the 'wget'

---

### Post by Lars Noodén on 2011-06-20
If there is nothing else in the same directory, then it can be done entirely using wget:
```

wget --no-parent --mirror --level=1 http://somesite.com/directory/

```

---

