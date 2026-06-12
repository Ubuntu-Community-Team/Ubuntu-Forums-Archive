---
title: "Python Input not working"
date: 2012-08-25
forum: Programming Talk
---

### Post by Apertus on 2012-08-25
I just switched from Windows 8 to Ubuntu and am having some problems with Python.

I think I installed Python 3, whenever I run my code that has input in it, the program won't do anything, no box will come up asking for the users in put, the program just stops. 

I'm using Stani's Python Editor. Any help?

---

### Post by Bachstelze on 2012-08-25
Post the code.

---

### Post by Apertus on 2012-08-25
It's just the start of my little game. It just hangs on the Menu: 1. Start Game 2. Quit.

```
    print("Menu:")
    print("1. Start Game")
    print("2. Quit")
    print()
    menu_choice = 0
    choice = int(input("What would you like to do: "))
    if choice == 1:
        startGame()
    elif choice == 2:
        quit()

    else:
        print("Not valid")
```

---

### Post by Bachstelze on 2012-08-25
It works fine here, so the problem most probably lies in your IDE. Normally when you do input() you don't have any kind of "box", you type the text in the terminal where the script is running.

In general, when you are just beginning with a language, it is preferable to run programs directly with the compiler/interpreter from a terminal. Adding an IDE in-between will just get into the way of learning. Only when you have a good knowledge of the language and start working on large projects will an IDE be of any help.

---

### Post by Apertus on 2012-08-25
I can get it to work in the terminal, but nothing else. Do I need to use something to import python3 to editors or something?

---

### Post by Tony Flury on 2012-08-28
> **Apertus said:**
> I can get it to work in the terminal, but nothing else. Do I need to use something to import python3 to editors or something?

No - you don't need to use something - you need to stop using an IDE to run your code.

Certainly use an IDE if you find it helps you edit your code/refactor/search & replace/highlight syntax, but run your code from the terminal not from the IDE. Don't spend time making your code work from an IDE - as you are likely to be the only person who ever needs to execute it that way. Spend your time and effort making the code work from the environment it will be executed when it is finished - either the terminal or the GUI.

Personally I think that people who persuade beginners to use an IDE should be shot, and then shot again just to make sure. They don't add enough value and add a whole heap of pain.

For my python work I use two simple editors - for single file scripts I use gedit - very plain and simple - but it works. 

For more complex applications (such as my Flickr upload tool and my TimeWarp prototype) I use Kate (as a multi-file editor with syntax highlighting, and the ability to recall groups of files as a single entity). I have IDLE installed but have never used it, as I could not even get it to open my Flickr tool, and I have no wish to change my code just so a glorified editor can open it.

---

### Post by prismctg on 2012-08-29
For multiple script ; i m using Eclipse via Pydev ; Its easy to configure

---

