---
title: "How to get the value of a string to name a variable in JAVA2??"
date: 2008-06-14
forum: Programming Talk
---

### Post by theodorekon on 2008-06-14
Hi,
I'm writing a program in Java and I have a creator which creates objects and I want to name an object with the value of a string variable. For example if I had a creator which creates objects of the kind human and I also have a string variable called name with the value "theodore" I want to create an object named theodore. The command creatorName name = new creatorName() does not work because the compiler says, as expected, that the variable name is already in use. If I wrote a script I would use the dollar symbol ($name) in order to get the value of the variable and not the variable itself. Is there something similar in Java2??

Thanks in advance

---

### Post by bruce89 on 2008-06-14
I'm not sure what the question is asking, but I think you want to create objects with data. For instance, here's a [FONT="Monospace"]Human[/FONT] class with a constructor which takes a [FONT="Monospace"]String[/FONT] for the name.

```

public class Human
{
	String name;

	public Human(String name)
	{
		this.name = name;
	}

	public String getName()
	{
		return name;
	}

	public static void main(String[] args)
	{
		Human molly = new Human("Molly");
		System.out.println("There is a human called " + molly.getName());
	}
}

```

By the way, Molly is my rabbit's name.

---

### Post by theodorekon on 2008-06-14
Thanks but that's not exactly what I need. I don't want to create a field for the object human in which I will insert the name of the human. I want the object itself to be named with the string value of the variable name. Let me give you an example:

Let's say I have a constructor named human which creates objects of the kind human which contain fields such as height, weight etc. 
I want to create 100 objects of the kind human with 100 different names. Instead of:
```

Human theodore = new human();
Human mary = new human();
Human molly = new human:
.
.
.
etc
```
I want to create the matrix [100]names which has 100 string variables corresponding to 100 names and then creating a loop:
```

for (i=0;i<100;i++) {
Human a[i] = new human()
}
```

---

### Post by issih on 2008-06-14
Not at all sure that is achievable, nor can I really see why you'd do it.....Just use a name field on human and an accessor method. Make it immutable if you really want so it can't be messed about with. Anything you want to do such as sort the array can be done just as easily on the name field.

If for some reason you really don't want a name field (I really can't think why I'm afraid) then have a map and map the names to the appropriate object.

Best I can do...sorry its not what you want, but I don't think what you want is particularly sensible, but then I'm not particularly sensible so I shouldn't criticise :)

---

### Post by descendency on 2008-06-14
[PHP]
String[] names = generateNames();  // generates an Array of names 

foreach(String s in names)
{
  Human a[i] = s;
}[/PHP]

I really don't understand what else you are asking.

edit: Then the variable you want to call for the name would simply be a[i].name or if you over-ride the ToString() method, you could use it to return the name.

---

### Post by theodorekon on 2008-06-14
Thanks again!! I forgot to tell you the reason why I want this so maybe you have some other more sensible (:):)) suggestion.
 My program takes a .txt file as an input, in which I have columns with all the necessary field values. So my program creates as many objects as the number of lines of the .txt input file and each column represents a field (age,height,weight etc). I read the .txt file in the program and put the values first in a string matrix and then from there I take them in order to create the objects and give them the corresponding field values. After that I want to make various calculations with the field values of the objects and the only way to refer to each object is by its position in the string matrix.
In simple words I do not know from the beginning how many objects will be created so I cannot name them from the beginning, they have to be created and named after the input .txt file is given.
Any suggestions??

---

### Post by descendency on 2008-06-14
you mean if you have a human named "Molly" you want to be able to refer to them as humanArray["Molly"]?

if it is, I think [this]("http://java.sun.com/javase/6/docs/api/java/util/Map.html") is what you are looking for.

edit: They are called associative arrays. (Java calls them maps)

---

### Post by theodorekon on 2008-06-14
Let's say that I have a .txt input file with ten rows which would mean that the program would create ten objects. How can I name those objects?? I could have created ten objects in my program from the beginning and then use the input just to give them their field values but then what would happen if I gave an input with 100 rows. 
I mean that the usual way to create an object is:
```

creatorName objectName = new creatorName()

``` 
But what happens if you don't know how many objects to create until after the input is given. Then somehow I should be able to do the following:
```

for (int i=0;i<inputMatrix.length;i++) {
  creatorName inputMatrix[i] = new creatorName()
}

```
But of course that does not work.

