---
title: "Java - what can and cannot be done with generics? Add your favourite trick here"
date: 2008-08-21
forum: Programming Talk
---

### Post by dribeas on 2008-08-21
I once was an experienced Java programmer, but when Java 5 came out I stopped that path and went into C++. With time I have learned what can be done with C++ templates, and they **are** powerful.

With time I have never gone back to Java, but each so often I wonder what the real power inside Java generics is. I once believed that it was a nice utility to add type safety from containers, but I wonder what else can be done.

Anyone has experience with generics? What can be done with them? Any code snippets and/or short descriptions, links... will be appreciated.

   David

---

### Post by tinny on 2008-08-21
Wildcards are worth knowing.

[PHP]
		List<?> strs = new ArrayList<String>();
		//TODO add some objects
		for(Object obj : strs){
			//TODO
		}
		
		List<? extends JComponent> comp = new ArrayList<JPanel>();
		//TODO add any JPanel object
		
		List<? super JPanel> comp2 = new ArrayList<JComponent>();
		//TODO add any JComponent object
[/PHP]

Wildcards are useful when you want to take advantage of polymorphism in generic collections

[PHP]
	public void method(List<? extends JComponent> list) {
		//deal with a collection of JComponents
	}
[/PHP]

The above method is only concerned with dealing with JComponents and doesn't care about the specific type.

---

### Post by slavik on 2008-08-21
this is something that C++ templates do as well.

---

### Post by dribeas on 2008-08-21
> **slavik said:**
> this is something that C++ templates do as well.

Well, I strongly believe that Java/.NET generics are far behind the power of C++ templates. What I want to know is how much can be done with Java. 

The thing is that I used to believe that C++ templates were all about defining containers, and I know now how far from the truth I was. I believe that Java generics are about removing unneeded casts from Object, how wrong am I?

Note that Java has super and extends keywords for generic type definitions:

```

public static <T extends Comparable<? super T>> void sort(List<T> list) {...}

```

This means that sort will receive a list of T where some ancestor of T must implement Comparable. Not as complete as C++0x concepts but still it is more expressive than current templates in C++. Now this is solved with docs and compiler errors, where the latter are not always user friendly.

NOTE: My intention is learning the possibilities, not comparing languages. Please, no more language flamewars :)

---

### Post by tinny on 2008-08-21
> 
I believe that Java generics are about removing unneeded casts from Object, how wrong am I?


More or less.

Its about type safety.
[http://www.angelikalanger.com/GenericsFAQ/FAQSections/Fundamentals.html#FAQ004](http://www.angelikalanger.com/GenericsFAQ/FAQSections/Fundamentals.html#FAQ004)

---

