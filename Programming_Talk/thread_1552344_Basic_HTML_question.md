---
title: "Basic HTML question"
date: 2010-08-13
forum: Programming Talk
---

### Post by anewguy on 2010-08-13
I don't know if I'm in the correct forum or not, but it was the closest thing I could find for the question.

I have noticed that if I use frames on a web page, specifying percentages of the screen for the size, that the pages don't "auto-size" depending on the resolution.  If I build a page that looks good in 800x600, going to something larger keeps the page the same size with white space around it.

Is there some way with frames to make it auto-size?

Thanks in advance!

Dave ;)

---

### Post by durand on 2010-08-13
I ended up writing some js to do that. Something like this should do the trick:
```

<script type="text/javascript" >
document.body.onresize=function() {
document.getElementById('id_of_iframe').style.width="20%";
}
</script>

```

---

### Post by durand on 2010-08-13
Make that "window.onresize". It seems to work in more browsers.

---

### Post by teryret on 2010-08-14
Do not use frames.

I repeat: do not use frames.

I don't know what you're trying to do, but I do know that you don't need frames for it.  iframes are okay, just not the regular 1998 geocities html3 atrocities that some of us can't scrape from our memories.

I realize this doesn't answer the question you asked, but if you had asked "Is this a good technique for tripping random strangers in busy crosswalks?" I'd have probably diverted the question similarly.

---

### Post by simeon87 on 2010-08-14
> **teryret said:**
> Do not use frames.

I repeat: do not use frames.

I don't know what you're trying to do, but I do know that you don't need frames for it.  iframes are okay, just not the regular 1998 geocities html3 atrocities that some of us can't scrape from our memories.

I realize this doesn't answer the question you asked, but if you had asked "Is this a good technique for tripping random strangers in busy crosswalks?" I'd have probably diverted the question similarly.

+1. Whatever you do, get rid of the frames. They're on the way out.

---

### Post by nvteighen on 2010-08-14
There's a nice alternative that might give you a really classy look: playing with fixed position divs and depths. The idea is similar to the "layers" approach you use in photo manipulation software: you construct a div for each "frame", plus the div for your text area (which should not be fixed so it scrolls). The effect will be that the fixed divs will eventually be above the text when scrolling, thus simulating a frame.

---

### Post by ehsannp on 2010-08-14
try to design your tables and divs with percentage instead of pixel.
for example u can use <div style="width: 100%">your content</div>

---

### Post by anewguy on 2010-08-18
Everything was done with frames because it worked.  All frames were desribed as percentages of the screen.

I think I had things reversed in my original post though, so I should explain:

[LIST]
[*]a small top section of the screen is devoted to a menu that remains the same for every page
[*]a section of the left side of the screen is devoted to information that doesn't change
[*]the larger frame in the rest of the screen is what changes from page to page.  So, it easy to define links with target= to that frame and avoid all kinds of duplicate html per page and there is no need to reload the menu and left sections for each "page".
[/LIST]

I'm no expert at any of this - this is what I knew how to do from the past.  The biggest problem is that there is text and on-mouse-over images in the top menu, so when you go from one screen size (in this case 1024x780) to a smaller resolution (800x600), you end up with scroll bars in the menu and the left portion of the screen.  Building the text and mouse-over images for 800x600 then results in white space when going to a higher resolution.

So, if there is some way to not use frames, but still maintain only 1 definition of the menu and left side (and consequently only 1 loading as everything else goes to the "main" frame), have pages that work in multiple resolutions without adding scroll bars or white space, then that's what I need.

Please, while I appreciate your wisdom, don't condemn me for using the only thing I knew to make something work - and it does work as intended.  The multiple resolution support is what is messing things up.

Dave ;)

---

### Post by teryret on 2010-08-19
If I were you I'd look at using jQuery to AJAX in the main body and then replace the current one with that.  Even if you've never written a line of javascript before, it's so easy to do with jQuery there's really no reason not to.  

For example, if you're doing a good layout you're going to have plenty of divs, and for the sake of the example one of them will have id="gladImNotAFrame", and further that the page you want the contents of is called newPage.html.  The jQuery to do the AJAXing for you is:

```

$("#navButton").click(function (){
    $.ajax({
       url: "http://www.example.com/newPage.html",
       data: {},  //if you need to pass get args to newpage this is how you do it
       success: function(data){
          $("#gladImNotAFrame").html($(data).find("#gladImNotAFrame").html());
       },
       dataType: "html"
    });
}

```

