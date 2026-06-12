---
title: "Gnome Panel Applets in Python"
date: 2007-07-08
forum: Programming Talk
---

### Post by zanelightning on 2007-07-08
Hi, I'd like to get started in writing my own applet for the gnome-panel in python, but I really have no idea where to begin (or to finish, for that matter). I've searched for tutorials and references, but they seem obfuscated, deprecated, or unfinished. I believe the most recent I could find was from 2004, and its code is outdated (uses gnome.applet instead of gnomeapplet for instance). 

I am completely new to coding for gnome, so I don't have a solid idea of what to do, basically I'm starting from square one. So, my question is if anyone would be willing to help me start (first by writing a basic applet, maybe a hello world) and/or help me with the api and/or point me to a tutorial or how-to that is up-to-date that I can use for this purpose.

For me, at this point, I think simplicity is paramount! :)

---

### Post by Quikee on 2007-07-09
I will try to help when I get back from work. 

You could look into a working program like "ubuntu system panel" or "gimmie" how they add themselves to the panel.

---

### Post by Quikee on 2007-07-09
OK.. I have looked into how this works and this example came out:

gnomeAppletExample.py
```

#!/usr/bin/env python

import pygtk
import sys
pygtk.require('2.0')

import gnomeapplet
import gtk

def factory(applet, iid):
	button = gtk.Button()
	button.set_relief(gtk.RELIEF_NONE)
	button.set_label("ExampleButton")
	button.connect("button_press_event", showMenu, applet)
	applet.add(button)
	applet.show_all()
	return True

def showMenu(widget, event, applet):
	if event.type == gtk.gdk.BUTTON_PRESS and event.button == 3:
		widget.emit_stop_by_name("button_press_event")
		create_menu(applet)

def create_menu(applet):
	propxml="""
			<popup name="button3">
			<menuitem name="Item 3" verb="About" label="_About" pixtype="stock" pixname="gtk-about"/>
			</popup>"""
	verbs = [("About", showAboutDialog)]
	applet.setup_menu(propxml, verbs, None)

def showAboutDialog(*arguments, **keywords):
	pass

if len(sys.argv) == 2:
	if sys.argv[1] == "run-in-window":
		mainWindow = gtk.Window(gtk.WINDOW_TOPLEVEL)
		mainWindow.set_title("Ubuntu System Panel")
		mainWindow.connect("destroy", gtk.main_quit)
		applet = gnomeapplet.Applet()
		factory(applet, None)
		applet.reparent(mainWindow)
		mainWindow.show_all()
		gtk.main()
		sys.exit()

if __name__ == '__main__':
	print "Starting factory"
	gnomeapplet.bonobo_factory("OAFIID:Gnome_Panel_Example_Factory", gnomeapplet.Applet.__gtype__, "Simple gnome applet example", "1.0", factory)

```

You also have to define a .server file which you have to put into "/usr/lib/bonobo/servers".
gnomeAppletExample.server
```

<oaf_info>

	<oaf_server iid="OAFIID:Gnome_Panel_Example_Factory" type="exe" location="/home/quikee/projects/examples/python/various/gnomeAppletExample.py">
		<oaf_attribute name="repo_ids" type="stringv">
			<item value="IDL:Bonobo/GenericFactory:1.0"/>
			<item value="IDL:Bonobo/Unknown:1.0"/>
		</oaf_attribute>
		<oaf_attribute name="name" type="string" value="Gnome Applet Example"/>
		<oaf_attribute name="description" type="string" value="Simple gnome applet example"/>
	</oaf_server>

	<oaf_server iid="OAFIID:Gnome_Panel_Example" type="factory" location="OAFIID:Gnome_Panel_Example_Factory">
		<oaf_attribute name="repo_ids" type="stringv">
			<item value="IDL:GNOME/Vertigo/PanelAppletShell:1.0"/>
			<item value="IDL:Bonobo/Control:1.0"/>
			<item value="IDL:Bonobo/Unknown:1.0"/>
		</oaf_attribute>
		<oaf_attribute name="name" type="string" value="Example"/>
		<oaf_attribute name="description" type="string" value="Simple gnome applet example"/>
		<oaf_attribute name="panel:category" type="string" value="Utility"/>
		<oaf_attribute name="panel:icon" type="string" value="computer.png"/>
	</oaf_server>

</oaf_info>

```

You have to define the exact path to the executable. Maybe it also works if you only define the executable name and the executable is in path but I haven't checked this. The executable must have +x rights. 

In this file you also define how to represent the program in "Add to panel" dialog (you define name, description, icon).

