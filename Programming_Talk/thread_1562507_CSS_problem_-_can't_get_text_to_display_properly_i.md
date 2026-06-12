---
title: "CSS problem - can't get text to display properly in popup"
date: 2010-08-27
forum: Programming Talk
---

### Post by themusicalduck on 2010-08-27
This isn't exactly a programming problem but hopefully someone might know the answer.

I have made some links on a website page that popup a little information box. The problem is that I don't know how to format the text that is displayed in the popup.

This is the code I have in the .css file

```
#blanket {
background-color:#111;
opacity: 0.65;
filter:alpha(opacity=65);
position:absolute;
z-index: 9001;
top:0px;
left:0px;
width:100%;
}
#popUpDiv {
	position:absolute;
	background-color:#FFF;
	opacity: 0.80;
	filter:alpha(opacity=80);
	width:500px;
	z-index: 9002;
	font-family:Tahoma, Geneva, sans-serif;
	color:#000
}
```

This is what I put in the html

```
<div id="blanket" style="display:none;"></div>
<div id="popUpDiv" style="display:none;">
<a href="#" onclick="popup('popUpDiv')">Close</a>Text here
</div>
<a href="#" onclick="popup('popUpDiv')">Info...</a></p>
```

I essentially used the demo here [http://www.pat-burt.com/web-development/how-to-do-a-css-popup-without-opening-a-new-window/](http://www.pat-burt.com/web-development/how-to-do-a-css-popup-without-opening-a-new-window/) but it only says how to make the popup and not how to actually enter text..

In the part where it says "Text here" the text will appear in the box, but I want to have the text below the "Close" link and preferably have justify alignment for all text as well. At the moment the text just runs on from the Close link on the same line.


Thanks.

---

### Post by Bachstelze on 2010-08-27
> **themusicalduck said:**
> 
In the part where it says "Text here" the text will appear in the box, but I want to have the text below the "Close" link and preferably have justify alignment for all text as well. At the moment the text just runs on from the Close link on the same line.

Someting like

```
<a href="#" onclick="popup('popUpDiv')">Close</a>
<p>Text here</p>
```



> Also, I was wondering if it's possible to change the colour of links in the popup box only. At the moment I have ```
a img {border: none; }
a:link { color:#000; } 
a:visited { color:#69F }
``` at the top of the .css file but if I put a:link { color:#FFF; }  into #popUpDiv then it doesn't change it.

You want:
```
#popUpDiv a img {border: none; }
#popUpDiv a:link { color:#000; } 
#popUpDiv a:visited { color:#69F }
```

---

### Post by themusicalduck on 2010-08-27
Thanks! Worked perfectly.

I though it was something like using </p> tags, but I was not putting them in the right place.

Found a fix for the other problem too and I worked out how to justify the text as well so all sorted.

Thanks again.

---

