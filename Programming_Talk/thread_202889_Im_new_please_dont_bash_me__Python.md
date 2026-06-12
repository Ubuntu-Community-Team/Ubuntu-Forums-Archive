---
title: "Im new please dont bash me :/ Python"
date: 2006-06-24
forum: Programming Talk
---

### Post by deathbyswiftwind on 2006-06-24
Okay I am a major newb when it comes to programming. I started at the python site on python for non programmers. I got through the first stages ago when I came apon this problem.

Modify the password guessing program to keep track of how many times the user has entered the password wrong. If it is more than 3 times, print ``That must have been complicated.''

and here is the original source from the program

```

while password != "unicorn":
    password = raw_input("Password:")
print "Welcome in"

```

I have re-read every chapter at least a dozen times but I cant seem to figure this out. I really didnt want to post but since they dont have the answers to it and I **REALLY** wonna learn cause someday Id like to contribute to linux I came to what I thought would be a somewhat safe place to ask a rather *ahem* newbish question

The only other programming I ever did was qbasic in high school and boy that was ages ago!

---

### Post by digby on 2006-06-24
Well, the first thing I would say is necessary is that you need to assign your password variable to something first (i.e. before you can do 'while password !=...  you have to assign 'password = 'something.that.is.not.unicorn'

I'm not sure exactly what is causing your problem, but I would guess it's the part about keeping track of how many guesses it takes.  I used a variable called count that I set as 0 at the top.  After the password was input correctly, I used an if/elif statement to test how many guesses it took by seeing if count was >3, <3, etc.

If this doesn't make any sense, let me know... it's early and I'm not quite awake yet...  I know your frustration with this, because I just finished that tutorial a couple of weeks ago, so I'm not far ahead.  But stick with it, it's an interesting ride, and with a little help, you'll pick it up in no time.

edit:  I still have the code I wrote for the exercise, but I hesitate to post it, because I think you'll learn a lot more doing it yourself.  But if you play with it some more and can't get it let me know, and I'll give you some snippets.

---

### Post by Revert on 2006-06-24
Try talking yourself through the code, it usually helps.  Like digby said, password needs to be declared before the first comparison.  From there, the program's something like: while password isn't equal to unicorn, take user input; if it took them more than three tries, print "That must be complicated."  By working through it in english, you can find out what you have to do (while, not equal, user input, if, etc.)  Now that you know you'll need an if comparison to see if they have guessed more than three times, all you have to do is find a way to keep track of how many guesses they've made (if the guess is wrong, increment some variable), then figure out where in the program the variable should be incremented.

Good luck! :)

---

### Post by deathbyswiftwind on 2006-06-24
Okay here is what I came up with 

```

#Problem: Make password program take 3 guesses before quitting telling user
#too many tries


password = "imma"
n = "noob"
b = 4 #max_tries
a = 0 #tries

print "Please enter your password: "

while password != n:
    a = a + 1
    if a < b:
        password = raw_input("Password:  ")
    else:
        print "That must have been to difficult"

```

Now while this works after the third guess it goes into a infinate loop printing that must have been to difficult could someone please just hint as to where my mistake is to kill the infinite loop. Im so close but so far away ](*,)

---

### Post by Revert on 2006-06-24
You have two main options:

1. Have the a < b comparison be one of the conditions of the while loop (along with password != n).

2. In your else, have it also terminate the loop.

I'd look up logical operators ("and" and "or" keywords) and the "break" and "continue" statements.

Also, when you're initializing password to be empty, you might want to just do password = ""
It's not much of a difference, but it helps to make your purpose clear, and if you ever have to go back and figure out what you were trying to do in a program, it's much easier.

---

### Post by deathbyswiftwind on 2006-06-25
Hey thank the both of you guys VERY much! My ending code ended up being

```

#Problem: Make password program take 3 guesses before quitting telling users
#too many tries


password = ""
n = "noob"
b = 3 #max_tries
a = 0 #tries

print "Please enter your password: "

while password != n:
    if a < b:
        password = raw_input("Password:  ")
        a = a + 1
    elif a >= b:
        print "That must have been to difficult"
        break

```

