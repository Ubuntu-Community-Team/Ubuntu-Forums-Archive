---
title: "ImportError from trying to run script, help needed (python)~"
date: 2008-06-29
forum: Programming Talk
---

### Post by myromance123 on 2008-06-29
Hi, I have been trying to learn game programming with python, and I had made my tank.py file. When i used the "from tank import Tank" to basically use the info from that file I get this annoying error and I dont know how to fix it:

  Traceback (most recent call last):
  File "<pyshell#3>", line 1, in <module>
    import tank
ImportError: No module named tank

  When it says no module named tank does it mean it cant find the file OR is the file not supposed to be saved as .py ?

  I have tried using the terminal, SciTE and IDLE to run this script but to no avail, so please help me understand my mistake(s).:)

---

### Post by raja on 2008-06-29
You have to make sure that -  
1. The names are right - remember that everything is cap sensitive
2. The module to import is in the python path or in the same directory

The filename will still have .py appended. 
I think the second point may be your problem. Navigate to the directory holding the module in Idle and try importing. Otherwise, it will help to put the source here.

---

### Post by myromance123 on 2008-06-30
Ok, I believe no.1 is not my problem and no.2 shouldnt be either. They are all in the same directory.

  By put the source here, you want to see the script right?

 tank.py:
```
>>> class Tank(object):
	
	def _init_(self, name):
		
		self.name = name
		self.alive = True
		self.ammo = 5
		self.armor = 60
		
	def _str_(self):
		
		if self.alive:
			return "%s (%i armor, %i shells)" %(self.name, self.armor, self.ammo)
		else:
			return "%s (DEAD)" % self.name
			
		def fire_at(self, enemy):
			
			if self.ammo >= 1:
				self.ammo -=1
				print self.name, "fires on", enemy.name
				enemy.hit()
			else:
				print self.name, "has no shells!"
				
			def hit(self):
				
				self.armor -= 20
				print self.name, "is hit!"
				if self.armor <= 0:
					self.explode()
					
				def explode(self):
					
					self.alive = False
					print self.name, "explodes!"
```

  tankgame.py:
```
from tank import Tank

tanks = { "a":Tank("Abba"), "b":("Barker"), "c":("Clorox")}
alive_tanks = len(tanks)

while alive_tanks > 1:
	
	print
	for tank_name in sorted( tanks.keys() ):
		print tank_name, tanks[tank_name]
		
	first = raw_input("Who fires?").lower()
	second = raw_input("Who at?").lower()
	
	try:
		first_tank = tanks[first]
		second_tank = tanks[second]
	except KeyError, name:
		print "No such tank!", name
		continue
		
	if not first_tank.alive or not second_tank.alive:
		print "One of those tanks is DEAD!!"
		continue
		
	print
	print "*" * 30
	
	first_tank.fire_at(second_tank)
	if not second_tank.alive:
		alive_tanks -= 1
		
	print "*" * 30
	
for tank in tanks.values():
	if tank.alive:
		print tank.name, "is the winner!"
		break
```

 These are not my own scripts, I am using them from a book for learning to use python in gaming. I followed the instructions and this is why I am at a loss to what Im doing wrong. Hopefully the code helps you figure it out.

---

### Post by ghostdog74 on 2008-06-30
its admirable what you are doing, learning Python using Pygame, however, my advice is still, to get the basics right. Learn all you can about Python first, before embarking on gaming.

---

### Post by raja on 2008-06-30
There were a few mistakes in the code (did you type them yourself?).

I have attached the files with the corrections. See now if you can run test.py without problems. I am able to do that.

---

### Post by myromance123 on 2008-06-30
I understand that learning python first makes it all easy, but I am learning how to make games with it so that I can actually apply it to something :P  
(Im thinking of how I can go about learning python where I can understand it and use it, just found python 2.0 quick referance so possiblities are open for me ~)

  Yes I did type it myself :)  I tried opening the file you gave and I get this error :
> /tmp/tank.tar-2.gz could not be opened, because the associated helper application does not exist. Change the association in your preferences.

 My archive manager doesnt support it, what do you use to open it?

---

### Post by rlameiro on 2008-06-30
> **myromance123 said:**
> I understand that learning python first makes it all easy, but I am learning how to make games with it so that I can actually apply it to something :P  
(Im thinking of how I can go about learning python where I can understand it and use it, just found python 2.0 quick referance so possiblities are open for me ~)

  Yes I did type it myself :)  I tried opening the file you gave and I get this error :


 My archive manager doesnt support it, what do you use to open it?

Are you on ubuntu?
first download and save the file to a folder, don't use it from the temp. The file must be named "tank.tar.gz" and not tank.tar-2.gz something happened there. If the filename still is named tank.tar-2.gz just rename it and strip the "-2" from the name and it will opened. Tarball + Gzip are the compression formats that are really suported by GNU/linux so you shouldn't have any problem with it.

About the script, i ran it and it worked, just didn't understood the location but worked. keep going!

---

