---
title: "Help creating an appindicator using subprocess"
date: 2012-12-06
forum: Programming Talk
---

### Post by R2D2! on 2012-12-06
I'm writing an appindicator for [Grive]("https://github.com/Grive/"), a daemon for syncing Google Drive files. Since I have little programming experience, I decided to write a Python script that calls Grive as a subprocess instead of integrating it in its C++ source code.

I've adapted Stefaan Lippens' [code for asynchronously reading subprocess pipes]("http://stefaanlippens.net/python-asynchronous-subprocess-pipe-reading") to both show a notification and change the indicator's icon when something important happens (e.g. a new file is added, or a network error). Notifications work well; however, the indicator's icon changes only when the whole process has finished, which is useless because I need to change it many times after it finishes.

Here is the code I'm using:

async.py

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
import subprocess
import time
import threading
import Queue

class AsynchronousFileReader(threading.Thread):
    '''
    Helper class to implement asynchronous reading of a file
    in a separate thread. Pushes read lines on a queue to
    be consumed in another thread.
    '''

    def __init__(self, fd, queue):
        assert isinstance(queue, Queue.Queue)
        assert callable(fd.readline)
        threading.Thread.__init__(self)
        self._fd = fd
        self._queue = queue

    def run(self):
        '''The body of the tread: read lines and put them on the queue.'''
        for line in iter(self._fd.readline, ''):
            self._queue.put(line)

    def eof(self):
        '''Check whether there is no more content to expect.'''
        return not self.is_alive() and self._queue.empty()

def run(command, show):
    '''
    Main function to consume the output of a command.
    command = The command to be run
    show = Function that will process output
    '''
    # Launch the command as subprocess.
    process = subprocess.Popen(command, shell=True, stdin=None, stdout=subprocess.PIPE, stderr=subprocess.PIPE, close_fds=True)

    # Launch the asynchronous readers of the process' stdout and stderr.
    stdout_queue = Queue.Queue()
    stdout_reader = AsynchronousFileReader(process.stdout, stdout_queue)
    stdout_reader.start()
    stderr_queue = Queue.Queue()
    stderr_reader = AsynchronousFileReader(process.stderr, stderr_queue)
    stderr_reader.start()

    # Check the queues if we received some output (until there is nothing more to get).
    while not stdout_reader.eof() or not stderr_reader.eof():
        # Show what we received from standard output.
        while not stdout_queue.empty():
            line = stdout_queue.get()
            show(line)

        # Show what we received from standard error.
        while not stderr_queue.empty():
            line = stderr_queue.get()
            show(line)

        # Sleep a bit before asking the readers again.
        time.sleep(.1)

    # Let's be tidy and join the threads we've started.
    stdout_reader.join()
    stderr_reader.join()

    # Close subprocess' file descriptors.
    process.stdout.close()
    process.stderr.close()

    return True
```
grive.py

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
import subprocess
import time
import async
from gi.repository import Gtk
from gi.repository import Gio
from gi.repository import GObject
from gi.repository import Notify
from gi.repository import AppIndicator3 as AppIndicator

GRIVE_FOLDER = "/home/ilhuitemoc/Publike/Google Drive"

def show(line):
    line = line.replace("\n", "")
    print line
    if line.startswith("[gr::expt::MsgTag*] = "):
        line = line.replace("[gr::expt::MsgTag*] = ","",1)
        n = Notify.Notification.new("Error", line, icon)
        n.show()
        indicator.set_icon("ubuntuone-client-offline")
    if line.startswith("sync "):
        line = line.replace("sync ","",1)
        line = line.replace('"','<b>',1)
        line = line.replace('"','</b>',1)
        n = Notify.Notification.new("Sync in progress", line, icon)
        n.show()
        indicator.set_icon("ubuntuone-client-updating")
    if "Finished!" in line:
        #n = Notify.Notification.new(line, line, icon)
        #n.show()
        indicator.set_icon("ubuntuone-client-idle")

def openinfolder(obj):
    subprocess.call(["xdg-open",GRIVE_FOLDER])

def openinbrowser(obj):
    subprocess.call(["xdg-open","http://drive.google.com/"])

if __name__ == '__main__':
    indicator = AppIndicator.Indicator.new('grive', 'ubuntuone-client-offline', AppIndicator.IndicatorCategory.APPLICATION_STATUS)
    indicator.set_status(AppIndicator.IndicatorStatus.ACTIVE)
    menu = Gtk.Menu()

    status = Gtk.MenuItem("Connecting...") #Not implemented yet
    status.set_sensitive(False)
    menu.append(status)

    sp = Gtk.SeparatorMenuItem()
    menu.append(sp)

    mi = Gtk.MenuItem("Open Google Drive folder")
    mi.connect('activate',openinfolder)
    menu.append(mi)

    mi = Gtk.MenuItem("Go to Google Drive webpage")
    mi.connect('activate',openinbrowser)
    menu.append(mi)

    sp = Gtk.SeparatorMenuItem()
    menu.append(sp)

    mi = Gtk.ImageMenuItem("Quit")
    img = Gtk.Image.new_from_stock(Gtk.STOCK_QUIT, Gtk.IconSize.MENU)
    mi.set_image(img)
    mi.connect('activate',Gtk.main_quit)
    menu.append(mi)

    menu.show_all()

    indicator.set_menu(menu)

    Notify.init('grive')
    icon = 'google-drive'

    GObject.timeout_add(5*60000, async.run, 'cd "%s" && grive' % GRIVE_FOLDER, show)
    Gtk.main()
```
I think I'm doing something wrong, but it's not obvious to me. Is it right to modify the indicator using a subprocess? Or is any other way I can correctly do this?

---

