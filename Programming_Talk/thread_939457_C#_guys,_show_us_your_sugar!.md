---
title: "C# guys, show us your sugar!"
date: 2008-10-05
forum: Programming Talk
---

### Post by tinny on 2008-10-05
Im hoping that there are some good C# guys out there that can help me with this thread. Basically I want to demonstrate two things, C# is different from Java (its actually better) and C# has learnt something from dynamic languages.

This is not an ignorant “I hate M$” thread. This an informative thread that aims to dispel some of the common misconceptions about C# and also a good opportunity for you C# guys to show off (please do!!!).

Now, I can start this off but because I have been somewhat removed from the C# dev world im going to need some help.

C# basically used to be the same as Java back when I was developing with it (Version 1 of the language spec). But since I developed with it there have been 2 further spec updates that I think have yielded some nice syntax sugar for the language.

Some of the most notable for me are...

**Type Inference:**
var list = new List<string>();

**Automatic properties:**
This is a great time saver, no more being a monkey and writing getters and setters code.

**Object initializers:**
Person p = new Person { Name="tinny" }; 

**Collection initializers:**
MyList list = new MyList { 1, 2 }; 

**Anonymous types:**
Hack together a type on the fly
var x = new { Name = "tinny" } 

Im sure this is just the tip of the iceberg, I know for a fact that im not the only one wanting to learn more about the best parts of C#.

So, C# guys show us your sugar!

---

### Post by Quikee on 2008-10-06
> **tinny said:**
> 
**Object initializers:**
Person p = new Person { Name="tinny" }; 

You can do something very similar in Java.

[PHP]Person p = new Person() {{
   this.name = "tinny";
   this.age = 19;
}};[/PHP]

Means that this also can be done:

[PHP]List list = new ArrayList() {{
   this.add("first");
   this.add("second");
}};[/PHP]

It's a hack but... ;)


Things supernice in C# are delegates and anonymous delegates (example from wikipedia):

[PHP]public void Foo(object parameter) {
    // ...
 
    ThreadPool.QueueUserWorkItem(delegate
    {
        // anonymous delegates have full access to local variables of the enclosing method
        if (parameter == ...)
        { 
            // ... 
        }
 
        // ...
    });
}[/PHP]

extesion methods (example from wikipedia):
[PHP]public static class IntExtensions
{
    public static void PrintPlusOne(this int x) { Console.WriteLine(x + 1); }
}
 
int foo = 0;
foo.PrintPlusOne();
[/PHP]

python like iterators, generators(example from wikipedia):
[PHP]public static IEnumerable<int> GetEven(IEnumerable<int> numbers)
{
    foreach (int i in numbers)
    {
        if (i % 2 == 0) yield return i;
    }
}[/PHP]
and generics without erasure.

Edit:
Oh.. and I forgot one very nice thing - operator overloading!

---

### Post by davidryder on 2008-10-06
In regards to C# being better than JAVA: Do you write C# applications for linux?

---

### Post by tinny on 2008-10-06
> **davidryder said:**
> In regards to C# being better than JAVA: Do you write C# applications for linux?

I know what you are trying to get at.

The OP mentioned the C# language, not .Net / Mono (mono is a .Net port for linux ;) ) vs Java platform. The Java platform is another story...

</offtopic>

---

### Post by tinny on 2008-10-06
> **Quikee said:**
> 
Oh.. and I forgot one very nice thing - operator overloading!

