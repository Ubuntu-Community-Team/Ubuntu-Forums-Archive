---
title: "A little python help"
date: 2008-07-31
forum: Programming Talk
---

### Post by Visti on 2008-07-31
Hi guys, I'm trying to implement a small change in Frets of Fire, but I've seem to run into a wall of sorts.. Let me show you the original code here:

```
#self.engine.resource.load(self, "song", lambda: loadSong(self.engine, songName, library = libraryName, part = [player.part for player in self.playerList]), synch = True, onLoad = self.songLoaded)
   self.engine.resource.load(self, "song", lambda: loadSong(self.engine, songName, library = libraryName, part = [player.part for player in self.playerList], practiceMode = self.playerList[0].practiceMode), synch = True, onLoad = self.songLoaded)


   #myfingershurt: new loading place for "loading" screen for song preparation:
   #blazingamer new loading phrases
   phrase = self.song.info.loading
   if phrase == "":
     phrase = random.choice(Theme.loadingPhrase.split(","))
     if phrase == "None":
       i = random.randint(0,4)
       if i == 0:
         phrase = "Let's get this show on the Road"
       elif i == 1:
         phrase = "Impress the Crowd"
       elif i == 2:
         phrase = "Don't forget to strum!"
       elif i == 3:
         phrase = "Rock the house!"
       else:
         phrase = "Jurgen is watching"
   # glorandwarf: show the loading splash screen and load the song synchronously
   #Dialogs.showLoadingScreen(self.engine, lambda: self.song, text = phrase)

   splash = Dialogs.showLoadingSplashScreen(self.engine, phrase)
```

Basically, this shows the player a random phrase while the level is loading. What I want to do is check for a variable (whether the player is playing as drums or guitar) and then show a different set of phrases if he/she is..

Basically, my thought was to use an *if* statement to check for the variable and then put the original code in the *else* block, thus (in my head) bypassing my hacky code if the variable doesn't check out, but it's not working out for me.. 

Here's what I tried:

```
    #self.engine.resource.load(self, "song", lambda: loadSong(self.engine, songName, library = libraryName, part = [player.part for player in self.playerList]), synch = True, onLoad = self.songLoaded)
    self.engine.resource.load(self, "song", lambda: loadSong(self.engine, songName, library = libraryName, part = [player.part for player in self.playerList], practiceMode = self.playerList[0].practiceMode), synch = True, onLoad = self.songLoaded)


    #myfingershurt: new loading place for "loading" screen for song preparation:
    #blazingamer new loading phrases
    phrase = self.song.info.loading
    if self.guitars[0].isDrum:
    	if phrase == "":
		phrase = random.choice(Theme.loadingPhrase.split(","))
		if phrase == "None":
			i = random.randint(0,2)
		 	if i == 0:
				phrase = "Don't forget to drum!"
			elif i == 1:
				phrase = "Hit them hard!"
			else:
				phrase = "Remember to count!"
    else:
    if phrase == "":
      phrase = random.choice(Theme.loadingPhrase.split(","))
      if phrase == "None":
        i = random.randint(0,4)
        if i == 0:
          phrase = "Let's get this show on the Road"
        elif i == 1:
          phrase = "Impress the Crowd"
        elif i == 2:
          phrase = "Don't forget to strum!"
        elif i == 3:
          phrase = "Rock the house!"
        else:
          phrase = "Jurgen is watching"
    # glorandwarf: show the loading splash screen and load the song synchronously
    #Dialogs.showLoadingScreen(self.engine, lambda: self.song, text = phrase)

    splash = Dialogs.showLoadingSplashScreen(self.engine, phrase)

    #splash = Dialogs.showLoadingSplashScreen(self.engine, phrase)
```


I have no idea what I'm doing wrong, but it's probably very basic. Any help would be greatly appreciated!

---

### Post by pmasiar on 2008-07-31
Simple tip: Random answer can be generated more obviously:

[php]
import random

phrases = [ "Let's get this show on the Road",
            "Impress the Crowd",
            ...
          ]

phrase = random.choice(phrases)
[/php]

---

### Post by nvteighen on 2008-07-31
> **pmasiar said:**
> Simple tip: Random answer can be generated more obviously:

