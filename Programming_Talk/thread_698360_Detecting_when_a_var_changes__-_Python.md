---
title: "Detecting when a var changes  - Python"
date: 2008-02-16
forum: Programming Talk
---

### Post by oscrp on 2008-02-16
Hi!, I need to call function self.update() when the content of one variable changes. I tested with self.var.trace('w', self.update) but dont worked for me :/. What I need to do?

Thanks :)

---

### Post by xlinuks on 2008-02-16
Pretty weird, normally one uses getter/setter methods, a pseudo code would look like this:
```

var yourPrivateVar = 0;

public void setValue( var newValue ) {
 yourPrivateVar = newValue;
}

public int getPrivateValue() {
 return yourPrivateVar;
}

```

PS: Inside the method you do what you want before/after the update of the var takes place, you can even trace the call

---

### Post by Jessehk on 2008-02-16
> **oscrp said:**
> Hi!, I need to call function self.update() when the content of one variable changes. I tested with self.var.trace('w', self.update) but dont worked for me :/. What I need to do?

Thanks :)

I'm sorry if this is a stupid question (I am not familiar with **all** of Python's standard libraries), but how is *self.var* defined? Did you define a trace method? I ask because as far as I know, none exists for an object in Python.

---

### Post by lnostdal on 2008-02-16
this reminds me of a technique implemented by Cells [http://common-lisp.net/project/cells/](http://common-lisp.net/project/cells/)

here is some more info about Cells: [http://common-lisp.net/cgi-bin/viewcvs.cgi/cells/cells-manifesto.txt?root=cells&view=markup](http://common-lisp.net/cgi-bin/viewcvs.cgi/cells/cells-manifesto.txt?root=cells&view=markup)

..it's quite interesting, and there are two implementations of this idea for Python also (Cells is for/in Common Lisp) -- here is the one that seems most "alive" atm.: [http://peak.telecommunity.com/DevCenter/Trellis](http://peak.telecommunity.com/DevCenter/Trellis)

edit:
here is some more general information about this: [http://en.wikipedia.org/wiki/Dataflow](http://en.wikipedia.org/wiki/Dataflow)

---

### Post by Quikee on 2008-02-16
You could also do it like this:

[PHP]class Test(object):
	def __setattr__(self, name, value):
		object.__setattr__(self, name, value)
		if name == 'somevalue':
			self.someothervalue = getattr(self, name) * 100

t = Test()
t.somevalue = 10
print 'some value:', t.somevalue
print 'some other value:', t.someothervalue
t.somevalue = 20
print 'some value:', t.somevalue 
print 'some other value:', t.someothervalue
[/PHP]

---

### Post by oscrp on 2008-02-16
> **Quikee said:**
> You could also do it like this:

[PHP]class Test(object):
	def __setattr__(self, name, value):
		object.__setattr__(self, name, value)
		if name == 'somevalue':
			self.someothervalue = getattr(self, name) * 100

t = Test()
t.somevalue = 10
print 'some value:', t.somevalue
print 'some other value:', t.someothervalue
t.somevalue = 20
print 'some value:', t.somevalue 
print 'some other value:', t.someothervalue
[/PHP]

Thank you, It solved my problems :D

---

### Post by pmasiar on 2008-02-16
Python has generic way to [add getter and setter later](http://snippets.dzone.com/posts/show/954) by using property()

BTW if your problem is solved, please mark your thread as solved to help future searchers.

---

