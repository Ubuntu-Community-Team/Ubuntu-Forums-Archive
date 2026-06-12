---
title: "Need CSS Help!"
date: 2008-03-12
forum: Programming Talk
---

### Post by markekeller on 2008-03-12
Basically, I'm trying to get the header of [this site]("http://www.penguinsightings.org") to look good.  It's a Wordpress blog, and I'm using this [Pluralism]("http://www.freewpthemes.net/preview/pluralism") theme, with a few modifications made by me.  The main change that I made is adding in the subtitle of my blog, to the header.  I created a new style for it (the last one is it, called "description"):

```
#header {
	height: 200px;  /* MK: was "height: 140px;" */
	background: #087FE7 url(images/img03.jpg) no-repeat;
}

/* Logo */

#logo {
	float: left;
}

#logo h1 {
	margin: 0;
	padding: 150px 0 0 78px;  /* MK: was "padding: 90px 0 0 78px;" */
	text-transform: lowercase;
	letter-spacing: -3px;
	font-size: 40px;
	color: #FFFFFF;
}

#logo h1 a {
	text-decoration: none;
	color: #FFFFFF;
}

/* MK: added this. */

#description d1 {
	margin: 0;
	position:absolute; top:140px; left:220px;
	text-transform: lowercase;
	letter-spacing: 0px;
	font-size: 15px;
	color: #FFFFFF;
}
```


And added it into my header (again, the part called "description"):

```
		<div id="header">
			<div id="logo">
				<h1><a href="<?php echo get_option('home'); ?>/"><?php bloginfo('name'); ?></a></h1>
			</div>
			<div id="menu">
				<ul>
					<li class="first page_item<?php if (is_home()) echo ' current_page_item'; ?>"><a href="<?php echo get_option('home'); ?>/">Home</a></li>
					<?php wp_list_pages('title_li=' ); ?>
				</ul>
			</div>
			<div id="description">
				<d1><?php bloginfo('description'); ?></d1>
			</div>
		</div>
```

I tweaked the numbers until it looked just the way I wanted it to, in Firefox, running under Linux.  Then I decided to see how it looked in other browsers - and was rather shocked.  In Windows Firefox, the subtitle text was shifted horizontally half an inch to the left.  In Internet Explorer, the subtitle was in tiny text at the top of the screen.  In Konqueror it looked exactly the same as in IE, and Epiphany was like Firefox in Windows, only shifted even farther.  But, interestingly enough, everything else looks almost identical between browsers - it's just the subtitle that is messed up.

So, evidently, I'm doing something wrong.  But what?

---

### Post by kostkon on 2008-03-12
I believe it would be more semantic to change your description to a header level 2, i.e.
```
<div id="logo">
     <h1><a href="<?php echo get_option('home'); ?>/"><?php bloginfo('name'); ?></a></h1>
     <h2><?php bloginfo('description'); ?></h2>
</div>
```
The way you have your description is wrong, anyway. You are putting it inside a definition list (you use <d1> but I assume you mispelled <dl>) which is wrong. Actually, the right code would be
```
<dl>
     <dt>Description</dt>
     <dd><?php bloginfo('description'); ?></dd>
</dl>
```
Furthermore, try to use relative positioning for your description, this should make it to show OK in most browsers, i.e.
```
#description  {
	margin: 0;
	position: relative
etc. etc.
```

Play with the top, bottom, left, and right values of the relative position of the <h2> description tag until you achieve an acceptable result.

---

### Post by markekeller on 2008-03-12
Thanks!  Using relative really helped.  I wasn't trying to do a definition list (I don't even know what that is, being an utter beginner to CSS), but was rather using d1 the same way you'd use h1 - as a style.  But I've changed that now, and it looks the same in all three browsers in Linux!  It looks the same in both the Windows browsers, too, but because the fonts are different there, it's alligned differently, and the subtitle covers up part of the penguin.  Is there any way to fix that?

---

### Post by kostkon on 2008-03-12
> **markekeller said:**
> Thanks!  Using relative really helped.  I wasn't trying to do a definition list (I don't even know what that is, being an utter beginner to CSS), but was rather using d1 the same way you'd use h1 - as a style.  But I've changed that now, and it looks the same in all three browsers in Linux!  It looks the same in both the Windows browsers, too, but because the fonts are different there, it's alligned differently, and the subtitle covers up part of the penguin.  Is there any way to fix that?

