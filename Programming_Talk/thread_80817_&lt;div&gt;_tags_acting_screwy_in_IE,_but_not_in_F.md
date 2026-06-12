---
title: "&lt;div&gt; tags acting screwy in IE, but not in Firefox..."
date: 2005-10-23
forum: Programming Talk
---

### Post by Zarkoth on 2005-10-23
Hey there, I'm pretty new to <div> tags, although they're very nice.  And I'm messing with my high school's web page, and after using two divs off to the right to help make this page much more readable, and it laid out like this....

Un <div>             one div             a second div
tagged list           table went         with a pic
here..                    here                  was here...

but in IE, it moved the normal list over so that it was halfway behind the second div table...   I was sort of expecting some sort of weirdness like this, but how can I fix this?

---

### Post by Jenda on 2005-10-23
Don't use IE?

---

### Post by wolphin on 2005-10-23
Show us the code and we might be able to help you out. :)

That's happened to me before, but I'm not quite sure what you're saying - did you put one div inside another one? If that's what you *did* do, then check that you haven't accidentally made the second div's width/height larger than the first (sound stupid, but does screw things up) or if not just make the second div's dimensions be as percentages [of the first].

-Wolphin

---

### Post by Zarkoth on 2005-10-23
You know, Jenda's response is probably the best one, but being that IE has something like the upper 80's percent in market share, I should probably fix this problem...   lol, and no wonder what I said wasn't very clear....lol, should've used a <pre> tag in my post, or at least previewed....

Here's a fixed version of that post. Ignore, the whole 'Code' thing, I was just using that to make sure the spacing was right
```


Just a normal         one div                    a second div
list                    table went            with a pic
here..                   here                        was here...


```

---

### Post by Pathogenix on 2005-10-23
Um.... your pre tags aren't much more helpful.

From what you've said, I assume your code runs something like

```

<UL class="someMenu">
  <LI>aaaa</LI>
  <LI>bbbb</LI>
  <LI>cccc</LI>
</UL>

<DIV id="middleDiv">content</DIV>
<DIV id="rightDiv">content</DIV>

```

and that you want a three column layout to result?

When in doubt, use someone else's bugfixed code. Works for Linux :)

