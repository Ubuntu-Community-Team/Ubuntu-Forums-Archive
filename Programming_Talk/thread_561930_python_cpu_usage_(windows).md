---
title: "python cpu usage (windows)"
date: 2007-09-28
forum: Programming Talk
---

### Post by Xcarma on 2007-09-28
Hey

(1st of all... I'm all new to this programming thingie)

I have written a little program on windows to log incomming calls...

Flow
- Call enters
- Solidus Ecare does a DDE execute to my program
- My program opens a webpage that does the actual logging in to a mysql db.
(i can't use a direct connection due to firewalling ****)

```
import win32ui, dde, urllib2, sys, win32api
from pywin.mfc import object

class LogTheCall(object.Object):
	def __init__(self, topicName):
		object.Object.__init__(self, dde.CreateTopic(topicName))

	def Exec(self, customer):
		agent=win32api.GetUserName()
		customer = customer.strip()
		print "You are talking to: ", customer
		if customer != "":
			theurl = 'myurl removed for security reason' % (customer, agent)
			username = 'my username removed for security reason'
			password = 'my password removed for security reason'

			passman = urllib2.HTTPPasswordMgrWithDefaultRealm()
			passman.add_password(None, theurl, username, password)
			authhandler = urllib2.HTTPBasicAuthHandler(passman)
			opener = urllib2.build_opener(authhandler)
			urllib2.install_opener(opener)
			f = urllib2.urlopen('myurl removed for security reason' % (customer, agent))
			print "Call Logged"

server = dde.CreateServer()
server.AddTopic(LogTheCall("LogTheCall"))
server.Create('migration')

while 1:
	win32ui.PumpWaitingMessages(0, -1)

```

But this uses 50% cpu all the time... Is there anything I can do about this?

Thx in advance

Maarten

---

### Post by cwaldbieser on 2007-09-28
Maybe yo could sleep a couple seconds in your while loop (e.g. time.sleep(2))?

---

