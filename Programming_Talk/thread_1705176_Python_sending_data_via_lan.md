---
title: "Python sending data via lan?"
date: 2011-03-11
forum: Programming Talk
---

### Post by BlackRat90 on 2011-03-11
I fairly new to python, but Ive been studing 3.1 and I believe I have a fair understanding in it.

I was hoping someone might be able to aid my curiosity on the subject of making a program (in this case is a simple game) talk to its self on another computer over LAN or the internet through the use of TCP or something?

an example of the simple game being:
```

print("Choose the highest number?"
number = input()
#Sends number to other player and receives the number the other player gave
if number > enemiesNumber:
print("You win!")

```

---

### Post by cgroza on 2011-03-11
Take a look at socket:
[http://docs.python.org/howto/sockets.html](http://docs.python.org/howto/sockets.html)

---

### Post by BlackRat90 on 2011-03-11
Thanks a ton! thats exactly what i was looking for!

---

