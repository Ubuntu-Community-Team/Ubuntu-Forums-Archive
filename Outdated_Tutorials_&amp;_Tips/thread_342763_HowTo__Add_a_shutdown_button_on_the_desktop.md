---
title: "HowTo:  Add a shutdown button on the desktop"
date: 2007-01-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Phatfiddler on 2007-01-20
The main problem with adding a shutdown/restart buton to the desktop is that you have to use a sudo command in the launcher that you are using.  Because of this, you have to supply a password, which defeats the purpose of a 1-click button to shutdown.  Using /etc/sudoers and a pyGTK script, we can defeat this and create a true shutdown method.

[CENTER][IMG]http://cutlersoftware.com/images/snapshot10.png[/IMG][/CENTER]

**[SIZE="2"]Info:[/SIZE]**
Tested on (U,K)buntu and Debian (Stable/Testing/Unstable)
BUT - should work on any Linux distro utilizing these packages and sudo.

You need GTK+ libraries, and python2.X.  Also may work on previous versions of Python.

**[SIZE="2"]Step 1:[/SIZE]**
You need to access /etc/sudoers

You can do this by using the visudo command.  You need to do this using sudo or root terminal.  Visudo will alert you if there are errors with your sudoers file after you have modified it.

```
visudo -f /etc/sudoers
```

Under "# Cmnd alias specification", add the following:

```
Cmnd_Alias     SHUTDOWN = /sbin/shutdown
Cmnd_Alias     HALT = /sbin/halt
Cmnd_Alias     REBOOT = /sbin/reboot
```

or

**NOTE:  Some users may need to use the following instead:**

```
Cmnd_Alias     SHUTDOWN = /usr/sbin/shutdown
Cmnd_Alias     HALT = /usr/sbin/halt
Cmnd_Alias     REBOOT = /usr/sbin/reboot
```

This will create the aliases SHUTDOWN, HALT, and REBOOT that we will need for specifying user privelages.

Under "# User privelage specification", add the following:

```
<user>     ALL=NOPASSWD:  SHUTDOWN, HALT, REBOOT
```

<user> = the user that needs the shutdown button on the desktop.  This let's the machine know that when <user> uses sudo to shutdown, halt, or reboot, they will not have to specify a password.

"ALL" specifies that this works on all the machines.  You can put your machine name here if you wish to do so, but it probably makes no difference.

**[SIZE="2"]Step 2:[/SIZE]**
We can create a Launcher on the desktop that shuts the system down when it is clicked, but what if you click it by accident?  That would suck.  To fix this, I made a python script that opens a GTK interface that lets you select what you would like to do - shutdown, restart, or cancel the action.

Use the following python script code and save it as the file "power_options".  Place it somewhere safe and where you can access it.

```
#!/usr/bin/env python

import os
import sys
import pygtk
import gtk

class power:
	
	def restart(self, event):
   	 	command = "sudo shutdown -r now"
   	 	os.system(command)
		
	def shutdown(self, event):
		command = "sudo shutdown -h now"
		os.system(command)
		
	def cancel(self, event):
		import sys
		sys.exit()
		
	def delete_event(self, widget, event, data=None):
        	gtk.main_quit()
        	return False
	
	def __init__(self):
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.set_title("Power Options")
		self.window.connect("delete_event", self.delete_event)
		self.window.set_border_width(10)
		
		self.box1 = gtk.HBox(False, 0)
        	self.window.add(self.box1)
	
		self.button1 = gtk.Button("Restart")
		self.button1.connect("clicked", self.restart)
		self.box1.pack_start(self.button1, True, True, 0)
		
		self.button2 = gtk.Button("Shutdown")
		self.button2.connect("clicked", self.shutdown)
		self.box1.pack_start(self.button2, True, True, 0)
		
		self.button3 = gtk.Button("Cancel")
		self.button3.connect("clicked", self.cancel)
		self.box1.pack_start(self.button3, True, True, 0)
		
                self.window.set_position(gtk.WIN_POS_CENTER)
		self.button1.show()
		self.button2.show()
		self.button3.show()
		self.box1.show()
		self.window.show()
def main():
	gtk.main()
	
if __name__=="__main__":
	pwr = power()
	main()
```

**[SIZE="2"]Step 3:[/SIZE]**
Now we need to make a Launcher on the desktop that initializes the python script.  For the "Command" entry, add:

```
python <location of script here>/power_options
```

Choose the "Application" option for the Launcher.  If you choose to execute the command in a terminal, you will get a terminal box everytime you click the desktop Launcher.

Choose a nifty icon for your new launcher, and click OK.

