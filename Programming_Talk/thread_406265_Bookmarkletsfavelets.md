---
title: "Bookmarklets/favelets"
date: 2007-04-10
forum: Programming Talk
---

### Post by kerry_s on 2007-04-10
Any one use bookmarklets/favelets ? ( [http://en.wikipedia.org/wiki/Bookmarklet](http://en.wikipedia.org/wiki/Bookmarklet) )

I'm wanting to replace some of my extensions with simple favelets.

I have:

```
Name: Hide All Images
Location: javascript:if (document.images.length<1){alert('No image on page!')}else{for(jK6bvW=0;jK6bvW<document.images.length;jK6bvW++){void(window.document.images[jK6bvW].src='missing');}void(null)}

Name: Page Color...
Loaction: javascript:Cys8Np=prompt('Background color...','');Fj9z4M=new Function('x','i','if(Cys8Np){if(x.length==0){if(document.all)x.document.body.background=\'\';void(x.document.bgColor=Cys8Np)}else{for(i=0;i<x.length;i++){Fj9z4M(x.frames[i])}}}');Fj9z4M(this)

Name: zap colors
Location: javascript:(function(){var newSS, styles='* { background: white ! important; color: black !important } :link, :link * { color: #0000EE !important } :visited, :visited * { color: #551A8B !important }'; if(document.createStyleSheet) { document.createStyleSheet(%22javascript:'%22+styles+%22'%22); } else { newSS=document.createElement('link'); newSS.rel='stylesheet'; newSS.href='data:text/css,'+escape(styles); document.getElementsByTagName(%22head%22)[0].appendChild(newSS); } })();

Name: zoom images in
location: javascript:(function(){ function zoomImage(image, amt) { if(image.initialHeight == null) { /* avoid accumulating integer-rounding error */ image.initialHeight=image.height; image.initialWidth=image.width; image.scalingFactor=1; } image.scalingFactor*=amt; image.width=image.scalingFactor*image.initialWidth; image.height=image.scalingFactor*image.initialHeight; } var i,L=document.images.length; for (i=0;i<L;++i) zoomImage(document.images[i], 2); if (!L) alert(%22This page contains no images.%22); })();

Name: zoom images out
Location: javascript:(function(){ function zoomImage(image, amt) { if(image.initialHeight == null) { /* avoid accumulating integer-rounding error */ image.initialHeight=image.height; image.initialWidth=image.width; image.scalingFactor=1; } image.scalingFactor*=amt; image.width=image.scalingFactor*image.initialWidth; image.height=image.scalingFactor*image.initialHeight; } var i,L=document.images.length; for (i=0;i<L;++i) zoomImage(document.images[i],.5); if (!L) alert(%22This page contains no images.%22); })();


```
If you do use bookmarklets/favelets and would like to share, please feel free. :)

---

