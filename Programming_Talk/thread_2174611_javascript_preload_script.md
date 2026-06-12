---
title: "javascript preload script"
date: 2013-09-15
forum: Programming Talk
---

### Post by maclenin on 2013-09-15
Essentially, I am trying to optimize the following script to facilitate the preload of a large array (**imIP**) of (400+) images (~ 100 KB each) into the brower's cache.... The script "works" but is inexcusably slow....

Thanks for any guidance!

```

function preload() {
if (!preload.list) {
preload.list = [];
}
for (var i = 0; i < len**imIP**; i += 1) {
pImg = new Image();
pImg.src = imIP[i];
pImg.onload = preload_b;
preload.list.push(pImg);
}
function preload_b() {
a = preload.list;
add_tn(a);
display(a);
}
}

```

---

### Post by ofnuts on 2013-09-15
400 images times 100KB = 40MB of images. Unless it's for your own personal use, you are going to make a lot of people unhappy.

---

