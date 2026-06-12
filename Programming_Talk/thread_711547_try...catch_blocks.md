---
title: "try...catch blocks"
date: 2008-02-29
forum: Programming Talk
---

### Post by slavik on 2008-02-29
Anyone else hate try/catch blocks?

They are expensive to set up and can be handled by simply checking for error on return ...

What is the real benefit to them?

NOTE: I code C.

---

### Post by melopsittacus on 2008-02-29
Hi!

Their advantage is that you can handle errors apart from "normal" code, and since Exceptions are objects you can pass more complex information along with them than you would with a simple error code.

By the way, I thought there was no try/catch in C...

---

### Post by aks44 on 2008-02-29
The whole goal of try/catch is twofold:

1) you don't have to clutter your code with error checking (makes the code cleaner)

2) you can't forget to handle an error. eg. do you ever check printf's return value? You should, it can fail... with C++'s exceptions, if std::cout::operator << fails you are automagically warned. :)

---

### Post by slavik on 2008-02-29
> **melopsittacus said:**
> Hi!

Their advantage is that you can handle errors apart from "normal" code, and since Exceptions are objects you can pass more complex information along with them than you would with a simple error code.

By the way, I thought there was no try/catch in C...
No, there aren't ... that's a reason I like C :)

because in C++ you have to catch exceptions which could be thrown by new.

my thinking is that with try catch you can just put your whole program into a giant try/catch block ...

---

### Post by mike_g on 2008-02-29
Its good to hate code, especially if its new to you. Hatred causes long term potentiation.

---

### Post by scourge on 2008-02-29
I also learned C before C++, so my code isn't as pure C++ as it could be. Right now I'm mixing C and C++ a lot, using return codes when applicable and exception handling elsewhere. For example, I only write functions that return an error code if the errors have to be caught in a really tight loop.

> do you ever check printf's return value? You should, it can fail...

I agree with your point in general but I wouldn't go that far. Sure, printf can fail, but then you're pretty much screwed no matter what kind of error handling you do or do not do. Even splint, which is extremely whiny about ignoring return values, doesn't care about printf by default.


> my thinking is that with try catch you can just put your whole program into a giant try/catch block ...

I don't think it's a bad thing that you can do it, though you probably shouldn't. You're correct that return values force you to catch errors as soon as possible, but they can also be frustrating and a big part of your code may end up being just checking for error codes.

---

### Post by rbprogrammer on 2008-02-29
one main purpose of try/catch blocks is the concept of handling errors within the caller instead of the callee.  what if you write a library that is generic enough to be used in multiple projects, but the error handling will be different.  exceptions provide a way of just saying "there was an error, now handle it somewhere else"....

---

