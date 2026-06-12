---
title: "Help with writhing java equals function for objects"
date: 2009-03-22
forum: Programming Talk
---

### Post by rob1101 on 2009-03-22
I need some help here, I am scratching my head over this one. I have a driver file that needs to compare two objects it calls a function I have to write the function in the class
[I]
obj1.equals(obj2)[/I]

How am I supposed to write this function? Each object has two variables but how would i compare the objects if only one of them is passed into the function?

---

### Post by Tomosaur on 2009-03-22
> **rob1101 said:**
> I need some help here, I am scratching my head over this one. I have a driver file that needs to compare two objects it calls a function I have to write the function in the class
[I]
obj1.equals(obj2)[/I]

How am I supposed to write this function? Each object has two variables but how would i compare the objects if only one of them is passed into the function?

Well if the variables you need to check in object2 are available either publicly or through get methods, then the solution pretty much writes itself.

```

bool equal = false;
if(myVariable == obj2.myVariable){
  equal = true;
}

```

---

### Post by rushmobius on 2009-03-22
Here is a basic example of creating a custom equals method.

```

public boolean equals(Object obj) {
        if (obj == null) return false;

        if (!this.getClass().equals(obj.getClass())) return false;

        MyObj mobj = (MyObj)obj;

        if (this.x.equals(mobj.x) &&
            this.y.equals(mobj.y)) {
            return true;
        }

        return false;
    }


```

---

### Post by simeon87 on 2009-03-22
Eclipse can automatically generate the equals method, here's an example:

```

public boolean equals(Object obj) {
		if (this == obj)
			return true;
		if (obj == null)
			return false;
		if (getClass() != obj.getClass())
			return false;
		final Example other = (Example) obj;
		if (var != other.var)
			return false;
		return true;
	}

```

---

### Post by rob1101 on 2009-03-22
Thanks for all the help guys I have got it working now :)

How can eclipse generate custom equals methods? That sounds like it could be useful.

---

### Post by simeon87 on 2009-03-22
> **rob1101 said:**
> How can eclipse generate custom equals methods? That sounds like it could be useful.

It's in the Source menu. then one of the generate options.

---

### Post by pbrockway2 on 2009-03-22
It's often reccommended to override hashCode() as well when overriding equals(). [http://www.javaworld.com/javaworld/jw-06-2004/jw-0614-equals.html]("http://www.javaworld.com/javaworld/jw-06-2004/jw-0614-equals.html")

(equal objects must have the same hash code)

---

### Post by HotCupOfJava on 2009-03-22
Keep in mind that equals() methods are intended to show if you have a reference to the SAME object, not if the objects are clones. You may already know this and that may be what you are wanting to test for - if so, I apologize for insulting your intelligence. 

If you are wanting to test to see if you have two separate objects that are identical, you need the compareTo() method. If it is a custom object you have created, you will need for it to implement the Comparable interface in order to do this. Or, you can write a custom Comparator to use for comparing them to each other. Check out the API documentation for the details.

---

