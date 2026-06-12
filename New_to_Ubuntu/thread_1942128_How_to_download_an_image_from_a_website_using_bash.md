---
title: "How to download an image from a website using bash?"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by mferarri on 2012-03-16
Hi UbuntuForums,

How would I download this picture [http://www.viemu.com/vi-vim-cheat-sheet.gif]("http://www.viemu.com/vi-vim-cheat-sheet.gif") using bash?

thanks,:KS

---

### Post by papibe on 2012-03-16
Hi mferarri.

You can use 'wget'. For instance:
```
wget http://www.viemu.com/vi-vim-cheat-sheet.gif
```
Hope that helps.
Regards.

---

### Post by andrew.46 on 2012-03-17
Or for a variation:

```

curl -O http://www.viemu.com/vi-vim-cheat-sheet.gif

```

---

### Post by mferarri on 2012-03-17
thanks everyone for your response. wget works fine for me. so my original question is solved. 

2) if i want to get the picture of the beans in my profile (rank2.png) without knowing the url to it how would i get the pic?

---

### Post by andrew.46 on 2012-03-17
> **mferarri said:**
> 2) if i want to get the picture of the beans in my profile (rank2.png) without knowing the url to it how would i get the pic?


```

wget http://ubuntuforums.org/images/rank_2.png

```

---

### Post by mferarri on 2012-03-17
> **andrew.46 said:**
> ```

wget http://ubuntuforums.org/images/rank_2.png

```

... but what if i dint know that url?... ok solved it myself (you can actually right click on a pic in the browser and select copy url) 

thanks guys.

---

### Post by andrew.46 on 2012-03-18
> **mferarri said:**
>  ok solved it myself (you can actually right click on a pic in the browser and select copy url) 

You found it :)

---