I hope it helps...

---

### Post by zanelightning on 2007-07-10
Quikee, thanks for the fast and helpful response, I've got my applet going now...I should be able to take it from here since it seems that applets are only slightly different from regular gnome apps, and there are tons of good pygtk references out there.

My question now is, is it:
  a) possible to create a gradient in gtk instead of resorting to create gradient images
  b) possible to set this gradient (or an image/pixmap) as the background to an element (I want to have a gradient behind a Label, so I would likely have to attach this to an EventBox or something similar)

---

### Post by zanelightning on 2007-07-17
Those previous questions are still unanswered for me, and I have another one. I am now using threading to update information from the internet so I can maintain a responsive GUI while the applet is searching. When I run the applet in a window from the command line, everything works perfectly. When I add the applet to the panel for the first time, it works perfectly also, but when I remove it and try to add it again, it stalls and throws an error, unable to attach to the panel. I then have to reboot, and it's able to be added one time, etc.

My hunch was that this had to do with the thread never being killed and thus interfering with a new instance of the applet, so I modified the updater to run once and kill the thread. Sure enough, I was then able to remove it and add it again, with it completely functional. So, my question is how I would resolve this issue; is there a function that gets called automatically on removal of the applet that I could use to kill the update thread?

---

### Post by zecarioca on 2008-01-18
That code was really helpful... Thanks a lot! But now I need to ask this... There's anyway for me to use a .directory file on that xml? I'm trying to create an apple that have a popup menu like the applications menu.

---

### Post by Quikee on 2008-01-21
As far as I know you can't use ".directory" files in this way. You have to create the pop-up menu yourself and use something like "python gmenu" or python-xdg (both work but python-xdg is more DE neutral) to parse *.desktop, *.directory and *.menu information. 



About left button click, the following should work fine:

[PHP]
def showMenu(widget, event, applet):
    if event.button == 1:
        print "do something on button 1"
        widget.emit_stop_by_name("button_press_event")
[/PHP]

To help you out a little.. with the code below you can create a menu on the fly:

[PHP]
def createAndShowMenu(event, menuItems):
	menu = gtk.Menu()
	for menuItem in menuItems:
		item = gtk.MenuItem(menuItem[0], True)
		item.show()
		item.connect( "activate", *menuItem[1:])
		menu.add(item)
	menu.popup( None, None, None, event.button, event.time )
[/PHP]

And use it like this to create a menu with elements: "first", "second", "third" in the "showMenu" method:

[PHP]

def doFirst(widget, additionalParameter):
    print "do first"
def doSecond(widget):
    print "do second"
def doThird(widget):
    print "do third"

def showMenu(widget, event, applet):
    if event.button == 1:
        menu = [
            ["first", doFirst, "AdditionalParameterIfYouNeedIt"],
            ["second", doSecond],
            ["third", doThird]]
        createAndShowMenu(event, menu)
        widget.emit_stop_by_name("button_press_event")
[/PHP]

NOTE! I have not checked any of this.. errors in the code are possible.

---

### Post by zecarioca on 2008-01-22
Thanks a lot, but I'v tried "if event.button == 1:" it simple wont work!
iv tried
```

def showMenu(widget, event, applet):
        global num
        widget.emit_stop_by_name("button_press_event")
        propxml="""
                        <popup name="button3">
                        <menuitem name="Item 3" verb="About" label="_About" pixtype="stock" pixname="gtk-about"/>
                        <menuitem name="file-unlock"    verb="file-unlock"      label="Unlock File"             pixtype="stock" pixname="revelation-unlock" />
                        <menuitem name="file-lock"      verb="file-lock"        label="Lock File"               pixtype="stock" pixname="revelation-lock" />
                        <menuitem name="file-reload"    verb="file-reload"      label="Reload File"             pixtype="stock" pixname="revelation-reload" />
                        <separator />
                        <menuitem name="revelation"     verb="revelation"       label="Start Revelation"        pixtype="stock" pixname="revelation-revelation" />
                        <menuitem name="prefs"          verb="prefs"            label="Preferences"             pixtype="stock" pixname="gtk-properties" />
                        <menuitem name="about"          verb="about"            label="About"                   pixtype="stock" pixname="gnome-stock-about" />
                        </popup>"""

        verbs = [("About", showAboutDialog)]
        applet.setup_menu(propxml, verbs, None)


```

and

