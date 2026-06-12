---
title: "Java Static vs Non-Static"
date: 2013-07-19
forum: Programming Talk
---

### Post by mhaggard on 2013-07-19
I am trying to understand the difference between static and non static methods in java as I am new to java and have little to no experience with classes and all things that go with them.

I read that a static method belongs the class itself and the non static method belongs to the object that is generated from that class. Can anyone help me understand this a little better? Any analogies are appreciated lol. 

Thank you in advance.

---

### Post by r-senior on 2013-07-20
Imagine you have a big 12" pizza cutter and a massive sheet of pizza dough. As you press the cutter into the dough, you make individual pizzas. Each pizza can then be topped differently -- cheese, ham, onion, etc. 

Each individual pizza is an instance of the Pizza class. A method like addTopping() is an instance (non-static) method because it operates on an individual instance of the class. When you add a topping, you add it to an individual pizza. Instance methods are the most common methods in an OO design.

Static methods (and variables) are not associated with any particular instance, they are associated with the class. If you wanted to keep a count of how many pizzas you had made, you could use a static variable 'count' on the Pizza class. If you wanted a convenience method to convert from weight in grams to weight in ounces, you could make that a static method. Neither the count nor the conversion method need a pizza for them to make sense.

```

public class Pizza {

    // Constant for weight conversion
    private static final float OUNCES_PER_GRAM = 0.0352739619;

    // Variable to count how many pizzas have been made
    private static int count = 0;

    // Toppings for this pizza
    private List toppings = new ArrayList();

    // Constructor
    public Pizza() {
        // Each time we make a pizza, increment the count
        ++count;
    }

    // Instance method -- needs an instance (a pizza) to make sense
    public void addTopping(String topping) {
        toppings.add(topping);
    }

    // Static method -- doesn't need an instance to make sense
    public static float gramsToOunces(float grams) {
        return grams * OUNCES_PER_GRAM
    }

}

```

Later on, when you expand your product line beyond pizzas, you might move the weight conversion to its own class because it's not just useful for converting the weight of pizzas. Changing the structure of your classes to adapt to changing needs is called refactoring.

(I haven't compiled the code above, it's for illustration).

---

### Post by mhaggard on 2013-07-20
Ok! That made perfect sense!! Thanks a lot. Now I understand why the examples I was looking at used the particular methods they used when they used them. Great analogy btw. I appreciate it.

---

