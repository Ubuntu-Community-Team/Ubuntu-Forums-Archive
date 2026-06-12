---
title: "Facebook picture downloader -- Greasemonkey (javascript)"
date: 2007-11-02
forum: Programming Talk
---

### Post by mrpeenut24 on 2007-11-02
I'm working on a Greasemonkey script to go through a Facebook user's photo album and download every picture in the album.  (I plan on doing a photographic mosaic for my girlfriend for Christmas.)  The only problem is, I'm not sure if javascript has the ability to download a file directly.

Here's what I *do* have:
```
// ==UserScript==
// @name           Facebook Photo Downloader
// @author         mrpeenut24
// @description    A script to download all files from a facebook photo album
// @include        *facebook.com/photo.php*
// ==/UserScript==
x = document.getElementById("myphoto").src;
win1 = window.open(x);
y = document.getElementById("myphotolink").href;
window.location = y;

```What this will do is pop open a new tab of the picture (or window, depending on your FF settings) and then change the page to the next picture, whereupon the script will be called again.  This does an incredibly good job for only four lines, and it seems I only need something that will download the jpeg image instead of opening up a new window with it.  I've tried an FF addon called Bazzacuda, which saves all images in open tabs, but after saving, then closing the tabs, FF starts blocking the facebook 'popups'.  I tried editing the MIME-type settings to force it to download all jpeg images, and the settings are reflected in FF, but it's not actually downloading the images.  As you may be able to tell, this doesn't have to be restricted to a Greasemonkey script, although I would prefer it, but it *should* be automated.

---

### Post by mrpeenut24 on 2007-11-04
Does anyone know if it's even possible for javascript to download files?  What I would like it to do is download it directly to a directory.  I have a feeling that it can't as this would pose a serious security risk, but if it's possible, that would be great!  (I've heard it's possible when the javascript is running locally.)

---

### Post by henchman on 2007-11-05
afaik this is not possible with javascript :/

you will have to write a standalone program...

---

### Post by egibby on 2007-11-09
I know this doesn't solve the javascript problem that you have, but if all you want to do is download pictures from facebook, you can try this program:  [FaceDown]("http://www.vincentcheung.ca/facedown/")

There used to be an extension for Firefox that would also let you download pictures off of facebook, but I don't think it works anymore.  At least it didn't work for me.


-- egibby

---

### Post by mrpeenut24 on 2007-11-11
> **egibby said:**
> I know this doesn't solve the javascript problem that you have, but if all you want to do is download pictures from facebook, you can try this program:  [FaceDown]("http://www.vincentcheung.ca/facedown/")

...

-- egibby

That works great!  Thanks!

---

