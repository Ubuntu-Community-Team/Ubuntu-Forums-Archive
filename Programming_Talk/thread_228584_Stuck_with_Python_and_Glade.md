---
title: "Stuck with Python and Glade"
date: 2006-08-03
forum: Programming Talk
---

### Post by jethro10 on 2006-08-03
Hi,
I just starting on the Python/Glade train. Now I am a programmer, but getting started with this has been troublesome in the least!

I have a problem where the code below. It is only a fragment and mainly calles a function called parseqif() (it's a quicken export file) but got a strange error when updating a status label.
I added an extra button to experiment, called btnDisplay and when I click it, see btnDisplay_clicked, it opens a new window to display "yo" instead of on the current open window.
I've spent ages trying to figure out how to output back to a label or text box on my window and this is as far as i've got!

can anyone tell me how to reference my currently open window ?
I bet it's all about this 'self' thingy I see everywhere :???: 

Thanks
Jeff


```

# main window class from GladeWrapper ==========================================
class mainWindow(libglade.GladeWrapper):

    # grab widgets from xml ================================================
    def __init__(self, Filename, WindowName):
        libglade.GladeWrapper.__init__(self, Filename, WindowName)

    def menuQuit(self, widget):  # How a basic menu item works - the event the button raises
        gtk.main_quit()

    def btnQuit_clicked(self, widget):  # How a basic button works
        gtk.main_quit()

    def btnRun_clicked(self, widget):
        items = parseQif()
        print repr(items[0])
        outfile = open('outfile.csv','w')
        for item in items[1:]:
            print item.dataString()
            outfile.write(item.dataString()+'\n')
        outfile.close()
    def btnDisplay_clicked(self, widget):
        gtk.glade.XML("quicken.glade").get_widget("label1").set_text("yo")

# start the application ========================================================
mainWindow = mainWindow("quicken.glade", "mainWindow")

gtk.main()
# end of program ===============================================================

```

---

### Post by sapo on 2006-08-03
hum.. did you try?

self.get_widget("label1").set_text("yo")

or maybe:

gtk.get_widget("label1").set_text("yo")

I didnt understand your code but it seens that your class mainWindow is the window you want the texto to be in.. i m at work right now, i ll try to take a better look when i get home.

---

### Post by Daverz on 2006-08-03
I'm not familiar with GladeWrapper, but I'm guessing that you're loading your gladefile twice, the first time when instantiating the GladeWrapper object, and the second time at the top of your btnDisplay__clicked method, which is why you are seeing a second window.  I assume that the GladeWrapper class exposes the XML node tree as an attribute, so you should use that.

---

### Post by jethro10 on 2006-08-04
> **sapo said:**
> hum.. did you try?

self.get_widget("label1").set_text("yo")

or maybe:

gtk.get_widget("label1").set_text("yo")

I didnt understand your code but it seens that your class mainWindow is the window you want the texto to be in.. i m at work right now, i ll try to take a better look when i get home.

thanks, this is likely to be close.
I'll be back if it does not point me in theright direction.
Thanks
Jeff

---

### Post by jethro10 on 2006-08-04
> **Daverz said:**
> I'm not familiar with GladeWrapper, but I'm guessing that you're loading your gladefile twice, the first time when instantiating the GladeWrapper object, and the second time at the top of your btnDisplay__clicked method, which is why you are seeing a second window.  I assume that the GladeWrapper class exposes the XML node tree as an attribute, so you should use that.

this line
gtk.glade.XML("quicken.glade").get_widget("label1").set_text("yo")
loaded the glade wrapper again, I am trying the code from the post above later. Thanks

Jeff

---

