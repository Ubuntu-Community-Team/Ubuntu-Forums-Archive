---
title: "Pygtk and os.system"
date: 2011-03-07
forum: Programming Talk
---

### Post by xpow on 2011-03-07
Hi,

I have the following code:

```

window = gtk.Dialog() 
window.set_size_request(400, 40)
window.set_title("Please wait")
window.show()        
label = gtk.Label()
label.set_text("..waiting...")
label.show()    
window.vbox.pack_start(label, True, True, 0)  
window.set_position(gtk.WIN_POS_CENTER_ALWAYS)
window.set_resizable(False)

os.system("python hello.py")

```

what hello.py does basically communicating with arduino through serial communication; what i want to achieve is that the 'waiting window' open while os.system is called to communicate with arduino

But right now, the 'waiting window' never shows up before os.system, it shows after the os.system is done executed

Could someone help me please?

Thanks

---

### Post by LemursDontExist on 2011-03-07
For gtk windows/widgets to work right you need the gtk main loop to be running.  While it is possible to control the details of main loop execution and insert code into it, your best bet is something like
```
import os
import gtk
import gobject

window = gtk.Dialog() 
window.set_size_request(400, 40)
window.set_title("Please wait")
label = gtk.Label()
label.set_text("..waiting...")
window.vbox.pack_start(label, True, True, 0)  
window.set_position(gtk.WIN_POS_CENTER_ALWAYS)
window.set_resizable(False)
window.connect("destroy", gtk.main_quit)
window.show_all()

gobject.timeout_add(100, os.system, "python hello.py")
gtk.main()
```

(I also added a line to connect the 'destroy' signal so that the program will shut down if you close the waiting window)

On the whole, though, I would actually suggest looking into a simpler gui system such as [Zenity]("http://en.wikipedia.org/wiki/Zenity").  For a quick gui interface to a simple script, gtk is more trouble than it's worth.  If you're comfortable scripting in bash, this would be a very fast script to write in bash with zenity.  If not, zenity does have python bindings.

---

### Post by xpow on 2011-03-07
Thanks for the reply [LemursDontExist]("http://ubuntuforums.org/member.php?u=787249")

Your solution: adding gobject.timeout_add(..), somewhat works

I'll try to look at zenith in the future because the application that i have is done basically but now, the app needs to run on windows as well ... I have couple of question if you dont mind me asking:

```
gobject.timeout_add(100, os.system, "python configuration.pyc /dev/ttyUSB0")
```

1. with code above, is it possible to redirect the output of hello.py to a file? 

2. i use vte, and it works well on linux, but windows doesn't support vte, is there any alternative for it? I need the vte so that i can run 'python conf.py' from it by using the self.fork_command and then based on the output on the vte, i can decide what i need to do, whether to have a pop up dialog, run another script, terminate a process, etc 

3. im asking for question 1, so that maybe i can have another process that monitor the file, then read it frequently and based on that i know what i need to do

Do you have any advice about what i should do?

Thanks

---

### Post by LemursDontExist on 2011-03-07
My old solution is problematic in that the gui will become nonresponsive as long as hello.py runs.  Here's a better solution:


```
import gtk
import gobject
import subprocess

window = gtk.Dialog() 
window.set_size_request(400, 40)
window.set_title("Please wait")
label = gtk.Label()
label.set_text("..waiting...")
window.vbox.pack_start(label, True, True, 0)  
window.set_position(gtk.WIN_POS_CENTER_ALWAYS)
window.set_resizable(False)
window.show_all()
window.connect("destroy", gtk.main_quit)

def do_stuff():
    if p.poll() is None:
        return True
    else:
        # Do whatever you want to do on completion here
        pass

gobject.idle_add(do_stuff)
p = subprocess.Popen(["python", "hello.py"])
gtk.main()
```

The subprocess module creates a new process to run the code for you in the background, freeing up your main processes cycles for responding to gui events.  Again - Zenity presents none of these complexities =P.

If you don't actually need to do anything on completion you can cut out the do_stuff function of course.

---

### Post by LemursDontExist on 2011-03-07
Hi!  I just missed your post before posting my correction.

I'm actually pretty iffy on getting data from a pipe, but if you look at the [documentation]("http://docs.python.org/library/subprocess.html") on the subprocess module, I think you'll find everything you need to get the data out of the pipe.  I haven't actually used this module much myself, but I'm pretty sure it's the right tool for what you're doing.

As for vte...  I *really* don't know anything about vte!  But you might be able to do the things you're talking about using the subprocess module?  It is pretty flexible, and cross platform (mostly?  I think there are minor issues sometimes on windows).

Sorry I can't be more help, and let me know if there's anything else I can help with!

---

### Post by xpow on 2011-03-07
the subprocess works wonder .. 

thanks

---

### Post by Vox754 on 2011-03-08
> **xpow said:**
> the subprocess works wonder .. 

thanks

A system() command, such as those found in C and Python, should never be used, except for the most trivial hacks.

These system() basically only call the underlying shell, so they are not portable at all, and usually don't return anything.

Thankfully, higher level programming languages also provide a way to directly call other programs the correct way, including C popen(), and Python subprocess module.

The short advice is never use system(), if you do, you are probably doing it wrong.

---

