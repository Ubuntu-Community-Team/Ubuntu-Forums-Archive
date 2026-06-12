---
title: "adding images in easygui"
date: 2009-11-12
forum: Programming Talk
---

### Post by karimruan on 2009-11-12
I am writing a small game to practice with gui's in python on ubuntu.

It is a personal version of a game I hope to release for ubuntu. But, I am having trouble with images. Here is the code:

[code=python]
#!/usr/bin/env python
# Graphical Romance Game
# KarimRuan November 2009
# Version 1.0
# under GPL License

from easygui import *
import sys

def mat():
    while 1:
        msgbox("Your turn sexy man! What do you want to do to me now, baby?")
        image = "/home/mat/naynay.gif"
        msg = "What do you want to do to Miss NayNay?"
        title = "Textual Adventures"
        choices = ['Take her out to Dinner', 'Drink Wine With her', 'Kiss Her Neck', "Rub her Feet"]
        choice = choicebox(msg, title, choices)

        msgbox("You chose to " +str(choice), ".")

        msg = "Do you want to continue?"      
        title = "Please confirm."
        if ccbox(msg, title):
            naynay()
        else:
            sys.exit(0)




def naynay():
    msgbox("Oooooh, that felt good Hunny! What do you want me to do to you?")
    image = "/home/mat/naynay.gif"
    msg = "What do you want Miss NayNay to do to you?"
    title = "Textual Adventures"
    choices = ["Kiss you", "Lick you", "Cuddle with you", "Hold Your Hand"]
    choice = choicebox(msg, title, choices)

    msgbox("NayNay decides to " + str(choice), "!")
    msg = "Do you want to continue?"
    title = "Please Confirm"
    if ccbox(msg, title):
        mat()
    else:
        sys.exit(0)
        
        
    
    
while 1:
    msgbox("""Welcome to Textual Adventures, the Graphical Text Based
        Romance Game. In this game, (which by the way you should not be
        playing unless your me), you get to play with Miss NayNay, the best
        wife one could ever have!""")
    msg = "What do you want to do to Miss NayNay?"
    title = "Textual Adventures"
    choices = ['lick', 'kiss', 'caress', 'fondel', 'french kiss']
    choice = choicebox(msg, title, choices)
    

    # conver choice to string, in case
    # if user cancles choice, return None.
    msgbox("You chose to  " + str(choice), "Miss NayNay")
    msg = "Do you want to continue?"
    title = "Please Confirm"
    if ccbox(msg, title): # show continue/cancle dialog
        naynay()   # user chose continue
    else:
        sys.exit(0) # user chose cancle

[/code]

I have tried this:

[code=python]

while 1:
    msgbox("""Welcome to Textual Adventures, the Graphical Text Based
        Romance Game. In this game, (which by the way you should not be
        playing unless your me), you get to play with Miss NayNay, the best
        wife one could ever have!""", image = "/home/mat/image.gif")
    msg = "What do you want to do to Miss NayNay?"
    title = "Textual Adventures"
    choices = ['lick', 'kiss', 'caress', 'fondel', 'french kiss']
    choice = choicebox(msg, title, choices)
    

    # conver choice to string, in case
    # if user cancles choice, return None.
    msgbox("You chose to  " + str(choice), "Miss NayNay")
    msg = "Do you want to continue?"
    title = "Please Confirm"
    if ccbox(msg, title): # show continue/cancle dialog
        naynay()   # user chose continue
    else:
        sys.exit(0) # user chose cancle
[/code]

This shows the picture where I want it, but no buttons, so you are basically stuck on that dialog box! I have to use Force Quit to exit.

Any ideas, i am using EasyGui!

Here is a link to the tutorial I am using as a reference:

[http://www.ferg.org/easygui/tutorial.html#contents_item_9.4](http://www.ferg.org/easygui/tutorial.html#contents_item_9.4)

Thanks for the extra help!

---

### Post by karimruan on 2009-11-12
Okay, i got it. It is done. Very simple, I made a version for the ubuntu community, but it is graphic, contains nudity. So, email me at [email]ruane.tech@gmail.com[/email] if you want a copy of Textual Adventures: Mina Edition.

I hope you guys like it, the pictures are pretty good too. (No, they are not of my wife :))

NOTE TO MODS:

If I am breaking a rule, feel free to delete this post. I don't think I am, because I am making those who want it contact me off of the forums. It is an adult game, so if this post is not appropriate, let me know. Thanks!

---

