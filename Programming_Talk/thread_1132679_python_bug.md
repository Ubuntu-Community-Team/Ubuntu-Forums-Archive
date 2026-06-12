---
title: "python bug?"
date: 2009-04-22
forum: Programming Talk
---

### Post by giuspen on 2009-04-22
today i find something in python that left me without words, please help me it's just a couple of rows:

IDLE 2.6.1
>>> test = [{'key':[]}]
>>> test.append(test[0])
>>> test
[{'key': []}, {'key': []}]
>>> test[0]['key'].append('element')
>>> test
[{'key': ['element']}, {'key': ['element']}]
>>>

i duplicate an element of the vector, then i work upon one element and the other element changes too!
is this a bug? if not how can i duplicate an element of the vector without have it connected with the original?
thanks in advance.

---

### Post by unutbu on 2009-04-22
{'key':[]} is a dictionary object.
When you type 
```

test.append(test[0])
```

the list called "test" gets two copies of the same dictionary object.

When you type
```

test[0]['key']
```

you access the list inside the "{'key':[]}" dictionary object. And when you append 'element' to this list, the "{'key':[]}" dictionary object is changed. Since the list called "test" had two copies of the same dictionary, both dictionaries appear modified.

If you use
```

test.append({'key':[]})
```

instead of 
```

test.append(test[0])
```

then you will get two different dictionary objects in test.

---

### Post by giuspen on 2009-04-22
> **unutbu said:**
> {'key':[]} is a dictionary object.
When you type 
```

test.append(test[0])
```

the list called "test" gets two copies of the same dictionary object.

When you type
```

test[0]['key']
```

you access the list inside the "{'key':[]}" dictionary object. And when you append 'element' to this list, the "{'key':[]}" dictionary object is changed. Since the list called "test" had two copies of the same dictionary, both dictionaries appear modified.

If you use
```

test.append({'key':[]})
```

instead of 
```

test.append(test[0])
```

then you will get two different dictionary objects in test.

i understand, thanks, the problem is that i simplified the problem but i need to append to the list a exact copy of a dictionary that is in another position of the list.
is there a way to duplicate an element in the list that is a dictionary without having them connected?

---

### Post by giuspen on 2009-04-22
got it: [http://www.doughellmann.com/PyMOTW/copy/index.html]("http://www.doughellmann.com/PyMOTW/copy/index.html")

[PHP]import copy

new_dict = copy.deepcopy(original_dict)[/PHP]

---

