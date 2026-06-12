---
title: "Polymorphism -- &quot;if else&quot; statements considered bad, smelly code"
date: 2008-07-05
forum: Programming Talk
---

### Post by Asham on 2008-07-05
Ok, so we know that **[FONT="Courier New"]if else - else if - else if - else[/FONT]** is a sign of a bad design pattern.

But I wonder how to create objects when reading from the database, such as

```
select product_name, product_type, from product where product_id=5
```

I gather there is need for a factory here?
```
ProductFactory factory = ProductFactory.getInstance();

Product product = factory.createNew(rs.getString("product_type")); //creates new product (abstract class or interface)
```

Now the if-else is encapsulated in the factory. Neat and well.

But whait a minute. Inside the factory method that create objects, how do we know what strain of the product to create?
If we use string as keys for each type we would have to store that information in more than one place -- database and source code. Not so optimal considering type names can change. Id's are less likely to change so maybe that would be a better solution.

How do you normally solve these question marks? Care to provide some pseudo code (if I'm waay out there with my thoughts).

Thanks for reading! :)

/Adam

---

### Post by CptPicard on 2008-07-05
In Java in particular, if you store the class name in the database, you can do something like Class.forName("MyClass").newInstance() (or get the constructors and invoke those if you need something other than default constructor).

In general though and in languages that do not have this sort of runtime reflection support, I don't think you really can avoid the if-elses. The information has to be somewhere. :)

---

### Post by pmasiar on 2008-07-05
> **Asham said:**
> Ok, so we know that **[FONT="Courier New"]if else - else if - else if - else[/FONT]** is a sign of a bad design pattern.

Why so? It obviously depends on the language: in ASM, IFs is all you got. :-)

Also, quite often I'll prefer to deal with 3 if-else than with a factory. One of gurus I know has a rule of thumb: Make generic solution when you do it 4th time. Only then you have enough info collected from special cases that the generalization you design has chance to be future-proof. Chance, not guarantee! :-)

If you do generalizations too soon, you are something Joel Spolsky calls [Architecture Astronauts](http://www.joelonsoftware.com/articles/fog0000000018.html), who use so high abstractions that they run out of oxygen :-)

---

### Post by tinny on 2008-07-05
> **pmasiar said:**
> Why so? It obviously depends on the language: in ASM, IFs is all you got. :-)

Also, quite often I'll prefer to deal with 3 if-else than with a factory. One of gurus I know has a rule of thumb: Make generic solution when you do it 4th time. Only then you have enough info collected from special cases that the generalization you design has chance to be future-proof. Chance, not guarantee! :-)

If you do generalizations too soon, you are something Joel Spolsky calls [Architecture Astronauts](http://www.joelonsoftware.com/articles/fog0000000018.html), who use so high abstractions that they run out of oxygen :-)

I agree, nice post.

Code smells are an interesting topic. Have you heard of the [Rule of three]("http://en.wikipedia.org/wiki/Rule_of_three_(programming)"). Yeah, a different code smell topic but related to Architecture Astronauts.

---

### Post by pmasiar on 2008-07-06
Yup, seems like my guru is little more conservative... or less aggressive in refactoring. :-)

