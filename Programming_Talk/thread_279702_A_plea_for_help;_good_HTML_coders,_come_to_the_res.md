---
title: "A plea for help; good HTML coders, come to the rescue!"
date: 2006-10-18
forum: Programming Talk
---

### Post by maniacmusician on 2006-10-18
Hey guys,

I'm looking for some seriously experienced people who can troubleshoot a problem for me. the problem is at [http://dohickey.sourceforge.net/client/download.shtml](http://dohickey.sourceforge.net/client/download.shtml) . If you look down at the bottom of the page, the footer won't load correctly and sticks to the section above it. The footer works fine on all other pages. The situation is rather complicated. I've implemented <div> sections and SSI's and whatnot and it's really hard to explain in a thread.

I just need someone with a lot of experience to troubleshoot this for me. I've been at it for 3 nights! and it's simple code as well. Just some anomaly happening. If you think you can help, please please please step forward, and i'll try to better explain the situation.

---

### Post by aysiu on 2006-10-18
I'm hoping you might get some good help from programming talk.

---

### Post by justin whitaker on 2006-10-18
It looks like the container above is auto expanding to cover that last CVS quote. That's mucking up the layout, because the browser is not rendering all those breaks.

Have you thought about giving the center section a fixed width in the css file? You could also give the footer a fixed location in the css sheet.

BTW, do not look at the site in IE. :rolleyes:

---

### Post by rbalfour on 2006-10-18
```

</div><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
				<div class="contain" style="padding-top: 50px; padding-bottom: 0%;">**<div>&nbsp;</div>**
	<div class="footer">
		<div class="tr">
			<h4>Copyright 2006, Martin Owens and Uddit Sachdev</h4>
		</div>
	</div>
</div>
			</div>

```
Will this work for you?

---

### Post by iovar on 2006-10-18
I removed the breaks and added a hidden div. It works for me on konq and firefox.

EDIT: and from what I see rbalfour is right.  Removing all the breaks
and entering one &nbsp; instead does it, too.

---

### Post by maniacmusician on 2006-10-19
okay, that worked; but can someone please explain why? I can see that you added the nonbreaking space inside a div, and added an extra </div>....why? did I have an unclosed div section somewhere? if so, where? it didnt show up when i put it through the w3c validator. Sorry to bug you but i'll go crazy if I don't know why. Also, why was it happening with only this page?

@justin: I'm pretty sure the center does have a width. I was pretty much learning *while* creating the css and whatnot, so i mucked with it. Right now it's just a bunch of divs with classes embedded inside one another with the superceding ones having control over the width and the inner ones having control over the font, contour and whatnot. The site is also definitely not supposed to look good in IE, it's a linux based project :). IE also doesn't handle the transparency's in the png very well, so they come out with a gray background. this is apparently fixed in IE7, but eh. what a POS. 

@aysiu: thanks for moving the thread. didnt even know this section existed!

i have some more questions but i figured I'd better wait until my first couple get answered.

thanks guys.

---

### Post by tturrisi on 2006-10-19
Several things will cause layout issues in the code of the site's pages;
1. div has no property assigned in the css file thus should not use this:  <div>&nbsp;</div>

2. this is sloppy (but sometimes works):  </div><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
Use margin-top for child element or use a 1x1 transparant gif <img> for exact spacing, never use line break for layout spacing because the <br> inherits it's line-height dimension from a font style or browser default font.  Mozilla & Firefox always display slightly smaller text than same code displayed in other browsers.

