---
title: "Python: Compare list elements to string"
date: 2011-07-28
forum: Programming Talk
---

### Post by infectedorganism on 2011-07-28
I am currently doing Beginner Challenge 2. I have everything working except this: 

I created an list(incomplete) of characters that are disallowed in the user's forum name. I am trying to compare the elements of the list to the forum name the user enters. I have tried various things, but I can't seem to get it working properly. 

I understand that the for loop is broken and incomplete. I want it so if a list element is found, the entire while loop will restart. I am just having a hard time structuring it all to make it work properly.

Any help is appreciated.

** Instead of making a new thread, I'll ask here. Once your condition has been met, it okay to 'break' out of loops (while True) or is it better to set while to False instead?


```


import sys

# Function to check if the user enters 'quit'. If so, terminate program.

def check_quit(string):
	if string.lower() == 'quit':
		print '\nQuitting..'
		sys.exit()


def get_name():
	
	invalid = ['!', '@', '#', '$', '%', '^', '&', '*', '(', ')']
	
	while True:
		# .strip() will remove leading/trailing whitespace of returned value 
		forum_name = raw_input('Forum name: ').strip()	
		check_quit(forum_name)
		
		for characters in invalid:
			if characters in forum_name:
				print 'Invalid character in forum name.'
		
		if len(forum_name) in range(3, 21):
			break
		else:
			print 'Invalid name: Must be 3-20 characters long\n'
				
	return forum_name


```

---

### Post by schauerlich on 2011-07-28
I would suggest putting that for loop into another function, and then using 'continue'. 'continue' will skip you ahead automatically to the next iteration of whatever loop you put it inside. Something like this:

```
import sys

# Function to check if the user enters 'quit'. If so, terminate program.

def check_quit(string):
    if string.lower() == 'quit':
        return True
    return False


def name_is_valid(name):
    invalid = ['!', '@', '#', '$', '%', '^', '&', '*', '(', ')']
    
    for char in invalid:
        if char in name:
            return False

    return True

def get_name():
    while True:
        # .strip() will remove leading/trailing whitespace of returned value 
        forum_name = raw_input('Forum name: ').strip()
        
        if check_quit(forum_name):
            print ""
            print "Quitting..."
            sys.exit(0)

        if not name_is_valid(forum_name):
            print "Invalid character in forum name"
            continue

        if len(forum_name) in range(3, 21):
            break
        else:
            print 'Invalid name: Must be 3-20 characters long\n'

    return forum_name

if __name__ == "__main__":
    print get_name()

```

---

### Post by TwoEars on 2011-07-28
Well, there are lots of ways of doing this - 

```


def get_name():
	
	invalid = ['!', '@', '#', '$', '%', '^', '&', '*', '(', ')']

```
Every time this function is called, this gets defined. I suggest moving it out of the function - and also looking into either the string module or re

```

	while True:
		# .strip() will remove leading/trailing whitespace of returned value 
		forum_name = raw_input('Forum name: ').strip()	
		check_quit(forum_name)
		
		for characters in invalid:

```
Surely here you mean character? ;) 
```

			if characters in forum_name:
				print 'Invalid character in forum name.'

```
You need to do something more than just print if it's an invalid name character ;)
```

		if len(forum_name) in range(3, 21):
			break
		else:
			print 'Invalid name: Must be 3-20 characters long\n'

```
Right, well, we don't normally use range to test whether a number is a certain length - mainly because it creates a list every time. Instead, how about 
```

if 2<len(forum_name)<21:

```
As for your break - that's how we do it in Python, as it reduces code waste. :)

---

### Post by thornmastr on 2011-07-29
In looking at the requirement for user name in challenge 2, they are defined as follows.
User name can't begin with spaces, or have no characters in it. It can truncate strings over 20, if needed.

That is it. So there s nothing wrong with a user name of 'j12az!!@q'. Remember, it is not the name you use on your taxes..it is your log on to something name. The requirements are clearly specified. Don't over edit.

Robert

---