It works like its supposed to. One question though while this accomplishes the needed result is this the best way to do it?

---

### Post by digby on 2006-06-25
Your solution is fine.   As for the best way... that could be argued... some of my code might be a little better, but I see something in yours that I didn't think to include.  The idea to break if the user took too many guesses... I never thought of that.  I'm just cruel, I guess... :mrgreen:

Here's mine so you can see what I did, but substantially, they're pretty similar.  Now on to the next challenge!  Let us know if we can help.  Like I said, I'm not to terrible far ahead of you, so I'm enjoying being able to help someone out.```
#Modified password program to track number of wrong entries

password = "foobar"
count = 0

while password != "answer":
        password = raw_input("Password:")
        count = count + 1

#once password is correct

count = count - 1 #correct for extra while loop after correct guess

print "You got it in " ,count, " tries."

if count >= 3:
        print "Must have been harder than I thought..."

else:
        print "Nice guessing..."
```

---

### Post by GStubbs43 on 2006-07-23
digby, just to let you know... if you get it wrong three times, nothing happens, I got it wrong 23 times and nothing ever hapened.

---

### Post by anthro398 on 2006-07-23
Also, notice the difference in variable names between your program and digby's program.  Readability is almost always one of the primary goals.  I'd rather write something that is slower and less efficient if I can make it simpler and more readable.  Keep working on it.  I think python is a joy to work with.

---

### Post by forrestcupp on 2006-07-29
Another thing to make it slightly easier.

instead of   count = count + 1

you can use   count += 1

or   count -= 1

or whatever you want to do

---

### Post by ifokkema on 2006-07-29
I wonder why Python doesn't support the count ++ option, just like many other popular languages.

---

### Post by sapo on 2006-07-29
> **ifokkema said:**
> I wonder why Python doesn't support the count ++ option, just like many other popular languages.
Is it so difficult to do this?

YourUselessCounter += 1

---

### Post by ifokkema on 2006-07-30
> **sapo said:**
> Is it so difficult to do this?

YourUselessCounter += 1
No, but my fingers are just so much used to typing it :)

---

### Post by Van_Gogh on 2006-07-30
> **ifokkema said:**
> I wonder why Python doesn't support the count ++ option, just like many other popular languages.

It's because Pythonistas think there are better/more readable ways :-D E.g. instead of
```
for(i=0;i<10;i++){
  doSomething()
}
```
Pythonistas do
```
for i in range(10):
  doSomething()
}
```
Because they think it's human-readable, especially when combined with some other readability-related features of Python. Personally I agree with view:-)

---

### Post by ifokkema on 2006-07-31
> **Van_Gogh said:**
> E.g. instead of
```
for(i=0;i<10;i++){
  doSomething()
}
```
Pythonistas do
```
for i in range(10):
  doSomething()
}
```

Yikes! :-& I guess for new programmers it's easier to learn because they haven't seen it done differently.

I've been using PHP and C++ for quite some time now. If I ever take on Python in a more serious way, I will have quite some reading up to do. Not to mention try not to mess up while typing too fast... I've seen 'elif' in stead of 'elseif' already and that really doesn't make sense to me...

---

### Post by Daverz on 2006-07-31
> **Van_Gogh said:**
> It's because Pythonistas think there are better/more readable ways :-D E.g. instead of


Well, i++ is pretty readable IMO.

Actually, I think it's because

count = 5
count = count + 1

in Python doesn't mean "increment the integer variable 'count'", it means "reassign the reference 'count' from the integer 5 to the integer 6", so count++ would be sort of false advertising.  Another way to put it is that integers are immutable in Python, so they can't have any increment or decrement methods that would parallel a ++ operator.

But that's just speculation.  This has all been hashed out on a gazillion threads on comp.lang.python, but I'm too lazy to google them.

---

