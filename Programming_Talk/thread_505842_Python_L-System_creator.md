---
title: "Python L-System creator"
date: 2007-07-20
forum: Programming Talk
---

### Post by red_Marvin on 2007-07-20
I'm trying to learn python, and am slowly starting to appreciate the small differences from languages in the c syntax class, so I thought I'd share this little code snippet I've written, and in the meantime ask if there's anything you'd solve differently, especially in the lsystem class, but also in the demonstration program (which are more c-like implementation wise)

The snippet iterates simple [L-Systems]("http://en.wikipedia.org/wiki/L-system"), and the demo program creates a small dragon curve from the definition on wikipedia.

You will need the to have pyx module (python-pyx) installed (since that was the first easy interfaceable image exporter I found) to run the demo...

Run with *python lsystem.py* or *chmod +x lsystem.py* and treat as a normal executable.
Code is GPL.

```

#! /usr/bin/env python

class lsystem:
	"""L-system
	A small class for creating and iterating L-systems
	Usage: l = lsystem(rules, depth)
	rules is a dictionary containing the following keys and values:
		constants = string containing characters that do not change during iteration
		variables = string containing characters that do change during iteration
		axiom = initial setup of constants and variables
	For each variable there should also be a key with the variables name with the value
	a string containing what the variable changes into during iteration.
	depth is the numer of iterations.
	the result is stored as a stringin the public variable result"""
	# I don't know if it's a good thing that the doc string is bigger than the implementation ^_^;;
	def __init__(self, rules = None, depth = 0):
		self.result = None
		if rules is not None:
			rdstr = rules['axiom']
			for i in range(0, depth):
				wrstr = ''
				for char in rdstr:
					if char in rules['variables']:
						wrstr += rules[char]
					elif char in rules['constants']:
						wrstr += char
				rdstr = wrstr
			self.result = rdstr


# Demonstration
if __name__ == '__main__':
	try:
		from pyx import *
		ruleset = {'constants':'+-',
			   'variables':'XYF',
			   'X':'X+YF+',
			   'Y':'-FX-Y',
			   'F':'F',
			   'axiom':'FX'}
		print 'Generating a dragon curve...          ',
		l = lsystem(ruleset, 10)
		print 'finished, result is',len(l.result),'characters long.'
		print 'Starting conversion to coordinates... ',
		dmodx = (1, 0, -1, 0)
		dmody = (0, 1, 0, -1)
		x = 0
		y = 0
		d = 0
		c = canvas.canvas()
		for char in l.result:
			if char == 'F':
				newx = x+dmodx[d]*.1
				newy = y+dmody[d]*.1
				c.stroke(path.line(x, y, newx, newy))
				x = newx
				y = newy
			if char == '+':
				d += 1
				if d > 3: d = 0
			if char == '-':
				d -= 1
				if d < 0: d = 3
		print 'finished.'
		print 'Starting writing file...              ',
		c.writeEPSfile("DragonCurve")
		print 'finished.'
		print 'The file is saved as DragonCurve.eps'
	except:
		print """
		Couldn't run demo, probably since you haven't installed pyx."
		If you are running Ubuntu you might want to try"
		sudo apt-get install python-pyx
		"""
```

---

