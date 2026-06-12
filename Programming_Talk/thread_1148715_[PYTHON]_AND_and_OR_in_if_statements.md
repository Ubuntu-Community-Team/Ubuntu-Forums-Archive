---
title: "[PYTHON] AND and OR in if statements"
date: 2009-05-04
forum: Programming Talk
---

### Post by maandverband on 2009-05-04
Hello. I've just started Python and I have a question. Can I turn this:

```

answer = raw_input('Do you like Monty Python?')

if answer == 'yes':
    print 'Ok'
elif answer == 'oui':
    print 'Ok'
elif answer == 'ja':
    print 'Ok'
elif answer == 'no':
    print 'I don\'t like you!'
elif answer == 'nein':
    print 'I don\'t like you!'
elif answer == 'nee':
    print 'I don\'t like you!'

```

into something like this:

```

answer = raw_input('Do you like Monty Python?')

if answer == 'yes' || 'oui' || 'ja':
    print 'Ok'
elif answer == 'no' || 'nein' || 'nee':
    print 'I don\'t like you!'

```

---

### Post by dandaman0061 on 2009-05-04
Use a list for the options you want to check for.  e.g.
```

answer = raw_input('Do you like Monty Python?')

if answer in ['yes', 'oui', 'ja']:
    print 'Ok'
elif answer in ['no', 'nein', 'nee']:
    print 'I don\'t like you!'

```

Another suggestion for the heck of it would be to check if answer.strip().lower() is in the lists.  That way you would get rid of any spaces and the user could enter "Yes" instead of "yes"

---

### Post by Can+~ on 2009-05-04
> **maandverband said:**
> Hello. I've just started Python and I have a question. Can I turn this:

...

into something like this:

```

answer = raw_input('Do you like Monty Python?')

if answer == 'yes' || 'oui' || 'ja':
    print 'Ok'
elif answer == 'no' || 'nein' || 'nee':
    print 'I don\'t like you!'

```

Of course you can, the C-ish way:

```

answer = raw_input('Do you like Monty Python?')

if answer == 'yes' || answer == 'oui' || answer == 'ja':
    print 'Ok'
elif answer == 'no' || answer == 'nein' || answer == 'nee':
    print 'I don\'t like you!'

```

Or the pythonic way

(Posted above with "in")

---

### Post by maandverband on 2009-05-04
> **dandaman0061 said:**
> Use a list for the options you want to check for.  e.g.
```

answer = raw_input('Do you like Monty Python?')

if answer in ['yes', 'oui', 'ja']:
    print 'Ok'
elif answer in ['no', 'nein', 'nee']:
    print 'I don\'t like you!'

```

Another suggestion for the heck of it would be to check if answer.strip().lower() is in the lists.  That way you would get rid of any spaces and the user could enter "Yes" instead of "yes"

Great. Thank you for the answer.strip().lower() tip. That was going to be my next question.

---

### Post by Reiger on 2009-05-04
Out of curiosity, 'maandverband': why did you choose to call yourself 'sanitory towel'?

---

### Post by ibuclaw on 2009-05-04
> **Reiger said:**
> Out of curiosity, 'maandverband': why did you choose to call yourself 'sanitory towel'?
Please try not to sway offtopic.

I am closing this thread as the OP's question has been answered, and the thread has outlived it's life.

---

