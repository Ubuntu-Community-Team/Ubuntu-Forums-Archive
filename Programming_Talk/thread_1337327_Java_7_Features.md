---
title: "Java 7 Features"
date: 2009-11-25
forum: Programming Talk
---

### Post by Can+~ on 2009-11-25
Seems that Sun is taking a hint from python's syntax:

[PHP]List<String> list = ["item"];
String item = list[0];

Set<String> set = {"item"};

Map<String, Integer> map = {"key" : 1};
int value = map["key"];[/PHP]


From:
[http://code.joejag.com/2009/new-language-features-in-java-7/](http://code.joejag.com/2009/new-language-features-in-java-7/)

---

### Post by Reiger on 2009-11-25
Ehrm are you sure? From that article it looks more like JSON to me; in particular that:
> These collections are immutable..

---

### Post by froggyswamp on 2009-11-25
If they are "immutable" it makes no sense using that. I guess he means something else.

EDIT: Anyway, I hope they won't do the same to Java 7 as they did to JavaFX: they focused (got obsessed) so much on the language itself that they screwed everything else and forgotten (or didn't have time) to include features and actual improvements to the APIs/runtime people have been asking.

---

### Post by Reiger on 2009-11-25
> **froggyswamp said:**
> If they are "immutable" it makes no sense using that. I guess he means something else.

Either it means that the object is automatically final (in case of a Map you can still add stuff) or he means that the object must be a constant much the same like Enum types may contain fields.

In the former case it basically boils down to having a more convenient initializer than:
```

final Map myMap;

static {
  myMap = new HashMap();
  /* insert preset values here */
}

```

At any rate, writing myMap["myKey"] is better than myMap.get("myKey"); for the common case of string keys.

---

### Post by jespdj on 2009-11-26
> **Reiger said:**
> Ehrm are you sure? From that article it looks more like JSON to me; in particular that: ...
He's right, this is one of the proposed new language features for Java 7.

> **froggyswamp said:**
> If they are "immutable" it makes no sense using that. I guess he means something else.
No, he certainly means immutability. Immutability is an important concept, especially when programming in a functional style. Why do you say that ik makes "no sense using that"?

---

### Post by Habbit on 2009-11-26
Many languages are moving in the same direction: C++0x will also have "initializer lists" so that code like this is possible: ```
vector<int> my_ints = { 10, 25, -7, 42 };
map<string, float> class_grades = { {"Jasper Brown", 7.25f}, {"Natalie Santos", 5.5f} };
```
In the last case, the constructor to map<K,V> takes an initializer_list<pair<K,V>>, without the need for even more new syntax.

Btw, immutability need not be a huge problem if the collections created with the new Java syntax can be copied into a normal collection object: ```

List<String> imm_list = ["item"]; // Immutable
List<String> normal_list = new ArrayList<String>(["item"]); // Mutable

```

---

### Post by Reiger on 2009-11-26
> **jespdj said:**
> He's right, this is one of the proposed new language features for Java 7.

That is not what I meant. I meant the combination of that syntax in combination with not being mutable seems more like JSON (a data definition concept) than Python (a syntax/programming concept) to me.

---

### Post by NovaAesa on 2009-11-26
Hmmmm, I'm not liking the idea of initializers like this... It's going to break alot of Java's orthogonality IMHO.

---

### Post by myrtle1908 on 2009-11-26
To quote more from the article ...

```
Here are 7 of the new features that have been completed:

    * Language support for collections
    * Automatic Resource Management
    * Improved Type Inference for Generic Instance Creation (diamond)
    * Underscores in numeric literals
    * **Strings in switch**
    * Binary literals
    * Simplified Varargs Method Invocation
```

Finally Strings in switch.  It may not mean much to many but there are times where I've longed for this ... if only to avoid (the often unavoidable) lengthy if/else-if blocks.

---

