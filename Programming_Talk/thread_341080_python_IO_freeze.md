---
title: "python IO freeze"
date: 2007-01-18
forum: Programming Talk
---

### Post by compwiz18 on 2007-01-18
Is there a way to prevent Python from locking up during an I/O event?  I'm using os.popen right now.  It is somewhat annoying the have the interface jam while waiting for dhclient to complete.

Thanks in advance.

---

### Post by gpolo on 2007-01-18
It is all about threading

---

### Post by compwiz18 on 2007-01-18
That was my thought - so I threaded the thing, and it still locks up.  I've got a (threaded) daemon using dbus, and whenever I try and read from the popen stream (which has its own thread), it locks the entire thing up, client, daemon and all.  I'm kinda new to Python, so chances are I'm doing something wrong.  Would you like to see the code?

---

### Post by gpolo on 2007-01-18
what do you mean by "threaded the thing?"

I don't know if you did the right way.. but, did you create a thread class, added something to it and started ? Show me your revelant code

---

### Post by compwiz18 on 2007-01-18
Like I said, I'm new, and probably did something wrong.


the [supposedly] threaded class:
```

	class ConnectThread(threading.Thread):
		IsConnecting = None
		
		def __init__(self,network,wireless,wired,wpa_driver):
			threading.Thread.__init__(self)
			self.network = network
			self.wireless_interface = wireless
			self.wired_interface = wired
			self.wpa_driver = wpa_driver
			self.IsConnecting = False
			
		def run(self):
			self.IsConnecting = True
			network = self.network
			
			#put it down
			print "interface down..."
			misc.Run("ifconfig " + self.wireless_interface + " down")
			#rest of code omitted...

```

the code that launches said class
```

		#triggered by a call via dbus to the daemon
		self.ConnectingThread = self.ConnectThread(network,self.wireless_interface,self.wired_interface,self.wpa_driver)
		self.ConnectingThread.run()
		return True

```

---

### Post by gpolo on 2007-01-18
some points:

first:
self.ConnectingThread = self.ConnectThread(network,self.wireless_interface,self.wired_interface,self.wpa_driver)

I didnt really understood this, did you create a class inside a class ?

second:
You start a thread doing self.ConnectingThread.start() not ConnectingThread.run()

third:
you need to use the method join() before that return, join (in python threads) waits for a run method to terminate.

fourth:
after seeing what you posted, maybe what you really want is to run the process in background

---

### Post by compwiz18 on 2007-01-18
That fixed it, I was doing .run() instead of .start().  Thanks for your help!

---

