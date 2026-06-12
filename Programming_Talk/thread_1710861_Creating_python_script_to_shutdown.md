---
title: "Creating python script to shutdown"
date: 2011-03-20
forum: Programming Talk
---

### Post by rabbitdaone on 2011-03-20
Is it possible to have a python script monitor a set of downloads, and shutdown the system once they are finished?

I would be using "Transmission BitTorrent Client" for the downloads. 

Thanks for taking the time to read and reply.

---

### Post by cgroza on 2011-03-20
Transmission allows you to execute a script whdn the downoads are finished,you just need a way to shut down the thing. A os.system can do it but it requires a password for sudo.

---

### Post by rabbitdaone on 2011-03-20
@cgroza
Thanks for your reply; is it possible then to run the script as root to prevent needing the password a second time?

---

### Post by Alan D on 2011-03-20
I made one of these. Basically the best thing to do is assign the script ownership to root, but allow other to execute it. make sure anyone/other cannot write to the file however.

---

### Post by rabbitdaone on 2011-03-20
> **Alan D said:**
> I made one of these. Basically the best thing to do is assign the script ownership to root, but allow other to execute it. make sure anyone/other cannot write to the file however.

Thanks for your suggestion Alan D. Would you mind if I saw your code? 
I am teaching myself python and I believe that would be of great assistance to me and anyone else who reads this thread.

---

### Post by Alan D on 2011-03-21
Sure, give me a bit to find it, It was a while back.

---

### Post by rabbitdaone on 2011-03-22
@Alan D
That would be appreciated. 

To anyone else reading, any assistance with creating this script is appreciated.

---

### Post by rabbitdaone on 2011-03-22
bump

---

### Post by Alan D on 2011-03-23
> **rabbitdaone said:**
> bump


Whoops. Forgot about it. One sec.


```

#!/usr/bin/env python
import os, gtk

class Shutdowndialog:
    def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_decorated(False) # no close/minimize in the corner
        self.window.set_default_size(-1,-1)
        self.window.set_position(gtk.WIN_POS_CENTER)
        self.box = gtk.HButtonBox()
        # create three buttons
        self.shutbutt = gtk.Button("Shut Down")
        self.restbutt = gtk.Button("Restart")
        self.canbutt = gtk.Button("Cancel")
        # give them actions and add them into the button box
        self.box.add(self.shutbutt)
        self.shutbutt.connect("clicked", self.on_shutdown)
        self.shutbutt.show()
        self.box.add(self.restbutt)
        self.restbutt.connect("clicked", self.on_restart)
        self.restbutt.show()
        self.box.add(self.canbutt)
        self.canbutt.connect("clicked", self.on_destroy)
        self.canbutt.show()
        # we need to add the box to the window
        self.window.add(self.box)
        # and show the box in the window and tell the window to draw its contents
        self.box.show()
        self.window.show()
    # these define what the buttons do
    def on_destroy(self, widget, data=None):
        gtk.main_quit() # kill the window
        
    def on_shutdown(self, widget, data=None):
        os.system("gksudo shutdown now -h")
        
    def on_restart(self, widget, data=None):
        os.system("gksudo reboot now")
        
    def main(self):
        gtk.main() 

if __name__ == "__main__":
    displaywindow = Shutdowndialog() # create the window
    displaywindow.main() # pass control to our dialog

```

You wont need the gksudo when root owns it. I have those so you can easily and safely test/modify it. It can reside, owned by root, in your home folder. Use a PYTHONPATH var in .bashrc that points at /home/scripts or where ever. 

I am sure it could be simplified and cleaned up, but it did the trick for me. I hope it is helpful to you.

---

### Post by rabbitdaone on 2011-03-23
> **Alan D said:**
> Whoops. Forgot about it. One sec.


