---
title: "[SOLVED] Java Null Pointer Exception"
date: 2008-11-30
forum: Programming Talk
---

### Post by ghandi69_ on 2008-11-30
Hey Guys... Just getting back into some Java after a few weeks break, and I'm making some silly mistakes I believe.

Anyway, I am trying to create an array of objects called "Words", described in Words.java.  The array is described in wordList.java.

Anyway, my Words.java looks like below..

```
public class Words {
	
	public String s;
	private int frequency;
	
	public Words(){
		
		s = "---";
		frequency = 0;
		
	}
```

with the appropriate getter and setter methods following.  In the class WordList, I try to create an array by the following...

```

public class wordList {
	
	//private data members, described above
	private Words hashtable[];
	private int M;
	private int totalwords = 0;
	private LinkedList<String> templist; 
	private String replacements[][];
	private int totalreplacements = 0;

	
	/**
	 * Constructor for class wordList, initializes hashtable to size M, 
	 * and initializes replacement matrix and link list of strings.
	 * @param size
	 */
	public wordList(int size){
		
		M = size;
		hashtable = new Words[M];
		for(int i=0;i<hashtable.length;i++){
			System.out.println(hashtable[i].getS());
			
		}
		
		
	}


```

But I get a Null pointer exception when running the first line in the for loop...

Any ideas?

---

### Post by dwhitney67 on 2008-11-30
Where is getS() implemented?

---

### Post by ghandi69_ on 2008-11-30
> **dwhitney67 said:**
> Where is getS() implemented?

Sorry..I didn't include all of Words.java to save space in the initial post,here it is.. 

```
public class Words {
	
	public String s;
	private int frequency = 0;
	
	
	public void increment(){
		
		frequency++;
		
	}

	public String getS() {
		return s;
	}

	public void setS(String s) {
		this.s = s;
	}

	public int getFrequency() {
		return frequency;
	}

	public void setFrequency(int frequency) {
		this.frequency = frequency;
	}
	
	

}
```

---

### Post by dwhitney67 on 2008-11-30
It appears that the following is missing from your code:
```

    ...

    hashtable = new Words[M];

    for (int i = 0; i < M; ++i) {
      hashtable[i] = new Words();
    }

    ...

```
Now, why it is needed is strange.  I almost expected (as you have) that the allocation of the array of Words would have sufficed.  But this is Java (and not C++).

---

### Post by ghandi69_ on 2008-11-30
> **dwhitney67 said:**
> It appears that the following is missing from your code:
```

    ...

    hashtable = new Words[M];

    for (int i = 0; i < M; ++i) {
      hashtable[i] = new Words();
    }

    ...

```
Now, why it is needed is strange.  I almost expected (as you have) that the allocation of the array of Words would have sufficed.  But this is Java (and not C++).

Thanks dwhitney,

Yeah.. I came to the same conclusion as you did, and after inserting that It was able to run without any errors.  I was as surprised by this as well, and have been looking through my past code to find an example where initializing like that was not needed, but I appear to have false memories of doing that (probably from c++, as you mentioned)

Anyway, thanks again!

---

### Post by DougB1958 on 2008-11-30
> **dwhitney67 said:**
> It appears that the following is missing from your code:
```

    ...

    hashtable = new Words[M];

    for (int i = 0; i < M; ++i) {
      hashtable[i] = new Words();
    }

    ...

```
Now, why it is needed is strange.  I almost expected (as you have) that the allocation of the array of Words would have sufficed.  But this is Java (and not C++).

I think Java initializes object references (i.e., the elements of hashtable) to null. That would explain why you need your own explicit initializations in order to avoid null pointer references....

---

### Post by drubin on 2008-11-30
> **ghandi69_ said:**
> 
But I get a Null pointer exception when running the first line in the for loop...

Best bet next time would be to post the null pointer error it displays. It normally contains the line number that the error accorded on.

---

