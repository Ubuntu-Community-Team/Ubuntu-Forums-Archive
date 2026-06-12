---
title: "Need help with simple html div layout (toolbar, sidebar and content)"
date: 2009-03-12
forum: Programming Talk
---

### Post by Yuzem on 2009-03-12
I have searched the web but nothing work as I want it to.
The layout I want is just as any many normal desktop applications: toolbar, sidebar and content.

The toolbar and the sidebar have a specific size in pixels. The content must be elastic. The problem is to make the height of the sidebar and the content to take all the remaining space.

This is what I have so far:
```

#toolbar {
	text-align:right;
	background-image: url(images/toolbar.png);

	height: 39px;

	border-bottom-style: solid;
	border-color: #8F8F8F;
	border-width: 1px;
}

#main {
	vertical-align: top;
}

#view {
	margin-left:151px;
	height:100%;
	overflow: auto;
}

#sidebar {
	float:left;
	padding-left: 9px;
	padding-right: 9px;
	padding-bottom: 9px;
	width:150px;
	background-color:#D6DDE5;
	height:100%;

	border-right-style: solid;
	border-color: #A1A1A1;
	border-width: 1px;

	overflow: auto;
}
```

The html is something like this:
```
<div id=toolbar></div>
<div id=main>
  <div id=sidebar></div>
  <div id=view></div>
</div>
```

The problem is that the vertical size of the content and sidebar are 100% plus the size of the toolbar (the scrollbar is always displayed).

Thanks in advance!

---

### Post by hastur on 2009-03-12
hi,