PS Don't confuse the human name with the object name. My problem is not how to name humans (which I could of course do via a field) but how to name objects.

---

### Post by NormR2 on 2008-06-14
If you were able to "name" an object dynamically at runtime, how would you then reference/use that object in your code?  
You want to have a one-to-one correspondence of the "names" read from a text file with the newly created objects. A class like hashtable could be used to do this. 

Or something like this:```

creatorName newVals[] = new creatorName[inputMatrix.length];

for (int i=0;i<inputMatrix.length;i++) {
  creatorName newVals[i] = new creatorName()
}
```

---

### Post by issih on 2008-06-14
If you are just trying to work out how to allocate an arbitrary number of objects without knowing how many you are going to create, then you need something like this:

```

List aList = new ArrayList();

for (int i = 0; i<10; i++)
{
    Human aHuman = new Human(<Constructor Arguments>);
    aList.add(aHuman);
}

```

Because java knows if an object is being referred to by something else in memory or not (garbage collection) the objects created in the loop and assigned to variable aHuman, are never thrown away because they are pointed to by the list object.

This code can create an arbitrary number of Human objects by simply changing the loop to one iterating to a variable max number n.

Your objects are now held by the list, and you do not need a direct mapping to a variable name, you just access them dynamically with a command like:

Human aHuman = aList.get(i);

where i represents the index of the specific human object you want in the list.

Using this you will have a list of human objects you can then iterate through to do anything else you want to (assign field values, perform calculations, whatever.

You do not HAVE to have an object mapped to a variable, as long as something still loaded in memory refers to it, it will not be unloaded.

---

### Post by Habbit on 2008-06-14
AFAIK, Java does not implement such kind of dynamic symbol-tree approaches. Most probably, your best option is to use any implementation of the Map<K,V> interface like this:
```

// Assuming you have the names in the "names" String array:
java.util.Map<String, Human> people = new java.util.HashMap<String, Human> ();
for (String curName : names) {
    Human curObj = new Human (curName);
    // Fill in other properties
    people.put (curName, curObj);
}
// Then you can refer to each individual like this:
Human aperson = people.get ("Molly");

```
The problem with this implementation is that the name is stored twice, by map and by the Human class, and thus you could store a Human named "Molly" under the "Arthur" key of the map. There is a class in the Microsoft .NET Framework 2.0+ named KeyedCollection<K,V> that addresses precisely this need: a map whose values are self-keyed.

---

### Post by theodorekon on 2008-06-14
Thanks issih!! I 'll try that, it seems a good idea. 
Cheers

---

### Post by issih on 2008-06-14
You are welcome, we all have to learn at some point :)

---

### Post by theodorekon on 2008-06-14
> AFAIK, Java does not implement such kind of dynamic symbol-tree approaches. Most probably, your best option is to use any implementation of the Map<K,V> interface like this:
Code:

// Assuming you have the names in the "names" String array:
java.util.Map<String, Human> people = new java.util.HashMap<String, Human> ();
for (String curName : names) {
    Human curObj = new Human (curName);
    // Fill in other properties
    people.put (curName, curObj);
}
// Then you can refer to each individual like this:
Human aperson = people.get ("Molly");

The problem with this implementation is that the name is stored twice, by map and by the Human class, and thus you could store a Human named "Molly" under the "Arthur" key of the map. There is a class in the Microsoft .NET Framework 2.0+ named KeyedCollection<K,V> that addresses precisely this need: a map whose values are self-keyed.
__________________
I'm not sure I got that completely but I 'll try it. Thanks anyway!!

---

### Post by issih on 2008-06-14
A "map" is basically a collection of objects, but as well as being able to access the members of that collection by index e.g. get(0), each item can be mapped to a specific key. The object mapped to this key can then be retrived from the collection using the key instead of the index.

The key can usually be a variety of things, but strings are common. 

