---
title: "Python/PyGTK - Webkit or MozEmbed?"
date: 2010-01-10
forum: Programming Talk
---

### Post by bsharitt on 2010-01-10
I'm working on a little project, in Python(PyGTK for the GUI). Basically what it is a GUI for concordance/libconcord to program Logitech Harmony remotes. It's similar to the Congruity GUI(which this was originally going to be an addon to until I decided to switch to GTK from wxPython), except I'm integrating the browser part to download the config files to provide a more seamless experiance among a few other UI tweaks. Now the libconcord funtionality is easy because I have the excellent congruity codebase to refer to and I'm familiar enough with PyGTK for my other UI and funtionality tweaks, but I've never dealt with python-gtkmozembed or pywebkitgtk. So far I've been able to find enough code on the internet to get the web view embedded and go to the correct website and they are both fairly similar in that respect, which is why I haven't been able to pick which one to go with.

The problem I've run into is how to download the needed files when I get to them. All of the example browsers don't get to that, so they, and my program just go to a blank page when I get to the file download. This is pretty much the one part I'm missing of my program to bring the two parts together. Until then I've got a bare browser and a GTK rewrite of Congruity. Im pretty much going to choose between WebKit or MozEmbed based on which one I can implement the downloads in first.

Also for bonus points, it might me useful to be able to change the useragent.

---

