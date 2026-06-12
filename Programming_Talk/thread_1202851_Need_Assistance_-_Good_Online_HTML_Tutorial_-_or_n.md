---
title: "Need Assistance - Good Online HTML Tutorial - or ninja's will kill my family!!!"
date: 2009-07-02
forum: Programming Talk
---

### Post by drbrando007 on 2009-07-02
OK Community, I am well aware this a non-linux issue, but I really dig the deep experience present in our community. Here is the story:

A computer programmer with a good decade + of programming experience, in numerous languages (whatever the situation required), is now going to do what every twelve year old and their grandmother have done, he has to put up a couple of website's or else he will not be given the antidote for the poison that was dubiously given to him by a wacky pseudo-fascist terrorist cell. Will you help this doomed and intrepid programmer find the path of least resistance? HTML Tutorial suggestions, s'il tu plait?

I know HTML is so basic, so dumb, so easy, that I should have just learned and executed with it 15 years ago, and made some money in that dot-com boom. But I was too proud, and now, I will most surely die a painful and horrifying death if I cannot get these basics down. I am CSS-ing the sheeit out of this, blah blah my php coding is solid. I cannot get my href's to line up to all my custom elements, so basically, I need the basics.


PLEASE POST SOME PLACES I CAN GET THAT BASIC HTML TUTORIAL, THESE GUYS ARE SERIOUS, AND I DON'T KNOW HOW LONG THEY WILL WAIT!!!

...stayed tuned to see whether or not I will make it...AIIIIEEEEEEE

---

