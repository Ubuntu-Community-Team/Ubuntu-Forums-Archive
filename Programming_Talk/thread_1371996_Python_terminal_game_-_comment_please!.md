---
title: "Python terminal game - comment please!"
date: 2010-01-04
forum: Programming Talk
---

### Post by DanielJackins on 2010-01-04
So I've started to develop a text game with python, and I was wondering if some people could check out/try my code and comment and/or critique it. Here goes!

```

from random import *
import cPickle as pickle

class Character:
    def __init__(self, name, class_type):
        self.name = name
        self.type = class_type
    def stats(self, class_type):
        if class_type == 'Warrior':
            self.strength = 10
            self.dexterity = 5
            self.vitality = 10
            self.energy = 3
            self.hp = 3*self.vitality
            self.mp = 5*self.energy
        elif class_type == 'Archer':
            self.strength = 5
            self.dexterity = 12
            self.vitality = 6
            self.energy = 5
            self.hp = 3*self.vitality
            self.mp = 5*self.energy
        elif class_type == 'Mage':
            self.strength = 4
            self.dexterity = 4
            self.vitality = 5
            self.energy = 15
            self.hp = 3*self.vitality
            self.mp = 5*self.energy
        self.experience = 0
        self.level = 1
        self.money = 0
            
            
class Monster(Character):
    def __init__(self, name):
        self.name = name
    def stats(self, level):
        self.strength = randint(1,level)
        self.dexterity = randint(1,level)
        self.vitality = randint(1,level)
        self.energy = randint(1,level)
        self.hp = 3*self.vitality
        self.mp = 5*self.energy
        self.money = randint(1,26)


def battle(character, monster):
    while character.hp > 0 and monster.hp > 0:
        print 'Character health: ', character.hp
        print 'Monster health: ', monster.hp
        choice = input("1) Attack 2) Defend 3) Magic 4) Run Away : ")
        if choice == 1:
            monster.hp -= randint(1,character.strength)
            character.hp -= randint(1,monster.strength)
        elif choice == 2:
            character.hp -= (randint(1,monster.strength))/2
        elif choice == 3:
            print 'Please choose a spell: '
        elif choice == 4:
            run_success = randint(0,10)
            if run_success > 1:
                print 'Ran away!'
            else: print 'Failed to escape!'
        if monster.hp <= 0:
            print 'You win! You gained one experience, and recieved ' + str(monster.money) + ' gold!'
            character.experience += 1
            character.money += monster.money
        elif character.hp <= 0: print 'You died'


choice = input('1) Start a new game or 2) load? (enter 1 or 2) ')
if choice == 1:
    char = Character(raw_input('What is your characters name?: '), raw_input('What class is your character? (Type Warrior, Archer, or Mage): '))
    char.stats(char.type)
elif choice == 2:
    char = pickle.load(open('/home/daniel/Desktop/Game/'+raw_input('Enter your character name: ')))


while 1:
    print 'Welcome to town! What would you like to do?'
    print '1) Random battle'
    print '2) Visit the shop'
    print '3) Go to the hospital'
    print '4) View character info'
    print '5) Save and quit'
    choice = input('Please enter your choice: ')
    if choice == 1:
        slime = Monster('Slime')
        slime.stats(5)        
        battle(char,slime)
    elif choice == 2:
        pass
    elif choice == 3:
        if raw_input('It costs 15 gold to be healed. Accept? (Yes/No) ') == 'Yes':
            if char.money <= 15:
                print 'Not enough money!'
            else:
                char.hp = 3*char.vitality
                char.money -= 15
    elif choice == 4:
        print 'You are level', char.level
        print 'You have', char.experience, 'experience.'
        print 'You have', char.money, 'gold.'
        print 'You have', char.strength, 'strength.'
        print 'You have', char.vitality, 'vitality.'
        print 'You have', char.energy, 'energy.'
        print 'You have', char.dexterity, 'dexterity.'
    elif choice == 5:
        break

pickle.dump( char, open( char.name, "w" ) )

```

