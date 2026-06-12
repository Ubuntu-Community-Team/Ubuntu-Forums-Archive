---
title: "Arraay.Find and Array.FindAll methods in C#"
date: 2008-05-19
forum: Programming Talk
---

### Post by true_friend on 2008-05-19
Hi 
I am a c# learner. studied arrays and a bit practiced as well. A little question about above two methods of C# arrays. Array.Find and Array.FindAll. Can someone provide an example so I can understand them. I want to use them to get a word's frequency but do not know how to increment an integer if it finds. And there is no guarantee of no "overcounting" i mean a word searched before and the next call search same once again in Array (if there are more then once occurances would it be fine to use Arrays?). I haven't learnt generics and collections yet but little study told me that they are more useful in this regard (I mean to find a given word's frequency in an object say string array which is made after splitting a string). 
Anyhows I'll be very thankful if someone can show me examples to use Array.Find and Array.FindAll.
Regards

---

### Post by sakabato on 2008-05-19
```

public static void Main () {

  int[] numbers = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };        

  int[] odds = Array.FindAll<int>(numbers, IsOdd);
}

private static bool IsOdd(int number)
 {

      return ((number % 2) != 0);

}
        
```

---

### Post by true_friend on 2008-05-20
Thanks for your reply. I've found a way to get word freqeuncy by Length property of the resulting array of the FindAll method. There is a problem i couldn't pass string to FindAll method, the compiler give error. Can you tell me where i am wrong? below is the code I've written on the basis of this example.
Regard
> using System;
namespace arr
{
class arr
{
	public static void Main () {
	string tofind = "is";
	string sentence = "This is a Book";
	string[] word = sentence.Split( );
	string[] find = Array.FindAll<string>(word, tofind);
  int i = find.Length;
  Console.WriteLine(i);
  Console.ReadLine();
}
}
}


---

### Post by clasificado on 2008-05-20
> **true_friend said:**
> string tofind = "is";

The ToFind object must be a static function (really a predicate) that do the comparison returning a boolean result.

take a look to the skabato's example

clasificado

---

### Post by dwhitney67 on 2008-05-20
> **clasificado said:**
> The ToFind object must be a static function (really a predicate) that do the comparison returning a boolean result.

take a look to the skabato's example

clasificado

I'm using Ubuntu and the 'mcs' compiler to compile Csharp apps.  When I tried compiling the code below, I got the following error:
```

$ mcs Odd.cs 
Odd.cs(7,35): error CS1002: Expecting `;'
Compilation failed: 1 error(s), 0 warnings
```

What's causing this??

[PHP]class Odd
{ 
  public static void Main ()
  { 
    int[] numbers = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };  

    int[] odds = Array.FindAll<int>( numbers, IsOdd );
  } 

  private static bool IsOdd( int number ) 
  { 
    return ( (number % 2) != 0 );
  } 
}[/PHP]

---

### Post by true_friend on 2008-05-20
clasificado: Thanks. I take a loot at it. I am actually a learner. Do not have very deep knowlege yet. Learned Arrays couple of days ago and this method I found last day but didn't know how to implement it. Its arguments are new to me I mean that static boolean method. 
dwhitney67: It(Array.FindAll) is new in C# and available in C# 2 (2005). You'll have to use gmcs the mono compiler for C# 2. 
Regards

---

### Post by dwhitney67 on 2008-05-20
Using your helpful hint, I got the following to work:
[PHP]
using System;

namespace Find
{
  class Find
  {
    public static string searchString;

    private static bool FindWord( string word )
    {
      return word == Find.searchString;
    }

    public static void Main ()
    {
      string sentence = "This is a Book";

      string[] word = sentence.Split();

      Find.searchString = "is";

      string[] find = Array.FindAll<string>( word, FindWord );

      int i = find.Length;

      Console.WriteLine("Number of instances of the word '" + Find.searchString + "' is: " + i);
    }
  }
}[/PHP]

---

### Post by sakabato on 2008-05-21
Don't use **mcs**, use **gmcs**. It's C# 3.0 compiler!

---