3. this could potentially cause a problem in layout because no position style is defined:
.footer {
	background: url("../images/tl.png") 0 20% no-repeat;
	background-color: #A0A0D0;
	color: red;
	text-align: center;
	**height: 100%;**
The height:100% is supposed to relate to the parent element, but can get kinda screwy if use a parent like this:
<div class="contain" style="padding-top: 50px; padding-bottom: 0%;">
because the height:100% does not take into account the parent's padding-top:50px.

Keep it simple and define ALL blocks in the stylesheet.  Too many nested <divs> make it really tough to control layout and debug when needed.

Footer is same on all pages, thus just give .footer ALL needed layout properties in the stylesheet.  How & where IT gets displayed should be of no concern to other elements, thus do not try to control footer using css properties of other elements or blocks.

> 
i have some more questions but i figured I'd better wait until my first couple get answered
ask away!

---

### Post by maniacmusician on 2006-10-20
wow thank you! i sort of understood that. I'll keep it in mind for future projects, but I don't think i should mess with what i have now, since it's working. I know that nested div's can create a problem, which is why I was hesitant to do it, but it was the best way for me to control grouping of objects (with the knowledge that I had). this was necessary and mostly only done during the stage where I was trying to make the site low-resolution compliant. That stats box would float all the way to the right. If i float: left 'd it, then it would interfere with other sections. So i nested it even more, and that seemed to work.


anyways, my other question is, the footer is not working very well in Opera or Konqueror. actually those 2 display similar problems as IE in rendering it. I'm sure it has to do with the nesting of div's again (but nesting was necessary for the rounded corners), and that I attributed the wrong properties to the wrong div section. I tried to follow the same outline as with the content pages, which also has rounded corners, but I guess that didn't work so well with the footers. I was going to tackle this problem over the next few nights, but if someone experienced can take a glance at the code of the footer ( [http://dohickey.sourceforge.net/client/client-foot.html](http://dohickey.sourceforge.net/client/client-foot.html) ) and the css file ([http://dohickey.sourceforge.net/client/main.css](http://dohickey.sourceforge.net/client/main.css) ) and can pick up whats wrong right away, that'd be a help. If it's too much of a bother, that's okay too, I'll get around to it myself, it'll just take me a little longer :) 

thanks a lot again guys, for the awesome responses.

note:you'll have to view the code of the footer page in order to see its classes, because obviously it's not going to show up the way it's supposed to without the link to css file.

---

### Post by tturrisi on 2006-10-20
Best to "control" the rounded corner positioning using table cells or align styles:
Existing:
```

.footer {
	background: url("../images/tl.png") 0 20% no-repeat;
	background-color: #A0A0D0;
	color: red;
	text-align: center;
	height: 100%;

<div class="contain" style="padding-top: 50px; padding-bottom: 0%;"><div>&nbsp;</div>
        <div class="footer">
                <div class="tr">
                        <h4>Copyright 2006, Martin Owens and Uddit Sachdev</h4>
                </div>
        </div>
</div>
```

Try this
example page:
[http://members.cox.net/tonyt/maniacmusician/](http://members.cox.net/tonyt/maniacmusician/)
stylesheet:
[http://members.cox.net/tonyt/maniacmusician/main.css](http://members.cox.net/tonyt/maniacmusician/main.css)
html source:
[http://members.cox.net/tonyt/maniacmusician/source.txt](http://members.cox.net/tonyt/maniacmusician/source.txt)

The MAIN reason why your layout gets messed up is the fact that the <body> has no font property assigned to it, thus the browser determines what font is being used.  This is no good because many folks set goofy fonts as their defaults and that plays havoc w/ page layout.

This is especially true when use heading tags <h1> <h2> <h3> etc.  A heading by default has a very large top & bottom margin (whitespace).  This margin should be controlled using css width & height.  And this whitespace is handled differently in different browsers.

In fact, one should not use heading tags at all in a footer!  A heading has a specific purpose, i.e. it says, "this is a new section and the content below me is all about...".  

If use a block of elements on all site pages, such as header & footer, then define the text using <p> styles.

see this wonderful guide (describeds your issue w/ the whitespace above & below elements):
[http://www.w3.org/MarkUp/Guide/Style](http://www.w3.org/MarkUp/Guide/Style)

tip:
use this to locate obscurities when degugging:
(be patient, it's sometime slow loading)
[http://validator.w3.org/check?uri=http%3A%2F%2Fdohickey.sourceforge.net%2Fclient%2Fdownload.shtml](http://validator.w3.org/check?uri=http%3A%2F%2Fdohickey.sourceforge.net%2Fclient%2Fdownload.shtml)

On another note, how are you at bash scripting? I need some help here:
[http://www.ubuntuforums.org/showthread.php?t=280346](http://www.ubuntuforums.org/showthread.php?t=280346)

---

### Post by maniacmusician on 2006-10-20
I don't know anything about bash scripting, sorry :( . I do use the w3c validator sometimes. I'll check out your files when I get home to see the changes you've made. you understand, cant just replace my files with yours without knowing exactly whats going on. Thanks for the help :) Hopefully that will be the end of my troubles.

---

### Post by tturrisi on 2006-10-20
Understood.  Just try some code on one page after backing up the existing page.  Cut+Paste different sections and see if works within an existing page. At minimum, the footer table will work.

---

