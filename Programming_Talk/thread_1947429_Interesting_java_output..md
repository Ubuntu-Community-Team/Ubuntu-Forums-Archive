---
title: "Interesting java output."
date: 2012-03-26
forum: Programming Talk
---

### Post by Ghostmn on 2012-03-26
Consider the following code. I would imagine that a memory address would be displayed, but instead a string is displayed.

My justification for not knowing the answer is, I don't use java often.

```

public class hello
{
    public static void main(String[] args) {

        College tt = new College("Raiders");
        tt.rah();
        tt.rah();

        System.out.println(tt);

    }

}

class School {

    private String Mascot;

    public School(String m) {

        Mascot = m;

    }
    public void rah() {

        Mascot += "!";

    }
    public String toString() {

        return Mascot;

    }

}

class College extends School {

    public College(String s) {

        super(s);

    }

}

```

---

### Post by satsujinka on 2012-03-26
System.out.println() calls the toString() method of any object you pass to it.

I don't know what command you'd use to get the memory address of an object or if it's possible.

---

### Post by Ghostmn on 2012-03-26
> **satsujinka said:**
> System.out.println() calls the toString() method of any object you pass to it.

I don't know what command you'd use to get the memory address of an object or if it's possible.

I didn't know that it calls the toString method. As far as memory addresses, comment out the toString method to see that specific object's memory address.

---

### Post by satsujinka on 2012-03-26
> **Ghostmn said:**
> I didn't know that it calls the toString method. As far as memory addresses, comment out the toString method to see that specific object's memory address.

Except all objects in Java inherit from the Object class by default. Object has a toString() so you can't avoid it by doing that either (you'll just get weird output.)

You can get an object's reference-id, but that tells you nothing about where the object is located (it deals more with == then with memory addresses.)

So, basically, you're out of luck. You can't get a memory address in Java.

---

### Post by Ghostmn on 2012-03-27
> **satsujinka said:**
> Except all objects in Java inherit from the Object class by default. Object has a toString() so you can't avoid it by doing that either (you'll just get weird output.)

You can get an object's reference-id, but that tells you nothing about where the object is located (it deals more with == then with memory addresses.)

So, basically, you're out of luck. You can't get a memory address in Java.

Hmm, if what you're saying is true, my class has been somewhat misleading.

Thanks for clearing this up. I'm going to have to spend more time with Java.

---

