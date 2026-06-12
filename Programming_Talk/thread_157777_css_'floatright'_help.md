---
title: "css 'float:right' help"
date: 2006-04-09
forum: Programming Talk
---

### Post by DirtDawg on 2006-04-09
I'm attempting to build a website using only css, which I am unfamiliar with, but learning. 

I've created a few classes for pictures to make it easier on myself whenever I need to place one. A class for left, center, and right assignments as well as a caption class.

In practice, things aren't working as well as I'd like. The pic.lft and pic.cntr classes (for floating left, centered) seem to work great, but the pic.rght causes text to appear way out of whack. 

Please see what I'm talking about here:
[http://www.weeklyhilarity.com/csshelp/home.html](http://www.weeklyhilarity.com/csshelp/home.html)
 
I've scoured my code but can't find any problems. I thought perhaps Firefox was screwing up, but the same thing happens in Opera. I think what it comes down to is a lack of understanding, on my part, of how css works. 

 I've also checked google, but finding info on this particular problem is difficult, to say the least. I know there's likely an html forum, but I like you guys better and thought maybe I could pick your brain.

Any help would be appreciated, Thank you.


Below is the relevent css code, though the entire file can be found here:
[http://www.weeklyhilarity.com/csshelp/master.css](http://www.weeklyhilarity.com/csshelp/master.css) 

```

#pic
	{
		border: 0;
		padding-left: 3px;
		padding-right: 3px;
		padding-bottom: 0px;
		padding-top: 3px;
	}


#pic p
	{
		text-align: center;
		font-style: italic;
		font-size: smaller;
		color: #00aeed;
	}

#pic.cntr
	{
		display: block;
		margin-left: auto;
		margin-right: auto;
	}

#pic.lft
	{
		float: left;
		padding-right: 7px;
	}
	
#pic.rght
	{
		float: right;
		padding-left: 7px;
	}

```

EDIT: Fixed broken links

---

### Post by orlox on 2006-04-09
I downloaded your page and fixed it. The problem wasn't on the code you show here, but on the part of the css that refers to the paragraphs. there you asign a right margin, wich will generate a separation from a picture that floats to the left. So, I changed that and something on the body to make it look the way it should:
```
body
	{
		position:absolute;
		left:150px;
		background-image: url(Images/spade.gif)
	}

p
	{
		font-size: 15px;
		color: #a4d4b0;
		margin-top: 15;
		margin-right: 20;
		margin-left: 20;
		text-align: justify;
		text-indent: 15;
	}
```
basically, I changed the right margin of the paragraphs (wich was at something like 180px, and the positioning of the body)

---

### Post by DirtDawg on 2006-04-09
Oh, that did it! Thank you. 

I haven't quite figured out the hierarchy system yet (obviously). I also didn't realize the body itself could be positioned. Very cool.

Thanks for taking the time to help, it's appreciated.

---

