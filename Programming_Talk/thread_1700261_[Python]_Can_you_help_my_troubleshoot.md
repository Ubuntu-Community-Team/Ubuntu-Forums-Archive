---
title: "[Python] Can you help my troubleshoot"
date: 2011-03-04
forum: Programming Talk
---

### Post by ki4jgt on 2011-03-04
```

#!/usr/bin/env python
# Mercy Web Browser is a spin off of Virgil's Web Browser.
# (http://tinyurl.com/4a7ch2w) It's original
# code has allowed the creation of this great program.
# Updates to this may be found at http://www.smashindex.org
# Known bugs: Trying to open a new browser window from the GUI, is not possible
# Requires gtk and webkit.
import gtk
import webkit

sit = ['http://www.google.com']
sindex = 0

# Create main window and it's properties.
window = gtk.Window()
window.set_title("SmashIndex")
window.resize(640, 480)
window.connect("destroy", gtk.main_quit)
window.set_icon_from_file("favicon.ico")

# Create the widgets.
m = gtk.MenuItem("|\/|")
m.set_submenu(m)

back = gtk.Button(" < ")
forward = gtk.Button(" > ")

address = gtk.Entry()

progress = gtk.ProgressBar()
progress.set_text("Loading. . .")

browser = webkit.WebView()

scroll = gtk.ScrolledWindow()
scroll.add(browser)

# Load a default page. This can be changed.
DEFAULT_URL = 'http://www.google.com'
url = DEFAULT_URL
browser.open(url)

# Define the horizontal widgets.
toolbar = gtk.HBox()
toolbar.pack_start(m, False)
toolbar.pack_start(back, False)
toolbar.pack_start(forward, False)
toolbar.pack_start(address)

# Define the vertical widgets.
display = gtk.VBox()
display.pack_start(toolbar, False)
display.pack_start(scroll)
display.pack_start(progress, False)

# Function to load a page on key press.
def backclicked(btn):
    global sindex
    sindex = sindex - 1
    if sindex < 0:
        sindex = 0
    browser.open(sit[sindex])
back.connect("clicked", backclicked)

def forwardclicked(btn):
    global sindex
    sindex = sindex + 1
    if sindex > len(sit) - 1:
        sindex = len(sit) - 1
    browser.open(sit[sindex])
forward.connect("clicked", forwardclicked)

def loadpagekey(key):
    site = address.get_text()
    if site.find(" ") != -1 or site.find(".") == -1:
        site.replace(" ", "+")
        site = "http://duckduckgo.com/?q=" + site
    elif site.find("://") == -1:
        site = "http://" + site
    browser.open(site)
    global sindex
    sindex = sindex + 1
    sit.append(site)
    if sit[sindex] != sit[len(sit) - 1]:
        del sit[sindex + 1:]
address.connect("activate", loadpagekey)

# Funtion to define the progress bar.
def load_progress_changed(webview, amount):
    progress.set_fraction(amount / 100.0)
browser.connect("load-progress-changed", load_progress_changed)

# Function to show the progress bar during page load.
def load_started(webview, frame):
    progress.set_visible(True)
browser.connect("load-started", load_started)

# Function to hide the progress bar when load is finished.
def load_finished(webview, frame):
    progress.set_visible(False)
    address.set_text(frame.get_uri())
browser.connect("load_finished", load_finished)

# Show the widgets
window.add(display)
window.show_all()

# Start the program
gtk.main()

```

