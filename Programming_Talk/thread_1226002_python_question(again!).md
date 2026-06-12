---
title: "python question(again!)"
date: 2009-07-29
forum: Programming Talk
---

### Post by flyingsliverfin on 2009-07-29
heres my code:

[PHP]#! /usr/bin/python

#interates through all the possibible combinations in a string


x = 0

y = 1

seq = []

seqlen = 0


seq = raw_input('enter a string that will be searched: ')

seqlen = len(seq)


while x < seqlen:

	while y <= seqlen:
		
		print seq[x:y]

		y = y + 1
	x = x + 1
[/PHP]

for some reason the first while loop seems to be ingnored... im on vacation and am working on this just on the side a little, and my brain is kinda tunred off or being fried, not sure witch, its REALLy hot here... can some1 tell me wahts wrong? also, when i say

x = raw_input('enter somehting')

and i dont assign X beforehand, what does x look after it has been assigned: a list, tuple, or string? and if anything but a string is the way i did it in my small program (the iterator) the way to do force it?

---

### Post by Tony Flury on 2009-07-29
My inbuilt python interpreter can't see anything wrong - but I will fire up python and try to get you an answer. As a hint to helping you find your own, a liberal sprinkling of print commands will often help you work out what is going wrong.

Watch this space

---

### Post by frunns on 2009-07-29
Been a while since I programmed, but I'm fairly sure you should move y=1 to just before the second while-loop. Let's say you have a string 'abcdefgh' won't this just print
```

ab
abc
abcd
abcde
abcdef
abcdefg
abcdefgh
bc (if you implement my change to the code)
bcd
bcde
etc...

```
I might be wrong though! Been a long time since I did any real coding...

---

### Post by Paul Miller on 2009-07-29
No, your first while loop is not being ignored.  It's just that when x > y, the value of
[php]
seq[x:y]
[/php]
is 
[php]
''
[/php]
So, the outer while loop is printing a bunch of empty strings, which isn't very exciting.

What were you trying to get it to print?  If I input "Just another Python hacker" at the raw_input() prompt, what should you expect to be printed, for instance?

---

### Post by StunnerAlpha on 2009-07-29
This is what you want to change your code to:
```

#! /usr/bin/python

#interates through all the possibible combinations in a string


x = 0

y = 1

seq = []

seqlen = 0


seq = raw_input('enter a string that will be searched: ')

seqlen = len(seq)


while x < seqlen:

	y = 1
	while y <= seqlen:
		print seq[x:y]

		y = y + 1
	x = x + 1  

```
I changed it like frunns said. It works with this output:
```

enter a string that will be searched: 12345
1
12
123
1234
12345

2
23
234
2345


3
34
345



4
45




5

```
To get rid of the spaces, I did this:
```

	while y <= seqlen:
		if seq[x:y] != '':
			print seq[x:y]

```
Hope this helps.

---

### Post by frunns on 2009-07-29
Ah, now I see the point of it too... :) Haha.

---

### Post by nvteighen on 2009-07-29
Now, as a task, rewrite that using **for...in**. It'll be much easier :)

---

### Post by veda87 on 2009-07-29
the code using for...in ....```
#! /usr/bin/env python

def seq():
        seq = []
        seqlen = 0

        seq = raw_input('enter the name:')
        seqlen = len(seq)

        for x in range(0,seqlen):
                for y in range(1,(seqlen+1)):   #to go till the last letter we are adding 1
                        print seq[x:y]


```

---

### Post by flyingsliverfin on 2009-07-30
right, got that, 

im on vacation with my family and the only computer availible is my mom's work laptop (she doesnt trust me to do much on it for that reason) (and cuz im 13) does any1 know a good text editor for python on mac? ive been doing it all on ubuntu and i just used Gedit...

---

### Post by smartbei on 2009-07-30
You can search google for some editors - the first result I found was: [http://wiki.python.org/moin/PythonEditors](http://wiki.python.org/moin/PythonEditors), which looks like a pretty good resource :-).

---

