---
title: "using python to construct feature vectors"
date: 2012-01-18
forum: Programming Talk
---

### Post by shortridge11 on 2012-01-18
I'm new to python and I'm trying to figure out how to use python to construct some feature vectors. I'm looking at about 50 text documents and i just need to make a different file for each document, as well as a document covering all 50 different text documents.  The feature vector can be super basic, I'm just trying to get a handle on this language and hopefully after this I'll be able to do something useful.  I'm thinking an easy feature vector would be some sort of partial map with each word mapped to a integer value of how many times it occurs. I'd appreciate any pointers in the right direction, and any libraries that would make this easy.

---

### Post by shortridge11 on 2012-01-18
So far I've figured out how to cut out the body, now I'm attempting to chop up each string and place it in a map (dict?).

Here's what I have so far:
```
with open('test.txt', 'r') as f:
	read_data = f.read()						## puts the entire file into this string
	f.close()							## we're done reading, free up resources
	body_end = 0							## explicitly named so we start scraping the <BODY>s from the start
	body_position = 0						## just initialized
	last_body = read_data.rfind('<BODY>')				## gets the index of the last <BODY> so the loop knows when to stop
	##print last_body							## debugging
	while (body_position != last_body):
		body_position = read_data.find('<BODY>', body_end)	## gets the next <BODY> index
		body_end = read_data.find('</BODY>', body_position)	## gets the following </BODY> index
		body_data = read_data[body_position + 6:body_end]	## now we have each <BODY>....</BODY> in a string to play with, add 6 to cut out <BODY>
		print body_data

```

This just prints out each <BODY>. any suggestions for splitting up each string using the space char (\0 i think) as a delimiter?

---

### Post by Arndt on 2012-01-18
> **shortridge11 said:**
> So far I've figured out how to cut out the body, now I'm attempting to chop up each string and place it in a map (dict?).

Here's what I have so far:
```
with open('test.txt', 'r') as f:
	read_data = f.read()						## puts the entire file into this string
	f.close()							## we're done reading, free up resources
	body_end = 0							## explicitly named so we start scraping the <BODY>s from the start
	body_position = 0						## just initialized
	last_body = read_data.rfind('<BODY>')				## gets the index of the last <BODY> so the loop knows when to stop
	##print last_body							## debugging
	while (body_position != last_body):
		body_position = read_data.find('<BODY>', body_end)	## gets the next <BODY> index
		body_end = read_data.find('</BODY>', body_position)	## gets the following </BODY> index
		body_data = read_data[body_position + 6:body_end]	## now we have each <BODY>....</BODY> in a string to play with, add 6 to cut out <BODY>
		print body_data

```

This just prints out each <BODY>. any suggestions for splitting up each string using the space char (\0 i think) as a delimiter?

If it's in XML, you may want to use the modules which parse XML documents. That way, you will learn XML at the same time.

---

