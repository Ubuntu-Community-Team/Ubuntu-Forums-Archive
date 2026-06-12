---
title: "IE6 and :hover"
date: 2007-04-16
forum: Programming Talk
---

### Post by ironfistchamp on 2007-04-16
Hey all

Got a webdev, IE6 issue I would really like some help with. Anyway, my friend designed a funky looking homepage that works perfectly in Firefox (damn right it does) but not so great in IE. Basically he has a link with a nested span tag that has display:none in its style. Well in Firefox we can do 


a:hover span {dsiplay:inline;}

Works perfectly. Doesn't work at all in IE6. Is there a work around. I can't make head nor tail of the things on the net. I would love to do this without JS..possibly use the hover.htc I've seen floating around. Can anyone give me any help/advice/soultions?

Thanks

Ironfistchamp

---

### Post by nautilus on 2007-04-16
i would suggest using a div, and hiding that, but it's just a shot in the dark.

---

### Post by ironfistchamp on 2007-04-16
Thanks for the reply. I have found out with a bit of tinkering that the problem arrises when I put the containing div's (or without a div, the link's) positioning to absolute. The thing is that if I dont position it absolutely the design doesn't work at all.


Anyone got a work around?

Thanks

Ironfistchamp

---

### Post by Slim Odds on 2007-04-16
> **ironfistchamp said:**
> 
a:hover span {**dsiplay**:inline;}

How about spelling "display" correctly?   That might help.

---

### Post by Mirrorball on 2007-04-16
If you post the code here, we will be able to help you better.

---

### Post by ironfistchamp on 2007-04-16
haha good catch there Slim Odds. It is spelt correctly in the code. Like I said it is because I am positioning the div absolutely. I shall post the relevant sections of the code below. 


CSS
```


//styling
div#text_home  {
		position:absolute;
		font-size:29px;
		top: 14%;
		left: 18%;
		}

a {color: #FF00FF;}
a:hover {color: #000;}
a span{display: none;}
a:hover div{display: inline;}


```

HTML
```


<div id="text_home"><a id="text_home" href="./news.html">News
			<span>Here is the news</span></a></div>

```


Like I said if I remove the absolute statement it works perfectly. Put it in and it all messes up.

---

### Post by Paul41 on 2007-04-16
What exactly is the problem? For me it looks the same in Ff and IE.

---

### Post by ironfistchamp on 2007-04-16
Hmm I can't seem to replicate it. It is only in that one file. This will drive me insane. Perhaps a rethink on the design. 

Thank you anyway

Ironfistchamp

---

### Post by goghgoner on 2007-04-16
here's the code i use for popout menus. sorry, i am no good at web development but i think this can be modified to work for you. i keep the javascript in an external file "iehover.js" and use the class names assigned to the list items (in your case an anchor) in the script. i haven't moved this to production, yet, so I can't send you the link. 

in web page:
```
<script src="iehover.js" type="text/javascript"></script>
<script type="text/javascript">
	window.onload = IEHoverPseudo;
</script>
```

in iehover.js:
```
function IEHoverPseudo() {
	
	var navItems = document.getElementById("popmenu").getElementsByTagName("li","ul");
	popmenu.HideDelayTime = 1;	// seconds
	for (var i=0; i<navItems.length; i++) {
		if(navItems[i].className == "menuparent") {
			navItems[i].onmouseover=function() { this.className += " over"; }
			navItems[i].onmouseout=function() { this.className = "menuparent"; }
		}
		else if (navItems[i].className == "secondparent") {
			navItems[i].onmouseover=function() { this.className += " secondover"; }
			navItems[i].onmouseout=function() { this.className = "secondparent"; }
		}
	}
}
```

---

### Post by ironfistchamp on 2007-04-16
Thank you goghgoner  

I shall take a look and see what can be done.

Ironfistchamp

---

