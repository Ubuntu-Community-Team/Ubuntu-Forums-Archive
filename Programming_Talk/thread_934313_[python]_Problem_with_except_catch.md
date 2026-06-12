---
title: "[python] Problem with except catch"
date: 2008-09-30
forum: Programming Talk
---

### Post by Titan8990 on 2008-09-30
I have taken a break from programming for about a month. I wanted to pick it back up so I started with a refresher that I failed with. It is a simple program that takes 2 integers from user input and divides the two. The problem is with my caught exception.

It will catch the exception properly but when main() is ran through again I get syntax error: variable referenced before assignment.

[php]#!/usr/bin/python


def main():
	dmg = 0
	time = 0


	dmg = raw_input("\nEnter the Damage of the DOT: ")
	time = raw_input("\nEnter the time of the DOT: ")

	try: 

		result = int(dmg) / int(time)

	except:
		print "\n\nEnter a integer for time and damage"
		main()

	print "\n\nYour DOT does", result, "DPS\n\n"

main()[/php]

```
jordan@bourne:~/python$ ./dpstest.py

Enter the Damage of the DOT: 10

Enter the time of the DOT: 1


Your DOT does 10 DPS


jordan@bourne:~/python$ ./dpstest.py

Enter the Damage of the DOT: blue

Enter the time of the DOT: green


Enter a integer for time and damage

Enter the Damage of the DOT: 10

Enter the time of the DOT: 1


Your DOT does 10 DPS




Your DOT does
Traceback (most recent call last):
  File "./dpstest.py", line 22, in <module>
    main()
  File "./dpstest.py", line 20, in main
    print "\n\nYour DOT does", result, "DPS\n\n"
UnboundLocalError: local variable 'result' referenced before assignment
```


Any help is appreciated.

---

### Post by snova on 2008-09-30
It's because of the recursion. When it calls itself again, it runs through the procedure correctly, but then it returns. The next code to be executed is the line that prints the result, but since the exception was thrown, the variable was never assigned to. Thus, it doesn't exist, and you're getting an error because you're trying to access it.

---

### Post by LaRoza on 2008-09-30
You should use a loop for this or use the simple built in methods for validating the input. You shouldn't use exceptions to control program flow.

---

### Post by Titan8990 on 2008-09-30
Alright, so from a psuedocode perspective I could do something like this:  ?


If dmg is an integer then ask for time

If time is an integer than calculate and print result


I am in bad need of a more advanced book as I have read all of the one that I have and feel as though I know nothing. Also, I do things that the book had taught me and then I find out here that it is not the best practice (not the first occasion).



Thanks for the input.

---

### Post by LaRoza on 2008-09-30
> **Titan8990 said:**
> Alright, so from a psuedocode perspective I could do something like this:  ?


If dmg is an integer then ask for time

If time is an integer than calculate and print result

I am in bad need of a more advanced book as I have read all of the one that I have and feel as though I know nothing. Also, I do things that the book had taught me and then I find out here that it is not the best practice (not the first occasion).

Thanks for the input.


```

#!/usr/bin/python

def main():
    dmg = 0
    time = 0
    cont = True
    
    while cont:
        dmg = raw_input("\nEnter the Damage of the DOT: ")
        if cont.isdigit():
            cont = False
        else:
            print "Enter a number"

    cont = True

    while cont:
        time = raw_input("\nEnter the time of the DOT: ")
        if time.isdigit():
            cont = False
        else:
            print "Enter a number"

    result = int(dmg) / int(time)

    print "\n\nEnter a integer for time and damage"
    print "\n\nYour DOT does", result, "DPS\n\n"

if __name__ == "__main__":
    main() 

```

There are better ways, but that is the concept. My indents are off because you can't use tab in a browser.

---

### Post by Titan8990 on 2008-09-30
Tyvm LaRoza. I was on the right track with the isdigit function but I was currently trying to do it a bit differently and it was not working.

[php]def main():
	dmg = 0
	time = 0
	dmg.isdigit()

	
	while dmg.isdigit() == 0:
		dmg = raw_input("\nEnter the Damage of the DOT: ")
		if dmg.isdigit() == 0:
			print "Please enter an integer"[/php]


