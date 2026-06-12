---
title: "python string checking and modification"
date: 2009-02-16
forum: Programming Talk
---

### Post by djbushido on 2009-02-16
Ok, so this sounds stupid, but can't figure this out. Actually, is pretty stupid.

I am wanting to do a test for a string xxxx where the x's are a number. These are saved in a file, so I can't have the program count by itself up, I need to figure out what the biggest number is, the only problem being that there are a whole lot of other numbers. So I really  need to test for something like test-xxxx and have x increment by one for every file entry. So it would go like this
```
test-0001
Some Stuff...
test-0002
More Stuffs...
```
Etc.,Etc.
Any ideas, and thanks for taking the time to answer a n00bish question...

---

### Post by Can+~ on 2009-02-16
You could split in "test-" and get a list with two elements for each line. Lines that don't match won't have a second member ([1]) on said list.

[PHP]for line in numfile:
	try:
		print("number:",line.split("test-")[1].strip())
	except IndexError:
		pass[/PHP]

Other than that... you could check for other [string methods]("http://docs.python.org/library/stdtypes.html#string-methods"), or, if there's no other option, use [Regular Expressions]("http://docs.python.org/library/re.html").

---

### Post by djbushido on 2009-02-16
My idea was to search for "test-"+x where x is 1,2,etc. and if not found, use this. Is there a way to do this, or is it really that ineffective. Your way is kind of like that, but will be wading through hundreds of lines, rather than just scanning. Anyway, thanks for the tip. Will try if nothing else comes up.

---

### Post by Can+~ on 2009-02-16
> **djbushido said:**
> Your way is kind of like that, but will be wading through hundreds of lines, rather than just scanning. Anyway, thanks for the tip. Will try if nothing else comes up.

Of course you have to transverse through hundreds of lines, the fact that you wrote in the OP "Some Stuff..." makes me think it's a sequential file, where "Some Stuff" could be any length of text.

In that case, you're condemned to use sequential reading, "just scanning" doesn't mean anything, computers can't tell where exactly a match occurs unless they read throughout the whole text.

Notice that this is not a limitation of Python, nor a problem in computers in general (well..), the problem lies in how you define the file. If you want to store text allowing quick access through a title ("test-x"), you're better off with a defined block-size and using random access, or using a database (which is that already implemented).

---

### Post by djbushido on 2009-02-17
Sorry, I meant that I know that I have to wade through the entire thing.
Anyway, what I need to do is know the xxxx portion of "test-xxxx". I need the xxxx in a variable. So do I just use your method and
```
try iteration = line.strip("test-")[1].strip()
except IndexError:
    pass
iteration = int(iteration)
```

---