```

#!/usr/bin/env python
import os, gtk

class Shutdowndialog:
    def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_decorated(False) # no close/minimize in the corner
        self.window.set_default_size(-1,-1)
        self.window.set_position(gtk.WIN_POS_CENTER)
        self.box = gtk.HButtonBox()
        # create three buttons
        self.shutbutt = gtk.Button("Shut Down")
        self.restbutt = gtk.Button("Restart")
        self.canbutt = gtk.Button("Cancel")
        # give them actions and add them into the button box
        self.box.add(self.shutbutt)
        self.shutbutt.connect("clicked", self.on_shutdown)
        self.shutbutt.show()
        self.box.add(self.restbutt)
        self.restbutt.connect("clicked", self.on_restart)
        self.restbutt.show()
        self.box.add(self.canbutt)
        self.canbutt.connect("clicked", self.on_destroy)
        self.canbutt.show()
        # we need to add the box to the window
        self.window.add(self.box)
        # and show the box in the window and tell the window to draw its contents
        self.box.show()
        self.window.show()
    # these define what the buttons do
    def on_destroy(self, widget, data=None):
        gtk.main_quit() # kill the window
        
    def on_shutdown(self, widget, data=None):
        os.system("gksudo shutdown now -h")
        
    def on_restart(self, widget, data=None):
        os.system("gksudo reboot now")
        
    def main(self):
        gtk.main() 

if __name__ == "__main__":
    displaywindow = Shutdowndialog() # create the window
    displaywindow.main() # pass control to our dialog

```You wont need the gksudo when root owns it. I have those so you can easily and safely test/modify it. It can reside, owned by root, in your home folder. Use a PYTHONPATH var in .bashrc that points at /home/scripts or where ever. 

I am sure it could be simplified and cleaned up, but it did the trick for me. I hope it is helpful to you.

@Alan D, thanks for the reply friend. Just a few questions:

You said "Use a PYTHONPATH var in .bashrc that points at /home/scripts or where ever".
Whats .bashrc? 

And where in this code would I enter the parameters to monitor the downloads? 
Or maybe im not sure what exactly this is doing, would you elaborate please?

---

### Post by Alan D on 2011-03-23
Oh. what? No, sorry. All I have is a shut down script. cgroza mentioned that Transmission will run a script when the downloads are done. This could be that script.

In fact, to simplify, just type this into terminal and save it in a good spot.

gksudo gedit DLshutdown.py


```

#!/usr/bin/env python
import os

if __name__ == "__main__":  
    os.system("shutdown now -h")

```and that should do it. Then show transmission where it is.

---

### Post by rabbitdaone on 2011-03-23
@Alan D, thanks for your reply again.

I understand what that code you just wrote means, do you mind me asking how you know what os.shutdown does? And how did you find out about it?

Was it that you read the documentation?

---

### Post by Alan D on 2011-03-23
> **rabbitdaone said:**
> 
You said "Use a PYTHONPATH var in .bashrc that points at /home/scripts or where ever".
Whats .bashrc? 


.bashrc is a special hidden configuration file in your home folder. It lets you do some nifty tricks and can ease convenience. 

For example the last line of my .bashrc file looks like this. 

export PYTHONPATH="/home/alan/bin"

This lets anything in that directory to be run from anywhere on the machine without bothering to type in paths.

---

### Post by rabbitdaone on 2011-03-23
@[Alan D]("http://ubuntuforums.org/member.php?u=1260756"), Thanks for your reply
So home/alan/bin is where you keep your scripts, that way you can run them from anywhere without changing directory. Correct me if im wrong please.

And how do I get transmission to use the script that is created?

---

### Post by d3v1150m471c on 2011-03-23
if you have the script execute as root then you won't need sudo. ie a snippet added to /etc/rc.local.
OR you could make the script pass sudo via pipe and then remove the read privileges and change the ownership of the script to root with chown and chmod :)

```

#!/bin/bash
echo 'yourpasswordhere' | sudo -S shutdown <other necessary input>

```

---

### Post by rabbitdaone on 2011-03-23
@[d3v1150m471c]("http://ubuntuforums.org/member.php?u=979822"), Thanks fr your reply

Do you know how to point **"transmission bittorrent client"** to the script that is created?

---

### Post by Alan D on 2011-03-23
> **rabbitdaone said:**
> @Alan D, thanks for your reply again.

