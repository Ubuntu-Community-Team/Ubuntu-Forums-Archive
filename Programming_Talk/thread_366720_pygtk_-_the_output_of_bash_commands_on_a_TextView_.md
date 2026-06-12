---
title: "pygtk - the output of bash commands on a TextView widget"
date: 2007-02-21
forum: Programming Talk
---

### Post by tseliot on 2007-02-21
Hi, I would like to know how I can redirect the output of bash commands (e.g. apt-get install vim-gnome) to a TextView widget using pygtk.

For example if I press a button (see the attached code) I would like to call a few commands in bash (os.popen doesn't seem to handle well commands such as "apt-get install vim-gnome" ) and display their output on the TextView widget.


If this is not possible with a TextView widget I would appreciate any suggestion about an alternative. An explanation about how I could use python-vte in this case would be very welcome.

I have attached the file project.tar.gz which contains the file written in Python (myapp.py) and the .glade file

Thanks in advance.

---

### Post by duff on 2007-02-21
> **tseliot said:**
>  An explanation about how I could use python-vte in this case would be very welcome.

easy.  here's a snippet from a program i wrote a while back.
```

         v = vte.Terminal()
         v.fork_command('bash')
         v.feed_child('ssh %s tail -f %s.o%s \n' % (host,jname,id))
         v.show()
         notebook.append_page(v, tab_label=gtk.Label(nodeid))

```

---

### Post by tseliot on 2007-02-21
Thanks for your reply.

VTE works great now :-D

---

### Post by earobinson on 2007-09-04
any way to get rid of the prompt?

eg ```
v = vte.Terminal()
v.fork_command('bash')
v.feed_child('whoami\n')
v.feed_child('echo test\n')
v.show()
```outputs> whoami
echotest
earobinson@minusone:/media/data/dev/propensity/src/sandbox$ whoami
earobinson
earobinson@minusone:/media/data/dev/propensity/src/sandbox$ echo test
test but I want > earobinson
test

---

### Post by earobinson on 2007-09-04
Ok so I have found another problem

```
#!/usr/bin/env python

import os
import gtk
import vte
import time
from subprocess import Popen, PIPE

def show_callback(terminal):
    terminal.feed_child('cd /\n')
    terminal.feed_child('whoami\n')
    terminal.feed_child('echo test\n')
    for ii in range (10):
        terminal.feed_child('echo ' + str(ii + 1)  + '\n')
        time.sleep(1)

def write(terminal, text):
    x, y = terminal.get_cursor_position()
    terminal.feed(text + '\n', len(text) + 1)

window = gtk.Window()
window.connect('destroy', lambda w: gtk.main_quit())

terminal = vte.Terminal()
terminal.connect("show", show_callback)

child_pid = terminal.fork_command()

#write(terminal, '1234567890')

window.add(terminal)
window.show_all()
gtk.main()

``` dose not count down, instead it waits 10 seconds then prints everything, any way to make it happen in real time?

---

### Post by tseliot on 2007-09-04
Here is the solution to your problem.

create a file named "ear1" and make it look like this:
```
#!/bin/bash

NUM="0"

cd /
whoami
echo test

while [ $NUM -lt 10 ]; do
    echo $[$NUM+1]
    NUM=$[$NUM + 1]
    sleep 1
done
```

type:
```
chmod +x ear1
```

then make your python file look like the following:
```
#!/usr/bin/env python

import os
import gtk
import vte
import time
from subprocess import Popen, PIPE

    
def show_callback(terminal):
    terminal.feed_child('./ear1')

def write(terminal, text):
    x, y = terminal.get_cursor_position()
    terminal.feed(text + '\n', len(text) + 1)

window = gtk.Window()
window.connect('destroy', lambda w: gtk.main_quit())

terminal = vte.Terminal()
terminal.fork_command()
terminal.connect("show", show_callback)



#write(terminal, '1234567890')

window.add(terminal)
window.show_all()
gtk.main()
```

in other words you will have to make it run a bash script

---

### Post by earobinson on 2007-09-04
hum, so there is no way I could have a user inputting commands in one terminal and the results coming out on the other?

UPDATE:
The problem is then I need to know all the commands that I want to run when I launch the terminal, there seems to be no way to make it interactactive(sp) or monitor the success of each command I issue to the terminal is there?

Ex like a gtk.ProgressBar that monitored each command like synaptic does.

Thanks for the feedback :)

