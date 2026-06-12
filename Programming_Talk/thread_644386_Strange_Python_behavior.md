---
title: "Strange Python behavior"
date: 2007-12-18
forum: Programming Talk
---

### Post by scruff on 2007-12-18
What's the deal here...

(simplified example)

[PHP]
def main();
    rel_type = get_release_type()


def get_release_type():
    types = {'1': 'Gold/',
             '2': 'QFE/',
             '3': 'beta/'}
    
    ans = raw_input("\nWhat type of release is this?\n\n"
                     "1 = gold\n"
                     "2 = QFE\n"
                     "3 = beta\n# ")

    if not types.has_key(ans):
        print "\nYou must enter either 1, 2, or 3"
        get_release_type()
        
    return types[ans]

if __name__ == '__main__':
    main()
[/PHP]

You can see that get_release_type() will call itself if the user enters invalid input. The strange issue I am seeing is if you DO enter invalid input, the 2nd time around at return types[ans] it will try to look up whatever you invalid key you entered the first time around and raise a KeyError exception.

Stepping through this code in the debugger is further confusing because I can plainly see that ans contains my latest answer, in my case a '1'.

```

What type of release is this?

1 = gold
2 = QFE
3 = beta
# q

You must enter either 1, 2, or 3

What type of release is this?

1 = gold
2 = QFE
3 = beta
# 1
Traceback (most recent call last):
  File "/home/ssulliva/work/test/releaseEngineering/publishRelease/publishRelease.py", line 289, in <module>
    main()
  File "/home/ssulliva/work/test/releaseEngineering/publishRelease/publishRelease.py", line 168, in main
    rel_type = get_release_type()
  File "/home/ssulliva/work/test/releaseEngineering/publishRelease/publishRelease.py", line 227, in get_release_type
    return types[ans]
KeyError: 'q'

```

I am relatively new to Python coming from Perl. Any ideas?

---

### Post by LaRoza on 2007-12-18
When the function is called, and invalid input is given, it called itself, however, it doesn't return, so it waits for the second function call to return then it returns the original value.

It is recursive, use a loop.

[php]
while True:
    rel_type = get_release_type()
    if rel_type ! = 0:
        break
[/php]

For this, alter the function to return 0 on an error.

---

### Post by tyoc on 2007-12-18
You "recursive" call have an actual state, you are not returning the correct state, instead, you are returning just the key that you have already rejected.

---

### Post by Tuna-Fish on 2007-12-18
> **scruff said:**
> What's the deal here...

(simplified example)



You can see that get_release_type() will call itself if the user enters invalid input. The strange issue I am seeing is if you DO enter invalid input, the 2nd time around at return types[ans] it will try to look up whatever you invalid key you entered the first time around and raise a KeyError exception.

Stepping through this code in the debugger is further confusing because I can plainly see that ans contains my latest answer, in my case a '1'.

which ans? You create 2 variables named ans if you call the function 2 times.

Here is it fixed so that it's still recursive.
[PHP]
def main();
    rel_type = get_release_type()


def get_release_type():
    types = {'1': 'Gold/',
             '2': 'QFE/',
             '3': 'beta/'}
    
    ans = raw_input("\nWhat type of release is this?\n\n"
                     "1 = gold\n"
                     "2 = QFE\n"
                     "3 = beta\n# ")

    if not types.has_key(ans):
        print "\nYou must enter either 1, 2, or 3"
        return get_release_type()
        
    return types[ans]

if __name__ == '__main__':
    main()
[/PHP]

Function call is NOT a goto, don't try to use it as one.

---

### Post by scruff on 2007-12-18
Thanks for the responses.

---

### Post by pmasiar on 2007-12-19
"if not types.has_key(ans):" is ugly, cleaner way to say the same is:

"if not ans in types:"

Python does the right thing.

---

### Post by scruff on 2007-12-19
> **pmasiar said:**
> "if not types.has_key(ans):" is ugly, cleaner way to say the same is:

"if not ans in types:"

Python does the right thing.

Thanks. I'm still learning how simple Python makes things in comparison to Perl. There are so many cool ways of doing things!

With regards to my original question, I spent some time watching the call stack and now understand why this didn't work to begin with. It seemed strange to me because Perl doesn't behave this way however I also tried a similar example in c++ and it acts just like Python. 

Looks like Perl just allows too much sloppiness :)

I went Tuna-Fish's solution because it seems more readable with the entire operation contained in the function itself, which is why I went about it this way in the first place.

---

