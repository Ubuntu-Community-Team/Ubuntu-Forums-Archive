---
title: "Star Trek Cypher Challenge? Really strange!"
date: 2009-04-10
forum: Programming Talk
---

### Post by evymetal on 2009-04-10
Ok, strange question this - Found via twitter (original tweet was in Spanish, so I don't really understand it, just came up in a search).

Seems there have been some really cheesy parties to launch the new Star Trek film, someone spotted that in the background of one of the pictures there was a weird URL.

(here's the pic with the URL in the background)
[http://www.thecobrasnake.com/partyphotos/hollywoodstars/IMG_8403.html](http://www.thecobrasnake.com/partyphotos/hollywoodstars/IMG_8403.html)

The url is in Binary, and is just the letter "O" in Ascii.

That url just loops a flash video over and over. *BUT* there seems to be some cyphertext in there (you have to do freeze-frame to get this image):

```

|*^|.|#%|.|*#@|.|*^@|

```

which looks like cyphertext for an ip address to me.

Assuming it's a substitution cypher, all I can work out is that "*" must be either a 1 or a 2.

Can anyone work anything else out? Or do you think I'm looking at this too deeply?


There are a couple of other things in there too which might be part of the cypher, like four elements:
```

Fe    Ca  Si    Al

```
(The spacing might be important, but I don't know)

and what might be a date:
```

-04|14|09

```
(EDIT) - Date seems to have changed to  "-04|17|09"

---

### Post by Mark76 on 2009-04-10
14th of April 2009 is the date (it's in American notation with the month first)

The elements are: iron (Fe), calcium (Ca), silicon (Si) and aluminium (Al).

How do you work out that * is 1 or 2?

---

### Post by evymetal on 2009-04-10
> **Mark76 said:**
> 14th of April 2009 is the date (it's in American notation with the month first)

The elements are: iron (Fe), calcium (Ca), silicon (Si) and aluminium (Al).


The date makes more sense in the american style (was wondering what the 14th month was!)


> **Mark76 said:**
> How do you work out that * is 1 or 2?

I'm assuming that 
```

|*^|.|#%|.|*#@|.|*^@|

```

is an ip address.

So
```

1 <= *^  <= 255
1 <= #%  <= 255
1 <= *#@ <= 255
1 <= *^@ <= 255

```

i.e. * must be 0,1 or 2 - but I don't think they'd have two-numeral numbers in there if they were writing the first 0 sometimes, so it must be 1 or 2.

There's a lot of other noise-like images in the original video, but apart from the Roman numeral "VI" (6) I can't make sense of anything else yet.

---

### Post by Greyed on 2009-04-10
> **Mark76 said:**
> 14th of April 2009 is the date (it's in American notation with the month first)

The elements are: iron (Fe), calcium (Ca), silicon (Si) and aluminium (Al).

How do you work out that * is 1 or 2?

Because if the presumption of it being an IP address is true then it can only be a 1 or a 2.  Remember, every octet is well, an octet.  0-FF in HEX or 0-255 in decimal.  3 positions in the latter octets with * bing in the first position.  1xx or 2xx are the only numbers that fit.  ;)

---

### Post by CptPicard on 2009-04-10
Atomic numbers of the elements -- Fe 26; Ca 20; Si 14; Al 13.

---

### Post by evymetal on 2009-04-10
> **CptPicard said:**
> Atomic numbers of the elements -- Fe 26; Ca 20; Si 14; Al 13.

Ah, that's a good point - wonder how/if they're involved.

Forgot to mention, for the same reason given for * being 1 or 2, I'm assuming that # is not 0 (as it appears as the first number in the b-block.)

so That leaves us with

"*" \in {1,2}
"#" \in {1...9}
"@" \in {0...9}
"^" \in {0...9}

... but that's still 1,800 possible ip addresses :-(


Got people coming over for the weekend so I'll mull it over off-line, but if anyone finds out more then I'll be interested. Couldn't find this video mentioned anywhere else when I looked earlier.

---

### Post by jimi_hendrix on 2009-04-10
whats the date of the movie launch

---

### Post by nvteighen on 2009-04-10
This sounds a bit like the "Publius Enigma" thing Pink Floyd started when released their "The Division Bell" album... ([http://en.wikipedia.org/wiki/Publius_Enigma](http://en.wikipedia.org/wiki/Publius_Enigma))

---

### Post by soltanis on 2009-04-10
Well you do know one thing. Assuming that in the cipher 

|*^|.|#%|.|*#@|.|*^@|

Each character stands for an individual number,
* = 1 or 2, like you said
# cannot be 1 or 2, so it must be 0,3..9
% cannot be 1 or 2 or #, but right now all we know is 0,3..9
@ cannot be 1, 2, #, or %, 0,3..9
^ appears in the first and last places.

Now let me extrapolate a little here.

10.0.0.0 is a reserved subspace of addresses. So ^ cannot be 0.
If * is 2, then ^ cannot be greater than 5, and if ^ is 5 when * is 2, @ cannot be greater than 5 either.

Lets pretend * is 1.
Listing who owns the addresses for all possible ^.
```

11.0.0.0 - 11.255.255.255 : US Department of Defense
12.0.0.0 - 12.255.255.255 : ATT Worldnet
13.0.0.0 - 13.255.255.255 : Xerox Corp.
14.0.0.0 - 14.255.255.255 : IANA
15.0.0.0 - 15.255.255.255 : HP
16.0.0.0 - 16.255.255.255 : HP
17.0.0.0 - 17.255.255.255 : Apple Computers
19.0.0.0 - 19.255.255.255 : Ford Motor Company

```
Hmm. Safe to say whoever this is probably isn't from the DoD, Xerox, IANA, HP, Apple, or Ford. So...if * is 1, then ^ is most likely to be 2...an AT&T customer.

PS. That URL doesn't seem to exist (I was going to do a whois on it to try to see where its coming from)

---

### Post by benj1 on 2009-04-10
just done a quick hack to work out all unique ip addresses don't think i have the speed to implement a war dialer for it tho will have to wait till next week ind im back on broadband

[ATTACH]109384[/ATTACH]

heres what i used:
```
	A = 1  # *
	B = 2  # #
	C = 3  # @
	D = 4  # ^
	E = 5  #  %
	file = open("/home/ben/Desktop/ip",'w')
	while A <= 2:
		
		while B <= 9:
			
			while C <= 9:
				
				while D <= 9:
					
					while E <= 9:
						numa = int("%d%d%d" % (A,B,C))
						numb = int("%d%d%d" % (A,D,C))
						
						if numa < 256 and numb < 256:
							if A != B != C != D != E:
								file.write("%d%d.%d%d.%d%d%d.%d%d%d\n" % (A,D,B,E,A,B,C,A,D,C))
						E += 1
						if E == 10: E = 0; break
					D += 1
					if D == 10: D = 0; break
				C+= 1
				if C == 10: C = 0; break
			B +=1
			if B == 10: B = 1; break
		A += 1
```


i think this should dial them to see if they are valid(ripped it from a web site but should work) might need some way of controlling open threads
haven't tried it as i say slow connection

```
	file = open("/home/ben/Desktop/ip",'r')
	fileout = open("/home/ben/Desktop/ip2",'w')

	text = file.readlines()
	import os
	import re
	import sys
	from threading import Thread

	class testit(Thread):
		def __init__ (self,ip):
			Thread.__init__(self)
			self.ip = ip
			self.status = -1
		def run(self):
			pingaling = os.popen("ping -q -c2 "+self.ip,"r")
			while 1:
				line = pingaling.readline()
				if not line: break
				igot = re.findall(testit.lifeline,line)
				if igot:
					self.status = int(igot[0])

	testit.lifeline = re.compile(r"(\d) received")
	report = ("No response","Partial Response","Alive")


	pinglist = []

	for lines in text:
		current = testit(lines)
		pinglist.append(current)
		current.start()

	for pingle in pinglist:
		pingle.join()
		if pingle.status == "Alive": fileout.write(pingle.ip)   

			
```

---

### Post by soltanis on 2009-04-10
You really need to narrow down the address space before we start dialing. I mean, we don't even know what we're looking for; a webserver port is ideal, but what if it's an ssh server (or worse, an echo, chargen, or motd server?). We'd essentially have to port scan the entire address space we decide to look in, and while nmap is capable of doing that, it would take a very, very long time.

If it ever gets down to that, we'd have to distribute the load over several workstations to have any reasonable expectation of finding our mystery server.

---

### Post by evymetal on 2009-04-11
Don't think we'll need to dial after all.

Looks like there are multiple videos on different domains - and the other videos hold the substitution.

(NOTE: weirdly, the date seems to have changed since I first saw the video - it's now -04|17|09)

[http://trekmovie.com/2009/04/10/new-star-trek-viral-campaign/](http://trekmovie.com/2009/04/10/new-star-trek-viral-campaign/)
[http://forums.unfiction.com/forums/viewtopic.php?t=27713](http://forums.unfiction.com/forums/viewtopic.php?t=27713)

> 
When you do this for all four elements you get 97.74.158.186. 
(snip)
However, 01001111.com matches the IP [http://97.74.158.184](http://97.74.158.184). IPs that close are likely housed at the same location and possibly even the same server.

So for now it looks like the solution is to visit [http://97.74.158.186/](http://97.74.158.186/) on Friday April 17th. Unclear what the ‘VI’ clue leads to. That may be a code used for the site, or maybe it means 6 AM (or PM).


---

### Post by evymetal on 2009-04-11
Oh, and this may be of interest to us Linux users:

Output of nmap:

Aggressive OS guesses: Linux 2.6.18 (95%), Linux 2.6.19 - 2.6.20 (Gentoo) (95%), Linux 2.6.9 - 2.6.15 (95%), Linux 2.6.11 - 2.6.19 (94%)

---

