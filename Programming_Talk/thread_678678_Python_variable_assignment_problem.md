---
title: "Python variable assignment problem"
date: 2008-01-26
forum: Programming Talk
---

### Post by G|N| on 2008-01-26
Hi,

I have  a little programming problem:
I have a variable 'values' that holds a dictionary with values (user, password,...)
In the actual program i want them to be assigned dynamically like this:
```

#the values that were given to the class
values = {'name':'test', 'user': 'me', 'password': 'hello'}


name = ""
user = ""
password = ""
#the first is the label (the same as in values), the second is the variable
#where it has to be assigned to.
watch_values = [
                ['name', name], 
                ['user', user], 
                ['password', password]
               ]
               
watch_values[0][1] = values[watch_values[0][0]]
print watch_values[0][1]
print name
print user
print password

```

of course this does not work because my values['name'] is stored in watch_values[0][1] and not the variable that it held before.

Is there a way to assign it to the variable instead of watch_values?

I want to make a dynamic assignment so i can automatically check if all values are filled in.

---

### Post by Quikee on 2008-01-26
If I understand what you want to do is that when you do this: 
```
watch_values[0][1] = values[watch_values[0][0]]
```
that in the same time your variable 'name' gets the value that has been assigned to watch_values[0][1] (watch_values[0][1] should be identical to name)?

You can only do this "dynamically" if name, user, password variables are also declared as lists.

#the values that were given to the class
values = {'name':'test', 'user': 'me', 'password': 'hello'}

[PHP]
name = ["a"]
user = ["b"]
password = ["c"]
#the first is the label (the same as in values), the second is the variable
#where it has to be assigned to.
watch_values = [
                ['name', name], 
                ['user', user], 
                ['password', password]
               ]
               
watch_values[0][1][0] = values[watch_values[0][0]]
print watch_values[0][1]
print name[0]
print user[0]
print password[0][/PHP]

Alternatively you could manually change valuse in globals() dictionary on assignment of the value. 

Generally I don't think there is need for a thing like that at all.

---

