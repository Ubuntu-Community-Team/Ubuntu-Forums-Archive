---
title: "[SOLVED] [Python] I-don't-get-it error message on huge if statement"
date: 2008-09-13
forum: Programming Talk
---

### Post by fiddler616 on 2008-09-13
After my last Python thread got solved, I was making an effort to think two and three times about posting a new help thread. But I really don't understand this error:
```
if pos == 1 or pos == 3 or pos == 5 and user_input == 6:
                                                           ^
SyntaxError: invalid syntax

```
And here's the code block it's coming from:
```
while running == True:
	print map[pos]
	asking = True
	while asking == True:
		user_input = int(raw_input("What now?")
		if pos == 1 or pos == 3 or pos == 5 and user_input == 6:
			print "Invalid"
			invalidity = True
		elif pos == 0 or pos == 1 and user_input == 8:
			print "Invalid"
			invalidity = True
		elif pos == 0 or pos == 2 or pos == 4 and user_input == 4:
			print "Invalid"
			invalidity = True
		elif pos == 4 or pos == 5 and user_input == 2:
			print "Invalid"
			invalidity = True
		elif user_input == 8 and invalidity == False:
			pos = (pos - vertical)
		elif user_input == 4 and invalidity == False:
			pos = (pos - 1)
		elif user_input == 6 and invalidity == False:
			pos = (pos + 1)
		elif user_input == 2 and invalidity == False:
			pos = (pos + vertical)
		asking = False
	print "That's all folks!"
	running = False
```
Where I defined a dictionary--'map', invalidity = False, vertical = two, and running = True earlier on.
Here's my previous thread, in case you care:
[http://ubuntuforums.org/showthread.php?t=912915](http://ubuntuforums.org/showthread.php?t=912915)
Thanks!

---

### Post by y-lee on 2008-09-13
ah shouldn't this line:
> user_input = int(raw_input("What now?")

be user_input = int(raw_input("What now?")**)**?

btw I didn't look at the rest your logic is a complete mess :confused:

---

### Post by fiddler616 on 2008-09-13
Dang.
That's embarassing.
Here I am looking at my if statement from every angle I can think of...
:(
Thanks you though

On logic:
First, make sure that you're thinking of my map, which looks like this:
```

0 1
2 3
4 5

```
From 3, I want the person to be able to move to 2 (pos - 1), 1 (pos - vertical)(which in this case is two), and 5 (pos + vertical). However, if the person goes 'east' (pos + 1, they'll end up in four, instead of generating a "You can't do that!" error message. I raised the question to nvteighen, who thought up the dictionary in the first place, and he said:

> But there's a little solution to that: notice that such situation (only if you start counting from 0) will only occur when you are either in the last or first element of a row. All last elements are multiples of the amount of cols minus 1 (in other words, the modulo is (cols - 1)), and all first elements are multiples of the amount of cols (the modulo is 0). In Python (and in many programming languages), you take the modulo of x in y by using x % y, so, before moving, you'd have to check if the (current position % cols) is either (cols - 1) or 0 in order to detect whether you're in the border or not.
But that really doesn't make sense when I only have two columns. I'm making a 'practice', small (2x3) version before I make the real (5x5) one, because I want to make sure I have stuff like gameplay mechanics worked out before then.
...
Dang, that was long. Sorry

---

### Post by y-lee on 2008-09-13
> Dang.
That's embarassing.
Here I am looking at my if statement from every angle I can think of...

:lolflag: yeah sometimes python error messages are not very smart. Errors can be caused by the code above and sometimes it helps to back away from your code and take a break for a while. At least it does for me.

As to your logic I see what you are doing but my criticism was directed at the long if elif statement. That is never a good thing. I always use in C terminology an array of function pointers to simplify code like that to where it is readable. Also i note alot of duplicated code, namely the lines

```
print "Invalid"
invalidity = True
```

as well as your complex logical statements. I would try to find a way to simplify that using some math trickery. Just a thought :)

---

### Post by fiddler616 on 2008-09-13
> Array of function pointers
You lost me
> simplify that using some math trickery
You found me again. I could just make a function. Edit: For the print "Invalid", invalidity = True part. Misread what I was answering, sorry. </edit>
I've been thinking of mathematical trickery for the 4 elifs, but nothing's coming to mind since it's so arbitrary.

---

### Post by pp. on 2008-09-13
> **fiddler616 said:**
> 
But that really doesn't make sense when I only have two columns. I'm making a 'practice', small (2x3) version before I make the real (5x5) one, because I want to make sure I have stuff like gameplay mechanics worked out before then.

That way lies ruin. Once you change your 'universe' from a two by three to a five by five map, you'll have to discard all of your wonderful if else snake and start all over again.

I suggest that you first work out the 'theoretical' principle behind navigating your map so that you can write code which is independent of the number of rows and columns of your map.

The other suggestions made by y-lee apply as a matter of course. He gives sound advice.

---

### Post by fiddler616 on 2008-09-13
*GRUMBLE!*
So I replaced the:
```
print "Invalid"
invalidity = False
```
with:
```
invalid()
```
which was defined as:
```
def invalid():
	print invalid
	invalidity = True
```
And it went ahead and gave me:
> What now?8
<function invalid at 0xb7cdf56c>
That's all folks!


---

### Post by fiddler616 on 2008-09-13
> **pp. said:**
> That way lies ruin. Once you change your 'universe' from a two by three to a five by five map, you'll have to discard all of your wonderful if else snake and start all over again.

I suggest that you first work out the 'theoretical' principle behind navigating your map so that you can write code which is independent of the number of rows and columns of your map.

The other suggestions made by y-lee apply as a matter of course. He gives sound advice.
All I see myself changing is:
[LIST]
[*]Replace the elif monster with the modulo thingy
[*]Redefine vertical as 5, not 2
[*]Make a new, larger dictionary
[/LIST]
Did I not have enough coffee this morning?

---

### Post by fiddler616 on 2008-09-13
Just out of curiousity, pp., how did you get thanked in four posts if you've only made three?

---

### Post by pp. on 2008-09-13
@fiddler: work slower, check everything twice.

---

### Post by pp. on 2008-09-13
> **fiddler616 said:**
> Just out of curiousity, pp., how did you get thanked in four posts if you've only made three?

Trade secret? Virtual posts? - No, I hang around in subforums where you can be thanked while posts don't count. Day before yesterday or so my statistics were even better with zero (counted) posts and 2 thanks.

---

### Post by y-lee on 2008-09-13
> 
[quote]Array of function pointers
Array of function pointers
You lost me[/quote]

Ok lets say we have some code for a simple data base that adds deletes edits and displays the data with functions defined like

```
def add(Accounts):
    # bunch of code to input data

def delete(Accounts):
    # bunch of code to input account to delete
    # as well as code to delete the account

def edit(Accounts):
    # bunch of code to input account to edit
    # as well as code to change the account info

def display(Accounts):
    # a little bit of code to print all account info
```

Now in our main function we want the user to input a choice represent what they wish to do, namely add, delete, edit an account, simply display all accounts, or exit the program.

instead of inputting user choice and processing with a long **if elif ...** (or a Case like statement in other languages)

We could put the functions above in a list as in

```
actions = [add, edit, view, delete, view]
```

and then in our main function, input the choice and process the choice like the below:

```
def main(Accounts):
    while True:
        choice = input_display(message[0])
        if choice == 5:
            break
        actions[choice](Accounts) 
```
          
of course alot of code is missing in this simple example like the definition of **input_display** function and the global variable **message**. Also note input_display has to return a valid number like an int from 0 to 4 (inclusive). Also note that this example uses global variables which one maybe should avoid, lol.

In this example the list actions is what i would refer to as an array of function pointers. Note how I call the functions in this list:

```
actions[choice](Accounts)
```

As to the math trickery i mentioned I could easily do it but you learn nothing if others write your code for you. Use whatever techniques and such work for you based upon your current knowledge.

Hope this helps.

---

### Post by pp. on 2008-09-13
> **fiddler616 said:**
> 
[*]Replace the elif monster with the modulo thingy

Did I not have enough coffee this morning?

It's not about how much coffee, but how it is made. I myself drink espresso only.

I do not recall having seen a modulo thingy in this thread. While it might work if done properly, I don't think that this is the best solution for your problem. 

Consider that your map is just a rectangle, and you want to prevent your user from leaving it on any side.

---

### Post by fiddler616 on 2008-09-13
> **pp. said:**
> @fiddler: work slower, check everything twice.
True... :(
Um, I've been through the code again, reasoning everything out and:
*Added an else at the end of the if elif mammoth. Just because it seemed like a good idea.
*Check my function skills [here]("http://www.ibiblio.org/g2swap/byteofpython/read/functions.html#def-function"), and reassured myself that I was doing it correctly.
*Realized that while wasn't looping because I False-ified it at the end, and replaced the code at the end with:
```
elif user_input == 9 and invalidity == False:
			running = False
		else:
			print "It broke :("
		asking = False
	print "#End of loop, FYI"
```
And the only thing ALL of that changed was the looping, I still get the yucky <function invalid...etc.> error, even though the program kept running.
---
I don't think I *did* have enough coffee this morning.

---

### Post by nvteighen on 2008-09-13
What you need is to catch the player's position and test it against the "edge conditions" I told you in the other thread. Don't hard code positions, use something like:

[PHP]
invalid_keys = [] # Here we store invalid places according to position;
                  # possibly this should go into its own function.
if (position % map_width) == 0: # if we're on left-edge
    invalid_keys += [4] # Notice that we add things to the list, so we don't
                        # overwrite anything if there's a condition above
elif (position % (map_width - 1)) == 0: # if we're on right-edge
    invalid_keys += [6]
elif position < map_width: # if we're on top 0 or 1 in this case...
    invalid_keys += [8]
elif position > (map_width * map_height - map_width): 
    # This is a bit trickier, but observing how the map is arranged makes
    # that condition obvious..
    invalid_keys += [2]
[/PHP]

map_width and map_height are variables, so these conditions work for **any** rectangular map drawn with the dictionary as we did in the last thread. There are no absolute values (except for the keys... and that could also be changed to a general device).

I don't know if you notice it, but that code abstracts a restricted set of valid/possible **paths** inside your **position** map. If you add more invalidity conditions according to other positions, you can start creating walls inside the grid and make the game more interesting (of course, in the future).

And then, when you check user's input, you first check if the key isn't in the invalid_keys "blacklist" (use Python's magical "in" operator... it's a nice feature!).

Everything else seems to be fine. Keep doing the good job! And you know we're here to help.

---

### Post by fiddler616 on 2008-09-13
Holy cow, that stuff that gets posted while you're posting yourself!
@pp. Re posts/thanks: Oh, now I feel better.
@y-lee Re pointers, etc.: Reading that made my brain feel like it was crawling through mud. To say I understand it perfectly would be dishonest arrogance, since all I'm really getting out of it is:
Make function to do elif-ing, so everything's tidy.
> you learn nothing if others write your code for you
Excellent call.
@pp. Re Modulos/coffee: Well what I didn't-but-normally have is mostly-equal espresso, milk, and cocoa. Maybe that's it :)
On the modulos though, it was in the quote back in the beginning from nvteighen.
@both of you: Many thanks!

---

### Post by pp. on 2008-09-13
> **fiddler616 said:**
>  yucky <function invalid...etc.> 

Very broad hint: check the function definition.

---

### Post by fiddler616 on 2008-09-13
> **nvteighen said:**
> What you need is to catch the player's position and test it against the "edge conditions" I told you in the other thread. Don't hard code positions, use something like:

[PHP]
invalid_keys = [] # Here we store invalid places according to position;
                  # possibly this should go into its own function.
if (position % map-width) == 0: # if we're on left-edge
    invalid_keys += [4] # Notice that we add things to the list, so we don't
                        # overwrite anything if there's a condition above
elif (position % (map-width - 1)) == 0: # if we're on right-edge
    invalid_keys += [6]
elif position < map-width: # if we're on top 0 or 1 in this case...
    invalid_keys += [8]
elif position > (map_width * map_height - map_width): 
    # This is a bit trickier, but observing how the map is arranged makes
    # that condition obvious..
    invalid_keys += [2]
[/PHP]

map_width and map_height are variables, so these conditions work for **any** rectangular map drawn with the dictionary as we did in the last thread. There are no absolute values (except for the keys... and that could also be changed to a general device).

I don't know if you notice it, but that code abstracts a restricted set of valid/possible **paths** inside your **position** map. If you add more invalidity conditions according to other positions, you can start creating walls inside the grid and make the game more interesting (of course, in the future).

And then, when you check user's input, you first check if the key isn't in the invalid_keys "blacklist" (use Python's magical "in" operator... it's a nice feature!).

Everything else seems to be fine. Keep doing the good job! And you know we're here to help.
Muchas gracias.
(So much for the quote about doing it myself, but I think this is the first code > three lines I've read so far that made sense on the first read-through)
*Don't ever tell me how to make walls though!* I certainly hope I'm able to do that when the time comes. :)
...Some might be thinking I should start thanking people and marking this thread as [Solved], except first I'm going to go actually write the code, to make sure nothing daft happens.
Thanks to all of you!

---

### Post by fiddler616 on 2008-09-13
> **pp. said:**
> Very broad hint: check the function definition.

Not having coffee was the stupidest thing I've done all day. I don't understand.
Valid function definition:```

def sayHello():
	print 'Hello World!'
```
Invalid function definition:
```
def invalid():
        print "Invalid"
        invalidity = False
```
Ooh, never mind, idea (I don't think it'll work since it's local, but...):
```
def invalid(invalidity):
        print "Invalid"
        invalidity = False
```
Never mind, that's even worse.

---

### Post by fiddler616 on 2008-09-13
Never mind, I think I get it!
```

def invalid(var):
    print "Invalid"
    var = False
#To call:
invalid(invalidity)

```
Note: I haven't tested it yet, I'm trying to post before someone else does.
Edit: Now I have tested it, and it doesn't work. This is like one of those brainteasers where knowing there's an answer right in front of your face just makes it more agonizing. But if it clicks for me, the mental high will be worth it.

---

### Post by Greyed on 2008-09-13
> **fiddler616 said:**
> 
```

0 1
2 3
4 5

```
From 3, I want the person to be able to move to 2 (pos - 1), 1 (pos - vertical)(which in this case is two), and 5 (pos + vertical). However, if the person goes 'east' (pos + 1, they'll end up in four, instead of generating a "You can't do that!" error message.

This is all a matter of how you're organizing your data.  For example, in the above situation my first attempt was horrible.  My second attempt is what it should have been the first time around.  Create a matrix of the legal coordinates inside a dict like this:
```

map = {(0,2): True,
       (1,2): True,
       (0,1): True,
       (1,1): True,
       (0,0): True,
       (1,0): True
}

```

Then you have your current position stored in a list like this:
```

curpos = [1,1]

```
Finally your x, y movements are simple add/subtracts on the two elements in the list.  So a vertical move would be:
```

prevpos = curpos.deepcopy() # prevpos = [1,1]
curpos[1] = curpos[1] + 1 # curpos = [1,2]

```
Finally, is it legal?  Simple to check!
```

if not map.has_key(tuple(curpos)):
    curpos = prevpos

```
This presumes that it is a simple x,y grid and that NSEW are legal moves traversing rows and columns.  On the other hand it is entirely possible to have rows which are of different lengths and boundaries and have the player traverse any point on the map.  The only difference is the initialized data and not the logic.

---

### Post by kahping on 2008-09-13
> **fiddler616 said:**
> 
```
def invalid():
        print "Invalid"
        invalidity = False
```

looks ok to me. copy & pasting your code then trying it works for me, too

---

### Post by fiddler616 on 2008-09-13
@greyed: If this were GMail, I'd 'star' your post. And I really appreciate the thought behind it. But to be honest, all I understand is that you made an x, y grid, and as y-lee said:
> you learn nothing if others write your code for you 
So I'm saving that for when when (sic on double when) I read it, it'll make sense straight-off.
Thanks though.

---

### Post by fiddler616 on 2008-09-13
> **kahping said:**
> looks ok to me. copy & pasting your code then trying it works for me, too
Well, it doesn't like me :(

---

### Post by nvteighen on 2008-09-13
> **fiddler616 said:**
> Muchas gracias.
(So much for the quote about doing it myself, but I think this is the first code > three lines I've read so far that made sense on the first read-through)
*Don't ever tell me how to make walls though!* I certainly hope I'm able to do that when the time comes. :)
...Some might be thinking I should start thanking people and marking this thread as [Solved], except first I'm going to go actually write the code, to make sure nothing daft happens.
Thanks to all of you!

De nada :)

I won't ever tell you how to make walls, because I have already given you a base for them :D

---

### Post by fiddler616 on 2008-09-13
Eh...que no hay algo corto para decir en Español...
(All right, before people jump on me with Google Translate again. I said Thanks a lot, and he said You're welcome, and I said "Eh...it's that there's nothing short to say in Spanish...")
Back to the scheduled programming:
Re walls: Score. I'd be somewhat scarred if you did.
@Everyone: I'm still kind of baffled by this function error. It doesn't stop the program, so I guess I'll just kind of ignore it for now...

---

### Post by fiddler616 on 2008-09-13
> **nvteighen said:**
> What you need is to catch the player's position and test it against the "edge conditions" I told you in the other thread. Don't hard code positions, use something like:

[PHP]
invalid_keys = [] # Here we store invalid places according to position;
                  # possibly this should go into its own function.
if (position % map-width) == 0: # if we're on left-edge
    invalid_keys += [4] # Notice that we add things to the list, so we don't
                        # overwrite anything if there's a condition above
elif (position % (map-width - 1)) == 0: # if we're on right-edge
    invalid_keys += [6]
elif position < map-width: # if we're on top 0 or 1 in this case...
    invalid_keys += [8]
elif position > (map_width * map_height - map_width): 
    # This is a bit trickier, but observing how the map is arranged makes
    # that condition obvious..
    invalid_keys += [2]
[/PHP]

map_width and map_height are variables, so these conditions work for **any** rectangular map drawn with the dictionary as we did in the last thread. There are no absolute values (except for the keys... and that could also be changed to a general device).

I don't know if you notice it, but that code abstracts a restricted set of valid/possible **paths** inside your **position** map. If you add more invalidity conditions according to other positions, you can start creating walls inside the grid and make the game more interesting (of course, in the future).

And then, when you check user's input, you first check if the key isn't in the invalid_keys "blacklist" (use Python's magical "in" operator... it's a nice feature!).

Everything else seems to be fine. Keep doing the good job! And you know we're here to help.
Note for anybody using this who's not me (future viewers or something): Be sure to change all the map widths to either map-width, or map_width. It's a wee bit inconsistent here.

---

### Post by nvteighen on 2008-09-13
> **fiddler616 said:**
> Note for anybody using this who's not me (future viewers or something): Be sure to change all the map widths to either map-width, or map_width. It's a wee bit inconsistent here.

Oh, thanks. I didn't notice that.

I'll edit the original post.

---

### Post by fiddler616 on 2008-09-13
> **nvteighen said:**
> Oh, thanks. I didn't notice that.

I'll edit the original post.
Pssht, no problem. It's the least I can do :)
Haha, wow. I've been messing with the program and:
[LIST]
[*]I can move around great!
[*]I tried going off the 'edge', just to see what happened. And got an error. And was getting stressed. And then I realized that I'd never made the in-statement for the blacklist. So we're good, I'm just laughing at my stupidity :)
[/LIST]

Edit: My beans aren't roasted anymore! Ooh! (I feel like such a cheater though, since the majority of my posts have been asking for, not giving help. I guess my time will come.)

---

### Post by fiddler616 on 2008-09-13
> **kahping said:**
> looks ok to me. copy & pasting your code then trying it works for me, too

I guess it'll remain a mystery, since now I'm using nvteighen's modulo method, not the elif monster.

---

### Post by fiddler616 on 2008-09-13
I was kind of debating making the modulo method a function, since it'd look cleaner (right now it still looks like an elif monster, even though it's an elif monster that makes sense), but then I kind of thought that since I'm only calling it once, it's just a waste of space defining it.
Thoughts?
--------
This is a completely new post, I just didn't want to quadruple-post.
--
Future thread-lookers also note: You need to reset the blacklist after each cycle, or else every possible thing will work its way into the blacklist, and you're in trouble.
----
Current helpers note: I have the source for all the versions of this [here]("http://tmac.andrewmin.com/python"), if you want to see it for some reason.
On that: STEXBAG is the first (very sloppy) line
Tuxt is the current (somewhat sloppy) line.
Version 0.2a of Tuxt is the first to use the dictionary, and version 0.2b of Tuxt is the first to use the modulo method, except it's not up yet, because it's still being worked on.
Now you know.

---

### Post by imdano on 2008-09-13
> **fiddler616 said:**
> ```
		if pos == 1 or pos == 3 or pos == 5 and user_input == 6:
			print "Invalid"
			invalidity = True
```I know you're not using this code anymore, but just for future reference, you can shortcut this line with ```
if pos in [1, 3, 5] and user_input == 6:
```

---

### Post by matja on 2008-09-13
You actually managed to correct the code yourself ;)

First post:
> **fiddler616 said:**
> 
```

def invalid():
    print invalid
    invalidity = True

```

Second post:
> **fiddler616 said:**
> 
```

def invalid():
    print [COLOR="Red"]"[/COLOR]Invalid[COLOR="Red"]"[/COLOR]
    invalidity = False

```

In the first post, the print statement printed the function itself (in a human-readable format).

> **fiddler616 said:**
> 
```

def invalid(var):
    print "Invalid"
    var = False
#To call:
invalid(invalidity)

```

As you suspected, this wont work to modify invalidity. You can either declare invalidity as a global variable:
```

invalidity = False

def invalid()
    global invalidity
    print "Invalid"
    invalidity = True

```
or just return it from the function:
```

def invalid()
    print "Invalid"
    return True

invalidity = invalid()

```
although it looks a bit silly in this case since we already know invalidity is True when we call the function. It might make more sense to do it if invalid() checked for invalidity and returned either True or False.

Best regards,
Mattias

---

### Post by fiddler616 on 2008-09-14
imdano and matja: Thanks to both of you.
(@imdano: Stuff like that shortcut is exactly the kind of useful thing that isn't 'useful' enough to get published in a tutorial/guide, but that improves the sanity of the progammer)

---

### Post by fiddler616 on 2008-09-18
I'm feeling rather foolish right now.
I successfully implemented the modulo method, and (after enjoying how I could prance about in circles, and not encounter any bugs), took the next step in the program, and made objects available. That's not the question :)
The thing is: that somehow crashed the modulo method, and after trying to undo whatever I did with the objects, I just couldn't get it worked out, and decided to make a new version from 'scratch' (previously, new versions had just been 'Save As's)
And I still get the error. Harrumph. Here's the code:
```
while running == True:
	print map[pos]
	user_input = int(raw_input("What now?"))
	asking = True
	while asking == True:
		askvar = False
		#nvteighen's modulo method
		invalid_keys = []
		if (pos % map_width) == 0: # if we're on left-edge
  		  invalid_keys += [4] # Notice that we add things to the list, so we don't
    	                    # overwrite anything if there's a condition above
		elif (pos % (map_width - 1)) == 0: # if we're on right-edge
   		 	invalid_keys += [6]
		elif pos < map_width: # if we're on top 0 or 1 in this case...
  		  invalid_keys += [8]
		elif pos > (map_width * map_height - map_width): 
  		  invalid_keys += [2]
		if user_input in invalid_keys:
			user_input = 10
		if user_input == 8:
			pos = (pos - vertical)
		elif user_input == 4:
			pos = (pos - 1)
		elif user_input == 6:
			pos = (pos + 1)
		elif user_input == 2:
			pos = (pos + vertical)
		elif user_input == 10:
			print "Invalid"
			askvar = True
		if askvar == False:
			asking = False
		if askvar == True:
			asking = True
		

```
The error is:
> print map[pos]
KeyError: -2

So I know it comes for having -2 as pos, but I feel like the user_input that would make that (in this case going North from position 0) shouldn't have happened, since the user_input was changed from 8 (North) to 10 (which should fast-forward to the Invalid part, and leave pos alone)
----
Note: I know the introduction of askvar is a bit sloppy, but it's just temporary until I play with whiles a bit more and figure out how to escape them (I think it's 'break'?)

---

### Post by nvteighen on 2008-09-18
Hmm... Could you send us the code? Chances are there's something using 'pos' before this code... Anyway, it's impossible to know what's happening without being able to run a test.

(Thanks for attributing my work, btw :))

> **fiddler616 said:**
> 
Note: I know the introduction of askvar is a bit sloppy, but it's just temporary until I play with whiles a bit more and figure out how to escape them (I think it's 'break'?)

Yes. 'break' interrupts the most inner while with respect to it. 'continue' interrupts the while, but makes it return to the condition test (extremely useful sometimes).

'break' is also used for another kind of block structure you shouldn't worry about now (try...except), but it does exactly the same. 

The break/continue pair is the modern replacement for goto's (which Python doesn't have). They're jumps, but local to a certain part of the code... and they can't jump wherever. They're safer and don't hurt the program's logic.

---

### Post by fiddler616 on 2008-09-18
> **nvteighen said:**
> Hmm... Could you send us the code? Chances are there's something using 'pos' before this code... Anyway, it's impossible to know what's happening without being able to run a test.
Attached
> 
(Thanks for attributing my work, btw :))

No problem, it's the least I can do! :)
> 

Yes. 'break' interrupts the most inner while with respect to it. 'continue' interrupts the while, but makes it return to the condition test (extremely useful sometimes).

'break' is also used for another kind of block structure you shouldn't worry about now (try...except), but it does exactly the same. 

The break/continue pair is the modern replacement for goto's (which Python doesn't have). They're jumps, but local to a certain part of the code... and they can't jump wherever. They're safer and don't hurt the program's logic.


Thanks for the explanation, and it's definitely 'cleaner' than using askvar.

---

### Post by nvteighen on 2008-09-18
Ok, it's pretty simple, but I want you to find out... Interestingly, the bug seems to be my fault.

1) Check how the conditions are working. We already know that the buggy position is 0. Execute the code step-by-step in you mind. Read carefully and slowly... and you'll learn a real subtle difference between two statements that look very similar.

Don't worry, if you are lost, we're here to help, but just that I want you to teach how to fish (very according to your game ;))

2) Not essential, but recommended. Your nested while's can be reduced to a single while. Use break/continues and get rid of the dummy variables askvar and asking (hint: use the "while True:" idiom).

Enjoy!

EDIT: Change the program's filename. "0.2c.py" gives a lot of trouble, because many environments (like the Emacs text editor, which I use) load the file into the Python shell through an implicit "import", and dots inside an "import" are reserved for a special behaivor. Change it to "02c.py", "mygame.py", "tuxt.py", whatever, but avoid inner dots.

---

### Post by fiddler616 on 2008-09-18
[PHP]invalid_keys = [] #Fine
		if (pos % map_width) == 0: #0 % 2 = 0, so true. # if we're on left-edge
  		  invalid_keys += [4] # Notice that we add things to the list, so we don't
    	        elif (pos % (map_width - 1)) == 0: #0 % 1 = 0, so true (though it really shouldn't be, I'll have to write an exception)
   	       	  invalid_keys += [6]
		elif pos < map_width: # 0 < 2, so true
  		  invalid_keys += [8]
		elif pos > (map_width * map_height - map_width):  # 0 !>4, so false.
  		  invalid_keys += [2]
#invalid_keys is now [4, 6, 8]
		if user_input in invalid_keys: #If user_input is 4, 6, or 8. Let's pretend it's 8 (the bug)
			user_input = 10
		if user_input == 8: #Doesn't matter, because now user_input is 10
			pos = (pos - vertical)
		elif user_input == 4: #Doesn't matter, because now user_input is 10
			pos = (pos - 1)
		elif user_input == 6:#Doesn't matter, because now user_input is 10
			pos = (pos + 1)
		elif user_input == 2: #Legal, but disregarded since user_input is 10
			pos = (pos + vertical)
		elif user_input == 10: #This *should* happen
			print "Invalid"
			askvar = True#Pops us back to the top, where the invalid_keys is cleared, and a new user_input is found[/PHP]
Note comments.
I guess I'm missing something :(
[s]That might be because it's late at night though...[/s] Edit: I looked at it with morning eyes, and remain baffled.
Other edit: I removed *your* comments in the interest of clarity.

---

### Post by fiddler616 on 2008-09-18
Re: Your edit on filenames: OK

---

### Post by fiddler616 on 2008-09-19
Re. getting rid of nested whiles: It's a good idea, and I plan to do it, but since I'm currently in debugging mode, I'm trying to remove as much questionable code as possible, to see where the problem is, not add more.
What number am I on? 0.2c? 0.2d will have less whiles. 0.2e will have objects, and 0.3 will begin play-testing. But now I'm jumping the gun :)

---

### Post by nvteighen on 2008-09-19
You're missing a point. Hint:

> **fiddler616 said:**
> [PHP]invalid_keys = [] #Fine
		if (pos % map_width) == 0: #0 % 2 = 0, so true.
  		  invalid_keys += [4] # Notice that we add things to the list, so we don't
    	        elif (pos % (map_width - 1)) == 0: #Are you sure this condition is ever checked?
   	       	  invalid_keys += [6]
		elif pos < map_width: #The same as above
  		  invalid_keys += [8]
		elif pos > (map_width * map_height - map_width):  #The same as above
  		  invalid_keys += [2]

                # invalid_keys include 4, no doubt, but the rest?
                # put a print invalid_keys to check it out.

                # etc.
[/PHP]


In one word, there's a logic issue there. Think: if you're in 0, you're the left edge and also at the top, does the code above handle that correctly? What does "elif" means contrasted to "if"? (I'm almost giving you the solution, but I want you to understand what's going on)

---

### Post by fiddler616 on 2008-09-19
Ooooh. I get it... (Now that you've spoon-fed me :) )
I'm away from my home computer, and the niceties of Ubuntu, so I have no way of testing it, but I'm assuming that the solution is to use ifs, not elifs.
(TI-BASIC habits die hard--I'm still not used to dealing with else/else ifs)(Even though it makes sense, now that I think about it like that)

---

### Post by fiddler616 on 2008-09-20
Yes! Now it says "Invalid".
There's still a big bug, but I'm not even going to post it until I fry my brains trying to crack it myself.

---

### Post by nvteighen on 2008-09-20
> **fiddler616 said:**
> Yes! Now it says "Invalid".
There's still a big bug, but I'm not even going to post it until I fry my brains trying to crack it myself.
:) That's the attitude!

---

