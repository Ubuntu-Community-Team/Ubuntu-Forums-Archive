---
title: "Python: I can't figure out why this crashes."
date: 2009-03-24
forum: Programming Talk
---

### Post by Arazu on 2009-03-24
This used to work. I must have accidentally altered a character or something.

**Note:** The odd part is that I can drag and drop various parts of it into the interpreter and they run fine. I can get it to output it to a file just fine by dragging the function over. It crashes where commented when I attempt to run the entire thing.

[PHP]#! /usr/bin/python


def get_run():
	r = raw_input('\n\nRun again? (y/n): ')
	while r != 'y' and r != 'Y' and r != 'n' and r != 'N':
		r = raw_input('Run again? (y/n): ')
	if r == 'Y':
		r = 'y'
	return r


def get_dest():
	d = ''
	while d != 's' and d != 'S' and d != 'f' and d != 'F':
		d = raw_input('Output to (F)ile or (S)creen?: ')
	if d == 'S': d = 's'
	if d == 'F': d = 'f'
	return d


def fib_calc(d):
	n = long(raw_input('\nPlease enter a number: '))
	if n >= 0:
		a, b, output = 0, 1, [0]
		while b <= n:
			output.append(b)
			a, b = b, a + b
		if d == 's':
			print '\nFibanacci numbers <=', n, '\n',
			print output,
		elif d == 'f':
			fname = 'Desktop/FibOutput' + str(n)
			print fname
			check = raw_input('one')
#crash here --->
			f = open(fname, 'w')
			check = raw_input('two')
			f.write(str(output))
			f.close
			print '\nResults written to ', fname,
	else: print '\nError: Unsupported number.',


run =  'y'
while run == 'y':
	dest = get_dest()
	fib_calc(dest)
	run = get_run()[/PHP]

Thanks for any thoughts.

---

### Post by elCabron on 2009-03-24
Are you running it while inside a different directory (not containing a Desktop directory) ?

---

### Post by Arazu on 2009-03-24
I've tried it both ways. It used to work from Documents.

I'm just going to re-write it. I've already found tons of things I need to do better. I am curious why it fails though.

---

### Post by namegame on 2009-03-24
I copied and pasted your code into a file called "test.py" and ran it VIA commandline with the command "python test.py" It worked for me, both ways, with a file, and to screen. I have Python 2.4.3.

Maybe you have hidden characters in your file or something.

---

### Post by Arazu on 2009-03-24
[PHP]douglas@Prometheus:~/Documents/PythonScripts$ python Fibonacci.py
Output to (F)ile or (S)creen?: f

Please enter a number: 3
Desktop/FibOutput3
one
Traceback (most recent call last):
  File "Fibonacci.py", line 46, in <module>
    fib_calc(dest)
  File "Fibonacci.py", line 36, in fib_calc
    f = open(fname, 'w')
IOError: [Errno 2] No such file or directory: 'Desktop/FibOutput3'
[/PHP]

I moved the .py file to my desktop and changed fname to fname = 'FibOutput' + str(n).

Now it works. I don't know why it worked last night and now it's complaining at me.

---

### Post by days_of_ruin on 2009-03-24
> **Arazu said:**
> [PHP]douglas@Prometheus:~/Documents/PythonScripts$ python Fibonacci.py
Output to (F)ile or (S)creen?: f

Please enter a number: 3
Desktop/FibOutput3
one
Traceback (most recent call last):
  File "Fibonacci.py", line 46, in <module>
    fib_calc(dest)
  File "Fibonacci.py", line 36, in fib_calc
    f = open(fname, 'w')
IOError: [Errno 2] No such file or directory: 'Desktop/FibOutput3'
[/PHP]

I moved the .py file to my desktop and changed fname to fname = 'FibOutput' + str(n).

Now it works. I don't know why it worked last night and now it's complaining at me.

You need to change the filepath to an absolute filepath "/home/yourusername/Desktop/FibOutput"

or move your program to your home folder and run it from there.

---

### Post by delfick on 2009-03-30
A couple of things unrelated to your problem directly (seeing as the above post seems to have the solution anyways :p).

instead of using while r != 'y' and r != 'Y' and r != 'n', etc you can do 

while r not in ('y', 'Y', 'n', 'N')

better yet, because you're dealing with strings here, we can do

while r not in ("yYnN"):

then we can further reduce the code by doing

while r.lower() not in ("yn"):

and then when you return r, we can do
return r.lower()
instead of checking if it's capital or not.

So the first two functions become 

[PHP]
def get_run():
	#get initial input
	r =raw_input('\n\nRun again? (y/n): ')
	
	#While the input is incorrect
	#  keep asking for correct input
	while r.lower() not in ('yn'):
		r = raw_input('Run again? (y/n): ')
		
	return r.lower()

def get_dest():
	question = 'Output to (F)ile or (S)creen?: '
	
	d = raw_input(question)
	while d.lower() not in ('sf'):
		d = raw_input(question)
	
	return d.lower()
[/PHP]

Then we can see that the two functions are very similar, so we can create a decorator function that reduces code repetition a little more

[PHP]
def get_value(f):
	def replacementFunc():
		options = f()
		if len(options) == 2:
			question1, acceptableInput = options
			question2 = question1
		
		elif len(options) == 3:
			question1, acceptableInput, question2 = options
		
		d = raw_input(question1)
		while d.lower() not in list(acceptableInput):
			d = raw_input(question2)
		
		return d.lower()
	
	return replacementFunc

@get_value
def get_run():
	return ('\n\nRun again? (y/n): ',
		'yn',
		'Run again? (y/n): ',
	)

@get_value
def get_dest():
	return ('Output to (F)ile or (S)creen?: ',
		'sf',
	)
[/PHP]

Whilst you could probably argue that reduces readability slightly, if you have a lot of these type of functions, that's quite a bit of typing you can save :)

Anywho, enough procrastination, I think I'll return to my uni studies now :p

---