[php]
import random

phrases = [ "Let's get this show on the Road",
            "Impress the Crowd",
            ...
          ]

phrase = random.choice(phrases)
[/php]
Don't know if you've impressed the crowd, but surely me!

---

### Post by Titan8990 on 2008-07-31
I am a beginner myself but wouldn't it be better to use a tuple here? If not, any reason why?

```
import random

phrases = ( "Let's get this show on the Road",
            "Impress the Crowd",
            ...
          )

phrase = random.choice(phrases)
```

---

### Post by Visti on 2008-07-31
> **pmasiar said:**
> Simple tip: Random answer can be generated more obviously:

[php]
import random

phrases = [ "Let's get this show on the Road",
            "Impress the Crowd",
            ...
          ]

phrase = random.choice(phrases)
[/php]

Neat! I'll keep that in mind. I was just trying to keep as close to the code I was modifying as possible to cause less confusion. But is the if statement set up correctly?

What I don't understand is that even if drums are not selected it still doesn't work, which confuses me, because I thought it would then completely bypass what I had written and run the original code as originally intended..

---

### Post by pmasiar on 2008-07-31
> **Titan8990 said:**
> I am a beginner myself but wouldn't it be better to use a tuple here? If not, any reason why?

Tuple is **ordered** structure of possibly values  of different types (struct), each has own place and meaning. In list/array, all items are supposed to be same type, and you process them one by one.

---

### Post by Titan8990 on 2008-07-31
My speculation is something is preventing this statement from being true:

if phrase == "":

In the second set of nested if statements.

> Tuple is **ordered** structure of possibly values of different types (struct), each has own place and meaning. In list/array, all items are supposed to be same type, and you process them one by one.

This is good to know as I thought the only difference was that a list was mutable while a tuple was not.

---

### Post by WW on 2008-07-31
Is the code shown in the original post exactly what you are working with?  If so, it looks like you have not indented the code in the "else" part of the outermost if/else statement.

---

### Post by WW on 2008-07-31
> **pmasiar said:**
> Tuple is **ordered** structure of possibly values  of different types (struct), each has own place and meaning. In list/array, all items are supposed to be same type, and you process them one by one.
Huh?  From the first paragraph of [Section 3.1.4](http://docs.python.org/tut/node5.html#SECTION005140000000000000000) of the tutorial:
> 
List items need not all have the same type.

```

>>> a = ['spam', 'eggs', 100, 1234]
>>> a
['spam', 'eggs', 100, 1234]

```
If they are "supposed to be of the same type", why would the first example not be?

---

### Post by pmasiar on 2008-07-31
> **WW said:**
> List items need not all have the same type.

Sure they don't have to be same type, but how you will process different types in loop? (unless you can rely on polymorphism, but then they are same duck-type)? You usually don't loop over the tuple but unpack it to give specific name to each component:

a, b, c = mytuple

Certainly that is deeper semantic difference in using tuples vs lists than just remembering which one is mutable.

---

### Post by WW on 2008-07-31
Loops and unpacking work for both:
```

>>> tpl = (1,'spam',98.6)
>>> for x in tpl:
...     print x
... 
1
spam
98.6
>>> lst = [1,'spam',98.6]
>>> x,y,z = lst
>>> x
1
>>> y
'spam'
>>> z
98.599999999999994
>>> 

```

---

### Post by pmasiar on 2008-07-31
> **WW said:**
> Loops and unpacking work for both:

Of course. Python is not Java, you have all the flexibility you may want, and more.

I am talking about idiomatic use.

---

### Post by days_of_ruin on 2008-07-31
> **Titan8990 said:**
> My speculation is something is preventing this statement from being true:

if phrase == "":

In the second set of nested if statements.



This is good to know as I thought the only difference was that a list was mutable while a tuple was not.

That is the only difference.

---

### Post by nanotube on 2008-08-01
> **pmasiar said:**
> 

Certainly that is deeper semantic difference in using tuples vs lists than just remembering which one is mutable.

due to being immutable, tuples can be used as keys in a dictionary. 
that's a pretty important difference, too. :)

---

