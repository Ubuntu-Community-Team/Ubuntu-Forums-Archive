---
title: "to enclose string in a variable with &quot;&quot;&quot; and &quot;&quot;&quot;"
date: 2012-10-07
forum: Programming Talk
---

### Post by madhu91 on 2012-10-07
hi.. 
i have a big html content assigned to a variable. 
its something like this.
import mechanize
import cookielib
import re
br=mechanize.Browser()
br.set_handle_robots(0)
br.set_handle_refresh(0)
a=br.open("SOME URL").read()
#the variable 'a' contains the necessary html
# now i need to search for a string something like this
#<span class="xyz"></span> Some content here </div>
#i have written a regular expresssion like this
p=re.findall('\<span\ class\=\"xyz\"\>\<\/span\>([ \t\n]*)([a-zA-Z]*([ ])([a-zA-Z]*)([ ])([a-zA-Z])*([ \n]*)\<\/div\>',a)
now if i print p, it shows an empty array.
i googled and i found out that the contents of the variable 'a' should be enclosed with """ and """ so that the regular expression is matched. How do i enclose the contents of the variable 'a' with """ and """


any suggestions/help are very well appreciated.! thank you.. :)

---

### Post by oldos2er on 2012-10-07
Moved to Programming Talk.

---

### Post by Majorix on 2012-10-07
Regex will work with all kinds of strings. Text enclosed in """ and """ are strings themselves too, so it should work with them too. I suggest trying out a few regexes in the interactive environment.

---

### Post by epicoder on 2012-10-07
Once a variable contains a string, you don't need to worry about quotes. Your problem is your regex- Python is attempting to expand the backslashes to special characters. To avoid this, you can use a raw string:
```
p=re.findall(**r**'\<span\ class\=\"xyz\"\>\<\/span\>([ \t\n]*)([a-zA-Z]*([ ])([a-zA-Z]*)([ ])([a-zA-Z])*([ \n]*)\<\/div\>', a)
```
The r before the string makes it a raw string, which will cause Python to interpret the string literally and treat backslashes as normal characters rather than escape sequences.

---

### Post by greenpeace on 2012-10-08
looks like you're parsing HTML... I've always found the beautifulsoup module to be a huge help in this... [http://www.crummy.com/software/BeautifulSoup/#Download](http://www.crummy.com/software/BeautifulSoup/#Download)

It makes it really easy to "walk" the HTML tree, picking the bits you want.  It also handles malformed HTML really nicely, and leaves your code nice and clear (easier to read than regex I think.. :) )

Some examples (I have assumed in both that there are more than one <span> with this class)

if you want to extract the text that comes after (outside) the <span> with class=xyz

```
#!/usr/bin/python
from bs4 import BeautifulSoup

html = '<div><span class="xyz"></span>Some content here</div>'   
soup = BeautifulSoup(html)

# find all <span> with class=xyz
tags = soup.div.find_all("span", "xyz")

for t in tags:
  print t.next_sibling
```

However, if we were to assume that the text we want falls inside the <span> with class=xyz we can use the following code to identify it:

```
html = '<div><span class="xyz">Some content here</span></div>'
soup = BeautifulSoup(html)

# find all <span> with class=xyz
tags = soup.find_all("span", "xyz")

for t in tags:
  print t.text
```

hope that helps!

g

---

### Post by madhu91 on 2012-10-08
well.. Beautiful soup solved the problem. :) however i wanted to solve it using regular expression. anyhow, thanks! :)

---

### Post by Majorix on 2012-10-08
Golden Rule Of Programming: Don't reinvent the wheel. You can find many more exercises to learn regexes :)

---

### Post by greenpeace on 2012-10-08
+1 for not reinventing the wheel!

For programming tasks like this, there is nearly always someone far smarter than me that has already solved the problem!


...don't forget to mark the thread as "solved" if you're happy! :)

---

### Post by trent.josephsen on 2012-10-08
> **greenpeace said:**
> there is nearly always someone far smarter than me that has already solved the problem!

I like this. I may steal it. "The Programmer's Mantra" or some such. :D

---

### Post by Vaphell on 2012-10-08
> well.. Beautiful soup solved the problem. however i wanted to solve it using regular expression. anyhow, thanks! 

regexes used to parse stuff belong in the 'quick and dirty hack' category (and sometimes 'not so quick' if your needs are very specific) because they are oblivious to language rules. In some simple scenarios they work, in some they don't. Tools able to deal with syntax trump dirty hacks any day.

---

