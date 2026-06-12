---
title: "[SOLVED] [Python] Function calling problem"
date: 2008-09-19
forum: Programming Talk
---

### Post by dodle on 2008-09-19
Edit:  Here are the scripts that will describe my problem better:
[PHP]# This script is called "name"

def char_name():
    loop = "1"
    while loop == "1":
        print
        char_name = raw_input('Please select a name for the main character.\
 \nAolis is the default: ')
        if char_name == "":
            char_name = "Aolis"
        print
        confirm = raw_input('You have chosen the name "%s", is this okay? ' % (char_name))  # Confirm that this is the desired name
        if confirm in ("yes", "y", "Yes", "Y"):
            loop = "0"
        elif confirm not in ("yes", "y", "Yes", "Y"):
            loop = "1"
    return char_name 



def char_gender():
    loop = "1"
    while loop == "1":
        print
        char_gender = raw_input('Is %s a male or a female? ' % char_name())
        if char_gender in ("f", "F", "female", "Female", "g", "G", "girl", "Girl"):
            char_gender = "female"
            print "%s is a %s." % (char_name(), char_gender)
            loop = "0"
        if char_gender in ("m", "M", "male", "Male", "b", "B", "boy", "Boy"):
            char_gender = "male"
            print "%s is a %s" % (char_name(), char_gender)
            loop = "0"
    return char_gender  [/PHP]
[PHP]#  Trial of Aolis v0.1 2008
import name


print
print "Trial of Aolis v0.1 2008"
print
raw_input('press "enter" to start')

game_state = "active"
while game_state == "active":


    char_name = name.char_name()
    char_gender = name.char_gender()


# Here, the main game starts

    print
    print "%s, %s" % (char_name, char_gender)
    print

# Main game ends here

    cont_ = "undecided"
    while cont_ == "undecided":
        game_over = raw_input('Would you like to play again?')
        if game_over in ("yes", "y", "Yes", "Y"):
            game_state = "active"
            cont_ = "decided"
        elif game_over in ("no", "n", "No", "N"):
            game_state = "inactive"
            cont_ = "decided"
        elif game_over in ("name", "Name"):
            print
            print char_name
            print
            cont_ = "undecided"
        elif game_over not in ("yes", "y", "Yes", "Y", "no", "n", "No", "N", "name", "Name"):
            print
            print 'I don\'t understand "%s".' % (game_over)
            print
            cont_ = "undecided"
        
print
raw_input('Press "enter" to exit')  [/PHP]

*char_name()* is being called three times.  But if I change the following lines from "name":
[PHP]char_gender = raw_input('Is %s a male or a female? ' % char_name())
print "%s is a %s." % (char_name(), char_gender)
print "%s is a %s" % (char_name(), char_gender)[/PHP]
to:
[PHP]char_gender = raw_input('Is %s a male or a female? ' % char_name)print "%s is a %s." % (char_name, char_gender)print "%s is a %s" % (char_name, char_gender)[/PHP]

Then *char_name* isn't called multiple times but the output looks like this:
[PHP]<function char_name at 0x009FE070>[/PHP]

Edit:  I have been able to solve this problem by defining all of my functions in the main script instead of importing, but I want to get better at importing.  So, if possible I would like to keep the two scripts separate.

---

### Post by dwhitney67 on 2008-09-19
I'm a reluctant student of Python myself, but from other experience I have gained, I can see that one (and perhaps the only) problem you are having is with the multiple calls to char_name().

You need to call the function char_name() once, and assign the return value to a variable.  Then proceed to use this variable during the flow of char_gender().

P.S.  You should consider passing the result of char_name() to char_gender() as a parameter.

---

### Post by dodle on 2008-09-19
I'm not very good with functions yet, I've been reading a few different tutorials.  How can I pass char_name() as a parameter of char_gender()?

---

### Post by dwhitney67 on 2008-09-19
Like I stated, I am a mere student... the following may be incorrect:

[PHP]name = char_name();

char_gender( name );[/PHP]
or[PHP]
char_gender( char_name() );[/PHP]

The definition for char_gender() should be changed to:

[PHP]def char_gender( name ):
...[/PHP]

