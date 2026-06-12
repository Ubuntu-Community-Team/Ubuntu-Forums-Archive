---
title: "help with worlds most annoying bug python GTK"
date: 2011-10-19
forum: Programming Talk
---

### Post by mushy365 on 2011-10-19
i have a scroll window and im trying to get it to auto scroll to the bottom of the page - no matter what i do it only scrolls to the second bottom row, leaving the bottom row not visable until more content is added. 

ive been trying to debug it and found out that when the window populates and it starts changing values it seems to *** 16 every time to the new position start.  so i figured 16 = 1 row so tried to add 16 to the new position  but that didnt work.

i tried to add and subtract 16 from the upper none of them worked, tried to add and subtract 16 from the page size none of them worked. My head is melting here. ill post the code. 

The problem comes in the add_message function thats where it adds to the list store and tries to scroll the window the bottom. 

I added in the prints to see what the values of each of upper, page size and new pos where doing but now matter how i fiddled with them i cant get it to scroll to the bottom. Please help!

```


#!/usr/bin/env python

#imports
import os
import sys
import gtk
import glob
import string
import pygtk
import socket
import shutil
pygtk.require('2.0')


class Base:
    s = None

    def add_message(self,pix,txt):
              
        pos=self.contentwindow.get_vadjustment()
        
        newpos=pos.get_upper()-pos.get_page_size()
        print "upper: "+ str(pos.get_upper())
        print "page size: " + str(pos.get_page_size())
        print "start new pos: " + str(newpos)
        pos.set_value(newpos)
        self.contentwindow.set_vadjustment(pos) 
        self.liststore.append([pix,txt])  

    def connect_to_host(self,widget):
        self.ip = self.connectbariptxtbox.get_text()
        self.port = self.connectbarporttxtbox.get_text()

        self.s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        try:
          self.s.connect((self.ip, int(self.port))) 
          self.add_message(self.successIcon,"Successfully connected to host")
        except:
          self.add_message(self.errorIcon,"Error connection to host: " + self.ip + "on port" + self.port )
    
    def destroy(self,widget,data=None):
        gtk.main_quit()

    def set_images(self):
        self.currentdir = os.getcwd() + "/icons/"
        
        self.incomingIcon = gtk.gdk.pixbuf_new_from_file_at_size(self.currentdir + "recv.png",24,24)
        self.outgoingIcon = gtk.gdk.pixbuf_new_from_file_at_size(self.currentdir + "sent.png",24,24)
        self.errorIcon = gtk.gdk.pixbuf_new_from_file_at_size(self.currentdir + "Error.png",24,24)
        self.successIcon = gtk.gdk.pixbuf_new_from_file_at_size(self.currentdir + "success.png",24,24)

    def __init__(self):
        #lets get a window
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_position(gtk.WIN_POS_CENTER)
        self.window.set_size_request(800,800)
        self.window.set_title("Remote File Downloader")

        #connectbar hbox
        #label ip txtbox label port  button connect
        self.connectbar = gtk.HBox()
        self.connectbar.set_size_request(800,30)
        
        #declare the connectbar widgets
        self.connectbariplabel = gtk.Label(" IP:")
        self.connectbariptxtbox = gtk.Entry()
        self.connectbariptxtbox.set_size_request(500,30)
        self.connectbarportlabel = gtk.Label("Port:")
        self.connectbarporttxtbox = gtk.Entry()
        self.connectbarporttxtbox.set_size_request(60,30)
        self.connectbarconnectbutton = gtk.Button("Connect")
        self.connectbarconnectbutton.connect("clicked",self.connect_to_host)

        #pack them into the bar
        self.connectbar.pack_start(self.connectbariplabel,False,False,5)
        self.connectbar.pack_start(self.connectbariptxtbox,False,False,5)
        self.connectbar.pack_start(self.connectbarportlabel,False,False,5)
        self.connectbar.pack_start(self.connectbarporttxtbox,False,False,5)
        self.connectbar.pack_start(self.connectbarconnectbutton,False,False,5)

        #scroll window hbar treeview and listview need to be declared before this
        self.contenthbar = gtk.HBox() 
        self.contenthbar.set_size_request(800,700)      
        #liststore creation
        self.liststore = gtk.ListStore(gtk.gdk.Pixbuf,str)
        #treeview
        self.treeview = gtk.TreeView(self.liststore)
        #self.treeview.connect("row-activated", self.on_src_activated)
        #self.treeview.set_rules_hint(True)

        #columns and cell rendering
        self.imgrend = gtk.CellRendererPixbuf()
        self.txtrend = gtk.CellRendererText()

        #columns
        self.imgcolumn = gtk.TreeViewColumn(" Action ", self.imgrend, pixbuf = 0)
        self.imgcolumn.set_min_width(70)

        self.txtcolumn = gtk.TreeViewColumn(" Data", self.txtrend, text = 1)
        self.txtcolumn.set_min_width(650)

        ##add columns
        self.treeview.append_column(self.imgcolumn)
        self.treeview.append_column(self.txtcolumn)


        
        self.contentwindow = gtk.ScrolledWindow()
        self.contentwindow.set_shadow_type(gtk.SHADOW_ETCHED_IN)
        self.contentwindow.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)
        self.contentwindow.add(self.treeview)
        
        self.contenthbar.pack_start(self.contentwindow)

        #declare the vertical bar
        self.mainbar = gtk.VBox()
        self.mainbar.pack_start(self.connectbar,False,False,5)
        self.mainbar.pack_start(self.contenthbar,False,False,0)
        
        #other functions to run before displaying window
        self.set_images()
        #self.add_message(self.successIcon,"Its working! Huzzah!!")
        #add to windown and display
        self.window.add(self.mainbar)
        self.window.show_all()
        self.window.connect("destroy",self.destroy)

    def main(self):
        gtk.main()





if __name__ == "__main__":
    base = Base()
    base.main()
```

---

### Post by StephenF on 2011-10-19
self.treeview.scroll_to_cell(len(self.liststore) - 1)

---

