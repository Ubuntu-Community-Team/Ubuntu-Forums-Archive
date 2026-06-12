---
title: "Python calling functions for a game menu"
date: 2012-11-03
forum: Programming Talk
---

### Post by MagnusKGD on 2012-11-03
Dear all,
I am new here and have no other option to turn to you, since I have tried to solve this on my own forever, without success.

I have programmed a fully working photographic cardgame in Python 3.2, using pygame.

My problem is, that I need a menu for the game. It has not been succesful so far.

Mainly because of the fact that I do not know how to get the menu() function to remember the pygame screen settings, which are working fine if the menu is not there.

So could someone give me a hint of how I could handle the following scenario, where the problem is how I could properly tell python to draw the menu, and then by a click on the deal button draw the board and the cards...The game itself works, as I said, it is just the menu I need to allow the player to play again, if they wish.

def main():
 init.pygame()
 Make the cards,deal, draw the board
 When Game over, draw menu() again to allow to play again
 
def menu():
 init.pygame()
 draw the menu with a deal button and a quit button
 when deal button is pressed, it calls main()
 when quit button is pressed, it quits the pygame.

menu()

---

### Post by Tony Flury on 2012-11-04
> **MagnusKGD said:**
> Dear all,
I am new here and have no other option to turn to you, since I have tried to solve this on my own forever, without success.

I have programmed a fully working photographic cardgame in Python 3.2, using pygame.

My problem is, that I need a menu for the game. It has not been succesful so far.

Mainly because of the fact that I do not know how to get the menu() function to remember the pygame screen settings, which are working fine if the menu is not there.

What exactly do you mean by "I do not know how to get the menu() function to remember the pygame screen setting" ?
If you need your menu function to know something about the pygame screen when it exacutes then pass the values as arguments, or even pass teh screen object as an argument.

> 
So could someone give me a hint of how I could handle the following scenario, where the problem is how I could properly tell python to draw the menu, and then by a click on the deal button draw the board and the cards...The game itself works, as I said, it is just the menu I need to allow the player to play again, if they wish.

... Code snipped ...

Rather than have your menu function call main again, or quit the application - it would be better if your menu faction simply returns which button was clicked. you then have your code :

```

def main():
   pygame.init()
   while True:
       draw()
       play()
       if menu() == "Quit":
          break
   pygame.close()

```

the while True loop just makes sure the player plays again unless they choose quit.

---