```

def showMenu(widget, event, applet):
        global num
        if event.button == 1:
                propxml="""
                                <popup name="button3">
                                <menuitem name="Item 3" verb="About" label="_About" pixtype="stock" pixname="gtk-about"/>
                                <menuitem name="file-unlock"    verb="file-unlock"      label="Unlock File"             pixtype="stock" pixname="revelation-unlock" />
                                <menuitem name="file-lock"      verb="file-lock"        label="Lock File"               pixtype="stock" pixname="revelation-lock" />
                                <menuitem name="file-reload"    verb="file-reload"      label="Reload File"             pixtype="stock" pixname="revelation-reload" />
                                <separator />
                                <menuitem name="revelation"     verb="revelation"       label="Start Revelation"        pixtype="stock" pixname="revelation-revelation" />
                                <menuitem name="prefs"          verb="prefs"            label="Preferences"             pixtype="stock" pixname="gtk-properties" />
                                <menuitem name="about"          verb="about"            label="About"                   pixtype="stock" pixname="gnome-stock-about" />
                                </popup>"""

                verbs = [("About", showAboutDialog)]
                applet.setup_menu(propxml, verbs, None)
                (... other part of the code... )
        
                widget.emit_stop_by_name("button_press_event")

```

It simple wont pop with the left mouse button!
Any idea where im wrong?

---

### Post by zecarioca on 2008-01-22
Oh, and as you can notice I'm really trying this based on your code :)
thanks

---

### Post by zecarioca on 2008-01-22
Doing the menu on the fly works ( not really the way I want, but pops when I click with the left button ), but when I try applet.setup_menu(..) it wont work with the left mouse button... :(

---

### Post by Quikee on 2008-01-22
I think the problem is in the xml.. change the <popup name="button3"> to <popup name="button1"> and try if it works. If this doesn't work I would need to look into the documentation :)

---

### Post by zecarioca on 2008-01-22
Iv changed it but still nothing... When the server comes online again here I will make sure that there was no other mistakes and post all the code of the applet and the server here with some commentary 2 :)

---

### Post by Quikee on 2008-01-22
As far as I can see now this xml is something gnome applet uses for its general menu (If you right click on several applets you will see that they are quite similar) and is only meant to be used for right click.

---

### Post by zecarioca on 2008-01-23
dang... The problem of using the menu on the fly is that it appears where the user clicks, I will have to figure out latter how to put it like a toolbar menu... welll, here is the code

