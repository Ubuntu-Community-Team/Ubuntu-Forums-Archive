---
title: "[SOLVED] Python help"
date: 2008-09-13
forum: Programming Talk
---

### Post by dodle on 2008-09-13
[PHP]def username():
    name = raw_input('What is your name?')

username()

print name[/PHP]I know this is all wrong, but it might give you an idea of what I am trying to do.  Can the output of a function be saved to a variable?  Or should I give up on functions and try to do this another way?

---

### Post by OutOfReach on 2008-09-13
I don't know if this is what you want to do, but I'll give it a shot: You want to call the username() function and store the output (the username that the user typed in) to a variable and print that variable? If so, it would look something like this:

[PHP]def username():
    name = raw_input('What is your name?')
    return name

name = username()

print name  [/PHP]

---

### Post by dodle on 2008-09-13
[PHP]def restart():
	answer = raw_input('Would you like to do it again?')
	if answer == "y":
		user_name()


def user_name():
	name = raw_input('What is your name?')
	restart()
	return name

my_name = user_name()


user_name()


print "Your name is %s ." % (my_name)

raw_input('Press "enter" to quit')[/PHP]Can you tell me what is wrong with this code?  I can't figure it out.

---

### Post by Can+~ on 2008-09-13
> **dodle said:**
> [PHP]def restart():
	answer = raw_input('Would you like to do it again?')
	if answer == "y":
		user_name()


def user_name():
	name = raw_input('What is your name?')
	restart()
	return name

my_name = user_name()


user_name()


print "Your name is %s ." % (my_name)

raw_input('Press "enter" to quit')[/PHP]Can you tell me what is wrong with this code?  I can't figure it out.

You're creating a little level of recursion there, calling the restart function and then user_name again will cause it to spawn another "level" of recursion, diagram:

```
[COLOR="Red"]user_name() # input: Joathan
 restart() # yes[/COLOR]
[COLOR="Lime"]  user_name() # input: Jonatan
   restart() # yes again[/COLOR]
[COLOR="DeepSkyBlue"]    user_name() # input: Jonathan
     restart() #no.
    end user_name()[/COLOR]
[COLOR="Lime"]  end user_name()[/COLOR]
[COLOR="Red"]end user_name()[/COLOR] # <-- this one outputs the value.


```

You could circumvent this by making the confirm funcion return a boolean:

[PHP]def restart():
    answer = raw_input('Would you like to do it again?')
    if answer == "y" or answer == "yes":
        return True
    else:
        return False
    #This could also be return answer == "y" or answer == "yes", but it might be hard to understand.


def user_name():
    again = True

    while again:
        name = raw_input('What is your name?')
        again = restart()
    
    return name

my_name = user_name()

# user_name() (Edit, missed this one)

print "Your name is %s ." % (my_name)

raw_input('Press "enter" to quit')[/PHP]

(I'm pretty sure there must be at least 10 different ways to do this.)

---

### Post by dodle on 2008-09-13
It's not ending the script after until I input "n" fro a second time:
```
What is your name?blahblah
Would you like to do it again?n
What is your name?blahblah
Would you like to do it again?n
Your name is blahblah .
Press "enter" to quit

```I was having the same problem with the script that I posted.

---

### Post by Def13b on 2008-09-13
That'd be because your calling the user_name function twice (if your going by the code posted above by Can+~,

```
.
.
my_name = user_name()  # called once here, your first 'n' exits this one

user_name() # called again here, 2nd 'n' exits this
```

---

### Post by dodle on 2008-09-13
```
def char_name():
    loop = "1"
    while loop == "1":
        char_name = raw_input('Please select a name for the main character.  Aolis\
 is the default name.')
        if char_name == "":
            char_name = "Aolis"
        confirm = raw_input('You have chosen "%s", is this okay?.' % (char_name))
        if confirm == "yes" or "y":
            print "thank you very much."
            loop = "0"  # *[COLOR="Red"]Shouldn't this break the "loop"?[/COLOR]*
        if confirm != "yes" or "y":
            loop = "1"
    return char_name
```
My function keeps looping.  Why?  I'm having such a hard time getting this programming stuff >_<.

---

### Post by OutOfReach on 2008-09-13
Fixed it for you:
[PHP]
def char_name():
    loop = "1"
    while loop == "1":
        print loop
        char_name = raw_input('Please select a name for the main character.  Aolis\
 is the default name.')
        if char_name == "":
            char_name = "Aolis"
        confirm = raw_input('You have chosen "%s", is this okay?.' % (char_name))
        if confirm == "yes" or confirm == "y":
            print "thank you very much."
            loop = "0"  # Shouldn't this break the "loop"?
        elif confirm != "yes" or confirm != "y":
            loop = "1"
    return char_name  [/PHP]

Ok, I'm not great at explaining things, but here I go:
You put ```
if confirm == "yes" **or "y"**:
```
Now, basically what that says is: if the confirm variable is equal to "yes" or "y" is "y". Now, that made the loop variable equal "0", but when the elif comes up, you put: ```
elif confirm != "yes" **or "y"**
```
What that's saying is: else if the variable confirm is not equal to "yes" or "y" is "y".
Now obviously "y" is "y", so the loop variable gets changed to "1", so the loops continues...

Ok, now the proper way to put it is:
```
if confirm == "yes" **or confirm == "y"**:
```
Now this is the correct way, which says: if the variable confirm is equal to "yes" or the variable confirm is equal to "y" then...
Same concept goes for the elif.
Hope that helped somehow, as I said I'm not exactly what you call a teacher.

EDIT: Oh btw you should use booleans (True, False) for managing loops, makes your life easier. :)

