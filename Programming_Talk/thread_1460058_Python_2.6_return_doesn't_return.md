---
title: "Python 2.6 return doesn't return"
date: 2010-04-22
forum: Programming Talk
---

### Post by saphil on 2010-04-22
What obvious thing am I missing?
 
```

# python 2.6
def main():
    cow = raw_input('What\'s your cow\'s name?   ')
    moo(cow)
    print 'Your cow\'s new name is %s' % (cow)

def moo(c):
    c = 41
    a = "mooey"
    b = "looey"
    if c == a:
        cow = "bossy"
        print 'How do you like the name %s?' % (cow)
    elif c == b:
        cow = "chessie"
        print 'How do you like the name %s?' % (cow)
    else:
        cow = "slow-foot"
        print 'How do you like the name %s?' % (cow)
    return cow
main()

```the following is the output
the module takes the input from main, but dosn't return the changed value of the variable.
 
```
>>> 
What's your cow's name?   we
How do you like the name slow-foot?
Your cow's new name is we
>>> 
```

---

### Post by WillFerrellLuva on 2010-04-22
I believe doing this will fix your problem:

```

new_name = moo(cow)
print 'Your cow\'s new name is %s' % (new_name)

```

---

### Post by saphil on 2010-04-22
Thanks, that fixed the return. 
```
# python 2.6
def main():
    cow = raw_input('What\'s your cow\'s name?   ')
    moo(cow)
    new_name = moo(cow)
    print 'Your cow\'s new name is %s' % (new_name)
def moo(cow):
    if cow == 'mooey':
        cow = "bossy"
        print 'Do you like the name %s?' % (cow)
    elif cow == 'looey':
        cow = "chessie"
        print 'How do you like the name %s?' % (cow)
    else:
        cow = "slow-foot"
        print 'Don\'t you like the name %s?' % (cow)
    return cow
main()
```
 
but now the output doubles the print line.  when I comment out the module's print line, it doesn't print at all.
 
```
>>> 
What's your cow's name?   mooey
Do you like the name bossy?
Do you like the name bossy?
Your cow's new name is bossy
>>> ====== RESTART ========
>>> 
What's your cow's name?   rdg
Your cow's new name is slow-foot
>>> ====== RESTART ========
>>> 
What's your cow's name?   ol
Don't you like the name slow-foot?
Don't you like the name slow-foot?
Your cow's new name is slow-foot
>>> 

```

---

### Post by simeon87 on 2010-04-22
That's because you're calling moo twice:

```

moo(cow)
new_name = moo(cow)
```

The first time, it calls moo but it doesn't use the return value. Then you're calling moo again and you're using the return value. Both times, it'll print that line of text.

---

### Post by saphil on 2010-04-22
Aha!  I was visualizing it as running moo(cow) and then using the content with the next line.  That is fun.

---

