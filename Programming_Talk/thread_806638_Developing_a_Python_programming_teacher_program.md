---
title: "Developing a Python programming teacher program"
date: 2008-05-25
forum: Programming Talk
---

### Post by Tobi-fp on 2008-05-25
Hi there Lads and Lasses.
I am fairly new to developing (only know a little python language).
But i was thinking that while it is fairly easy to learn programming in python, it could be easier, and therefore i wanted to start a project with some other programming newbies and well, maybe one or two skilled python programmers that could function as advisors..

The Project:

To write a program that can help others learn Python.
It should be a gui program with an index of all commands, some tasks, and trainers.

Anybody up for the challenge?

Greetings Tobias F. Petersen

---

### Post by xlinuks on 2008-05-25
```

To write a program that can help others learn Python.
It should be a gui program with an index of all commands, some tasks, and trainers.

```
Perhaps it sounds easy for unexperienced programmers, but when you start thinking about the actual things you have to implement and take care of - it's very difficult, especially the "trainers" (depending on how you actually define them).
A good ( I mean really "good", such as MS Visual Studio, NetBeans 6.1 or alike ) GUI program takes a lot of time for only creating/designing the GUI itself, not to mention other issues..
Hope you find someone :) But I think you'd find people unless you first present to them a beta version of what you want so they can decide for sure if they wanna develop an app that way.

---

### Post by slavik on 2008-05-25
you mean something along the lines of [http://www.turingscraft.com/](http://www.turingscraft.com/) ???

---

### Post by OpenFish on 2008-05-25
Sound good idea to me may i sujest using pygtk so as to avoid all that mess

i know this means installing library's in non gnome systems (inc all windows and mac's) but if its in python u would have to install the python interpreter any way and there are nice installer im told 
(havnt used a non *nix system for 6 mounth and havnt had to use one for more than 1/2 an hour for 12)

ps are u familial with

[PHP]
import Libry
listOfFunctions =  dir( Libry )
for function in listOfFunctions:
  print function 
  #or add it to a GUI element/widget
[/PHP]
i know this is patronizing's for most of u but i use it all the time but never see it in any tuts

---

### Post by Tobi-fp on 2008-05-25
> **slavik said:**
> you mean something along the lines of [http://www.turingscraft.com/](http://www.turingscraft.com/) ???

Well, actually something like that yeah..
Just i want it to be made free..
But right now im just a guy with too much free time, and a strong will of learning python..

Anybody wanna help? if so, then mail me at [email]tobi-fp@hotmail.com[/email]

---

### Post by pmasiar on 2008-05-25
I don't want to discourage you, you are free to do whatever you want in your free time. But...

You, like most newbies, consider GUI important part of being easy to learn. It is not so. Set of simple tasks which input and output to console is much simpler to manage, and there are many websites with simple training tasks. See sticky FAQ and wiki in my sig. PythonChallenge.com is little more advanced.

Another trap for beginners is to try to automate something you do not understand how it works (learning programming). Only after you master it, you may start thinking how to automate it.

What you may want to do is to have forum for beginners to discuss solving those problems, but it will be hard to gather audience - beginners are beginners because they do not know where to start :-) Start with a blog and a wiki.

---

### Post by slavik on 2008-05-25
> **Tobi-fp said:**
> Well, actually something like that yeah..
Just i want it to be made free..
But right now im just a guy with too much free time, and a strong will of learning python..

Anybody wanna help? if so, then mail me at [email]tobi-fp@hotmail.com[/email]
One thing to keep in mind is that the turingscraft system doesn't actually just compile the code and run it. If an exercise says to declare x as an int and assign a value of 10 to it, it will complain and mark it wrong if you use y instead of x.

Not only that, but the code being inputed is actually wrapped around by a fair amount of code that does some heavy checking.

Also, turingscraft is not something that will teach you a language, it is more like homework, where a single topic will have 20-30 exercises (think math books).

---

### Post by Ann.A on 2008-05-25
This can be a fun or terrible experience depending on how its set up and the personalities of your teammates, but it sounds like the scope can grow quickly enough to discourage you and your team.

I think you should try to define your project so that its small enough that it can be accomplished and later extended if you want.  IE: How can this be broken down to see some progress?  Is this interactive?  How will the lessons be stored? What kind of format will the lessons be in: code or questions with fill in the blanks?  How will it be used: wizzard style like you are following a text book or a pick and choose section like [W3 Schools]("http://www.w3schools.com/")?  How are you guys going to collaborate, do you know about version control systems?  How much time are you willing to spend and expect your teammates to spend?

