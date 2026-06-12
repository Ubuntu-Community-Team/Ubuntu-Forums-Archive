---
title: "Overlapping Images in a website"
date: 2009-05-06
forum: Programming Talk
---

### Post by enduser000 on 2009-05-06
Hello,
     I am currently trying to develop a simple website just for me (info, code, interests, etc).  I made some image borders, and some text.  I used gimp to make sure  the background is transparent.  I now want to pick a border for the text and put them on top of each other (because then it will be like one image).

I've been to a few websites looking this up and so far have found two good ones, [here]("http://www.w3schools.com/Css/tryit.asp?filename=trycss_zindex2") and [here]("http://www.commadelimited.com/code/overlapimages/").

The problem I'm having is that I want to have this 2 image combo on the top middle of my page (for the banner) and along the left side (for the navigation buttons).  It dosen't seem to want to do that (I'm assuming it's because of the "position: absolute" attribute.  Does anyone know of a way to do this in php or css or html?  Those are the three I'd like to use with this site.  Thanks for looking,

enduser

---

### Post by enduser000 on 2009-05-11
Ok,
  So I've messed with it a bit and found out a little more about the problem.  It works fine with this code:
```

<head>
    <style type="text/css">
        img.front {
            position: absolute;
            left: 0px;
            top: 0px;
            z-index: 10;
        }

        img.halfsize {
            height: 33%;
            width: 33%;
            padding: 0;
        }
    </style>
</head>

<body>
    <center>
        <div style="position: relative;">
            <img class="front" src="images/home_banner_text0.png" />
            <img src="images/banner_splash6.png" />
        </div>
    </center>
</body>

```

BUT, if I use the class "halfsize (or if I use height="" or style="height: XX%;", or any other way I can think of doing it) it squishes one image and doesn't correctly overlap them.

I also noticed It doesn't let me use <center></center> tags to center the whole thing.  Could this be because I'm using tables to put the page together?  How could I make this work?  Thanks for taking a look,

enduser

---

### Post by Reiger on 2009-05-11
If you just wish to stack exactly 2 images, you can use the background-image property on the image element. If the top image is transparent, the background should "see through":

In CSS:
```

#backed { 
  background-image: url('mybackground.png'); /* our background texture */
  background-position: center; /* center the image, read up on this property on w3c schools for instance */
  background-repeat: no-repeat; /* avoid repetition in case the background image is smaller than the overlay */
}

```

In XHTML:
```

<img id="backed" src="myoverlay.png" alt="this is an example of background effects" />

```

If you want arbitrarily many images stacked on top this way, you will want to (a) use this thechnique with nested <div> elements or use relative positioning:

```

<img src="mytexture" alt="" style="float:left; width: 50px; height: 50px;" />
<img src="myoverlay" alt="an example of stacking multiple images on top of each other, using positioning" style="float:left; position:relative; top: 0px; left: -50px; width: 50px; height: 50px;" />

```

---

### Post by enduser000 on 2009-05-12
Getting closer,
      That works if I don't scale the image at all.  I was having trouble scaling using %s so I think I'll just use px units from now on.  I can't seem to scale the background image If I do it that way, but if I use the <div> way I can't seem to get them in the same spot, or one will be squished.  If I don't scale at all it works great.  I can use the css with background-image: url(''); and put <center> around the <img> tags to center it.  This is what I'm looking for, but ideally I would like to be able to scale either with px or %.  Thanks so far,

enduser

---

### Post by tturrisi on 2009-05-13
The <center> tag is depreciated, don't use it.

```
<div style="text-align:center; width:00px; height:00px">
	<div style="position:relative; top:00px; left:00px"><img src="" width="" height="" alt="" style="z-index:1"></div>
	<div style="position:relative; top:00px; left:00px"><img src="" width="" height="" alt="" style="z-index:2"></div>
	<div style="position:relative; top:00px; left:00px"><img src="" width="" height="" alt="" style="z-index:3"></div>
</div>
```

---

### Post by hessiess on 2009-05-13
> **tturrisi said:**
> The <center> tag is depreciated, don't use it.


ALL formatting tags are depreciated;)

