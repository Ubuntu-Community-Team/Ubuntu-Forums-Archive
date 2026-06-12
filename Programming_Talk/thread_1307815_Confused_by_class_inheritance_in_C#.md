---
title: "Confused by class inheritance in C#"
date: 2009-10-31
forum: Programming Talk
---

### Post by liquidbee on 2009-10-31
The idea is pretty simple:
[LIST=1]
[*]create a fruit and set it's color/size
[*]add chemicals which would change the fruit color
[/LIST]

What exactly do I need to add to be able to access [COLOR="blue"]Apple[/COLOR] objects from [COLOR="Blue"]Chemicals[/COLOR] class ?

```
namespace Fruit
{

    class Apple
    {
        string color;
        int size;

        public Apple(string icolor, int isize)
        {
            color = icolor;
            size = isize;
        }
    }

    public class Chemicals
    {
        public Chemicals()
        {
            
        }
    }

}
```

---

### Post by PaulM1985 on 2009-10-31
The idea of inheritance is that a class that inherits from another class is a specific type of thing it is inheriting from.  So if Class_B inherits from Class_A, Class_B is a more specific type of Class_A.  So in your example, it would be more likely that you would create a class Apple, which would inherit from the class Fruit, because Apple would be a specialised type of fruit.

What you need in your example is that Chemical should have a reference to a Fruit object.

So somewhere in your Chemical class you would have:

Fruit aFruit = new Fruit("Red", 1);

If you wanted to change the colour of this fruit, in the Fruit class you would need a method:
void setColour(String newColour)

which would change the colour of the fruit.  In your Chemical class, to change the colour of the fruit, aFruit, which has already been defined, you would call the setColour method of Fruit, doing:

aFruit.setColour("Blue");

Hope this clears up the inheritance issue for you and you understand what is needed to solve the problem.

Paul

---

### Post by liquidbee on 2009-10-31
I see. Thanks for an explanation - finally I got it running the way I wanted.

---

### Post by Frak on 2009-10-31
You could also use colon inheritance. By using a colon next to your class definition, it inherits from the specified class/interface.

```
public class Chemicals : Apple
{
    ...
}
```

If I'm misconstruing the question, tell me now. Paul's answer, though, sounds more "correct".

EDIT
Just a quick note, using colon inheritance won't inherit private data, so be aware.

---

### Post by liquidbee on 2009-10-31
> **Frak said:**
> You could also use colon inheritance. By using a colon next to your class definition, it inherits from the specified class/interface.

```
public class Chemicals : Apple
{
    ...
}
```

If I'm misconstruing the question, tell me now. Paul's answer, though, sounds more "correct".

EDIT
Just a quick note, using colon inheritance won't inherit private data, so be aware.

Honestly, the whole problem was just my imagination. I thought [COLOR="Blue"]namespace[/COLOR] works pretty much in the same way as classes do ( as an example, UbuntuForums class would have 2 subclasses - users and moderators ).

---

