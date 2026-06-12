---
title: "looking for a design pattern for a discount model"
date: 2005-01-10
forum: Programming Talk
---

### Post by dninja on 2005-01-10
I am working on a php based ecommerce site and have been asked if I can implement a discount model where you get a discount if you have certain group of products, eg

If you have A and B then you get 10 pounds off
If you have X, Y and Z you get 20 pounds
If you have A, Z, G, L, O you get 10 pounds

This has to be administerable so needs to be represented in a database.

the products will be identifiable by a unique id and I'll have an array of the ones currently in the shoppers basket.

Does anyone know of a design pattern for something like this? I've had a few ideas but they never seem to be able to cover all posibilities.

I'd like a stylish pattern rather than a brute force, check everything in the basket against every discount group.

---

### Post by Enygma on 2005-01-19
I did something like this a few years back in Java.
Each 'Product' looked something like this:

```

public class Product 
{
   int m_price;
   int m_quantity;
   .
   .
   .
   .
   void addPromotion(Promotion p)
   {
      // add this promotion to a list
   }

   void applyPromotions()
   {
      // for each promotion in the list
         // call the p.applyPromotion(this) method
   }
}

```

The Promotion interface just looked like this:
```

public interface Promotion
{
   public void applyPromotion(Product p);
}

```

Then you'd implement that to create different promotions like this:
```

public class TwoForThePriceOfOnePromotion implements Promotion
{
   public void applyPromotion(Product p)
   {
      // logic in here
      // you can lookup p.getQuantity()
      // and modofy p.getPrice() with a p.setPrice() method.      
   }
}

```

In practice then you've got something like this:

```

.
.
.
Product shirt = new Product(productCode, quantity, price);
shirt.addPromotion(new TwoForThePriceOfOnePromotion());  // or create a PromotionFactory
.
.
shirt.applyPromotions();
totalPrice = shirt.getTotalPrice();

```

It worked fairly well from what I can remember. I don't know if it's a Pattern with a capital P or anything but it does the job.

You might want to look into Rule Engines though, they're suited perfectly to this type of scenario. An example of one is drools ([http://www.drools.org](http://www.drools.org)) I don't know of any for PHP I'm afraid.

Hope this helps

---

### Post by dninja on 2005-01-19
Ta, that is a nice idea but not quite what I am after. Your answer only covers things like "2 for 1" as far as I can tell, what I need is "if you buy a, b and c you get x off".

For your solution to work the product class would need to know about all the other products in your basket.

I would say thought that it is a Pattern :-)

---

### Post by Viro on 2005-01-19
Off the top of my head, if you want to avoid the bruteforce method, you could implement some sort of dictionary/hash table. You'd still need some comparisons, but they number of comparisons would be a lot less when compared with a brute force method.

Seeing as your IDs are unique, for each combination you could sum the IDs together, apply a hashing function to the keys, and then store them in a database.  To determine if the customer has bought a known discountable combination, sum the IDs of the products the customer bought, apply the hashing algorithm, get the key, and compare it with what you have in the database to determine which combination it corresponds to.

This assumes that your keys are numeric. If they're alpha numeric, you could still devise some sort of hash algorithm. This problem is well suited to a hashing algorithm. If what I've said isn't clear (hey, it's 12:05 am where I am :)), look up some documentation on the net on hashing algorithms.

---

