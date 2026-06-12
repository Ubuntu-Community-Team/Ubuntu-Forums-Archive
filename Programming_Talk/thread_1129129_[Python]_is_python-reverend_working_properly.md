---
title: "[Python] is python-reverend working properly?"
date: 2009-04-18
forum: Programming Talk
---

### Post by unutbu on 2009-04-18
I'm trying to learn how to use python-reverend.

After installing the python-reverend package, I try the example code from
[http://www.divmod.org/trac/wiki/DivmodReverend:](http://www.divmod.org/trac/wiki/DivmodReverend:)

[PHP]
#!/usr/bin/env python
from reverend.thomas import Bayes
guesser = Bayes()
guesser.train('french', 'le la les du un une je il elle de en')
guesser.train('german', 'der die das ein eine')
guesser.train('spanish', 'el uno una las de la en')
guesser.train('english', 'the it she he they them are were to')
guesser.train('english', 'the rain in spain falls mainly on the plain')
#                    es  de  fr fr/es fr/es fr   en
print(guesser.guess('uno das je de    la    elle in'))
# [('german', 0.99990000000000001), ('english', 0.99990000000000001), ('french', 0.67285006523593538), ('spanish', 0.58077905232271598)][/PHP]

If I understand correctly, guesser.guess should try to tell me what language is the sentence 'uno das je de    la    elle in'. It seems to think it is most likely German or English. 

But 
[list]
[*]there is only one "German" word in the sentence, das.
[*]there is only one "English" word in the sentence, in.
[*]there are four "French" words, je de la elle.
[*]there are three "Spanish" words, uno de la.
[/list]

If anything, it seems one should guess the sentence is French.
What is the good Reverend thinking?

Also, does anyone know where I can find documentation on python-reverend?

---

