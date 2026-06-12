---
title: "Python Incompatable Types Problem"
date: 2009-05-03
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-05-03
Ey fellas, having a little bit of trouble again. Here is my code:
```

#!/usr/bin/python

import random, cmath, Queue, copy

global MAXBUFFER
MAXBUFFER = 0

class event(object):
	eventType = None
	eventTime = 0
	srvTime = 0
	DT = 0
	def __init__(self, eventType, eventTime, serviceTime):
		self.eType = eventType
		self.eTime = eventTime
		self.srvTime = serviceTime
	def departure(self, ti):
		self.DT = ti + self.srvTime
		self.eventType = "departure"


class buffer(object):
	buff = Queue.Queue(MAXBUFFER)
	length = buff.qsize()
	def __init__(self):
		buff = Queue.Queue(MAXBUFFER)
	


time = 0
lam = 0.9
transtime = 1
EvntL=[]
GEL=[]
droppedPkts = 0
#buffer = Queue.Queue(MAXBUFFER)
#print buffer.buff.empty()
#print buffer.buff.qsize()
#print buffer.length
for i in range(10):
	t = ((-1/lam)*cmath.log10(1-random.uniform(0,1)))
	time = time + t
	st = ((-1/transtime)*cmath.log10(1-random.uniform(0,1)))
	EvntL.append(event("arrival",t,st))
	GEL.append(event("arrival",t,st))
	eventHolder = copy.deepcopy(EvntL[i]) #was EvntL.pop(0)
	if buffer.length == 0:
		eventHolder.departure('time')
		#print eventHolder.pktTime
		GEL.append(eventHolder)
	elif buffer.length > 0:
		if buffer.length-1 < MAXBUFFER:
			if buffer.buff.full():
				droppedPkts = droppedPkts + 1
			else:
				buffer.buff.put(eventHolder)
print GEL
#print EvntL
#print EvntL[0].eTime
#print EvntL[0].eType
#print EvntL[0].pktTime
exit

```
It is giving me this error:
```

$ python projPT1.py 
Traceback (most recent call last):
  File "projPT1.py", line 48, in <module>
    eventHolder.departure('time')
  File "projPT1.py", line 18, in departure
    self.DT = ti + self.srvTime
TypeError: cannot concatenate 'str' and 'complex' objects
$

```
I am not quite understanding why it is seeing ```
self.DT = ti + self.srvTime
``` as incompatable types. They have all been initialized to ints previously...

---

### Post by samjh on 2009-05-03
> **StunnerAlpha said:**
> I am not quite understanding why it is seeing ```
self.DT = ti + self.srvTime
``` as incompatable types. They have all been initialized to ints previously...

What type does the parameter ti pass?

```
def departure(self, ti):
		self.DT = ti + self.srvTime

```

Somewhere further down your code listing, I can see:
```
eventHolder.departure('time')
```

I don't know Python well enough to fully comprehend your code, but with working knowledge of over six programming languages, I smell an error somewhere thereabouts.

---

### Post by StunnerAlpha on 2009-05-03
> **samjh said:**
> What type does the parameter ti pass?

```
def departure(self, ti):
		self.DT = ti + self.srvTime

```

Somewhere further down your code listing, I can see:
```
eventHolder.departure('time')
```

I don't know Python well enough to fully comprehend your code, but with working knowledge of over six programming languages, I smell an error somewhere thereabouts.
The variable ti sends in time from here:
```

eventHolder.departure('time')

```
I took off the quotes on time and it looked for a function called departure rather than one in the class. It gave me an error to the effect that departure was not defined. I do not think I need to put double quotes around time, I already tried it in any case and gave me the exact same error message. Thanks for the help, if you can be anymore specific as to what the problem is, that would be greatly appreciated.

---

### Post by Arndt on 2009-05-03
> **StunnerAlpha said:**
> The variable ti sends in time from here:
```

eventHolder.departure('time')

```
I took off the quotes on time and it looked for a function called departure rather than one in the class. It gave me an error to the effect that departure was not defined. I do not think I need to put double quotes around time, I already tried it in any case and gave me the exact same error message. Thanks for the help, if you can be anymore specific as to what the problem is, that would be greatly appreciated.

