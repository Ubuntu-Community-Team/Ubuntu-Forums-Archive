---
title: "Scraping colors from the current Gnome/GTK/Metacity theme in Python"
date: 2008-08-02
forum: Programming Talk
---

### Post by Endolith on 2008-08-02
In [Bug 111061]("https://bugs.launchpad.net/ubuntu/+source/wine/+bug/111061") I suggested writing a script to scrape colors from Gnome and import them into Wine to make the color scheme match.  (There is theming support in Wine but it really hurts performance, so this would be a middle ground solution.)

Since I had been wanting to learn some Python, I tried to take a stab at it but got pretty stuck.  Most of it was already done for me by KillerKiwi; I added some things and fixed some things, but I cannot figure out how to get many of the colors.  Can anyone help with this?

Some of the colors can be found in gtk.something, but others either don't exist there, or don't match the actual colors being used, so I think that is the wrong place to be looking.  I think I need to get some of the colors from metacity or the other active window manager instead, since the window borders are not part of GTK, right?  (I don't even know how to figure out which window manager is running in Python.)

I know I can "import metacity", but I have no idea what to do with it, and can't find any documentation on it.

I posted my script so far in the thread [here]("http://ubuntuforums.org/showthread.php?p=5506889#post5506889"), but I don't think many Python experts are going to see it in the *Tutorials & Tips* section.

---

### Post by Endolith on 2008-08-22
No one knows anything about this?  I really don't understand the relationship between metacity and clearlooks and gtk.  I want to scrape the colors metacity uses to draw window borders and titles, but I can't find any documentation on this.

---

### Post by days_of_ruin on 2008-08-22
The metacity module is used for metacity theme previewing.Not what you want.
Unless wine programs are inside a gtk widget.(The Metacity module can generate a preview of a window that is a gtk container)


Otherwise there is no good solution because some metacity themes use images for a lot of stuff and there are no colors to get.But you can get the color
the users set in the preferences dialog using the module "gconf".

But even then you probably won't get all the colors specified in 
gtk themes.You will have to parse those to get all the colors.

---

### Post by Endolith on 2008-08-22
> **days_of_ruin said:**
> Unless wine programs are inside a gtk widget.(The Metacity module can generate a preview of a window that is a gtk container)

I don't know what you mean, but I don't think it's applicable to what I'm doing.  I need to know the border and title bar colors purely so that I can color Wine windows inside a Wine virtual desktop.  I am reading the colors from metacity windows and applying them to Wine windows so the theme matches.

> Otherwise there is no good solution because some metacity themes use images for a lot of stuff and there are no colors to get.

Ok, that makes it a lot easier.  :)  I will just do what Clearlooks does and it will be good enough to match the theme while not being exactly the same.  The title bar gradient is horizontal while the gradient in most themes is vertical anyway.  Close enough.  :)

> But you can get the color
the users set in the preferences dialog using the module "gconf".

I tried that, but the keys aren't always there.

> But even then you probably won't get all the colors specified in 
gtk themes.You will have to parse those to get all the colors.

