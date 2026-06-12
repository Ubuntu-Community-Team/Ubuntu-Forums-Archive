---
title: "preload to browser cache advice"
date: 2013-04-21
forum: Programming Talk
---

### Post by maclenin on 2013-04-21
I have distilled the following preload snippet, which I use for multiple-image, multiple-page / gallery web sites...

**.css**
```
.preload {display:none;}

```
**.js**
```
var imgArray=[];
imgArray[0]="img0.jpg";
imgArray[1]="img1.jpg";
imgArray[2]="img2.jpg";
var imgArraylen=imgArray.length;

```
**.html**
```

<script type="text/javascript">for (i=0; i<imgArraylen; i++) {document.write('<img class="preload" src="'+imgArray[i]+'">');}</script>

```

...is there a "better" way?

I have tinkered with [this method]("http://stackoverflow.com/questions/10240110/how-do-you-cache-an-image-in-javascript"), as well, but it's not clear that there is a comprehensive performance benefit.

Thanks for any suggestions.

---

