---
title: "I made a little script, tell em what you think :D"
date: 2008-07-31
forum: Programming Talk
---

### Post by kitili on 2008-07-31
Allot of times I will mess up awnsers with stupid mistakes. This has been expesaly prominent in my chemistry class. So I decided to start making a script which can check my awnswers. :P Right now it only works with conversion of grams to moles to atoms, useing only a few elements, but eventualy I hope it can work with nomenclature, and calculating the number of valance e-, etc..

here's what I've written so far, tell me what you think :D constructive criticism is welcomed
```
#!/usr/bin/python
import sys

Br = {"es" : "Br", "en" : "Bromine", "pnum" : 35, "aaw" : 79.904, "g" : 17, "p" : 4 }

print 'Please insert element symbol (case sensative)'
element = input('>:  ')


print
print '  %---------------------------------------------%'
print '    Element Symbol :', '          ', element["es"]
print '    Elemnet Name :', '            ', element["en"]
print '    Periodic Number :', '         ', element["pnum"]
print '    Average Atomic Weight :', '   ', element["aaw"]
print '    Group :', '                   ', element["g"]
print '    Period :', '                  ', element["p"]
print '  %--------------------------------------------%'

print ''' 
--------Avalable Calculations--------
Calculate number of grams/moles/atoms (type 'gma')
'''

calculate = raw_input('>:  ')

if calculate == 'gma':
	print 'starting measurement ( grams / moles / atoms )'
	start = raw_input('>:  ')
	
	if start == 'grams':
		mass = float(raw_input('Mass (g) >: '))
		product = mass/element['aaw']
		
	if start == 'moles':
		mass = float(raw_input('Number of moles >: '))
		product = mass
			
	if start == 'atoms':
		mass = float(raw_input('Number of atoms >: '))
		product = mass/602200000000000000000000000 		
		
	print 'ending measurement ( grams / moles / atoms )'
	fin = raw_input('>:  ')	
	if fin == 'grams':
			print
			print '      ', '%------------------------%'
			print '     ', '', mass, start, 'of', element['en'], 'contains about', product*element['aaw'], 'grams'
			print '      ', '%------------------------%'
			print
				
	if fin == 'moles':
			print
			print '      ', '%------------------------%'
			print '     ', '', mass, start, 'of', element['en'], 'contains about', product, 'moles'
			print '      ', '%------------------------%'
			print
				
	if fin == 'atoms':
			print
			print '      ', '%------------------------%'
			print '     ', '', mass, start, 'of', element['en'], 'contains about', product*602200000000000000000000000, 'atoms'
			print '      ', '%------------------------%'
			print
		
else:
	print 'That is not an option'
	sys.exit()
```

---

### Post by ghostdog74 on 2008-07-31
use a  python dictionary instead of if/else like that. please read the documentation for how to create dictionaries

---

### Post by kitili on 2008-08-01
> **ghostdog74 said:**
> use a  python dictionary instead of if/else like that. please read the documentation for how to create dictionaries

ah, thank you, that is much esyier to work with

---

### Post by mssever on 2008-08-01
Also, try using descriptive variable names. Extreme abbreviations can easily get confusing.

Also, you might want to consider creating an Element class that stores data about the element. You can then create an instance for each element. It might me overkill for this project, but it's a good thing to know.

---