```


#!/usr/bin/env python

import commands
import pygtk
import sys
pygtk.require('2.0')

import gnomeapplet
import gtk

num = 0
button = gtk.Button()

def factory(applet, iid):
        global button
#       button = gtk.Button()

        button.set_relief(gtk.RELIEF_NONE)
        button.set_label("")
        image = gtk.Image()
        image.set_from_file("/usr/share/icons/gnome/48x48/devices/gnome-dev-floppy-red.png")
        button.set_image(image)
        button.connect("button_press_event", showMenu, applet)
#       button.connect("clicked", on_button_clicked)
        applet.add(button)
        applet.show_all()
        return True

def on_button_clicked(button, *args):
#       button.emit_stop_by_name("button_press_event")
#       create_menu(applet)
        global num
        if (num%2==0):
                image = gtk.Image()
                image.set_from_file("/usr/share/icons/gnome/48x48/devices/gnome-dev-floppy-red.png")
                button.set_image(image)
                button.set_label("")
        else:
                image = gtk.Image()
                image.set_from_file("/usr/share/icons/gnome/48x48/devices/gnome-dev-floppy-green.png")
                button.set_image(image)
                button.set_label("")
        num=num+1

def showMenu(widget, event, applet):
    if event.button == 1:
        global num
        if (num%2==0):
#               image = gtk.Image()
#               image.set_from_file("/usr/share/icons/gnome/48x48/devices/gnome-dev-floppy-red.png")
#               widget.set_image(image)
#               widget.set_label("")
                menu = [
                        ["Ativar Disquete", doFirst],
                        ["Formatar Disquete", doSecond]]
        else:
#               image = gtk.Image()
#               image.set_from_file("/usr/share/icons/gnome/48x48/devices/gnome-dev-floppy-green.png")
#               widget.set_image(image)
#               widget.set_label("")
                menu = [
                        ["Desativar Disquete", doFirst],
                        ["Acessar o Disquete", doSecond]]
#       num=num+1
        createAndShowMenu(event, menu)
        propxml="""
                        <popup name="button1">
                        <menuitem name="Item 1" verb="About" label="_About" pixtype="stock" pixname="gtk-about"/>
                        <menuitem name="file-unlock"    verb="file-unlock"      label="Unlock File"             pixtype="stock" pixname="revelation-unlock" />
                        <menuitem name="file-lock"      verb="file-lock"        label="Lock File"               pixtype="stock" pixname="revelation-lock" />
                        <menuitem name="file-reload"    verb="file-reload"      label="Reload File"             pixtype="stock" pixname="revelation-reload" />
                        <separator />
                        <menuitem name="revelation"     verb="revelation"       label="Start Revelation"        pixtype="stock" pixname="revelation-revelation" />
                        <menuitem name="prefs"          verb="prefs"            label="Preferences"             pixtype="stock" pixname="gtk-properties" />
                        <menuitem name="about"          verb="about"            label="About"                   pixtype="stock" pixname="gnome-stock-about" />
                        </popup>"""
        verbs = [("About", showAboutDialog)]
        applet.setup_menu(propxml, verbs, None)
        widget.emit_stop_by_name("button_press_event")

def doFirst(widget):
    global button
    global num
    num=num+1
    if (num%2==0):
        image = gtk.Image()
        image.set_from_file("/usr/share/icons/gnome/48x48/devices/gnome-dev-floppy-red.png")
        button.set_image(image)
        button.set_label("")
        commands.getstatusoutput("zenity --info --title='Disquete' --text='Disquete desativado. Pode remove-lo do computador agora.'")
    else:
        image = gtk.Image()
        image.set_from_file("/usr/share/icons/gnome/48x48/devices/gnome-dev-floppy-green.png")
        button.set_image(image)
        button.set_label("")
        commands.getstatusoutput("zenity --info --title='Disquete' --text='Disquete ativado. Pronto para uso! (ou nao)'")

def doSecond(widget):
    print "do second"
def doThird(widget):
    print "do third"

def createAndShowMenu(event, menuItems):
    menu = gtk.Menu()
    for menuItem in menuItems:
        item = gtk.ImageMenuItem(menuItem[0], True)
        item.show()
        item.connect( "activate", *menuItem[1:])
        menu.add(item)
    menu.popup( None, None, None, event.button, event.time )


def create_menu(applet):
        propxml="""
                        <popup name="button3">
                        <menuitem name="Item 3" verb="About" label="_About" pixtype="stock" pixname="gtk-about"/>
                        <menuitem name="file-unlock"    verb="file-unlock"      label="Unlock File"             pixtype="stock" pixname="revelation-unlock" />
                        <menuitem name="file-lock"      verb="file-lock"        label="Lock File"               pixtype="stock" pixname="revelation-lock" />
                        <menuitem name="file-reload"    verb="file-reload"      label="Reload File"             pixtype="stock" pixname="revelation-reload" />
                        <separator />
                        <menuitem name="revelation"     verb="revelation"       label="Start Revelation"        pixtype="stock" pixname="revelation-revelation" />
                        <menuitem name="prefs"          verb="prefs"            label="Preferences"             pixtype="stock" pixname="gtk-properties" />
                        <menuitem name="about"          verb="about"            label="About"                   pixtype="stock" pixname="gnome-stock-about" />
                        </popup>"""
        verbs = [("About", showAboutDialog)]
        applet.setup_menu(propxml, verbs, None)

def showAboutDialog(*arguments, **keywords):
        pass

if len(sys.argv) == 2:
        if sys.argv[1] == "run-in-window":
                mainWindow = gtk.Window(gtk.WINDOW_TOPLEVEL)
                mainWindow.set_title("Ubuntu System Panel")
                mainWindow.connect("destroy", gtk.main_quit)
                applet = gnomeapplet.Applet()
                factory(applet, None)
                applet.reparent(mainWindow)
                mainWindow.show_all()
                gtk.main()
                sys.exit()

if __name__ == '__main__':
        print "Starting factory"
        gnomeapplet.bonobo_factory("OAFIID:Gnome_Panel_Example_Factory", gnomeapplet.Applet.__gtype__, "Simple gnome applet example", "1.0", factory)


```

---

### Post by zecarioca on 2008-01-23
and the server file

