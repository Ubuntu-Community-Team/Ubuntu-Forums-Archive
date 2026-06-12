---
title: "Java: Handling classes without common interface similarly"
date: 2011-03-31
forum: Programming Talk
---

### Post by worldsayshi on 2011-03-31
Let's say I've written bellow methods to print the names of cats and dogs. Cats and dogs are defined in a separate package that I can not control. They have no common interface for their names. 

```
import animals.Cat;
import animals.Dog;

void printMember(Cat pet){
   print(pet.name);
}

void printMember(Dog pet){
   print(pet.name);
}
```

Is there some way I could merge the two methods to avoid redundancy without having to alter Cat or Dog at their source? Can I apply a common interface or apply abstraction somehow in retrospect?

---

### Post by dwhitney67 on 2011-03-31
How is the member 'name' declared?  Where is it declared?  Do Cat and Dog share a common base-class where perhaps the attribute 'name' is declared?

Also, it would be helpful if you presented proper Java code; we all know (right?) that all methods must be encapsulated within a class.  Yours are not.

Anyhow, check if you have something similar to the following:
```

class Animal
{
   private String name;

   protected Animal(String n)
   {
      name = n;
   }

   public String getName()
   {
      return name;
   }
}

class Cat extends Animal
{
   public Cat()
   {
      super("Cat");
   }
}

class Dog extends Animal
{
   public Dog()
   {
      super("Dog");
   }
}

public class Test
{
   public static void main(String[] args)
   {
      Animal an1 = new Cat();
      Animal an2 = new Dog();

      System.out.println(an1.getName());
      System.out.println(an2.getName());
   }
}

```

---

### Post by worldsayshi on 2011-03-31
Ok, I realise the piece that I posted might not make much sense. It was not my intention to make it complete and buildable anyway. 
I guess I will have to be more specific.

More closely to what I want to achieve: I'm using the visitor pattern to visit subclasses of the Animal superclass. However, it turns out that, say, half of these subclasses has names, and I want to print them out when visiting. For the others I want to do something else. 

So it would make sense to bundle the visitor method for all classes with a 'name' member. 

To understand the example you might need to be familiar with the visitor pattern, which you might be after this overworked example anyway:
```

public class NamePrinter implements Animal.Visitor {
 public visit(Parrot p) {
  System.out.println(p.name);
 }
 public visit(Dog p) {
  System.out.println(p.name);
 }
 public visit(Cat p) {
  System.out.println(p.name);
 }
 public visit(Zebra p) {
  System.out.println("Wild animals doesn't have names!");
 }
 public visit(Pelican p) {
  System.out.println("Wild animals doesn't have names!");
 }

/*...
  etc
  ...
*/

}

```

Usage example:
```

import TheWholeZoo;
import java.util.LinkedList;

class Test{
 public static void main(String[] args){
  Linkedlist<Animal> animals = TheWholeZoo.goGetMeSomeAnimals();
  for (Animal a:animals){
   showMeTheNameOfThatAnimalIfItHasOnePrettyPlease(a);
  }
 }
 public static void showMeTheNameOfThatAnimalIfItHasOnePrettyPlease(Animal a){
  a.accept( new NamePrinter() );
 }
}

```

The Animal class:
```

public abstract class Animal {
 public abstract void accept(Animal.Visitor);
 public interface Visitor {
  public void visit(Parrot p);
  public void visit(Dog p);
  public void visit(Cat p);
  public void visit(Zebra p); 
  public void visit(Pelican p);
 }
}

```

Ah, what the heck, The dog as example:
```

public class Dog extends Animal{
 public String name;
 public Dog(String name){
  this.name=name;
 }
}

```

Zebras:
```

public class Zebra extends Animal{
 int numberOfStripes;
 public Zebra(){
  numberOfStripes=42;
 }
}

```

PS: 
Gah, this became a crazy long example. But I believe it's actually a 'complete' visitor pattern example. Hopefully at least someone will have gotten him/herself a crash course. Maybe I shouldn't expect an actual answer to my original question though. I might turn this into some kind of visitor demo.  :)

No, I won't show you what "TheWholeZoo" looks like. It's a mess. Who put the cats and dogs there anyway?



**THE ACTUAL QUESTION:**
Is there some way that I can accomplish something like this in the visitor implementation: 
(Deviating from established syntax here.)
```

public class NamePrinter implements Animal.Visitor {
 public visit(<Parrot | Dog | Cat>  p) {
  System.out.println(p.name);
 }
 public visit(<Zebra | Pelican> p) {
  System.out.println("Wild animals doesn't have names!");
 }
/*...
  etc
  ...
*/
}

```

I doubt it but maybe there is some workaround/"trick"?

---

### Post by worldsayshi on 2011-03-31
Additionally, I do realize I could use 'instanceof' instead of using the visitor pattern, like so:

Replacing showMeTheNameOfThatAnimalIfItHasOnePrettyPlease method:
```

public static void showMeTheNameOfThatAnimalIfItHasOnePrettyPlease(Animal a){
 if((a instanceof Dog) || (a instanceof Cat) || (a instanceof Parrot) ){
  
  // But what do I write here then??
  // System.out.println(a.name); -- will cause error. I will 
  // have to make a cast, but there is no common interface to 
  // cast to.

 } else if((a instanceof Zebra) || (a instanceof Pelican) ){

  // This works fine though..
  System.out.println("Wild animals doesn't have names!");

 }
}


```

