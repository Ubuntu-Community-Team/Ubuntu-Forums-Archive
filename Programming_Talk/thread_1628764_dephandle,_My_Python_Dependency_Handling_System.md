---
title: "dephandle, My Python Dependency Handling System"
date: 2010-11-23
forum: Programming Talk
---

### Post by DangerOnTheRanger on 2010-11-23
*phew* Now that was a title! :D

Why would you want a dependency handling system?
Because in larger, modular systems, that have several components depending on one another, some(or all) will need to get explicitly initialized, and possibly deinitialized on exit.

Sounds easy, huh?

Not so! Some components will require others to get initialized first, and they might need to be deinitialized, in order of dependencies(most dependent first). How are you going to go about that?

Enter dephandle, my dependency handling system for Python. Just add this code in all your modules after all your imports:

```

import dephandle
dephandle.gendeps(__name__, modprefix)

```...where modprefix is what all your modules are prefixed with(or the  name of your root package, if you have one). Setting modprefix to '' will check *every *module you've imported; this is *not* recommended, as this will add about 0.3 seconds per module check.

dephandle will automatically detect *init *and *deinit *methods in your module, and call them when your modules dependencies(if any) have been initialized, and when your dependents(if any) have been deinitialized, respectively.

Your module does not need to include this code if you do not need dependency handling in that specific module, i.e, modules that use dephandle can still use modules that don't, and vice versa.

You can also optionally add an *excludes *argument, that contains all  the modules you do *not *wish to check, since dephandle takes about  0.3 seconds per module per dependency(which is about 1 second for 3  modules with 1 dependency each), so excluding modules that do not need  to be explicitly initialized can be a big time saver.

A simple example:
```

#mod1.py
import dephandle

dephandle.gendeps(__name__, 'mod')

def init():

    print __name__, 'init'
    print __name__, 'deps:', deps

def deinit():

    print __name__, 'deinit'

#mod2.py
import mod1, dephandle

dephandle.gendeps(__name__, 'mod')

def init():

    print __name__, 'init'
    print __name__, 'deps:', deps

def deinit():

    print __name__, 'deinit'

#mod3.py
import mod2, dephandle

dephandle.gendeps(__name__, 'mod')

def init():

    print __name__, 'init'
    print __name__, 'deps:', deps

def deinit():

    print __name__, 'deinit'

#__main__.py
# Import dephandle, and our modules
# Mix 'em up, to prove dephandle's prowess... :D
import dephandle, mod2, mod1, mod3

print 'Initalizing...'

dephandle.init()

print 'Doing stuff...'
# Ho hum...
print 'Finished! Closing...'

```This outputs:

```

Initalizing...
mod1 init
mod1 deps: []
mod2 init
mod2 deps: ['mod1']
mod3 init
mod3 deps: ['mod1', 'mod2']
Doing stuff...
Finished! Closing...
mod3 deinit
mod2 deinit
mod1 deinit

```See? mod1(which had no dependencies) was initialized first, and mod3(which had the most dependencies) was initialized last.
Also notice that mod3(which was the least depended-upon module) was deinitialized last, and mod1(which had the most dependents) was deinitialized last, and dephandle makes a list named *deps *available to each module that lists its own dependencies.

As an extra plus, notice that each module was initialized and deinitialized just once, even though they had(in the case of mod1) multiple dependents!

dephandle will also warn you of the dreaded circular dependencies(where 2 or more modules depend on each other, either directly or indirectly thorough another module).

Say you modified the import statement in mod1.py to read:
```

import mod3, dephandle

```Now mod1 depends on mod3, which depends on mod2, which depends on mod1.
Now they all depend on each other!

Thankfully, dephandle will warn you of this predicament:
```

Initalizing...
WARNING: Circular dependency between mod1 and mod2
WARNING: Circular dependency between mod1 and mod3
WARNING: Circular dependency between mod2 and mod3
mod1 init
mod1 deps: ['mod1', 'mod2', 'mod3']
mod2 init
mod2 deps: ['mod1', 'mod2', 'mod3']
mod3 init
mod3 deps: ['mod1', 'mod2', 'mod3']
Doing stuff...
Finished! Closing...
mod3 deinit
mod2 deinit
mod1 deinit

```Notice the warnings, and the dependencies each module emits.

dephandle is licensed under the GNU GPLv3. Go ahead and try it!

-DangerOnTheRanger

---