[http://glish.com/css/7.asp](http://glish.com/css/7.asp)
[http://www.thenoodleincident.com/tutorials/box_lesson/boxes.html](http://www.thenoodleincident.com/tutorials/box_lesson/boxes.html)

You should be able to replace the leftmost div in these examples with a UL as both are block level elements. Or you can cheat and just throw your list inside a wrapping DIV - nobody's going to hold you to account for a single non-structural element.

If I'm not understanding, you'd have to post your code and your CSS before anyone could offer you a solution. Wrap it in a code tag rather than a pre.

---

### Post by Zarkoth on 2005-10-23
Yeah, I suppose just posting my code in the first place would've been best, heh

Anyway, here it is - 

[HTML]
<!-- the div in on the far right --!>
<div style="position:absolute;top:85px;left:350px;background:#360100 url();border:#360100 1px double;color:#360100;width:600px;height:375 px;overflow:auto">
<center>

<img src=pics/front_stairs.jpg>
<br>
<br><font color=white>
Welcome!<br>
<br>
<br>
<br>
 <a href="http://www.ebutler.esu7.org"target="_top"><font size = +2>Return to Home Page</font></a>
</font></center>
</div>


<!-- the normal bunch of links on the far left of the page --!>
</H4><H3>High School</H3><H4>

UPSTAIRS<br>
<A HREF="R201.html">Room 201 Art</A><br>
<A HREF="R202.html">Room 202 Math</A><br>
<A HREF="Ulab.html"> Room 203 Upstairs Lab</A><br>
<A HREF="R204.html">Room 204 English</A><br>
<A HREF="R205.html">Room 205 Spanish</A><br>
<A HREF="R206.html">Room 206 English</A><br>
<A HREF="R207.html">Room 207 History</A><br><br>

DOWNSTAIRS<br>
<A HREF="R108.html">Room 108 </A><br>
<A HREF="R109.html">Room 109 </A><br>
<A HREF="R110.html">Room 110 </A><br>
<A HREF="Dlab.html">Downstairs Lab </A><br>
<A HREF="dl.html">Distance Learning Room </A><br>
<A HREF="R112.html">Room 112 </A><br>
<A HREF="agroom.html">Room 118 Ag </A><br>

<A HREF="bandroom.html"> Room 119 Band</A><br>
<A HREF="R151.html">Room 151 </A><br>
<A HREF="mproom.html">Multi-Purpose Room</A><br>
<A HREF="gym.html">Gym</A><br>
<A HREF="library.html">Library</A><br>
<A HREF="weightroom.html">Weight Room</A><br>
<a href="wrestlingroom.html">Wrestling Room</a><br>






<!--The div in the middle --!>
<div style="position:absolute;top:70px;left:250px;background:#360100 url();border:#360100 1px double;color:#360100;width:125px;height:200px;overflow:auto">
<h3>
<font color=C46713>Elementary</font><br></h3><br>
<A HREF="kindergarten.html">Kindergarten</a><br>
<A HREF="first.html">First Grade</a><br>
<A HREF="second.html">Second Grade</a><br>
<A HREF="third.html">Third Grade</a><br>

<A HREF="fourth.html">Fourth Grade</a><br>
<A HREF="fifth.html">Fifth Grade</a><br>
<A HREF="sixth.html">Sixth Grade</a><br>
</div>
[/HTML]

Yeah, so there it is, hope that helps!

---

### Post by Pathogenix on 2005-10-23
Okay... absolute positioning is the work of the devil. Likewise, inline styles are the work of the devil, and - finally - unquoted attributes are the work of the devil.

I've hacked up a very quick demo of your layout - let me know how it displays. I can't test directly in IE because I can't be bothered to boot XP :)

Let me know if any of it fails to make sense, and I'll explain it more detail. Briefly, I've moved all your styling to a separate style sheet. Later you can put this in its own file - that way everything is nice and clean and your visitors can download your page quicker; I've moved your divs into a sensible order, and marked up your links as a list - this is nice way to do it because you get far more flexibility with formatting them, and they'll be more accessible to a screen reader.

```


<html>

	<head>
	<style type="text/css">
		#leftMenu
		{
			float: left;
			margin-right: 20px;
		}

		#leftMenu ul, h2
		{
			margin-top: 0px;
			padding: 0px;
		}

		#leftMenu li
		{
			list-style: none;
			display: block;
		}
		#middleDiv
		{
			float: left;
			margin-right: 20px;
			width: 125px;
		}
		#rightDiv
		{
			float: left;
		}

	</style>
       </head>
	<body>
		<h1>High School</h1>
		<div id="leftMenu">
			<h2>Upstairs</h2>
			<ul id="upstairs">
				<li><a href="#">Link 1</a></li>
				<li><a href="#">Link 2</a><li>
			</ul>
			<h2>Downstairs</h2>
			<ul id="downstairs">
				<li><a href="#">Link 1</a></li>
				<li><a href="#">Link 2</a><li>

			</ul>
		</div>
		<div id="middleDiv">
			some content goes here, hopefully more interesting than this
		</div>

		<div id="rightDiv">
			Lorum ubuntu dolor sic amet monkey monkey monkey
		</div>
	</body>
</html>

```

---

### Post by raublekick on 2005-10-23
using float: left might lead to more trouble with IE. IE add's 3px margins to some elements, and i know i had trouble with it using float before.

---

### Post by Zarkoth on 2005-10-23
Well although I'll have to tweak it a little bit, it looks like it's fine for IE, thanks!

Yeah, it's just m'school's webpage, although I was discussing using CSS with my teacher, and that was my first attempt at div's, in case you couldn't tell ;)

I'll actually put my school's code into it tomorrow, I'll let you know how it all works out!

and a little explaination would be cool later, as to what actually told IE where to put the div's....It was puzzling though, why on earth would IE take the lists that weren't in divs and move it all over the place?  Just strikes me as odd....

O'well, IE just sucks I guess :)

---

### Post by Pathogenix on 2005-10-24
[QUOTE=raublekick]using float: left might lead to more trouble with IE. IE add's 3px margins to some elements, and i know i had trouble with it using float before.[/QUOTE]


Yeah, IE's box model is competely scr00ed - but if you've got space to allow the extra gutter, or you're willing to throw in a quick hack to ameliorate it, then this is the quickest and dirtiest way to knock up a table-free columnar layout.

As far as the explanation goes, I just checked your code in IE, and I don't see the problem that you had. Which version of IE were you running?

---

### Post by Zarkoth on 2005-10-24
Really?  Hmm....I first saw the problem at school, but these are running older versions of IE, but I checked again at home, which is probably up-to-date, although we've firmly switched to Firefox,  and it was still acting odd.

perhaps I should just take up a poll on whether or not it works to determine whether or not enough people can or can't see it?:)

Weird though, and even with the CSS code that you gave me, the second div, the one that should be in the middle, shows up below the first div....

although, interestingly enough, the third div is in about the right place

---

### Post by atoponce on 2005-10-24
IE does not handle relative and absolute CSS positioning very well.  Supposedly, this will be fixed with IE 7.  Because IE still controls the market share, I would reccomend switching your div tags to a table.

---

### Post by Zarkoth on 2005-10-25
We're considering perhaps using frames...but I dunno, at this point, a table is as good a suggestion as any, those CSS tables were acting a tad funny too.
Hmm....

---

### Post by Pathogenix on 2005-10-25
[QUOTE=Zarkoth]
Weird though, and even with the CSS code that you gave me, the second div, the one that should be in the middle, shows up below the first div....

although, interestingly enough, the third div is in about the right place[/QUOTE]

Below the links, or just below the title? The title is at the head of the screen where I assumed you wanted it, but I've just tested the code I sent you in IE 6.0, 5.01 and 5.5 and they all display perfectly.

Is this *after* you've added your content? If so, I'd be inclined to suspect that you'd forgotten to close a tag, which sometimes has seriously weird effects.

---

### Post by David Marrs on 2005-10-25
ugh! I wouldn't recommend tables or frames for layout. You just have to be a little more conservative with your CSS. The bugs in IE's rendering engine are well known by now and a quick google will tell you what coding habits to avoid.

Tables just become a nightmare to code, especially if you start nesting them.
Unless you're coding with something like Dreamweaver, they're more hastle than they're worth. Besides which, CSS is better coding practice. Frames, on the other hand, don't like search engines, don't bookmark well, can be difficult to navigate and can really get annoying when the wrong half of the screen scrolls.

---

### Post by Luke Redpath on 2005-10-25
[QUOTE=atoponce]IE does not handle relative and absolute CSS positioning very well.  Supposedly, this will be fixed with IE 7.  Because IE still controls the market share, I would reccomend switching your div tags to a table.[/QUOTE]

Rubbish. Sites have been and continue to convert to standards driven, CSS-based layouts (including big well known websites) and whilst isn't great it can usually be made to behave.

No professional web developer should be using table-based layouts in 2005 and whilst I realise this person isn't a pro, the fact that they are making the effort should be praised and tableless layouts should be encouraged.

---

### Post by atoponce on 2005-10-25
[quote=Luke Redpath]Rubbish. Sites have been and continue to convert to standards driven, CSS-based layouts (including big well known websites) and whilst isn't great it can usually be made to behave.[/quote] 
Correct.  Sites are making the converesion, and CSS layouts should be encouraged.

[quote=Luke Redpath]No professional web developer should be using table-based layouts in 2005 and whilst I realise this person isn't a pro, the fact that they are making the effort should be praised and tableless layouts should be encouraged.[/quote]

Unless of course browsers won't render your pages ...or... you need to display tabular data.

Tables aren't going anywhere my friend, and while CSS layouts are the creme de la creme, tables are still the viable solution until browsers become more standards compliant.

---

### Post by Zarkoth on 2005-10-26
Success!

Heh, although absolute positioning has been declared to be the devil previously, it seems that absolute positioning when used inside an embedded CSS seems to work...I took the suggestion of googling for common CSS bugs, and found a page that was a test for the version of IE we use at our school, and being that it was working fine, and I was a bit desparate, I simply had to have a look ;).

I'm just glad I could get it to work, heh.  I'll probably end up overhauling the school's entire web page later on in the year....it needs a lot of work.

But anyway, thanks for all your help!

---

### Post by Pathogenix on 2005-10-26
[QUOTE=Luke Redpath]
No professional web developer should be using table-based layouts in 2005 and whilst I realise this person isn't a pro, the fact that they are making the effort should be praised and tableless layouts should be encouraged.[/QUOTE]

Are you a professional developer? I'm just curious... most of the other developers I know are a bit more pragmatic than this. See, for example, Jeffrey Zeldman.

Glad you got things working, Zarkoth - CSS has a _weird_ learning curve but it all starts to make sense once you grok the box model. You might want to google "css box model tutorial" and see what comes up, because these things are a lot easier once you understand the, admittedly poor, reasoning behind them.

Hopefully the kinks with CSS will be slowly ironed out. It's a nice technology, and it's more flexible than tables, but some things are practically impossible to do effectively without resorting to hacks, kludges, and table-based layouts.

And don't forget - when in doubt, use someone else's code :)

