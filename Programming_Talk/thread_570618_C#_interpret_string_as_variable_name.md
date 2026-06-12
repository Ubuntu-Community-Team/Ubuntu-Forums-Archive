---
title: "C# interpret string as variable name"
date: 2007-10-08
forum: Programming Talk
---

### Post by ironfistchamp on 2007-10-08
Hey all,

New language for me this C#, have to use it for my course at Uni. Anyway I have come to a situation where the perfect solution would be if I could interpret a string as a variable name.

Example

```


int myInteger = 10;
string varName = "myInteger";

int returnFunc(string varName)
{
    return <whatever variable has a name the same as the value in varName>
}

```

Any ideas? It would be great if this is actually possible.

Thanks

Ironfistchamp

---

### Post by ryno519 on 2007-10-08
I'm not sure where this kind of approach would ever be considered a perfect solution, but it is possible. I quickly coded up the following example of how to do something like this.

```

using System;

namespace Test
{
	class MainClass
	{
		public int myInteger = 7;
		
		public void Test()
		{
                       // Grabs the integer by the variables name
			int test = (int)this.GetType().GetField("myInteger").GetValue(this);
			
			Console.WriteLine(test);
		}
		
		public static void Main(string[] args)
		{
			MainClass mc = new MainClass();
			
			mc.Test();
		}
	}
}

```

---

### Post by aks44 on 2007-10-08
> **ironfistchamp said:**
> I have come to a situation where the perfect solution would be if I could interpret a string as a variable name.

Sorry, I don't know C# so I have no idea how to do it (if it's even possible), but may I suggest that you have a design problem here?


More info about your real goal may help to sort it out... ;)

---

### Post by ryno519 on 2007-10-08
> **aks44 said:**
> Sorry, I don't know C# so I have no idea how to do it (if it's even possible), but may I suggest that you have a design problem here?


More info about your real goal may help to sort it out... ;)

I would have to agree here, I can't see a situation where it would be preferable to access a variable in this way. If you tell us what you are trying to do we might be able to recommend you a better way to solve the problem at hand. :)

---

### Post by CptPicard on 2007-10-08
IMO the solution you're really looking for is a key-value map, if you really need to do something like this... does C#'s API come with hashmaps or treemaps like Java's?

---

### Post by skeeterbug on 2007-10-08
> **CptPicard said:**
> IMO the solution you're really looking for is a key-value map, if you really need to do something like this... does C#'s API come with hashmaps or treemaps like Java's?

```

using System.Collections.Generic;

public class SomeClass
{
private Dictionary<string, int> list = new Dictionary<string, int>();

        public int GetValue(string varName)
        {
            return list[varName];
        }

        public void SetValue(string varName, int value)
        {
            list.Add( varName, value );
        }
}

```

---

### Post by ironfistchamp on 2007-10-08
Ah it's OK now. Talked with a programmer friend of mine and he sorted me right out. Thanks for the replies.

Ironfistchamp

---

