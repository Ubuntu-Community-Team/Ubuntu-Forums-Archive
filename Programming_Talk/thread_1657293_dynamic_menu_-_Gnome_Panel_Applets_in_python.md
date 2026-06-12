---
title: "dynamic menu - Gnome Panel Applets in python"
date: 2011-01-01
forum: Programming Talk
---

### Post by volt220 on 2011-01-01
Hi,
I try to create a gnome panel applet that have a dynamic menu. 
On right mouse click I need to create part of the menu on the fly. 
Possible I can create the whole menu again.

So far I haven't find out how to do it.
If I create a complete new menu by my self I will lose the standard options "Remove from panel", "Move", "Lock to panel"

I could use applet.setup_menu(propxml, verbs, None) and create a xml string on fly but there must be some other way to do it??

I'm elaborating with the code in this post 
[http://ubuntuforums.org/showthread.php?t=496185](http://ubuntuforums.org/showthread.php?t=496185)

The applet way "Static"
[PHP]
def showMenu(widget, event, applet):
        global num
        widget.emit_stop_by_name("button_press_event")
        propxml="""
                        <popup name="button3">
                        <menuitem name="Item 3" verb="About" label="_About" pixtype="stock" pixname="gtk-about"/>
                        <menuitem name="revelation"     verb="revelation"       label="Start Revelation"        pixtype="stock" pixname="revelation-revelation" />
                        <menuitem name="prefs"          verb="prefs"            label="Preferences"             pixtype="stock" pixname="gtk-properties" />
                        <menuitem name="about"          verb="about"            label="About"                   pixtype="stock" pixname="gnome-stock-about" />
                        </popup>"""

        verbs = [("About", showAboutDialog)]
        applet.setup_menu(propxml, verbs, None)
[/PHP]By my own "Dynamic"
[PHP]
def createAndShowMenu(event, menuItems):
    menu = gtk.Menu()
    for menuItem in menuItems:
        item = gtk.ImageMenuItem(menuItem[0], True)
        item.show()
        item.connect( "activate", *menuItem[1:])
        menu.add(item)
    menu.popup( None, None, None, event.button, event.time )
[/PHP]I hope that someone knows!

---

