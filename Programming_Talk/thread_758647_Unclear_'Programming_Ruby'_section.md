---
title: "Unclear 'Programming Ruby' section"
date: 2008-04-18
forum: Programming Talk
---

### Post by Caduceus on 2008-04-18
I've spent nearly 30 minutes trying to decipher this:

[PHP]class MyLogger
	private_class_method :new	
	@@logger = nil		
	
	def MyLogger.create
		@@logger = new unless @@logger	
		return @@logger
	end
end[/PHP]

I understand private_class_method (that's self-explanatory), but can anyone walk me through the class line-by-line and tell me what it does and why? The explanation in the book isn't clear (I'll post it if need be).

---

### Post by mssever on 2008-04-18
This is similar to the official documentation: ```
ri private_class_method
```
If for some reason you wanted to prevent people from calling YourClass.new, you'd use this. You'd of course need a method that people could call to get a new instance.

This particular class ensures that there is only ever one instance of MyLogger. If there isn't one yet, MyLogger.create creates and returns a new one. If one does exist, then MyLogger.create returns the existing instance.

---

### Post by Caduceus on 2008-04-18
Thanks, I can finally move on now I'm sure on what it means!

---

### Post by geraldm on 2008-04-18
As it stands, it is non-working code.

Every attempt to create a new class instance fails as it is written, because @@logger is assigned nil before new is called, and it must be non-nil to allow new to be performed the first time.

There should be other methods to have a working class code.

Gerald

---

### Post by skeeterbug on 2008-04-18
FYI this is the singleton design pattern (if the book didn't already mentioned it). Read more about it here:

[http://en.wikipedia.org/wiki/Singleton_pattern]("http://en.wikipedia.org/wiki/Singleton_pattern")

---

### Post by mssever on 2008-04-18
> **geraldm said:**
> As it stands, it is non-working code.

Every attempt to create a new class instance fails as it is written, because @@logger is assigned nil before new is called, and it must be non-nil to allow new to be performed the first time.

There should be other methods to have a working class code.
Did you test it? It DOES work. I just ran it as written. There's nothing wrong with @@logger being nil to begin with. The first time MyLogger.create is called, an instance is created and assigned to @@logger. There's nothing wrong with the code.

EDIT: FWIW, the similar class given in the ri doc for private_class_method warns that this approach isn't threadsafe.

---

### Post by crush304 on 2008-04-18
iirc @@ is used for a class variable (it is the same in every instance of the class)

the example code blocks you from using the new method to initialize a class and forces you to use the create method

the first time you call create, it calls the new method, all other times it returns the class you created the first time

for example

```
class MyLogger
    private_class_method :new    
    @@logger = nil        
    
    def MyLogger.create
        @@logger = new unless @@logger    
        return @@logger
    end
end  

a=MyLogger.create
b=MyLogger.create

puts a.to_s
puts b.to_s
```

results in 

```
#<MyLogger:0x2ae17098a018>
#<MyLogger:0x2ae17098a018>

```

a and b are the same

---

### Post by Caduceus on 2008-04-19
skeeterbug - It says that in the book, yes. It also mentions the built-in Singleton pattern.

mssever - It says in small print it's not thread safe, yes.

Thanks for the replies everyone!

---