Double-click your new Launcher, and you should get a pop-up window asking if you would like to shutdown, reboot, or cancel the command.

Enjoy!

---

### Post by capink on 2007-02-06
Thank you for this nice little script. I'm using openox with lxpanel and this script is very handy.
I like your theme. can you post link for it please.

---

### Post by Phatfiddler on 2007-02-07
Glad you found the script useful!  The theme I used comes with Gnome.  It is called Smokey Blue.  I can't remember which icon theme I was using though.

---

### Post by zyg0t3 on 2007-09-14
Hi, I know this is an old thread but if anyone is listening, i can't seem to get it to work correctly. I got the script running and i edited sudoer but when i click on shutdown nothing happens.

I ran the command script in term and i see that its promting for the password so something in sudoer must not have worked properly.

Any help would be appreciated.

---

### Post by capink on 2007-09-14
this is how my sudoers look like. Hope it helps

```
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

user	ALL= NOPASSWD: /usr/sbin/pppd
user	ALL= NOPASSWD: /sbin/shutdown
```

---

### Post by mogie on 2007-11-26
Nice script.

* I just found my bug..

I used "python ~/bin/power_options" in the launch. I need to specify the EXACT location for it to work..
it then should be in this case: python /home/username/bin/power_options

...in case someone is just as clumsy as I am :lolflag:

---

### Post by kaiju on 2008-03-25
thanks for this cute little thing :)
i modified it a bit for use with fluxbox. the logout function needs "session.screen0.allowRemoteActions: true" in ~/.fluxbox/init.

```

#!/usr/bin/env python
# from Phatfiddler@ubuntuforums.org, modified

import os
import sys
import pygtk
import gtk

class power:

	def cancel(self, event):
		import sys
		sys.exit()
		
	def logout(self, event):
		command = "fluxbox-remote exit"
		os.system(command)
		
	def reboot(self, event):
   	 	command = "sudo shutdown -r now"
   	 	os.system(command)
		
	def shutdown(self, event):
		command = "sudo shutdown -h now"
		os.system(command)
		
	def delete_event(self, widget, event, data=None):
        	gtk.main_quit()
        	return False
	
	def __init__(self):
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.set_title("Power Options")
		self.window.connect("delete_event", self.delete_event)
		self.window.set_border_width(2)
		
		self.box1 = gtk.HBox(False, 0)
        	self.window.add(self.box1)
		
		self.button1 = gtk.Button("Cancel")
		self.button1.connect("clicked", self.cancel)
		self.box1.pack_start(self.button1, True, True, 0)
		
		self.button2 = gtk.Button("Logout")
		self.button2.connect("clicked", self.logout)
		self.box1.pack_start(self.button2, True, True, 0)
	
		self.button3 = gtk.Button("Reboot")
		self.button3.connect("clicked", self.reboot)
		self.box1.pack_start(self.button3, True, True, 0)
		
		self.button4 = gtk.Button("Shutdown")
		self.button4.connect("clicked", self.shutdown)
		self.box1.pack_start(self.button4, True, True, 0)
		
                self.window.set_position(gtk.WIN_POS_CENTER)
		self.button1.show()
		self.button2.show()
		self.button3.show()
		self.button4.show()
		self.box1.show()
		self.window.show()
def main():
	gtk.main()
	
if __name__=="__main__":
	pwr = power()
	main()

```

---

### Post by eriqjaffe on 2008-03-25
> **Auston said:**
> great, I was looking for something like this.+1

This is far better than the individual Zenity dialogs I was using before.  ;)

---

### Post by Tux_2008 on 2008-11-30
> **Phatfiddler said:**
> 
We can create a Launcher on the desktop that shuts the system down when it is clicked, but what if you click it by accident?  That would suck.  

How exactly can this be done? I'm looking for it to *restart* immediately as the button is pressed, and I don't feel I need the popup menu.


Thanks for the excellent tutorial!:)

---

### Post by Cptn Toya on 2011-03-10
> **kaiju said:**
> i modified it a bit for use with fluxbox. the logout function needs "session.screen0.allowRemoteActions: true" in ~/.fluxbox/init.

Hi there !

Just a little tweak so that you can use this script either in graphical mod or by specifying a command line argument :

```

if __name__=="__main__":
	pwr = power()

	try:
		if sys.argv[1] in ("-h", "--halt"):
			power.shutdown
		elif sys.argv[1] in ("-r", "--restart"):
			power.restart
		elif sys.argv[1] in ("-l", "--logout"):
			power.logout

	except IndexError:
		main()

```

---