---

### Post by tseliot on 2007-09-04
> **earobinson said:**
> hum, so there is no way I could have a user inputting commands in one terminal and the results coming out on the other?

UPDATE:
The problem is then I need to know all the commands that I want to run when I launch the terminal, there seems to be no way to make it interactactive(sp) or monitor the success of each command I issue to the terminal is there?
you can monitor the success of each command by keeping a log and parsing each line you append to the log on the fly.

I'm not sure as to what you mean by interactive.

---

### Post by earobinson on 2007-09-04
I guess the idea in my head was two guis, one that you can type commands into and the other (the terminal) that displays the commands.

maybe this isent possible?

But it seems like I should be able to issue commands to the terminal and get a response from them.

I have made a simple example., What I would like is to push the press me button and then not be able to interact any more until the command has ran to completion.

eventually I would add a gtk.entry and be able to run any command.

I guess what your saying is I should send but the program I want to run and then a output log file to signify that the program is done?

---

### Post by tseliot on 2007-09-04
> **earobinson said:**
> I have made a simple example., What I would like is to push the press me button and then not be able to interact any more until the command has ran to completion.

eventually I would add a gtk.entry and be able to run any command.

I guess what your saying is I should send but the program I want to run and then a output log file to signify that the program is done?

You can gray out the text are when the user can type the command, pass the command to VTE as you know and then look for a certain line (which you will set) in the log.

here is an example from Envy:
```
def log_output(self,term):
        column,row = self.term.get_cursor_position()
        if self.r != row:
            off = row-self.r
            text = self.term.get_text_range(row-off,0,row-1,-1,self.capture_text)
            self.r=row
            text = text.strip()
            if "\n" not in text or text[-1] != "\n":
                text += "\n"
            ##self.logged += text
            self.completetxt.append(text)
            a = self.logged
            error = re.compile('.*ENVY ERROR.*\n')
            success = re.compile('.*ENVY:.*Operation.*Completed.*')
            for line in self.completetxt:#self.logged:
                m1 = error.match(line)
                m2 = success.match(line)
            if m1:
                self.error = 'error'
                sep = ''#write a logfile
                logtext = sep.join(self.completetxt)
                logfile = open(self.logtxtfile, 'w')
                logfile.write(logtext)
                logfile.close()
                self.errorcheck()
            if m2:
                self.error = 'noerror'
                sep = ''#write a logfile
                logtext = sep.join(self.completetxt)
                logfile = open(self.logtxtfile, 'w')
                logfile.write(logtext)
                logfile.close()
                self.errorcheck()
```

in this example the method looks for strings such as "ENVY ERROR" or "ENVY:.*Operation.*Completed" and acts accordingly. For example if self.error == 'noerror' you can trigger a specific action.

You might use strings such as "DONE", etc. so that if you find such a string you can allow the user to type commands again in the text input area.


EDIT: in case you're wonder what self.term is: self.term = vte.Terminal()

---

### Post by earobinson on 2007-09-04
thanks, I have actualy been reading a lot of the ENVY code, I think im going to write my own, and lock on a file so that I can monitor the status.

Thanks for you help you have really cleard a lot of things up for me :)

---

### Post by tseliot on 2007-09-04
Good luck with your project ;)

---

### Post by earobinson on 2007-09-05
Thanks, I have a semi working copy of what I was talking about but for some reason it seems to hang half the time, any ideas?

---

### Post by earobinson on 2007-09-05
Fixed the bug...

Im not sure if you will want to use this for ENVY or not, it seems a bit more straight forward than how ENVY dose things.

Well feel free

---

### Post by tseliot on 2007-09-05
Very nice :-)

Envy's use case is a bit different though. I need to know whether something went wrong in the installation process and show a popup. And I need to keep a log of what happened otherwise I wouldn't be able to see what went wrong.

I'm glad to see that you managed to find a solution which suits your needs.

---

### Post by earobinson on 2007-09-05
I'm pretty sure you could still keep logs (with a bit of adapting), This would also make it easy to track each command you run.

Just throwing it out there for the future.

Once again thanks for the help.

---

