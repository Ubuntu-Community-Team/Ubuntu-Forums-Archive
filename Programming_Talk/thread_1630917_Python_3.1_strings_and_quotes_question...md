---
title: "Python 3.1 strings and quotes question.."
date: 2010-11-25
forum: Programming Talk
---

### Post by hopelessone on 2010-11-25
Hi,

I'm learning python after coming across from VB6 a few years ago...

I have the following:
```
import urllib.request
import re

page = urllib.request.urlopen("http://www.yellowpages.com.au/search/listings?clue=auto+electrician&locationClue=Queensland&x=41&y=17")
text = page.read().decode("utf8")

str = text;

sub = '<span id="listing-name-';
print("Total : ", str.count(sub))

before, tag, txt = text.partition('<span id="listing-name-1">') # before = text before the tag, tag = <span id>, txt = text after the tag
while txt:
   
   txt, endtag, after = txt.partition('</span>') #txt = text before the end tag, endtag = </span>, after = text after the endtag

   if endtag:
          print(txt) #this is the text between the tags
   else:
          raise ValueError('Missing end tag ' + txt) #no end tag to delimit the text

   before, tag, txt = after.partition('<span id="listing-name-1">') #repeat

```

Now [COLOR="Red"]str.count(sub)[/COLOR] is 40 for this page

how can i say for 1 to 40 in this string?

text.partition('<span id="listing-name-[COLOR="Red"]1[/COLOR]">')

because str.count(sub) is an Integer and I can't figure out how to mix them together in a string..

Hoping you can shed light to it all...

Thanks...

---

### Post by Arndt on 2010-11-26
> **hopelessone said:**
> Hi,

I'm learning python after coming across from VB6 a few years ago...

I have the following:
```
import urllib.request
import re

page = urllib.request.urlopen("http://www.yellowpages.com.au/search/listings?clue=auto+electrician&locationClue=Queensland&x=41&y=17")
text = page.read().decode("utf8")

str = text;

sub = '<span id="listing-name-';
print("Total : ", str.count(sub))

before, tag, txt = text.partition('<span id="listing-name-1">') # before = text before the tag, tag = <span id>, txt = text after the tag
while txt:
   
   txt, endtag, after = txt.partition('</span>') #txt = text before the end tag, endtag = </span>, after = text after the endtag

   if endtag:
          print(txt) #this is the text between the tags
   else:
          raise ValueError('Missing end tag ' + txt) #no end tag to delimit the text

   before, tag, txt = after.partition('<span id="listing-name-1">') #repeat

```

Now [COLOR="Red"]str.count(sub)[/COLOR] is 40 for this page

how can i say for 1 to 40 in this string?

text.partition('<span id="listing-name-[COLOR="Red"]1[/COLOR]">')

because str.count(sub) is an Integer and I can't figure out how to mix them together in a string..

Hoping you can shed light to it all...

Thanks...

Is it the % operator you want? It works like this

```
>>> "hej %d hopp %d foo" % (4, 5)
'hej 4 hopp 5 foo'
>>> 

```

---

### Post by hopelessone on 2010-11-26
no sorry, here's what i got so far, but it doesn't loop and exits after the first find..
```
import urllib.request
import re

page = urllib.request.urlopen("http://www.yellowpages.com.au/search/listings?clue=auto+electrician&locationClue=Queensland&x=41&y=17")
text = page.read().decode("utf8")

sub = '<span id="listing-name-';
s = text.count(sub)
k = 1

while k!=s:
 t = ('<span id="listing-name-1">')
 t.replace('1', str(k))
 k=k+1

 
 before, tag, txt = text.partition(t) # before = text before the tag, tag = <span id>, txt = text after the tag

while txt:
 
 txt, endtag, after = txt.partition('</span>') #txt = text before the end tag, endtag = </span>, after = text after the endtag

 if endtag:
  print(txt) #this is the text between the tags
 else:
  raise ValueError('Missing end tag ' + txt) #no end tag to delimit the text

 before, tag, txt = after.partition(t) #repeat

print("finished")
```

Any ideas?
Thanks

---

### Post by smartbei on 2010-11-27
Let's use Regular Expressions instead of parsing the string ourselves. With RE, we can tell it to find any string that has, say, one or two digits at a certain position. To match the span start tag (whole) we would use something like:
```

pattern = re.compile('<span id="listing-name-\d{1,2}">')

```
We match the whole tag, and allow one or two digits following the listing-name.

