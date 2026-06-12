---
title: "How to integrate python interpreter to web?"
date: 2009-11-12
forum: Programming Talk
---

### Post by elasolova on 2009-11-12
Hi,

I am working on a challenge site and I want to ask problems where people will code in python. Then the code will be executed and the website will accept the code or not. 

I do not know how to do such manipulation without compromising security. Do you have any suggestion?

Thanks

---

### Post by Reiger on 2009-11-12
You can (a) either pre-process the Python code to strip it from any &#8216;dangerous&#8217; stuff; or (b) create a sandbox for the interpreter of choice.

(a) Is still not entirely 100% fool proof -even if done right- because code like this is likely to upset your server:
```

# this is recursive stuff which is a good way of keeping your stack
# occupied if the interpreter is unable to do tail-call optimization
# and that isn't so easy here
def fun(arg):
    if arg == 0 : return 1 # prevent infinite recursion == stack overflow == end of attack
    else: return 1 / (fun(arg -1) + 1)

# let's put the website in a coma
# a real world example would embark on things such as matrix manipulation
# in pure python by the most inefficient 
# algorithms possible...
def loop() :
    while(true)
      print(1 + fun(150)) # 150 stack frames is likely to be accepted

loop()

```

Furthermore there are eval() caveats lurking in darker corners of the Python world.

Incidentally: guess what Mathematical constant my code approximates ad nauseam? :P

(b) Is more appropriate if you are willing to spend the time to learn how-to. This kind of thing itself is fairly trivial in e.g. Java with its JSR spec for that (javax.script) package -- you can put computation on a background thread, and abort it if it takes too long to complete; furthermore you have precise control over what objects are exposed to the guest code.

---