### Post by Wybiral on 2008-02-29
Strictly using function returns will limit the acceptable values of what the function could legally return. For example when your function needs to return an integer (but you don't want to restrict the use of 0 or -1). Or when your function needs to return a pointer, but it's OK to return NULL (so you can't use that as the error message). What about floating point values, especially if you need to be able to use 0.0 (and remember that floating-point comparison isn't always reliable).

You could use work-arounds like passing a pointer as an argument to flag when an error occurs (or returning a struct with the value and the error flag) but any way you do it is still going to result in some hacky work-around...

What's wrong with try/catch?

---

### Post by LaRoza on 2008-02-29
Some feel that try...catch are just another form of a goto.

(I am leaning toward that side as well...)

---

### Post by mssever on 2008-02-29
As others have observed, using exceptions to report errors is a good way to make sure that errors don't fly by unnoticed. Compare this with PHP, where you only detect MySQL errors if you remember to test the result, then conditionally examine mysql_error(). Of course, you have to use try/catch intelligently; using a global try/catch block to simply surpress errors isn't such a good idea. I make it a policy to only catch specific exceptions; that way, if one occurs that I'm not expecting, the program dies (which is the proper behavior for unhandled errors).

Exceptions are also useful when you need to unwind the stack. For example, one of my projects, Net Responsibility (see my sig) is a daemon written in Ruby that logs URLs visited to an SQLite database for accountability purposes. Periodically, a separate report tool runs. When it's finished generating the report, it prunes the logfile. However, SQLite only grants write access to one process at a time. So, the report tool has to signal the daemon to close the database. When the daemon receives the proper signal, it raises an exception. In the process of unwinding the stack, it encounters a series of [FONT=Courier New]ensure[/FONT] blocks that do the necessary cleanup. Finally, the exception is rescued at the proper point in the stack. Once the logfile has been pruned, the daemon executes a [FONT=Courier New]retry[/FONT], and reopens the database. As far as I know, exceptions are the simplest way to implement such functionality.

In summary, I find that using exceptions greatly simplifies programming.

---

### Post by Wybiral on 2008-03-01
> **LaRoza said:**
> Some feel that try...catch are just another form of a goto.

(I am leaning toward that side as well...)

How is it any more than a condition or something?

---

### Post by LaRoza on 2008-03-01
> **Wybiral said:**
> How is it any more than a condition or something?

Perhaps I should have said the misuse of them is like gotos.

---

### Post by scourge on 2008-03-01
> **LaRoza said:**
> Some feel that try...catch are just another form of a goto.

(I am leaning toward that side as well...)

It could be worse; in Visual Basic exception handling actually requires the use of goto.

---

### Post by Quikee on 2008-03-01
I also don't like try..catch but I think there is nothing wrong with exceptions in general. 

Yes.. as many other things, exceptions can be abused or misused but I just don't like that every function / method should return an error code as an return parameter if something can go wrong. On the other hand I also would not want to enclose every function / method call in a try..catch block if this is not necessary. 

IMHO a function / method should not throw exceptions unless the error is so severe that it can not be handled "localy" or be avoided. Exceptions should not be used to steer the programming logic. 

For example:

[PHP]
try {
   File file  = new File("/file.txt");
catch (FileNotFoundException ex) {
  ... handle "File not found" ...
}[/PHP]

This is stupid.. instead of this one should do it like this:

[PHP]
if(File.exists("/file.txt")) {
   .. also check permissions and other things that can be handled here ..
   File file  = new File("/file.txt");
}
[/PHP]

Unless something is very wrong the method call should not fail with an exception if the file does not exists. But if a exception is thrown it is not the responsibility of this level to decide how to react on such a exception.

A similar unnecessary exception "misuse" in python:

[PHP]d = {1:1, 3:3, 5:5, 7:7}

for i in xrange(10):
    try:
        d[i] = d[i] + i
    except KeyError:
        d[i] = i
 
print d
[/PHP]

instead of:

[PHP]d = {1:1, 3:3, 5:5, 7:7}

for i in xrange(10):
    if i in d:
        d[i] = d[i] + i
    else:
        d[i] = i
 
print d[/PHP]

Or a total case of exception abuse:
[PHP]
class ColorException(Exception):
	def __init__(self, color):
		self.color = color if color else "black"

class ColorChooser(object):
	def __init__(self):
		self.color = "red"
	
	def getColor(self):
		raise ColorException(self.color)
		
colorChooser = ColorChooser()
try:
	colorChooser.getColor()
except ColorException, e:
	color = e.color

if color == "red":
	print "Perfect exception abuse!"[/PHP]

I hope nobody programs like that! ;)

---

### Post by pmasiar on 2008-03-01
> **LaRoza said:**
> Some feel that try...catch are just another form of a goto.

(I am leaning toward that side as well...)

Error handling was the only "good and approved" use of GOTO back in the days before languages had exceptions.  Now languages **do** have exceptions (at least the decent ones do :-) ) so rejecting of using exceptions is almost like arguing for using GOTO for error handling.

Yes, exceptions **are** kind of GOTO: stuctured GOTO which is aware of call context. Something bad happened, and you need to treat situation differently, and possibly at different place, too, you cannot continue processing as you planned. So you raise error, and magic unrolls: functions close, stack cleans, and you get to the place where you are ready to handle that situation. What not to like? As mentioned before, the only alternative is to check errors after every call, checking every index for boundaries, etc. It would be even slower, because exception checking can be optimized (compiler knows what is going on), while manual checking looks like "normal" code.

Hating exceptions might be also a case of **language bias**: people programming in languages where exceptions are friendly, useful and easy to use (like Python) might like them, and users of languages where exceptions are not as easy and useful might hate them.

This also hints why static exception checking like in Java is such a bad idea: it makes exceptions harder to use.

---

### Post by pmasiar on 2008-03-01
> **Quikee said:**
> 
A similar unnecessary exception "misuse" in python:

[PHP]d = {1:1, 3:3, 5:5, 7:7}

for i in xrange(10):
    try:
        d[i] = d[i] + i
    except KeyError:
        d[i] = i
 
print d
[/PHP]

instead of:

[PHP]d = {1:1, 3:3, 5:5, 7:7}

for i in xrange(10):
    if i in d:
        d[i] = d[i] + i
    else:
        d[i] = i
 
print d[/PHP]