Since we are using RE anyway, we might as well use it to get us the actual text from the spans:
```

import urllib.request
import re

page = urllib.request.urlopen("http://www.yellowpages.com.au/search/listings?clue=auto+electrician&locationClue=Queensland&x=41&y=17")
text = page.read().decode("utf8")

pattern = re.compile('<span id="listing-name-\d{1,2}">(.*?)</span>')
for match in pattern.finditer(text):
	print(match.group(0))

```
Try that - it should work for you.
The changes we made are simple - the RE now looks for the ending span tag, and 'saves' all of the characters that appear before it:
[LIST]
[*]'.' - match any character
[*]'*' - any number of times
[*]'?' - but not greedily (otherwise, it would return all the text up until the last "</span>" in the document).
[*]The parentheses tell the RE parser to save the data found inside them.
[/LIST]

Then we just iterate through the results and print the data we saved.

If you work on the RE pattern some more, you should be able to make it return all of the interesting data (address, phone number...) with only a single run through the page.

---

### Post by Arndt on 2010-11-27
> **hopelessone said:**
> no sorry, here's what i got so far, but it doesn't loop and exits after the first find..
```
import urllib.request
import re

page = urllib.request.urlopen("http://www.yellowpages.com.au/search/listings?clue=auto+electrician&locationClue=Queensland&x=41&y=17")
text = page.read().decode("utf8")

sub = '<span id="listing-name-';
s = text.count(sub)
k = 1

while k!=s:
 t = ('<span id="listing-name-1">')
 t.replace('1', str(k))
 k=k+1

 
 before, tag, txt = text.partition(t) # before = text before the tag, tag = <span id>, txt = text after the tag

while txt:
 
 txt, endtag, after = txt.partition('</span>') #txt = text before the end tag, endtag = </span>, after = text after the endtag

 if endtag:
  print(txt) #this is the text between the tags
 else:
  raise ValueError('Missing end tag ' + txt) #no end tag to delimit the text

 before, tag, txt = after.partition(t) #repeat

print("finished")
```

Any ideas?
Thanks

I suggest you insert some print statements here and there to see what happens.

---

### Post by Cheesehead on 2010-11-27
The answer to your direct question is string slicing:

stringdame[starting_index:ending_index]
0 is before the first character
1 is after the first and before the second character
20 is after the 20th and before the 21st character
(blank) is after the last character
-1 is before the final character
-2 is before the next-to-final character (so you can count from the right, too) 

```

>>> fred = 'abcdefghijklmnopqrstuvwxyz 1234567890'
>>> fred[0:10]
'abcdefghij'
>>> fred[3:25]
'defghijklmnopqrstuvwxy'
>>> fred[18:]
'stuvwxyz 1234567890'
>>> fred[18:-1]
'stuvwxyz 123456789'
```


You can also use string.split ruthlessly to pare away big parts of strings, plus slicing and stripping for fine honing.

For example:```
import urllib.request
import re

page = urllib.request.urlopen("http://www.yellowpages.com.au/search/listings?clue=auto+electrician&locationClue=Queensland&x=41&y=17")
text = page.read().decode("utf8")

# Use .split ruthlessly to create a list of strings based on the delimiter we care about
text_list = text.split('<span id="listing-name-')    
del text_list[0]       # delete the useless list item before our first span tag
# You can also use slice lists: modified_text_list = text_list[1:]

for line in text_list:

    # Use the same string-to-list trick to get rid of the rest of each line
    name_list = line.split('</span>')
    name_plus_leading_trash = name_list[0]

    # Get rid of the remaining trash at the beginning of each string
    name = name_plus_leading_trash[3:]     # Slicing
    name = name.lstrip('>')                       # Stripping

    print(name)

print("finished")
```

Then you can wave a magic wand and combine some of these terms and reuse some variables. Keep it easy to read!```
import urllib.request
import re

page = urllib.request.urlopen("http://www.yellowpages.com.au/search/listings?clue=auto+electrician&locationClue=Queensland&x=41&y=17")
text = page.read().decode("utf8")

text_list = text.split('<span id="listing-name-')[1:]
for line in text_list:
    name = line.split('</span>')[0]
    name = name[3:].lstrip('>')
    print(name)

print("finished")
```



Of course, there are also great Python classes out there that will do all this parsing for you and simply return the list of results.

---

### Post by L815 on 2010-11-27
You can use range.

```

for i in range(1, len(str)):
    print i

```

---

### Post by hopelessone on 2010-11-29
THANK YOU ALL !!

I just got back to looking at this piece of code and I can sort of understand it, i'll read and re-read again so i can understand how python thinks..so i can do the same

and thanks Cheesehead!

---

