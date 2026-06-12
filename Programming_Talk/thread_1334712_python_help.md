---
title: "python help"
date: 2009-11-22
forum: Programming Talk
---

### Post by flyingsliverfin on 2009-11-22
so i was just writing a small program to warm up my brain after a long time of not programming with this:


```
while True:
	ask = raw_input('tell me something as a sentence: ')
	print ask
	asklst = ask.split(' ')
	print asklst
	length = len(asklst)
	randomize = ['guacamole','good day too you too', 'goo', ask, 'what???', 'somoene cant spell', 'bad grammar', 'idiot!', 'hm...', 'cricket']
	chose = random.choice(randomize)
	_if asklst[0][0] == asklst[0][0].lower_:
		print('you didnt capitalize your first word.')
		length = len(asklst)
		while True:
			if length <= 1:
				print('thats not a sentence!')
			else:
				break
			if length == 2:
				print('thats a veeeeeerrrrry looooooong sentence.')
				break
			if length >= 3:
				print(chose)
```

the underlined portion doesn't seem to work, or am i missing it completely? im sure there are some other things wrong too...

---

### Post by jeffathehutt on 2009-11-22
You forgot the parentheses on .lower()  :)

```
if asklst[0][0] == asklst[0][0].**lower()**:
```

---

### Post by flyingsliverfin on 2009-11-28
oh thx! 


glad the prgram isnt very long. it wouldve taken ages to find it :)

---

