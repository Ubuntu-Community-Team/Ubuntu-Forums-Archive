---
title: "Python PIL Batch Image Modify"
date: 2009-04-11
forum: Programming Talk
---

### Post by ulysses-31 on 2009-04-11
Hi there 

I am trying to batch convert as small group of files however i cannot get it working. The program should take the original images and darken them and then save them in the output directory

Here it the code:

```

from PIL import Image
import ImageEnhance
OUTDIR="output/" 



images=[ "im%02d.jpg"%(i) for i in range(4)] 

def myFunc(c):
    c = ImageEnhance.Contrast(images)
    images = contrast.enhance(1.21)
    return c

for i in images:
    print i
    img=Image.open(i)
    img=img.point(myFunc) #Wrong i think
    img.save(OUTDIR+i)
```


Could someone have a look and see tell me what i am doing wrong
I think it is something to do with the img.point(myFunc)

Cheers
Scott

---

### Post by ghostdog74 on 2009-04-11
put your code in code tags.

---

