---
title: "Java class issue"
date: 2012-05-22
forum: Programming Talk
---

### Post by Drenriza on 2012-05-22
Hey guys.

I have a class that i have called ALM, where i store all my arraylists for my program.

I then "connect" to this class when needed to retrieve information from these arraylists.

```
ALM alm = new ALM();
```

My problem is now that i need to "connect" to the ALM class from two different classes.

Class1
```
ALM alm = new ALM();
```

Class2
```
ALM alm = new ALM();
```

But when i do so i clear the information inside the arraylists. So my question is.
How can i "connect" to the ALM class without saying it should be a new object? But just use the existing object.

Hope it makes sense. I'am no Java pro.
Thanks on advance.
Kind regards.

---

### Post by Zugzwang on 2012-05-22
Say, do you have any "static" stuff in your ALM class? If yet, give use some description of what you do in the ALM class to have static fields in it.

If not, you are mixing the concepts of classes and objects. In that case, I suggest starting by reading the Wikipedia article on these for clarification. Maybe this already answers your question.

---

### Post by PaulM1985 on 2012-05-22
It sounds like you are looking for a singleton pattern.

```

public class ALM
{
	private static ALM mInstance;

	public static ALM getInstance()
	{
		if (mInstance == null)
		{
			mInstance = new ALM();
		}

		return mInstance;
	}

	// Rest of your ALM implementation below here
}

```

For more information on a singleton pattern look here: [http://en.wikipedia.org/wiki/Singleton_pattern](http://en.wikipedia.org/wiki/Singleton_pattern)

Although it sounds like odd design if you are creating a class to hold all the ArrayLists for a program.  Shouldn't classes using these ArrayLists have references to them, rather than having one container for things that it doesn't need or use?

Note: My implementation of the singleton is not thread safe, that is something that you can research and learn yourself if you need to :-)

Paul

---

### Post by muteXe on 2012-05-22
yea you're gonna have to use a singleton (yuk imo), or actually pass that first 'alm' object around into other class ctors.

---

### Post by Drenriza on 2012-05-23
Hey guys.

Thanks so far. I will try and read more about singleton pattern.

Kind regards.

---

### Post by PaulM1985 on 2012-05-23
> **muteXe said:**
> yea you're gonna have to use a singleton (yuk imo), or actually pass that first 'alm' object around into other class ctors.

Singletons are alright if they are used appropriately.  For example, in a project I am working on I have a singleton Deck which contains 52 Cards.  Since I always use the same Deck, I can check if Card objects are equal, which is quicker than checking suit and value.

---

### Post by muteXe on 2012-05-23
Agreed, but I've found that one person's 'appropriately' can be a lot different to another persons  :)

---