As for having one definition of the top bar etc look at either PHP, ASP.NET, or SHTML ([http://en.wikipedia.org/wiki/Shtml](http://en.wikipedia.org/wiki/Shtml)).

Getting nice nav is a tricky business, but the way I prefer is to have an image with no text that is much much wider than you need, then set that as the background image of a li, fill the li with the text of the button and a div that has the very thin image for the other side of the tab.  The result is buttons that resize automatically as the text size changes, look good from an SEO perspective, and work in every browser (even the lamentable ones).  I realize this is pretty high level, but I don't know exactly what you're trying to do so I'm covering bases.

---

### Post by worksofcraft on 2010-08-19
> **anewguy said:**
> ...
So, if there is some way to not use frames, but still maintain only 1 definition of the menu and left side (and consequently only 1 loading as everything else goes to the "main" frame), have pages that work in multiple resolutions without adding scroll bars or white space, then that's what I need.


Yes, I would like to know about that too, cuz I've seen people use lots of fancy css to get the same effect, but what I hate about their solution is the way every single page on the site duplicates all their navigation links!

Whenever they want to change something like adding a link they have to go edit **all** of their pages. While much maligned by puritans, frames do let you have just **one** single site navigation .htm that you bung in one of the frames for the whole site.

Never throw out dirty bath water when the baby is still in the bath :lolflag:

---

### Post by teryret on 2010-08-20
If you do it in SHTML (or any other serverside processing language/framework) you get one nav file to share across whatever you would have it shared across.

One big problem with frames is that they don't really make any semantic sense.  Why is it that "a page" isn't actually a page, but is instead three pages that are carefully aligned with one another and only barely interacting with one another?  For example: each frame has a different title, abuah?!

Another problem is that frames are inherently slower, and not just a little bit slower, a lot slower.  These days putting a few KB of html onto the network takes less time than waiting for the first bit of that response to get from the server back to the client.  This means that to improve perceived speed the data size isn't the problem, it's the number of get requests you make, and each frame makes 1 for html, 1 for css, 1 for each image (doesn't actually have to, but that's a more advanced technique), and 1 for javascript.  You could then make the download take a third of the time by not using frames.

Another is that they can't be made anywhere near as pretty as any of their competing technologies.

Another is that being forced to maintain backwards compatibility with ancient techniques impedes progress.

---

### Post by anewguy on 2010-08-20
But when you're running a cheap account you may not have access to all the tools you mention.  It also appears to require more knowledge than I have, and this was done for someone's small business where they have to maintain it and they know less than I do.  I don't mean to tick anyone off, it's just that I only have a basic knowledge of all of this from years ago, and not sure how much I really need to know at this point in my life (54, on disability, only did this 1 small site recently as a favor for some friends and their small business).  There is some javascript already in the page, and I was thinking of trying to use something like the java screen.width to test the screen size and adjust the images in the frame.

As far as frames running slow, in this particular instance there absolutely no noticable difference.  Everything pops up quick and the load into the main frame is especially fast.  Perhaps this is because everything is fairly simple, in some cases EXTREMELY simple, in each of the frames and what gets posted into main (slideshow, images and text).

Please keep the ideas and thoughts coming!

Thanks so far to everyone!

Dave ;)

---

### Post by Hellkeepa on 2010-08-22
HELLo!

Nearly *every**cheap web host have PHP installed on their servers, so using PHP includes is almost a given. If not, then SSI (Server Side Includes) is a standard Apache feature, and while ancient should still work.

As for using CSS, that's client only, and as such totally irrelevant what host you use.

Now, to make the menus like you described, and to have them stay in place even if the page is scrolled. I present you with a quick and dirty example:
```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>

<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
<title>Insert title here</title>

<style type="text/css">
* {
	margin: 0;
	padding: 0;
}

div.navbar {
	height: 60px;
	width: 100%;
	position: fixed;
	top: 0px;
	left: 0px;
}

div.navbar ul {
	list-style-type: none;
}

div.navbar ul li {
	float: left;
}

div.content {
	margin-left: 170px;
}

div.information {
	width: 150px;
	position: fixed;
	top: 60px;
	left: 0px;
}
</style>

</head>
<body>

<div class="navbar">
	<ul>
		<li><a href="#">Link 1</a></li>
		<li><a href="#">Link 2</a></li>
		<li><a href="#">Link 3</a></li>
		<li><a href="#">Link 4</a></li>
	</ul>
</div>
<div class="content">
	<p>This is where the content goes.</p>
	<p style="margin-top: 1000px">Added a scroll here, just to show how things works</p>
</div>

<div class="information">
	<p>Here you have the information for the left side, less important than the content, thus displayed below it.</p>
</div>

</body>
</html>
```
Happy codin'!

---

