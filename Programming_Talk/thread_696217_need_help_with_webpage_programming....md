---
title: "need help with webpage programming..."
date: 2008-02-13
forum: Programming Talk
---

### Post by hockey97 on 2008-02-13
Hi I so far made a layout still not fully finished with it. I  created a naviagtion menu on top of the page going across the top from right to left ect. The their is a table that's on the left of that menu  which diplays a picture. 

  My problem I notice is that when I have the web browser IE in full mode the page looks ok but when I put it in  a small window mode the menu on the top the buttons and the menu shift to the left which goes behind the table on the left of the menu.

Is their some way where I can have the menu detect any collsions with tables so the menu wont go behind that table.

---

### Post by ogwilson on 2008-02-13
I'd like to see the code in question. Could have alot to do with XHTML or improper use of styline.

---

### Post by pedro_orange on 2008-02-14
How are you specifying the size of the elements?

I've found if you use % of the window to relatively size your page depending on the users' resolution/browser size you get better results.

---

### Post by hockey97 on 2008-02-15
I am using px for width. 

here is the script I am using. 

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" 

"http://www.w3.org/TR/html4/loose.dtd"> 

<html>
<head>
<title>Porfile</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"> 
<link href="c:\profilestyle.css" rel="stylesheet" type="text/css">
<style type="text/css">
<!--
.style1 {color: #CC0000;float:left;Position:relative;}
.style3 {color: #CC0000; font-size: 18px;}
-->
</style>
</head>
<body background="C:\www\chillenvillenart\backround.png">
<table width="728" height="50" border="0" align="right"cellpadding="0" cellspacing="0" background="../../../menu.png">
<tr>
<th width="500" height="40" align="right"><span class="style1">how are you mon?</span></th></tr></table>
</tr>
</table>
<table align="left width="128" height="30"  border="0" cellpadding="0" cellspacing="0">
<tr bgcolor="darkred">
<td align="left"><img src="WoodCherryFinish.jpg" width="255" height="30"></td>
</tr>
</table>
<table align="left width="10" height="10"  border="0" cellpadding="0" cellspacing="0">
<tr bgcolor="darkred">
<td><img src="WoodFinish.jpg" width="30" height="215"></td>
<td><img src="http://www.mexicanpictures.com/archives/photos/amdo/raulinhiselement.jpg" width="195" height="215"></td>
<td><img src="WoodFinish.jpg" width="30" height="215"></td>
</tr>
</table>
<table width="128" height="30"  border="0" cellpadding="0" cellspacing="0">
<tr bgcolor="darkred">
<td><img src="WoodFinish.jpg" width="255" height="30"></td>
</tr>
</table>
<div id="controlpanel">
  <table width="254" height="300" align="bottom" cellpadding="0" cellspacing="0" bgcolor="#FFFFFF">
<tr>
<div id="tab">
<th width="255" height="30" align="left" valign="middle" background="../../../tab.png" >  <div align="center"><span class="style3">Control Panel </span></div></th></div>
</tr>
<tr>
<td width="255" height="300" align="left" valign="top" background="../../../profilecontrol.png">Hey man what's up?</td>
</tr>
</table>
</div>
</body>
</html>
```

here is the outside css ```
#controlpanel{
position: absolute;

background-image:url(c:\profilecontrol.png);

layer-background-image:url(c:\profilecontrol.png);
 
background-origin: content;

width: 100px; 

height: 300px; 

margin: 0; 

margin-top: 0px;
margin-right: 500px;} 

#menu{position:relative;background-image:url(menu.png);background-repeat:no-repeat; background-position:center; height:30px; width:728px;}

#tab{background-image:url(tab.png); background-repeat:no-repeat; position:relative; alight:left;}
```

This is how it looks at full window mode:[what it looks like full size but I want it to look the same when in a small window.]("http://67.149.150.40/right.png")
Here is what it looks like if you made the window smaller:[Problem photo]("http://67.149.150.40/pb.png")

any ideas?? any place I went wrong??

---

### Post by MacAnthony on 2008-02-15
It's not an answer to your problem, but you spelled Profile wrong in the title:
<title>Porfile</title>

---

### Post by hockey97 on 2008-02-15
lol hahaha ya I know lol I plan to fix it at the end I am just focusing on the web layout. In the title I plan to have the username then after their name would be account,but I will worry about that at the end I just right now want to shape the whole layout of the website and then connect and make sure every function works then I will plan on looking for spelling errors ect .

I know some css but I can't say I am a pro at it, still trying to master it.

---

### Post by MacAnthony on 2008-02-15
There is a lot going on, but here is my theory. Since the width of the top table is wider than the width of the window and you have the div with the picture specified as being absolute, it's floating your table over the top of the div with the photo since there isn't enough room to display them both side by side. Personally, I wouldn't use absolute positioning unless I would need to.

You also have a bunch of misc code issues like the first table has 2 sets of closing row and table tags:
<table width="728" height="50" border="0" align="right"cellpadding="0" cellspacing="0" background="../../../menu.png">
<tr>
<th width="500" height="40" align="right"><span class="style1">how are you mon?</span></th></tr></table>
</tr>
</table>

---

### Post by hockey97 on 2008-02-15
I don't think I am using css on the top table. I am not also using div on the top table.

the top table is the first table in the html of the page.

I fixed that one mistake I did with the closings thanks for pointing that out.

I linked the css page with my html page dose that mean all the css is being applied to my whole html page??

or allows to use the css at certain areas??

I thought that when I link css page to the html page I have to do that in order to use those css codes in my html page . So I thought it just's gets applied with you call for those css elements ect.

The top table gets shoved behind the other table with the photo. if you see the one screen shot I gave you that one with the window small if you look by where the wood is you can see the text still their.

also did you notice the sides that there are gaps. you can see it on the left and on the right why is that??  how can I align them all the way to the left?? I am using the html align="left" but  their is like an inch gap.

---

### Post by MacAnthony on 2008-02-15
You are right, you aren't using css, but you are specifying height and width for the top table:
<table width="728" height="50" border="0" align="right"cellpadding="0" cellspacing="0" background="../../../menu.png">


I didn't say you had a div on the top table, the div i was referring to was the div witht eh controlpanel class. The css applied to that is forcing it to float over the other elements.

If you link a css file to a page, it applies those styles to all the elements on the page based on the css selector that it uses. Basically, you define "rules" of what those styles apply too. So #controlpanel, will be applied to any and all elements with the class of controlpanel.

The gaps are probably caused by margins or padding applied to the body element forcing all internal elements to be a certain width away from the edge. Each browser has it's own default styles on how it displays things like that if they aren't specified. You coud get rid of it by adding:
BODY {
margin: 0px;
padding: 0px;
}

---

### Post by hockey97 on 2008-02-15
You might be right I see what your talking about right now.I am going to play with those thanks for the help.

---

### Post by shawnhcorey on 2008-02-15
> **hockey97 said:**
> Is their some way where I can have the menu detect any collsions with tables so the menu wont go behind that table.

No.

---

### Post by Geekkit on 2008-02-15
I have a few suggestions to you:

a.) Don't use tables for anything other than tabular data. Tables being used for layout are a horrible misuse of tables and cause nothing but problems.
b.) CSS and XHTML transitional are your friend. You will find your layouts much more compatible across browsers if you try to comply with CSS and XHTML transitional (or better: strict).
c.) The following sites have many examples, have a look, I've found them incredibly useful:

[http://www.maxdesign.com.au/presentation/liquid/](http://www.maxdesign.com.au/presentation/liquid/) <-- for liquid layouts (i.e., DIV, CSS, etc.)
[http://www.oswd.org](http://www.oswd.org) <-- open source web design templates (really useful)
[http://www.freecsstemplates.org/](http://www.freecsstemplates.org/) <-- yet more templates

Just be careful though, some sites suggest never even using tables at all which is silly. Just remember this:
[INDENT]HTML tables are for tabular data, not layouts. If you are displaying tabular data (e.g., a calendar, a spreadsheet, grades, statistics), then tables are the right tool for the job. If you are attempting to create a layout, use DIV and CSS[/INDENT]

---

### Post by shawnhcorey on 2008-02-15
> **Geekkit said:**
> I have a few suggestions to you:

a.) Don't use tables for anything other than tabular data. Tables being used for layout are a horrible misuse of tables and cause nothing but problems.

No.  Sigh.

There are certain, limited abilities that HTML tables can do that CSS can never do.

If you don't believe me, check out my [website]("http://www.magma.ca/~shawnhcorey/").  It contains HTML elements that cannot be reproduced in CSS.  And no, that is not arrogance; I have tried many, many ways to do it with CSS.  All have failed.

If anyone can match what I do on my website in CSS (not HTML), then please let me know.  But I think you are doom to fail.

---

### Post by Geekkit on 2008-02-15
> **shawnhcorey said:**
> No.  Sigh.

There are certain, limited abilities that HTML tables can do that CSS can never do.

If you don't believe me, check out my [website]("http://www.magma.ca/~shawnhcorey/").  It contains HTML elements that cannot be reproduced in CSS.  And no, that is not arrogance; I have tried many, many ways to do it with CSS.  All have failed.

If anyone can match what I do on my website in CSS (not HTML), then please let me know.  But I think you are doom to fail.

Shawn,

You can do it, I've done it many times and so have countless others. Check out:

[http://www.maxdesign.com.au/presentation/two-columns/](http://www.maxdesign.com.au/presentation/two-columns/)
[http://blog.thegioiwebsite.net/2008/01/27/two-columns-with-color/](http://blog.thegioiwebsite.net/2008/01/27/two-columns-with-color/)
[http://css-discuss.incutio.com/?page=ThreeColumnLayouts](http://css-discuss.incutio.com/?page=ThreeColumnLayouts)
[http://www.alistapart.com/articles/holygrail](http://www.alistapart.com/articles/holygrail)
[http://www.glish.com/css/7.asp](http://www.glish.com/css/7.asp)
[http://pmob.co.uk/temp/3colfixedtest_explained.htm](http://pmob.co.uk/temp/3colfixedtest_explained.htm)
[http://matthewjamestaylor.com/blog/ultimate-3-column-holy-grail-pixels.htm](http://matthewjamestaylor.com/blog/ultimate-3-column-holy-grail-pixels.htm)
[http://matthewjamestaylor.com/blog/ultimate-3-column-holy-grail-pixels.htm](http://matthewjamestaylor.com/blog/ultimate-3-column-holy-grail-pixels.htm)
[http://www.dynamicdrive.com/style/layouts/item/css-liquid-layout-31-fixed-fluid-fixed/](http://www.dynamicdrive.com/style/layouts/item/css-liquid-layout-31-fixed-fluid-fixed/)
[http://www.satzansatz.de/cssd/companions.html](http://www.satzansatz.de/cssd/companions.html)

There are dozens, nay, hundreds of examples out on the Web that show that CSS and HTML together creating liquid layouts can and do work in all browsers with minimal effort. You just have to let go of your old habits and predispositions. :)

EDIT:
> **shawnhcorey said:**
> If anyone can match what I do on my website in CSS (not HTML), then please let me know.  But I think you are doom to fail.
If you check out those links I think you'll find that others have done this with clean HTML code. I won't fix your site for you but I will say that if you check these links you'll find your solutions there dude.:)

---

### Post by LaRoza on 2008-02-15
> **shawnhcorey said:**
> 

If anyone can match what I do on my website in CSS (not HTML), then please let me know.  But I think you are doom to fail.

I will try. It seems possible, but I will start tomorrow because I will not be able to stop once I start.

Do you mind if I use your exact content for my test?

(I ask because I will upload it to my server if I get it right for you to see.)

---

### Post by shawnhcorey on 2008-02-16
> **LaRoza said:**
> I will try. It seems possible, but I will start tomorrow because I will not be able to stop once I start.

Do you mind if I use your exact content for my test?

(I ask because I will upload it to my server if I get it right for you to see.)

Yes, you may use my contents.

I'm sure the RIAA has put the fear of God into you, but they still haven't extended their ugly claws into Canada.  You can do whatever you want, provided they fall within the Bern Copyright Treaty.  Yes, that does means you can copy for scholastic reasons:  to prove me wrong.

But if you make money from it, I want my share ;)

---

### Post by LaRoza on 2008-02-16
> **shawnhcorey said:**
> Yes, you may use my contents.

I'm sure the RIAA has put the fear of God into you, but they still haven't extended their ugly claws into Canada.  You can do whatever you want, provided they fall within the Bern Copyright Treaty.  Yes, that does means you can copy for scholastic reasons:  to prove me wrong.

But if you make money from it, I want my share ;)

God has put the fear of RIAA into me, ever since they sued Him for some passages in the Bible and won.

---

### Post by LaRoza on 2008-02-16
> **shawnhcorey said:**
> No.  Sigh.

There are certain, limited abilities that HTML tables can do that CSS can never do.

If you don't believe me, check out my [website]("http://www.magma.ca/~shawnhcorey/").  It contains HTML elements that cannot be reproduced in CSS.  And no, that is not arrogance; I have tried many, many ways to do it with CSS.  All have failed.

If anyone can match what I do on my website in CSS (not HTML), then please let me know.  But I think you are doom to fail.

I am working on it, as stated, and I started early. It is "tomorrow", 0331 my time, but I ended up staying up late anyway.

[http://laroza.freehostia.com/test/css.php](http://laroza.freehostia.com/test/css.php)

You will note by looking at the markup I have divided it up into logical parts and I am doing each part separately. This is not only because it is logical to do so, but because it is actually a PHP script and the parts are entirely different files.

The files are in [http://laroza.freehostia.com/test/includes](http://laroza.freehostia.com/test/includes)

My PHP syntax is weird because I have different versions of PHP on my server and my host, so I do last second kludges to fix it.

(web.inc was heavily altered for this, and isn't the original template)

---

### Post by Wybiral on 2008-02-16
> **LaRoza said:**
> God has put the fear of RIAA into me, ever since they sued [COLOR="Blue"]Him[/COLOR] for some passages in the Bible and won.

You mean [COLOR="Red"]Her[/COLOR]?

---

### Post by LaRoza on 2008-02-16
> **Wybiral said:**
> You mean [COLOR="Red"]Her[/COLOR]?

No, I view God as a masculine pronoun. That is the way it is in the Bible, and no one should alter it. 

(Note, anyone reading this, feel free to have and express you own beliefs, but don't do it on this thread. I do not use my personal beliefs as a moderator but the Codes of Conduct)

---

### Post by ruy_lopez on 2008-02-16
> **shawnhcorey said:**
> No.  Sigh.

There are certain, limited abilities that HTML tables can do that CSS can never do.

If you don't believe me, check out my [website]("http://www.magma.ca/~shawnhcorey/").  It contains HTML elements that cannot be reproduced in CSS.

CSS can do a good three column, if that's what you mean. The problem isn't with CSS. Many of the tutorials are ugly hacks which don't scale.

I copied a template from a good tutorial last year, it's attached. It's just a bare-bones template.

---

### Post by LaRoza on 2008-02-16
> **ruy_lopez said:**
> CSS can do a good three column, if that's what you mean. The problem isn't with CSS. Many of the tutorials are ugly hacks which don't scale.

I copied a template from a good tutorial last year, it's attached. It's just a bare-bones template.

It isn't a column issue. I think it is a "not used to CSS" issue. Look at the CSS for that site, it shows an awkwardness for CSS use. The markup isn't logical at all.

Columns should automatically wrap to the next column, which is not possible with CSS.

---

### Post by Wybiral on 2008-02-16
> **LaRoza said:**
> No, I view God as a masculine pronoun. That is the way it is in the Bible, and no one should alter it.

The word "God" has been feminine to me ever since I watched the movie Dogma, and she looks exactly like Alanis Morissette too (yes, I get all of my philosophical insight from Kevin Smith movies).

---

### Post by hockey97 on 2008-02-16
Ok I plan to remake the layout this time using css. I started learning css a while back like 2 months ago.

I am having problems seeing how you can position a image or test anywhere the page.

I get confuse and have a habit of just using tables lol .

To what I understand css dose nothing but apply properties to elements in an html doc  like position also backround  ect .

I notices just a month ago myspace started to use css. 

I need to see some examples of how you would position stuff and how I can overlap elements.  

Like on my page I am making I want a border frame around the users image.

Also buttons but have a square with a background behind the buttons. 
I am having trouble making my website flow as one art wise and layout.

I am trying to make the page so noone can notice that their in pieces and would think the whole page is all in one.

any examples would help me. I am confused on the measuring scale.

in css I know their is position  but I don't' know how I can put an image at certain areas and know  what values I have to put in to get the picture where I want it.

I know px is pixel but I don't know what areas on the page what values they are so I would know exactly where the images and test go.

I just need some examples and a little help finding my way.

---

### Post by LaRoza on 2008-02-16
See my home page, you can use the Web Developer toolbar for Firefox to view all the CSS.

It uses positioning a lot.

There are several ways of measuring in CSS. You can use absolute measurements like inches, centimetres, and points or you can use relative measurements, like percentages and em values.

You can view the site I was redoing, although it isn't done yet. You will see the basic positioning and borders in action.

---

### Post by hockey97 on 2008-02-16
ok I  got it working with css. One question though, in css would I be able to take images place them anywhere and have text or buttons on top of it??  Like I hear you don't need no tables  but then how can you put buttons over images and thos images would be the backround of that area where you want to put many buttons??

---

### Post by MacAnthony on 2008-02-16
You can use absolute positioning to do this, but there tends to be issues between browsers with that. If you want text on the image, you will get much better results from editing the image so that it has text on it.

I am another one who doesn't believe that tables can't be used for layout. I do think that the use of them was more of an abuse and got to be a bad habit for a lot of designers though. Use the tool that works the best. Sometimes that is a table - most of the time, you can use other elements, though.

---

### Post by hockey97 on 2008-02-16
Can you give me some examples of other elements??

I got the thing to work but is it possible to with css do what I am doing without using tables like  just position a pic in a certain area and then put buttons on top of it??

well the page I was working on I am finshed with it. But I have many more pages to do but I would love to not use tables if I could.
In the few pages coming up I am making I will be using lot's of javascript to make the user able to resize the tables.

Is it also possible to use php or some script to apply css codes if some event occurs?? like example if the user has mail and I want to pop in on the layout a alert table with text that say's  you got mail  but I only would want that to occur if in the database their was new mail.

---

### Post by hockey97 on 2008-02-17
Thanks for the help I now understand css better now.

One more question I have it's not really related to programming. Is their a way in ubunut to make an exact copy of all the setup and installations and put it on a cd or somthing?

Well  I have 2 computers  one is my main one which I have ubuntu and windows xp on it a dual boot.  Well I have ubuntu setup and everything like mysql database setup all up.

I now am having second thoughts. So the computer that has ubuntu on it  is on the computer that I am used to using it for personal use. My new computer  I don't use much  has windows xp on it.

What I want to do is make an exact copy of my ubuntu that is already installed and put it  on my new computer SO I can hav ethe new computer server my websites and use my personal computer as a backup.

is that possible?? I have alot of useful programs on windows xp so the computer that has ubuntu I only use  ubuntu to host websites and stuff.
Also some develoment work other than that I used windows xp.


So do you know of a way I can copy everything that is on the hard drive that is in the Ubuntu OS  so I can save it on my new computer hard drive and just boot up without needing to  install??

well even if I have to install it is their a way I don't have to install mysql and stuff becuse that is a pain in the neck took me at least 2 or 3 months to get everything up and running and able to point to my hosting service that host's my domain name .???

---

