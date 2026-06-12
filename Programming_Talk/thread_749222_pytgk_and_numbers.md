---
title: "pytgk and numbers"
date: 2008-04-08
forum: Programming Talk
---

### Post by christooss on 2008-04-08
I have writen program that calculates rent in our apartment(in python) but Im having problem porting it to pygtk.

I have writen funckiton
```

def callback_romies(self,widget,data):
		rommies = []
		entry_text1v1 = self.rommie1.get_text()
		rommies.append(entry_text1v1)
               print rommies
```

And it works flawlessly cause it gets text. Now I have column of gtk.entry fields that i will write number in too and than append it to different list.

if I use get_text() i will get [''1000' ,'1500'] when printing values of gtk.etnry fields but I want it to be [1000, 1500]

Any Ideas?

I looked thorugh [Gtk.entry]("http://www.pygtk.org/docs/pygtk/class-gtkentry.html#method-gtkentry--get-text") but I didn't find anything usefull.

---

### Post by tseliot on 2008-04-08
try with:
```
rommies.append(int(entry_text1v1))
```

---

### Post by christooss on 2008-04-08
numbers = map(int, mylist)

I did it with this code ^

I will use your suggestion too.

Thanks for the anwser

---

