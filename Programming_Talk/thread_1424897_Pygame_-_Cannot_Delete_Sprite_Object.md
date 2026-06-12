---
title: "Pygame - Cannot Delete Sprite Object"
date: 2010-03-08
forum: Programming Talk
---

### Post by Penguin Guy on 2010-03-08
Simple case of not understanding variables properly:
[LIST]
[*]Namespace rules apply to [FONT="Courier New"]del[/FONT] - functions and classes can't delete outside variables
[*]You use [FONT="Courier New"]pop[/FONT] or [FONT="Courier New"]remove[/FONT] to delete list items, not [FONT="Courier New"]del[/FONT]
[/LIST]

In my case, I had a list (opponents) that I was trying to delete from using a for loop and [FONT="Courier New"]del[/FONT]:
[PHP]
for opponent in opponents:
    del opponent
[/PHP]

I just switched [FONT="Courier New"]del opponent[/FONT] to [FONT="Courier New"]opponents.remove(opponent)[/FONT], now everything works fine!
[PHP]
for opponent in opponents:
    opponents.remove(opponent)
[/PHP]

Thanks to [Zugzwang]("http://ubuntuforums.org/showpost.php?p=8940641") for the help. Fixed code attached.

---

### Post by Zugzwang on 2010-03-08
A quick googling yields the following: [http://www.python.org/search/hypermail/python-1994q3/0131.html](http://www.python.org/search/hypermail/python-1994q3/0131.html)

Short story: the "del" command removes some object from the namespace. However, what you are deleting is a parameter to the function. Thus this symbol is locally bound to the function anyway and it would be removed anyway when returning from the function. Of course the caller can have a local variable named "prey" which however remains untouched by the "del" statement as only the one in the function's namespace is removed.

---

### Post by Penguin Guy on 2010-03-08
> **Zugzwang said:**
> A quick googling yields the following: [http://www.python.org/search/hypermail/python-1994q3/0131.html](http://www.python.org/search/hypermail/python-1994q3/0131.html)

Short story: the "del" command removes some object from the namespace. However, what you are deleting is a parameter to the function. Thus this symbol is locally bound to the function anyway and it would be removed anyway when returning from the function. Of course the caller can have a local variable named "prey" which however remains untouched by the "del" statement as only the one in the function's namespace is removed.
After moving the [FONT="Courier New"]del[/FONT] statement outside the function, it still fails.

---

### Post by Zugzwang on 2010-03-09
I don't quite get what you are trying to achieve with the "del" commands. Unlike in C/C++, you do not have to delete objects after you finished using them (to be precise: of course you only have the deallocate them if you allocated them manually using pointer stuff). "del" just removes the object under the stated name from the namespace. Here are some examples:

```

Python 2.6.2 (release26-maint, Apr 19 2009, 01:56:41)
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> A = "hello"
>>> print A
hello
>>> del A
>>> print A
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'A' is not defined
>>> A = [1,2,3]
>>> B = A[1]
>>> print B
2
>>> del B
>>> print A
[1, 2, 3]
>>> def myfunction(A):
...     del A
...
>>> J = "hello"
>>> myfunction(J)
>>> print J
hello
>>>

```
As you can see, in the last example, the string is still accessible even after it was deleted. This is because only the object identifier "A" in the namespace of the function is removed, but the outer namespace remains intact.

In your code, I have seen that you iterate over some containers and then "del" their elements. This does *not* remove them from the container! You have to use other functions for doing so. Either you call "del" on the list and add the index of the element to delete or you use the "remove" function of the list. Note that it generally not a good idea to remove an element from the list you iterate over, but I'm quite sure that you favourite search engine has some tricks in its database.

---

### Post by Penguin Guy on 2010-03-09
> **Zugzwang said:**
> I don't quite get what you are trying to achieve with the "del" commands. Unlike in C/C++, you do not have to delete objects after you finished using them (to be precise: of course you only have the deallocate them if you allocated them manually using pointer stuff). "del" just removes the object under the stated name from the namespace. Here are some examples:

A string is still accessible even after it was deleted. This is because only the object identifier "A" in the namespace of the function is removed, but the outer namespace remains intact.

In your code, I have seen that you iterate over some containers and then "del" their elements. This does *not* remove them from the container! You have to use other functions for doing so. Either you call "del" on the list and add the index of the element to delete or you use the "remove" function of the list. Note that it generally not a good idea to remove an element from the list you iterate over, but I'm quite sure that you favourite search engine has some tricks in its database.

Got it - all variables are pointers. Thanks, I can't believe I got this far with Python without knowing that. I just had to replace [FONT="Courier New"]del opponent[/FONT] for [FONT="Courier New"]opponents.remove(opponent)[/FONT]!

---