The only thing I don't understand about your code is this:

[php]if __name__ == "__main__":
    main()[/php]

What is the purpose of this? Why not just run main() directly? Is this actually needed or just considered to be good practice?


Thanks again!

---

### Post by snova on 2008-09-30
> **Titan8990 said:**
> 
The only thing I don't understand about your code is this:

[php]if __name__ == "__main__":
    main()[/php]

What is the purpose of this? Why not just run main() directly? Is this actually needed or just considered to be good practice?

Thanks again!

It's so that you can import the file as a module in addition to running it as a program. That way you could perhaps use the function somewhere else. If you didn't have these lines, then main() would always be run when you import the module, which isn't always desirable.

So it's just good practice is all. Several library modules have a test function in them with lines like these, so that you can run the module and have it run self-tests. Handy, isn't it?

---

### Post by Titan8990 on 2008-09-30
This is good because I do plan to integrate this in to a bigger program once I have brushed up on my skills and learned a bit more.

If anyone is interested the end result will be a program that will find your most efficient combination of skills for the game Warhammer Online.

---

### Post by gomputor on 2008-09-30
First, if you want to get arithmetic values form the input, you don't have to use **raw_input()** and convert it to integer. You can just use **input()** and enter even floats. But if you use it, then you must catch any errors that may occur if the user doesn't type an arithmetic value.
Second, if you want a function to call itself again, then you must put a return statement after that call.
For example your piece of code could be like this:
[PHP]#!/usr/bin/env python

def calculate():
    try:
        dmg = input("\nEnter the Damage of the DOT: ")
        time = input("\nEnter the time of the DOT: ")
        result = dmg / time
    except Exception, e:
        print '\nERROR: %s\nPlease try again.' % e
        calculate()
        return

    print "\nYour DOT does", result, "DPS\n"

if __name__ == "__main__":
    calculate()[/PHP]

---

### Post by pp. on 2008-09-30
> **LaRoza said:**
> ```

    
    while cont:
        dmg = raw_input("\nEnter the Damage of the DOT: ")
        if cont.isdigit():
            cont = False
        else:
            print "Enter a number"

```


cont.isdigit() should be dmg.isdigit()

---

### Post by y-lee on 2008-09-30
> **LaRoza said:**
> You shouldn't use exceptions to control program flow.

What :confused:

Who told you that LaRoza? :confused: The use of exceptions to control program flow is a very powerful tool and should be in the tool bag of all programmers, at least those that use a language that allows such constructs. Admittedly like everything it can be abused.

so here is yet another way to accomplish the OPs task more in line with his original code and using the magic of decorator strings :D

```
#!/usr/bin/python

def onlyvalid(func):
    def wrapper():
        valid = False
        while not valid:
            try:
                res = func()
                valid = True
            except ValueError:
                print "\n\nEnter a integer for time and damage"
        return res
    return wrapper

@onlyvalid
def main():
    dmg = 0
    time = 0
    dmg  = raw_input("\nEnter the Damage of the DOT: ")
    time = raw_input("\nEnter the time of the DOT: ")
    return int(dmg) / int(time)

if __name__ == '__main__':
    result = main()
    print "\n\nYour DOT does", result, "DPS\n\n"
```

Admittedly it would be better to test for validity as the data was entered, but this gave me an excuse to play with decorator strings and illustrate their use here.

Anyway as to Titan8990 original code it is a bad idea to catch all exceptions as in:

```

try: 
    result = int(dmg) / int(time)
except:
    print "\n\nEnter a integer for time and damage"
```

If one uses try and except catch only the exceptions you need or expect :D

---

### Post by Titan8990 on 2008-09-30
Alright, sorry to bother you guys again but it seems that A) I have picked a poor choice of learning material B) Can not understand this OOP stuff.

