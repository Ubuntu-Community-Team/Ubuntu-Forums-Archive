---
title: "CSS Box?"
date: 2008-07-08
forum: Programming Talk
---

### Post by Arctic_Fox on 2008-07-08
I'm trying to make a simple box using CSS. It should be white in the middle, fading to grey on the sides. I've mostly copied it from a site, as I don't know CSS. This is really all I need, so I don't want to spend much time on learning it (sorry, I'm short on time). Could anyone help me complete this small example? I have an image for the interior, one for each of the four sides of the box, and the 4 corners.

style.css
/* set millions of background images */
.rbroundbox { background: url(nt.gif) repeat; }
.rbtop { background: url(tp.gif) repeat-x top; }
.rbtop div { background: url(tl.gif) no-repeat top left; }
.rbtop div div { background: url(tr.gif) no-repeat top right; }
.rbbot div div { background: url(bl.gif) no-repeat bottom left; }
.rbbot div{ background: url(br.gif) no-repeat bottom right; }
.rbbot { background: url(bp.gif) repeat-x bottom; }

/* height and width stuff, width not really nessisary. */
.rbtop div,.rbtop div div, .rbtop, .rbbot div, .rbbot div div, .rbbot {
width: 100%;
height: 15px;
font-size: 1px;
}
.rbcontent { margin: 0 15px; }
.rbroundbox { width: 50%; margin: 1em auto; }





test.html
<html>
	<head>


	<title>Win!</title>

	<style type="text/css">

		@import url('style.css');

	</style>


	</head>

	<body>
		<div id="body">
			<div class="rbroundbox">
				<div class="rbtop"><div><div></div></div></div>
					<div class="rbcontent">
						<p>Text here. And here.</p>
					</div><!-- /rbcontent -->
				<div class="rbbot"><div><div></div></div></div>
			</div><!-- /rbroundbox -->
		</div>
	</body>
</html>

:guitar:

---

### Post by Tony Flury on 2008-07-10
To the best of my knowlede you can't do fades/colour gradients straight from CSS - all you can do is use a fixed background colour, or an use image (as your example is doing)

If you want a gradient background, then you will need to modify the imagess you are using to build your border so that they include the gradient/fade that you want.

---

### Post by mike_g on 2008-07-10
Well microsoft made their own set of css functions, one of which does gradients, but its not standard. 

It looks like the OP is attempting to do gradients with images though which is how you would normally do it.

In my experience drawing the corners it makes the code overcomplicated. If you are happy to use a fixed width, then just slice it as: gradient top, midsection, gradient bottom.

Writing off the top of my head the code would look something like:

```

.top
{
    width: 100px;
    height: 32px;
    display: block;
    background: url("top.png") no-repeat;
}

.mid
{
    width: 100px;
    background: url("mid.png") repeat-y;
} 
.bot
{
    width: 100px;
    height: 32px;
    display: block;
    background: url("bot.png") no-repeat;
}

```

And to draw it would be something like:
```

<div class="mid">
    <div class="top"></div>
    Blah de blah
    <div class="bot"></div>
</div>
```

---