These questions are not here to discourage, only for you to research more and not become the blind leading the blind away from a great learning experience.

---

### Post by OpenFish on 2008-05-27
Now Guys N Gals lets not get ahead of our selfs and through the baby out with the bath water!!

i do agree that a tutor would take a massive amount of work and isn't a realistic goal for many people let alone a learner

but i do sometimes fancy some nice tools for looking at and analyzing library's

i find that Google usaly finds some helpful documents for me
but google always works best when u know what u are looking for witch is fine for us with a bit of expireance but much harder for newbs

i have found also that M$ gives some useful tools for getting info about there simple DLL's and when i used DLL's with VB6 i fond the add ons with the 'professional' IDE simply invaluable and wouldn't have made nearly as successful apps

this said, linux is a very different animal to M$ but i make me think

hears my first draft
(i am in the middle of my A levels, 4 more mods next week, so i didn't add a pygtk gui as im also doing loads of revision but u can use the two functions from a different script)
[PHP]
import sys, types

def _get_mod(modulePath):
# this function was taken from 
# http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/223972
# it didnt apper to have any lisen atached to it
	try:
		aMod = sys.modules[modulePath]
		if not isinstance(aMod, types.ModuleType):
			raise KeyError
	except KeyError:
		# The last [''] is very important!
		aMod = __import__(modulePath, globals(), locals(), [''])
		sys.modules[modulePath] = aMod
	return aMod
 # every thing down is mine --> OpenFish, Isle of Man, Please Keep it open
 # This library is distributed in the hope that it will be useful,
 # but WITHOUT ANY WARRANTY; without even the implied warranty of
 # MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
 # Library General Public License for more details.
 # Thank U
def myBit(lib):
	ans = {}
	try:
		lb = _get_mod(lib)
		for at in dir(lb):
			ans[ at ] = getattr(lb, at)
	except ImportError:
		print 'Just Cant Find the Damn Libry'
	return ans
	
def _main():
	print 'Hello There (dont foget h)'
	locat = 'sys'
	while True:
		try:
			a = str(raw_input(' :'))
		except KeyboardInterrupt:
			print '' # makes ctl-C exit a lot cleaner and less messy
			print 'U could have just hit return!'
			sys.exit()
		args = a.split(' ')
		if args == ['']: sys.exit()
		if args[0] == 'Help' or args[0] == 'help' or args[0] == 'h':
			print 'Please use me to help u with python'
			print '  '
			print '  getLibs		find all libs in  sys.modules'
			print '  Lib *			used to test if libry is findable'
			print '  Select Lib *		selects libry for finding a Atribute'
			print '  Atribute * fromLib	used to test if libry has Atribute'
			print '  '
			print '  g		alius for getLibs'
			print '  l		alius for Lib -- this is intresting try :l pygtk'
			print '  s		alius for Select Lib'
			print '  a		alius for Atribute'
		if args[0] == 'getLibs' or args[0] == 'get' or args[0] == 'g':
			print sys.modules
		if args[0] == 'Lib' or args[0] == 'lib' or args[0] == 'l':
			#try:
				#a = _get_mod(args[1])
				#print dir(a)
			dic = myBit(args[1])
			for at in dic.keys():
				tmp = str(at) +'\t'+ str(dic[at])
				print tmp.expandtabs(15)
			#except ImportError:
			#	print 'Just Cant Find the Damn Libry'
		if args[0] == 'Select' or args[0] == 'sel' or args[0] == 's':
			locat = args[1]
		if args[0] == 'Atribute' or args[0] == 'atr' or args[0] == 'a':
			if len(args)==2:
				aFunc = getattr(_get_mod(locat), args[1])
				print aFunc
			elif len(args)==3:
				aFunc = getattr(_get_mod(args[2]), args[1])
				print aFunc
if __name__ == "__main__":
# if u want to use my tui then use $python thisFile.py
# if u want to use _get_mod then place this file in the
# same directory and add 'import thisFile.py' to ur script
# or add
# modulePath = '/path/to/lib.py'
# aMod = __import__(modulePath, globals(), locals(), [''])
# sys.modules[modulePath] = aMod
	_main()
[/PHP]

---

