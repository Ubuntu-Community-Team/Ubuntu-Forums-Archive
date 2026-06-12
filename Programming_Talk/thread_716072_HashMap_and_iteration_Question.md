---
title: "HashMap and iteration Question"
date: 2008-03-05
forum: Programming Talk
---

### Post by Sugz on 2008-03-05
OK, so in Java i have created a HashMap as follows

Map<String,Integer> WordList = new HashMap<String, Integer> ();

The string part contains the word and the integer part contains the Frequesncy of that word in a sentence.

Here i am trying to itterate through and...

```

Set entries = WordList.entrySet();
        Iterator it = WordList.keySet().iterator();
            while (it.hasNext())
                {
                    Map.Entry entry = (Map.Entry) it.next();
                    System.out.println(entry.getKey());
                    int temp = (int)entry.getValue();
                    for (int j = 0; j < temp; j++)
                    {
                        System.out.print("*");
                    }
                }
                
```

get and display the word and then next to it, a star chart showing the words frequency. 

My question is this part

```

Map.Entry entry = (Map.Entry) it.next();
                    System.out.println(entry.getKey());
                    int temp = (int)entry.getValue();
                    for (int j = 0; j < temp; j++)

```

I am trying to retrieve the integer value (look above) and use it in the for loop to create a star chart, but i keep on getting allsorts of compiler errors ranging from incompatible types. 

Any help will be greatly appreciated

---

### Post by CptPicard on 2008-03-05
Give the errors as well, but my first thought is that your problem is that you're not parametrizing the Set entrySet and the Map.Entry as well so that they correlate with your HashMap.

In other words, your entryset is of type Set<String,Integer> and your entry is Map.Entry<String,Integer>

I've been spoiled by Eclipse so my wetware type inference engine is rusty, but this is my first 0.02€.

---

### Post by Quikee on 2008-03-05
This example might help you:

[PHP]
Map<String, Integer> map = new HashMap<String, Integer>();
map.put("A", 1);
map.put("B", 2);
		
// iterate keys
for(String key : map.keySet()) {
	System.out.println("Key: " + key + " Value: " + map.get(key));
}

// iterate values
for(Integer value : map.values()) {
	System.out.println("Value:" + value);
}
		
// iterate entries - keys and values
for(Map.Entry<String, Integer> entry : map.entrySet()) {
	System.out.println("Key: " + entry.getKey() + " Value: " + entry.getValue());
}[/PHP]

---

### Post by Timdejager on 2008-03-05
> **Sugz said:**
> OK, so in Java i have created a HashMap as follows

Map<String,Integer> WordList = new HashMap<String, Integer> ();

The string part contains the word and the integer part contains the Frequesncy of that word in a sentence.

Here i am trying to itterate through and...

```

Set entries = WordList.entrySet();
        Iterator it = WordList.keySet().iterator();
            while (it.hasNext())
                {
                    Map.Entry entry = (Map.Entry) it.next();
                    System.out.println(entry.getKey());
                    int temp = (int)entry.getValue();
                    for (int j = 0; j < temp; j++)
                    {
                        System.out.print("*");
                    }
                }
                
```

get and display the word and then next to it, a star chart showing the words frequency. 

My question is this part

```

Map.Entry entry = (Map.Entry) it.next();
                    System.out.println(entry.getKey());
                    int temp = (int)entry.getValue();
                    for (int j = 0; j < temp; j++)

```

I am trying to retrieve the integer value (look above) and use it in the for loop to create a star chart, but i keep on getting allsorts of compiler errors ranging from incompatible types. 

Any help will be greatly appreciated

I believe that there are two things wrong with this code:

int temp = (int)entry.getValue();

This method gives back an object an as you will know the int is a primitive try this :
int temp = (Integer)entry.getValue();

the Object integer can be safely converted to an int by java.

furthermore this line:

Iterator it = WordList.keySet().iterator();
should be:
Iterator it = WordList.entrySet().iterator();

because keyset returns only a keyset of string and entryset returns  an object of type Map.Entry. I ran the code and it compiled without problems

*edit* And paramterize the entryset because its derived from the hashset,this way you will not need to cast explicitly to an Integer either , or dont parameterize the hashset at all.

---

### Post by jespdj on 2008-03-06
Here's an error: You are getting an iterator on the set of keys, but the rest of the code assumes it's iterating over the set of map entries.

This looks strange:
```
Set entries = WordList.entrySet();
Iterator it = WordList.keySet().iterator();
```
It should have been:
```
Set entries = WordList.entrySet();
Iterator it = entries.iterator();
```

---

### Post by Sugz on 2008-03-07
Ah brilliant! thank you very much all of you.. :)

---

