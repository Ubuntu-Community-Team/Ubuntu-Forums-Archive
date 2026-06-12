---
title: "Python self learning"
date: 2011-04-06
forum: Programming Talk
---

### Post by hdanap on 2011-04-06
Hi people,

in my self study im doing, not assignment fro school but and exercise in a pyhton book, the question are.


[LIST=1]
[*]Copy catch.py to pong1.py and  change the ball into a paddle by using Box instead of the Circle. You  can look at Appendix A for more information on Box. Make the adjustments  needed to keep the paddle on the screen.
[*]Copy pong1.py to  pong2.py. Replace the distance function with a boolean function hit(bx,  by, r, px, py, h) that returns True when the vertical coordinate of the  ball (by) is between the bottom and top of the paddle, and the  horizontal location of the ball (bx) is less than or equal to the radius  (r) away from the front of the paddle. Use hit to determine when the  ball hits the paddle, and make the ball bounce back in the opposite  horizontal direction when hit returns True. Your completed function  should pass these doctests:
 def hit(bx, by, r, px, py, h):
    """
      >>> hit(760, 100, 10, 780, 100, 100)
      False
      >>> hit(770, 100, 10, 780, 100, 100)
      True
      >>> hit(770, 200, 10, 780, 100, 100)
      True
      >>> hit(770, 210, 10, 780, 100, 100)
      False
    """

 
 3. Finally, change the scoring logic to give the player a point when the ball goes off the screen on the left.
[/LIST]
======================================

I have figured out everything but i kinda think i cheated in the code i  wrote up for the 1st question, the part that instructs keeping the  paddle on the screen, mayb im right but i feel there should be a better  way to keep the paddle on screen

This is my code for the exercise:

```


from gasp import *

COMPUTER_WINS = 1
PLAYER_WINS = 0
QUIT = -1

def distance(x1, y1, x2, y2):
    return ((x2 - x1)**2 + (y2 - y1)**2)**0.5
    
    
def hit(bx, by, r, px, py, h):
    """
    >>> hit(760, 100, 10, 780, 100, 100)
    False
    >>> hit(770, 100, 10, 780, 100, 100)
    True
    >>> hit(770, 200, 10, 780, 100, 100)
    True
    >>> hit(770, 210, 10, 780, 100, 100)
    False
    """
    if px - bx <= r and by >= py and by <= (py + h):
        return True
    else:
        return False
        
        
        

    
    
def play_round():
    # the ball
    ball_x = 10
    ball_y = 300
    ball = Circle((ball_x, ball_y), 10, filled=True, color=color.BLACK)
    dx = 4
    dy = random_between(-5, 5)
    
    #paddle
    mitt_x = 780
    mitt_y = random_between(20, 290)
    r = 20
    h = 100
    #paddle
    mitt = Box((mitt_x, mitt_y), r, h)  
    
    
    
    
    while True:
        if ball_y > 590 or ball_y < 10:
            dy *= -1
        ball_y += dy
        if ball_x > 810:
            remove_from_screen(ball)
            remove_from_screen(mitt)
            return COMPUTER_WINS
        ball_x += dx
        
        move_to(ball, (ball_x, ball_y))
                
        if key_pressed('k') and mitt_y <= 580:
            mitt_y += 5
        elif key_pressed('j') and mitt_y >= 20:
            mitt_y += -5
        else:
            if key_pressed('o'):
                return QUIT
            
        move_to(mitt, (mitt_x, mitt_y))
            
                   
        # makes the ball bounce back    
        if hit(ball_x, ball_y, r, mitt_x, mitt_y, h):
            dx *= -1
        
        # new scoring logic    
        if ball_x < 10:
            remove_from_screen(ball)
            remove_from_screen(mitt)
            return PLAYER_WINS
                
        update_when('next_tick')
        

def play_game():
    player_score = 0
    computer_score = 0
    
    while True:
        pmsg = Text('Player: %d Points' % player_score, (10, 570), size = 24)
        cmsg = Text('Computer: %d Points' % computer_score, (640, 570), size = 24)
        
        # this is the part i think i cheated, keeping the paddle on screen
        # I think, i should be keeping the paddle on screen in function play_round at the
        # top, but cant seem to do that, is the code right? or is ther something im missing

        mitt_x = 780
        mitt_y = random_between(20, 290)
        r = 20
        h = 100
        #paddle
        mitt = Box((mitt_x, mitt_y), r, h)  
        move_to(mitt, (mitt_x, mitt_y))
        sleep(3)
        remove_from_screen(pmsg)
        remove_from_screen(cmsg)
        remove_from_screen(mitt)
        
        
        result = play_round()
        
        if result == PLAYER_WINS:
            player_score +=1
        elif result == COMPUTER_WINS:
            computer_score += 1
        else:
            return QUIT
            
        if player_score == 5:
            return PLAYER_WINS
        elif computer_score == 5:
            return COMPUTER_WINS
            
            
begin_graphics(800, 600, title='Catch', background=color.YELLOW)

result = play_game()

if result == PLAYER_WINS:
    Text('Player Wins!', (390, 290), size = 24)
else:
    Text('Computer Wins!', (390, 290), size = 24)
    
sleep(5)
end_graphics()    
            

    
    
            
if __name__ == '__main__':
    import doctest
    doctest.testmod()




```