I understand what that code you just wrote means, do you mind me asking how you know what os.shutdown does? And how did you find out about it?

Was it that you read the documentation?

os.system runs external programs. So in essence, its the same as typing shutdown in the bash terminal. I learned about os.system through the python documentation and online references, and I knew of shutdown through use of the terminal and general ubuntu resources such as this forum. 

Basically that is exactly what transmission will do with your script. 

So you could use something like os.system("firefox"), but if you are a gnome user, there is a better trick. try: 

os.system("xdg-open https://www.google.com") 
or 
os.system("xdg-open ~/Music/mysong.ogg") 

xdg-open is a special application which will open it with the system default application for that type of file(if there is one). You should read up on try/except blocks at [http://docs.python.org/tutorial/errors.html](http://docs.python.org/tutorial/errors.html) which will let you catch errors, such as the aforementioned unknown file type.

---

### Post by Alan D on 2011-03-23
> **rabbitdaone said:**
> @[d3v1150m471c]("http://ubuntuforums.org/member.php?u=979822"), Thanks fr your reply

Do you know how to point **"transmission bittorrent client"** to the script that is created?


Open Transmission and click edit, then preferences. What you are looking for is in the first tab called Torrents and its labeled "Call script when torrent is completed". Check mark that and then click the button on the right, and locate the script. Close preferences and go start your torrent.

---

### Post by rabbitdaone on 2011-03-23
@Alan D, thanks for replying yet again.

I now understand how xdg-open will be used(from what you explained)
but wouldnt making a call to
```

os.system("xdg-open /my/python/file")

```

Just result in it using gedit or geany to open it? Seeing that those programs would be associated with the .py file type.

---

### Post by rabbitdaone on 2011-03-23
> **Alan D said:**
> Open Transmission and click edit, then preferences. What you are looking for is in the first tab called Torrents and its labeled "Call script when torrent is completed". Check mark that and then click the button on the right, and locate the script. Close preferences and go start your torrent.

WAOW, That is embarrassing...I swore I checked that tab 3 times...Thanks again Alan D. 
I believe this thread is now solved, I would not mind continuing the discussion if you dont mind. I am learning alot from you, thanks to all who posted. Your replies are appreciated.

---

### Post by rabbitdaone on 2011-03-23
What if Transmission did not have that option in the tab menu, how would one go about launching a script after a program event?

---

### Post by Alan D on 2011-03-23
> **rabbitdaone said:**
> @Alan D, thanks for replying yet again.

I now understand how xdg-open will be used(from what you explained)
but wouldnt making a call to
```

os.system("xdg-open /my/python/file")

```Just result in it using gedit or geany to open it? Seeing that those programs would be associated with the .py file type.

Whatever the type of file xdg-open is presented with, it will try to associate it with the correct (and primary) application for that type. Its pretty smart. So yeah, "xdg-open coolapp.py" will open it as text with gedit in my case. Use "python myscript.py" to get it to run.

---

### Post by Alan D on 2011-03-23
> **rabbitdaone said:**
> What if Transmission did not have that option in the tab menu, how would one go about launching a script after a program event?


You would probably be better off using bash to do that. Have some bash script start and check routinely for the transmission process, and if it was gone, then it starts a new script. It would perhaps be structured like this. 

script starts transmission
find and record its PID (process id)
check every x minutes to see if the process is gone
if so, fire clean up script or other application. 

Some bash tutorials could help with that. I am not fond of it myself.

---

### Post by rabbitdaone on 2011-03-23
@[Alan D]("http://ubuntuforums.org/member.php?u=1260756")
Thanks again for your reply, and thanks for the direction with my query. If I need further assistance, i'll start a new thread. 

again, thank you.

---

### Post by Alan D on 2011-03-23
> **rabbitdaone said:**
> @[Alan D]("http://ubuntuforums.org/member.php?u=1260756")
Thanks again for your reply, and thanks for the direction with my query. If I need further assistance, i'll start a new thread. 

again, thank you.

You are welcome.

---

