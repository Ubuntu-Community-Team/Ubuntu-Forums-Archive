---
title: "Python call a variable from a function"
date: 2011-08-29
forum: Programming Talk
---

### Post by Affrikka on 2011-08-29
Hey all,

I'm trying to make a text-based rpg in python (it will be my first.. shall we say 'major' project and I've hit a road block with the battle functions.

I have a function, let's call it 'enemy' that has two variables (for now, until later when I figure it out and I can make it more advanced)

```
 def enemy():
      hp = 20
      atk = 1

```

and I have our hero:

```
 def hero():
      hp = 20
      atk = 3

```

What I'm trying to do is have a thing that subtracts our hero's attack power from the enemy's hp.

So far, this is what I can come up with:

```

def attack():
		hit_miss = random.randint(1,100)
		if hit_miss < 79:
			x = enemy.hp - hero.atk
			print "You hit! His health is now", x
		else:
			print "You miss!"

attack()

```

But it gives an error, saying "function enemy() has no attribute 'hp.'"
So how do I turn the variable 'hp' into an attribute?

I do realize there are better ways of going about doing this, after I get this part figured out I am going to make an enemy class and a hero class, but I wanted to start off simple first :P

Of course, if there is anything I'm doing totally wrong with this little section of the game and anyone has some awesome better way of doing it, please tell me!



Thanks,



Mathieux

---

### Post by Bachstelze on 2011-08-29
That's not how functions work. You have to use some kind of data structure, it can be a class but a dictionary should also work reasonably well.

---

### Post by Affrikka on 2011-08-29
Well I did have it working under classes, but then what's the point of OOP if you have to make a class for each different type of enemy? For example if I had a grunt, a guard and a warlord, I would have to make a class for each one- doesn't that defeat the purpose of OOP? From my understanding, a class is like, "all enemies have hit points, attack and defence." and then I can create an object for each enemy (which, up until this point, I thought were functions, but if they aren't, what do you use to create an object belonging to a class?) and just adjust the stats for each object.

I don't necessarily need to know all the exact code for it all, but if you could point me in a general direction of where to go and what to look for, that would be awesome.

---

### Post by Senesence on 2011-08-29
Make a class called Fighter:

[PHP]
class Fighter:

	def __init__(self, points_attack, points_defense):

		self.points_attack = points_attack
		self.points_defense = points_defense

	def attackFighter(self, fighter):
		fighter.points_defense -= self.points_attack

-------------------------

knight = Fighter(5, 10)
ogre = Fighter(7, 30)

knight.attackFighter(ogre)
ogre.attackFighter(knight)
[/PHP]

You can always subclass from Fighter for ogre and/or knight, if those two objects have some specific characteristics that are not shared with other fighters.

But if you just need them to have different attack/defense values, than a single Fighter class should be enough.

---

### Post by Bachstelze on 2011-08-29
It would look something like this:

```
Class Enemy:
    def __init__(self, hp, atk):
        self.hp = hp
        self.atk = atk

grunt = Enemy(hp=30, atk=1)
guard = Enemy(hp=40, atk=1)

```

It would make sense to have classes for different kinds of enemies if there is more difference between them than just attributes. For example some enemies could have a special power, and you would add a method implementing it to the class that represents that kind of enemy.

---

### Post by Affrikka on 2011-08-29
Thank you all so much! I was always confused about the whole __init__ thing, but that really cleared it up and I should be good to go! Thanks!

---

