---
title: "Help understanding synax in c++ (the int&amp;)"
date: 2006-08-05
forum: Programming Talk
---

### Post by cobbweb on 2006-08-05
Hey, 
 
 Im learing c++ and can't find out what the diffrence between the "int&" declaration and the "int" is. What is the diffrence?????

 
 Thank you so much, 

 Cobbweb

---

### Post by ylixir on 2006-08-05
i'm assuming you are looking at something that looks kind of like
```
void func(int & x){}
```
basically the & says "don't make a copy of this variable, use the same variable"

that probably doesn't make sense, so here is an example
```

void byref(int & x){ x++; }

void byval(int x){ x++; }

void main()
{
  int y=0;
  //so y is zero right now
  byval(y); //the program is giving byval a copy of y to work with, so
            //byval can do whatever it wants, and the value of y will not
            //change

  //y is still zero right now
  byref(y); //the program is actually giving the function access to y, so
            //whatever the function does to it will show up here.
  
  //y is now one, because byref incremented it.
  return;
}

```

hopefully that makes sense?

---

### Post by ifokkema on 2006-08-05
ylixir gave you a good example. If you want to know more, maybe this page will help you out:
[http://cplus.about.com/od/beginnerctutorial/l/aa061002a.htm](http://cplus.about.com/od/beginnerctutorial/l/aa061002a.htm)

Have fun!

---

### Post by cobbweb on 2006-08-05
wow this really helped. Yes I get it now, thank you very much. 

 Cobbweb

---

