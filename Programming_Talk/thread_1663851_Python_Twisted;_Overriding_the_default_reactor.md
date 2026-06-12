---
title: "Python Twisted; Overriding the default reactor"
date: 2011-01-10
forum: Programming Talk
---

### Post by vik_2010 on 2011-01-10
If you import and install another reactor prior to importing the default (select) reactor, then you can use that as the reactor whenever you call "from twisted.internet import reactor"

Alex Martelli over on StackOverflow.com wrote at 

[http://stackoverflow.com/questions/3424825/is-twisted-internet-reactor-global](http://stackoverflow.com/questions/3424825/is-twisted-internet-reactor-global)

that calling "from twisted.internet import reactor" checks to see if a previous reactor module as been installed (by looking up twisted.internet.reactor in sys.modules), and if so, returns that.

BUT I don't see that. All I see from the source docs, here ...

[http://twistedmatrix.com/trac/browser/trunk/twisted/internet/reactor.py](http://twistedmatrix.com/trac/browser/trunk/twisted/internet/reactor.py)

is that importing the reactor module DELETES the entry in sys.modules and replaces it with a new select loop.

I know I'm missing something, since that's not what happens in actuality. If anyone knows twisted well, can they point out what piece of the puzzle is missing?

Best,

-V

---

### Post by vik_2010 on 2011-01-10
Wait, I have to be missing something . . . If the first thing one does (quit possible, of course) is :

from twisted.internet import reactor

and reactor.py is merely:

[PHP]
import sys
del sys.modules['twisted.internet.reactor']
from twisted.internet import selectreactor
selectreactor.install()
[/PHP]Then the above code should throw a KeyError at the delete line if a reactor hasn't been introduced previously - which doesn't occur.

---