the best I found at the time :
[http://matthewjamestaylor.com/blog/ultimate-2-column-left-menu-pixels.htm]("http://matthewjamestaylor.com/blog/ultimate-2-column-left-menu-pixels.htm")

in short, all you have to do is create a div container for the header+sidebar+content and give it min-height:100% (or height:100% for IE) then use background colors witfully to give the impression the sidebar is 100% height when it's really shorter.

I did some testing at the time (feel free to use the css) :
[http://eauc.free.fr/test/layout/]("http://eauc.free.fr/test/layout/")
this one with a menu :
[http://eauc.free.fr/test/layout_4/]("http://eauc.free.fr/test/layout_4/")
an actual website :
[http://www.acalbertville.com/]("http://www.acalbertville.com/")

---

### Post by Yuzem on 2009-03-12
Thanks for the answer.
> **hastur said:**
> in short, all you have to do is create a div container for the header+sidebar+content and give it min-height:100% (or height:100% for IE) then use background colors witfully to give the impression the sidebar is 100% height when it's really shorter.
The problem is that the content has a background image, it is a shelf and it has to scroll with the content. Any other ideas?

---

### Post by hastur on 2009-03-12
> **Yuzem said:**
> The problem is that the content has a background image, it is a shelf and it has to scroll with the content.

I'm not sure I understand the problem here, with this method the content can have a normal background : color, image, scrolling or not...
the only visual trick is to use the background of the html element as the background of the sidebar (which can be plain color or an image too).
if you look at the first of my test layout, you can see the two level of background available for the content :
- one is white and has the same height as the text.
- one is (very) light blue and has a 100% height.
header and footer has their own background, but the two side columns share the same one, which in your case should not be a problem as you have only one sidebar.

---

### Post by Yuzem on 2009-03-12
> **hastur said:**
> I'm not sure I understand the problem here, with this method the content can have a normal background : color, image, scrolling or not...
The problem is that if I don't set an height value the scrollbars don't show up (overflow: auto). It has to work exactly as for example thunar.

> **hastur said:**
> the only visual trick is to use the background of the html element as the background of the sidebar (which can be plain color or an image too).
Yes the sidebar is ok except for the scrollbar problem but how do I make the background for the content to fill all the space?

---

### Post by Can+~ on 2009-03-12
> **Yuzem said:**
> The problem is that the content has a background image, it is a shelf and it has to scroll with the content. Any other ideas?

[background-attachment:scroll;]("http://www.w3schools.com/css/css_background.asp")

---

### Post by Yuzem on 2009-03-12
> **Can+~ said:**
> [background-attachment:scroll;]("http://www.w3schools.com/css/css_background.asp")
Well... I realized that that wasn't a problem after all. If the content div has a content large enough to need scrolling the faked background will not be visible. The other problems remain:
1. How to fake the background of the content div
2. How to make the scrollbars appear when necessary for the sidebar and content without setting the height.

Thanks so far!

---

### Post by myrtle1908 on 2009-03-12
You should really consider using one of the JS frameworks if you are trying to achieve complex desktop-like layouts.

Have a look at ExtJS [http://extjs.com](http://extjs.com) or JQuery [http://jquery.com](http://jquery.com)

For example, in ExtJS to create a layout such as you are attempting it is as simple as:-

[PHP]
var toolbar = new Ext.Toolbar({...});
var sidebar = new Ext.tree.TreePanel({...});
var content = new Ext.Panel({...});
var vp = new Ext.Viewport({
  layout: 'border',
  items: [{
    region: 'north',
    height: 32,
    items: [toolbar]
  },{
    region: 'west',
    width: 200,
    items: [sidebar]
  },{
    region: 'center',
    items: [content]
  }]
});[/PHP]

There is obviously a little more to be done with the above example but you get the idea.

The drawback of these JS libraries is that they are quite large so if you are just serving up a trivial "about me" page or similar then you obviously wouldn't go with this.

---

### Post by Yuzem on 2009-03-12
Those are very interesting technologies... but they seem a little to much to learn just to make a simple layout.

I think I will end up using tables... is just that I have read a lot about not using tables and that divs can do everything tables do...

Anyways, if someone has a div + css solution for this problem please let me know.

---

### Post by myrtle1908 on 2009-03-12
> **Yuzem said:**
> I think I will end up using tables... is just that I have read a lot about not using tables and that divs can do everything tables do..

I wouldn't take any notice of the childish CSS vs tables for layout arguments.  They are terribly emotive and serve almost no purpose.  Browsers aren't about to stop table support.

Just use what makes most sense in your brain and don't get bogged down worrying whether or not you are doing things the "right" way.

---

### Post by hastur on 2009-03-13
I seem to have a really hard time understanding what you want, and how my first layout doesn't fit...

> **Yuzem said:**
> If the content div has a content large enough to need scrolling the faked background will not be visible.

well, if by faked background you mean the html background used for the side bar, it will never be visible under the content, whatever its height.

> 1. How to fake the background of the content div

I don't see the need to "fake" it, just "set" it. it will work normally... no ?
I changed my first layout test to display an image as background for the content. please tell me exactly how this is not what you want.
[http://eauc.free.fr/test/layout/]("http://eauc.free.fr/test/layout/")

> 2. How to make the scrollbars appear when necessary for the sidebar and content without setting the height.

once again I'm not sure I understand everything :
play with the font size of my first example (ctrl+mouse wheel under FF) and you'll see the vertical scroll bar appears when necessary for the sidebar or in this case the content.

> Thanks so far!

you're welcome, even if I'm not sure to be of any help/understanding at all. must be needing some sleep :\

---

### Post by Yuzem on 2009-03-13
Well... I found out that it does not work neither with tables.
I don't care anymore about the background problem, I just want the scrollbars to work.

If I use all tables "overflow: auto" doesn't work.
If I use div I can't give them an height to fill the space below the toolbar so the the scrollbars appear when the content is not visible.
If I combine tables and divs, the div doesn't inherit the table size.

I want to do exactly what google reader does.
It seems that the only way to do it is to dynamically change the height with javascript.

---

### Post by Yuzem on 2009-03-13
> **hastur said:**
> I changed my first layout test to display an image as background for the content. please tell me exactly how this is not what you want.
[http://eauc.free.fr/test/layout/]("http://eauc.free.fr/test/layout/")
I will try: In your layout the content doesn't have a scrollbar that shows only for that div when necessary like google reader. Suppose you have a scrollbar. If the scrollbar appears, when scrolling, the background will not scroll with the content. The content is fill with icons on a shelf, the background, so it has to scroll together.
> **hastur said:**
> once again I'm not sure I understand everything :
play with the font size of my first example (ctrl+mouse wheel under FF) and you'll see the vertical scroll bar appears when necessary for the sidebar or in this case the content.
Only one scrollbar appears, I need one for the sidebar and one for the content.


you're welcome, even if I'm not sure to be of any help/understanding at all. must be needing some sleep :\[/QUOTE]

---

### Post by Yuzem on 2009-11-26
Accidentally I found the answer (no javascript needed):
[http://stackoverflow.com/questions/485827/css-100-height-with-padding-margin](http://stackoverflow.com/questions/485827/css-100-height-with-padding-margin)

It works perfectly!

---