I am not sure why first case is "misuse" - AFAIK, it is canonical way to do it :-) If exceptions are rare (keys usually exist), I bet it would be faster: it avoids superficial "if i in d". Error checking happens every time, after every statement, so you may as well use it for specific logic if you need it.

I am too busy/lazy to write a benchmarks, but my hunch is try/except version is faster.

---

### Post by slavik on 2008-03-01
one of the problems I have with try/catch is how it is used for AJAX stuff in javascript ... ie:
```

try { the_mozilla_http_connection(); the_ie_http_connection(); }
catch {}

```

it's like calling malloc and not checking for NULL.

@mssever: couldn't you use interrupts for communicating between the daemon and the process?

---

### Post by popch on 2008-03-01
> **pmasiar said:**
> I am not sure why first case is "misuse" - AFAIK, it is canonical way to do it :-) If exceptions are rare (keys usually exist), I bet it would be faster: it avoids superficial "if i in d". Error checking happens every time, after every statement, so you may as well use it for specific logic if you need it.

I am too busy/lazy to write a benchmarks, but my hunch is try/except version is faster.

The first variant sets up the event handling environment for every single iteration. That does not sound so much faster than just doing the test for each iteration.

---

### Post by beardiggin on 2008-03-01
> **mssever said:**
> I make it a policy to only catch specific exceptions; that way, if one occurs that I'm not expecting, the program dies (which is the proper behavior for unhandled errors).

This is not such a good idea.  A program should never just die, this just makes the user mad.  It should recover gracefully, which is the point of exception handling.  I suppose if you are not leaving the user stranded, it would be okay to not handle exceptions.  But how do you know if and when you are leaving the user stranded or not?

---

### Post by slavik on 2008-03-01
> **beardiggin said:**
> This is not such a good idea.  A program should never just die, this just makes the user mad.  It should recover gracefully, which is the point of exception handling.  I suppose if you are not leaving the user stranded, it would be okay to not handle exceptions.  But how do you know if and when you are leaving the user stranded or not?
if you need 100MB of memory and it is not available, there is no way to really recover (unless you want to sit in memory for user to kill other processes).

---

### Post by Quikee on 2008-03-01
> **pmasiar said:**
> I am not sure why first case is "misuse" - AFAIK, it is canonical way to do it :-) If exceptions are rare (keys usually exist), I bet it would be faster: it avoids superficial "if i in d". Error checking happens every time, after every statement, so you may as well use it for specific logic if you need it.

I am too busy/lazy to write a benchmarks, but my hunch is try/except version is faster.

True.. but if you care about speed in such a trivial case you would not be using python in the first place. Anyway you should not forget that in case of exception you have to instantiate a exception class which can also be a heavy weight operation. Also with try..catch the intention is not so clear IMHO. 

Also what about such an situation:

If a key is not in dictionary, lets try another key before setting a value.

[PHP]d = {1:1, 3:3, 5:5, 7:7}

for i in xrange(10):
    try:
        d[i] = d[i] + i
    except KeyError:
        try:
            d[i] = d[i+1] + i
        except KeyError:
            d[i] = i

print d  
[/PHP]

With try..catch it can get messy pretty quick. ;)

---

### Post by the_unforgiven on 2008-03-01
> **aks44 said:**
> The whole goal of try/catch is twofold:

1) you don't have to clutter your code with error checking (makes the code cleaner)

2) you can't forget to handle an error. eg. do you ever check printf's return value? You should, it can fail... with C++'s exceptions, if std::cout::operator << fails you are automagically warned. :)
To elaborate this, try/catch allows you to decouple error *reporting* from error *handling*.

Let's say, you're deep down into call hierarchy - well into the lib - and you detect an error condition. I suppose we all agree that handling errors in library is not really a good idea - we can never predict what should be the right behaviour of the app in the erroneous condition - neither is plain termination using something like abort().

Now, if you were to let app handle the error properly, you'd have to unwind the entire call stack with the proper return value that communicates the error condition to the app - which I think is too tedious. A simpler solution is to just raise the proper type of exception. 

Moreover, what's the guarantee that some intermediate function in the call stack doesn't modify or somehow mistreat the return value (or maybe just doesn't catch to be returned back)? For that, you'd have to place ugly retval checks all over the place.

So, the clarity and readability of code takes precedence over a little suboptimal nature of the alternate solution that is exceptions.

In C, this can be achieved using setjmp()/longjmp() - though that's also suboptimal - which looks quite ugly and hacky too.

Moreover, exceptions is just another tool provided by the language - by no means it's forced on the developer. So, proper use of exceptions is still left to the discretion of the developer. You could still write C-styled retval checks in C++/python (unless you're using some prebuilt stuff that already uses exceptions).

