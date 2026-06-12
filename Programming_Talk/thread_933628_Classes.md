---
title: "Classes"
date: 2008-09-29
forum: Programming Talk
---

### Post by luke77 on 2008-09-29
Hi guys,

I'm teaching myself python by working through the MIT Opencourseware computer science site, and I'm at the point in the class where they start to deal with classes and object oriented programming. Basically, I'm trying to work through a problem and am confused both HOW to use a class structure and WHY it is even beneficial. Here is a link to the problem I am dealing with:  

[http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/6-00Fall-2007/Assignments/index.htm](http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/6-00Fall-2007/Assignments/index.htm)

It is problem 7, part one. The problem has to deal with parsing feeds from Google and Yahoo's RSS news feeds. I have been messing around with it and basically confusing myself more because I don't know how to develop a good "top down" structure. I've deleted everything that I'm unsure about and have pasted a very, very bare bones structure at the end of this post. I'm unsure about a number of things:

First, the problem says to write a constructor that takes 'guid, title, subject, link, and summary' as arguments and stores them appropriately. I don't know how to do this - should the constructor go inside the class definition, or outside, ...? And specifically, what does the constructor do? If I fill in the methods (getGuid, getTitle, etc) with code that assigns the given variables within each method, then what is the purpose of writing a constructor? In other words, it seems like the problem is asking me to write both a constructor and methods that do the same thing. And honestly, I'm not really sure how to do either one. 

To elaborate, if I was simply asked to do this problem without using classes, I'd simply write a function:

def NewsStory (guid, title, subject, link, summary) 

that would store these arguments in a list or something and each list would represent an individual newstory. So, you could say 

story1=NewsStory (1234, 'Title', 'Story subject', 'www.yahoo.com/1234', 'This is a news story') and return a list with this data. This is pretty basic. My question, I guess, is how to write a class structure that stores this data? And then, once the class structure is created, how to pass variables the way you would with a standard function definition. Thanks for any suggestions, and below is the bare bones outline I have written.



import feedparser

class NewsStory:
    def getGuid():
        
    def getTitle():
        
    def getSubject():
        
    def getSummary():
        
    def getLink():
        




story = NewsStory()

def process (url,type=0):
    d = feedparser.parse(url)
    for i in range(0,len(d.entries)):

---

### Post by snova on 2008-09-29
Classes are for bundling data and things to do with that data in one neat little package. Instead of calling a function and passing it the data as a parameter:

```
function( data )
```

You treat the operation as part of the data, much like addition is an operation on numbers:

```
data.function()
```

On the one hand, they can make things simpler if you write them well. On the other hand, sometimes they just make things unnecessarily complicated.

The contructor goes inside the class. It's purpose is just to initialize everything within the class when you create it, so that the data is in a known state. It's only called once, at creation time.

The methods in question are for getting and setting individual values, whereas the constructor is for setting up the entire thing.

Towards your example with the list-returning function, classes aren't much different. But instead of accessing the guid as instance[0], you access it as instance.getGuid().

The outline looks good so far.

---

### Post by pmasiar on 2008-09-29
If you are learning by yourself, consider skipping **designing** your own classes - just learn how to use existing classes from libraries. Leter, when you gain experience  and confidence, you can learn OOP. Python is good language for OOP, but OOP itself is rather tricky subject, and for quire a while for your own use dictionaries would be sufficient.

Don't get bogged down, for a beginner writing and debugging code is more important than learning abstract design patterns, like OOP. Of course you have to promise to return and learn them later :-)

---

