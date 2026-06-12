---
title: "Python Word manipulation"
date: 2011-09-12
forum: Programming Talk
---

### Post by Ravenshade on 2011-09-12
Hi folks. This little problem is stumping me. I want to: 

```

def Alter(take_old_Word):
     #somehow change Bird to ...ex: 32Ab 
     return the_new_word

old_word = "Bird"

new_word = alter(myWord)
```

Now... adding things I can do, but I'm not certain how to split the string into single letters which I can then do...nasty things to

---

### Post by Senesence on 2011-09-12
You can iterate over each character like this:

```

my_str = "Bird"

for c in my_str:
 print c

```

---

### Post by Ravenshade on 2011-09-12
That's good, but then there's no way to get back :confused:

---

### Post by Erdaron on 2011-09-12
I think what Senesence meant to illustrate is that a string is basically an iterable. For example:
```
>>> a = 'blah'
>>> b = []
>>> for letter in a:
	b.append(letter)

	
>>> b
['b', 'l', 'a', 'h']
```

Once you have a list of altered letters, you can re-assemble it into a word using the .join() method on an empty string:
```
>>> ''.join(b)
'blah'
```
Enjoy doing nasty things to letters :).

---

### Post by cgroza on 2011-09-12
> **Erdaron said:**
> I think what Senesence meant to illustrate is that a string is basically an iterable. For example:
```
>>> a = 'blah'
>>> b = []
>>> for letter in a:
    b.append(letter)

    
>>> b
['b', 'l', 'a', 'h']
```Once you have a list of altered letters, you can re-assemble it into a word using the .join() method on an empty string:
```
>>> ''.join(b)
'blah'
```Enjoy doing nasty things to letters :).
Or you could just do:
```

list(my_string)

```
and you get a list of characters.

You could access it by index instead of using an iterator so you can jump wherever you want through it.

---

### Post by Smart Viking on 2011-09-12
```
>>> def word(word):
...   word = word[::-1]
...   return word
... 
>>> stri = "Hello, Word!"
>>> word(stri)
'!droW ,olleH'
>>> 
```Characters in strings in python can be retrieved like elements from a list. To get the first character, do string[0] etc:

```

>>> stri = "Hello, Word!"
>>> stri
'Hello, Word!'
>>> stri = stri[:10]+"l"+stri[-2:]
>>> stri
'Hello, World!'

```To assign items directly though, it needs to be a mutable list, like those before me explained.

---

### Post by Ravenshade on 2011-09-12
Thanks for the assistance. It has proved most lucrative. I'll reveal the reason. I've just learned about Input Output using data files and I've created a login system for my program. Unfortunately that meant the password was out in the open. 

So I wanted to manipulate the password somehow to encrypt it. So i've made it so that the program changes the letters to something not so readable. Thanks muchly.

---

### Post by StephenF on 2011-09-13
Well now that you have told us what you are really trying to do here is the proper answer.
```

import hashlib

password = "123456"  # Don't ever use 123456 in real life.
encrypted_form = hashlib.sha1(password).hexdigest()

print password, encrypted_form

```
This type of encryption is not reversible or at least not in a practical timeframe. If you need better security try sha512.

The idea is to encrypt the password entered by the user and compare it to the encrypted form in the password file and not the other way around.

---

### Post by ofnuts on 2011-09-13
> **StephenF said:**
> Well now that you have told us what you are really trying to do here is the proper answer.
```

import hashlib

password = "123456"  # Don't ever use 123456 in real life.
encrypted_form = hashlib.sha1(password).hexdigest()

print password, encrypted_form

```This type of encryption is not reversible or at least not in a practical timeframe. If you need better security try sha512.

The idea is to encrypt the password entered by the user and compare it to the encrypted form in the password file and not the other way around.
Actually the proper way is to encode userid+password, otherwise all users with the same password end up with the same hash and this makes things very easy for a dictionary attack.

---