---

### Post by enduser000 on 2009-05-13
Ok...
   So is there a list of what I should use?  I want to write the most portable and up-to-date code possible.  As I am just starting, this is a good time to find out what that is.  Using that last part:
```

		<div style="text-align:center; width:00px; height:00px;">
			<div style="position:relative; top:00px; left:00px;"><img src="path/to/banner0.png"
			width="250" height="100" alt="" style="z-index:1"></div>
			
			<div style="position:relative; top:00px; left:00px;"><img src="path/to/home_banner_text0.png"
			width="250" height="100" alt="" style="z-index:2"></div>
		</div>

```

I get one image above the other on the left side of the screen, though they are scaled.  Any more ideas? :P.  I'll keep looking too,

enduser

---

### Post by hessiess on 2009-05-13
> **enduser000 said:**
> Ok...
   So is there a list of what I should use?  I want to write the most portable and up-to-date code possible.  As I am just starting, this is a good time to find out what that is.  Using that last part:
```

		<div style="text-align:center; width:00px; height:00px;">
			<div style="position:relative; top:00px; left:00px;"><img src="path/to/banner0.png"
			width="250" height="100" alt="" style="z-index:1"></div>
			
			<div style="position:relative; top:00px; left:00px;"><img src="path/to/home_banner_text0.png"
			width="250" height="100" alt="" style="z-index:2"></div>
		</div>

```

I get one image above the other on the left side of the screen, though they are scaled.  Any more ideas? :P.  I'll keep looking too,

enduser

You should use CSS classes in an external style sheet instead of using the style="" attribute, it makes the code MUCH easier to maintain in the long run.

HTMLdog is a good referance for wrighting standards complient HTML.

---

### Post by enduser000 on 2009-05-16
Ok,
   I'm now using an external style sheet and some other things that work pretty well.  I'm still having problems with some things with images.  If I scale down the images that I want to overlap, they have problems (see attached). Any ideas?

enduser

---

### Post by enduser000 on 2009-05-18
Ok...
  So I've been messing with it and don't get that error anymore, in fact I've decided to use px units for the images and can get the successfully overlapped and scaled now.  The only problem I'm having now is with centring them both.  Here's the code I'm working off, I've put the css in the tags with the style="" element, but am going to put that into a separate css file later.  Any tips are appreciated, here's the code:
```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
		<link rel="stylesheet" type="text/css" href="style.css" />
    </head>

    <body>
		<div style="position: relative;">
			<img style="position: absolute; top: 0px; left: 0px; z-index: -1; width: 125px; height: 50px;" src="images/legacy/banner0.png" />
			<img style="width: 125px; height: 50px;" src="images/legacy/home_banner_text0.png" />
		</div>
	</body>
</html>


```

Thanks,

enduser

---

### Post by enduser000 on 2009-05-22
I've been making progress...

I got some stuff down, and decided to put some of the stuff I was trying to use through the [css validator]("http://jigsaw.w3.org/css-validator/") and see if it's all valid.  This is what I'm getting:

Parse Error  // img classes img.behind { position: absolute; top: 0px; left: 0px; z-index: -1; }
Parse Error // div classes div.center { text-align: center; } 

I've attached images of what I can get, I can get them overlapped but not centered, or I can get one of them centered and not overlapped.

Mind taking another look?

enduser

Edit: found out that the problem was the comments "//", but it still dosen't work

---

### Post by enduser000 on 2009-05-23
Got it done, here is the code if you're wondering:
```

main.html:

<div class="relative center">
	<img class="behind banner" src="images/legacy/banner4.png" />
	<img class="banner" src="images/legacy/home_text0.png" />
</div>


style.css:
img.behind {
	text-align: center;
	position: absolute;
	z-index: -1;
}

```

Thanks again for all your help ^^

enduser

---

