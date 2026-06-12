---
title: "Replace string in file from file, a bit complicated?"
date: 2009-03-24
forum: Programming Talk
---

### Post by Beefeater on 2009-03-24
Hi guys,

When I thought I was almost finished I stumbled upon a problem writing my bash script.

Let me explain.. I've got two files, newdata.txt and data.xml

The file newdata.txt looks similar to this:

<url>http://example.com/1234</url><info>63113</info>
<url>http://example.com/3253</url><info>245121</info>
<url>http://example.com/3454</url><info>212512</info>
<url>http://example.com/6364</url><info>2531</info>
<url>http://example.com/3582</url><info>2352</info>

The file data.xml:

.....
<url>http://example.com/1234</url>
.....
<url>http://example.com/3253</url>
.....
<url>http://example.com/3454</url>
.....
<url>http://example.com/6364</url>
.....
<url>http://example.com/3582</url>
.....

What I want to do is replace the line in data.xml with the corresponding data from newdata.txt.

As you can see from the structure, line by line replacement is not an option. 

My first solution to the problem was something like this.

1. Read newdata.txt line by line.
2. Save the line into two variables, $newdata (<url>http://example.com/1234</url><info>2482</info>) and $olddata (<url>http://example.com/1234</url>)
3. Do a sed replace $olddata with $newdata on data.xml

And there is the problem, is it even possible to 1. direct data from sed into a variable and 2. use variables with sed?

Everything I've done up to this point is part of a bash script so I would really appreciate any suggestions on how to achieve this without writing a new program from the beginning.

Hopefully I made myself clear enough, been sitting with this the entire evening until I crash landed with this problem an hour ago. So I'm a bit nackerd.

Cheers

---

### Post by Can+~ on 2009-03-24
Are the <url>...</url><info>...</info> well formatted? I mean, are there any other things mixed in? Like

<linkinfo>
<url>...</url><info>...</info></linkinfo>

I could write a quick py script.

---

### Post by Beefeater on 2009-03-24
> **Can+~ said:**
> Are the <url>...</url><info>...</info> well formatted? I mean, are there any other things mixed in? Like

<linkinfo>
<url>...</url><info>...</info></linkinfo>

I could write a quick py script.

Oh cheers mate. They are well formated. Really appreciate it!

---

### Post by Can+~ on 2009-03-24
[PHP]#!/usr/bin/python

def getSpaces(line):
	"""Retrieve the spaces before the first character."""
	space = ""
	
	for char in line:
		if char == " " or char == "\t":
			space += char
		else:
			break
	
	return space

fnewdata = "newdata.xml"
fdata = "data.xml"
fexport = "data_export.xml" # In case I accidentaly break sth.

matches = {}

fnewdata = open(fnewdata, "r")

#Open newdata
for line in fnewdata:
	line = line.strip()
	line_key = line
	
	#Filter
	if line_key.startswith("<url>") and line_key.endswith("</info>"):
		#Get the key
		line_key = line_key.split("<info>")[0]
		
		matches[line_key] = line

fnewdata.close()

fdata = open(fdata, "r")
fexport = open(fexport, "w")

for line in fdata:
	#Swap'em
	try:
		#Create a correctly formatted string, <space><content>\n
		replace = "%s%s\n" % (getSpaces(line), matches[line.strip()])
		
		#Write it down
		fexport.write(replace)	
			
	except KeyError:
		#Otherwise just copy it
		fexport.write(line)

fdata.close()
fexport.close()
[/PHP]

Not the most optimal way, didn't use the xml library or regexps, just a plain if check, so it may not work well.

It also saves it as another file (data_export.xml) so you can run it safely.

(whoa, it took me 8 minutes to make this)

---

### Post by ghostdog74 on 2009-03-24
```

awk 'BEGIN{FS="<[/]?info>"}FNR==NR{_[$1]=$2;next}{print "<url>http://example.com/"_[$1]"</url>"}' newdata data

```

---

### Post by Beefeater on 2009-03-25
> **Can+~ said:**
> [PHP]#!/usr/bin/python

def getSpaces(line):
	"""Retrieve the spaces before the first character."""
	space = ""
	
	for char in line:
		if char == " " or char == "\t":
			space += char
		else:
			break
	
	return space

fnewdata = "newdata.xml"
fdata = "data.xml"
fexport = "data_export.xml" # In case I accidentaly break sth.

matches = {}

fnewdata = open(fnewdata, "r")

#Open newdata
for line in fnewdata:
	line = line.strip()
	line_key = line
	
	#Filter
	if line_key.startswith("<url>") and line_key.endswith("</info>"):
		#Get the key
		line_key = line_key.split("<info>")[0]
		
		matches[line_key] = line

fnewdata.close()

fdata = open(fdata, "r")
fexport = open(fexport, "w")

for line in fdata:
	#Swap'em
	try:
		#Create a correctly formatted string, <space><content>\n
		replace = "%s%s\n" % (getSpaces(line), matches[line.strip()])
		
		#Write it down
		fexport.write(replace)	
			
	except KeyError:
		#Otherwise just copy it
		fexport.write(line)

fdata.close()
fexport.close()
[/PHP]

Not the most optimal way, didn't use the xml library or regexps, just a plain if check, so it may not work well.

It also saves it as another file (data_export.xml) so you can run it safely.

(whoa, it took me 8 minutes to make this)

Whoa, I love it! Worked like a charm on the first run.
Thanks!

---

