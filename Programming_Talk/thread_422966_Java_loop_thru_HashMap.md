---
title: "Java: loop thru HashMap"
date: 2007-04-25
forum: Programming Talk
---

### Post by pmasiar on 2007-04-25
Java gurus, 

I have HashMap nodeIDs (key and value are String). I need to extract keys as Array/list/ArrayList/whatewer

I need to translate to Java Python snippet "ids = nodeIDs.keys()", or to make space for some processing later: 

```

ids = []
for kk in nodeIDs.keys():
    ids.append(kk)
```

I was gogling and strugling and found [this](http://forum.java.sun.com/thread.jspa?threadID=540338&messageID=2619891) and [this](http://www.dynamicobjects.com/d2r/archives/003033.html) and many more examples, even more confusing :-(

```

for (Iterator iter = noteIDs.entrySet().iterator(); iter.hasNext();) {
	Map.Entry entry = (Map.Entry) iter.next();
	String key = (String)entry.getKey();
	//String value = (String)entry.getValue();	
}
```

Is this the bast what Java can do, or it's just me being spoiled by Python? Create iterator, and cast  to Map.Entry, just to get the darn key?

God, I just love Python!

---

### Post by Todd Bealmear on 2007-04-25
This is some example code I threw together real fast - it uses my own Map ADT, but it should be easy enough to adapt it to HashMap.
```
	  private ArrayList<String> list = new ArrayList<String>();
	  public ArrayList<String> createKeyList() {
		  if (root == null)
			  return null;
		  else {
			 concatKeys(root);
			 return list;
		  }
	  }
	  
	  private void concatKeys(MapNode t) {
		  if (t != null) {
			  concatKeys(t.left);
			  list.add(t.key);
			  concatKeys(t.right);
		  }
	  }
```

---

### Post by Ragazzo on 2007-04-25
Maybe this helps

```

import java.util.*;

public class Test {
	public static void main(String[] args) {
		Map<String,String> map = new HashMap<String,String>();
		map.put("first", "one");
		map.put("second", "two");
		map.put("third", "three");
		for(String s : map.keySet()) {
			System.out.println(s);
		}
	}
}

```

---

### Post by joseelsegundo on 2007-04-25
You could try something like:

```


HashMap<String, String> myHashMap = new HashMap<String,String>();
....
ArrayList<String> keysAsList = new ArrayList<String>(myHashMap.keySet());


```

I think the keysAsList object will contain the object references from the Set object returned by keySet(), so if you need to alter the values you'll probably want to do a ```
 ArrayList<String> myCopyOfKeysAsList = (ArrayList<String>) keysAsList.clone(); 
```

---

### Post by joseelsegundo on 2007-04-25
Oops.  the ArrayList.clone() only makes a shallow copy which does not make copies of the actual elements in the List.  So if you want to change the elements without affecting the keys of your HashMap, you would need to loop through and copy the elements.

---

### Post by samjh on 2007-04-25
Example pulled from the SDN forums:

```
Iterator myVeryOwnIterator = HashMap.keySet().iterator();
while(myVeryOwnIterator.hasNext()) {
    System.out.println(myVeryOwnIterator.next());
}
```

See here: [http://forum.java.sun.com/thread.jspa?threadID=663576&messageID=3887990](http://forum.java.sun.com/thread.jspa?threadID=663576&messageID=3887990)

---

