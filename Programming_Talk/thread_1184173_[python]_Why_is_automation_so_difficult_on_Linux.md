---
title: "[python] Why is automation so difficult on Linux?"
date: 2009-06-10
forum: Programming Talk
---

### Post by pokerbirch on 2009-06-10
I'm trying to write myself a small library which will allow me to automate tasks in external windows. I need functions that can: 

* find a window by title or classname
* get a list of all child windows
* reposition a window
* resize a window
* send messages to a window (close, key up/down, mouse move/click, etc)

Under Win32, you can do all these things very easily with a few API calls. Under Linux, it seems to be a major pain in the rear...OR i've not yet found some decent documentation...

I've spent a couple of days playing with xdotool and dogtail but they don't do what i want and i don't particularly want to rely on a 3rd party app. For instance, xdotool can do the window find/reposition/resize stuff but when it comes to mouse and keyboard simulation, it sends it to the whole screen rather than a specific target window. That's no good to me.

I even took a look at the Java Robot class (i'm not a fan of Java) but even that isn't able to target specific windows.

Best i've got so far is using python-xlib but the documentation is very poor and it's taken me all day just to work out how to do this:

[PHP]#!/usr/bin/python

from Xlib import display, protocol, Xatom

class Automate(object):
    """automates window, mouse and keyboard actions"""
    def __init__(self):
        self.display = display.Display()
        self.win_root = self.display.screen().root

    def find_windows(self, win_title = "", win_class = ""):
        """returns a list of window objects that match the search params.
        if no search params are specified, it returns a list of ALL windows"""
        ret = list()
        win_list = self.win_root.query_tree().children # children of Desktop window
        for win in win_list:
            # check if window matches search params
            try:
                if win_title and win_class: # (need to match both params)
                    if win.get_wm_name() == win_title and win.get_wm_class()[0] == win_class:
                        ret.append(win)
                elif win_title: # (match title only)
                    if win.get_wm_name() == win_title:
                        ret.append(win)
                elif win_class: # (match class only)
                    if win.get_wm_class()[0] == win_class:
                        ret.append(win)
            except:
                pass
            # enumerate all windows (parents/children/grandchildren/etc)
            children = win.query_tree().children
            for child in children:
                win_list.append(child)
        # return
        if not ret: ret = win_list # (windows not found)
        return ret


    ### PROTOTYPES ###
    def resize_window(self, window):
        pass

    def reposition_window(self, window):
        pass

    def close_window(self, window):
        pass

    def send_keys(self, window, keys):
        pass

    def send_mouse(self, window, mouse_action):
        """mouse_action = mouse move/button down/button up/etc"""
        pass[/PHP]

I'd appreciate some help from anyone that is familiar with xlib as i'm really struggling with this...

---

### Post by jpkotta on 2009-06-10
> * find a window by title or classname
* get a list of all child windows
* reposition a window
* resize a window
* send messages to a window (close, key up/down, mouse move/click, etc)

All of these things are things that are handled by a window manager.  Some window managers (FVWM) have this functionality built-in, in the sense you can script these actions.  But I'm guessing you want a solution that isn't tied to a particular wm.

You should definitely have a look at xte in the xautomation package, and xprop, which should be installed by default.  If those don't already do what you want, you can probably learn a lot by understanding their source.

Edit: Also try xse (X send event).  This is basically just a wrapper around the XSendEvent() call.

---

### Post by unutbu on 2009-06-10
Perhaps try the wmctrl package (it's in the official repository):
[http://tripie.sweb.cz/utils/wmctrl/](http://tripie.sweb.cz/utils/wmctrl/)

---

### Post by UbuKunubi on 2009-06-11
My weapon of choice for desktop automation is xdotool, very easy to use with python!

Example:
```

def do(dothis):
    cmd = "xdotool "+dothis
    #print cmd
    print
    f=os.popen(cmd)
    f.close()
    cmd=""
    dothis=""

do("mousemove 153 778")
do("click 1")
time.sleep(2)
do("type 'poff internet'")
do("key Return")
#do("type 'pon internet' | key Enter")

```

hope this helps,
Ubu

---

### Post by pokerbirch on 2009-06-12
Thanks for the suggestions. I forgot to mention that i've been using Ubuntu for around a year now, but i'm not very familiar with how the WM works. Fact is, i've never needed to know because it works fine and i'm a strong believer in "if it ain't broke, don't fix it"...so apologies if i ask any dumb questions.

The command line apps you have suggested are useful in their own right, but i'm trying to program a solid library that i can re-use in lots of apps. Shelling off a load of command lines is NOT what i'm aiming for...that is why i've been looking at Xlib. I don't mind using C if necessary, it's just that Python is *easier* and i don't want to re-invent an existing library (if one exists)...

Having done more research, it seems that my best options are to either learn more about Xlib or GTK/GLIB. I've not (yet) done any GUI programming on Linux, so i'd like to get intimate with whichever one of these libraries is most useful. As far as i understand, GTK is simply a "dumbed down" Xlib wrapper? I've looked at the GTK documentation and it looks ideal, however i can't find a way of looping through all the desktop windows. Under Win32, i'd use EnumWindows() and would have finished this project by now...which is why i'm getting frustrated with Linux. :(

The way i've approached my find_window() routine using GTK is like this:
[PHP]import gtk

root = gtk.gdk.screen_get_default().get_root_window()
print "ROOT:", root.xid
children = root.get_children()
for child in children:
    print "    CHILD:", child.xid
[/PHP]
But all it gives me is a couple of child windows. If i then call get_children() on the child windows, they return an empty list. So according to GTK (the way I'VE used it), there are only 3 windows open. The screen i'm looking at right now says otherwise.

Sooooo, what i need is some solid advice from an experienced programmer who's done this kind of thing before. To be honest, i'm very surprised that nobody has ever released a linux library with "simple" API functions. As much as i dislike the whole M$ money wagon, their API system IS a lot easier to work with.

---

### Post by monraaf on 2009-06-12
If you've read the API documentation at [http://www.pygtk.org](http://www.pygtk.org), you would have known that:

> 
The get_children() method returns the list of children gtk.gdk.Window objects of the window. **This method only returns children created via PyGTK**, so for example it's useless when used with the root window; it only returns windows an application created itself.


looks like you'll need to use Xlib.

---

### Post by Reiger on 2009-06-12
GTK isn't a window manager. You are looking for Window Manager functions where there are just a bunch of UI controls (that is what GTK provides, mostly: under the hood there is more but *not* a Window Manager).

... Fortunately the KDE website refers you to standards for WM interoperability... 

See: [http://techbase.kde.org/Projects/KWin](http://techbase.kde.org/Projects/KWin) (Referring page.), and in particular: [http://www.freedesktop.org/wiki/Specifications/wm-spec](http://www.freedesktop.org/wiki/Specifications/wm-spec)

---

### Post by iponeverything on 2009-06-12
> **UbuKunubi said:**
> My weapon of choice for desktop automation is xdotool, very easy to use with python!

Example:
```

def do(dothis):
    cmd = "xdotool "+dothis
    #print cmd
    print
    f=os.popen(cmd)
    f.close()
    cmd=""
    dothis=""

do("mousemove 153 778")
do("click 1")
time.sleep(2)
do("type 'poff internet'")
do("key Return")
#do("type 'pon internet' | key Enter")

```

hope this helps,
Ubu

pretty cool!

---

### Post by pokerbirch on 2009-06-12
Oooops, now i feel like an idiot. :redface:

After a few days of Googling and looking at 100's of pages and different tools, libraries and source codes, my brain is pretty fuzzy. Can't believe i missed that.

I guess Xlib is the way forward. It's a lot more complicated but also a lot more powerful. I might do this in C because there seems to be a lot more documentation and example code.

---

### Post by pokerbirch on 2009-06-12
The problem with XDOTOOL...as stated in my first post...is that the events are global and cannot be targetted at specific windows. I don't want to actually move the mouse around the screen, i want to TELL the window that the mouse has been moved without actually moving it. That is why i'm asking about lower level API's...because i want to interact with the window signals (messages/events/etc). Under Win32, i'd use SendMessage() or PostMessage().

---

### Post by Echhzperienz on 2009-08-17
Pokerbirch, why is dogtail unsuited to your needs (apart from being a 3rd-party package) ?

---

### Post by wmcbrine on 2009-08-17
Automation is anything but difficult in Linux. The problem here is thinking that it makes sense to automate GUI apps. In Windows, almost everything is GUI, so maybe you have no choice. In Linux, there tends to be better separation between the GUI front-ends, and the CLI back-ends that do the real work. So you just call the back-ends directly from a script -- simple.

---

### Post by pelle.k on 2009-08-17
install python-wnck.
[http://library.gnome.org/devel/libwnck/stable/intro.html](http://library.gnome.org/devel/libwnck/stable/intro.html)
[http://rox4debian.berlios.de/0install/Python-Wnck.xml](http://rox4debian.berlios.de/0install/Python-Wnck.xml)

---

### Post by soltanis on 2009-08-18
Yes, I was going to say -- automation in Linux is way easier than in Windows specifically because you aren't clicking stupid buttons, your piping commands in an intuitive/smart way.

On the GUI front, you can either tie yourself to a WM or use XLib and its handy-dandy functions for sending events to windows. Of course that's really hard to work with -- and I don't know of any existing libraries to do it -- but if you're up to it, I'm sure everyone would appreciate it if you took the first step in making this a reality.

---

