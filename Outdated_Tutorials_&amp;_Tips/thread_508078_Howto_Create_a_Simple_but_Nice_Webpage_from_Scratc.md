---
title: "Howto Create a Simple but Nice Webpage from Scratch"
date: 2007-07-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Gen2ly on 2007-07-23
**[SIZE="4"][COLOR="DarkRed"]Howto Create a Simple but Nice Webpage from Scratch.[/COLOR][/SIZE]**

Definitely in our modern age, it's about making thing simpler, a little bit easier.  Now we see, where once we created, webpages already manufactured so that we can do the things most important to us, blog, show visitors our pictures.  These webpages are nice but but if you are interesting in learning webdesign or want to have a custom design, this tutorial should be a good start.  Since I just created an internet site, I'll be using it as an example.

The basic law today is to use .html files for your wording and .css files for style.  I use Gnome so the commands will be Gnome-specific, it shouldn't be too difficult to figure out on other desktops however.

Create two new files.  Create a new folder on the Desktop, pick a name for your webpage and enter the folder.  In the folder Right-click and select "Create a Document" then "Empty File".  Name one "index.html" and the other "default.css".  Right-click on these new files and open them with the text-editor.  I use Geany:

[IMG]http://www.archive.org/download/LittleCreativity-HowtoCreateASimpleButNiceWebpageFromScratch/01-GeanysGotit.png[/IMG]

I've included the example templates I created.  They are well commented that may be easier to use on their own.  You decide.  I'll point out whats important:

**[COLOR="DarkRed"]Creating the html[/COLOR]**

We'll start with the [FONT="Fixedsys"][COLOR="DarkOrange"]example.html[/COLOR][/FONT].

You'll need to specify [FONT="Fixedsys"][COLOR="Green"]DOCTYPE[/COLOR][/FONT] at the top of the document.  Strict is often used and since we're writting this is shouldn't be too much trouble to follow the rules.
[FONT="Fixedsys"]
[COLOR="Green"]<html>[/COLOR][/FONT] signals the beginning of the html document.  You'll notice for any given tag, there's a closing tag.  There are a few exceptions like [FONT="Fixedsys"][COLOR="Green"]<br>[/COLOR][/FONT].  To close a tag use the forward slash in the tag: [FONT="Fixedsys"][COLOR="Green"]</html>[/COLOR][/FONT]

I always like to comment my tags so that I can easily refer back to them without translating code.  To do that prepend a comment with [COLOR="Gray"]<!--[/COLOR] and append with [COLOR="Gray"]-->[/COLOR]

[COLOR="Green"]<header>[/COLOR]: define the meta data, and title, and css script.  The header section uses meta data to alert search engines of the basic type of content that is in a webpage.  It used to be real important to have a very complete meta section but I not sure they are used as much now.  The example doesn't show search engine metadata, only shows what's needed.  The title is what is display on the Titlebar in the browser.  You'll also need to point where you css script is.

The [FONT="Fixedsys"][COLOR="DarkOrange"].html[/COLOR][/FONT] file refers to the css script for further formating.  In the [COLOR="DarkOrange"][FONT="Fixedsys"]exampletutorial.html[/FONT][/COLOR] [FONT="Fixedsys"][COLOR="Green"]<div id="background">[/COLOR][/FONT] refers to the css entry [FONT="Fixedsys"][COLOR="Green"]#background[/COLOR][/FONT].  These are often called CSS Boxes in the webdesign world.  The css entry can define what [COLOR="Green"][FONT="Fixedsys"]<div id="background">[/FONT][/COLOR] is.  Color, shape, images...  In the [FONT="Fixedsys"][COLOR="DarkOrange"].html[/COLOR][/FONT] section, I put in and [FONT="Fixedsys"][COLOR="Green"]<a href[/COLOR][/FONT] section which essentially means nothing.  Browsers need to have information in between div tags to work.  Yes, I know, it's weird.

The next section I input the image tabs - links to the other pages.  I'll make these rollover tabs.  The initial images will be defined here and I'll specify the rollover ones in the css script.  You'll notice you can specify their location, use the absolute variable if you don't want the the browser trying to move the images.  Also be sure to link them to the other [COLOR="DarkOrange"][FONT="Fixedsys"].html[/FONT][/COLOR] files you will create.  A basic webpage structure that a lot of people use is to put all html files in the base directory, then putting your images in an seperate image directory:

[IMG]http://www.archive.org/download/LittleCreativity-HowtoCreateASimpleButNiceWebpageFromScratch/03-screenshot-museumAtThePortage-FileBrowser.png[/IMG]

Ok back on topic.  You may have seen in the tab section that it's listed.  [FONT="Fixedsys"][COLOR="Green"]<ul>[/COLOR][/FONT] is short for "unordered list" (meaning it doesn't show numbers), [FONT="Fixedsys"][COLOR="Green"]<li>[/COLOR][/FONT] is the "list item".  The reason these are in here is to specify to the css script where to put the hover images later.

The next [FONT="Fixedsys"][COLOR="Green"]div[/COLOR][/FONT] section defines the text columns, position, and finally the text!