[http://www.csharphelp.com/archives/archive135.html](http://www.csharphelp.com/archives/archive135.html)

Cool, I must say I am a fan!


C# Closures

[http://srtsolutions.com/blogs/billwagner/archive/2008/01/22/looking-inside-c-closures.aspx](http://srtsolutions.com/blogs/billwagner/archive/2008/01/22/looking-inside-c-closures.aspx)


Closures are coming in Java 7, I cant believe it has taken that long to get them! I am constantly left begging for Closures, I dont really like the anonymous inner class approach (the way you do it in Java right now) and tend just to live without pretend Closures in Java (smells up the code IMO).

---

### Post by Quikee on 2008-10-06
> **tinny said:**
> 
C# Closures

[http://srtsolutions.com/blogs/billwagner/archive/2008/01/22/looking-inside-c-closures.aspx](http://srtsolutions.com/blogs/billwagner/archive/2008/01/22/looking-inside-c-closures.aspx)


Closures are coming in Java 7, I cant believe it has taken that long to get them! I am constantly left begging for Closures, I dont really like the anonymous inner class approach (the way you do it in Java right now) and tend just to live without pretend Closures in Java (smells up the code IMO).

Yes closures are also supernice - but if Java would have a "simpler" syntax to instantiate anonymous classes would already be a lot nicer. Most of the syntactic sugar that is normally solved with closures can be solved with anonymous classes.

---

### Post by true_friend on 2008-10-06
Great thread, I'd like to read more things about C#, and it will increase my knowlege as a C# beginner.

---

### Post by jimi_hendrix on 2008-10-06
i learned to program in C# but stopped due to lack of tutorials and books for game programming

i still think its a good language and has better error handling (or maybe i just do it wrong...) then java

---

### Post by Kadrus on 2008-10-06
> i learned to program in C# but stopped due to lack of tutorials and books for game programming
Disagreed.
[Books from Amazon related to C# game development.]("http://www.amazon.com/Beginning-C-Game-Programming-Development/dp/1592005179")
[Google->tutorials]("http://http://www.google.com/search?q=C%23+game+programming+tutorial&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a")
That's not a reason to stop/start learning a language in my opinion.

---

### Post by CptPicard on 2008-10-06
> **Quikee said:**
> Most of the syntactic sugar that is normally solved with closures can be solved with anonymous classes.

The anonymous inner class approach in Java is seriously limited though by the weird "final" requirement for the "closure member variables". Writing a loop around an anonymous inner class with some loop counter inside a final wrapper, for example, because really ugly really quickly :)

That said, I am so spoiled by languages that do have closures that my Java is full of instantiations of my Callback<T> and is probably really hard to read for someone who isn't used to the style :)

---

### Post by skeeterbug on 2008-10-06
Someone already brought up delegates. But here is another example.

```

private delegate void Test(string output);

private void UseDelegate()
{
    Test t = new Test(TheTest);
    t("Testing delegates.");
}

private void TheTest(string output)
{
    Console.WriteLine(output);
}

```

You can also write explicit/implicit converters for boxing/unboxing your classes. I wrote plain C# objects for passing to webservices because our ORM generates heavy entity classes.

```

public static explicit operator User(UserEntity entity)
{
    return new User(entity.UserId , entity.UserName , entity.Password , entity.FirstName , entity.LastName , entity.Disabled , entity.Email , entity.JobTitle , entity.CanSign , entity.WorksFor , entity.Keyword , entity.PrivateKey , entity.PublicKey , entity.CreatedOn , entity.ModifiedOn , entity.PasswordModifiedOn , entity.ReadAgreement , entity.IsHideHealthSummary );
}
```

This allows me to fetch the UserEntity from my ORM, and transform it to a plain object and send it via web services.

```

// Fetch
UserEntity user = new UserEntity();
user.FetchUsingPK(1);

User simple = (User)user;

```

Tracing support in the framework is very powerful as well. You can specify trace switches that can be easily configured via your app or web.config. See my open source payment processor library: [http://code.google.com/p/payment-processor/](http://code.google.com/p/payment-processor/)

Enabling tracing is as easy as adding the switch.

```

<system.diagnostics>
    <switches>
        <add name="PaymentProcess" value="4"/>
    </switches>
</system.diagnostics>

```

You can use the debugger output or add a textwriter listener to send the output to. 

```

<trace autoflush="true" indentsize="4">
    <listeners>
        <add name="TextLogListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="C:\Mission3Source\trunk\OnDemand\Web\log\Trace.log"/>
    </listeners>
</trace>

```

You can also extend this and write your own trace listener class, so I could use remoting or web services and monitor my trace output remotely if I wanted to.

Now on to LINQ. Not only can you query a database, but you can query other collection types. 

```

List<string> fruit = new List<string>();
fruit.Add("Apple");
fruit.Add("Orange");
fruit.Add("Banana");

var q = from f in fruit
        where f.StartsWith("A")
        select f;

foreach (var results in q)
{
    Console.WriteLine(results);
}

```

Using the same syntax to query a database and other collections is a huge time saver. Once you are knowledgeable in it you can easily grab data from other data sources using the same technique.

I still do Python/Ruby in my free time because those languages are fun to program in. However, LINQ has really brought out some fun in doing C# again. Plus I use it at work, I might as well enjoy it a little.

---