I have never done something similar to this before so it's all new, so any help or suggestions is welcome. 

Also, if you plan on running it you'll have to change the directory to wherever you put the game file, in the pickle.load line.

Next I was going to try and incorporate some kind of levelling system, but I couldn't think of how. I thought I'd make a dictionary and compare the experience somehow to see what level the character is, but I want it to alert the player when he reaches the next level only once (when he first reaches it).

Thanks!

---

### Post by DanielJackins on 2010-01-04
Okay so I made lots of changes, and figured out a (temporary) levelling system, so now just any comments or suggestions would be greatly appreciated :)

```

from random import *
import cPickle as pickle
import os

class Character:
    def __init__(self, name, class_type):
        self.name = name
        self.type = class_type
        self.assign_stats(class_type)
    def assign_stats(self, class_type):
        if class_type == 'w':
            self.stats = {'strength' : 10, 'dexterity' : 5, 'vitality' : 10, 'energy' : 3}
            self.stats['hp'] = 3*self.stats['vitality']
            self.stats['mp'] = 5*self.stats['energy']
        elif class_type == 'a':
            self.stats = {'strength' : 5, 'dexterity' : 12, 'vitality' : 6, 'energy' : 5}
            self.stats['hp'] = 3*self.stats['vitality']
            self.stats['mp'] = 5*self.stats['energy']
        elif class_type == 'm':
            self.stats = {'strength' : 4, 'dexterity' : 4, 'vitality' : 5, 'energy' : 15}
            self.stats['hp'] = 3*self.stats['vitality']
            self.stats['mp'] = 5*self.stats['energy']
        self.stats['experience'] = 0
        self.stats['level'] = 1
        self.stats['money'] = 0
        self.stats['stat_points'] = 0
            
            
class Monster:
    def __init__(self, name, level):
        self.name = name
        self.assign_stats(level)
    def assign_stats(self, level):
        self.stats = {'strength' : randint(1,level), 'dexterity' : randint(1,level),
                      'vitality' : randint(1,level), 'energy' : randint(1,level)}
        self.stats['hp'] = 3*self.stats['vitality']
        self.stats['mp'] = 5*self.stats['energy']
        self.stats['level'] = level
        self.stats['money'] = randint(1,10*self.stats['level'])
        
def hit_continue(Prompt='Press enter to continue...'):
    raw_input(Prompt)

def battle(character, monster):
    os.system('clear')
    print 'You encountered a', monster.name + '!\n'
    while character.stats['hp'] > 0 and monster.stats['hp'] > 0:
        print character.name + ' health: ' + str(character.stats['hp'])
        print monster.name + ' health: ' + str(monster.stats['hp']) + '\n'
        choice = raw_input("[a]ttack, [d]efend, [m]agic, [r]un away : ")
        print
        if choice == 'a' and character.stats['hp'] > 0 and monster.stats['hp'] > 0:
            monster_damage = randint(1,monster.stats['strength'])
            character_damage = randint(1,character.stats['strength'])
            monster.stats['hp'] -= character_damage
            character.stats['hp'] -= monster_damage
            print 'You hit the ' + monster.name + ' for ' + str(character_damage) + '!'
            print 'The ' + monster.name + ' hits you for ' + str(monster_damage) + '!\n'
            hit_continue()
            os.system('clear')
        elif choice == 'd':
            character.stats['hp'] -= (randint(1,monster.stats['strength']))/2
        elif choice == 'm':
            print 'Please choose a spell: '
        elif choice == 'r':
            run_success = randint(0,10)
            if run_success > 1:
                print 'Ran away!'
                break
            else: 
                print 'Failed to escape!'
                print 'The ' + monster.name + ' hits you for ' + str(monster_damage) + '!\n'
                hit_continue()
        if monster.stats['hp'] <= 0:
            print 'You win! You gained one experience, and recieved ' + str(monster.stats['money']) + ' gold!'
            hit_continue()
            character.stats['experience'] += 1
            character.stats['money'] += monster.stats['money']
        elif character.stats['hp'] <= 0: print 'You died'
        if character.stats['experience'] >= 2**character.stats['level']:
            character.stats['level'] += 1
            character.stats['experience'] = 0
            character.stats['stat_points'] += 5
            print '\nYou have gained a level! You are now level', character.stats['level'], '.'
            while character.stats['stat_points'] > 0:
                print 'You have', character.stats['stat_points'] , 'unused stat points:'
                choice = raw_input('[s]trength, [v]itality, [d]exterity, [e]nergy, or [c]ancel: ')
                if choice == 's':
                    character.stats['strength'] += 1
                    character.stats['stat_points'] -= 1
                elif choice == 'v':
                    character.stats['vitality'] += 1
                    character.stats['stat_points'] -= 1
                elif choice == 'd':
                    character.stats['dexterity'] += 1
                    character.stats['stat_points'] -= 1
                elif choice == 'e':
                    character.stats['energy'] += 1
                    character.stats['stat_points'] -= 1
                elif choice == 'c':
                    break
                else:
                    hit_continue( '\nInvalid input, try again.' )
            
            
os.system('clear')

choice = '0'
while choice != '1' and choice != '2':
    choice = raw_input('1) Start a new game or 2) load? (enter 1 or 2) ')
    print
    if choice == '1':
        char = Character(raw_input('What is your characters name?: '), 
               raw_input('\nWhat class is your character? [w]arrior, [a]rcher, or [m]age: '))
    elif choice == '2':
        char = pickle.load(open('Saves/'+raw_input('Enter your character name: ')))
    else: print 'Invalid input, try again.'


while 1:
    os.system('clear')
    print 'Welcome to town! What would you like to do?\n'
    print '1) Random battle'
    print '2) Visit the shop'
    print '3) Go to the hospital'
    print '4) View character info'
    print '5) Save and quit\n'
    print 'Current HP:' , char.stats['hp'], '('+str(3*char.stats['vitality'])+')'
    print 'Current MP:' , char.stats['mp'], '('+str(5*char.stats['energy'])+')\n'
    choice = raw_input('Please enter your choice: ')
    print
    if choice == '1':
        slime = Monster('Slime',5)
        zombie = Monster('Zombie', 10)        
        battle(char,zombie)
    elif choice == '2':
        pass
    elif choice == '3':
        if raw_input('It costs 15 gold to be healed. Accept? (Yes/No) ') == 'Yes':
            if char.stats['money'] <= 15:
                print 'Not enough money!'
            else:
                char.stats['hp'] = 3*char.stats['vitality']
                char.stats['money'] -= 15
                print
                hit_continue('Healing successful!')
    elif choice == '4':
        os.system('clear')
        print 'You are level', char.stats['level']
        print 'You have', char.stats['experience'], 'experience.'
        print 'You have', char.stats['money'], 'gold.'
        print 'You have', char.stats['strength'], 'strength.'
        print 'You have', char.stats['vitality'], 'vitality.'
        print 'You have', char.stats['energy'], 'energy.'
        print 'You have', char.stats['dexterity'], 'dexterity.\n'
        hit_continue()
    elif choice == '5':
        os.system('clear')
        print 'Thanks for playing!\n'
        break
    else:
        print
        hit_continue( 'Invalid input, try again.' )

pickle.dump( char, open( 'Saves/' + str(char.name), "w" ) )

```

