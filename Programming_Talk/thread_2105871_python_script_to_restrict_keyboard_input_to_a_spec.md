---
title: "python script to restrict keyboard input to a specified length of characters"
date: 2013-01-17
forum: Programming Talk
---

### Post by madhu91 on 2013-01-17
hi..
i am trying to write a script, which accepts user input from keyboard. similar to this.
[http://stackoverflow.com/questions/8761778/limiting-python-input-strings-to-certain-characters-and-lengths](http://stackoverflow.com/questions/8761778/limiting-python-input-strings-to-certain-characters-and-lengths)

however, my idea is to stop the cursor in the output terminal, after it reaches a specified length (say 16 characters).

how do i do this? please help!

---

### Post by cariboo on 2013-01-18
Moved to programming talk

---

### Post by greenpeace on 2013-01-19
Not sure if you can to be honest... but probably the best thing is to handle the input afterwards:

You can define an exception to do this, or just trim/delete the content as you see fit... 

```
#!/usr/bin/env python

class LengthError(Exception):
  def __init__(self, value): 
    self.value = value 

user_input = raw_input("Enter 5 characters of text: ")

if len(user_input) > 5:
  raise LengthError("Input stream too long")
  
print user_input
```

gives:

```
gp@mariachi:~$ ./error.py 
Enter 5 characters of text: 12345
12345
gp@mariachi:~$ 
gp@mariachi:~$ 
gp@mariachi:~$ ./error.py 
Enter 5 characters of text: 123456
Traceback (most recent call last):
  File "./error.py", line 11, in <module>
    raise LengthError("Input stream too long")
__main__.LengthError
gp@mariachi:~$ 
gp@mariachi:~$ 
```

---

