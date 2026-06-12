---
title: "Css .ne. Fortran..."
date: 2007-06-17
forum: Programming Talk
---

### Post by xtacocorex on 2007-06-17
Here is the low-down, I'm a FORTRAN/C++ programmer and I have taken over a website for a club I'm in.  I've done web stuff a long time ago, but CSS layouts are a new thing for me and I'm having trouble with my footer.  I've googled a bit, but haven't found anything worthwhile.

I currently have the footer at an absolute position, but I want it to be position based upon the bottom of the content and/or the link sections.

The site is [here]("http://www.rockwellcollinsclubs.com/clubs-ia/model-aviators/newsite/index.php"), not all of the links work yet, so if you browse, pick wisely.

Here is my CSS file:
```

<!--

body              {margin: 5px; padding: 5px; background-color: #D6DEDE; font-family: Arial;}

div.cmaheader     {position: absolute; width: 1000px; height: 112px;}

div.cmalinks      {position: absolute; padding: 2px; margin: 5px; width: 155px; left: 15px; top: 135px; background-color: #8EBBCB; border-top: dashed 2px #D6DEDE; border-bottom: dashed 2px #D6DEDE;}

div.cmafooter     {position: absolute; padding: 2px; margin: 2px; width: 1000px; top: 760px; background-color: #D6DEDE; text-align: right; border-top: dashed 2px #8EBBCB;}

div.cmacontent    {position: absolute; padding: 2px; margin: 5px; width: 800px; left: 185px; top: 135px; background-color: #E5E5E5; border-left: dashed 2px #8EBBCB; background-image: url(./images/txtbgnd.png); background-position: center; background-repeat: repeat-y;}

div.subcon1       {position: relative; padding: 2px; margin: 2px;}
div.line1         {width: 90%; border-bottom: dashed 2px #D6DEDE;}
div.line2         {width: 90%; border-bottom: dashed 2px #8EBBCB;}

a.sidebar:link    {color: #000000; text-decoration: none;}
a.sidebar:visited {color: #000000; text-decoration: none;}
a.sidebar:hover   {color: #FFFFFF; text-decoration: none;}

a.content:link    {color: #000000; text-decoration: none;}
a.content:visited {color: #000000; text-decoration: none;}
a.content:hover   {color: #8EBBCB; text-decoration: none;}

td.officers       {font-family: Arial; font-size: medium;}

!-->

```

Thanks in advance for any help.

---

### Post by Modred on 2007-06-17
try the following:

```
body {
background-color:#D6DEDE;
font-family:Arial;
margin:5px;
padding:5px;
}
div.cmaheader {
height:112px;
width:1000px;
}
div.cmalinks {
background-color:#8EBBCB;
border-bottom:2px dashed #D6DEDE;
border-top:2px dashed #D6DEDE;
float:left;
left:15px;
margin:5px 5px 5px 0pt;
padding:2px;
top:135px;
width:155px;
}
div.cmafooter {
background-color:#D6DEDE;
border-top:2px dashed #8EBBCB;
clear:both;
margin:2px;
padding:2px;
text-align:right;
top:760px;
width:1000px;
}
div.cmacontent {
background-color:#E5E5E5;
background-image:url(./images/txtbgnd.png);
background-position:center;
background-repeat:repeat-y;
border-left:2px dashed #8EBBCB;
left:185px;
margin:5px 5px 5px 165px;
padding:2px;
top:135px;
width:800px;
}
div.subcon1 {
margin:2px;
padding:2px;
position:relative;
}
div.line1 {
border-bottom:2px dashed #D6DEDE;
width:90%;
}
div.line2 {
border-bottom:2px dashed #8EBBCB;
width:90%;
}
a.sidebar:link {
color:#000000;
text-decoration:none;
}
a.sidebar:visited {
color:#000000;
text-decoration:none;
}
a.sidebar:hover {
color:#FFFFFF;
text-decoration:none;
}
a.content:link {
color:#000000;
text-decoration:none;
}
a.content:visited {
color:#000000;
text-decoration:none;
}
a.content:hover {
color:#8EBBCB;
text-decoration:none;
}

```

I took out all of your absolute positioning and did everything using the float and margin properties.  The left bar floats to  the left has no margin on the left (so it will line up with the banner), but the same 5px as before everywhere else.  The center box has a left margin that pushes it out past the navigation and other margins of 5px, like before.  The footer comes right after the center box, just as you wished.

In short, here is what I did and where (aside from removing absolute positioning in everything, which should be obvious):
```

div.cmalinks {
margin: 5px 5px 5px 0pt;
float: left;
}
div.cmacontent {
margin: 5px 5px 5px 165px;
}
div.cmafooter {
clear: both;
}
```
The clear property tells the footer to never wrap around a floating element, so it should always remain below the links, even if the content is shorter than the links.  I assume you're using Firefox, so you might want to check out the [Firebug](https://addons.mozilla.org/en-US/firefox/addon/1843) addon.  It will allow you to inspect all sorts of aspects of your code, from HTML to CSS to JavaScript, and also allow you to make temporary edits to see how it affects things (that's how I did the changes to your styles).

---

### Post by xtacocorex on 2007-06-17
Thanks a lot Modred, it works perfectly!

---

### Post by xtacocorex on 2007-06-19
Well I thought this works perfectly, but it does not in IE 6, which is where I need to have it work.  Don't flame for wanting IE6 capability, it is required in this case.

---

### Post by Modred on 2007-06-19
> **xtacocorex said:**
> Well I thought this works perfectly, but it does not in IE 6, which is where I need to have it work.  Don't flame for wanting IE6 capability, it is required in this case.

Not supporting IE6 is suicide. ;)

What's happening is that IE handles it's page dividing slightly differently than Firefox.  You have assigned a specific width to your content column, and in Firefox that doesn't matter so much; any extra will just cause the page to scroll sideways (which most users hate, btw).

But IE counts up the number of pixels and sees that you don't have enough room to fit that content column on level with the nav column, so it bumps it down below the nav.  If you widen your window, then it fits up in the proper spot.  But we don't want the user to need to resize their window for it to work.

The easiest fix is to remove that **width: 800px** from the content DIVs and let it auto-size itself based on the size of the window.  I just tested it in IE6 and it works fine at any window size once you let IE handle sizing the column.  Of course, then someone with a larger resolution will have the content stretch beyond the edge of the footer and header.  It might take a little more cleverness to solve that problem.  Then again, you have the footer with a constant width too, so in a smaller window it's cut off.  Remove that **width: 1000px** in the footer and it will stretch out alongside the content area and line up nicely, regardless of the resolution.  Not much to be done about the header image.

EDIT: A quick little test revealed that, after making this change, it works fine in IE5 - IE7.  IE4 users are out of luck, but considering that 4 was the default for Windows98, it should be (mostly) safe to assume that very few people today are using it.  You might want to check out [Multiple IE](http://tredosoft.com/Multiple_IE) to have IE3-7 all side by side.  I'm not sure how well it would run in WINE, but it'd be worth a shot.

---

### Post by xtacocorex on 2007-06-20
Thanks Modred, I've made the changes, but will have to check tomorrow.  Thanks again!

---

