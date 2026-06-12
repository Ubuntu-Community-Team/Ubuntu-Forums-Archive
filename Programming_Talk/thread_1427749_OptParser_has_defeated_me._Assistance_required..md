---
title: "OptParser has defeated me. Assistance required."
date: 2010-03-11
forum: Programming Talk
---

### Post by Stev0 on 2010-03-11
Working on a small program in python 3.1, using the OptParse module, however its throwing the error message every time. I figure I have something wrong in the error related if statement, but I cant find it. Any of you more experienced optparse users see the problem? 
[PHP]#! /usr/bin/python3.1

import sys

from optparse import OptionParser

def main():
    
    usage = "usage: %prog [options] [target]"
    parser = OptionParser()
    parser.set_usage(usage)
    parser.add_option("-a", "--address", action="store", dest="addy", help="blah")
    parser.add_option("-r", "--range", action="store", dest="range", help="blah")
    (options, args) = parser.parse_args()

    if len(args) !=1:
        parser.error("Please use an option to specify the target.")
    addy = options.addy
    do_something_with_addy(addy)[/PHP]now when I run the script with ./<script> -a [www.test.com]("http://www.test.com"), it throws the error message every time. Where have I made the mistake?

---

### Post by snova on 2010-03-12
> **Stev0 said:**
> Working on a small program in python 3.1, using the OptParse module, however its throwing the error message every time. I figure I have something wrong in the error related if statement, but I cant find it. Any of you more experienced optparse users see the problem? 
[PHP]#! /usr/bin/python3.1

import sys

from optparse import OptionParser

def main():
    
    usage = "usage: %prog [options] [target]"
    parser = OptionParser()
    parser.set_usage(usage)
    parser.add_option("-a", "--address", action="store", dest="addy", help="blah")
    parser.add_option("-r", "--range", action="store", dest="range", help="blah")
    (options, args) = parser.parse_args()

    if len(args) !=1:
        parser.error("Please use an option to specify the target.")
    addy = options.addy
    do_something_with_addy(addy)[/PHP]now when I run the script with ./<script> -a [www.test.com]("http://www.test.com"), it throws the error message every time. Where have I made the mistake?

If you run it like that, the "www.test.com" argument will become **options.addy**, as you expect. But it will not be found in **args** in any case; **args** is the list of leftovers. Now, if you had run it like this (without -a):

```
./<script> www.test.com
```

Then **args** would have contained this, but **options.addy** would have been unspecified.

It is not possible to specify **-a** without also passing an argument. If **-a** is required somehow then you need to test for this some other way. For example:

[php]
    if options.addy is None:
         parser.error("You must specify an address.")
[/php]

---

### Post by Stev0 on 2010-03-12
Ok that helped. But I've run into another problem :) The other command line option :) How would I incorporate that into the error message so I can use options.range later?

Edit: Nevermind, I just figured out the wonder that is if len(args) is None:

---

### Post by snova on 2010-03-12
> **Stev0 said:**
> Edit: Nevermind, I just figured out the wonder that is if len(args) is None:

Wouldn't that always be False? **len**() either returns an integer or throws an exception; it's not possible for it to return None.

If you've solved your problems, great, but you've left me a little confused.

---