```
//First create a map in which the keys are strings, and the stored objects are Humans  
java.util.Map<String, Human> aMap = new java.util.HashMap<String, Human> ();

// a loop for assigning names stored in curNames to the newly created Human objects.
for (String curName : names) {
    //create a Human object
    Human curObj = new Human ();
    // Add this Human to the Map Collection keyed against the string curName
    aMap.put (curName, curObj);
}

//You can then retrieve the Human object keyed by a specific name (e.g. 'Molly') 

Human aperson = people.get ("Molly");

```

---

### Post by theodorekon on 2008-06-15
> **issih said:**
> If you are just trying to work out how to allocate an arbitrary number of objects without knowing how many you are going to create, then you need something like this:

```

List aList = new ArrayList();

for (int i = 0; i<10; i++)
{
    Human aHuman = new Human(<Constructor Arguments>);
    aList.add(aHuman);
}

```

Because java knows if an object is being referred to by something else in memory or not (garbage collection) the objects created in the loop and assigned to variable aHuman, are never thrown away because they are pointed to by the list object.

This code can create an arbitrary number of Human objects by simply changing the loop to one iterating to a variable max number n.

Your objects are now held by the list, and you do not need a direct mapping to a variable name, you just access them dynamically with a command like:

Human aHuman = aList.get(i);

where i represents the index of the specific human object you want in the list.

Using this you will have a list of human objects you can then iterate through to do anything else you want to (assign field values, perform calculations, whatever.

You do not HAVE to have an object mapped to a variable, as long as something still loaded in memory refers to it, it will not be unloaded.


I took your advice and created a List with the objects in the loop but then I haven't found a way to access the fields of each object. For example the command:
```
System.out.println("Human heigth is "+aList.get(0).height);
```
won't work..

Then I tried to assign each object of the List to a new object of the kind Human like this:
```
Human aHuman = aList.get(i);

```

When I tried to compile that I got the following message:

> ScanXan.java:52: incompatible types
found   : java.lang.Object
required: Human
                Human aHuman = aList.get(0);


Any suggestions on how to access the fields of the objects that are contained in the List??

---

### Post by NormR2 on 2008-06-15
Do you know what the compiler error message means?
What type does the get() method return?
Is it Human? If not, the compiler complains that the types are incompatible.
What you need to do to make the types compatible.
One way is to use type casting: put the required type in () infront of the get() ie = (Human)aList.get()
This will allow the program to compile, but could cause an error at runtime if the type returned by get() is not Human. 
 
A better solution is to use the Hashmap class as suggested above. Then the types are taken care of for you. The definition of the Hashmap defines the two types<K, V> that are passed in the put(K, V) method and the type returned by get. Look at the API doc for Hashmap to see. Coding this way will allow the compiler to check the usages of put() and get() to insure that you use the correct types.

---

### Post by theodorekon on 2008-06-15
> **NormR2 said:**
> Do you know what the compiler error message means?
What type does the get() method return?
Is it Human? If not, the compiler complains that the types are incompatible.
What you need to do to make the types compatible.
One way is to use type casting: put the required type in () infront of the get() ie = (Human)aList.get()
This will allow the program to compile, but could cause an error at runtime if the type returned by get() is not Human. 
 
A better solution is to use the Hashmap class as suggested above. Then the types are taken care of for you. The definition of the Hashmap defines the two types<K, V> that are passed in the put(K, V) method and the type returned by get. Look at the API doc for Hashmap to see. Coding this way will allow the compiler to check the usages of put() and get() to insure that you use the correct types.

I tried the first suggestion and it worked fine. Thanks!!

---

### Post by issih on 2008-06-16
Back when I used java extensively all collections (sets,lists maps,etc) were typed as holding objects (i.e. the base java class from which all others inherit). This was done so that the same collection class could be used to hold any type of object you create.

The result of this is that when the collection returns an object it is typed as an object (because the collection doesn't know what it actually is holding onto).

You then cast the object to whatever you actually put in there:

e.g. Human ahuman = (Human) aList.get(0);

That will work fine.

Having said that, I know that java implemented generics recently, and by the looks of it made at least the map class into one.

With these you actually type your collection as holding a specific type of object, when you instantiate it, so this casting is not necessary.

Sorry for the confusion :)

---

