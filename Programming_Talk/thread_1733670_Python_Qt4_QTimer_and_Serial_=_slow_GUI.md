---
title: "Python Qt4: QTimer and Serial = slow GUI ?"
date: 2011-04-19
forum: Programming Talk
---

### Post by Garyu on 2011-04-19
I am writing a small piece of software that listens to a serial port and saves communication, if certain requirements of filtering etc are met. I expect to receive serial communication maximum ten times per second. So I'm using a QTimer to read from the serial port every 100 ms, but only save information if there is incoming traffic. But when using this QTimer, the GUI becomes very laggy, if I write text in a line edit it waits for about one second and then prints everything I've written for the past second, then stalls again and then prints everything I've written for the past second, etc.

The code for the QTimer looks something like this:
```

self.cron = QtCore.QTimer()
QtCore.QObject.connect(self.cron, QtCore.SIGNAL('timeout()'), self.listen)
self.cron.start(100)

def listen(self):

	try:
		myline = self.ser.readline()
	except serial.SerialException:
		pass
	else:
		if myline:
			...do something...

```
If I comment that code out, it runs perfectly smooth. I also have another QTimer set to one hour triggers, and that does not affect GUI speed. Setting the start(100) to start(1000) does not improve GUI speed. So I'm thinking it's the combination of QTimer and pyserial that makes the GUI laggy.

What to do about this?

[http://eli.thegreenplace.net/2009/08/07/a-live-data-monitor-with-python-pyqt-and-pyserial/](http://eli.thegreenplace.net/2009/08/07/a-live-data-monitor-with-python-pyqt-and-pyserial/)
I was looking at this example where they use threading. But I don't really understand how threading works and what the difference to QTimer would be. I'm a Python newbie, and I would prefer to work with things I understand, like QTimer which is simple.

My aim is to get this running smooth on 4 COM-ports on the same computer. Which I have already done from a command-line interface, it's the Qt4 implementation that makes things start to go slow.

---

### Post by Garyu on 2011-04-23
I managed to solve it myself. It had nothing to do with the QTimer.

Pyserial was set to load with a 1 second timeout, which was default in some example I was looking at. So then it sat there waiting one second for input, which locked the GUI. Setting the timeout to 0.01 seconds means that there is no lag at all. Problem solved. :)

---

