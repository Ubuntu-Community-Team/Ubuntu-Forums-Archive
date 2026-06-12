---
title: "[SOLVED] [Python] Case Sensitivity?"
date: 2008-09-30
forum: Programming Talk
---

### Post by dodle on 2008-09-30
I was wondering if there was a way to bypass case sensitivity when it came to the 'raw_input' command.  For example:

Instead of having to write all of this:[PHP]answer = raw_input('Enter yes or no:  ')
if answer in ('y', 'Y', 'yes', 'Yes', 'YEs', 'YES', 'yEs', 'yES', 'yeS'):
    print "That's Great"
elif answer in ('n', 'N', 'no', 'No', 'NO', 'nO'):
    print "That's too bad"[/PHP]
I would like to simply write this:[PHP]answer = raw_input('Enter yes or no:  ')
if answer in ('y', 'yes'):
    print "That's Great"
elif answer in ('n', 'no'):
    print "That's too bad"
[/PHP]So no matter what case "answer" is put in, it will be read correctly.

---

### Post by ghostdog74 on 2008-09-30
just convert whatever that is entered to lowercase.

---

### Post by 3rdalbum on 2008-09-30
```

answer = raw_input('Enter yes or no:  ').lower()
if answer=='yes': print "That's great!"
elif answer=='no': print "That's too bad"

```

I didn't realise you could do "if string in ("a", "b", "c")", so thanks for the tip :-)

---

### Post by gomputor on 2008-09-30
```
answer = raw_input('Enter yes or no:  ').lower()
```

---

### Post by dodle on 2008-09-30
Can I still add split()?

like:[PHP]answer = raw_input('Enter yes or no').lower().split()[/PHP]

---

### Post by pmasiar on 2008-09-30
> **dodle said:**
> Can I still add split()?

like:[PHP]answer = raw_input('Enter yes or no').lower().split()[/PHP]

yes, it is called "chaining". Pretty cool feature.

But you don't have to ask, just try it in Python shell. ;-)

---

### Post by gomputor on 2008-09-30
> **dodle said:**
> Can I still add split()?

like:[PHP]answer = raw_input('Enter yes or no').lower().split()[/PHP]

Yes you can use split() that way.

But a better way to test all these, is simply invoke the python interpreter and make your tests there.
Open your terminal and just type python. You'll see something like this:

Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>

Type your code there and test it.

---

### Post by dodle on 2008-09-30
Sorry, I'm being lazy 'cuz I'm sleepy I guess.

---

### Post by dodle on 2008-09-30
I've found that if I put in ".lower().split()" it works just fine.  But if I input ".split().lower()" it returns the following error:```
AttributeError: 'list' object has no attribute 'lower'
```Why is this?

---

### Post by ghostdog74 on 2008-09-30
when you do split(), the result is a list. A list do not have lower() method.

---

### Post by dodle on 2008-09-30
Okay, I think I understand.

---

### Post by gomputor on 2008-09-30
> **dodle said:**
> I would like to simply write this:[PHP]answer = raw_input('Enter yes or no:  ')
if answer in ('y', 'yes'):
    print "That's Great"
elif answer in ('n', 'no'):
    print "That's too bad"
[/PHP]So no matter what case "answer" is put in, it will be read correctly.

A better way for your case:
```
answer = raw_input('Enter yes or no:  ')
if answer.lower() in ('y', 'yes'):
    print "That's Great"
elif answer.lower() in ('n', 'no'):
    print "That's too bad"
```

---

