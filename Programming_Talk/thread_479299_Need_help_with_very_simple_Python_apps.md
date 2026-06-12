---
title: "Need help with very simple Python apps"
date: 2007-06-20
forum: Programming Talk
---

### Post by microsoft92sucks on 2007-06-20
I'm trying to make a few very very simple apps with Python I'm still very new to programming.
Here's the first app.
```
import time
hour=time.strftime('%H')
min=time.strftime("%M")
while True:
	x=raw_input('Would you like to know the time ')
	if x=='yes':
		print 'The time is', hour, ':' , min
	else:
		continue
```
It work's the first time you do it but the It keeps the first time. So I need to know how to make it reload the time.

The second is a calculator.
```
print 'Welcome to Calc your friendly text based calculator'
print 'Just say quit to quit'
print
t=True
while t:
	x=input('What\'s your math problem ')
	if x=='quit':
		t=False
		print 'Hope you enjoyed Calc'
	else:
		x=int(x)
		print x
```
The problem with it is if you put in a letter I coses a error message. And I want to make it so it won't do that.
Thank's for any help

---

### Post by david_edmundson on 2007-06-20
> **microsoft92sucks said:**
> I'm trying to make a few very very simple apps with Python I'm still very new to programming.
Here's the first app.
```
import time
hour=time.strftime('%H')
min=time.strftime("%M")
while True:
	x=raw_input('Would you like to know the time ')
	if x=='yes':
		print 'The time is', hour, ':' , min
	else:
		continue
```
It work's the first time you do it but the It keeps the first time. So I need to know how to make it reload the time.



```
import time

while True:
	x=raw_input('Would you like to know the time ')
	if x=='yes':
               hour=time.strftime('%H')
                min=time.strftime("%M")
		print 'The time is', hour, ':' , min
	else:
		continue
```

You only had it collect the time once. therefore when it does it again it's using the variables you set earlier

---

### Post by LaRoza on 2007-06-20
> The second is a calculator.
```
print 'Welcome to Calc your friendly text based calculator'
print 'Just say quit to quit'
print
t=True
while t:
	x=input('What\'s your math problem ')
	if x=='quit':
		t=False
		print 'Hope you enjoyed Calc'
	else:
		x=int(x)
		print x
```
The problem with it is if you put in a letter I coses a error message. And I want to make it so it won't do that.
Thank's for any help
Do not use input(), use raw_input, and eval() with some checking so you don't crash.

---

### Post by pmasiar on 2007-06-20
You need to put collecting time *inside* the while loop:
```

while True:
    hour=time.strftime('%H')
    min=time.strftime("%M")
    # etc

```

---

### Post by Siph0n on 2007-06-20
Im very new too, so im not sure which is better, but you could use break instead of True and False to exit the loop in your second program (the calculator)

```
print 'Welcome to Calc your friendly text based calculator'
print 'Just say quit to quit'
print
while t:
	x=raw_input('What\'s your math problem ')
	if x=='quit':
		
		print 'Hope you enjoyed Calc'
		break
	else:
		x=int(x)
		print x
```

Also won't x only print out an integer? you might want to make it a float or double? Again, im super new to python also, so anyone else have any ideas on my suggestions?

Siph0n

---

### Post by Siph0n on 2007-06-20
oops, should be while (1)

---

### Post by LaRoza on 2007-06-20
you can convert the input to any data type.

---

### Post by Jessehk on 2007-06-20
Maybe something like this for the calc program?

```

def heading(): return "Welcome to Calc: Your friendly text-based calculator"

EXIT_COMMANDS = ('quit', 'exit')

def evaluate_input( prompt ):
    string = raw_input( prompt )
    
    if string in EXIT_COMMANDS:
        return False
    else:
        return eval( string )
        
def main_loop():
    print heading()
    
    while True:
        result = evaluate_input( ">> " )
        if result is False:
            return 
        else:
            print result
            
if __name__ == "__main__":
    main_loop()

```

---

### Post by steve.horsley on 2007-06-20
There are three bugs in the first program.

Firstly, the one you've found is that the time never updates. As others have pointed out, you need to move getting the imte inside the loop, like this:
```

import time
hour=time.strftime('%H')
min=time.strftime("%M")
while True:
	hour=time.strftime('%H')
        min=time.strftime("%M")
        x=raw_input('Would you like to know the time ')
	if x=='yes':
		print 'The time is', hour, ':' , min
	else:
		continue

```
The second bug is that it reads the time before asking the question. If the user goes away to get a coffee and answers when they get back, the time reported will be wrong. You should really read the time whan they say yes, lke this:
```

import time
hour=time.strftime('%H')
min=time.strftime("%M")
while True:
    x=raw_input('Would you like to know the time ')
    if x=='yes':
	hour=time.strftime('%H')
        min=time.strftime("%M")
        print 'The time is', hour, ':' , min
    else:
        continue

```
But there is still a possibility that the hour could roll over between the two calls to strftime. E.g. it could read the hour at 11:59 so the hour is 11 but by the time it getsround to reading the minute the time has rolled over to 12:00 giving a minute value of 00. So every hour, exactly on the hour, it could report the time an hour wrong. Unlikely but possible. You should really read the time once and use the same time value for generating both strings, like this (of course you could use strftime once with the string "%H:%M" instead):
```

import time
hour=time.strftime('%H')
min=time.strftime("%M")
while True:
    x=raw_input('Would you like to know the time ')
    if x=='yes':
        now = time.time()
	hour=time.strftime('%H', now)
        min=time.strftime("%M", now)
        print 'The time is', hour, ':' , min
    else:
        continue

```
and incidentally, you don't need the else: continue lines - it will continue anyway when it reaches the end of the while block.

If you thing I'm being picky, you're right. You have the right general outline and don't let me being picky out you off. I'm trying to educate you not put you down. Don;t let my comments worry you - they may help one day if you vaguely remember about them though - may point you in the right direction.

For the second code, you could always catch the exception (if you've read about exceptions yet):

```

        if x=='quit':
                t=False
                print 'Hope you enjoyed Calc'
        else:
                try:
                        x=int(x)
                        print x
                except:
                        print "Type a number, butterfingers!"

```

---