If you want to get [interesting read about patterns in programming](http://c2.com/cgi/wiki?WelcomeVisitors) (not only design patterns:  patterns in application development, all kind of rules of thumb), check "the original wiki" - first wiki by Ward Cunninghamhttp://en.wikipedia.org/wiki/Ward_Cunningham , "pioneer in both design patterns and Extreme Programming" (and you can see web oldtimer with domain name [http://c2.com](http://c2.com)). Since '95 incredible amount of good info was added by many smart people.

Ie: [http://c2.com/cgi/wiki?CodeSmell](http://c2.com/cgi/wiki?CodeSmell)

Enjoy!

---

### Post by Asham on 2008-07-06
> **pmasiar said:**
> Why so? It obviously depends on the language: in ASM, IFs is all you got. :-)
I'm talking about OOP here, I don't think that applies to ASM but I may be misinformed. Was ages ago I played with assembly and even then I only scratched the surface. I found it to be too abstract. But let's not get into ASM here ok. :)


> **pmasiar said:**
> Also, quite often I'll prefer to deal with 3 if-else than with a factory.
I know guys who prefer this too but I don't like it one bit! 
The sooner you refactor if-else if-else's the better. That is my firm opinion. If that makes me an astronaut, so be it. 
I agree with the rule of three so I don't think I'm all about principles. I find them important but don't live or die by them.

Thanks for posting the link to c2.com! Looks like I have something to do the next couple of hours.

---

### Post by Asham on 2008-07-06
**CptPicard**, Class.forName looks interesting. However I'm a little bit reluctant to that strong of a relation between class names and the database. What if we were to refactor the code? I'm not sure I like the risks of the application breaking... names come with semantic meaning, that's why I was contemplating using id's in the factory methos. An id have no semantic meaning and is usually not changed.

Yes, somewhere you need to put those ifelses or switch statements! That's not the issue. :) The interesting thing is how do you best hide them so that you don't need to repeat the if-else-statements in more than one location.

Let's pretend we have an admin interface for handling products. We can remove, create or edit existing products - it's a CRUD application. We also have a web service that gets us products each day. Now we would have at least three locations in the code where product objects are created. Three locations where we, IMO, do not want to use if-else-statements!

---

### Post by Quikee on 2008-07-06
> **Asham said:**
> Let's pretend we have an admin interface for handling products. We can remove, create or edit existing products - it's a CRUD application. We also have a web service that gets us products each day. Now we would have at least three locations in the code where product objects are created. Three locations where we, IMO, do not want to use if-else-statements!

Then make it so that you have it in one place and not three - I don't see a problem here. Use a factory class or a [DAO]("http://en.wikipedia.org/wiki/Data_Access_Object") and you don't need to use if-else statements, you can use a HashMap instead. ;)

---

### Post by tinny on 2008-07-06
> 
CptPicard, Class.forName looks interesting. However I'm a little bit reluctant to that strong of a relation between class names and the database. What if we were to refactor the code?


What about ORM? You have your domain model and database schema defined all in one. If you reactor your model you are refactoring your schema. (Well this is true for any JPA derived scheme,not sure about other spec's)

However migrating your data is another story... :(

---

### Post by Quikee on 2008-07-06
> **tinny said:**
> What about ORM? You have your domain model and database schema defined all in one. If you reactor your model you are refactoring your schema. (Well this is true for any JPA derived scheme,not sure about other spec's)

However migrating your data is another story... :(

You can still choose a model-driven architecture (and I don't mean UML here but a centralized model with its own meta-model specifically tailored for the needs of application) and then code generate and allow to read the model in runtime for generic operations. 

If you use this approach you can have a advantage in migration that the only thing you need to do is a model to model conversion. Because you know how different meta-models constructs for both models map one with each other and you can write a generic code generator for conversion between all "domain objects".

---

### Post by Asham on 2008-07-06
I intend to eliminate them. :)

A factory is one way to make the code cleaner but are there other ways I've overlooked?

---

### Post by dotkam on 2009-05-16
Hey Asham,

    Your concern:

    > If we use string as keys for each type we would have to store that information in more than one place -- database and source code

    Is easily solvable:

    When you insert a row in a PRODUCTS table, use a Java constant file with the 'ProductType' constants. Use the same exact constant file in your Factory when looking for a specific implementation. This way the product types are only maintained in one place - the constant file.

```
Product product = factory.createProduct( rs.getString( "PRODUCT_TYPE" ) );
```

    So here "rs.getString( "PRODUCT_TYPE" )" will equal to one of your 'ProductType' Java Constants. Now inside the Factory you can use a HashMap, that would have 'ProductType' constants as keys, and actual 'Product' implementations as values ( values, of course can be lazily initialized, if it makes sense ). Which makes your factory to be very simple:

```
private HashMap<ProductType,Product> typeAndProductsHashMap;

public static Product createProduct( ProductType ptype ) {
    return typeAndProductsHashMap.get( ptype );
}
```

Let me know if you have any questions,
-- dotkam

*P.S. Only in case you need to have DB constraints, you will need to sync them with constants, which is actually a good thing as it ensures a strong product typing.*

---

### Post by ghostdog74 on 2009-05-16
this is an old thread.

---