Please feel free to correct if I've made mistake or add to it.

---

### Post by scourge on 2008-03-01
> **slavik said:**
> if you need 100MB of memory and it is not available, there is no way to really recover (unless you want to sit in memory for user to kill other processes).

Yes, the program should terminate if it runs out of memory, but you shouldn't just let it crash. For example I always check the return value of malloc so that my program can terminate as soon as possible and tell the user why it had to terminate.

---

### Post by pmasiar on 2008-03-01
> **popch said:**
> The first variant sets up the event handling environment for every single iteration. That does not sound so much faster than just doing the test for each iteration.
try/except is **always** there. Python adds it for you. OTOH "if i in d" does not have to be there, and does use time.

---

### Post by the_unforgiven on 2008-03-01
> **scourge said:**
> Yes, the program should terminate if it runs out of memory, but you shouldn't just let it crash. For example I always check the return value of malloc so that my program can terminate as soon as possible and tell the user why it had to terminate.
You may not always get the chance to let it terminate gracefully.
Keep in mind the [OOM Killer]("http://linux-mm.org/OOM_Killer") ;)

Some info on OOM conditions:
[http://en.wikipedia.org/wiki/Out_of_memory](http://en.wikipedia.org/wiki/Out_of_memory)

Another interesting article on OOM Killer:
[http://lwn.net/Articles/104179/](http://lwn.net/Articles/104179/)

---

### Post by mssever on 2008-03-01
> **slavik said:**
> @mssever: couldn't you use interrupts for communicating between the daemon and the process?
I'm not quite sure I understand you. What I'm doing is using SIGUSR1 and SIGUSR2 for communication. But the daemon still has to respond to the signal, hence the exception it raises. The only interrupts I can think of are hardware or OS interrupts. I'm working at a higher level than that.
> **Quikee said:**
> [php]
try {
   File file  = new File("/file.txt");
catch (FileNotFoundException ex) {
  ... handle "File not found" ...
}[/php]This is stupid.. instead of this one should do it like this:

[php]
if(File.exists("/file.txt")) {
   .. also check permissions and other things that can be handled here ..
   File file  = new File("/file.txt");
}[/php]There really isn't much of a substantial difference in terms of readability between this:
```
begin
  File.open('somefile') { |f| puts f }
rescue Errno::ENOENT #This exception is terribly named...
  puts default_content
end
```
and this:
```
if File.exists? 'somefile'
  File.open('somefile') { |f| puts f }
else
  puts default_content
end
```
As far as speed goes, I haven't tested it, but I'm guessing that the bottleneck here would be the filesystem, not the exception. Besides, each case involves similar overhead.

And when the situation gets more complicated, using exceptions can result in more readable code since you need fewer if statements to add levels of indentation.

> **beardiggin said:**
> This is not such a good idea.  A program should never just die, this just makes the user mad.  It should recover gracefully, which is the point of exception handling.  I suppose if you are not leaving the user stranded, it would be okay to not handle exceptions.  But how do you know if and when you are leaving the user stranded or not?
The thing is, any unhandled exception is, by definition, a bug. The fact that it's unhandled proves that the program doesn't know how to recover gracefully in that situation. So instead of limping along in an inconsistant state in which the program could be doing who knows what, it should fail and report an error. Of course, part of the bug fix would involve handling similar exceptions in the future.

There are a couple of principles at work here:
[LIST=1]
[*]Whenever possible, a program should recover gracefully from errors.
[*]When recovery isn't possible, the program should fail noisily and as soon as possible. Depending on the type of error (and the type or program), the failure could range from displaying a message to crashing.[/LIST]A crash is one thing. Stomping on the user's data because the program got into an inconsistent state is another.

---

### Post by pmasiar on 2008-03-02
> **mssever said:**
> 
There are a couple of principles at work here:


Zen of Python says:

"Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess."

:-)

---

### Post by popch on 2008-03-02
> **mssever said:**
> 
There are a couple of principles at work here:[LIST=1]
[*]Whenever possible, a program should recover gracefully from errors.
[*]When recovery isn't possible, the program should fail noisily and as soon as possible. Depending on the type of error (and the type or program), the failure could range from displaying a message to crashing.[/LIST]

Agreed. There ought to be a third one:

3. If at all possible, the failed program must not leave any side effects.

Removing side effects is, of course, an important part of exception handling.

---

