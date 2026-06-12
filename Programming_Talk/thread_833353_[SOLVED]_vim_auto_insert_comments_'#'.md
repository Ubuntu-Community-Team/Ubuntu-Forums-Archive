---
title: "[SOLVED] vim auto insert comments '#'"
date: 2008-06-18
forum: Programming Talk
---

### Post by prkfriryce on 2008-06-18
When I copy and paste using the 'right mouse button', comments and tabs automatically inserted in the copied text:

ie
```

#!/usr/bin/perl
use strict;
my $test;
###
     if ($test) {  blah
           }
my $test2;

```

after copied:

```

#!/usr/bin/perl
use strict;
my $test;
###
     if ($test) {  blah
           }
my $test2;
###
#           if ($test) {   blah
#                           }
#                            my $test2;
#
#

```


I am not using any aliases for vi in .bashrc or .bashrc_alliases

Any ideas how to disable this?

---

### Post by geirha on 2008-06-18
turn off smartindenting and autoindenting (not sure if you need to turn off both, but I never bother to check)
```
:set nosi noai
```

A better solution, in my opinion, is to use one of the graphical versions of vim, which will not indent like that. Install [vim-gnome](apt:vim-gnome), and try it by running «gvim». It integrates better with the mouse; if you mark something with the mouse, it treats it as a marking in visual mode etc...

---

### Post by rangalo on 2008-06-19
Another solution would be to turn on paste before pasting 

```
:set paste
```

And after pasting, turn it off

```
:set nopaste
```


you can also bind a key to toggle these commands 


regards,
Hardik

---

### Post by geirha on 2008-06-19
> **rangalo said:**
> 
```
:set paste
```


Nice, didn't know about that one. Much better solution :)

---

### Post by rangalo on 2008-06-19
> **geirha said:**
> Nice, didn't know about that one. Much better solution :)

I found this on vim.org they have really nice tips ...

---

### Post by prkfriryce on 2008-06-19
> **rangalo said:**
> Another solution would be to turn on paste before pasting 

```
:set paste
```

And after pasting, turn it off

```
:set nopaste
```


you can also bind a key to toggle these commands 


regards,
Hardik

ahhh,thank you! that's what I was looking for.

> **geirha said:**
> turn off smartindenting and autoindenting (not sure if you need to turn off both, but I never bother to check)
```
:set nosi noai
```

A better solution, in my opinion, is to use one of the graphical versions of vim, which will not indent like that. Install [vim-gnome](apt:vim-gnome), and try it by running «gvim». It integrates better with the mouse; if you mark something with the mouse, it treats it as a marking in visual mode etc...

yeah, i have gvim installed and that was not affected.  no worries


thank you everyone!

---

### Post by dani3lr on 2009-05-20
thank you this post.

I'm just lucky today.
it took years for me to find the solution.

---

### Post by monkeyking on 2009-05-20
Hmm,
this had been nagging me for years.


I wonder why this isn't default

---

### Post by Sfate on 2012-03-17
to someone who will get this info useful..

to resolve problem with inserting some text/code in vim with comments you can just add in your .vimrc file this line:
```
set pastetoggle=
```
that will make `set paste` on pasting and `set nopaste` when it's done..

p.s. sorry for necroposting :oops:

---

