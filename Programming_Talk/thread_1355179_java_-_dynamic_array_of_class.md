---
title: "java - dynamic array of class"
date: 2009-12-14
forum: Programming Talk
---

### Post by LKjell on 2009-12-14
Hi I am trying to refresh my java memories but finds it very annoying to not the flexibility of C.

I have a linked list where each node has a name. In that list I want to have an array of the list which contain its friends. In C I would have done something like this.

```
struct list
{
	char *name;
	list *next;
	list **friends;
};
```

In Java I have 

```
class list
{
	String name;
	list next;
	list friends[];

	list(String str)
	{
		name = str;
	}
}
```

The question is how to append more data to friends? I know I can allocate a fixed size but I want to have it dynamically.

```
list root = list("Mary");
root.friends = new list[5];
```

---

### Post by Reiger on 2009-12-14
You are building a C-style data structure in Java??

In Java you'd write:

```

import java.util.List;

public class Node<T> {
  
  protected List<T> friends;
  public Node() {
    // init friends here; e.g. friends = new ArrayList<T>(); 
  }
  
  public void addFriend(T friend) {
    friends.add(friend);
  }
}

```

Elsewhere your LinkedList is a simple: 

```

import java.util.LinkedList;
/* more code, omitted */

LinkedList<Node> nodeList = new LinkedList<Node>();

```

---

### Post by dwhitney67 on 2009-12-14
Consider using a Vector<>.

```

import java.util.Vector;

class List
{
   public String name;
   public List   next;
   Vector<List>  friends;

   ...
}

```

For more info on the Java Vector, read [here]("http://java.sun.com/javase/6/docs/api/java/util/Vector.html").

Use the add() method to insert new 'Link' entries.

---

### Post by LKjell on 2009-12-14
@Reiger you code is too complex I did not follow. Might be some Java fancy.

@dwhitney67 thanks for the suggestion. It looks like what I needed. My other solution was to make a linked list of friends too. But that would be too redundant

---

### Post by japju on 2009-12-14
No, you should avoid using a Vector. All access to Vector is synchronised which unnecessarily slows down single threaded applications. For multi-threaded applications, its synchronisation model is rarely the most appropriate one. Mostly, it will work but inefficiently.

Instead use List interface and choose whatever concrete implementations suits the purpose best.

The literal, close translation to Java of the C example is probably:


```
// imports omitted

class ListNode
{
   private String name;
   // You can substitute ArrayList by any class implementing List interface
   private List<ListNode> friends = new ArrayList<ListNode> ();

   ListNode(String myName)
   {
      name = myName;
   }

   List<ListNode> getFriends()
   {
      return friends;
   }

   String getName()
   {
      return name;
   }

}

LinkedList<ListNode> strangeList = new LinkedList<ListNode>();
```

