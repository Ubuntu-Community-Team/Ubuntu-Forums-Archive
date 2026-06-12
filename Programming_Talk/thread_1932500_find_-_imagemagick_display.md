---
title: "find - imagemagick display"
date: 2012-02-27
forum: Programming Talk
---

### Post by gtburt on 2012-02-27
Hi,

I'm using the following in a bash script to do a quick and dirty slideshow with ImageMagick's display.

find /home/user_1/Pictures/ -iname "*$SEARCHSTRING*JPG" -print -exec display -delay 1x1 -define jpeg:size=200x250 {} \+


I have the pictures organized in folders by year and would like them to appear in order... but 'find' is not returning the file names in order.


SEARCHSTRING is defined earlier from the arguments.

Any help?

Thanks.

---

### Post by MG&amp;TL on 2012-02-27
I'm not familiar with imagemagick, so I'm not sure where you'd slot it in, but a pipe to *sort *should do the trick. Example.

```

#unordered
find /dev -iname "*"

#ordered alphabetically

find /dev -iname "*" | sort
```

see *man sort* for details.

---

### Post by ofnuts on 2012-02-27
```

find . -iname "*$SEARCHSTRING*JPG" -print0 | sort -z | xargs -0 display -delay 1x1 -define jpeg:size=200x250

```

---

### Post by gtburt on 2012-02-27
Worked great.  Thank you.

> **ofnuts said:**
> ```

find . -iname "*$SEARCHSTRING*JPG" -print0 | sort -z | xargs -0 display -delay 1x1 -define jpeg:size=200x250

```

---

