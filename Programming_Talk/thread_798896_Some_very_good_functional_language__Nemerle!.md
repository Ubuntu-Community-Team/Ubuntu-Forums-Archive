---
title: "Some very good functional language : Nemerle!"
date: 2008-05-18
forum: Programming Talk
---

### Post by sakabato on 2008-05-18
Hello ,

 I've encountered [nemerle]("http://nemerle.org/Main_Page") a long time ago and it was quite matured since then. As a developer I was looking for more power and nemerle gave me what I want. It is definitely not a newbie language but is very very powerful. It is basically unification of C# and OCALM with enhanced macro support. Here are some features:

* **Cross platform: ** Nermele is an open source CLR based language, it runs on mono / linux and .net platforms (please don't post about mono patent FUD in this thread).

* ** C#/Java like syntax (statically typed):**  The syntax is similar to C#.

* ** Functional **: Nemerle is functional.


* ** Macros :** This is what makes nemerle very powerful. Basically it allows you to invent your own keywords. The language normally does not have constructs as if. But instead they are created as macros.

Here is how or a reverse loop implemented basically:

```

macro ReverseFor (i, begin, body) 
syntax ("ford", "(", i, ";", begin, ")", body)
{
  <[ for ($i = $begin; $i >= 0; $i--) $body ]>
}

```

then you can use this :

```

ford (i ; n) print (i);

```

You see! "ford" is on our own keyword.


* ** Type inference with Generics **: Unlike C#/Java, this syntax works:
```

def d = Dictionary ();
d.Add ("Ala", 7);
foreach (s in args) {
  ...
}

```


* ** Builtin Design By Contract **:
```

public Substring (startIdx : int) : string 
  requires startIdx >= 0 
  { ... }


```

Here we say startIdx must be =>0 . Contracts are builtin!

```

public Length () : int
  ensures value >= 0


```

This ensures the property returns >= 0 values otherwise an exception is thrown (we can also customize that exception).


```

Cass Vector [T]
invariant position >= 0 
  private mutable position : int = 0;
....


```

Here, we say for the life time of this class , position can't be <0.


* ** Speed** : Ironically nemerle compiler is written with nemerle itself which is CLR language. Because of mono Runtime JIT'ing  the speed is somewhat close to (average about 80% levels) to native C code.

* ** Interop ** : nemerle can interop with any CLR/mono language. You can use windows.net libraries or mono libraries, you can intermix your code with C# or you can reuse your nemerle libraries from C#

For more details go to here: [http://nemerle.org/Features]("http://nemerle.org/Features")

---

### Post by CptPicard on 2008-05-18
> **sakabato said:**
> 
* ** C#/Java like syntax (statically typed):**  The syntax is similar to C#.

Is this a plus somehow? :confused:

Why not use Common Lisp instead, it's got everything already :)

---

### Post by sakabato on 2008-05-18
> **CptPicard said:**
> Is this a plus somehow? :confused:

Why not use Common Lisp instead, it's got everything already :)

Static typing can be annoying at times. However nemerle overcome this by its late binding feature [http://nemerle.org/Late_Binding_Macro]("http://nemerle.org/Late_Binding_Macro")

---

### Post by slavik on 2008-05-18
is it me or does it have assignment operators? I thought that functional languages aren't supposed to have those.

---

### Post by LaRoza on 2008-05-18
> **slavik said:**
> is it me or does it have assignment operators? I thought that functional languages aren't supposed to have those.

Functional languages can have assignment operators. 

A pure functional language like Haskell has them, so they must be allowed. However, Haskell doesn't allow "variables" to change once assigned.

A big thing for functional languages is that a function always returns the same value with the same arguments.

```

raw_input("Python isn't purely functional")

```

---

### Post by slavik on 2008-05-18
but in Haskel, they aren't variables, they are symbols.

x=5 #means that wherever you see 'x', you can replace it with '5'
y=func() #means that wherever you see 'y', you can replace it with 'func()'

---

### Post by sakabato on 2008-05-18
> **LaRoza said:**
> Functional languages can have assignment operators. 

A pure functional language like Haskell has them, so they must be allowed. However, Haskell doesn't allow "variables" to change once assigned.

A big thing for functional languages is that a function always returns the same value with the same arguments.

```

raw_input("Python isn't purely functional")

```

in nemerle all variables are readonly by default. however you can make the mutable by explicitly calling mutable

def x = 5 ; // x cannot be modified in future
mutable y = 3; // y can be modified

---

### Post by LaRoza on 2008-05-18
ford is from the wikipedia article: [http://en.wikipedia.org/wiki/Nemerle](http://en.wikipedia.org/wiki/Nemerle)

It is an interesting concept but does this language have a future? Haskell, Lisp, Python, Java, C#, etc are all competitors in the field. What does Nemerle bring that makes it special? Also, functional languages for .NET also include F#. And there is L# (Lisp for .NET).

Frankly, this language seems to have no future.

---

### Post by Wybiral on 2008-05-18
The macro system is interesting, but IMO, is still a joke compared to something like Common Lisp though. And it will never be as strong as lisps for one good reason: code is not a unified data structure. This crappy C-style code will never be capable of the expressibility that a language like Lisp has.

TBH, it looks like a glorified C# to me...

---

### Post by sakabato on 2008-05-19
> **Wybiral said:**
> The macro system is interesting, but IMO, is still a joke compared to something like Common Lisp though. And it will never be as strong as lisps for one good reason: code is not a unified data structure. This crappy C-style code will never be capable of the expressibility that a language like Lisp has.

TBH, it looks like a glorified C# to me...

With one more thing: The  macros in nemerle is very different than C macros. The macros in nemerle allows you to play with the Abstract Syntax Tree. So you can insert, remove, replace "nodes (must be sematically meaningful)" rather than doing plain text erasure. But it is also different than Lisp macros imho

For example 
```

[Accessor]
private  _myField:int;

```

when compiler sees built in Accessor macro attribute (which is built in but you are free to implement yours) it will go through reflection find this field and attach a property to it by directly inserting a node to abstract syntax tree.And after compiler done , the macro would be expanded to
```

private  _myField:int;

public MyField:int{
   get { return this._myField;}
}

```
This is very powerful. While writing your macros if you fail to inject valid code, you will get a compilation time error, rather than a runtime error.

just my 2 cents

---

### Post by CptPicard on 2008-05-19
> **sakabato said:**
> The macros in nemerle allows you to play with the Abstract Syntax Tree. So you can insert, remove, replace "nodes (must be sematically meaningful)" rather than doing plain text erasure. But it is also different than Lisp macros imho

Well, Wyb's objection still stands I think... it still does not have a uniform syntax stucture that is also a uniform recursive data structure. You can manipulate AST all you want but it still isn't as general as Lisp's macros that can really do anything.

It is also a *good* thing that Lisp macros can also manipulate literally any list and not just valid code -- this way you can write those famous mini-languages within Lisp. Look at the Lisp loop macro for example ... it's not valid plain Lisp, but because the macro compiles it to valid plain Lisp, it extends the language with new syntax. :)

---