---

### Post by 102jon on 2011-04-06
What's the question?

---

### Post by hdanap on 2011-04-06
> **102jon said:**
> What's the question?

The question is i

 change the ball into a paddle by using Box  instead of the Circle. You can look at Appendix A for more information  on Box. 

{Main question is: Make the adjustments needed to keep the paddle on the screen.}

After the program executes, both ball and paddles disappear from the screen by using
statements

remove_from_screen(ball)#the ball
remove from_screen(mitt) # the paddle

but when i try to keep the paddle on the screen by removing or commenting the    remove from_screen(mitt) # the paddle.

 I find out that that works, but on the next run of the play_game() function, now i have 2 paddles on the screen, the previous one from the last play thru and a new one from the present play, and the number of paddles increase as the game play continues and eventually i end up with 5 paddles on the screen instead of 1

Pls advise me on what im doing wrong

---

### Post by andrew1992 on 2011-04-07
You're not being really clear enough. Are you trying to remake classic pong? Is your problem that whenever a point has been scored, you want to reset the ball to the center of the screen, but not the paddles, and you're ending up with extra paddles every round?

---

### Post by 102jon on 2011-04-07
"Main question is: sentence with no question mark."

Hmm....

---

### Post by hdanap on 2011-04-07
> **andrew1992 said:**
> You're not being really clear enough. Are you trying to remake classic pong? Is your problem that whenever a point has been scored, you want to reset the ball to the center of the screen, but not the paddles, and you're ending up with extra paddles every round?


Sorry for not being clear, yes im trying to remake classic pong and yes, thats exactly the problem, im facing, when i reset the ball and the paddles, that works but when i simply try to just reset the ball alone, i end up with extra paddles.

Pls advise me on how to go

---

### Post by andrew1992 on 2011-04-07
```
def play_round():
    # the ball
    ball_x = 10
    ball_y = 300
    ball = Circle((ball_x, ball_y), 10, filled=True, color=color.BLACK)
    dx = 4
    dy = random_between(-5, 5)
    
    #paddle
    mitt_x = 780
    mitt_y = random_between(20, 290)
    r = 20
    h = 100
    #paddle
    mitt = Box((mitt_x, mitt_y), r, h)  
```

Every time you play a round, you're creating new paddles. This is probably left over from when you were clearing the paddles at first.  When is the only time you need to create a paddle? That should answer your question.

---

### Post by hdanap on 2011-04-07
> **andrew1992 said:**
> ```
def play_round():
    # the ball
    ball_x = 10
    ball_y = 300
    ball = Circle((ball_x, ball_y), 10, filled=True, color=color.BLACK)
    dx = 4
    dy = random_between(-5, 5)
    
    #paddle
    mitt_x = 780
    mitt_y = random_between(20, 290)
    r = 20
    h = 100
    #paddle
    mitt = Box((mitt_x, mitt_y), r, h)  
```Every time you play a round, you're creating new paddles. This is probably left over from when you were clearing the paddles at first.  When is the only time you need to create a paddle? That should answer your question.

I create a new paddle at the start of each round and at the end i can clear the whole screen, ball and paddles included.
But if im to just reset the ball, i cant seen to do that, without having an extra paddle or paddles on screen. 

Should i build a separate function to control the paddles inside of play_round() instaed of having both ball and paddles running 2gether being controlled by the same loop?

I dont know, im confused, im very new to programming in general

---

### Post by hdanap on 2011-04-08
Hey Drew,

I figured im still working on that part,

Im trying to make the ball randomly do let or right at start of a round, now when i use

dx = 4 to move the ball_x to the right that works, but i find out when i use 

dx = random_between(-4, 4), when dx happens to be 0(zero) the ball just moves vertically up on own on the same axis

what can i do?

I could use something like 

```

if dx == 0:
    dx += 2


```

will that work, im trying it now

---

### Post by hdanap on 2011-04-08
Worked just fine

Thanks all for the time

---

### Post by andrew1992 on 2011-04-08
That works, but it gives preference to direction in the case of the random selection being 0. If you wanted it to be totally random, and have the speed gradient, it would be better to store all the speeds (which include directions based on their sign) in an array, and make the **index** the random number that is selected.

---

