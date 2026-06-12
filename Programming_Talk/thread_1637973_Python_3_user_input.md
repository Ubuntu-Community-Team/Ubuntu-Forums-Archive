---
title: "Python 3 user input"
date: 2010-12-05
forum: Programming Talk
---

### Post by Vert on 2010-12-05
I'm trying out Python 3.1 by making a small text based game (Zork style). All I'm trying to do is take user input. Here is my code sample...

```

def test():
        print("You are in a room. There is a door to the north. There is nothing else to see here.")
        uInput = input('> ').lower()
        try:
            if uInput == "n":
                room2()
            elif uInput == 'look':
                test()
            else:
                print("Sorry, but that's invalid.")
                test()
        except ValueError:
                print("Sorry, but that's invalid.")
                test()

```

I couldn't figure out why typing "n" wasn't evaluating to true until I debugged it and it said uInput was equal to "n/r" after taking the stdin. The Python documentation said that input() will strip the trailing newline, however, it is keeping the carriage return. 

Are there functions that do exactly this? Is input() supposed to act in the way I'm describing and this is a bug?

I'm going to be taking a lot of user input in this little program, so how would I accomplish this? The only solution I'm aware of is wrapping the input function in a custom one which will slice off the last two characters, but that seems like an ugly hack (and most likely unnecessary).

Thank you for any help you are able to give.

---

### Post by Arndt on 2010-12-05
> **Vert said:**
> I'm trying out Python 3.1 by making a small text based game (Zork style). All I'm trying to do is take user input. Here is my code sample...

```

def test():
        print("You are in a room. There is a door to the north. There is nothing else to see here.")
        uInput = input('> ').lower()
        try:
            if uInput == "n":
                room2()
            elif uInput == 'look':
                test()
            else:
                print("Sorry, but that's invalid.")
                test()
        except ValueError:
                print("Sorry, but that's invalid.")
                test()

```

I couldn't figure out why typing "n" wasn't evaluating to true until I debugged it and it said uInput was equal to "n/r" after taking the stdin. The Python documentation said that input() will strip the trailing newline, however, it is keeping the carriage return. 

Are there functions that do exactly this? Is input() supposed to act in the way I'm describing and this is a bug?

I'm going to be taking a lot of user input in this little program, so how would I accomplish this? The only solution I'm aware of is wrapping the input function in a custom one which will slice off the last two characters, but that seems like an ugly hack (and most likely unnecessary).

Thank you for any help you are able to give.

Carriage return doesn't normally appear in input coming from the user on Unix. It can be made to do so if you manipulate the terminal settings, with stty. Do you get the carriage return with other programming languages too?

---

### Post by Vert on 2010-12-05
Since this is Python and I assumed it would be cross platform (I'm trying to keep it as OS agnostic as I can) so long as I don't do anything too "out there". I'm currently doing this part on a Windows machine using Eclipse and Pydev.
-----------
I found the culprit. You helped me by leading me down the line of thought (maybe it was the tools I was using). The Eclipse console was adding the "/r" for some reason. I don't even see an option to fix that, but lesson learned. If using an IDE... always debug with the vanilla Python interpretor. It was a silly, simple problem, but thank you very much for leading me in the right direction!

---

### Post by MadCow108 on 2010-12-05
you can use strip/lstrip/rstrip to trim the input from newlines and whitespaces (or anything else you require)

---

### Post by Vert on 2010-12-05
Awesome! Thanks MadCow, I didn't catch those methods earlier! I'll definitely use those later on to maintain compatibility across OS's and different terminal types!

---

