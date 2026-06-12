---
title: "Creating a list of object in Pyton"
date: 2018-10-15
forum: Programming Talk
---

### Post by stevencorrea on 2018-10-15
I have created a basic class and each new object that I create, I want to append it to a list.  When I print the length of the list, the output is 1, not 3.  Based on the output generated within the for loop, I am generating 3 different objects.  Any clues as to why the listOfObjects has length 1? 

```
class newObject (object):
    total = 0


    @staticmethod
    def status():
        print("\nThe total number of new objects is", newObject.total)


    def __init__(self, name):
        print("A new object has been created!")
        self.name = name
        newObject.total += 1


#main
print("Accessing the class attribute newObject.total:", end=" ")
print(newObject.total)


print("\nCreating objects!")


for i in range(3):
    listOfObjects = []
    listOfObjects.append(newObject("object"+str(i+1)))
    newObject.status()

print (len(listOfObjects))
```

---

### Post by spjackson on 2018-10-16
Welcome to the forums. It would help greatly if you could use [code tags]("https://ubuntuforums.org/faq.php?faq=vb3_reading_posting#faq_vb3_basic_bb_code") when posting python code in order to preserve indentation.

Your problem is that this line:
```

  listOfObjects = []

```
is **inside** the for loop. So on each pass through the loop you empty out the list and append 1 item. The above line should instead appear before the for loop, like this:
```


class newObject (object):
  total = 0


  @staticmethod
  def status():
    print("\nThe total number of new objects is", newObject.total)


  def __init__(self, name):
    print("A new object has been created!")
    self.name = name
    newObject.total += 1


#main
print("Accessing the class attribute newObject.total:", end=" ")
print(newObject.total)


print("\nCreating objects!")


listOfObjects = []
for i in range(3):
  listOfObjects.append(newObject("object"+str(i+1)))
  newObject.status()

print (len(listOfObjects))


```

---

