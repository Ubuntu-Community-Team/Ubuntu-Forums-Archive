---
title: "[Python] Need help with this code"
date: 2008-05-22
forum: Programming Talk
---

### Post by blaq145 on 2008-05-22
this part of the code should reflect the user's input

when i type in 

reflect_phrase('You are the same as me')
    
Expected:
    'I am the same as you'

this is the list of reflections
the first word being the one in the user's input and the second being it's replacement

reflections = \
[
['yourself', 'myself'],
['myself', 'yourself'],
['your', 'my'],
['Your', 'My'],
['my', 'your'],
['My', 'Your'],
['you', 'I'],
['You', 'I'],
['I', 'you'],
['me', 'you'],
['am', 'are'],
['Am', 'Are'],
['are', 'am'],
['Are', 'Am'],
['was', 'were'],
['were', 'was'],
['Was', 'Were'],
['Were', 'Was'],
['we', 'us'],
['We', 'Us'],
['us', 'we']
]

---

### Post by blaq145 on 2008-05-22
this is the code i've got

```
def reflect_phrase(word):    
    ret = word.split()    

    for a in reflections:        
        i = 0        
        for b in ret:            
            if b == a[0]:                
                ret[i] = a[1]                
            i = i+1 

    if len(ret) > 0:        
        ret1 = ret[0]        
        i=0
        
        for k in ret:            
            if i > 0:                
                ret1 = ret1 + ' ' + k                
            i = i+1            
        print ret1
        
    else:        
        print word
```

---

### Post by imdano on 2008-05-22
Why not use a dict to hold the reflections?  Then you could just do something like:
[php]
def reflect_phrase(sentence):
    new_sent = ""
    for word in sentence.split():
        if reflections.has_key(word):
            new_sent = ''.join([new_sent, reflections[word], ' '])
        else:
            new_sent = ''.join([new_sent, word, ' '])
    return new_sent.strip()
[/php]

edit:
Also keep in mind you can convert your reflections list to a dict simply by doing
```
reflect = dict(reflections)
```

---

### Post by blaq145 on 2008-05-22
hi imdano, thanks for the reply
however it didn't work for all the tasks, there are 12 tasks

eg.
reflect_phrase('Do you think me and you should get together')
Expected:
    'Do I think you and I should get together'
Got:
    Do you think you and you should get together


reflect_phrase('What are you saying to me') 
Expected:
    'What am I saying to you'
Got:
    What am you saying to you


reflect_phrase('You are my friend')
Expected:
    'I am your friend'
Got:
    you am your friend

---

### Post by imdano on 2008-05-22
Try again, there was a typo or two in there I might have edited after you looked.  That or your dict isn't quite right, because all of those are working for me.

---

### Post by blaq145 on 2008-05-22
i applied the changes and only 1 task works

rying:
    reflect_phrase('')
    
Expecting:
    ''
ok

the rest just return something like this

Failed example:
    reflect_phrase('Do you think me and you should get together')
   
Exception raised:
    Traceback (most recent call last):
      File "C:\Python25\lib\doctest.py", line 1228, in __run
        compileflags, 1) in test.globs
      File "<doctest __main__[37]>", line 1, in <module>
        reflect_phrase('Do you think me and you should get together')
      File "C:\xxxx\xxxx\xxxx\xxxxx\xxxxxx.py", line 1240, in reflect_phrase
        if reflections.has_key(word):
    AttributeError: 'list' object has no attribute 'has_key'

---

### Post by WW on 2008-05-22
imdano's code expects the variable **reflections** to be a dict, but your definition of **reflections** is a list.  In post 3, imdano showed the command that creates a dict called **reflect**. If you use this, then you can get imdano's function to work by changing the two occurrences of **reflections** to **reflect**.  Perhaps a better way is to make the dict an argument:
```

def reflect_phrase(sentence,reflect):
    new_sent = ""
    for word in sentence.split():
        if reflect.has_key(word):
            new_sent = ''.join([new_sent, reflect[word], ' '])
        else:
            new_sent = ''.join([new_sent, word, ' '])
    return new_sent.strip()

```
For example,
```

>>> ref = dict(reflections)
>>> reflect_phrase('What are you saying to me',ref)
'What am I saying to you'
>>> reflect_phrase('You are my sunshine',ref)
'I am your sunshine'
>>> reflect_phrase('Do you think me and you should get together',ref)
'Do I think you and I should get together'
>>> 

```

---

### Post by tamoneya on 2008-05-22
I just tested the code from WW and it seems to check out fine on my end.  I also agree, a dictionary is the best way to do this.

---

### Post by blaq145 on 2008-05-22
Thank you! That helped out alot. It's working now. Thanks again!

---

