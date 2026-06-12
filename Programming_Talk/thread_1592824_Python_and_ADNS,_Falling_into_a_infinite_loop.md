---
title: "Python and ADNS, Falling into a infinite loop"
date: 2010-10-11
forum: Programming Talk
---

### Post by shoaibi on 2010-10-11
I have written some code that queries adns. Problem with this code is that it gets stuck, how? Let me explain it:

[LIST]
[*]Say my dnslist is ["8.8.4.4", "8.8.8.8", "208.67.220.220", "208.67.222.222", "192.168.50.1"] 
[*]It would pop a dns from the list and query againt it, now that means that DNS will be queried in reverse order
[*]No matter what i do, It never shows results from the dns it picked up first (in our case 192.168.50.1)
[*]I was not sure if that dns ever replied so
[LIST]
[*] First i changed DNS list to contain just that last DNS Server and code executes fine
[*] Second i used the old list with 5 DNS servers except that the last one was managed by my so i could track if code even queries it or not, and to my surprise the query does take place.
[*] So query is made, we get result but that result is never inserted into resolved_hosts for some reason, and because that results is not inserted, its length will remain less than the length of dnslist, causing a infinite loop.
[/LIST]
[/LIST]

What do you think could be causing this problem and how to solve it?



** Code Execution Results **
```

    Inside class's init'
    Data
    host www.yahoo.com
    dnslist length 5
    intensity 1
    Inside resolve()
    inside finished_resolving()
    Resolved : 0/5
    Inside 'while not finished_resolving'
    Queue: 0/1
    Launching Querying for www.yahoo.com/1 on 192.168.50.1
    Queue: 1/1
    Launching Querying for www.yahoo.com/1 on 208.67.222.222
    inside collect_results()
    inside finished_resolving()
    Resolved : 0/5
    Inside 'while not finished_resolving'
    ------------------------ CLIPPED ----------------
    Inside 'while not finished_resolving'
    inside collect_results()
    Inside collect_results's for query in self.adns.completed()
    DNS used was208.67.222.222
    Answered : (0, 'any-fp.wa1.b.yahoo.com', 1286169807, ('69.147.125.65', '67.195.160.76'))
    Resolved www.yahoo.com to 69.147.125.65 using 208.67.222.222
    Resolved hosts count1
    And they are: 
    {'208.67.222.222': '69.147.125.65'}
    
    
    inside finished_resolving()
    Resolved : 1/5
    Inside 'while not finished_resolving'
    Queue: 1/1
    Launching Querying for www.yahoo.com/1 on 208.67.220.220
    inside collect_results()
    inside finished_resolving()
    Resolved : 1/5
    Inside 'while not finished_resolving'
    -------------------------- CLIPPED --------------------
    inside collect_results()
    Inside collect_results's for query in self.adns.completed()
    DNS used was208.67.220.220
    Answered : (0, 'any-fp.wa1.b.yahoo.com', 1286169790, ('67.195.160.76', '69.147.125.65'))
    Resolved www.yahoo.com to 67.195.160.76 using 208.67.220.220
    Resolved hosts count2
    And they are: 
    {'208.67.222.222': '69.147.125.65', '208.67.220.220': '67.195.160.76'}
    
    
    inside finished_resolving()
    Resolved : 2/5
    Inside 'while not finished_resolving'
    Queue: 1/1
    Launching Querying for www.yahoo.com/1 on 8.8.8.8
    inside collect_results()
    inside finished_resolving()
    Resolved : 2/5
    Inside 'while not finished_resolving'
    -------------------------- CLIPPED --------------------
    inside collect_results()
    Inside collect_results's for query in self.adns.completed()
    DNS used was8.8.8.8
    Answered : (0, 'eu-fp.wa1.b.yahoo.com', 1286169758, ('87.248.122.122',))
    Resolved www.yahoo.com to 87.248.122.122 using 8.8.8.8
    Resolved hosts count3
    And they are: 
    {'208.67.222.222': '69.147.125.65', '208.67.220.220': '67.195.160.76', '8.8.8.8': '87.248.122.122'}
    
    
    inside finished_resolving()
    Resolved : 3/5
    Inside 'while not finished_resolving'
    Queue: 1/1
    Launching Querying for www.yahoo.com/1 on 8.8.4.4
    inside collect_results()
    inside finished_resolving()
    Resolved : 3/5
    Inside 'while not finished_resolving'
    -------------------- CLIPPED -------------------------------------
    inside collect_results()
    Inside collect_results's for query in self.adns.completed()
    DNS used was8.8.4.4
    Answered : (0, 'eu-fp.wa1.b.yahoo.com', 1286169757, ('87.248.122.122',))
    Resolved www.yahoo.com to 87.248.122.122 using 8.8.4.4
    Resolved hosts count4
    And they are: 
    {'208.67.222.222': '69.147.125.65', '208.67.220.220': '67.195.160.76', '8.8.8.8': '87.248.122.122', '8.8.4.4': '87.248.122.122'}
    
    
    inside finished_resolving()
    Resolved : 4/5
    Inside 'while not finished_resolving'
    inside collect_results()
    inside finished_resolving()
    Resolved : 4/5
    ---------------- CLIPPED -------------------------------

(last block keeps repeating until system starts to hang up, load goes upto 24)

```

