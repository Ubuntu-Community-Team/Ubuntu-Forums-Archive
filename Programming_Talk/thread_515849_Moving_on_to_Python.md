---
title: "Moving on to Python"
date: 2007-08-02
forum: Programming Talk
---

### Post by nesh87 on 2007-08-02
Hey guys,

i think its finally to say goodbye to PHP and start looking at Python. I should say that i have done that once, but shamefully returned back to PHP. Im much more comfortable with PHP and its easy syntax. I decided to give it another try because of a small problem i ran into, that may be solved.. *not sure*. The problem is, since PHP does not support mult-threads, my project cannot be completed. My project was to create an MSN messenger for linux (stupid i know, php isnt the best language for it, but meh). I did use some classes for msn and with GTK. I have logged in successfully from a GTK window, and i can switch to the switchboard, recieve and send messages, but in terminal. I think im starting to fall of track, the point is, do you think Python would be the best language to head into after PHP. And what do you think i should look at first. (I do want to continue my project, but in python)

Thanks,

Mohd.

---

### Post by Ramses de Norre on 2007-08-02
You're project might be quite the same as the emesene project which is a very fine msn client in python (but not wel known yet).
You can find it [here](http://emesene.org/trac/wiki/WikiStart).

---

### Post by bbzbryce on 2007-08-02
> **nesh87 said:**
> The problem is, since PHP does not support mult-threads, my project cannot be completed.

I would definitely suggest doing it in python however you can probably accomplish what you want with php using pcntl-fork ( [http://us2.php.net/manual/en/function.pcntl-fork.php](http://us2.php.net/manual/en/function.pcntl-fork.php) ).

---

### Post by nesh87 on 2007-08-24
hey guys,
i have quit this project so many times but i keep going back. I really need help because im not able to find a solution, or get blocked half way a "solution". I switched to python and im using glade to create my interface. What the msn protocol does is sends information lead by a 3 letter command. To get the users online i would get ILN then the user details. The problem is there is no number specifying the users online so i cant create a loop. I found a solution to that problem or a semi solution since i get my contacts but sometimes missing one or a couple of contacts. My real problem is once i click the button, the program does start the connecting procedures and receives the list. But i cant get the information back, and usually the GUI turns black. Ive read so many tutorials on how to use the threads but cant seem to understand them. Ill attach the two codes if anyone is willing to help?

```

import pygtk
import gtk  
import gtk.glade 
pygtk.require('2.0')
import MSN
import threading

class GUI(threading.Thread):
	def __init__(self):
		threading.Thread.__init__(self)
		self.wTree = gtk.glade.XML("NSN.glade")
		btnLogin = self.wTree.get_widget('btnLogin')
		self.entryEmail = self.wTree.get_widget('entryEmail')
		self.entryPassword = self.wTree.get_widget('entryPassword')
		
		dic = { 
		"on_btnLogin_clicked" : self.btnLoginClicked,
		"gtk_main_quit" : gtk.main_quit
		}

		self.wTree.signal_autoconnect(dic)

	def btnLoginClicked(self,widget):
		self.email = self.entryEmail.get_text()
		self.password = self.entryPassword.get_text()
		msngr = MSN.msn(self.email, self.password)
		msngr.start()
                #according to a tutorial, this would get the list from the other thread, in the other file MSN.py
		uList = Queue.get()
		print "from the main: "+userList


if __name__ == "__main__":
	app = GUI()
	app.start()
	gtk.gdk.threads_init()
	gtk.main()

```

Since the MSN.py is too long to be posted, ive attached.

oh btw, ive always wanted to create my own msn thats why i dont want to give up on this. i hope you guys help
Thanks,

---

### Post by Mirrorball on 2007-08-24
If you want to keep the interface responsive while the program is connecting to MSN, you have to have a thread to connect to MSN and *another thread* to draw the interface.

---

