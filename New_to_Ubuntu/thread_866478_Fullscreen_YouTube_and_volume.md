---
title: "Fullscreen YouTube and volume"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by trailofdead on 2008-07-21
I searched but couldnt find anything about this.  I'm new to linux so I'm sorry if this has already been answered.  

When I adjust the volume, there's an onscreen display showing the volume level.  When I have full screen youtube, the onscreen volume display exits full screen youtube.  What can I do so it doenst exit the full screen?  Also, where can I adjust all the onscreen displays such as volume control, brightness, etc.  I'm using Hardy and Opera 9.51.

Thanks.

---

### Post by Polygon on 2008-07-21
flash itself has some problems on linux, so it might be a problem with the linux build of flash that is causing youtube to exit full screen mode when you adjust the volume

also i dont understand your second question, you mean where to adjust the screen brightness and the volume control?

---

### Post by ice60 on 2008-07-21
i use this with youtube and opera, maybe it will help?? it makes the picture bigger, but not all the way to full screen. -
[http://userstyles.org/styles/3180](http://userstyles.org/styles/3180)
[http://userstyles.org/styles/userjs/3180/Youtube%20Video%20Resizer.user.js](http://userstyles.org/styles/userjs/3180/Youtube%20Video%20Resizer.user.js)

the site had exceeded it's bandwidth when i just tried those links to check it's the right script, but this is it here -

```
// ==UserScript==
// @name          YouTube - Video Resizer (Fixed April 10th, 2008)
// @namespace     http://userstyles.org
// @description	  This style is meant for YouTube.co
// @author        Diddle
// @homepage      http://userstyles.org/styles/6420
// @include       http://youtube.com/*
// @include       https://youtube.com/*
// @include       http://*.youtube.com/*
// @include       https://*.youtube.com/*
// ==/UserScript==
var css = "@namespace url(http://www.w3.org/1999/xhtml); #movie_player { width: 874px !important; height: 688px !important; } #watch-other-vids { padding-top: 700px !important;}";
if (typeof GM_addStyle != "undefined") {
	GM_addStyle(css);
} else if (typeof addStyle != "undefined") {
	addStyle(css);
} else {
	var heads = document.getElementsByTagName("head");
	if (heads.length > 0) {
		var node = document.createElement("style");
		node.type = "text/css";
		node.appendChild(document.createTextNode(css));
		heads[0].appendChild(node); 
	}
}
```
you put that code in a directory, i put mine here, and named it **youtube_resizer.js** -
**~/.opera/my_userjs**
then tell opera where to find it at -
Tools>Preferences>Advanced>content>Javascript Options>Under where it says User Javascript Files, in that box. i put the full path (NOTE if you do use this use your username and not mine :P)
/home/iceni60/.opera/my_userjs/

here's who it looks -

[[IMG]http://img108.imageshack.us/img108/6196/operayoutubeos3.th.png[/IMG]](http://img108.imageshack.us/my.php?image=operayoutubeos3.png)

---

### Post by trailofdead on 2008-07-22
In my second question, I was asking where I could adjust the settings for OSD or possibly disable it.  


ice, not quite what I'm looking for, but I'll look into that.

---

### Post by hedrian on 2008-07-22
err how can i adjust the system volume?

---

### Post by zachalekos on 2008-08-01
> **trailofdead said:**
> I searched but couldnt find anything about this.  I'm new to linux so I'm sorry if this has already been answered.  

When I adjust the volume, there's an onscreen display showing the volume level.  When I have full screen youtube, the onscreen volume display exits full screen youtube.  What can I do so it doenst exit the full screen?  Also, where can I adjust all the onscreen displays such as volume control, brightness, etc.  I'm using Hardy and Opera 9.51.

Thanks.

[http://ubuntuforums.org/archive/index.php/t-471599.html](http://ubuntuforums.org/archive/index.php/t-471599.html)

This might answer your question about the volume pop up. It doesn't help much though.
Been searching for a way to disable it myself, but there seems to be no much interest.

---

### Post by surrealize on 2010-04-27
It's a bug in flash.  The main thing (that I know of) that you can do at this point is vote for the bug in the adobe bug tracker:

[http://bugs.adobe.com/jira/browse/FP-902](http://bugs.adobe.com/jira/browse/FP-902)

also related:

[http://ubuntuforums.org/showthread.php?t=1294251](http://ubuntuforums.org/showthread.php?t=1294251)

---

### Post by surrealize on 2010-04-27
oops, didn't mean to bump such an old thread.  Came here from a recent reddit post.

---

### Post by arnab_das on 2010-04-27
you need to modify a file.

[http://explore-ubuntu.blogspot.com/2010/01/ultimate-flash-fix-for-ubuntu.html](http://explore-ubuntu.blogspot.com/2010/01/ultimate-flash-fix-for-ubuntu.html)

always worked for me. golden trick. thats the first thing i do after installing flash.

---