Here is the code.

**test.py**
```

    import adns
    from time import time
    from async_dns import AsyncResolver
    
    
    
    dnslist2 = ["8.8.4.4", "8.8.8.8", "208.67.220.220", "208.67.222.222", "192.168.50.1"]  #192.168.50.1  is a dns server i manage
    host = "www.yahoo.com"
    record = adns.rr.A
    intensity = len(dnslist2)/5+1
    
    ar = AsyncResolver(dnslist2, host, record, intensity)
    start = time()
    resolved = ar.resolve()
    end = time()
    
    print "\n\n"
    
    for dns, ip in resolved.items():
      if ip is None:
        print "%s could not resolv %s." % (dns, host)
      else:
        print "%s resolved it to %s : %s" % (dns, host, ip)
    
    print "\n\n----------------------------------------------------"
    print "It took %.2f seconds to query %d dns." % (end-start, len(dnslist))
    print "----------------------------------------------------"


```


**async_dns.py**

```

    #!/usr/bin/python
    #
    
    import sys
    import adns
    from time import time
    
    class AsyncResolver(object):
    	def __init__(self, dnslist, host, record, intensity=10):
    
    		"""
    		dnslist: a list of dns used to resolve
    		host : hostname to resolve
    		record: recordtype to resolve
    		intensity: how many hosts to resolve at once
    		"""
    		print "Inside class's init'"
    		self.dnslist = dnslist
    		self.host = host
    		self.record = record
    
    
    		if intensity >= len(dnslist) :
    			self.intensity = len(dnslist)/5+1
    		else:
    			self.intensity = intensity
    
    		print "Data"
    		print "host " + host
    		print "dnslist length " + str(len(dnslist))
    		print "intensity " + str(intensity)
    
    
    
    
    	def resolve(self):
    		""" Resolves hosts and returns a dictionary of { 'dns': 'ip' }. """
    		print "Inside resolve()"
    
    		host = self.host
    		record = self.record
    		resolved_hosts = {}
    		active_queries = {}
    		dns_queue = self.dnslist[:]
    
    		def collect_results():
    			print "inside collect_results()"
    			for query in self.adns.completed():
    				print "Inside collect_results's for query in self.adns.completed()"
    				answer = query.check()
    				dns = active_queries[query]
    				print "DNS used was" + dns
    				print "Answered : " + str(answer)
    				del active_queries[query]
    				if answer[0] == 0:
    					#print "Inside answer[0] == 0 , ip:" + answer[3][0]
    					ip = answer[3][0]
    					resolved_hosts[dns] = ip
    					print "Resolved %s to %s using %s" % (host, ip, dns)
    					print "Resolved hosts count" + str(len(resolved_hosts))
    					print "And they are: "
    					print str(resolved_hosts)
    					print "\n"
    
    				elif answer[0] == 101 and not record == adns.rr.CNAME: # CNAME if CNAME wasn't required'
    					print "ooopppps, i got a CNAME, gotta find its A"
    					print "\n"
    					query = self.adns.submit(answer[1], adns.rr.A)
    					active_queries[query] = dns
    				else:
    					resolved_hosts[dns] = None
    					print "THIS COULD NOT BE RESOLVED"
    
    		def finished_resolving():
    			print "inside finished_resolving()"
    			print "Resolved : " + str(len(resolved_hosts)) + "/" + str(len(self.dnslist))
    			return len(resolved_hosts) == len(self.dnslist)
    
    		while not finished_resolving():
    			print "Inside 'while not finished_resolving'"
    			while dns_queue and len(active_queries) <= self.intensity:
    				print "Queue: " + str(len(active_queries)) + "/" + str(self.intensity)
    				dns = dns_queue.pop()
    				self.adns = adns.init(adns.iflags.noautosys,sys.stderr,"nameserver "+dns)
    				query = self.adns.submit(host, record)
    				print "Launching Querying for " + host + "/" + str(record) + " on " + dns
    				active_queries[query] = dns
    			collect_results()
    		return resolved_hosts


```

---

### Post by Tony Flury on 2010-10-11
From your description it would appear not to be an issue with ADNS per-se but an issue with how you manage your lists ?

Have you tried to extract the relevants parts of the code into a seperate class/file and test them - with maybe dummy responses - so you can more easily see what is going on ?

---

### Post by shoaibi on 2010-10-11
> **Tony Flury said:**
> From your description it would appear not to be an issue with ADNS per-se but an issue with how you manage your lists ?