### Post by luke77 on 2008-09-29
Ok, I guess I understand that conceptually, I'm just having trouble translating it into a program. I'll try to explain using my outline. Looking ahead to part 2 and 3, the purpose of the program is to take a list of NewsStory objects and print each one (you can see what they want to do on the page I linked, but basically they just want to print the information for each news story by running a function printStories(StoryList). So what I want to do with class NewsStory is, for each instance, store the guid, title, etc. for the instance (I think). But, assuming this is accurate, how do I pass multiple variables for an instance?

For example, using your terminology, you pass data using data.function() rather than function(data). But when I have multiple data points, I don't think it would be correct to write guid.title.subject.summary.link.NewsStory; and, even if it was, there would be no label (eg. 'story1') associated with the instance. 

Next, when you say the constructor's purpose is 

> to initialize everything within the class when you create it, so that the data is in a known state. It's only called once, at creation time.

Do you mean it's only called once, total, or it is called once for each instance that is passed through? And what needs to be initialized in the class that is not taken care of by the individual functions within the class? I mean, presumably, def getGuid(): will set the given Guid for each instance, and getTitle(): will do the same for the title, etc. What remains to be done, that the constructor would do? This is what I mean when I say it seems like they're asking to do the same thing twice.

---

### Post by meanburrito920 on 2008-09-29
constructors are called automatically when you make a new instance of a class. So for instance, the class

```

class TestClass:
    def __init__(self, text):
        print text

test = TestClass("Hello World")

```

would print
```

Hello World

```

The purpose of classes are to allow for 'black box' programming methodology, which basically means that for any part A of your program that uses a function from part B, part A doesn't care how part B does it, just that it gets done. Classes allow this to happen easily by abstracting away blocks of code in favor of actors, or objects, performing actions, or methods.

---

### Post by Tony Flury on 2008-09-30
Another source of confusion i think you have is when you refer to the functions in the class such as getTitle and getGuid.

In OOP these functions are normally called methods - but that is really beside the point.
Also in OOP terminology individual data items (such as the Title, Guid, summary) are called attributes.

In one of your posts you say : 
[QOUTE]
I mean, presumably, def getGuid(): will set the given Guid for each instance, and getTitle(): will do the same for the title, etc. What remains to be done, that the constructor would do? This is what I mean when I say it seems like they're asking to do the same thing twice. 
[/QUOTE]

in a normal naming convention a method called getGuid would fetch an attribute value from an object so that functionality outside the class could use that value, and so this is very different from a constructor.

in general a class has a few different types of functionality which is associated tightly with the attributes : 
[LIST]
[*]Constructor : initialises an instance of an class and populates the attributes of that instance with either specific or defaulted data
[*]method : a "function" associated with and defined as part of the class that does some kind of operation on a class
[*]Destructor : a special method that is called when the instance is deleted, so that any tidy up is completed correctly
[/LIST]

There are many different types of method - but a few that you might encounter are : 
[LIST]
* set : normally called set<AttributeName> - a method designed to set an attribute on a given instance.
* get : normally called get<AttributedName> - a method designed to retrieve an attribute on a given instance.
* operator : a method designed to perform some form of operation on an instance (for example say add or multiple two objects or print an object instance to a stream)
[/LIST]

In theory one could design your object without using a constructor and by using whole set of set Pperators but it is not considered to be good design practice (you might miss a set call out that is actually needed, and it is far more difficult to validate that your object has been correctly initialised, as you can't know in what order the sets will be called).

In your case then - you have a Class called NewStory with attributes of guid, title, summary etc - each individual newsStory will becomes an instance of that class, each with its own guid, title, summary, url attribute values.

I would expect your class to define a constructor and probably a desctructor, and at least one method to output that news story in the right format - you may have some get and set Attributes - but you might not need them.

your code would then create a new instance for each news story it found, store the news stories in an array or similar, and then it can go along the array calling the output method for each instance - without neccessarily having to worry about the title or anything else.

---

### Post by pmasiar on 2008-09-30
getX and setX getters and setters are part of C++/Java orthodoxy. Python prefers simpler solutions, and unless you have real (supported by business logic) arguments to hide your data, you just make them accessible. It works just fine in 95% of the cases, which would be 100% of what beginners do.

Of course is good to know flavors of OOP what other languages use, but it's not necessary for Python. Yes, I know it is heretic and huge simplification: but goal is to make beginner's life easier by avoiding OOP mumbo-jumbo.

---

### Post by pp. on 2008-09-30
> **pmasiar said:**
> getX and setX getters and setters are part of C++/Java orthodoxy. (...) unless you have real (supported by business logic) arguments to hide your data, you just make them accessible. 

I do not consider this good advice. You will work much more if you decide in the course of the project that attributes are to be represented in a different way or that setting or getting values should be tightly coupled to some side effects.

Your needs might vary, of course. If you're just writing a quick and dirty scriptlet, you can easily dispense with most of the well-known sound software engineering solutions.

---

### Post by luke77 on 2008-09-30
Thank you all for the help. I am still having problems understanding how to translate this into code, though. Here is the additional code I have written based on the thread so far. For now I am ignoring everything about the problem except creating a proper class structure, so I'm focusing on creating one specific instance, rather than worrying about multiple stories at this point. I am still not confident that this is correct and I'm not sure what to put in the __init__ (constructor) function, so feel free to rewrite what I've written. Thanks again.

```
import feedparser

class NewsStory:
    
    def __init__(self):
        ??????????
        
    def getGuid(a):
        self.guid = a
        
    def getTitle(b):
        self.title = b

    def getSubject(c):
        self.subject = c

    def getSummary(d):
        self.summary = d

    def getLink(e):
        self.link = e

a='1234'
b='Story Title'
c='Subject'
d='Summary'
e='www.yahoo.com/1234'


story1 = NewsStory(a,b,c,d,e)
```

---

### Post by gomputor on 2008-09-30
I'm not pretty sure if I understand you fully in what you wanna do :), I haven't got the time to look into your link to the site, but maybe is that what you wanna do? :
```
import feedparser

class NewsStory(object):
    
    def __init__(self, guid, title, subject, summary, link):
        self.guid = guid
        self.title = title
        self.subject = subject
        self.summary = summary
        self.link = link
        
    def getGuid(self):
        return self.guid
        
    def getTitle(self):
        return self.title

    def getSubject(self):
        return self.subject

    def getSummary(self):
        return self.summary

    def getLink(self):
        return self.link

a='1234'
b='Story Title'
c='Subject'
d='Summary'
e='www.yahoo.com/1234'


story1 = NewsStory(a,b,c,d,e)

```

---

### Post by luke77 on 2008-09-30
I guess so, but if  you use this structure I'm confused as to the purpose of the def getGuid(), def getTitle(),etc. functions. It seems like you've defined all of these things in the constructor, and that the extra functions are unneccesary. 

Below I've written the code that accomplishes the tasks in Part2 and 3 of the problem, without using classes, and then below that I've written (attempted) code trying to do the same thing using the class structure you suggested above. Each story will be represented by an instance in the class and then passed to the printStories function. I'm still not confident that this is "correct", so please look over the code and suggest improvements or tell me where I'm wrong.

Code 1 (no classes):

```
import feedparser
from project_util import translate_html




def process (url,type=0):
    
        guid=d.entries[i].guid
        title=d.entries[i].title
        subject=d.entries[i].title
        summary=d.entries[i].description
        link=d.entries[i].link
        storylist=[guid,title,subject,link,summary]
        return storylist




def printStories(storyList):
    
    print "GUID: ", translate_html(storyList[0])
    print
    print "TITLE: ", translate_html(storyList[1])
    print
    print "SUBJECT: ", translate_html(storyList[2])
    print
    print "LINK: ", translate_html(storyList[3])
    print
    print "SUMMARY: " 
   
    print translate_html(storyList[4])

    

d = feedparser.parse('http://news.google.com/?output=rss')

for i in range (len(d)):
    print 'Story',(i+1),':'
    print

    storyList = process ('http://news.google.com/?output=rss')

    printStories(storyList)
```

Code 2 (with classes):

```
import feedparser
from project_util import translate_html

class NewsStory(object):
    
    def __init__(self, guid, title, subject, link,summary):
        self.guid = guid
        self.title = title
        self.subject = subject
        self.summary = summary
        self.link = link
        
    def getGuid(self):
        return self.guid
        
    def getTitle(self):
        return self.title

    def getSubject(self):
        return self.subject

    def getSummary(self):
        return self.summary

    def getLink(self):
        return self.link




def process (url,type=0):
    
        guid=d.entries[i].guid
        title=d.entries[i].title
        subject=d.entries[i].title
        summary=d.entries[i].description
        link=d.entries[i].link
        storylist=[guid,title,subject,link,summary]
        return storylist


def printStories():
    
    print "GUID: ", translate_html(i.guid)
    print
    print "TITLE: ", translate_html(i.title)
    print
    print "SUBJECT: ", translate_html(i.subject)
    print
    print "LINK: ", translate_html(i.link)
    print
    print "SUMMARY: " 
   
    print translate_html(i.summary)
    print

d = feedparser.parse('http://news.google.com/?output=rss')

for i in range (len(d)):
    print 'Story',(i+1),':'
    print

    storyList = process ('http://news.google.com/?output=rss')
    i=NewsStory(storyList[0],storyList[1],storyList[2],storyList[3],storyList[4])
    
    printStories()



```

---

### Post by pmasiar on 2008-09-30
> **luke77 said:**
> I am still having problems understanding how to translate this into code, though. Here is the additional code I have written based on the thread so far.

Your getters are in fact setters. This **exactly** proves my point, that instead of OOP orthodoxy OP would be better served using common sense. 

[http://www.voidspace.org.uk/python/articles/OOP.shtml](http://www.voidspace.org.uk/python/articles/OOP.shtml)  - OOP without getter and setters, plain and simple.

I now rest my case.

---

### Post by gomputor on 2008-09-30
> **pmasiar said:**
> Your getters are in fact setters. This **exactly** proves my point, that instead of OOP orthodoxy OP would be better served using common sense. 

[http://www.voidspace.org.uk/python/articles/OOP.shtml](http://www.voidspace.org.uk/python/articles/OOP.shtml)  - OOP without getter and setters, plain and simple.

I now rest my case.

But the OP said that this is a work that must be done with a Class with

getGuid
getTitle
getSubject
etc....

inside.
(Or am I wrong?)
You want him to do it without a Class or without the get methods,
that's all right with me :)

---

### Post by pp. on 2008-09-30
> **luke77 said:**
> I'm teaching myself python by working through the MIT Opencourseware computer science site, and I'm at the point in the class where they start to deal with classes and object oriented programming. Basically, I'm trying to work through a problem and am confused both HOW to use a class structure and WHY it is even beneficial.

What tutorials have you read up to now? After reading this thread several times over (as well as another thread by you), I think you might profit by some good introductory text which explains class basics. This forum's stickies hold a treasure trove of information for people like you who want to learn how to program.

---

### Post by luke77 on 2008-09-30
I started by reading the "Intro to Python" book on wikibooks, and then I moved on to "How to think like a computer scientist: Learning with Python" on this site:

[http://www.greenteapress.com/thinkpython/thinkCSpy/html/index.html](http://www.greenteapress.com/thinkpython/thinkCSpy/html/index.html)

My problem is that it's easy to read a tutorial, but relying only on the examples in the tutorials or even textbooks doesn't reinforce the material, which is why I'm trying to work my way through the MIT problems. Alternate suggestions are welcome and appreciated.

---

### Post by Tony Flury on 2008-10-01
Another point luke

If you look at your code, and the code gomputor sent you, you will see one fundamental difference which i had hoped that my earlier post had tried to explain - sorry that my explanation was not clear enough.

Anyway - to summarise the difference between the code that was posted : in your example

```

    def getTitle(b):
        self.title = b

```

and in gomputor's 
```

    def getTitle(self):
        return self.title

```

Your code actually defines the expected functionality of a Set type Method - it sets the value of the title Attribute. I think I can understand why you think what you wrote is a get Method - it is the class "getting" the attribute value - but the common naming convention is to makes the name sensible to the things that are calling your methods - so in this case a program using your class as you wrote it would call your getTitle method so it could actually set the title attribute - and therefore the name is confusing.

what gomputor posted is the correct functionality for a conventional get method - i.e. the calling code (that uses your class) is getting the value of the attribute from your class.

You probably recognise that these are just conventions (and therefore can be broken - it is after all perfectly possible to write a class where all the methods are named as it were looking out from the class (i.e. what is the class doing to the application). I would suggest though that this will actual be potentially confusing to other people (and eventually to yourself) as most classes and methods are named using an inward convention (i.e. what is the application doing to the class).

Since you are still learning, now is a good time to learn these conventions - they make life so much easier.

---

### Post by luke77 on 2008-10-01
Thanks guys. I understand the structure now; I guess I just didn't understand that things are written a certain way to follow convention and make it easier to understand. Also, part of my confusion arose because I was looking ahead to part two of the problem set, which is problem 8 on this page:

[http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/6-00Fall-2007/Assignments/index.htm](http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/6-00Fall-2007/Assignments/index.htm)

Again, my confusion isn't really with the code per se, it's more understanding how things are structured together and why. 

For example, in part one we created a class NewsStory, so that we can generate instances (individual stories) that share certain characteristics. So we can create story1, story2, story3, each of which are instances of the NewsStory class.

Where I get confused, though, is when I look to part 2 of the problem, which makes use of these instances to test for triggers. It asks us to define a Trigger class that takes a story as input and returns True if a trigger is in the story. The Trigger class is below, and it returns True for all stories:

```
class Trigger: 
def evaluate(self, story):
"""
 Returns True if an alert should be generated
for the given news item, or False otherwise.
""" 
return True
```


But we want to create new classes that are subclasses of the Trigger class, that will "fire" when a story contains the keyword. As I understand it, the basic structure will look like this:
```

class Trigger
def evaluate(self, story):
return True

class TitleTrigger(Trigger):
def evaluate(self,story)
if self in story:
return True


class SubjectTrigger(Trigger)
...
class SummaryTrigger(Trigger)
```

This is where my understanding breaks down. Say we have three instances of the NewsStory class: story1, story2, story 3, each of which has several variables assigned to it: GUID, Title, Link, Summary, and Description. We also have (or will have) a separate class Trigger, with several subclasses. Intuitively, it seems like we need to pass each instance of the NewsStory class through each subclass of the Trigger superclass, but I'm unsure how (or if you can) pass one class through another class. I know how to call the variable in question for each instance (eg. story1.Title will call the Title for the first story), which would lead to the following code:

```

triggerword= Trigger()
triggerword.evaluate(story1.Title)
```

True will be returned if the trigger is in the title of the story. But clearly this will not work as written because it doesn't specify which "evaluate" function to use (should it be the one in the superclass, or the one in the TitleTrigger class, or the one in the SubjectTrigger class, etc...). I am not sure how to properly pass a variable from an instance of one class so that it can be evaluated in a seperate class. Again, any help or suggestions are appreciated.

---

### Post by meanburrito920 on 2008-10-01
All you need to do is pass the object variable as the parameter to a function call. just like your code:

```

triggerword= Trigger()
triggerword.evaluate(story1.Title)

```

I think you will have to store each new instance of the NewsStory class in a list and then iterate over the list for the final version.

---

### Post by luke77 on 2008-10-02
OK, I'm getting there, I think, I just think that I am probably writing a lot of unneccesary code. Also, I am still unsure about the whole "Trigger" problem. I have a Trigger superclass with member classes titleTrigger, subjectTrigger, etc. but the Trigger superclass doesn't do anything, and isn't even called. It doesn't add anything at all to the program. And I must call each subclass individually, which would get pretty tedious if I had, say, 15 trigger tests.

I am thinking there is probably a way to call the Trigger superclass with a story as an argument, and have it test for all of its subclasses, rather than calling each subclass individually. In other words, instead of saying:

titleTest= titleTrigger(x)
subjectTest= subjectTrigger(x)

titleTest.evaluate(i.title)
subjectTest.evaluate(i.subject)
etc....

I should be able to write: 
test= Trigger(x)
test.evaluate(i)

and have all subclasses tested for. I'm not sure if this is possible, but if so, I don't know how to do it.

I've posted the completed code in a semi finished form below, with three trigger tests created. I'd really appreciate it if you guys could look over it and suggest improvements, and address the question above.

Thanks again,
Luke


```


import feedparser
from project_util import translate_html


#Create a NewsStory class that creates individual instances for each news story

class NewsStory(object):
    
    def __init__(self, guid, title, subject, link,summary):
        self.guid = guid
        self.title = title
        self.subject = subject
        self.summary = summary
        self.link = link
        
    def getGuid(self):
        return self.guid
        
    def getTitle(self):
        return self.title

    def getSubject(self):
        return self.subject

    def getSummary(self):
        return self.summary

    def getLink(self):
        return self.link




#Create Trigger superclass that tests for the presence of a trigger in a story
class Trigger():
    def evaluate (self, trigger):
        return True

class titleTrigger(Trigger):
    def __init__(self,triggerword):
        self.data = triggerword
    def evaluate(self, story):
        if self.data in story:
            
            return True

class subjectTrigger(Trigger):
    
    def __init__(self,triggerword):
        self.data = triggerword
    def evaluate(self, story):
        if self.data in story:
            
            return True

class summaryTrigger(Trigger):

    def __init__(self,triggerword):
        self.data = triggerword
    def evaluate(self, story):
        if self.data in story:
            
            return True

#Create list containing imported data for each story passed through function
def process (url,type=0):
    
        guid=d.entries[i].guid
        title=d.entries[i].title
        subject=d.entries[i].title
        summary=d.entries[i].description
        link=d.entries[i].link
        storylist=[guid,title,subject,link,summary]
        return storylist

#Prints a story
def printStories():
    
    print "GUID: ", translate_html(i.guid)
    print
    print "TITLE: ", translate_html(i.title)
    print
    print "SUBJECT: ", translate_html(i.subject)
    print
    print "LINK: ", translate_html(i.link)
    print
    print "SUMMARY: " 
   
    print translate_html(i.summary)
    print


#Inputs news stories from google's RSS feed
d = feedparser.parse('http://news.google.com/?output=rss')

#Ask for trigger to search for
x = raw_input("Enter trigger to search for. Program will output /n stories with trigger in title, subject, or summary")


#For each imported news story, creates a NewsStory instance for the story
#then tests for the presence of the trigger in the title, subject, or summary.
#If trigger is present, prints entire story

for i in range (len(d)):
    print 'Story',(i+1),':'
    print

    storyList = process ('http://news.google.com/?output=rss')
    i=NewsStory(storyList[0],storyList[1],storyList[2],storyList[3],storyList[4])
    
    
    
                      
    titleTest= titleTrigger(x)
    subjectTest= subjectTrigger(x)

    summaryTest= summaryTrigger(x)

    if titleTest.evaluate(i.title) == True:

        printStories()
        
    elif subjectTest.evaluate(i.subject) == True:

        printStories()
        
    elif summaryTest.evaluate(i.summary) == True:

        printStories()
```

---

### Post by meanburrito920 on 2008-10-03
While I can see that having separate classes to trigger for different elements would be more modular, I don't really think you need to take it to that extreme. you really only should need the Trigger class for what you are planning on doing. as for inheiritance, to make an object enheirit from another you write the class declaration as such:

```

class Test(Trigger): #this will cause class Test to inheirit trigger
   #stuff

```
any method that you write inside class Test will overwrite the method of the same name from the Trigger class. all other methods are accessable under Test.methodname even if you did not declare them within the body of Test

---

### Post by mosty friedman on 2008-10-03
i dont really understand what's troubling you, if its the idea of objects and classes, what are they and why do we use them? ..u could check out the web, you'll find many useful tutorials..but here's a brief explanation..
OOP is a style of programming which helps the programmer to model things from everyday use and translate it into code which results in creating a new data structure...
a class is the blueprint used to create new objects...like if ur building a car u first need blueprints which specify the characteristics and behaviors of the car.. the characteristics in programming are called instance fields or instance variables( could be number of seats of the car or Model,initial speed ,year of production etc )..and the behaviors are called methods and are used to manipulate the instance variables( apply brakes, increase speed etc)...
when you create a new object, the constructor is what instantiates the object with values( it assigns each instance variable with a value )...
also each Object you create has its own copy of each instance variable for example if you create 2 car objects(ex: car1, car2 ), each one would have a different Model, year of production, etc than the other..
its possible for all the objects to have the same value for certain fields, these fields are called static or class variables/fields..

sorry for the long post, just trying to help lol...anyway i hope this was helpful :)

---

