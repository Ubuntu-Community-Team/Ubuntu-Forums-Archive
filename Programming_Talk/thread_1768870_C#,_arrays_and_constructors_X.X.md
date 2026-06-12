---
title: "C#, arrays and constructors X.X"
date: 2011-05-27
forum: Programming Talk
---

### Post by Drenriza on 2011-05-27
If i have an array and a constructor in the same class, how do i get the object that the constructor creates and add it to my array?

So far i have something like this
```
public class LogicMgr
    {
        Project p = new Project();

        static Array[] _arrayProject = new Array[5];//oprettelse af array

        //Array constructor start
        public LogicMgr (string t, string n)
        {
            p.title = t;
            p.name = n;
        }
        //Array constructor ends

        //udskriv arrayets indhold ud
        public Array UdskrivArray()
        {
            return _arrayProject;
        }

        //Put i array
        public Array TilfojTilArray()
        {
            for(int i = 0; i <= _arrayProject.Length -1; i++)
            {
                _arrayProject[i] = p;//hvorfor er dette ikke = p?!?!?!?! hvad er det SÅ!?????
            }
        }
}
```

Im trying to use the p, and add that to my array but aparently something is going wrong.
```
cannot convert source type namespace.project to target type source.array
```
anyone who can help me?

---

### Post by doas777 on 2011-05-27
your code for adding to the array is fine. just a simple LVal = RVal thing (arr[idx] = new Project(); or arr[idx] = p; ). 
the problem is your array declaration line. in C# you don;t declare arrays as "arrays" but as arrays of a specfic type.
```

static Array[] _arrayProject = new Array[5];//oprettelse af array

```should be 
```
static Project[] _arrayProject = new Project[5]();//oprettelse af array

``` just add [] to the end of any type name to make it an array of that type.

system.Array is an object model class designed for inheritance, not a concrete class that your should use in your code, unless you are creating your own special type of array. 

[http://msdn.microsoft.com/en-us/library/aa288453%28v=vs.71%29.aspx]("http://msdn.microsoft.com/en-us/library/aa288453%28v=vs.71%29.aspx")

---

### Post by Drenriza on 2011-05-27
uhm even tho it goes against everything i have been told X.X i tried your way but i get an error 

```
methode, delegate or event is expected
```

---

### Post by PaulM1985 on 2011-05-27
Is this on the line where _arrayProject is defined?  I think that it should be:
new Project[5];
rather than
new Project[5]();

Paul

---

### Post by doas777 on 2011-05-27
> **PaulM1985 said:**
> Is this on the line where _arrayProject is defined?  I think that it should be:
new Project[5];
rather than
new Project[5]();

Paul
yep, you are right. mea culpa. I was thinking of 'new Arraylists<T>()'

anyway op, drop the parens that paul mentioned. 

here is a quick code sample to send you down the right path:
```

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

namespace testThing
{
    class Program
    {
        static void Main(string[] args)
        {
            arrtest a = new arrtest();
        }
    }

    public class thing //inspired by Dr Suess.
    {
        public string thing1 = "thing1";
        public string thing2 = "thing2";

        public thing(string iThing1, string iThing2)
        {
            thing1 = iThing1;
            thing2 = iThing2;
        }

        public string ToString()
        {
            return thing1 + " and " + thing2;
        }
    }

    public class arrtest
    {

        public thing[] things = new thing[3];

        public arrtest()
        {
            for (int i = 0; i < things.Length; i++)
            {
                things[i] = new thing("thing" + i, "thing" + (i + 1));
            }

            foreach (thing t in things)
                System.Diagnostics.Debug.WriteLine(t.ToString());
        }
    }
}

```

---

