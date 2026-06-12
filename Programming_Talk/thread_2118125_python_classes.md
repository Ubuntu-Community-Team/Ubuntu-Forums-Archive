---
title: "python classes"
date: 2013-02-20
forum: Programming Talk
---

### Post by wingnut2626 on 2013-02-20
Hi guys, here is the code that i am working on today:


```
class Song(object):
#creates a new class of Song that has an object argument

		
		
		def __init__(self, lyrics):
		#for now just understand that this needs to be in the class
			self.lyrics = lyrics
		#self is an empty object, that python creates for modification.
		def sing_me_a_song(self):
			#just a function definition.  Notice how self is in the argument placeholder.
			for line in self.lyrics:
				#creates a loop 
				print line
				
happy_bday = Song(["Happy birthday to you",
					"I don't want to get sued",
					"So I'll stop right there"])
					
bulls_on_parade = Song(["They rally around the family",
						"With pockets full of shells"])
						
happy_bday.sing_me_a_song()

bulls_on_parade.sing_me_a_song()
```
					
Im just confused on the whole __init__ and 'self' thing.  Could someone break it down for me or point me in the right direction to understand it?  I'm learning it from learnpythonthehardway.org

---

### Post by Tony Flury on 2013-02-21
> **wingnut2626 said:**
> Hi guys, here is the code that i am working on today:


```
class Song(object):
#creates a new class of Song that has an object argument
.... code snipped

```
					
Im just confused on the whole __init__ and 'self' thing.  Could someone break it down for me or point me in the right direction to understand it?  I'm learning it from learnpythonthehardway.org

ok - in basic terms - __init__ is the initialiser - if it exists for a class it is called immediately after an instance is created to allow the programmer to initialise the object - set some attributes to some initial values - etc. The __init__ method does not return anything so if you encounter errors then your code will need to handle the error or raise and exception.

self is a special varible (in fact it is just a special name) which refes to the specific instance of that class. What this means in practice is that your code can ceate multiple instances of the same class - and when you call a method on an object, the self argument which is passed to to the method is reference to the object.

```

class a(object):
    def __init__(self, initial):
        self.a = initial
        print id(self)
    def method1(self, value):
        print id(self)
        self.a = self.a + value

# Create an instances of a
o1 = a(15)
# This should be the same id as printed from __init__
print id(o1) 

# Create a second instance
o2 = a(5) 
# This should be the same id as printed from __init__
print id(o2)

# See what the initialiser did
print o1.a, o2.a # should print 15 and 5
o1.method1(5)
print o1.a, o2.a # should print 20 and 5

```

The above code demonstrates that each time you create a new object (in my case by calling a(<somevalue) ), it creates a new object with a new id.

the __init__ function, and all other methods defined on your class, are passed the object id as the first parameter (and it is strong convention that this parameter is called self), which means that everytime you use self.<something> within your methods you are refering to an attribute on that specific instance - meaning you can have hundreds of objects each with their own value of "a" attribute, or in your case, hundreds of song objects each with their own lyrics.

I hope that helps

---

### Post by limkokhole on 2013-02-21
I try my best to answer your queston:

1. Assume **Song** is your class name

2. Firstly, you have to **create a new instance(can have many)**(or you can said it a clone) in order to work with this class. Create instance also means **initializing class**.

3. __init__ method would process **compulsory when you create instance**. In your example, it would do **self.lyrics = lyrics**.

4. What does **self.lyrics = lyrics** means? I prefer explain by python comments, 

```
		def __init__(self, lyrics):
                        print lyrics #the lyrics is local variable, use inside __init__ method only!!!
			self.lyrics2 = lyrics #self.lyrics2 is global variable inside this class, not outside of class

                #Call by your example, happy_bday.print_lyrics()
                def print_lyrics(self):
                    print lyrics #i would error!
                    print self.lyrics2 #it works!



```

Another important conceptual is global, means you can access the variable outside AND inside the class.

```
class Song(object):
	def __init__(self, lyrics_list):
		global global_lyrics_list 
		global_lyrics_list = lyrics_list
		print "## print global_lyrics_list1: ", global_lyrics_list #it works inside same method of this class!
		self.instance_lyrics_list = global_lyrics_list

	def sing_me_a_song(self):
		for line in self.instance_lyrics_list:
			print line

	def print_lyrics(self):
	    print "## print global_lyrics_list2: ", global_lyrics_list #it works inside different method of this class!
	    print self.instance_lyrics_list #it works inside different method of this class!
				
happy_bday = Song(["Happy birthday to you", "I don't want to get sued",])
	
happy_bday.print_lyrics()

print "## print global_lyrics_list3: ", global_lyrics_list #it works outside the class!
```

#One important thing, you see both "global global_lyrics_list "and "global_lyrics_list = lyrics_list" inside __init__() method or not? If you didn't declare the variable as global(means global global_lyrics_list), AND you already put global_lyrics_list outside of the class as global(default is global if outside of the class), you would unable to do assignment like "global_lyrics_list = lyrics_list"


When to use **globals **or **self.** is depends on your needs. Normally, **if you want to change the value of variable**, you using **self.**. However, there still some cases i prefer using global. Such as pass the variables from main python file, you may using **print_lyris = sys.modules['__main__'].print_lyris**, then print_lyris(global) method can access anyway inside child files.


Another example is:

```
global_lyrics_list = ["Happy birthday to you", "I don't want to get sued",]
class Song(object):

        instance_lyrics_list = global_lyrics_list
        number_example = 123 #same effect as **self.number_example = 123** inside __init__()

	def __init__(self):
		pass

	def print_lyrics(self):
	    print self.instance_lyrics_list #it works!
            print self.number_example #it works!
				
happy_bday = Song()

happy_bday.print_lyrics()
```

One more thing, **valueA = sys.modules['__main__'].valueA** is global, and global is hard to control the variable if you need to change/manipulate the value. If you assign valueA=5 on child file, it didn't guarantee parent file's valueA would synchronize change to 5. So you may try pass **self** as arguments to other file.

Example your file, hallo.py:

```
class SONG:
        refresh = False
        def sing(self):
            print self.refresh
	def print_lyrics(self):
	    import hallo2
            other_file_class = hallo2.videos()
            other_file_class.yahoo("my name is limkokhole", startindex=1, clon=self)
            #put args before kwargs #**self** should pass as last argument(i forgot the reason why)

s = SONG()
s.print_lyrics()
```

Inside other file, hallo2.py:

```
class videos:
    def yahoo(self, my_name, startindex=0, clon=None):
        if clon is not None:
            clon.refresh = True
            clon.sing() #it would print True if run hallo.py
```

it would print **True** if run hallo.py


Now you should know **self** is so important on production(got many files and many developers). Understand **global** also would give you big picture compare with **self**.

Cheers :)

[http://limkokhole521.blogspot.com]("http://limkokhole521.blogspot.com")

---