### Post by wojox on 2009-07-02
Go to [http://www.w3schools.com/](http://www.w3schools.com/) they have lots of web programming tutorials.

---

### Post by MadsRH on 2009-07-02
> - or ninja's will kill my family!!! 


:lolflag:

HA HA HA

---

### Post by bodselecta on 2009-07-02
If you've got time and you want something standards compliant/cross browser compatible, google for advanced css layouts
e.g.
[http://www.webreference.com/authoring/style/sheets/layout/advanced/](http://www.webreference.com/authoring/style/sheets/layout/advanced/)

you'll see tips like using divs, but not too many and no table layouts (you should only use tables for data), use css (css2) to style the html with no inline  document styling, css has inheritance so if you learn your html document structure you can order how your website will look.....
you can create quite advanced menus and layout with basic html, but using css selectors and styling plus it keeps the html tidy (lots of other good reasons too)

it's a bit of a minefield but if you search for good examples it should get you going.

and if you've not already got it, get firebug for firefox, it's a brilliant web developers tool

---

### Post by drbrando007 on 2009-07-02
> **MadsRH said:**
> :lolflag:

HA HA HA

yeah yeah yeah, laugh it up.

see how funny you think it is when the ninjas come for YOU!!!

---

### Post by Can+~ on 2009-07-02
> **drbrando007 said:**
> yeah yeah yeah, laugh it up.

see how funny you think it is when the ninjas come for YOU!!!

Then I'll release my army of zombie pirates.

+1 to w3schools to learn (X)HTML

> I am CSS-ing the sheeit out of this

Actually, that's pretty good. Having the visual aspects solved on CSS properly is better than hard coding properties on HTML, mostly because of the rule "separating content from design".

---

### Post by drbrando007 on 2009-07-02
> **bodselecta said:**
> If you've got time and you want something standards compliant/cross browser compatible, google for advanced css layouts
e.g.
[http://www.webreference.com/authoring/style/sheets/layout/advanced/](http://www.webreference.com/authoring/style/sheets/layout/advanced/)

you'll see tips like using divs,  ...

I will check your link, I have done a CSS tut already, but I lacked the HTML groundwork, definitely tables are out (unless I have to...), and I was pretty much counting on most of these HTML Tut's to be laying into me with table after table after table implementations.

Thanks, I'm trying to find a quiet place to gloss the www3 Tut's (ty @wojox), and definitely will check your link, look for examples etc. Pretty much as you had mentioned, advanced dynamic menu creation is where I am right now.


AIIIEEEEEEEEEEEEEEE (the pain, the pain)

---

### Post by Can+~ on 2009-07-02
> **drbrando007 said:**
> I will check your link, I have done a CSS tut already, but I lacked the HTML groundwork, definitely tables are out (unless I have to...), and I was pretty much counting on most of these HTML Tut's to be laying into me with table after table after table implementations.

Thanks, I'm trying to find a quiet place to gloss the www3 Tut's (ty @wojox), and definitely will check your link, look for examples etc. Pretty much as you had mentioned, advanced dynamic menu creation is where I am right now.


AIIIEEEEEEEEEEEEEEE (the pain, the pain)

div's are the way to go. The thing is that you must understand the "block" rule on HTML, that objects behave like boxes with rules.

Then, div's have the particular behaviour of being either "fixed" (see, [FONT="Courier New"]position, float[/FONT]) into the layout and be part of this block structure, or being positioned "absolute" or "relative", existing above the content determined by it's z-index (see... well, [FONT="Courier New"]z-index[/FONT]).

Use tables only to present actual data tables (sounds redundant), not for styling.

---

### Post by drbrando007 on 2009-07-02
> **Can+~ said:**
> div's are the way to go...

Yeah, I div.

I ran into some trouble here,(not sure how to encaps for code in the forum)

the div id is menu,
the css looks like this:

#menu{blackety; blah;}

#menu item{to line up horiz (no linefeeds);to make it look like a button;}


;

And then when I <item><a href....></item> I don't quite get the result I was looking for in the link function or even in the positioning of the link as evidenced on the bottom of my FF browser when you mouse over the entire area of the div.

Brushing up on the HTML basics so I get the inheritance patterns better...

(hurts a little less, but still pretty serious) ps: zombie pirates, whoa that kicks *****

---

### Post by drbrando007 on 2009-07-02
> **bodselecta said:**
> ...
and if you've not already got it, get firebug for firefox, it's a brilliant web developers tool

@bodselecta

Any opinion on "Font Finder" vs "Firebug", just recently installed it for this very purpose.

will examine Firebug as well...

---

### Post by bodselecta on 2009-07-02
Firebugs what you want, honestly it's great, you'll understand your DOM and what css is being applied, you can also change css on the fly to see how it effects the page....
javascript debugging is brilliant too....

anyway, i wasn't sure exactly what you were trying to do with your menu, but you can create a css button by using a css display:block, you can use css background for the image off and use a :hover selector for rollover..
you can use floats to create a horizontal menu too...

---

### Post by Can+~ on 2009-07-02
Menu has an ul (unoredered list)? It should be

[PHP]#menu
{
	/* Blah */
}

#menu ul
{
	list-style-type: none; /* Corrected */
	padding-left:0px;
	text-indent:0px;
}

#menu ul li
{
	
	background: url("image that looks like a button");
	display:block;
	
	/* Also define height so the background image won't get cropped */
}


#menu ul li:hover
{
	background: url("image that looks like a button beign hovered");
}[/PHP]

Writing this from the top of my head, not sure if it will work, but I'm sure I've got the nested elements right.

---

### Post by drbrando007 on 2009-07-02
> **bodselecta said:**
> ....
anyway, i wasn't sure exactly what you were trying to do with your menu, but you can create a css button by using a css display:block,...

> **Can+~ said:**
> Menu has an ul (unoredered list)?...

The menu is dynamically created with MySQL queries, and I thought that <ul> was going to give a line feed, so I created the #menu item{} piece.

Absolutely working on getting the placement/spacing(of everything), have not had the chance to lookup z element/index yet.

Right now I have it going across at the top, under a different div successfully as just <item/>, when I add the <a href/> it does not correctly line up the proper click spacings, as in directly underneath the elements created. Had <item> set up with a good height and a {border:ridge;}, so it is somewhat buttonesque

Oh yes, and thank you both for helping me try to stay afloat, hell, when I get it, I'll post the correct ways and start a multimillion dollar business with my own html tips. jk...

---

### Post by bodselecta on 2009-07-02
shouldn't it be
#menu ul { list-style-type: none;}

and you should be selecting the anchor for the background and hover

---

### Post by drbrando007 on 2009-07-02
> **bodselecta said:**
> shouldn't it be
#menu ul { list-style-type: none;}

and you should be selecting the anchor for the background and hover

<ul> will give no linefeeds? <item> is not an official html tag, or is it? I thought I was creating a custom element, or was I wrong? Hmmm...

---

### Post by Can+~ on 2009-07-02
> **bodselecta said:**
> shouldn't it be
#menu ul { list-style-type: none;}

and you should be selecting the anchor for the background and hover

Again, did it from the top of my head; but I did correct the list-style-type.

And the anchor should be selected, yes, but I don't know if he wants a repeating image, a centered image, a left-upper'd image, dunno. So I left that empty.

> **drbrando007 said:**
> <ul> will give no linefeeds? <item> is not an official html tag, or is it? I thought I was creating a custom element, or was I wrong? Hmmm...

I looked for the <item> tag, but I can't find it. <li> means list item, and should be contained within a <ul> or <ol>, this forum has it for example:

Unordered list (ul):
[list]
[*]List item
[*]List item
[*]List item
[/list]

Ordered list (ol):
[list=1]
[*]List item
[*]List item
[*]List item
[/list]

And what's the problem with line feeds?

---

### Post by drbrando007 on 2009-07-02
> **Can+~ said:**
> ...
I looked for the <item> tag, but I can't find it. <li> means list item, and should be contained within a <ul> or <ol>, this forum has it for example:
...

And what's the problem with line feeds?

The way I had css'd, line feeds did not allow me to have the buttons go across horizontally. I do agree, that these elements should resemble some kind of unordered list type display, but I can't get the kinks out.
Yeah, and I'm not putting an image in there yet, just filling a background color maybe I can get a test screen shot posted...

Nope not here...
Im inventing the item tag here, because I thought I could create a custom child element of the #menu id that I had invented. This was done under the assumption that I would gain complete and total control of the display and placement of this element. But in my first thread, you will see that I do say that I know little about HTML- not even un peu

---

### Post by bodselecta on 2009-07-02
Ah i think i get you now, the 'items' ARE the li tags, you're not styling those though, you should be styling the a tags that make up the li content.
li's will expand to fit it's content.

and if you want a horizontal menu, you need to float the li's e.g
ul li{float:left;}  # these will sit side by side and stop your line feeds
and increase the ul width to fit the whole menu width....

there are other ways to do this too
hope it helps

---

### Post by tyblogger5 on 2009-07-02
Yes [W3Schools]("http://www.w3schools.com") is a great tutorial, follow the HTML tutorial there and you should be fine! ;-)
-tyblogger5

---

### Post by drbrando007 on 2009-07-02
> **bodselecta said:**
> Ah i think i get you now, the 'items' ARE the li tags, you're not styling those though, you should be styling the a tags that make up the li content.
li's will expand to fit it's content.

and if you want a horizontal menu, you need to float the li's e.g
ul li{float:left;}  # these will sit side by side and stop your line feeds
and increase the ul width to fit the whole menu width....

there are other ways to do this too
hope it helps

@bodselecta

Interesting that you should say that, about the a tags. I just changed a little bit of the code so that that my <a> comes before I call <item>.
Now it looks like this:
<a href....><item>MenuButton</item> - And now when I hover over each element, the correct link is showing on the bottom. However, I still have some spurious link evidence in areas where the 'buttons' are not even drawn(firebug has shown me some light on this subject, I can't thank you enough for that!). I will change it over to <ul> and <li> tags. I have acquired a fear over the positioning attributes in the last week of coding, so that it why I went 'off the reservation'. This is basically due to the fact that I just need to go check out those tutorial links.

It is working a little closer to what I was going for, I'll definitely examine why even these changes would affect it in this manner. Firebug, whew. I'll see if I can post when I get closer to the solutions.


This ought to get me closer to that antidote and keep those damn ninjas at bay for a while.
;)

---

### Post by HavocXphere on 2009-07-02
Man I hope that style of OP doesn't become a trend.:rolleyes:

Just ask for help. No need to dress it up in a fake Cry Wolf scenario w/ killing & pain.

---

### Post by drbrando007 on 2009-07-02
> **HavocXphere said:**
> 
Microsoft Patents the Crippling of Operating Systems. (Link: Patent 7,536,726) 

Well, you gotta make 'em laugh, or you gotta make 'em cry. Keep it light.

I followed your link, and I think I'm going to cry. Looks like ninjas are after our computers as well. You're not cryin wolf there, are ya? ;)

---

### Post by Can+~ on 2009-07-02
> **drbrando007 said:**
> Well, you gotta make 'em laugh, or you gotta make 'em cry. Keep it light.

I followed your link, and I think I'm going to cry. Looks like ninjas are after our computers as well. You're not cryin wolf there, are ya? ;)