OK, so the back button is working great. (I know the only thing in the list is what's typed into the browser and not what the user clicks on - going to do that later) The only problem is, if I go to [www.apple.com](www.apple.com)
then to [www.punk.com](www.punk.com)
then go back to [www.apple.com](www.apple.com)
enter [www.msn.com](www.msn.com)
then go back to [www.apple.com](www.apple.com)
then go forward
and instead of landing on MSN.com, I land on [www.punk.com&#8253;](www.punk.com&#8253;) I have no idea how to fix it??? Thanks for your support.

---

### Post by cgroza on 2011-03-04
Try printing the lists and deduce what is happening. You index gets messed up somehow, a little of logic should sole that.

---

### Post by Shpongle on 2011-03-04
edit , my bad . I misread what you were trying to do.

---

### Post by ki4jgt on 2011-03-04
> **cgroza said:**
> Try printing the lists and deduce what is happening. You index gets messed up somehow, a little of logic should sole that.

I've been trying that all day LOL I've made sindex -1 I've taken google out of the sit list. I've done a lot LOL. I'll keep trying though.

---

### Post by LemursDontExist on 2011-03-05
I find this code very confusing:

```
sit.append(site)
if sit[sindex] != sit[len(sit) - 1]:
    del sit[sindex + 1:]
```

You append the page you're currently at to the end of the list - and then erase it if the site at your current index in the list doesn't match the last one.  While I have trouble mentally following what happens in your example case, that can't be right.  Maybe you want something like:

```
if site != sit[sindex]:
    del sit[sindex:]
    sit.append(site)
```

If the site is already the right site, then you shouldn't need to append anything to the list, or change anything at all, I would think - but if the current site doesn't match the expected site, then I assume you want to clear the remainder of the list and set a new last entry?  Anyway, just a guess!

---

### Post by ki4jgt on 2011-03-05
> **LemursDontExist said:**
> I find this code very confusing:

```
sit.append(site)
if sit[sindex] != sit[len(sit) - 1]:
    del sit[sindex + 1:]
```

You append the page you're currently at to the end of the list - and then erase it if the site at your current index in the list doesn't match the last one.  While I have trouble mentally following what happens in your example case, that can't be right.  Maybe you want something like:

```
if site != sit[sindex]
    del sit[sindex:]
    sit.append(site)
```

If the site is already the right site, then you shouldn't need to append anything to the list, or change anything at all, I would think - but if the current site doesn't match the expected site, then I assume you want to clear the remainder of the list and set a new last entry?  Anyway, just a guess!

Thank you very much!! LOL, I've been going at that all day! Then I found out Webkit has this neat little feature Webkit.WebBackForwardList Ahhhhhh!!!!!!!!!!!! I had been using IDLE and every time those little popups would come up, IDLE would just disappear for no reason at all. I lost I don't know how much code due to that. Now, I'm using SPE and saw the little list. Now I'm just ready to pull my hair out :-(:confused::confused::confused: Anyway, I'm searching Google on how to use WebBackForwardList

---

### Post by LemursDontExist on 2011-03-05
As a side note, you might really want to think about subclassing gtk.Window to avoid putting all these variables in the global name space.  9 times out of 10 if you find yourself using the 'global' you're doing something wrong.

Something simple like

```
class MyWindow(gtk.Window):
    def __init__(self):
        super(MyWindow, self).__init__()
        self.sindex = 0
        self.sit = ['http://www.google.com']
        # make all your child widgets in here
```

would really tidy up your code.

Then, the only code you really need to run in the global name space is:

```
if __name__ == "__main__":
    window = MyWindow()
    window.show_all()
    gtk.main()
```

The if-check is just good style to allow you to import the module and work with the pieces without causing the browser to run if you want to.

Anyway, for a project of any real magnitude, you'll be grateful in the long run for keeping your namespaces clean.

---

### Post by ki4jgt on 2011-03-05
> **LemursDontExist said:**
> As a side note, you might really want to think about subclassing gtk.Window to avoid putting all these variables in the global name space.  9 times out of 10 if you find yourself using the 'global' you're doing something wrong.

Something simple like

```
class MyWindow(gtk.Window):
    def __init__(self):
        super(MyWindow, self).__init__()
        self.sindex = 0
        self.sit = ['http://www.google.com']
        # make all your child widgets in here
```

would really tidy up your code.

Then, the only code you really need to run in the global name space is:

```
if __name__ == "__main__":
    window = MyWindow()
    window.show_all()
    gtk.main()
```

The if-check is just good style to allow you to import the module and work with the pieces without causing the browser to run if you want to.

Anyway, for a project of any real magnitude, you'll be grateful in the long run for keeping your namespaces clean.

Thanks, I'm just starting in Python. I watched a lot of TheNewBoston.com's python section last week and decided to throw myself into it. I just came from JustBASIC, a very Windows style programming language. It was great, until I wanted to make advanced programs which started calling on Windows DLLs which WINE didn't seem to have.

---

### Post by nvteighen on 2011-03-05
What I would have done is something more graphical and more practical: stacks.

I'd have defined a "Past" list, a "Future" list and a variable pointing to the "Present" URL. So when a new webpage is loaded, the previous URL is placed in the "Past" list. If the Back button is hit, the following would occur:

```

Future.append(Present)
Present = Past.pop() # Assuming the last element is the newest
# Load Present

```

And when the forward button is hit:
```

Past.append(Present)
Present = Future.pop()
# Load Present

```

Also, Future should be reset if a URL is typed in. Here a callback for the URL bar's "changed" event can be handy.

As you see, such a thing avoids dealing with indices... it makes it quite obvious and much simpler... and less error-prone, I'm sure.

Now, what I also suggest you is to split the code into what defines the GUI and what defines browsing behaivor. Sometimes it's very useful to split both things into two different classes, as it allows you to change your globals with class data members (which will act like globals but with some good restrictions) that are accessed by the methods defined in your class. I'm sorry, but there's almost no way to do decent GUI programming without resorting to OOP, so if you haven't learned how it works, do it now.

---

### Post by cgroza on 2011-03-05
Do yourself a favor, spare 30 minutes to do it inside a class, after that, it simplifies things a lot.

---

### Post by ki4jgt on 2011-03-05
Just watched the Class video (Skipped ahead a few lessons). I'm so used to working with global variables :-( I don't know if I'll ever like this class thing at all, but I can try it.

---

### Post by cgroza on 2011-03-05
> **ki4jgt said:**
> Just watched the Class video (Skipped ahead a few lessons). I'm so used to working with global variables :-( I don't know if I'll ever like this class thing at all, but I can try it.
To get a variable global in a class, you just to make it "selfish" as I call it :D:D, by naming you identifier with a "self." prefix. Much better and gives you the advantage of having an object instead of a bunch of functions.

---

### Post by LemursDontExist on 2011-03-05
I'm not a big fan of object oriented programming myself.  I think, for instance, that Java's insistence on *everything* being in a class is arbitrary and counterproductive.  That said, for a project of any magnitude, they're very useful, and even for a small project, restricted namespaces will help you a lot in debugging.  

If you're in a global scope and you have a bug, you have to worry that every other line of code might be somehow causing the bug.  With a restricted namespace, you know that only a handful of lines of code can have any impact.  Debugging makes up 90%+ of what a programmer does, and making debugging fast and easy is worth a lot.

As for classes, lets suppose that at some later date you decide you want tabbed browsing in your browser.  If you're using global variables, the current system will totally break with multiple tabs with their own histories - if instead all of that information is stored in a class, you just need to create a new instance of the class and it will have it's own copy of the relevant data structures!

It seems like extra work for no good reason at first, but after a while, you'll wonder that you ever programmed another way.

---