---

### Post by dodle on 2008-09-14
Thanks OutOfReach, I feel like I keep making the same mistakes.  I'm having a hard time understanding when to use "if" and when to "elif".

What happens if I have a list of a thousand possible answers:

[PHP]...
if answer == "yes" and answer == "y" and answer == "red" and answer == "My brown saddle" \
and answer == "frog" and answer == "chicken nuggets" .....[/PHP]

That's a lot of ands.

---

### Post by Def13b on 2008-09-14
Assuming you mean 'or' instead of 'and', you can use,
[PHP]
if answer in ['yes', 'y', 'Yes', 'Y', 'YES', 'affirmative', 'damn straight']:
    do something[/PHP]

Also keep in mind that loop already = 1 so there should be no need for,

[PHP]elif confirm != "yes" or confirm != "y":
            loop = "1"[/PHP]


I'd also recommend not using char_name as both a function name and variable name, it makes the code more difficult to read.

---

### Post by OutOfReach on 2008-09-14
Well, to reduce all the 'and' s, you can use 'in', for example:

[PHP]if answer in ("something", "here", "one", "yes", "no", "maybe", "so"):[/PHP]

---

### Post by dodle on 2008-09-14
> **OutOfReach said:**
> Well, to reduce all the 'and' s, you can use 'in', for example:

[PHP]if answer in ("something", "here", "one", "yes", "no", "maybe", "so):[/PHP]

Oh, that's much better.

What about:[PHP]elif answer not in ("something", "here", "one", "yes", "no", "maybe", "so")[/PHP]

---

### Post by OutOfReach on 2008-09-14
Yes, that would work too. :)

---

### Post by dodle on 2008-09-14
> **OutOfReach said:**
> Yes, that would work too. :)

Whoa!  I got it right?

Okay, I've come across another problem.  Now I am trying to import this from another script:  launcher.py=[PHP]import main, name

name.char_name()


print name.char_name[/PHP]name.py=[PHP]def char_name():
    loop = "1"
    while loop == "1":
        char_name = raw_input('Please select a name for the main character.\
 \nAolis is the default.')
        if char_name == "":
            char_name = "Aolis"
        confirm = raw_input('You have chosen "%s", is this okay?.' % (char_name))
        if confirm == "yes" or confirm == "y":
            loop = "0"
        elif confirm != "no" or confirm != "n":
            loop = "1"
    return char_name[/PHP]The output of:[PHP]print name.char_name[/PHP]is:```
<function char_name at 0xb7dbe294>
```This has got me totally baffled.

---

### Post by OutOfReach on 2008-09-14
You should probably put the output of char_name() into a variable:

[PHP]import main, name

variable = name.char_name()


print variable[/PHP]

What you were doing, was you were trying to print out the physical function, literally. That's why this: ```
<function char_name at 0xb7dbe294>
``` would show up.

---

### Post by dodle on 2008-09-14
> **OutOfReach said:**
> You should probably put the output of char_name() into a variable:

[PHP]import main, name

variable = name.char_name()


print variable[/PHP]
Hmmm, this did work, but at the same time it made name.char_name run through twice.```
Please select a name for the main character.
Aolis is the default.
You have chosen "Aolis", is this okay?.y
Please select a name for the main character.
Aolis is the default.
You have chosen "Aolis", is this okay?.y
Aolis

```

Edit: Oh! I figured it out.  I changed launcher.py to this:[PHP]import main, name

blu = name.char_name()
print blu[/PHP]Oh, I guess that's what you said in the first place. :D

---

### Post by OutOfReach on 2008-09-14
EDIT: Ok I see you got it.

---

### Post by dodle on 2008-09-18
Edit: deleted

---

