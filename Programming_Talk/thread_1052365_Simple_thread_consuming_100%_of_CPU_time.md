---
title: "Simple thread consuming 100% of CPU time"
date: 2009-01-27
forum: Programming Talk
---

### Post by crashsystems on 2009-01-27
Just yesterday I started learning about threading in Python. In an attempt to test out what I've been reading, I created a simple little pyGTK/Glade app that starts a thread when a button is clicked. I was having some problems with that, so I posted a question on [StackOverflow]("http://stackoverflow.com/questions/482263/beginner-level-python-threading-problems").

I didn't get much help over there, so I decided to post over here. At the moment I'm able to start a thread, but that thread is consuming 100% of my program's CPU time. If someone could take a look at it, it would be greatly appreciated. You can view the code below, or you can download a tarball of the code, glade file, etc (see attachment). I've been using bzr to track the changes to the code, so if you download the tarball you'll get all the advantages of that awesome version control system.

Note: I'm a big fan of line numbers, which the forums here do not seem to support. If you want to reference line numbers in your reply, I've pasted the code at [http://dpaste.com/hold/113653/]("http://dpaste.com/hold/113653/")

```

#!/usr/bin/env python

# about stuff
import gtk, threading

class ThreadGUI:

    # Define signals
    def on_btnStartStop_clicked(self, widget, data=None):
        print "btnStartStop clicked"
        print "self.threadStop == " + str(self.threadStop)
        if(self.threadStop == 0):
            self.threadFile = open("output.txt", 'w')
            self.thread = threading.Thread(target=self.threadLoop)
            self.thread.run()
            print self.thread
        else:
            self.threadStop = 0
            self.thread.stop()
            print self.thread
            self.threadFile.close()
            # Now we must remake the thread, else thee will be hell to pay!
            del self.thread
            self.thread = threading.Thread(target=self.threadLoop)
            print self.threadCounter
        print "threadStop = " + str(self.threadStop)

    def on_btnMessageBox_clicked(self, widget, data=None):
        print "btnMessageBox clicked"
        self.lblMessage.set_text("This is a message!")
        self.msgBox.show()

    def on_btnExit_clicked(self, widget, data=None):
        print "btnExit clicked"
        self.exit()

    def on_btnOk_clicked(self, widget, data=None):
        print "btnOk clicked"
        self.msgBox.hide()

    def on_mainWindow_destroy(self, widget, data=None):
        print "mainWindow destroyed!"
        self.exit()

    def exit(self):
        print "exit() called"
        self.threadStop = 1
        gtk.main_quit()

    def threadLoop(self):
        while(self.threadStop != 1):
            self.threadFile.write(str(self.threadCounter) + '\n')
            self.threadCounter += 1

    def __init__(self):
        # Connect to the xml GUI file
        builder = gtk.Builder()
        builder.add_from_file("threadgui.xml")

        # Connect to GUI widgets
        self.mainWindow = builder.get_object("mainWindow")
        self.txtThreadView = builder.get_object("txtThreadView")
        self.btnStartStop = builder.get_object("btnStartStop")
        self.msgBox = builder.get_object("msgBox")
        self.btnMessageBox = builder.get_object("btnMessageBox")
        self.btnExit = builder.get_object("btnExit")
        self.lblMessage  = builder.get_object("lblMessage")
        self.btnOk = builder.get_object("btnOk")

        # Connect the signals
        builder.connect_signals(self)

        self.threadStop = 0
        self.threadCounter = 0

        # I'll use this file for testing output from the thread
        self.threadFile = None

if __name__ == "__main__":
    # Start GUI instance
    GUI = ThreadGUI()
    GUI.mainWindow.show()
    gtk.main()

```

---

### Post by Paul Miller on 2009-01-28
Just put time.sleep (0.001) at the end of your infinite while loop that's running in a separate thread.  This will cause your program to yield back to the OS.

---

### Post by crashsystems on 2009-01-28
> **Paul Miller said:**
> Just put time.sleep (0.001) at the end of your infinite while loop that's running in a separate thread.  This will cause your program to yield back to the OS.

I put time.sleep in that loop as you suggested, but the results are still the same. The one difference is that the number getting written to the text file does not increment as quickly.

---

### Post by crashsystems on 2009-01-28
A reply on [StackOverflow]("http://stackoverflow.com/questions/482263/beginner-level-python-threading-problems#487110") helped me figure out a fix. Basically, I just turned the thread into a daemon via .setDaemon(True), therefore putting the thread into it's own process space, leaving my little GUI at peace. To shut the daemon thread down, I just use a class level variable to signal the completion of the loop.

You can go to [http://drop.io/n0upemm]("http://drop.io/n0upemm") if you want to see the final code.

---

