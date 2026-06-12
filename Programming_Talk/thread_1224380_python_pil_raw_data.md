---
title: "python pil raw data"
date: 2009-07-27
forum: Programming Talk
---

### Post by sidious1741 on 2009-07-27
I have found out how to do everything with pil but read raw data.  Before I found out about pil I used a module called png to read png files.  I could easily get data like '0,12,234,255'.  I don't want to edit an image I just want to read the data for each pixel.

---

### Post by unutbu on 2009-07-27
Perhaps what you are looking for is Image.fromstring.
See the PIL handbook ([http://www.pythonware.com/library/](http://www.pythonware.com/library/)) for more info.

---

### Post by sidious1741 on 2009-07-27
> **unutbu said:**
> Perhaps what you are looking for is Image.fromstring.
See the PIL handbook ([http://www.pythonware.com/library/](http://www.pythonware.com/library/)) for more info.

I don't think so.  I want the opposite.  I have a bmp file that I want to read, not data that I want to save as a bmp file.

---

### Post by unutbu on 2009-07-27
If you have a bmp file, you should be able to load it with
```

Image.open('file.bmp')

```

---

### Post by sidious1741 on 2009-07-27
I know that too.  I just dont know what to do with the image object.

---

### Post by unutbu on 2009-07-28
This is my last try :)
[PHP]im=Image.open('file.bmp')
print(list(im.convert().getdata()))[/PHP]

---

### Post by sidious1741 on 2009-07-28
> **unutbu said:**
> This is my last try :)
[PHP]im=Image.open('file.bmp')
print(list(im.convert().getdata()))[/PHP]

Thanks, that worked.

---