---

### Post by David Marrs on 2005-10-26
[QUOTE=Pathogenix]
(Responding to Luke Redpath, who said "No professional web developer should be using table-based layouts in 2005 and whilst I realise this person isn't a pro, the fact that they are making the effort should be praised and tableless layouts should be encouraged.")

Are you a professional developer? I'm just curious... most of the other developers I know are a bit more pragmatic than this. See, for example, Jeffrey Zeldman.[/QUOTE]
I am, and I'd be inclined to agree. The final decision you make should obviously be based on what your site's actual traffic is, but as a general rule you should avoid tabular layouts and use xhtml where you can. Some old browsers don't support CSS, and so you can use a tabular layout for better backwards compatibility, but by doing this you're making life more difficult for the growing number of mobile phone and pda users, for whom tables mean a lot of sideways scrolling. Even Windows '95 users can install Firefox by now, so the arguments in favour of supporting old versions of Netscape and IE have been getting weak.

Obviously tables are still used for holding data, but I think Luke Redpath was refering to *page* layout, for which they were never designed in the first place.

---

### Post by Joh_ on 2005-11-25
Only answer I've got to most float problems: [http://css.maxdesign.com.au/floatutorial/](http://css.maxdesign.com.au/floatutorial/)

---

### Post by sapo on 2005-11-25
Wow, nice tutorials, already in my bookmarks, those are gonna be very usefull :D

---