Have you tried to extract the relevants parts of the code into a seperate class/file and test them - with maybe dummy responses - so you can more easily see what is going on ?

I have updated my code, now:
[LIST]
[*]It works with as many dns server inside dnslist as many you put if intensity is 1
[*]If intensity is >1 and len(dnslist) >1 then it falls into infinite loop like before
[/LIST]


**I think problem lies somewhere**
```

		def finished_resolving():
			#print "Inside finished_resolving()"
			#print "Resolved : " + str(len(resolved_hosts)) + "/" + str(len(self.dnslist))
			return len(resolved_hosts) == len(self.dnslist)

		while not finished_resolving():
			#print "Inside 'while not finished_resolving"
			while dns_queue and len(active_queries) < self.intensity:
				print "Queue: " + str(len(active_queries)) + "/" + str(self.intensity)
				dns = dns_queue.pop()
				self.adns = adns.init(adns.iflags.noautosys,sys.stderr,"nameserver "+dns)
				query = self.adns.submit(host, record)
				print "Launching Querying for " + host + "/" + str(record) + " on " + dns
				active_queries[query] = dns
			collect_results()
		return resolved_hosts

```

[B]because thats the only things that runs differently when intensity =1 and when intensity >1.
[/B]

**Updated code**

```


#!/usr/bin/python

import sys
import adns
from time import time

class AsyncResolver(object):
	def __init__(self, dnslist, host, record, intensity=10):

		"""
		dnslist: a list of dns used to resolve
		host : hostname to resolve
		record: recordtype to resolve
		intensity: how many hosts to resolve at once
		"""
		#print "Inside class's init"
		self.dnslist = dnslist
		self.host = host
		self.record = record


		if intensity >= len(dnslist) :
			self.intensity = len(dnslist)/5+1
		else:
			self.intensity = intensity

		#print "Data"
		#print "host " + host
		#print "dnslist length " + str(len(dnslist))
		#print "intensity " + str(intensity)




	def resolve(self):
		""" Resolves hosts and returns a dictionary of { 'dns': 'ip' }. """
		#print "Inside resolve()"

		host = self.host
		record = self.record
		resolved_hosts = {}
		active_queries = {}
		dns_queue = self.dnslist[:]

		def collect_results():
			#print "Inside collect_results()"
			#print "self.adns.completed(): " + str(self.adns.completed())
			#print "Resolved Host :  " + str(resolved_hosts)
			#print "Resolved hosts count : " + str(len(resolved_hosts))
			#print "\n"
			#print str(self.adns.completed)

			for query in self.adns.completed():
				#print "Inside collect_results's for query in self.adns.completed()"
				answer = query.check()
				dns = active_queries[query]
				#print "DNS used was : " + dns
				#print "Answered : " + str(answer)
				del active_queries[query]
				if answer[0] == 0:
					#print "Inside answer[0] == 0 , ip : " + answer[3][0]
					ip = answer[3][0]
					resolved_hosts[dns] = ip
					#print "Resolved %s to %s using %s" % (host, ip, dns)
					#print "Resolved hosts count : " + str(len(resolved_hosts))
					#print "And they are :  " + str(resolved_hosts)
					#print "\n"

				elif answer[0] == 101 and not record == adns.rr.CNAME: # CNAME if CNAME wasn't required'
					#print "ooopppps, i got a CNAME, gotta find its A"
					#print "\n"
					query = self.adns.submit(answer[1], adns.rr.A)
					active_queries[query] = dns
				else:
					resolved_hosts[dns] = None
					print "THIS COULD NOT BE RESOLVED"

		def finished_resolving():
			#print "Inside finished_resolving()"
			#print "Resolved : " + str(len(resolved_hosts)) + "/" + str(len(self.dnslist))
			return len(resolved_hosts) == len(self.dnslist)

		while not finished_resolving():
			#print "Inside 'while not finished_resolving"
			while dns_queue and len(active_queries) < self.intensity:
				print "Queue: " + str(len(active_queries)) + "/" + str(self.intensity)
				dns = dns_queue.pop()
				self.adns = adns.init(adns.iflags.noautosys,sys.stderr,"nameserver "+dns)
				query = self.adns.submit(host, record)
				print "Launching Querying for " + host + "/" + str(record) + " on " + dns
				active_queries[query] = dns
			collect_results()
		return resolved_hosts

```

---

### Post by Tony Flury on 2010-10-11
Have you got the output of your debug info when intensity >1 (I assume  intensity is your queue size - i.e. how many queries you can do simulatenously) ?

---

### Post by shoaibi on 2010-10-11
with intensity > 1 results are identical to the "Code Execution Results" posted in my first post of this thread, observe same phenomenon with intensity >1 as described in first post as well

---

### Post by Tony Flury on 2010-10-12
The example output seems to show results with intensity = 1 not >1, unless i completely misunderstand your code and its intentions.

---

