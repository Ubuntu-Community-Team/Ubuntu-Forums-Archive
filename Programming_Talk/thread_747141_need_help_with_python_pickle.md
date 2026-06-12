---
title: "need help with python pickle"
date: 2008-04-06
forum: Programming Talk
---

### Post by rob1101 on 2008-04-06
i am having trouble just getting pickle to work. 

the error
```

[robert@robert-laptop:~]$ python /home/robert/test.py
Traceback (most recent call last):
  File "/home/robert/test.py", line 7, in <module>
    pickle.dump(picklelist, picklefile)
  File "/usr/lib/python2.5/pickle.py", line 1362, in dump
    Pickler(file, protocol).dump(obj)
  File "/usr/lib/python2.5/pickle.py", line 224, in dump
    self.save(obj)
  File "/usr/lib/python2.5/pickle.py", line 286, in save
    f(self, obj) # Call unbound method with explicit self
  File "/usr/lib/python2.5/pickle.py", line 646, in save_dict
    write(MARK + DICT)
IOError: [Errno 9] Bad file descriptor

```

the code
```

import pickle

picklelist = {'item': 0, 'item2': 1}

picklefile = open("/home/robert/test.txt", "r")

pickle.dump(picklelist, picklefile)

```

---

### Post by smartbei on 2008-04-06
You probably want the file descriptor flag on 'w' if you are going to dump to a file... :D

---

### Post by rob1101 on 2008-04-06
its always the easy stuff that gets me lol

how would i unpickle

---

### Post by smartbei on 2008-04-06
Use pickle.load, and pass it a read file descriptor for the file with the pickled data.

BTW - I recommend that you use cPickle - it is much faster for large sets of data.

---

### Post by rob1101 on 2008-04-06
i swear i got it right in this code here but it gives me an error

```

# Pikcle index
def pickle_index(index_name):
    
    
    index = {'grub.lst':0}
    index_unpickle = open('/home/robert/.backup/index.txt', 'r')
    
    index = pickle.load(index_unpickle)
    index[index_name] += 1
    
    index_file = open('/home/robert/.backup/index.txt', 'w')
    pickle.dump(index, index_file)
    
    return(index[index_name])
    
    
    file.close(index_file)

```

but i get this error
```

Traceback (most recent call last):
  File "/home/robert/Desktop/safe_edit/safe_edit.py", line 11, in <module>
    filepath, filevar = get_option()
  File "/home/robert/Desktop/safe_edit/safe_edit_functions.py", line 19, in get_option
    index_num = pickle_index(index_name)
  File "/home/robert/Desktop/safe_edit/safe_edit_functions.py", line 46, in pickle_index
    index = pickle.load(index_unpickle)
  File "/usr/lib/python2.5/pickle.py", line 1370, in load
    return Unpickler(file).load()
  File "/usr/lib/python2.5/pickle.py", line 858, in load
    dispatch[key](self)
  File "/usr/lib/python2.5/pickle.py", line 880, in load_eof
    raise EOFError
EOFError
```

am i missing somthing simple agin?

---

### Post by rob1101 on 2008-04-06
nvm i got it :P thx for the help :)

---