---

### Post by Some Penguin on 2011-03-31
Reflection.

```

import java.lang.reflect.Field;

...

String getNameIfNotNullNotThatYouShouldDirectlyAccessFieldsLikeThisAnywayThatsWhatAccessorsAreFor(Object o) throws SecurityException, IllegalAccessException, IllegalArgumentException {
   try {
       Field nameField = o.getClass().getField("name");
       Object result = nameField.get(o);
       if (result != null) {
          return result.toString();
       } else {
          return null;
       }
   } catch (NoSuchFieldException nsfe) {
      return null;
  }
}

```

Or something evil like that.  *You shouldn't be doing this*; those classes were badly designed if 'name' really needs to be exposed.

---

### Post by Some Penguin on 2011-03-31
Caveat:  getField() will only work if the field is public.

You could also iterate up the class/interface tree and use getDeclaredField() if you're looking for non-public fields.  That's even more of something that generally you shouldn't be doing.

---

### Post by worldsayshi on 2011-04-01
Yea, I can see that the names probably "should" be hidden and that there should be accessors, but it would add even more code to the example so I saved on that. 

Interesting. Reflection I should keep in mind for the future. I can see why it's not a very good practice though. :)

If there is a getName() method for Dogs, Cats and Parrots I can't see any particular reason for your method (accessing "getName" method instead) to be bad though. 

Well... huh, except for the pile of potential exceptions thrown.

---

### Post by Reiger on 2011-04-01
In your example the method signature makes it perfectly plain that some objects are treated differently from others. It is not "visit(Animal a)", it is "visit(Cat p)" or "visit(Dog p)" or any of the other "visit()" methods.

So even if you had common code to extract info based on roundabout reflection you *still* have to deal with each type as if they're mutually incompatible (or at least, their visit() methods are). Which begs the question: why are you doing reflection in the first place? Why do you have that many "visit()" methods anyway?

Either of the two is definitely an indication of lousy design here:
 -- maybe you need all those methods and they must treat each type differently, for whatever reason, and so the repeated p.name (or whatever it is) is far better than reflection. Put common code that operates on equivalent data in separate methods with appropriate arguments, then call that code from within the "visit()" methods where needed.
 -- or maybe that visitor thing is fundamentally broken and it cannot accommodate what you need from it. Maybe "Animals" should have a "visit()" method which does all this work instead, maybe you need additional interfaces to declare more functionality based on Animal type.

---

### Post by 1clue on 2011-04-01
I think it's been said from a Java perspective already, but I can add some comments.

If you have no control of the animal classes, then introspection is your best bet.

If you can use an aspect of some sort (not strictly Java anymore) then you could use a pointcut maybe.  Don't know much about it.

If you find yourself doing this sort of thing frequently, you might want to consider a different language that runs on the JVM, like groovy.  My company used to be a Java shop, now we're doing everything except maintenance of the old stuff in groovy/grails, and we're slowly converting all the Java so it's just grails.

<soapbox>
What you're discussing here is a non-event in groovy, it uses what is called "duck typing" which means if it looks like a duck, acts like a duck and quacks like a duck then it's a duck.  Basically, you make a method call and it checks at runtime to see if that method is there with the proper parameters, and if so it calls it.

Groovy compiles to Java byte code, so with a small amount of effort you can package both together in the same jar/war/whatever.

FWIW groovy is much more compact and easy to understand than Java, and much more maintainable as well.
</soapbox>

---

### Post by Some Penguin on 2011-04-01
> **worldsayshi said:**
> Yea, I can see that the names probably "should" be hidden and that there should be accessors, but it would add even more code to the example so I saved on that. 

Interesting. Reflection I should keep in mind for the future. I can see why it's not a very good practice though. :)

If there is a getName() method for Dogs, Cats and Parrots I can't see any particular reason for your method (accessing "getName" method instead) to be bad though. 

Well... huh, except for the pile of potential exceptions thrown.

If it's a public method that all share but which isn't specified by a single interface, then it's not entirely unreasonable.   It would be preferred to have such a interface (of which there are quite a few in Java, like 'Closeable', 'Iterable' and the like) but if you're given final classes lacking such, reflection is an alternative.   You could also create individual wrappers that contain the offending classes and themselves export an interface, but this doesn't scale well in terms of programming time unless you use reflection to generate the wrappers.

If it's a method you normally wouldn't have access to (private, for instance) than you should question whether you should be using it at all because one of the reasons why it might be private is that it's not guaranteed to always be there or with consistent behavior.

---

### Post by dazman19 on 2011-04-04
ROFL @
String getNameIfNotNullNotThatYouShouldDirectlyAccessFieldsLikeThisAnywayThatsWhatAccessorsAreFor(Object o) throws SecurityException, IllegalAccessException, IllegalArgumentException {
  

HAHA
LOL SO FUNNY

Nah bro just use inheritance, this the first response was the best.

public class lolz extends NameIfNotNullNotThatYouShouldDirectlyAccessFieldsLikeThisAnywayThatsWhatAccessorsAreFor(Object lolz) impliments ShowMeTheNameOfThatAnimalIfItHasOnePrettyPlease throws LolThisIsTheFunniestPostIHaveSeenHereInQuiteAwhile {

---

### Post by cgroza on 2011-04-04
It is best to use inheritance and polymorphism to avoid cases like this.

---