```


<oaf_info>

	<oaf_server iid="OAFIID:Gnome_Panel_Example_Factory" type="exe" location="/usr/lib/gnome-panel/gnomeAppletExample.py">
		<oaf_attribute name="repo_ids" type="stringv">
			<item value="IDL:Bonobo/GenericFactory:1.0"/>
			<item value="IDL:Bonobo/Unknown:1.0"/>
		</oaf_attribute>
		<oaf_attribute name="name" type="string" value="Gnome Applet Example"/>
		<oaf_attribute name="description" type="string" value="Simple gnome applet example"/>
	</oaf_server>

	<oaf_server iid="OAFIID:Gnome_Panel_Example" type="factory" location="OAFIID:Gnome_Panel_Example_Factory">
		<oaf_attribute name="repo_ids" type="stringv">
			<item value="IDL:GNOME/Vertigo/PanelAppletShell:1.0"/>
			<item value="IDL:Bonobo/Control:1.0"/>
			<item value="IDL:Bonobo/Unknown:1.0"/>
		</oaf_attribute>
		<oaf_attribute name="name" type="string" value="Example"/>
		<oaf_attribute name="description" type="string" value="Simple gnome applet example"/>
		<oaf_attribute name="panel:category" type="string" value="Utility"/>
		<oaf_attribute name="panel:icon" type="string" value="computer.png"/>
	</oaf_server>

</oaf_info>


```

---

### Post by solarwind on 2008-02-25
Thanks, this thread really helped!

---

### Post by Cherry Cotton on 2008-05-15
Yep, this thread helped me, too.

By the way, I had problems loading the applet before I realized I needed to make the Python script executable ("chmod +x gnomeAppletExample.py"). After you do that, and you have the server file in its proper directory (edited to reflect the absolute path of wherever you saved the Python script), you can load the example applet from the right-click menu ("Add to Panel...").

(Edit: Ooops, you already mentioned this. Yeah, I'm silly...)

---

### Post by solarwind on 2008-05-15
> **Cherry Cotton said:**
> Yep, this thread helped me, too.

By the way, I had problems loading the applet before I realized I needed to make the Python script executable ("chmod +x gnomeAppletExample.py"). After you do that, and you have the server file in its proper directory (edited to reflect the absolute path of wherever you saved the Python script), you can load the example applet from the right-click menu ("Add to Panel...").

(Edit: Ooops, you already mentioned this. Yeah, I'm silly...)

I learned that if you don't need to make an applet - don't. You can make a tray icon and make a program that runs in many window managers and not just the one you made the applet for.

---

### Post by say2sky on 2008-06-08
I hope to find a way to have a cron event to run system health check, if something wrong, a gnome-panel applet is activated and show an icon/letter/word on gnome-panel. 

Is this possible by changing the example code here? Anyone is willing give a help. Thank a lot for help.

---

### Post by solarwind on 2008-06-08
> **say2sky said:**
> I hope to find a way to have a cron event to run system health check, if something wrong, a gnome-panel applet is activated and show an icon/letter/word on gnome-panel. 

Is this possible by changing the example code here? Anyone is willing give a help. Thank a lot for help.

You can do it in a way that works in any desktop environment. Look at my ggmail gmail checker. It changes the icon in the system tray if you have new messaes. You can EASILY change the code so it will do your task instead of check for messages. It's also not gnome-dependant meaning it should work on any desktop environment/window manager with a system tray, including gnome.

Just modify the gobject timer to suit your desired time interval and change some other code around. It's a very simple project so you shouldn't have too much trouble with it.

[http://www.blog.solarwind.metafy.org/category/ggmail/](http://www.blog.solarwind.metafy.org/category/ggmail/)

---

### Post by say2sky on 2008-06-08
> **solarwind said:**
> You can do it in a way that works in any desktop environment. Look at my ggmail gmail checker. It changes the icon in the system tray if you have new messaes. You can EASILY change the code so it will do your task instead of check for messages. It's also not gnome-dependant meaning it should work on any desktop environment/window manager with a system tray, including gnome.

Just modify the gobject timer to suit your desired time interval and change some other code around. It's a very simple project so you shouldn't have too much trouble with it.

[http://www.blog.solarwind.metafy.org/category/ggmail/](http://www.blog.solarwind.metafy.org/category/ggmail/)

That's a very good info and I have already download your ggmail. I hope I can understand your code and then make the necessary modification for my need. 

If I meet obstacle later, I will ask your help again. Thank you very much for help.

---

### Post by solarwind on 2008-06-09
> **say2sky said:**
> That's a very good info and I have already download your ggmail. I hope I can understand your code and then make the necessary modification for my need. 

If I meet obstacle later, I will ask your help again. Thank you very much for help.

I just realized I said gnome-dependent. I meant gnome-***_in_***dependent.

---

### Post by nylz on 2013-01-14
> **zecarioca said:**
> dang... 

**Thank You very very very much!** I've been searching for this solution for a very long time!!!
:KS

---

### Post by howefield on 2013-01-14
Old thread closed.

---

