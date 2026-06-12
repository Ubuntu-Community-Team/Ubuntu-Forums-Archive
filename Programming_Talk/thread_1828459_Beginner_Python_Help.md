---
title: "Beginner Python Help"
date: 2011-08-18
forum: Programming Talk
---

### Post by Jakemurray on 2011-08-18
Hey im sure this is a dumb question, but im trying to teach myself python and i dont know anyone else whos into computers so i have to ask all of my questions here...
i was reading a byte of python and it was explaining the format method, i understood it all then it threw this at me

"
>>> '{0:.3}'.format(1/3) # decimal (.) precision of 3 for float
'0.333'
>>> '{0:_^11}'.format('hello') # fill with underscores (_) with the text
centered (^) to 11 width
'___hello___'
>>> '{name} wrote {book}'.format(name='Swaroop', book='A Byte of Python')
# keyword-based
'Swaroop wrote A Byte of Python'
"
for whatever reasons i dont understand these examples
it went to this right after examples like;

print('{0} is {1} years old'.format(name, age))
print('Why is {0} playing with that python?'.format(name))

which i could understand.
Thank you for any help.

---

### Post by An Sanct on 2011-08-19
I'm not a python god, but my answer should do ;)

PS. ask questions here, that is why this forum exists...

>>> '{0:.3}'.format(1/3) # decimal (.) precision of 3 for float '0.333'

This formats a number with a three digits precission, so the number *pi* would be *3.141* . 
In your example you have *1 divided by 3* (1/3) it is *0.333333(to infinity)*, formatted to three digits, that is *0.333*.

>>> '{0:_^11}'.format('hello') # fill with underscores (_) with the text centred (^) to 11 width '___hello___'

This formats a string starting from 11 * '_', so '___________' and inserts the text hello centered in the middle of thos 11 underlines.

>>> '{name} wrote {book}'.format(name='Swaroop', book='A Byte of Python') # keyword-based 'Swaroop wrote A Byte of Python'"

The keyword based format works is like string replace so 
'{X} lal{Y}ala {Z}'.format(X='First Thing', Y=' Between LALALA ', Z=' ktnxby!')
would produce this -> 'First Thing lal Between LALALA ala  ktnxby!'

---

