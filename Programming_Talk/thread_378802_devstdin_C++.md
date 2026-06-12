---
title: "/dev/stdin C++"
date: 2007-03-07
forum: Programming Talk
---

### Post by Mars8082686 on 2007-03-07
I'm making a game that gets input from the user and if certain keys are pressed it does certain things i.e. move the character
anyways it works, but the problem is they have to press enter each time. because I guess the data doesn't get put into /dev/stdin till they hit enter. Anyways is there a way I can get a stream from there keyboard without them having to press enter? thanks

---

### Post by g3k0 on 2007-03-07
Check the below solution.  I should juist give up here.  My solutions always stink

---

### Post by maxamillion on 2007-03-07
```

if (key[KEY_RIGHT])	
{
           //do something in here to move right
}

```

KEY_LEFT, KEY_DOWN, and KEY_UP respectively

---

### Post by Mars8082686 on 2007-03-07
Hi... I looked up the key[KEY_RIGHT] and it's in the library allegro? I tried to include allegro and my compiler did not detect it. I guess I need to download the allegro library. Also, is there a way to do this from the standard GCC compiler library set? Or am I not got to be able to get away with creating even a simple game without non-standard libraries?

---

### Post by lnostdal on 2007-03-07
you'll need external libraries .. if you're creating a terminal based thing you need ncurses (sudo aptitude install libncurses5-dev) .. if you're creating a graphical game there are many alternatives

---

### Post by Wybiral on 2007-03-07
Yeah, what library are you using for the game?

Just console IO?

I suggest SDL, maybe allegro. You can get both of them (runtime and dev files) from synaptic... They both have routines for graphics and mouse/key input.

Also, as lnostdal mentioned, ncurses is good too... But you are limited to ASCII graphics with the console.

---

### Post by studiesrule on 2007-03-08
I believe it has something to termios. I don't know any resource for C++, but [here]("http://ibiblio.org/obp/py4fun/lode/lode.html")'s something for Python. Perhaps you could draw some inspiration.

However, it would frankly be irritating to go this way. I too would go with SDL or ncurses.

---

### Post by Mars8082686 on 2007-03-08
Ok... so basicly I loop through a while loop testing if there is any input, if there is, draw what needs to be drawn, then after that I draw other stuff that needs to be draw. etc. etc.... and it works ok... the problem is getch() waits for the next character in the stream... and thats not what I want, I want to see if there is a character ALREADY in the stream, if there isn't one I want to move on, (so I can write the other stuff that is happening and refresh). I know I can use halfdelay() to move on if I don't get a character after n seconds... but the problem is I want to go faster than N seconds... plus if they give input quickly, EVERY thing speeds up. I see two solutions to this, one would be to start a new thread that handles the background stuff as well as the refresh, and the main what to just test for input and write to the buffer. but I don't know how well that would work. The other solution would be to find a function that reads only what is in the stream at the time of calling it, and returns false if nothing is there without waiting for anything to be put in the stream. What do you think would be the best one, and if its the latter, do you happen to know a function that reads a stream without waiting if it finds nothing?

thanks

---

### Post by Wybiral on 2007-03-08
> **Mars8082686 said:**
> Ok... so basicly I loop through a while loop testing if there is any input, if there is, draw what needs to be drawn, then after that I draw other stuff that needs to be draw. etc. etc.... and it works ok... the problem is getch() waits for the next character in the stream... and thats not what I want, I want to see if there is a character ALREADY in the stream, if there isn't one I want to move on, (so I can write the other stuff that is happening and refresh). I know I can use halfdelay() to move on if I don't get a character after n seconds... but the problem is I want to go faster than N seconds... plus if they give input quickly, EVERY thing speeds up. I see two solutions to this, one would be to start a new thread that handles the background stuff as well as the refresh, and the main what to just test for input and write to the buffer. but I don't know how well that would work. The other solution would be to find a function that reads only what is in the stream at the time of calling it, and returns false if nothing is there without waiting for anything to be put in the stream. What do you think would be the best one, and if its the latter, do you happen to know a function that reads a stream without waiting if it finds nothing?

thanks

I advise going to synaptic and downloading libSDL... It's worth it. I will even help you learn the key event catch.

It's capable of being used the way you want... Which is to have a buffer of boolean values that get updated on key events. That way you can check them individually without having to stop and ask for a key to be pressed.

PM me if you need any help.

---

