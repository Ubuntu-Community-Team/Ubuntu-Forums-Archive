---
title: "Python help. AttributeError: 'NoneType' object has no attribute"
date: 2015-01-22
forum: Programming Talk
---

### Post by dana09alexandra on 2015-01-22
so i have this little program

```
class MyTodos:
    def __init__(self):
        self.list = []


    def add(self, todo):
        self.list.append(todo)


    def filter(self, s):
        l = []
        for i in self.list:
            if i.find(s) != -1:
                l.append(i)
        return l




todos = MyTodos()
todos.add("prepare fp").add("learn python").add("learn JS")
for todo in todos.filter("learn"):
    print(todo)
```

and i get this error:

```
todos.add("prepare fp").add("learn python").add("learn JS")
AttributeError: 'NoneType' object has no attribute 'add'
```

how can i fix it? i don't understand why after performing this:  ```
todos.add("prepare fp")
```  todos becomes a NoneType

---

### Post by Vaphell on 2015-01-22
todos stays todos just fine.
You have chained function calls yet add() returns nothing so it stops being about todos after the very first step

```
[COLOR="#0000FF"]todos.add("prepare fp")[/COLOR].add("learn python").add("learn JS")
=
[COLOR="#0000FF"]some_obj[/COLOR].add("learn python").add("learn JS")
=
[COLOR="#0000FF"]None[/COLOR].add("learn python").add("learn JS")

```

what would some_obj be? it's not todos, that's for sure.
add("learn python") is expected to be a method of the object coming from todos.add("prepare fp") but it's going to be *None*, because the function in question doesn't return anything.
and add("learn JS") does the same with the result of add("learn python")

add() in this form is to be executed only once at a time.

```
todos = MyTodos()
todos.add("prepare fp")
todos.add("learn python")
todos.add("learn JS")
```

in order to make add() chainable you'd have to add **return self** to it

---

### Post by dana09alexandra on 2015-01-22
thank you very much.

---

