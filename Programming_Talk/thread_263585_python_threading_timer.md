---
title: "python threading timer"
date: 2006-09-23
forum: Programming Talk
---

### Post by xrado on 2006-09-23
anyone programming in python?:) ..im a beginer

```
def hello():
	print "hello"
	t = threading.Timer(5.0, hello).start()

t = threading.Timer(5.0, hello)
t.start() 
```

i would like to make a thread which will repeat every 5 sec.
i done that...but when i exit gui form the tread is still running
and every 5 sec i get the output and i have to pres ctrl+c to end the program in console

i know i have to cancel it...i did that..but not working i get the errors like "AttributeError: 'NoneType' object has no attribute 'cancel'"

how can i solve this?

btw im seeking for good python forum...if anyone knows one

---

### Post by Tomosaur on 2006-09-23
The logical opposite of start() would be stop(), right?

---

### Post by xrado on 2006-09-23
actualy its t.cancel() ..but as i sad thats not working
t = threading.Timer(5.0, hello) ..runs only once

the problem is function hello wich call it self and new threads are defined with in... i tried also with global t..but cant get it working

there must be another way to do it

---

### Post by Tomosaur on 2006-09-23
I think I figured your problem out:

You are setting t to be a started timer:
t = threading.Timer(5.0, hello).start()

You need to be one level up - so t must be defined like this:
t = threading.Time(5.0, hello)

And then you may use:
t.start()
t.cancel()

as you so wish.

Can't believe I didn't spot that before :D


EDIT: On reading your last post, I'm not so sure I did solve that for you. Could you perhaps clarify what's happening again? The way I understood it is that you cannot find the attribute/method cancel(). The above solution should work for that, but if your problem is something different, I'm not sure :S

---

### Post by xrado on 2006-09-23
i know that..

t = threading.Timer(5.0, hello).start() ...makes execute function hello after 5 seconds...and that happens only once..but i need it to be run every 5 seconds...thats way i made function which do exactly that
```

def hello():
	print "hello"
	t = threading.Timer(5.0, hello).start()

t = threading.Timer(5.0, hello)
t.start()

```

function calls it self every 5 sec...the problem is now how to cancel threads that were made inside the function t.cancel cancels only outside thread...but function hello is continuing to call it self and making new threads

---

### Post by xrado on 2006-09-24
i solve it 
```

def hello():
 print "hello"
 global t 
 t = threading.Timer(5.0, hello)
 t.start()

t = threading.Timer(5.0, hello)
t.start()

```

i can call t.cancel() anytime ..and it works

---

