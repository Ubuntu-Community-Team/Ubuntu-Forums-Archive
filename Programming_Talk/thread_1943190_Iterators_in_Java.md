---
title: "Iterators in Java"
date: 2012-03-19
forum: Programming Talk
---

### Post by orrymr on 2012-03-19
Hi all

I've recently started using iterators to traverse LinkedLists in java. I've got the following code:
```

       LinkedList <Features> features = new LinkedList();
       //some code

        Iterator it = features.iterator();
        while(it.hasNext()){
            System.out.println(it.next().printFeature());
        }

```

and I'm not sure what's wrong here. printFeature() is a method in the Features class. I thought that the the "it" variable would be a placeholder for each of the elements in my LinkedList. Alas, I cannot call the printFeature() method.

---

### Post by GeneralZod on 2012-03-19
Untested, but you probably want:

```

       LinkedList <Features> features = new LinkedList();
       //some code

        Iterator<Features> it = features.iterator();
        while(it.hasNext()){
            System.out.println(it.next().printFeature());
        }

```

(based on [this](http://docs.oracle.com/javase/1.5.0/docs/guide/language/generics.html).)

Edit:

Actually, you might be able to just do the much cleaner:

```

       LinkedList <Features> features = new LinkedList();
       //some code

       for(Features feature : features) 
       {
            System.out.println(feature.printFeature());
       }


```

---

### Post by r-senior on 2012-03-19
I thought pre Java 7 it would be:

```
LinkedList<Features> features = new LinkedList<Features>()
```

and in Java 7, you get to use the "diamond":

```
LinkedList<Features> features = new LinkedList<>()
```

But what is in the Features class? Is it a feature, or is it a list of features, as the name Features suggests? If it's a class that represents a single feature, the singular works out much nicer:

```
List<Feature> features = new LinkedList<>()
for (Feature feature : features) {
    System.out.println(feature); // Assuming a toString() method
}

```

Are you sure you want a linked list? ArrayList is usually the more better list implementation unless you have good reasons for using a linked list. In any case, programming to the List interface, rather than a specific implementation, is usually a good idea, as shown above.

So many questions for such a small piece of code ;). I'd be interested to see what Features is and what printFeatures() is supposed to do.

---

### Post by KdotJ on 2012-03-19
While I agree with the other responses hat using Java's enhanced for-loop is the better and cleaner option, I still believe it's good to have an understanding of Iterators. Sometimes you may wish to iterate a structure in a certain way, like every other element or in descending order (using a descendingIterator). 

**orrymr**, what is the error you're getting exactly?
I see you're (rightly) using generics to bound the LinkedList to type Features, you should also bound your Iterator to type Features as well, so it knows what types of object it will handle.

Here is an updated snippet to try, with the change highlighted:

```

List<Features> features = new LinkedList<Features>();
//some code

Iterator**<Features>** it = features.iterator();
while(it.hasNext()){
    System.out.println(it.next().printFeature());
}

```

Other things to note:
- The "features" variable is declared to be of type List and not a LinkedList. This gives you much more flexibility like **r-senior** said, you should always do this and declare types to the most abstract level you can.

- I have not used Java 7's diamond notation to instantiate the LinkedList. Java 7 is pretty new and I'm not sure on backwards compatibility, or where you will be using this code.

---

### Post by Alberonn on 2012-03-19
Java 7 does not seem to have any issues with some of the older code. I installed Java 7 for my CS class and i had no issues even though most of the class was using Java 6. Towards the end of my class our instructor was starting to introduce some new Java 7 concepts, but he was still learning the ins and outs as well.

I do know that you need users to have 7 installed to run the new code though. That does not seem to be a huge problem if people keep up on the updates.

---

### Post by orrymr on 2012-03-20
Thank you for the responses. My mistake was that I forgot to specify the generic for my Iterator. ](*,)

I coded ```
 Iterator it = features.iterator(); 
```[FONT=monospace] Instead of [/FONT]```
 Iterator <LinkedList> it = features.iterator(); 
```Strangely I can implement my LinkedList without the use of the diamond:
```
 LinkedList <Features> features = new LinkedList();
```My reason for using the iterator initially was to remove elements from the LinkedList, if they comply with a certain condition. This didn't work with a normal for(int i = 0; i < features.size(); i++) loop, since as you remove an element the list shrinks. 

