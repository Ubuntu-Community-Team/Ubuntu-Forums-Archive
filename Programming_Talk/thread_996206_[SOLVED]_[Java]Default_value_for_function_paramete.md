---
title: "[SOLVED] [Java]Default value for function parameters?"
date: 2008-11-28
forum: Programming Talk
---

### Post by fiddler616 on 2008-11-28
Hello,
This is a quickie: Is there a way to assign a default value to a parameter in Java? For example, in Python you can do:
[PHP]
def spam(eggs = "tasty"):
    print eggs
spam() # "tasty"
spam("gross") #Returns "gross"
[/PHP]
Similar syntax in Java has failed me, and Google was obstinate (the only definitive answer came from a forum that´s way too 1337 for the likes of me...so I´m not sure I believe it)

Thanks

---

### Post by tinny on 2008-11-28
> **fiddler616 said:**
> Hello,
This is a quickie: Is there a way to assign a default value to a parameter in Java? For example, in Python you can do:
[PHP]
def spam(eggs = "tasty"):
    print eggs
spam() # "tasty"
spam("gross") #Returns "gross"
[/PHP]
Similar syntax in Java has failed me, and Google was obstinate (the only definitive answer came from a forum that´s way too 1337 for the likes of me...so I´m not sure I believe it)

Thanks

No. However there are a couple of hacks...

Passing a null value can indicate that a default value should be used.
[PHP]
public void spam(String eggs) {
    if (eggs == null) {
        //Default
        eggs = "tasty"
    } 
    System.out.println(eggs);  
}
[/PHP]

Or method over loading

[PHP]
public void spam(String eggs) {
    System.out.println(eggs);
}

public void spam() {
    System.out.println("tasty");
}
[/PHP]

Personally id use method overloading

---

### Post by wrtpeeps on 2008-11-28
+1 for overloading.

---

### Post by Reiger on 2008-11-28
> **wrtpeeps said:**
> +1 for overloading.

Yup, *especially* if you're writing code others will have to work with later.

---

### Post by fiddler616 on 2008-11-29
Thanks...however, I seem to be doing something wrong.
(Before you start grilling me, the Java I´m learning in school uses some kind of special conceptual library called Karel J Robot--you have different classes of robots, they can run about on a grid, etc. It´s "real Java"--it´s just...weird=
)
 
[PHP]
. . .
public void go(int dist, boolean safe)
{
for(int ii = 1; ii < dist; ii++)
{
    if(safe = true)
    {
        if(frontIsClear()) //No walls in the way of moving
        {
            move();
        }
    }
    else //safe = false
    {
        move();
    }
}
}
 
public void go(int dist) //same as go but with safe defaulted to true
{
    for(int ii = 1; ii < dist; ii++)
    {
        if(frontIsClear())
        {
            move();
        }
    }
}
[/PHP]
 
Whenever I call go, safe is *always* true, even if I explicitly set it to false.
 
 
(Before I get trouble from someone:
A)Yes, this is a school course.
B)No, this is not homework--I've gotten immensely bored with repeating instructions, and took it upon myself to read ahead, do research, and make a "master class" which has commonly used methods that I'm tired of defining (it being Thanksgiving Break and all...) They're still working out how nested ifs work--Python, you've saved me :)
)

---

### Post by bobrocks on 2008-11-29
> **fiddler616 said:**
> Thanks...however, I seem to be doing something wrong.
(Before you start grilling me, the Java I´m learning in school uses some kind of special conceptual library called Karel J Robot--you have different classes of robots, they can run about on a grid, etc. It´s "real Java"--it´s just...weird=
)
 
[PHP]
. . .
public void go(int dist, boolean safe)
{
for(int ii = 1; ii < dist; ii++)
{
    if(safe = true)
    {
        if(frontIsClear()) //No walls in the way of moving
        {
            move();
        }
    }
    else //safe = false
    {
        move();
    }
}
}
 
public void go(int dist) //same as go but with safe defaulted to true
{
    for(int ii = 1; ii < dist; ii++)
    {
        if(frontIsClear())
        {
            move();
        }
    }
}
[/PHP]
 
Whenever I call go, safe is *always* true, even if I explicitly set it to false.
 
 
(Before I get trouble from someone:
A)Yes, this is a school course.
B)No, this is not homework--I've gotten immensely bored with repeating instructions, and took it upon myself to read ahead, do research, and make a "master class" which has commonly used methods that I'm tired of defining (it being Thanksgiving Break and all...) They're still working out how nested ifs work--Python, you've saved me :)
)

If I understand your intentions correctly here is some steps to get you going

1) you don't want to be duplicating code.  Try something more like

[PHP]
. . .
public void go(int dist, boolean safe)
{
for(int ii = 1; ii < dist; ii++)
{
    if(safe = true)
    {
        if(frontIsClear()) //No walls in the way of moving
        {
            move();
        }
    }
    else //safe = false
    {
        move();
    }
}
}
 
public void go(int dist) //same as go but with safe defaulted to true
{
    go(dist, true);
}
[/PHP]

2) hint - == is not the same as =.

---

### Post by fiddler616 on 2008-11-29
> **bobrocks said:**
> If I understand your intentions correctly here is some steps to get you going
 
1) you don't want to be duplicating code. Try something more like
 2) hint - == is not the same as =.
 1)That´s a good idea, thanks!
2)Aach, you´re right. I used to do this in Python, and got over it, and now it´s back. Argh. More proof that *BASIC (TI-BASIC in my case) ruins your brain.
 
Solved, awesome!

---

### Post by drubin on 2008-11-29
> **tinny said:**
> No. However there are a couple of hacks...

Passing a null value can indicate that a default value should be used.
[PHP]
public void spam(String eggs) {
    if (eggs == null) {
        //Default
        eggs = "tasty"
    } 
    System.out.println(eggs);  
}
[/PHP]

Or method over loading

[PHP]
public void spam(String eggs) {
    System.out.println(eggs);
}

public void spam() {
    System.out.println("tasty");
}
[/PHP]

Personally id use method overloading

+1 for overloading. (this is how Java does default params) :)

Personally I prefer this approach as it is more default params then duplicating code and having the same thing in each method. 

[PHP]
public void spam(String eggs) {
    System.out.println(eggs);
}

public void spam() {
    spam("tasty");
}
[/PHP]

---

