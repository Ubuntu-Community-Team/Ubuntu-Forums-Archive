---
title: "'Crop' Images Using a Div and CSS?"
date: 2007-01-28
forum: Programming Talk
---

### Post by smartbei on 2007-01-28
Hello, I am trying to use JavaScript to make a 5-star standard rating feature with one additional property: Assuming the rating is 3.35, I want it to show 3 stars and 35% of the last star.
Here is the code I have tried with this:
```
<html>
<head><title>Testing!</title></head>
<script>
function putStars(r) {
	var fin = '';
	if (r > 5) r=5;
	else if (r < 0) r=0;
	s = Math.floor(r);
	for(var i = 0; i < s; i++) {
		fin += '<img src="staralone.gif" />';
	}
	if ((r-s) > 0)
		fin+='<img src="staralone.gif" width="' + Math.round((r-s)*16) + '" height="16"/>';
	document.getElementById('stars').innerHTML=fin;	
}
</script>
<body onload="putStars(3.5);">

<img src="00star.gif" style="z-index:0" /><div id="stars" style="position:relative; top:-16; z-index:1"></div>
</body>
</html>
```
But that looks like [IMG]http://img258.imageshack.us/img258/4540/untitledus2.png[/IMG]. As you can see, the last star is 'stretched', insted of its right side being cropped. How can I fix this?
I want exactly three and a half a gold stars to appear when the rating is 3.5, and the last one should be cropped on the right.

Thanks for the help guys!

Note - I haven't tested the code in anything but Firefox 2, sorry if that is a problem.

Here are the necessary files if you want to test it:
[IMG]http://img359.imageshack.us/img359/8373/00starsb9.gif[/IMG] - should be named 00star.gif
[img]http://img259.imageshack.us/img259/3531/staralonevt7.gif[/img] - should be named - staralone.gif

---

### Post by DirtDawg on 2007-01-28
One approach could be to control the size of the star's container rather than the star images themselves.

Maybe create a div for the stars, have the background of that div consist of a star gif of a precise size, like 20px wide(so: 5 stars X 20px = 100px). Then put the background image on repeat-x and chose the number of stars to display by changing the size of the div itself.
Example for 2.5 stars:
```

div#stars
    {
        background-image: url(/path/to/starimage.gif);
        background-repeat: repeat-x;
        width: 50px;
    }
```

Mind you, I'm assuming Javascript can manipulate the width of the 'stars' div.

---

### Post by smartbei on 2007-01-28
Great solution! With this I don't need the JavaScript at all. Thanks!
Here is the final code:
```
<html>
<head><title>Testing!</title></head>
<style>
#stars {
	position:relative; 
	top:-16; 
	background-image:url(staralone.gif);
	background-repeat:repeat-x;
	z-index:1;
	width:56;
}
</style>
<body>
<img src="00star.gif" style="z-index:0" /><div id="stars">&nbsp;</div>
</body>
</html>
```

---

### Post by finer recliner on 2007-01-28
this may be simpler than you think.

try using some CSS in a fashion similar to this button rollover tutorial:
[http://www.tutorio.com/tutorial/pure-css-image-rollovers](http://www.tutorio.com/tutorial/pure-css-image-rollovers)

all 3 states of the button are on 1 image. CSS will display only part of the image (specified by which state you are in).

in your case, you would have 1 image that has a full star on it, and a half star.

good luck

---

### Post by smartbei on 2007-01-28
> **finer recliner said:**
> this may be simpler than you think.

try using some CSS in a fashion similar to this button rollover tutorial:
[http://www.tutorio.com/tutorial/pure-css-image-rollovers](http://www.tutorio.com/tutorial/pure-css-image-rollovers)

all 3 states of the button are on 1 image. CSS will display only part of the image (specified by which state you are in).

in your case, you would have 1 image that has a full star on it, and a half star.

good luck
Yes, that is the obvious way to do it, but I want to be able to show a greater resolution than 0.5.

---