First of all, you should make sure that you cancel out any effects of the padding that may exist around the headers' boxes. Thus, put
```
padding: 0;
```
into the CSS of the <h1> and <h2> headers.
After doing that, your positioning will be easier to handle.

Now about the font sizes, I would strongly recommend you to use relative values for their sizes. Use *em* instead of *pixels*. Please read [this]("http://jontangerine.com/log/2007/09/the-incredible-em-and-elastic-layouts-with-css") to see what are the advantages of using *em*.

---

### Post by markekeller on 2008-03-13
Wow, that's a great article!  Beautiful typesetting. :)  Using em helped improve it, but there was still a little disparity between Windows and Linux - but then I tried using percentages for the horizontal measurements, and now it's lined up just about perfectly!  Thanks!

---

### Post by shawnhcorey on 2008-03-13
> **kostkon said:**
> Now about the font sizes, I would strongly recommend you to use relative values for their sizes. Use *em* instead of *pixels*. Please read [this]("http://jontangerine.com/log/2007/09/the-incredible-em-and-elastic-layouts-with-css") to see what are the advantages of using *em*.

I never heard it called Elastic Layout before.  Usually it is called Fluid Design or Liquid Design.

Some other  guidelines:

[LIST]
[*] Never make the font size small than 1em (100%).  Most browsers have a control that let's user set the minimum font size.  If you ask for a smaller size, you won't get it and your page will look weird.
[*] Set the [FONT="Courier New"]max-width[/FONT] for your text columns.  Columns that are too wide are hard to read.  Maximum width for a serif font is 42em, for sans-serif, 32em.  You can added 5em to each if you do 1 1/2 line spacing; 10em if double line spacing.
[*] Text has no bottom.  Always allow for the possibility for large font sizes to extend the size of a block downward.  Use [FONT="Courier New"]<br clear="all" />[/FONT] to place items under a text block.
[/LIST]

---

### Post by mssever on 2008-03-13
> **shawnhcorey said:**
> I never heard it called Elastic Layout before.  Usually it is called Fluid Design or Liquid Design.Hmm... elastic design is the term I'm most familiar with. But this is nitpicking...

> [LIST]
[*]Set the [FONT=Courier New]max-width[/FONT] for your text columns.  Columns that are too wide are hard to read.  Maximum width for a serif font is 42em, for sans-serif, 32em.  You can added 5em to each if you do 1 1/2 line spacing; 10em if double line spacing.[/LIST] Bear in mind that IE doesn't respect max-width. (I dunno about IE7, though.) You'll have to determine the best values based on your layout, etc. It's true that too-wide columns are hard to read, but the numbers given above merely reflect shawnhcorey's opinion, not some hard and fast rule.

While we're talking about readability, I'd strongly recommend a sans-serif font for body text. I don't have a link right now, but sans-serif is easier to read on-screen, while serif is easier to read when printed.

> [LIST]
[*] Text has no bottom.  Always allow for the possibility for large font sizes to extend the size of a block downward.  Use [FONT=Courier New]<br clear="all" />[/FONT] to place items under a text block.[/LIST]Using <br clear="all" /> is mixing structure and layout, which is a Bad Thing. Better to do this with CSS. If my memory serves me correctly, in CSS it's [FONT=Courier New]clear: both[/FONT].

---

### Post by shawnhcorey on 2008-03-13
> **mssever said:**
> Hmm... elastic design is the term I'm most familiar with. But this is nitpicking...

Until you want to search the web for it.  Then knowing all the possible names for it comes in handy.

> **mssever said:**
>  Bear in mind that IE doesn't respect max-width. (I dunno about IE7, though.) You'll have to determine the best values based on your layout, etc. It's true that too-wide columns are hard to read, but the numbers given above merely reflect shawnhcorey's opinion, not some hard and fast rule.

Mayhaps that's why I called the guidelines.

> **mssever said:**
> While we're talking about readability, I'd strongly recommend a sans-serif font for body text. I don't have a link right now, but sans-serif is easier to read on-screen, while serif is easier to read when printed.

A sans-serif font is easier to read on screen because of its lower resolution but in general, a serif font is easier to read.

---