---

### Post by nvteighen on 2010-01-04
Hm... You could get rid of the "char_type" thing in Character by using inheritance. Look at [http://docs.python.org/tutorial/classes.html#inheritance](http://docs.python.org/tutorial/classes.html#inheritance)

---

### Post by Can+~ on 2010-01-04
Ok, I have a lot of suggestions:

**About the coding style**

[LIST=1]
[*]Instead of doing this, which is cumbersome:
[PHP]print character.name + ' health: ' + str(character.stats['hp'])[/PHP]
Prefer using C-style formatting (Python < 2.6):
[PHP]print "%s health: %d" % (character.name, character.stats['hp'])[/PHP]
Or the new formatting method of strings (Python >= 2.6, 3):
[PHP]print "{0.name} health: {0.stats[hp]}".format(character)[/PHP]
[*]This:
[PHP]choice = raw_input("[a]ttack, [d]efend, [m]agic, [r]un away : ")[/PHP]
Is the typical switch-case in C, which in python can be achieved more efficiently with a dictionary and functions
[PHP]def attack(): pass
def magic(): pass
def defend(): pass
def escape(): pass

actions = {'a': attack, 'm': magic, 'd': defend, 'e': escape}[/PHP]

It would be better if this actions would be performed by the class "Character", also, as they are the ones who perform said actions.
[*]Multiline strings:
[PHP]        print 'You are level', char.level
        print 'You have', char.experience, 'experience.'
        print 'You have', char.money, 'gold.'
        print 'You have', char.strength, 'strength.'
        print 'You have', char.vitality, 'vitality.'
        print 'You have', char.energy, 'energy.'
        print 'You have', char.dexterity, 'dexterity.'[/PHP]

Can be worked better like:
[PHP]print """You have {0.experience} experience
You have {0.money} gold
...""".format(character)[/PHP][/LIST]

**About the organization**

[LIST=1]
[*]As nvteighen, consider instantiation and polymorphism for the "Character" class. Character can be anything that can fight, level, and other things. For example:
[PHP]class Character(object):
	
	def __init__(self):
		self.name = "Character"

	def magic(self, target):
		print "Inflicting magical damage on {0}".format(target)
	
	def attack(self, target):
		print "Inflicting physical damage on {0}".format(target)

	def __str__(self):
		return "{0.name}: ...".format(self)

class Wizard(Character):

	def __init__(self):
		self.name = "Wizard"

wizard = Wizard()
wizard.magic("Ogre")
print wizard[/PHP]

That way, you specify methods and attributes for all characters.

[*]Stat and damage calculation:

Now, here's a little complex topic. Calculating things. I'll use WoW as an example. In WoW, the server stores a file (in memory) which is a huge fixed-size table that contains constant values about monsters and characters, sorted over the ID of the creature.

You can imagine that WoW, being a massive game as it is, they had to choose a proper method to manage a huge range of monsters. Imagine having to delve into the code, recompile and set up the server if you wanted to tweak a monster/character damage.

That's why they preferred this method, in which the formula is known and it's the same for all creatures, but it's presented in linear-equation form. For example, your code, what if the wizard has extra mana, so it should receive a higher bonus of mana per point of energy and also, let's add an attribute as intelligence, therefore, the formula for everyone:

```
mp = energy*class_energy_multiplier + intelligence*class_int_multiplier
```

Say that the melee class will have a intelligence multiplier of 0, so it's energy is only determined by it's energy. The magician has a higher constant, etc. That way, you can tweak the formula in any moment just by changing constant values outside of it. In fact, you could add even more parameters (thus, giving you more granular control over all things)

```
mp = class_base_mp + energy*class_energy_multiplier*global_energy_multiplier + intelligence*class_int_multiplier*global_int_multiplier
```

In the case of your code, probably it's nothing important, but it's a good start point to get the idea of scalability. Working on a huge server/game and depending on constant, fixed numbers inside the code is terrible for maintenance later.
[/LIST]

---

### Post by Thought_Police on 2011-11-15
Looks a lot like what I am working on...  On first impression, it is a lot of good code but kind of slim on story line and character generation...

Here is a sample of my character generator, just so you know I am not full of it:

---