Then use 'name' in each place where you previously used char_name().

---

### Post by dodle on 2008-09-19
Okay I've changed the following lines in my scripts and it works perfectly now.

name.py
[PHP]def char_gender():[/PHP]to:[PHP]def char_gender( char_name)[/PHP]Then I replaced all of the *% (char_name()* with *% (char_name)*

and in the main script...

launcher.py
[PHP]char_gender = name.char_gender( char_name )[/PHP]Thanks dwhitney67

---

### Post by Greyed on 2008-09-19
Ok, my brain is hurting here.  Where, exactly are you making the change?  The first thing that comes to mind is that in the first case you're calling the function char_name where in the change you're referencing the function char_name.

Remember function() means "run function with the parameters contained in ()" where as function means "return a reference to function".  If you really are changing the three lines from calls to references that would be your problem.  However since you're using the same name for the function as the variable (a bad practice for reasons like this) it is hard to figure out what you are changing without knowing exactly where you're changing it.

---

### Post by dodle on 2008-09-19
[QUOTE="Greyed"]Ok, my brain is hurting here. Where, exactly are you making the change? The first thing that comes to mind is that in the first case you're calling the function char_name where in the change you're referencing the function char_name.

Remember function() means "run function with the parameters contained in ()" where as function means "return a reference to function". If you really are changing the three lines from calls to references that would be your problem. However since you're using the same name for the function as the variable (a bad practice for reasons like this) it is hard to figure out what you are changing without knowing exactly where you're changing it.[/QUOTE]

The lines that I changed are followed by a comment of the corrected line.

[PHP]# This script is called "name"

def char_name():
    loop = "1"
    while loop == "1":
        print
        char_name = raw_input('Please select a name for the main character.\
 \nAolis is the default: ')
        if char_name == "":
            char_name = "Aolis"
        print
        confirm = raw_input('You have chosen the name "%s", is this okay? ' % (char_name))  # Confirm that this is the desired name
        if confirm in ("yes", "y", "Yes", "Y"):
            loop = "0"
        elif confirm not in ("yes", "y", "Yes", "Y"):
            loop = "1"
    return char_name 



def char_gender():  # I changed this line to: def char_gender(char_name)
    loop = "1"
    while loop == "1":
        print
        char_gender = raw_input('Is %s a male or a female? ' % char_name())  # This line changed to: char_gender = raw_input('Is %s a male or a female?' % (char_name))
        if char_gender in ("f", "F", "female", "Female", "g", "G", "girl", "Girl"):
            char_gender = "female"
            print "%s is a %s." % (char_name(), char_gender)  # This line changed to: print "%s is a %s." % (char_name, char_gender)
            loop = "0"
        if char_gender in ("m", "M", "male", "Male", "b", "B", "boy", "Boy"):
            char_gender = "male"
            print "%s is a %s" % (char_name(), char_gender)  # This line to: print "%s is a %s" % (char_name, char_gender)
            loop = "0"
    return char_gender  [/PHP]
[PHP]#  Trial of Aolis v0.1 2008
import name


print
print "Trial of Aolis v0.1 2008"
print
raw_input('press "enter" to start')

game_state = "active"
while game_state == "active":


    char_name = name.char_name()
    char_gender = name.char_gender()  # And finally, this line to: char_gender = name.char_gender(char_name)


# Here, the main game starts

    print
    print "%s, %s" % (char_name, char_gender)
    print

# Main game ends here

    cont_ = "undecided"
    while cont_ == "undecided":
        game_over = raw_input('Would you like to play again?')
        if game_over in ("yes", "y", "Yes", "Y"):
            game_state = "active"
            cont_ = "decided"
        elif game_over in ("no", "n", "No", "N"):
            game_state = "inactive"
            cont_ = "decided"
        elif game_over in ("name", "Name"):
            print
            print char_name
            print
            cont_ = "undecided"
        elif game_over not in ("yes", "y", "Yes", "Y", "no", "n", "No", "N", "name", "Name"):
            print
            print 'I don\'t understand "%s".' % (game_over)
            print
            cont_ = "undecided"
        
print
raw_input('Press "enter" to exit')  [/PHP]

---

