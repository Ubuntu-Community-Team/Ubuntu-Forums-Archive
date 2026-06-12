---
title: "Another Python threading related post"
date: 2008-05-16
forum: Programming Talk
---

### Post by vasquez on 2008-05-16
I've been searching high and low for a way to solve this problem. basically i have to write a small GUI application that does several things.
1. Hook to a DV camera through firewire connection, use dvgrab to get the video and audio feed, pipe it in ffmpeg to do a real-time transconding in FLV format.
2. After CTRL+C to stop the 1st process a thumbnail is created.
3. Connect to a FTP server upload the FLV video and JPEG thumbnail file and add some entries to a MySQL database for easy online publishing.

In general that's about it, the only problem is that instead of sending CTRL+C command in console to stop transcoding i need a STOP button to do that. I used Glad to design a rather small GUI that helps the user to do just that. The only thing i need to do is figure out the threading mechanism and so far i had no success :( The record button works when pressed but hangs the entire GUI (typical :)) Any hints on how can i make all this stuff work together much appreciated!

Here's my code:
```

#!/usr/bin/env python
import sys, os, ftplib, time, datetime, MySQLdb
import gtk.glade
import threading

#---DATE TIME VARS---
TODAY = time.strftime("%m_%d_%y", time.localtime())
TIME_NOW = time.strftime("%H_%M_%S", time.localtime())
#---VARS---
ARRATE = "44100"
ABRATE = "128"
VBRATE = "400"
FPS = "25"
SIZE = "426x350"
FTP="ftp.address.com"
#---PATHS---
DVGRAB = "/usr/bin/dvgrab"
FFMPEG = "/usr/bin/ffmpeg"
#---OUTPUT DIR---
DIR = "/home/client/user-client/videos/"
REMOTE_DIR = "/home/server/www/website/video/"
VID_DIR = DIR+TODAY
FILE = TIME_NOW

class ClientGUI(threading.Thread):
    
    def __init__(self):
        self.wTree = gtk.glade.XML("client_gui.glade", "window1")
        dic={ "on_window1_destroy" : self.quit,
      "on_button1_clicked" : self.record,
      "on_button2_clicked" : self.stop,
        }
        self.wTree.signal_autoconnect(dic)
        return

    def quit(self,obj):
        #Handles the destroy signal of the window.
        gtk.main_quit()
        sys.exit(1)


    def record(self,obj):

            gtk.gdk.threads_enter()
            #Handles the clicked signal of the button.
            #CHECK IF DIRECTORY EXISTS, IF NOT CREATE IT
            if not os.access(VID_DIR, os.F_OK):
                print "Creating directory", VID_DIR
                os.mkdir(VID_DIR)
            print "Dumping"
            PIPE = "%s --format raw -|%s -qmin 1 -qmax 3 -f dv -i - -ar %s -ab %s -acodec mp3 -ac 2 -r %s -f flv -b %s -s %s %s/%s.flv"
            os.system(PIPE % (DVGRAB, FFMPEG, ARRATE, ABRATE, FPS, VBRATE, SIZE, VID_DIR, FILE))
            gtk.gdk.threads_leave()
        
    def stop(self,obj):
        
        #Handles the clicked signal of the button.
        print "Thumbnail creation"
        THUMB = "%s -y -i %s/%s.flv -f mjpeg -ss 00:00:03 -r 1 -vframes 1  -s %s -an %s/%s.jpg"
        os.system(THUMB % (FFMPEG, VID_DIR, FILE, SIZE, VID_DIR, FILE))
        
       
      
if __name__ == '__main__':
    ClientGUI()
    try:
        gtk.gdk.threads_init()
    except:
        print "No threading was enabled when you compiled pyGTK!"
        import sys
        sys.exit(1)
    gtk.gdk.threads_enter()
    gtk.main()
    gtk.gdk.threads_leave()

```

---