If you put quotes (of any sort) around "time", of course you're sending a string, not a number (the value of the variable 'time').

```
eventHolder.departure(time)
```

ought to be correct.

Why do you use 'cmath' and not 'math'? 'cmath' is for complex numbers.

---

### Post by StunnerAlpha on 2009-05-03
> **Arndt said:**
> If you put quotes (of any sort) around "time", of course you're sending a string, not a number (the value of the variable 'time').

```
eventHolder.departure(time)
```

ought to be correct.

Why do you use 'cmath' and not 'math'? 'cmath' is for complex numbers.
Yep, that did it, thanks for that comment about cmath. When I searched for log the documentation said to use cmath as opposed to math. So unquoting and changing it to math did the trick, thanks a ton!

---

### Post by StunnerAlpha on 2009-05-03
Ey guys, now I am getting something else a bit strange that I can't figure out... Here is my code:
```

#!/usr/bin/python

import random, math, Queue, copy

global MAXBUFFER
MAXBUFFER = 0
global Time
Time = 0

class event(object):
	eType = None
	eTime = 0
	srvTime = 0
	TheTime = 0
	def __init__(self, eventType, eventTime, serviceTime):
		self.eType = eventType
		self.eTime = eventTime
		self.srvTime = serviceTime
	def departure(self, ti):
		self.TheTime = ti + self.srvTime
		Time = ti + self.srvTime
		self.eType = "departure"
		buffer.buff.get()
		


class buffer(object):
	buff = Queue.Queue(MAXBUFFER)
	length = buff.qsize()
	def __init__(self):
		buff = Queue.Queue(MAXBUFFER)

def GELsort(object,itr):
	if GEL[itr].TheTime < GEL[itr-1].TheTime:
		temp = GEL[itr]
		GEL[itr] = GEL[itr-1]
		GEL[itr-1] = temp


#time = 0
lam = 0.9
transtime = 1
EvntL=[]
GEL=[]
droppedPkts = 0
#buffer = Queue.Queue(MAXBUFFER)
#print buffer.buff.empty()
#print buffer.buff.qsize()
#print buffer.length
for i in range(10):
	t = ((-1/lam)*math.log10(1-random.uniform(0,1)))
	Time = Time + t
	st = ((-1/transtime)*math.log10(1-random.uniform(0,1)))
	EvntL.append(event("arrival",t,st))
	GEL.append(event("arrival",t,st))
	eventHolder = copy.deepcopy(GEL[i]) #was EvntL.pop(0)
	GELsort(GEL,i)
	if buffer.length == 0:
		buffer.buff.put(eventHolder)
		eventHolder.departure(Time)
		#print eventHolder.pktTime
		GEL.append(eventHolder)
		GELsort(GEL,i)
	elif buffer.length > 0:
		if buffer.length-1 < MAXBUFFER:
			if buffer.buff.full():
				droppedPkts = droppedPkts + 1
			else:
				buffer.buff.put(eventHolder)
	#sorter(GEL)			
	print GEL[i].eType, GEL[i].TheTime
	#print "Here is the time: ", Time
#print GEL
#print EvntL
#print EvntL[0].eTime
#print EvntL[0].eType
#print EvntL[0].pktTime
exit

```
And this is what I get:
```

$ python projPT1.py 
departure 1.10300268507
departure 1.10300268507
departure 1.10300268507
departure 1.54028842792
departure 1.54028842792
departure 2.10686359662
departure 2.10686359662
departure 2.52621597623
departure 2.52621597623
departure 3.12823372422
$

```
I am making a program to simulate a router's packet flow, I need to make the packet arrival and departure events. In the code you will see that I make a deep copy of the object in GEL[i](Global Event List) and then make that object undergo a departure function defined in the class event, after making the changes to the copied object I append that copy back onto the GEL. Here is the relevant portion of code:
```

GEL.append(event("arrival",t,st))
	eventHolder = copy.deepcopy(GEL[i]) #was EvntL.pop(0)
	GELsort(GEL,i)
	if buffer.length == 0:
		buffer.buff.put(eventHolder)
		eventHolder.departure(Time)
		#print eventHolder.pktTime
		GEL.append(eventHolder)

```
If any of you are willing to spend time to follow my code and point out why only departures are being stored in the GEL, that would be awesome. Thanks in advance!

