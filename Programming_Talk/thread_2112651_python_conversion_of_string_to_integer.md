---
title: "python conversion of string to integer"
date: 2013-02-05
forum: Programming Talk
---

### Post by wingnut2626 on 2013-02-05
Hi guys Im working on a simple python script.  This is what i have

```
def fishing(bait, line_weight, pole_size):
    print "You really want to go fishing dont you?"
    raw_input()
    print "The water is perfect for the %s bait you want to use" % bait
    print "Don't want to use too heavy or too light line here. %d lb test weight might be too light.  Its a bit choppy. lets add 10 lbs to that and go with %d lb test" % (line_weight, line_weight + 10)
    print "Now to match the pole to the line weight and the lure. The %s pole size that you specified shows that you are a master fisherman." % pole_size
    print "You are the man! The %s combined with %d and the %s pole size are the combo of the masters! Now, get to work!" % (bait, line_weight + 10, pole_size)
    
fishing("bloodworms", 30, "medium")

print "Now to actually accept user input and return the same string"
print "Ready?"
raw_input()
print "Which type of bait are you using today?"
bait1 = raw_input("bait type>")
print "How about the line weight in lb?"
l[SIZE=4]ine_weight1 = raw_input("line weight>")
int lineweight = line_weight1[/SIZE]
print "Ok, Got it.  Now for the pole, sir?"
pole_size1 = raw_input("pole size>")

fishing(bait1, lineweight, pole_size1)

```

what i want to do is get an integer for the line weight and use it as the line_weight argument in the function fishing.  How would i do that?  THe way I have it isnt working......

---

### Post by Bachstelze on 2013-02-05
You want

```
lineweight = int(line_weight1)
```

---

### Post by wingnut2626 on 2013-02-05
thank you!

---

### Post by r-senior on 2013-02-05
You will probably also want to put that inside a try block because you'll get a ValueError if someone enters "heavy", for example, as the line weight.

See section 8.3 for exactly that example:

[http://docs.python.org/2/tutorial/errors.html](http://docs.python.org/2/tutorial/errors.html)

---

### Post by 3v3rgr33n on 2013-02-05
> **Bachstelze said:**
> You want

```
lineweight = int(line_weight1)
```

What's difference between that and this ```
lineweight = eval(line_weight1)
```

---

### Post by trent.josephsen on 2013-02-05
The difference is in what happens when some joker types "__import__('subprocess').call('rm -rf .'.split())" at the input prompt.

---

### Post by micahpage on 2013-02-05
I had once made that mistake of using eval() in an IRC bot. The end result was users could do whatever they wanted. They ended up making files on my HDD, etc. created their own python scripts, and was able to execute them, all from eval(). They ended up codepading sensitive files, etc.  All which was my simple answer to a simple calculator expression, thus i would say eval() is bad. There is almost always a better way. 

It was quite impressive watching them execute one liner python code from eval() and seeing the result, and process of giving myself a back door via eval(). Luckily they did no harm, just told me to never use eval() for that reason.

```
eval("__import__('subprocess').Popen('ls')")
```
```
eval("open('testoneliner.txt','w').write('this on liner')")

```

---

### Post by 3v3rgr33n on 2013-02-06
wow --- I've never thought of doing that. Thanks for the enlightenment.

---

