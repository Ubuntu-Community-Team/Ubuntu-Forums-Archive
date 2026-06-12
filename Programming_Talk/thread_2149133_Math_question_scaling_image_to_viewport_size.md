---
title: "Math question: scaling image to viewport size"
date: 2013-05-27
forum: Programming Talk
---

### Post by bird1500 on 2013-05-27
Hi,
I learned some OpenGL and wanna display an image in a viewport so that the image fills in the viewport as much as possible yet maintains its aspect ratio.

E.g. if viewport width/height = 800/600 and image width/height = 100/200, the image should be scaled to 300/600.

Can anyone please suggest how to construct the algorithm to get the final image size (in this example it would be 300/600)? I'm terrible at math.

---

### Post by Bachstelze on 2013-05-27
Hint: it depends on whether the aspect ratio of your image is smaller or larger than that of your viewport.

---

### Post by bird1500 on 2013-05-27
Thanks, I'm trying to solve this issue for like 3 days and I played with aspect ratio, the problem is there are different aspect ratios:
image width to height, or image width to viewport width - both of them lead to different approaches and gets muddy and none worked for me.

```

    if(img.w > view_w && img.h > view_h) {
        ratio_w = view_w / img.w;
        ratio_h = view_h / img.h;
    } else {
        ratio_w = img.w / view_w;
        ratio_h = img.h / view_h;
    }
    
scale_mat_.Scale(ratio_h, ratio_w, 1.0f);
// then model view projection matrix

```
it doesn't work properly: it minimizes the image too much, can't figure out why.

plus I might be piling lots of crappy math lines that could be solved properly in 2-3 lines of math code, I have nothing to do with math so it might take forever to figure out.

---

### Post by bird1500 on 2013-05-27
```

void
ScaleImage(float img_w, float img_h, float w, float h,
    float &scale_w, float &scale_h)
{
    if(img_w > w || img_h > h) { // scale down below natural size
        const float r_w = img_w / w;
        const float r_h = img_h / h;
        const float r = (r_w < r_h) ? r_w : r_h;
        scale_w = r / r_h;
        scale_h = r / r_w;
    } else { // scale (down) to natural size
        scale_w = img_w / w;
        scale_h = img_h / h;
    }
}

```
This is voodoo math, I wrote it and for some reason it works, and works well, don't know why. I guess I have to thank myself.

---