You really want to read up on Java collections. A gentle introduction can be found at [http://java.sun.com/docs/books/tutorial/collections/index.html](http://java.sun.com/docs/books/tutorial/collections/index.html).

Some examples how you'd use the above data structure:
```

ListNode first = new ListNode("FIRST");

strangeList.add(first);

ListNode friendOfFirst = new ListNode("A FRIEND OF FIRST");

first.getFriends.add(friendOfFirst);

ListNode anotherFriendOfFirst = new ListNode("ANOTHER FRIEND OF FIRST");

first.getFriends.add(anotherFriendOfFirst);

ListNode secondNode = new ListNode("SECOND NODE");
strangeList.add(secondNode);

```

Reiger, sorry somehow missed your answer.... Great minds, alike etc

---

### Post by LKjell on 2009-12-14
I am getting confused now. We have LinkedList, ArrayList and Vector which do almost the same thing ?

---

### Post by Reiger on 2009-12-14
Tutorial on the matter of collections: [http://java.sun.com/docs/books/tutorial/collections/index.html](http://java.sun.com/docs/books/tutorial/collections/index.html)

---

### Post by japju on 2009-12-14
Oh dear... Nothing to be confused about... As mention by me and Reiger, take a look at the tutorial.

LinkedList a class that implements List interface using link list structure as concrete implementation: fast insert/delete from the head and tail of the list but requires space for storing reference to the previous/next node.

ArrayList implements List interface using an array. This means that from time to time it needs to copy the elements from the current array used to a new larger one when the list size grows. Also, adding things to head of list always means moving all existing elements. Benefits: lower space costs as there are no previous/next references to store.

Vector is more or less obsolete. Precedessor to reorganization of the Collections framework and List interface.

You can think of the interface List as abstract data type and the various classes are concrete implementations of that. Each implementation has its own performance (space and time) and synchronisation characteristics. Which one is the best depends on what are you actually trying to do in what context. The great think is that if you declare you variables using an interface, the implementations can be changed without changing the code.....

---

### Post by LKjell on 2009-12-15
Here is the code for any interested. The confusing part is well like I said different data structure under one interface. But it is neat to be able to swap LinkedList, ArrayList and Vector without changing the rest of the code much. 

I guess next is to let the compiler decide which one to use depending on if you compile for speed, space or synchronized.  

```
import java.util.*;

class list
{
	private String name;
	private List<list> friends = new LinkedList<list>();

	list(String str)
	{
		name = str;
	}

	List<list> get_friends()
	{
		return friends;
	}

	String get_name()
	{
		return name;
	}
}

class data
{

	static void list_add(String str, List<list> people)
	{
		list node = new list(str);
		people.add(node);
	}

	static boolean friend_exist(String str, list people)
	{
		List<list> node = people.get_friends();
		int size = node.size();
		
		list friends;
		
		for(int i = 0; i < size; i++)
		{
			friends = node.get(i);

			if (str.equals(friends.get_name()))
				return true;
		}

		return false;
	}
	
	static void add_friend(String from, String to, List<list> people)
	{
		int size = people.size();
		
		list name = null;
		list friend = null;
		
		for (int i = 0; i < size; i ++) {
			list node = people.get(i);

			if (to.equals(node.get_name())) {
				name = node;

				if (friend_exist(from, name))
					return;
			}
			
			if (from.equals(node.get_name()))
				friend = node;

		}
			
		if (friend != null && name != null)
			name.get_friends().add(friend);
	}
	
	public static void main(String[] args) 
	{	
		List<list> people = new ArrayList<list>();

		list_add("Mary", people);
		list_add("Jonh", people);
		list_add("Erica", people);
		list_add("Victoria", people);
		list_add("Phil", people);

		add_friend("Jonh", "Mary", people);
		add_friend("Victoria", "Mary", people);
		add_friend("Phil", "Mary", people);
		add_friend("Phil", "Mary", people);
		add_friend("Phil", "Mary", people);

		list node = people.get(0);		
		List<list> friends = node.get_friends();

		int size = friends.size();
		System.out.println("Friends of " + node.get_name());
		
		for(int i = 0; i < size; i++) {
			node = friends.get(i);
			System.out.println(node.get_name());
		}

		System.out.println("************");
		size = people.size();
		System.out.println("List of people");
		
		for(int i = 0; i < size; i++) {
			node = people.get(i);
			System.out.println(node.get_name());
		}

	}
}
```

---

### Post by dwhitney67 on 2009-12-15
Your final solution, regardless of the use of Java' Linked/Array/List, is not very OO.

Avoid using static methods whenever possible, as shown in your 'data' class.  Consider augmenting your 'list' class to offer the appropriate accessor methods to add new friends.

I would also suggest that you rename your class 'list' to something more appropriate that describes what it really is; something like "FriendsList", "BlackBook", "HitList", etc.

And lastly, and perhaps too late for this suggestion, you should have considered using a Map in lieu of perhaps the Linked List.  The Linked List, as you have demonstrated, requires that you potentially search every entry to find a matching name when implementing add_friend() and friend_exist().  This could be potentially be very slow and impact your application if it were used on a larger scale (eg. consider Facebook).

Anyhow, good luck with your endeavor.

---

### Post by LKjell on 2009-12-15
I modified the code using HashMap. Though everything seems to be random.
Another thing I found out is that I can use keys as the names. Thus I do not need private String name in class person.

I need the static keyword otherwise I get java.lang.NoSuchMethodError: main

```
import java.util.*;

class people
{

	static void list_add(String str, Map<String, person> people)
	{
		person node = new person(str);
		people.put(str, node);
	}

	static void add_friend(String friend, String name, Map<String, person> people)
	{
		people.get(name).set_friends(friend, people);
	}
	
	public static void main(String[] args)
	{
		Map<String, person> people = new HashMap<String, person>();

		list_add("Mary", people);
		list_add("Jonh", people);
		list_add("Terry", people);
		list_add("Gina", people);

		add_friend("Mary", "Terry", people);

		Set<String> keys = people.keySet();
		
		Iterator<String> it = keys.iterator();
		while(it.hasNext())
			System.out.println(people.get(it.next()).get_name());

		/*But the keys are the same as names 
		 *therefore I can just iterate the keys instead...
		 */
		
	}
}

class person
{
	private String name;
	private Map<String, person> friends = new HashMap<String, person>();

	person(String str)
	{
		name = str;
	}

	Map<String, person> get_friends()
	{
		return friends;
	}

	String get_name()
	{
		return name;
	}

	void set_friends(String str, Map<String, person> people)
	{
		if (!friends.containsKey(str) && people.containsKey(str))
			friends.put(str, people.get(str));
	}
}
```

---

### Post by Can+~ on 2009-12-15
> **LKjell said:**
> I modified the code using HashMap. Though everything seems to be random.

Well of course, plain hashes never guarantee order (although, depending on the input, it may end up being sorted).

Hashes are another data structure that offer constant access time (O(1)), because they run a key through a function that points to the memory direction (simply as an offset from a base).

> Another thing I found out is that I can use keys as the names. Thus I do not need private String name in class person.

I would still keep the [FONT="Courier New"]String name[/FONT] inside the "person" class, mostly because, if you pass the object around, and later want to access the name, you'll have to kick around the name of the key too. Also, because it's more UML-friendly.

> I need the static keyword otherwise I get java.lang.NoSuchMethodError: main

That's... common on Java. The main method must be static, it doesn't make sense to instantiate the main class to access the main method.

---

### Post by dwhitney67 on 2009-12-15
If I may... this is what I was hinting at earlier with regards to using non-static methods; notice how *only* the main() function is declared static.

```

import java.util.ArrayList;
import java.util.HashMap;

class Person
{
   private String            name;
   private ArrayList<Person> friends = new ArrayList<Person>();

   public Person(String name)
   {
      this.name = name;
   }

   public void addFriend(Person f)
   {
      friends.add(f);
   }

   // ...
}

public class People
{
   private HashMap<String, Person> people = new HashMap<String, Person>();

   public People()
   {
   }

   public void addPerson(String name)
   {
      people.put(name, new Person(name));
   }

   public Person getPerson(String name)
   {
      return people.get(name);
   }

   public void addFriend(String name, Person person)
   {
      people.get(name).addFriend(person);
   }

   public static void main(String[] args)
   {
      People peeps = new People();

      peeps.addPerson("Batman");
      peeps.addPerson("Robin");

      peeps.getPerson("Batman").addFriend(peeps.getPerson("Robin"));
      peeps.getPerson("Robin").addFriend(peeps.getPerson("Batman"));

      // or

      peeps.addFriend("Batman", peeps.getPerson("Robin"));
      peeps.addFriend("Robin",  peeps.getPerson("Batman"));
   }
}

```
P.S.  I follow Java programming conventions... class names begin with an uppercase letter; method and variable names employ the 'humpback' style.

P.S. #2  The addFriend() method of the People class could stand to have some error checking code placed within it.

---

### Post by LKjell on 2009-12-15
I see. Every class is a big chunk of objects which you can reuse. OOP is kinda unfamiliar at first. Are there any way to get the pointer operator, -> , in Java? 
Too many dots make it hard to read.

---

### Post by CptPicard on 2009-12-15
> **LKjell said:**
> Are there any way to get the pointer operator, -> , in Java? 


What do you need the member-of-pointed-to-struct operator for in a language that does not have pointers? Java doesn't expose the underlying memory architecture in any direct way, being garbage-collected and all.

---

### Post by LKjell on 2009-12-16
An alias to dots. Even though there are no pointers.

---

### Post by CptPicard on 2009-12-16
> **LKjell said:**
> An alias to dots. Even though there are no pointers.

Hmm.. I do not understand why you would want to just rename the dot... it is about as simple an operator as it gets.

---

### Post by LKjell on 2009-12-16
I want dots for methods while class variables with the pointer operator.

I always pass pointer to struct in C. And if I take a struct in a function I will then just have a pointer in the function to get the syntax.

---

### Post by CptPicard on 2009-12-16
> **LKjell said:**
> I want dots for methods while class variables with the pointer operator.

Well, that's not how Java is defined :) Inside the class itself, its own methods, static or not, are recognized simply by their name; outside of the class, you have to specify either an instance or a class name.

> 
I always pass pointer to struct in C. And if I take a struct in a function I will then just have a pointer in the function to get the syntax.

I'm not sure I understand how this behaves much different?

---

### Post by nvteighen on 2009-12-16
> **LKjell said:**
> I want dots for methods while class variables with the pointer operator.

I always pass pointer to struct in C. And if I take a struct in a function I will then just have a pointer in the function to get the syntax.

Ugh... learn Common Lisp and use reader-macros... Common Lisp is the only language I know of that would allow you to change its entire syntax.

---

### Post by Redache on 2009-12-17
> I want dots for methods while class variables with the pointer operator.

I always pass pointer to struct in C. And if I take a struct in a function I will then just have a pointer in the function to get the syntax

Java is a garbage collected language, meaning you don't have to reference and dump memory, it does it for you.

Coming to Java expecting it to behave like C is a direction that will likely lead to you hating Java for not being C.

I recommend reading up on Object Orientation and it should all become clear.

---