---

### Post by Arndt on 2009-05-03
> **StunnerAlpha said:**
> Ey guys, now I am getting something else a bit strange that I can't figure out... 

If any of you are willing to spend time to follow my code and point out why only departures are being stored in the GEL, that would be awesome. Thanks in advance!

I suggest that you add comments to your code, explaining the logic.

---

### Post by StunnerAlpha on 2009-05-03
> **Arndt said:**
> I suggest that you add comments to your code, explaining the logic.
Aright, here is my code all commented up:
```

#!/usr/bin/python

import random, math, Queue, copy

global MAXBUFFER
MAXBUFFER = 0
global Time
Time = 0

class event(object):
	eType = None #can either be arrival or departure packet
	eTime = 0 #for arrivals-signifies arrival time of packet, which is added to Time
	srvTime = 0 #indicates how long it takes server to process packet for departure
	TheTime = 0 #class's own time variable
	def __init__(self, eventType, eventTime, serviceTime): #constructor sets arrival
		self.eType = eventType								#packet information
		self.eTime = eventTime
		self.srvTime = serviceTime
	def departure(self, ti): #converts arrival packet to departure packet
		self.TheTime = ti + self.srvTime
		Time = ti + self.srvTime
		self.eType = "departure"
		buffer.buff.get()
		


class buffer(object): #models router's packet queue
	buff = Queue.Queue(MAXBUFFER)
	length = buff.qsize() #how many packets currently in queue
	def __init__(self):
		buff = Queue.Queue(MAXBUFFER)

def GELsort(object,itr): #basic sorting algorithm to sort the GEL list based on time
						 #of events
	if GEL[itr].TheTime < GEL[itr-1].TheTime:
		temp = GEL[itr]
		GEL[itr] = GEL[itr-1]
		GEL[itr-1] = temp


#time = 0
lam = 0.9 #lamda-variable used in time calculations
transtime = 1 #transmission time-variable used in time calulations
EvntL=[] # just here for testing purposes
GEL=[] #holds all events
droppedPkts = 0
#buffer = Queue.Queue(MAXBUFFER)
#print buffer.buff.empty()
#print buffer.buff.qsize()
#print buffer.length
for i in range(10):
	t = ((-1/lam)*math.log10(1-random.uniform(0,1))) #calculating time of arrival
	Time = Time + t
	st = ((-1/transtime)*math.log10(1-random.uniform(0,1))) #calculating transmission time
	EvntL.append(event("arrival",t,st))
	GEL.append(event("arrival",t,st)) #adds arrival to the event list and makes the event
	eventHolder = copy.deepcopy(GEL[i]) #makes a copy of the object
	GELsort(GEL,i)
	if buffer.length == 0: #if router queue is empty
		buffer.buff.put(eventHolder) #put event in buffer queue
		eventHolder.departure(Time) #convert it to departure event by using a class method
		#print eventHolder.pktTime
		GEL.append(eventHolder) # add departure event to the GEL
		GELsort(GEL,i)
	elif buffer.length > 0:
		if buffer.buff.full():
			droppedPkts = droppedPkts + 1
		else:
			buffer.buff.put(eventHolder)
	#sorter(GEL)			
	print GEL[i].eType, GEL[i].TheTime #for testing purposes
	#print "Here is the time: ", Time
#print GEL
#print EvntL
#print EvntL[0].eTime
#print EvntL[0].eType
#print EvntL[0].pktTime
exit

```
Hope that helps and thanks!

---

### Post by StunnerAlpha on 2009-05-03
Nevermind guys I actually figured it out. The arrival events weren't being given a TheTime variable assigned while the departure events were causing only departure events to show up in the print statement due to the sorting feature.

---

### Post by Arndt on 2009-05-04
> **StunnerAlpha said:**
> Nevermind guys I actually figured it out. The arrival events weren't being given a TheTime variable assigned while the departure events were causing only departure events to show up in the print statement due to the sorting feature.

My plan succeeded: I hoped that when you thought your code through again, in order to comment it, that you would find the problem yourself.

---

### Post by StunnerAlpha on 2009-05-04
Yeah thanks for that, but it wasn't me that figured it out, it was a friend. He made a separate print function which helped us see everything.

---