### Post by NoBugs! on 2010-11-15
They have some documentation on how to get the html content, and set the html content of the browser:
[http://code.google.com/p/pywebkitgtk/wiki/HowDoI](http://code.google.com/p/pywebkitgtk/wiki/HowDoI)
Haven't tried it but it may work.

---

### Post by nvteighen on 2010-11-15
I may be terribly mistaken, but I think the comparison would be WebKit vs. Gecko, not MozEmbed. If I've understood well what MozEmbed is, it seems like the "Embedded IE" you get in Visual Basic: it's an embedded instance of the browser. But, WebKit is actually a HTML rendering engine, as Gecko is Mozilla's.

---

### Post by NoBugs! on 2010-12-26
That HowDoI page says you can define _navigation_requested_cb(view, frame, networkRequest) handler to use your own code to load a page (so you could change useragent, block ads, etc.) However, I tried to add their code to a simple browser example program and it wouldn't even reach the "print 'request to go to...'" line. Has something changed in pywebkitgtk?
```
#!/usr/bin/env python
#
# [SNIPPET_NAME: Webkit Browser]
# [SNIPPET_CATEGORIES: Webkit, PyGTK]
# [SNIPPET_DESCRIPTION: Create a simple browser using the webkit API]
# [SNIPPET_AUTHOR: Andy Breiner <breinera@gmail.com>]
# [SNIPPET_LICENSE: GPL]
# [SNIPPET_DOCS: http://ardoris.wordpress.com/2009/04/26/a-browser-in-14-lines-using-python-and-webkit, http://www.aclevername.com/articles/python-webgui]

import pygtk
pygtk.require('2.0')
import gtk

#you need to import webkit and gobject, gobject is needed for threads
import webkit
import gobject

class WebV(webkit.WebView):
    def _navigation_requested_cb(view, frame, networkRequest):
        # get uri from request object
        uri=networkRequest.get_uri()
        print "request to go to %s" % uri
        # load the page somehow.....
        page=urllib.urlopen(networkRequest.get_uri())
        # load into associated view, passing in uri
        view.load_string(page.read(), "text/html", "iso-8859-15", uri)
        # return 1 to stop any other handlers running
        # eg. the default uri handler...
        return 1


class Browser:
    default_site = "http://search.yahoo.com/"

    def delete_event(self, widget, event, data=None):
        return False

    def destroy(self, widget, data=None):
        gtk.main_quit()

    def __init__(self):
        gobject.threads_init()
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_resizable(True)
        self.window.connect("delete_event", self.delete_event)
        self.window.connect("destroy", self.destroy)

        #webkit.WebView allows us to embed a webkit browser
        #it takes care of going backwards/fowards/reloading
        #it even handles flash
        self.web_view = WebV()
        self.web_view.open(self.default_site)

        toolbar = gtk.Toolbar()

        #create the back button and connect the action to
        #allow us to go backwards using webkit
        self.back_button = gtk.ToolButton(gtk.STOCK_GO_BACK)
        self.back_button.connect("clicked", self.go_back)

        #same idea for forward button
        self.forward_button = gtk.ToolButton(gtk.STOCK_GO_FORWARD)
        self.forward_button.connect("clicked", self.go_forward)

        #again for refresh
        refresh_button = gtk.ToolButton(gtk.STOCK_REFRESH)
        refresh_button.connect("clicked", self.refresh)

        #add the buttons to the toolbar
        toolbar.add(self.back_button)
        toolbar.add(self.forward_button)
        toolbar.add(refresh_button)

        #entry bar for typing in and display URLs, when they type in a site
        #and hit enter the on_active function is called
        self.url_bar = gtk.Entry()
        self.url_bar.connect("activate", self.on_active)

        #anytime a site is loaded the update_buttons will be called
        self.web_view.connect("load_committed", self.update_buttons)

        scroll_window = gtk.ScrolledWindow(None, None)
        scroll_window.add(self.web_view)
        

        vbox = gtk.VBox(False, 0)
        vbox.pack_start(toolbar, False, True, 0)
        vbox.pack_start(self.url_bar, False, True, 0)
        vbox.add(scroll_window)

        self.window.add(vbox)
        self.window.show_all()

    def on_active(self, widge, data=None):
        '''When the user enters an address in the bar, we check to make
           sure they added the http://, if not we add it for them.  Once
           the url is correct, we just ask webkit to open that site.'''
        url = self.url_bar.get_text()
        #try:
        #    url.index("://")
        #except:
        #    url = "http://"+url
        self.url_bar.set_text(url)
        self.web_view.open(url)

    def go_back(self, widget, data=None):
        '''Webkit will remember the links and this will allow us to go
           backwards.'''
        self.web_view.go_back()

    def go_forward(self, widget, data=None):
        '''Webkit will remember the links and this will allow us to go
           forwards.'''
        self.web_view.go_forward()

    def refresh(self, widget, data=None):
        '''Simple makes webkit reload the current back.'''
        self.web_view.reload()

    def update_buttons(self, widget, data=None):
        '''Gets the current url entry and puts that into the url bar.
           It then checks to see if we can go back, if we can it makes the
           back button clickable.  Then it does the same for the foward
           button.'''
        print 'pagechange';
        self.url_bar.set_text( widget.get_main_frame().get_uri() )
        self.back_button.set_sensitive(self.web_view.can_go_back())
        self.forward_button.set_sensitive(self.web_view.can_go_forward())
        

    def main(self):
        gtk.main()

if __name__ == "__main__":
    browser = Browser()
    browser.main()

```

---

### Post by NoBugs! on 2010-12-27
Found solution at the bottom of that page... Subclassing webView like this lets you handle page loading in your code:

```
import urllib
class WebV(webkit.WebView):
    def __init__(self):
        webkit.WebView.__init__(self)
        self.connect("navigation-policy-decision-requested",self._nav_request_policy_decision_cb)
        self.l_uri=None
    def _nav_request_policy_decision_cb(self,view,frame,net_req,nav_act,pol_dec):
        uri=net_req.get_uri()
        if uri==self.l_uri:
            pol_dec.use()
            return True
        if uri.startswith('about:'):
            return False
        self.l_uri=uri
        page=urllib.urlopen(uri)
        data = page.read();
        #change data here
        frame.load_string(data,page.info().gettype(),page.info().getencoding(),page.geturl())
        pol_dec.ignore()
        return True
```

---

