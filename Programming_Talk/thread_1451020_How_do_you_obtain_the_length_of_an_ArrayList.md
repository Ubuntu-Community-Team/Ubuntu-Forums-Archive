---
title: "How do you obtain the length of an ArrayList?"
date: 2010-04-09
forum: Programming Talk
---

### Post by s3a on 2010-04-09
I'm asking for the length not size. Assuming I am correct, the length is how many components there are and the size is how many of those components have something "worthy" in them.

The following is my Sieve class (no bugs - works perfectly :)):
```

package assignment_3b;
import java.util.ArrayList;

public class Sieve
{
    ArrayList<Integer> numberList;
    ArrayList<Integer> primeList;
    int amount;
    
    public Sieve(int amount)
    {
        numberList = new ArrayList<Integer>(amount);
        primeList = new ArrayList<Integer>();
        this.amount = amount;
        int num;

        for(num = 2; num < amount; num++)
        {
            numberList.add(num);
        }
        
        findPrimeNumbers();
    }

    public void findPrimeNumbers()
    {
        while(numberList.size() != 0)
        {
            int p = numberList.get(0);
            primeList.add(p);
            
            for(int counter = 0; counter < numberList.size(); counter++)
            {
                if(numberList.get(counter) % p == 0) // Checks if the specific number is p or one of its multiples
                {
                    // Removes the number p or its multiple
                    numberList.remove(counter);
                }
            }
        }
    }

    public String toString()
    {
        String str = "List of primes up to " + amount +"\n";
        
        for(int num = 0; num < primeList.size(); ++num)
        {
            str += String.format("%5d", primeList.get(num));
            if((num + 1)%15 == 0) str += "\n";
        }
        
        return str;
    }

    public static void main(String[] args)
    {
        Sieve s30 = new Sieve(30);
        System.out.println(s30 + "\n");
        
        Sieve s50 = new Sieve(50);
        System.out.println(s50 + "\n");
        
        Sieve s100 = new Sieve(100);
        System.out.println(s100 + "\n");
        
        Sieve s1000 = new Sieve(1000);
        System.out.println(s1000);
    }

}

```

I used the **amount** variable as a limit in my for loops. My question is; is it possible to use something similar to arrays like for example if I were using a regular array I would do: *index < array.length*

(**index < arrayList.size()** is not what I am asking for.)

Any input would be greatly appreciated!
Thanks in advance!

P.S.
Is what I am asking for impossible?

---

### Post by JCoster on 2010-04-10
I don't understand what you're asking...

What do you mean by elements which are 'worthy?'  If you mean 'not-null' objects then ArrayList.size is the same as this because it's a dynamic structure which will only hold non-null elements (as of my understanding).

However, if you're asking for a method of determining the number of elements within an ArrayList which satisfy a certain rule, then:
```

int valid = 0; // track how many elements satisfy
ArrayList<Object> objectList = new ArrayList<Object>();
for (int i=0;i<objectList.size();i++) {
    if (*objectList.get(i).satisfies()*) {
        valid++;
    }
}
return valid;

```
..where *.satisfies()* is a method returning a boolean depending on whether the object satisfies your specification.

However, if you clarify your question I should be able to help more.

JC

---

### Post by leg on 2010-04-10
I think you might mean the capacity of the ArrayList. This is the number of items that can be stored without having to add any space to memory. The default constructor states it is created with a capacity of ten and there is an ensureCapacity() method but I can't seem to see a getCapacity() method which is what you would want. I though there was a getCapacity() somewhere so have a look for it.

---

### Post by ja660k on 2010-04-10
[http://java.sun.com/j2se/1.5.0/docs/api/](http://java.sun.com/j2se/1.5.0/docs/api/)
search for array list

i think you want .size()

---

### Post by s3a on 2010-04-10
First, .size() is not what I want (I mentionned that in the first post) but thanks anyways. By length, I did mean capacity, yes. Also, I can't seem to find a method called *getCapacity()* or something similar. So, am I just looking for something that does not exist?

---

### Post by CptPicard on 2010-04-10
> **s3a said:**
> Also, I can't seem to find a method called *getCapacity()* or something similar. So, am I just looking for something that does not exist?

You probably are, as the idea of the internal storage management of the ArrayList is that the external user probably doesn't and should not bother about how much free space there actually is reserved at some given time -- if they know their upcoming requirements, they can still "ensureCapacity" that makes the underlying array grow if needed.

---

### Post by s3a on 2010-04-10
Ok ensureCapacity isn't what I had initially asked for but it seems interesting enough. Could you post a super mini program on how it works exactly, please?

---

### Post by CptPicard on 2010-04-10
Uh, it's trivial. If you know beforehand that you'll be pushing, say, 10 000 items into the ArrayList, you can call ensureCapacity(10000) before doing that, so you avoid multiple resizes of the array underneath. That's all there is to it.

---

### Post by s3a on 2010-04-10
What's the advantage of doing that? I ask because, to my knowledge, the ArrayList would expand itself anyways if it needs more space. Is the difference that the ArrayList will only double itself when it needs more space while this allows me to specify exactly how many components I will need?

---

### Post by CptPicard on 2010-04-10
> **s3a said:**
> Is the difference that the ArrayList will only double itself when it needs more space while this allows me to specify exactly how many components I will need?

Yes. If you know beforehand that you'll make your ArrayList huge, you can tell it to allocate sufficient capacity straight away so that it doesn't need to reallocate and shuffle stuff around behind the scenes many times over.

---

### Post by s3a on 2010-04-10
Thanks! :)

---

