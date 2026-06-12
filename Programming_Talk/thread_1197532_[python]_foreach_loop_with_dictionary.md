---
title: "[python] foreach loop with dictionary"
date: 2009-06-26
forum: Programming Talk
---

### Post by xZachtmx on 2009-06-26
Ok i have a dictionary that holds a list of items in the solar system like this:

```

self.objectList = {"Sun": "Star", "earth" : "Planet", "ISS":  "Satellite", "Mars": "planet"}

```

now, i need to make a foreach loop that should go like this (i know its not the right syntax which is why im asking)

foreach "planet" IN self.objectlist:
     #rendering code here

how would i actually go about doing this in python?

---

### Post by .Maleficus. on 2009-06-26
Try out this:
```
for key in self.objectList.keys():
```


Edit:  And a link to the [Python Docs page]("http://docs.python.org/library/stdtypes.html?highlight=keys#dict.keys") about it.

---

### Post by xZachtmx on 2009-06-26
ok i have this now:

```

        
    

def renderArea(self):
        for key in self.objectList.keys():
            if key == "planet":
                planet.planetRender(key)

```

and here is the list its talking about
```
sol.objectList = {"Sun": "Star" , "earth" : "planet
```

and i call the method.  But i dont think its working because in the planet.render method it is supposed to be given an object's name, in this case its earth but in the dictionary it isnt earth its "earth" with quotes.  How can i change it?

---

### Post by .Maleficus. on 2009-06-26
Sorry, I'm kind of lost.  What does your planetRender() method do?  You want to give planetRender() "earth" and have it print out "planet", is that what I'm getting?

---

### Post by simeon87 on 2009-06-26
An alternative would be the following:

```

p = {"Sun": "Star", "Earth": "Planet"}
for k, v in p.items():
    print k, v

```

---

### Post by xZachtmx on 2009-06-26
no no no.  Im using panda3d to make a 3d game so all the planetrender does is render whatever planet name is given to it.  But i need the quotes from the dictionary to be taken away so its just earth not "earth" like in the dictionary.

---

### Post by simeon87 on 2009-06-26
> **xZachtmx said:**
> no no no.  Im using panda3d to make a 3d game so all the planetrender does is render whatever planet name is given to it.  But i need the quotes from the dictionary to be taken away so its just earth not "earth" like in the dictionary.

What type of value does the planetRender method expect? The dictionary now contains strings, for both the keys as the values. Perhaps you need to convert the string first to some planet/star object that the render method expects.

---

### Post by .Maleficus. on 2009-06-26
> **xZachtmx said:**
> no no no.  Im using panda3d to make a 3d game so all the planetrender does is render whatever planet name is given to it.  But i need the quotes from the dictionary to be taken away so its just earth not "earth" like in the dictionary.
The quotes aren't given to the planetRender() method.  The quotes simply signify the string object.  For the quotes to given to planetRender(), they would need to be single quoted as well, ie, '"earth"'.  If Panda is looking for an earth object (not an "earth" string object) that would be your problem.  Are you going through a tutorial or something?  Do you have a link to it?

---

### Post by curvedinfinity on 2009-06-26
The point of a dictionary is to have some generic information that takes the place of an index number. So, instead of numbering each slot, you use strings for the keys (the most common application).

To have your program be more flexible, what you need to do is put more data behind each name.

For instance, make a class that abstracts a celestial object:
```

class CelestialObject:
	name = ''
	type = ''
	rgbColor = (255,255,255)
	radius = 1
	def __init__(self,name,type,rgbColor,radius):
		self.name = name
		self.type = type
		self.rgbColor = rgbColor
		self.radius = radius
	def render(self):
		#use the color and radius to draw
		return

```

Then make a dictionary that has a bunch of those:

```

objects = {}
objects['Sun'] = CelestialObject('Sun','star',(255,255,200),20)
#add more objects

```

Then when you want to draw them, just go through the list:
```

for name in objects.keys():
	if objects[name].type == 'planet':
		objects[name].render()

```

---

