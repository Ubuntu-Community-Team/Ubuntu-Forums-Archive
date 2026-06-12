---
title: "[SOLVED] python: import versus __import__"
date: 2009-01-10
forum: Programming Talk
---

### Post by suprfish on 2009-01-10
I'm having trouble getting __import__ to work. I've [read]("http://docs.python.org/library/functions.html#__import__") (and think I understood) all the docs, etc. Here's the script's structure:

```

launcher.py
lib/
    __init__.py
    games/
        __init__.py
        dinosaur.py

```

It's fairly straight forward. launcher.py takes an input, and tries to start that game.

**launcher.py**
```

import lib
if __name__ == "__main__": lib.play(input)

```

The problem occurs in the lib module, which is (in entirety).
[B]
lib/__init__.py[/B]
```

def play(name):
    try:
        game = __import__("games.%s" % (name), level=0)
        game = getattr(game, name)
        
    except ImportError, e:
        sys.exit("Could not play '%s' because it doesn't exist." % (name))
    
    game.play()

```

The above never works; the below will (but isn't what I want)

```

def play(name):
    import games.dinosaur
    games.dinosaur.play()

```

What's going on here? :confused:

---

### Post by suprfish on 2009-01-10
Oh.
I actually had to supply the globals() list myself :mad:

```

__import__("games.%s" % (name), globals())

```

---

