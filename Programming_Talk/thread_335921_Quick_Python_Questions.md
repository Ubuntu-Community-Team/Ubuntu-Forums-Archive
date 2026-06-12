---
title: "Quick Python Questions"
date: 2007-01-10
forum: Programming Talk
---

### Post by amunimanghi on 2007-01-10
Hello,

I took up python a while back and decided to make a cititing sources program. So far i'm just making the base of it and later will create a gui for it. I have one question though. I'm having some trouble. Here is the portion in which I'm having trouble with: ```

print "Use quit without the quotes to exit. You can quit anytime."
print underline,"Menu Options",reset
print '1. Cite a book'
print '2. Cite a webpage'
print '3. Cite an encyclopedia article'
print '4. Cite an online encyclopedia article'
menu = raw_input('Type Option Number: ')
#this only allows the numbers above and nothing else
if menu != '1.' or '1' or '2' or '2.' or '3' or '3.' or '4.' or '4':
        print 'No letters allowed. Use only then numbers above.'

```

I want to make it so if they type something other than the numbers, it will display the menu and alow the user the choose it again. Hopefully I explained it well. Thanks

---

### Post by meng on 2007-01-10
What you need is a loop, for example, something like:

```

options = ['1. Cite a book', '2. Cite a webpage', '3. Cite an encyclopedia article', '4. Cite an online encyclopedia article']
menu = '\n'.join(options)
validChoices = [i[0] for i in options]
while True:
    print menu
    choice = raw_input('Type option number: ')
    if choice[0] in validChoices: break
    print "Invalid choice. Choose from the numbers above"

```

I've taken the liberty of refactoring your code, quite a lot. It could even be refactored further, to make expansion of your menu options more straightforward for future versions of your program. I haven't bothered debugging it though, so someone will probably find 5 errors in my code.

EDIT: No I had to go back and debug.
SECOND EDIT: This would also be a good time for you (and me) to revise the try/except functions in Python!

---

### Post by amunimanghi on 2007-01-10
Ok, thanks, thats ill I needed to know. :)

---

