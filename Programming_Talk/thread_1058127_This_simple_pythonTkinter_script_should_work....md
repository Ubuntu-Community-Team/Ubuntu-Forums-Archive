---
title: "This simple python/Tkinter script *should* work..."
date: 2009-02-02
forum: Programming Talk
---

### Post by eragon100 on 2009-02-02
Hello guys!

I am creating a space shooter with python and pygame, which is going great basically. ("scrolling" background, enemy ships, shooting, scoring, shields, hull, sounds, collision detection etc are all working :D)

However, the game currently has only a terminal "menu" for choosing video mode, so I decided to modernize this by making a GUI version, ran from the main program as a module, which allows the user to sets it with a button click, and then returns the value to the main program. For some reason tough, this simple stand-alone application isn't working. Python on the terminal doesn't show any error tough, it just doesn't do anything.

Can anyyone tell me what I am doing wrong? The code is here on pastebin.com:

[http://pastebin.com/m1b6e15d6](http://pastebin.com/m1b6e15d6)

---

### Post by unutbu on 2009-02-02
The reason why you are not seeing any windows is because your callback functions are being executed, rather than being referenced. For example,```


command = self.exit()
```

should be
```

command = self.exit
```

Also, IntVar() can make using Radiobuttons easier. See
demo-radio-auto.py from Mark Lutz's Programming Python examples: [http://examples.oreilly.com/python3/PP3E-Examples-1.2.tgz](http://examples.oreilly.com/python3/PP3E-Examples-1.2.tgz)

Your code, modified: [http://pastebin.com/f792b333f](http://pastebin.com/f792b333f)

---

