---
title: "Python help needed..."
date: 2012-06-05
forum: New to Ubuntu
---

### Post by abnordude on 2012-06-05
I studied C++ in my higher secondary studies (which I just completed)

Now I'm planning on studying python.....

I'm just beggining.......

I need help on a matter.....

In C++ I can write...
cout<<"The factorial of the number is " << factorial;

How can  do the same in python?????

---

### Post by abnordude on 2012-06-05
It's okay guys,.....

I figured it out with the help of a tutorial.....

Thanks everyone......

And for those who dont know...

we use it like this...
print ("The factorial of the number is " + str(factorial))

Note: str should be used for converting the integer to string.....

---

### Post by surfer on 2012-06-05
or, if you want more variables nicely formatted into a string:
```
print("The factorial of the number is {0}".format(factorial) )
```

---