**[COLOR="DarkRed"]Creating the CSS[/COLOR]**

Since the css style sheet ( [FONT="Fixedsys"][COLOR="DarkOrange"]example.css[/COLOR][/FONT] ) is pretty well commented, I'm not gonna take too much time explaining it.  Since css can have hundreds of different functions and adding these functions can be used like script, it can become very encumbering to a new user.  For now, just use the basic examples that I have given and work with those.  These will give you the basic functionality of items like backgrounds and links and text formatting.  If you want to learn more, the tutorial that I learned the from was this one:

[**[COLOR="Sienna"]_CSS from the Ground Up_[/COLOR]**]("http://www.wpdfd.com/issues/70/css_from_the_ground_up/")

Some designers use text headers to define font size.  These are basic formattings from the webs early days.  You can further define them in css and some examples are given.  Likely though, you'll just define one for the body, and use the example to format for special sections.  I've heard several designers say they prefer to use the size spec ([FONT="Fixedsys"][COLOR="Green"]xx-large,x-large,large,medium,small,x-small,xx-small[/COLOR][/FONT]) as it seems to scale well between browsers and monitor sizes nicely.

The section [FONT="Fixedsys"][COLOR="Green"]start #nav[/COLOR][/FONT] should be left alone.  This section defines the rollover tabs.  In the [FONT="Fixedsys"][COLOR="Green"]start #nav ids[/COLOR][/FONT]  section is where you specify the rollover images.

**[COLOR="DarkRed"]Create the images for the site with Gimp[/COLOR]**

If you've never used gimp before you should read a little about it before you dive in.  If you've used Photoshop, you'll find that gimp feels familiar.  I'll just go over the basics and let you do all the creative work.

First decide a size for your page.  Monitor sizes keep growing, but if you have a larger monitor you may find that others will see your website in tunnel vision.  To be safe, a site 1024x768 will suit most users.

Sketching, if you're an artist is probably the best way to start a design.  You can get your proportions and sizes as you'd like them then just scan the image.  Alternatively, you can do a sketch with gimp.  Both of these can be put in the background layer and used for reference.

The amazing thing about gimp is layers.  If you made a error, hopefully you made that error on a different layer as it can be erased or hidden.  And sometimes layers that don't look nice at the given time later on in the process will.

[IMG]http://www.archive.org/download/LittleCreativity-HowtoCreateASimpleButNiceWebpageFromScratch/05-Create-by-layers.png[/IMG]

You might like to think about creating images seperately as often they too can become many layered deep. Importing them in later isn't that difficult.

[IMG]http://www.archive.org/download/LittleCreativity-HowtoCreateASimpleButNiceWebpageFromScratch/10-Create-elements-seperately.png[/IMG]

Guides are great and often necessary.  I use them to create even sizes and items symmetrical (tabs are a perfect example).  Place these before you start any heavy lifting. :)

[IMG]http://www.archive.org/download/LittleCreativity-HowtoCreateASimpleButNiceWebpageFromScratch/40-UseGuides.png[/IMG]

Since the guides are in place, doing the tabs is easy.  Create a new layer, use black or white for the color, and fill in boxes you need.  Then lower the opacity of the layer until you have the image you like.  With the "Rectangle Select Tool" select each tab and "Copy Visible" in the Edit menu.  Open a "New" file of equal size and paste the image into it.  Save these as [FONT="Fixedsys"][COLOR="DarkOrange"].pngs[/COLOR][/FONT] or high quality [COLOR="DarkOrange"][FONT="Fixedsys"].jpgs[/FONT][/COLOR].

[IMG]http://www.archive.org/download/LittleCreativity-HowtoCreateASimpleButNiceWebpageFromScratch/55-Rollover-tabs.png[/IMG]

As you can see I used a background image that covered a good deal of the page, I experimented with a couple different ones, for this too you can use "Copy Visible" ability.  Hide the others layers before you do so.  Also be sure the image is specifid in the [COLOR="DarkOrange"][FONT="Fixedsys"].css[/FONT][/COLOR].

That should be about it.  With that you should about this time can have a beautiful looking webpage.  This is what mine looked like when I finally released it:

[IMG]http://www.archive.org/download/LittleCreativity-HowtoCreateASimpleButNiceWebpageFromScratch/99-screenshot-museumAtThePortage-MozillaFirefox.png[/IMG]

---

### Post by Gen2ly on 2007-07-24
Doh, updated the header.

---

### Post by rich.bradshaw on 2007-07-24
Good tutorial, maybe you should include example images in the zip so that the site looks good - or host it somewhere so people can see it...

<br> should be <br /> in XHTML as well - every tag has to close...

---

### Post by Gen2ly on 2007-07-24
thanks rich.  I'm in the process of having the site put on a server, and will definitely let people know of it when its available.

yes every tag does close, but I've noticed in the most expensive internet creation suites that this <br> is still widely used.

---

### Post by Gen2ly on 2007-08-08
Fixed a few errors and basic cleanup.

---

