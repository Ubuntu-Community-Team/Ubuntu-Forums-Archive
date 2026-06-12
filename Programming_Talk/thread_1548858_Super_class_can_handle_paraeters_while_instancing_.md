---
title: "Super class can handle paraeters while instancing subclass?"
date: 2010-08-09
forum: Programming Talk
---

### Post by koala114 on 2010-08-09
I just wonder how super class can take over paraeters while instancing subclass without __init__. 
Does super class implicitly invoke __init__ itself?
```
class Processor:
	def __init__(self, reader, writer):
		self.reader = reader
		self.writer = writer
	def process(self):
		while 1:
			data = self.reader.readline()
			if not data: break
			data = self.converter(data)
			self.writer.write(data)
	
	def converter(self, data):
		assert 0, 'converter must be defined'

class Uppercase(Processor):
	def converter(self, data):
		return data.upper()

if __name__ == '__main__':
	import sys
	Uppercase(open('spam.txt'), sys.stdout).process()

```

---

### Post by Bachstelze on 2010-08-09
In Python, a subclass does not implicitly call the superclass's constructor, you have to do it explicitly:

```
class Uppercase(Processor):
        def __init__(self, reader, writer):
                Processor.__init__(self, reader, writer)
	def converter(self, data):
		return data.upper()

```

---

### Post by koala114 on 2010-08-09
[QUOTE=Bachstelze;9696629]In Python, a subclass does not implicitly call the superclass's constructor, you have to do it explicitly:
QUOTE]

How does the script I posted work? 
Especially ```
Uppercase(open('spam.txt'), sys.stdout).process() 
```
Uppercase even have no __init__

Thx

---

### Post by Bachstelze on 2010-08-09
Actually, since Uppercase doesn't have a constructor, the constructor of the superclass gets called instead, so your code and the one I posted are equivalent.  If you just put a no-op constructor, however:

```
class Uppercase(Processor):
    def __init__(self):
        pass

    def converter(self, data):
        return data.upper()

```

It will not work.

---

