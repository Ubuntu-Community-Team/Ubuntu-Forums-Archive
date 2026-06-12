---
title: "Python file parsing help?"
date: 2005-01-12
forum: Programming Talk
---

### Post by amandla on 2005-01-12
Hi,

I am learning python, and i figured the best way would be to code something :D

I have plans to write a GUI for wireless-tools in python. My main focus is iwlist (for those of you who don't know, it list all the ssid's in the area). I want to write something similar to net stumbler. 

My first task is to parse the output which iwlist provides.
Looks like this:
```

 Cell 01 - Address: 00:03:52:F1:E0:10
                    ESSID:"videotron"
                    Mode:Master
                    Frequency:2.432GHz (channel 5)
                    Bit Rate:1Mb/s
                    Bit Rate:2Mb/s
                    Bit Rate:5.5Mb/s
                    Bit Rate:11Mb/s
                    Bit Rate:6Mb/s
                    Bit Rate:9Mb/s
                    Bit Rate:12Mb/s
                    Bit Rate:18Mb/s
                    Quality=51/100  Signal level=-47 dBm  Noise level=-98 dBm
                    Encryption key:off

  Cell 02 - ........

                ........

```

I would like to parse this output into a dictionary. So for example
Address is a key and 00:03:52:F1:E0:10 is the value
ESSID is a key and videotron is the value
etc etc

I am looking for some tips and/or modules that could help me out. I am already playing with the regular expressions. Any piece of advice would help a lot.


Cheers,

---

### Post by jdodson on 2005-01-12
[QUOTE=amandla]Hi,

I am learning python, and i figured the best way would be to code something :D

I have plans to write a GUI for wireless-tools in python. My main focus is iwlist (for those of you who don't know, it list all the ssid's in the area). I want to write something similar to net stumbler. 

My first task is to parse the output which iwlist provides.
Looks like this:
```

 Cell 01 - Address: 00:03:52:F1:E0:10
                    ESSID:"videotron"
                    Mode:Master
                    Frequency:2.432GHz (channel 5)
                    Bit Rate:1Mb/s
                    Bit Rate:2Mb/s
                    Bit Rate:5.5Mb/s
                    Bit Rate:11Mb/s
                    Bit Rate:6Mb/s
                    Bit Rate:9Mb/s
                    Bit Rate:12Mb/s
                    Bit Rate:18Mb/s
                    Quality=51/100  Signal level=-47 dBm  Noise level=-98 dBm
                    Encryption key:off

  Cell 02 - ........

                ........

```

I would like to parse this output into a dictionary. So for example
Address is a key and 00:03:52:F1:E0:10 is the value
ESSID is a key and videotron is the value
etc etc

I am looking for some tips and/or modules that could help me out. I am already playing with the regular expressions. Any piece of advice would help a lot.


Cheers,[/QUOTE]

a dictionary you have described might not be a good idea in this example.  reason:

if "Address" is the key, then for that line it is fine however when you get to "Bit Rate" you will then have multiple keys which will cause you problems(multiple instances of "Bit Rate").  in this example you have multiple keys.

btw python has dictionaries supported standard, like a list or a string.  documenation here:

[http://python.org/doc/2.3.3/tut/node7.html#SECTION007400000000000000000](http://python.org/doc/2.3.3/tut/node7.html#SECTION007400000000000000000)

btw parsing files is where python shines you can turn a file into a list and iterate over it, check that out here:

[http://python.org/doc/2.3.3/tut/node9.html#SECTION009200000000000000000](http://python.org/doc/2.3.3/tut/node9.html#SECTION009200000000000000000)

[http://python.org/doc/2.3.3/tut/node6.html#SECTION006200000000000000000](http://python.org/doc/2.3.3/tut/node6.html#SECTION006200000000000000000)

---

### Post by amandla on 2005-01-12
well i figure i was going to use br1 for the 1st Bit Rate, br2 for the 2nd and so on.
instead of using a list, i would perfer a dictionary since it will be easier to manilulate.

maybe i should convert the file into a list and then the list to a dictionary. what do you think??

---

### Post by Daniel G. Taylor on 2005-01-13
[Edit]: On second thought, this is probably not a very good example for you, since you are just learning Python. I would suggest reading up on Python's string and list/tuple/dict functionality on [http://python.org/doc](http://python.org/doc)

If the output is limited and you know exactly what will be output it should be trivial to find the strings you need in each line of the output and store them in a dict. I whipped up a quick example here that will parse that file and store the info in a tuple of dicts. The bit rates are stored as a list.

It's a bit of a cheap solution, but it would seem to work. Replace "data" with a filename to the output you are parsing.

```
#!/usr/bin/env python

data = open("data").readlines() # open the file

networks = () # initiate our networks tuple

for line in data:
	if "Address" in line: # create a new network dict
		address = line[line.find("Address") + 8:]
		networks += ({"Address" : address.strip()},)
	elif "Quality" in line: # store the entire line
		networks[len(networks) - 1]["Quality"] = line.strip()
	elif "Bit Rate" in line: # append the bitrate to our list of rates
		if not networks[len(networks) - 1].has_key("Bit Rates"):
			networks[len(networks) - 1]["Bit Rates"] = [] # create our list if it doesn't exist!
		rate = line[line.find("Bit Rate") + 9:]
		networks[len(networks) - 1]["Bit Rates"].append(rate.strip())
	else: # just grab the values and store them
		for string in ["ESSID", "Mode", "Frequency", "Encryption Key"]:
			if string in line:
				val = line[line.find(string) + len(string) + 1:]
				networks[len(networks) - 1][string] = val.strip()

print "Listing found networks:"
for network in networks:
	print network["Address"] + " [" + network["ESSID"] + "]"
	print "\tFrequency: " + network["Frequency"]
	for rate in network["Bit Rates"]:
		print "\tBit Rate: " + rate
	print "\t" + network["Quality"]
```
Alternatively you could store the networks as a dict with their unique address as the key, but I figured I'd throw the address into each network's dict and keep the top level structure a tuple.

---

### Post by amandla on 2005-01-14
thank you so much! I figured it would be something along those lines, just didn't have time to work it out. If your worried that its over my head, don't. I have coding experience ( c/c++, java, perl ... all because of school though, so I don't know if that counts as experience ;) )

I though I would have to use regular expressions to parse the file, and that was my main concern (the re.compile stuff was a bit wierd for me) but from your code, I see that it can be done without reg. exressions.

I will keep post any progress I make.

Thanks again!!!

---

