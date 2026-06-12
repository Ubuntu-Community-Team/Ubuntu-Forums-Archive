---
title: "Trouble with python to glade(gui) communication"
date: 2009-02-06
forum: Programming Talk
---

### Post by mhchem on 2009-02-06
Hi, I'm quite inexperienced with programming, but have managed to put together a little program to help crunch some data that I've gathered.  I'm making a GUI out of it, so others can use it, but am having trouble with a few points.  1) I can't get my output to print into a textview window that I've made in Glade. I know it has something to do with buffers, but I don't actually what that means.  I know very little about textview windows and how to get the glade program to communicate properly with the python script, so I have struggled a lot with this.
2) Also, i want my "exit" button to destroy the window, but it never does.  Instead it just greys the window out and I can't access it again.  
3) The little "x" that is also supposed to destroy the window doesn't work either.  

I've included my script below.  Have a look and any suggestions will be much appreciated.  Thanks very much!

#!/usr/bin/python
import gtk, gtk.glade

def done(widget):
    gtk.main_quit()

def presscalc(widget):
    """self.wTree = gtk.glade.XML(MAO_assignV1.glade)
    self.entryForText = self.wTree.get_widget("displayoutput")"""
    
    massAl = 26.9815386
    massO = 15.9994
    massMe = 15.02347
    massTMA = 72.05196

    #Assign mass and control elements
    mass = float(a.get_widget('mass').get_text())
    tolerance = float(a.get_widget('tolerance').get_text())

    #Define number and mass of known fragments
    frag1 = int(a.get_widget('frag1').get_text())
    totalfrag1 = frag1 * massTMA
    
    #begin loops for peak assignment
    #loop once for Al as "x", then again for O as "y", then again for Me as "z"
    for x in range(100):
            trial1 = x * massAl
            for y in range(100):
                trial2 = y * massO
                for z in range(100):
                    trial3 = z * massMe
                    totalmass = totalfrag1 + trial1 + trial2 + trial3
                    if (abs(totalmass - mass) <= tolerance):
                        """self.entryForText.get_buffer().set_text("all my output goes here")"""
                        print('%9.4f: Al %2d, O %2d, Me %2d, TMA %2d' %(totalmass, x, y, z, frag1))

#### might not need on_window1_destroy
#### don't know if i have assiged widgets in python correctly to the name in python



a = gtk.glade.XML('MAO_assignV1.glade')
dic = {'on_calculate_clicked':presscalc, 'on_exit_clicked':done, 'on_window1_destroy':done}
a.signal_autoconnect(dic)

gtk.main()

---