Wasn't that used when your windows copy was considered pirated on Vista? I remember claims of the "Reduced Functionality" mode.

---

### Post by drbrando007 on 2009-07-03
> **Can+~ said:**
> Wasn't that used when your windows copy was considered pirated on Vista? I remember claims of the "Reduced Functionality" mode.

Whatever it was, the patent wasn't pushed through until May 19 of 2009...

---

### Post by drbrando007 on 2009-07-03
> **Can+~ said:**
>  into the layout and be part of this block structure, or being positioned "absolute" or "relative", existing above the content determined by it's z-index (see... well, [FONT="Courier New"]z-index[/FONT]).

++ for the z-index. Always knew something like this should exist, good looking out for helping me find it.

z-index rocks :guitar:

---

### Post by Krupski on 2009-07-03
> **drbrando007 said:**
> Need Assistance - Good Online HTML Tutorial - or ninja's will kill my family!!!

A Colt M1911 with 230 grain hollowpoints will stop most any ninja... :)

---

### Post by j7%&lt;RmUg on 2009-07-04
I learnt HTML in 2 days here back when i was only 12 years old:

[http://www.davesite.com/webstation/html/](http://www.davesite.com/webstation/html/)

or if you happen to not like those tutorials then +1 to w3schools.com.

or you can check out most of the other good ones by googling html tutorials.

---

