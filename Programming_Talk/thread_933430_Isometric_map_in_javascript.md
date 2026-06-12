---
title: "Isometric map in javascript"
date: 2008-09-29
forum: Programming Talk
---

### Post by Vadi on 2008-09-29
Does anyone know any javascripts that, given a bunch of images and coordinates to place them at, would generate an isometric map?

Preferably an open-source license as this is for an oss project.

---

### Post by PC-XT on 2008-10-03
This is hard to do because you need to skew the image for 3D maps. You could do it for 2D maps, by just converting from isometric to rectangular coordinates, but the images will look the same. You could do it in Java, since it has more control over images, but I don't know if JavaScript can even skew images. I've seen lots of image effects in regular HTML/JavaScript, but not skewing.

---

### Post by Vadi on 2008-10-03
I don't need anything skewed; I'll provide the skewed images already.

Basically just need to be able to organize the images into a map given some data.

---

### Post by PC-XT on 2008-10-04
I suppose you mean a self-organizing map, then, and not a simple coordinate conversion.

Here is a terrain thing, though I think you can use different images. I couldn't get their wiki to load, so don't know the license: [http://www.pc-gamers.com/webgamex/iso_js_coords.php](http://www.pc-gamers.com/webgamex/iso_js_coords.php)
Here's why I couldn't load the wiki: (from [www.pc-gamers.com/](www.pc-gamers.com/))> Hi,

Welcome to pc-gamers.com


Due to a massive amount of Spam bots visiting this site, the whole thing is offline.
Some of my newer projects will be hosted here in the future.

Be back!

Someone named Komirad had made one in Flash here: [http://komirad.com/doc/12/flash-isometric-map-maker-oasis](http://komirad.com/doc/12/flash-isometric-map-maker-oasis)
He said he might make it open source here: [http://www.gotoandplay.it/_forums/viewtopic.php?t=3202&sid=874ff773f72cd19dcbe3230e02df4075](http://www.gotoandplay.it/_forums/viewtopic.php?t=3202&sid=874ff773f72cd19dcbe3230e02df4075)

Here's source for Pascal and C++ to display the map: [http://www.gamedev.net/reference/articles/article747.asp](http://www.gamedev.net/reference/articles/article747.asp) (Not sure how helpful, though, but just in case)

---

### Post by Vadi on 2008-10-04
I see. The pc-gamers.com one looks quite good (although a bit overkill, as I'll only use 2d for it). I'll see if I can find out what license is it...

---

### Post by PC-XT on 2008-10-04
If you are only using 2D, I made the following using the DOM and CSS positioning: [I fixed the typo in it.]```
function isoMapAdd(map,src,x,y){
//map is the element to hold the map,
// like a div or other containing block.
// This is not the id, but can be found by
// using the id in document.getElementById(mapid)
var h=16, w=20;//Height and Width of diamond in map images
// (the images should have transparent bottom corners,
// and the corners of the non-transparent diamond should
// meet each edge of the image at its midpoint;
// all the images should be the same size)
var t=document.createElement("img");
t.setAttribute("src", src);
t.setAttribute("style", "position:absolute;top:z-index:"+y+";"+Math.round(y*h/2)+";left:"+Math.round(x*w+((y&1)==0?w/2:0)));
map.appendChild(t);
}
```This will add a picture to the map (src is the url). Coordinates are assigned like this: (x,y)```
0,0  1,0  2,0  3,0
  0,1  1,1  2,1
0,2  1,2  2,2  3,2
```
You could call this function in a loop for each image.

If you use a div with width, height, and overflow:auto style properties set, it should allow you to scroll the map. You can also give it a border.

If you are working with cordinates:```
0,0  1,1  2,2  3,3
  0,1  1,2  2,3
-1,1 0,2  1,3  2,4
```I just made this conversion function:```
function isoMapAdd(map,src,x,y){
//map is the element to hold the map,
// like a div or other containing block.
// This is not the id, but can be found by
// using the id in document.getElementById(mapid)
var h=16, w=20;//Height and Width of diamond in map images
// (the images should have transparent bottom corners,
// and the corners of the non-transparent diamond should
// meet each edge of the image at its midpoint;
// all the images should be the same size)
var Y=y-x;
var t=document.createElement("img");
t.setAttribute("src", src);
t.setAttribute("style", "position:absolute;top:z-index:"+Y+";"+Math.round(Y*h/2)+";left:"+Math.round((x+Math.ceil(Y/2))*w+((Y&1)==0?w/2:0)));
map.appendChild(t);
}
```[I think the errors are fixed.]

---

### Post by Vadi on 2008-10-05
Thanks very much for that, but I think my map will be more like the following:
```

  0,0  1,0  2,0  3,0
0,1  1,1  2,1  3,1  4,1
  0,2  1,2  2,2  3,2
```

Since I'll be converting a plain 2d map onto it (here's an [example]("http://www.ubuntu-pics.de/bild/4038/screenshot_01_B0nTRO.png")). Would the code still work then?

---

### Post by PC-XT on 2008-10-05
You can try the first one I gave for that. The second is for making a rectangular map look rotated so you're looking at it from one corner. Your coordinates are a bit different in that the first line is indented rather than the second as in mine. You could change that by editing (y&1)==0? in the t.setAttribute "style" line to (y&1)==1? (changing the 0 to a 1) if you prefer to indent the first line instead.

Some notes:
If you use coordinates that the browser won't scroll to, you can add an offset to x or y in the beginning of the function as a quick fix.
Be sure you have the images as described in the comments, or the calculations will be off: [IMG]http://www.gamedev.net/reference/articles/taniso/MouseMapIso.gif[/IMG] (colored areas should be transparent) You can change width and height of the pictures, but also change them in the code. You can change width and not height or visa versa. (If they are just a bit off, you can try changing Math.round to Math.floor, which may work better for some images.) I don't have the img tag attributes setting size in the function, but you can add them with```
t.setAttribute("width", w);
t.setAttribute("height", h);
```in the same place as the other t.setAttribute statements to enforce the images to that size.

So the function I propose is```
function isoMapAdd(map,src,x,y){
//map is the element to hold the map,
// like a div or other containing block.
// This is not the id, but can be found by
// using the id in document.getElementById(mapid)
var h=16, w=20;//Height and Width of map images
// (the images should have transparent corners,
// and the corners of the non-transparent diamond should
// meet each edge of the image at its midpoint)
var t=document.createElement("img");
t.setAttribute("src", src);
t.setAttribute("width", w);
t.setAttribute("height", h);
t.setAttribute("style", "position:absolute;top:"+Math.round(y*h/2)+";left:"+Math.round(x*w+((y&1)==1?w/2:0)));
map.appendChild(t);
}
```BTW, this fixes a typo I found in the previous code I posted, where I typed x*w/2 instead of just x*w which would throw the calculations off and make the map squished. The other function, for a rotated rectangular coordinate system, also had a couple errors, so I edited both the functions.

To clear either map, set the innerHTML property of the map element to "".

---

### Post by killercow on 2008-10-06
Hi,

Im the owner for "Freevolution" mentioned above, and if you still want it, i can send you the code.

The license is GPL, and I hosted some of it on launchpad.net a while ago (might upload a new version)

---

### Post by PC-XT on 2008-10-06
Great code, killercow! I never saw a better one in JS.

BTW, if anyone does happen to use mine, I found a hack that allows better 3D type mapping (though ground level still is flat) by leaving out the```
t.setAttribute("width", w);
t.setAttribute("height", h);
```part and making h the height of the diamond, instead of the whole image, and making a place above the diamond for high-rises, trees, etc. [IMG]http://www.gamedev.net/reference/articles/taniso/GreenIso.gif[/IMG] All the images would still need to be the same size, and the diamonds should be the same size. The bottom corners should stay transparent, (unless you want to hack something,) but you can build higher from the level ground, making only the background transparent. The only side-effect is that the map appears slightly lower (by the amount added over the diamond) than if you used totally level graphics.

[Here's a demo I made.]("http://h1.ripway.com/qbasic010/public/isomap/isomap.html") I also added z-indexing to the functions above so this will work with them.

---

