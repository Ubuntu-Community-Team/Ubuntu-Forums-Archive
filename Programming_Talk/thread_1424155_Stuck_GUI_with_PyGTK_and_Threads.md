---
title: "Stuck GUI with PyGTK and Threads"
date: 2010-03-07
forum: Programming Talk
---

### Post by sparkus on 2010-03-07
arrgh.

I've been messing around with displaying a serial feed in PyGTK.  For some reason whenever I thread the little bugger the GUI hangs. 

YES, I've read the PyGTK FAQ (most of my code came from it)

Any help would be really appreciated!

```

import threading, thread
import gobject, gtk, time
import serial, csv, eeml

      
def getTime(): #little function that returns local time
        return time.strftime("%H:%M:%S", time.localtime())       
        
class MainWindow(gtk.Window):
   
   #displayText = 
   def __init__(self):
       self.displayText = "program start: " + getTime()
       self.serial = serial.Serial('/dev/ttyUSB0', 9600)
       self.viable = True
       #Window
       super(MainWindow, self).__init__()
       #VBOX
       vb = gtk.VBox()
       self.add(vb)       
       #Scrolling Window
       self.set_size_request(300, 400)
       sw = gtk.ScrolledWindow()
       sw.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)
       sw.set_shadow_type(gtk.SHADOW_ETCHED_OUT)
       sw.set_border_width(10)
       self.textview = gtk.TextView()
       textbuffer = self.textview.get_buffer()
       textbuffer.set_text(self.displayText)
       sw.add(self.textview)
       vb.pack_start(sw)
       #Button for Scrolling Window
       swButton = gtk.Button(stock=gtk.STOCK_OK)
       vb.pack_start(swButton)
       swButton.connect('clicked', self.on_swButton_clicked)
       #show All
       self.show_all()

   def on_swButton_clicked(self, button):
       self.getSerial(button)
   def getSerialThread(self, button):
       threading.Thread(target=getSerial, args=(button,)).start()
   
   def getSerial(self, button):
       while 1: 
         readings = self.serial.readline()#.strip().split(' ') # the readings are separated by space
         
         if (readings.find('%M')!=-1):
             readings = readings.strip().split(' ')
             if (len(readings) == 10):
                self.addTextToWidget(getTime() + ": " + "CO2:" + readings[1] + " Temp:" +readings[2] + " Light:" +readings[3] + " FAN:" +readings[4] + " CO2ON:" + readings[5] + " CO2LOSS:" + readings[6] + " CO2INJ:" + readings[7] + " HighBias:" + str(int(readings[8]) -200) + " LowBias:" + readings[9])
         else: 
             self.addTextToWidget("DEBUG: " + readings.strip())
   def addTextToWidget(self, newText):
          gtk.gdk.threads_enter()
          self.textview.get_buffer().insert(self.textview.get_buffer().get_start_iter(), newText) 
          gtk.gdk.threads_leave()
          
if __name__ == '__main__':
    gobject.threads_init()
    gtk.gdk.threads_init()
    w = MainWindow()
    w.connect("destroy", lambda _: gtk.main_quit())
    gtk.main()

```

---