Now, for printing out my features, I'm doing the following:
```

for (Feature feature : features) {
    feature.printFeature(); //should have just made a toString() method
}

```My Features class was unfortunately poorly named (going to have to change that). It contains *one *feature only (should have called it Feature). The feature is made up of an array of length 8, and 2 int primitives. I don't know when it would be preferable for me to use an ArrayList over a LinkedList, but I've been using LinkedLists for a while and haven't had any problems with them

Also, KdotJ, I'm not sure why I'd want to declare my list as the most abstract type available?

---

### Post by PaulM1985 on 2012-03-20
By declaring it as a list instead of a linked list, if you wanted to change the type in the future, you would only have to change the initialisation of the variable.

This is useful if you are planning on returning the feature list or passing it into a function as an argument.  When you do these things, the function is expecting a type.  If you specify the type is LinkedList, you have to change all these references from LinkedList to ArrayList if you decide that an ArrayList is better.  If you keep everything to be List, you only need to worry about changing the initialisation of the list.

Paul

---

### Post by r-senior on 2012-03-20
> **orrymr said:**
> I don't know when it would be preferable for me to use an ArrayList over a LinkedList, but I've been using LinkedLists for a while and haven't had any problems with them
An ArrayList is backed by an array (which usually has more elements than the list to allow for some expansion). A LinkedList is a series of objects where each has an associated pointer to the previous and next item in the list.

Sequential iteration and random access to an ArrayList is quicker than a LinkedList because it's just indexing an array. A LinkedList has to work through a chain of pointers. Adding or removing elements at the end of the list is also quicker with ArrayList, although there are times when the backing array fills up and needs to be reallocated. This can be reduced by setting the initial capacity of the list with the ArrayList constructor.

LinkedList can outperform ArrayList if there are lots of insertions and deletions other than at the end of the list because all it has to do is manipulate the "previous" and "next" pointers. Adding an element in the middle of an ArrayList results in all the elements in the "tail" being shunted to the right.

The memory usage is also different. With a LinkedList, each element has two pointers associated with it and that creates a fixed overhead (16 bytes per element on a 64-bit machine). An ArrayList has no overhead for individual elements but there will usually be spare slots at the end of the backing array. These can be trimmed using trimToSize() when your list reaches capacity.

So it depends on your application, but one or the other isn't suited to every case. As a general rule of thumb, I'd tend to use LinkedList if there was lots of random updating, but ArrayLists most of the time.

For a standalone or small application where there's plenty of memory and CPU available, it doesn't make that much difference in the whole scheme of things but it's a good habit to think about it and to use List to make a switch easier.

---

### Post by KdotJ on 2012-03-22
> **orrymr said:**
> Also, KdotJ, I'm not sure why I'd want to declare my list as the most abstract type available?

Just to add weight to what others have said, it's all about how implementation may differ. It can be confusing to understand why, I'll try give you just one reason that this is good practice. There are, of course, many other reasons.

So let us keep with your example of using LinkedLists as the type. Lets say you have a method somewhere where the method header looks like this: 

```
public void processFeatures(LinkedList<Features> featureList) {
    // do some stuff
}

```

Now, lets say somewhere else (may be a different class of whatever) that we make an ArrayList of features...

```
ArrayList<Features> features = new ArrayList<Features>();
features.add(new Features(...)); // add a feature
// ...add some more...
// ... do some sorting...
// ...do whatever to it.
```

And now we want to process the list of features with our method we defined earlier... we cannot simply call:

```
processFeatures(features);
```

because the method is expecting a LinkedList of Features... but we only have an ArrayList instead. Oh dear...


However, if we have declared the method to be:
```
public void processFeatures(**List<Features>** featureList) {
    // do some stuff
}

```

and then in our other code we had intialised the list as:
```
**List<Features>** features = new ArrayList<Features>();
``` 

then because the type is defined as a List<> instead, we can correctly pass this variable to the method and it will work. We can now pass any type of List to this method and it will work... such as ArrayList, LinkedList, Stack, Vector, RoleList etc.

I hope that makes sense as an example!

---