What I am currently trying to do is turn DOT in to an object that is represented by the final result (the DPS). In the book that I have he simply calls the function of a class and assigns it to a variable. Then he print that variable. However when I do so I get a pointed in the memory instead of what I am actually looking for. The end result will be an object with two attributes. One for its name (haven't started on this, one thing at a time), and another for it's DPS.

Anyways, I need to get the result of a function that is in a class and place in a variable so that it is an attribute of my object.

I have a feeling that I am approaching this completely wrong so feel free to tell me if I am doing so.

[php]#!/usr/bin/python

class dot(object):
	def dotdps(self):
		dmg = 0
	    	time = 0
	    	cont = True
	    	while cont:
	        	dmg = raw_input("\nEnter the Damage of the DOT: ")
	        	if dmg.isdigit():
	            		cont = False
	        	else:
	            		print "Enter a number"

	    	cont = True

	    	while cont:
	        	time = raw_input("\nEnter the time of the DOT: ")
	        	if time.isdigit():
	        	    	cont = False
	        	else:
	            		print "Enter a number"
	
	    	result = int(dmg) / int(time)
		str(result)
	
	       	print "\n\nYour DOT does", result, "DPS\n\n"
		return result
	
dot1 = dot()
dot1.dotdps()
print dot1[/php]

```
jordan@bourne:~/python$ ./dpstest.py

Enter the Damage of the DOT: 10

Enter the time of the DOT: 10


Your DOT does 1 DPS


<__main__.dot object at 0xb7d85d2c>

```

---

### Post by LaRoza on 2008-09-30
> **gomputor said:**
> First, if you want to get arithmetic values form the input, you don't have to use **raw_input()** and convert it to integer. You can just use **input()** and enter even floats. But if you use it, then you must catch any errors that may occur if the user doesn't type an arithmetic value. 

No. Never do that. 

> **y-lee said:**
> 
Who told you that LaRoza? :confused: The use of exceptions to control program flow is a very powerful tool and should be in the tool bag of all programmers, at least those that use a language that allows such constructs. Admittedly like everything it can be abused.


Don't use exceptions for normal program control. They are to catch exceptions, not expectation handling. [http://c2.com/cgi/wiki?AvoidExceptionsWheneverPossible](http://c2.com/cgi/wiki?AvoidExceptionsWheneverPossible)

---

### Post by gomputor on 2008-09-30
> **LaRoza said:**
> No. Never do that.

Why?

---

### Post by LaRoza on 2008-09-30
> **gomputor said:**
> Why?
[http://linuxgazette.net/issue83/evans.html](http://linuxgazette.net/issue83/evans.html)

---

### Post by gomputor on 2008-09-30
[B]"'input()' is fed to 'eval()' before your program gets it. This automatically
converts types, which is convenient if you want an integer and the user
accidentally gives you one. But the user would have to quote strings. Worse,
a rogue user might type 'os.system("rm -r *")', which would give you
a bad day."[/B]

I admit that I didn't know that. Thanks for the link! :)

---

### Post by y-lee on 2008-09-30
> **LaRoza said:**
> 
[QUOTE=y-lee;5882708]Who told you that LaRoza? :confused: The use of exceptions to control program flow is a very powerful tool and should be in the tool bag of all programmers, at least those that use a language that allows such constructs. Admittedly like everything it can be abused.
Don't use exceptions for normal program control. They are to catch exceptions, not excpectation handling. [http://c2.com/cgi/wiki?AvoidExceptionsWheneverPossible](http://c2.com/cgi/wiki?AvoidExceptionsWheneverPossible)[/QUOTE]

I am sorry LaRoza I have no idea what excpectation means :confused:

And that is an interesting link yet it demonstrates nothing. It is just a bunch of people arguing over the use of exceptions and proving only that as it often the case in programming dogmatic principles that there is much controversy over when and where and how often to use exceptions. Ironically the same link contains a link to [Exceptions Are Our Friends]("http://c2.com/cgi/wiki?ExceptionsAreOurFriends") contained on the very same web site. Surely if you truly believe the use of exceptions to control program logic is to be avoided in cases where other perhaps arguably more reasonable constructs would suffice you could do better than linking to a debate on the subject featuring mostly the opinions of Ron Jeffries and friends. Jeffries is credited with being a founder of the Extreme Programming methodology a programming philosophy of much controversy and certainly not universally excepted. Hmm anyway thanks for the link it was an interesting read :D 

That said perhaps I will help you, a quote from none other than Brian Kernighan and Rob Pike's Classic *The Practice of Programming*

> Exceptions should not be used for handling expected return values ... Exceptions are often misused. Because they can distort the flow of control, they can lead to convoluted constructions that are prone to bugs.

I agree with that statement by K.& P.

But I also feel the statement to not use them like ever as in

> **LaRoza said:**
> You shouldn't use exceptions to control program flow.

is wrong. or at least the impression i get from that dogmatic assertion is to not use exception handling.

I must admit I was shocked when I first saw code and really clever code at that that basically did all program logic with exceptions show up in Programming magazines I read at the time as i felt that was a very strange way to code and I still feel coding like that is an abuse of a useful programming construct. 
However, just because something can be abused does not mean it should not be used and one of my goals in programming is to have readable and understandable code as well as code that hopefully works. The whole argument over the use of exceptions reminds me of the much earlier dogmatic and blind application of structured programming principles. Dogmatism is bad whether in politics religion or programming.

---

### Post by LaRoza on 2008-09-30
> **y-lee said:**
> I am sorry LaRoza I have no idea what excpectation means :confused:

Spelled it wrong, meant "expectation handling". Basically, using exceptions when to catch things you expect. It is just a goto in that case.

> 
is wrong. or at least the impression i get from that dogmatic assertion is to not use exception handling.

No. I didn't say that...

> 
However, just because something can be abused does not mean it should not be used and one of my goals in programming is to have readable and understandable code as well as code that hopefully works. The whole argument over the use of exceptions reminds me of the much earlier dogmatic and blind application of structured programming principles. Dogmatism is bad whether in politics religion or programming.

I never said it shouldn't be used, just that I thought it was being misused. Is that code readable that was posted? A recursive function, a hidden bug, and exception handling to control it all.

Dogma isn't bad, just foolishly sticking to it.

---

### Post by y-lee on 2008-09-30
> **LaRoza said:**
> Is that code readable that was posted? A recursive function, a hidden bug, and exception handling to control it all.

:lolflag: Well it was readable sorta and it acted precisely as I expected it to act. Not well at all and truthfully with apologies to Titan8990 that code was a mess, but I could see what he was *trying to do* which is why i posted the decorator string solution.  And even that solution was not the preferred way to accomplish said task and admittedly a minor abuse of exception handling on top of it (you had already posted the preferred way of doing it :D )

Anyway I think we agree here more or less on the exception issue (the OP was attempting to misuse it) and dogmatism too so peace :D

---

### Post by dwhitney67 on 2008-09-30
I don't know if this reply will fall on the second or third page of the thread, but I am surprised no one mentioned that if the input of 'time' is zero, that the DOT/time division won't make any sense.

In fact, 'time' should be checked to ensure that it is greater than zero, since a negative time value does not make sense.

P.S.  The reply fell on the 2nd page.  :-)

---

### Post by y-lee on 2008-09-30
> **Titan8990 said:**
> What I am currently trying to do is turn DOT in to an object that is represented by the final result (the DPS). In the book that I have he simply calls the function of a class and assigns it to a variable. Then he print that variable. However when I do so I get a pointed in the memory instead of what I am actually looking for. The end result will be an object with two attributes. One for its name (haven't started on this, one thing at a time), and another for it's DPS.

Anyways, I need to get the result of a function that is in a class and place in a variable so that it is an attribute of my object.

I have a feeling that I am approaching this completely wrong so feel free to tell me if I am doing so.


I don't really know what you want here and the code you posted makes little sense. I would have an initialize function inside my class as well as a function to input the data (if that is the way you want to do it) and maybe a function to print the data or perhaps to convert the data to a string for printing. It is obvious from looking at your code that you don't understands the basics of python so my advice would be to work thru a book or tutorial on python basics first.

---

### Post by y-lee on 2008-09-30
> **dwhitney67 said:**
> I don't know if this reply will fall on the second or third page of the thread, but I am surprised no one mentioned that if the input of 'time' is zero, that the DOT/time division won't make any sense.

In fact, 'time' should be checked to ensure that it is greater than zero, since a negative time value does not make sense.

P.S.  The reply fell on the 2nd page.  :-)

Good point here too.

---

### Post by jbmurphy on 2008-09-30
all you need to do is change the print statement to

 print "\n\nYour DOT does %d \n\n" % (result)

---