I already did most of that.  Current script is here: [http://www.endolith.com/wordpress/wp-content/uploads/2008/08/wine_colors_from_gnome.py](http://www.endolith.com/wordpress/wp-content/uploads/2008/08/wine_colors_from_gnome.py)

---

### Post by Endolith on 2008-09-04
Alright, I'm looking at this again and I still can't $#@&$*#&$* figure it out.  [gtk.RcStyle Class Reference]("http://www.pygtk.org/docs/pygtk/class-gtkrcstyle.html") says:
> PRELIGHT
	A color used for widgets in the gtk.STATE_PRELIGHT state. **This state is** the **used for** gtk.Button and **gtk.MenuItem widgets that have the mouse cursor over them**, and for their children.

In Raleigh, I can use menuitem.style.bg[gtk.STATE_PRELIGHT] to read the menu hover background color, and it matches what I actually see (#EAEAEA), so this would seem to be correct.

In Human, though, it's completely different.  The menu hover highlight is yellowish orange, while menuitem.style.bg[gtk.STATE_PRELIGHT] gives me #F3F0ED, almost white.

**Why is the style object giving me the wrong color??**

In the Human gtkrc file, there's a bit like this:

```
style "ubuntulooks-menu-item" = "ubuntulooks-default"
{
	xthickness     = 2
	ythickness     = 3
**	bg[SELECTED]   = @selected_bg_color**
	fg[PRELIGHT]   = @selected_fg_color
	text[PRELIGHT] = @text_color
}
```

That's not bg PRELIGHT, as specified in the docs, but changing the bg[SELECTED] line changes the hover color, so that must be it, right?  "menuitem.style.bg[gtk.STATE_SELECTED]" returns #FFD799, and this is much closer to the actual highlight color.

(In the top of the gtkrc file, there's "selected_bg_color:#FFD799", which is where it comes from, I guess.)

But if I try to use this bg SELECTED value to get the color for Raleigh, it gives me a blue, which is not correct.

How do I get the *actual* color being used by a widget?  Not the GTK color it's theoretically supposed to us, but the color that GTK actually uses to draw it.

---

### Post by Endolith on 2009-03-05
The script works [pretty well for most themes]("http://www.endolith.com/wordpress/2008/08/03/wine-colors/"), but I've since learned that getting it perfect for all themes would require writing a separate scraper for each engine, since they can basically use the GTK colors however they want.

I've also found out that CSS2 defines a number of [system colors]("http://www.iangraham.org/books/xhtml1/appd/update-23feb2000.html") that coincide with the colors used in Windows/Wine.  So whatever web browsers like Firefox/Epiphany use for finding out these colors could be applied to Wine, too (or vice versa).   However, the colors I have seen them render are not so good.  :)

---

### Post by Can+~ on 2009-03-05
> **Endolith said:**
> The script works [pretty well for most themes]("http://www.endolith.com/wordpress/2008/08/03/wine-colors/"), but I've since learned that getting it perfect for all themes would require writing a separate scraper for each engine, since they can basically use the GTK colors however they want.

I've also found out that CSS2 defines a number of [system colors]("http://www.iangraham.org/books/xhtml1/appd/update-23feb2000.html") that coincide with the colors used in Windows/Wine.  So whatever web browsers like Firefox/Epiphany use for finding out these colors could be applied to Wine, too (or vice versa).   However, the colors I have seen them render are not so good.  :)

Great research, I'll try your script later.

---

### Post by Mr..Yeti on 2009-03-05
A little bit of self promotion here :D
I recently made my own script for gtk colour manipulations with python, to work with my new project [SledgeMan]("http://www.launchpad.net/sledgeman") see Sig.

It takes colour settings from gconf, but only when the theme has a colour-scheme. In practice this works for most themes, but the occasional theme crashes the program :D 

Some other features of the script include:
Getting the theme name and path. So it would be possible to parse the gtkrc file directly.
Converting hex strings to other formats.
Converting rgba values in the range 0-1, into hex strings.
And a pretty poor hex colour shifter.

I can't help but feel python can already do most of this, but it's still fun to reinvent wheels.

[Colour.py]("http://bazaar.launchpad.net/~robin-groves/sledgeman/settingsFramework/annotate/head%3A/colour.py")

---

### Post by Can+~ on 2009-03-05
> **Mr..Yeti said:**
> [Colour.py]("http://bazaar.launchpad.net/~robin-groves/sledgeman/settingsFramework/annotate/head%3A/colour.py")

I've been reading the code for a while, and I think this is one of those moments where a class suits perfectly, there's plenty of room for setters and getters.

---

### Post by Endolith on 2009-03-11
Indeed, I have found someone else with the same problem... the Mozilla developers!  It appears that these are scraped by nsLookAndFeel.cpp, which exists separately for each toolkit (mac, gtk2, qt)  They have tons of comments in their code explaining that they're not sure what they're doing, just like mine.  :)

```
    // It's really hard to effectively map these to the Appearance Manager properly,
    // since they are modeled word for word after the win32 system colors and don't have any 
    // real counterparts in the Mac world. I'm sure we'll be tweaking these for 
    // years to come. 
...
        // NOTE: this is an MDI color and does not exist on macOS.
        //used the closest match, which will likely be white.

```The gtk2 file uses statements like this:

[php]    case eColor_highlight:
        // background of selected item
        aColor = GDK_COLOR_TO_NS_RGB(mStyle->base[GTK_STATE_SELECTED]);
        break;[/php] Whereas the qt version does things like this:

[php]    case eColor_highlight:
      aColor = QCOLOR_TO_NS_RGB(activeGroup.highlight());
      break;[/php]This seems pretty similar to what I'm doing.   They also create an invisible widget to get the style from:

[php] mWidget = gtk_invisible_new();
        gtk_object_ref(GTK_OBJECT(mWidget));
        gtk_object_sink(GTK_OBJECT(mWidget));
        gtk_widget_ensure_style(mWidget);
        mStyle = gtk_widget_get_style(mWidget);[/php]The reason some of their colors don't match, like the desktop color, is because they aren't really trying too hard.  They just get a color from GTK instead of trying to figure out what Gnome or Xfce specifies for the desktop color:

[php]    case eColor_background:
        // desktop background
        aColor = GDK_COLOR_TO_NS_RGB(mStyle->bg[GTK_STATE_NORMAL]);
        break;
[/php]I tried the test page with Epiphany-WebKit for comparison, and they don't even try.  The colors are hardcoded and nothing changes if I change the theme.

---

### Post by ls-h on 2009-04-07
> **days_of_ruin said:**
> The metacity module is used for metacity theme previewing.............
How can I use it for theme previewing? 
Where I can find docs about it?

Thanks

**update**

I've found
:)

---

### Post by Flimm on 2009-04-17
> **ls-h said:**
> How can I use it for theme previewing? 
Where I can find docs about it?

Thanks

**update**

I've found
:)
Could you share the link to the metacity module docs? I can't seem to find them.

---

