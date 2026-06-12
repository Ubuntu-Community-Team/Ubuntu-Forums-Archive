---
title: "Java - Searching a good forum"
date: 2014-09-15
forum: Programming Talk
---

### Post by Drenriza on 2014-09-15
Hi guys and gails.

At the moment im looking into Java, and are in that regard looking for a good active Java forum. If anyone have some good experiences with specific forums please let me know about them.

Other than that i have a open programming question someone might be able to help me with here, since their is many talented people in all areas.
I'am currently making a softdrink "machine", where i have two classes to make these. One with all the variables that different softdrink shares and one with specific variables. One for Coca Cola, Pepsi, Sprite and so on.
But when i make my softdrink object, how do i merge it with the CocaCola object. So the variables from the two different classes are combined.

The current code i work with to make the first object is as follows
```

//main class
ArrayList<Softdrink> softDrinkArray = new ArrayList<Softdrink>();        
for(byte count = 0; count < 20; count++) {[INDENT]softDrinkArray.add(new Softdrink(5, 20, "x", "x"));
[/INDENT]
}


```

```

//softdrink class
public class Softdrink {
    private int size;
    private int price;
    private String expirationDate;
    private String manufactureDate;
    
    public Softdrink() {
        //Empty constructor
    }
    
    public Softdrink(int size, int price, String expirationDate, String manufactureDate) {
        this.size = size;
        this.price = price;
        this.expirationDate = expirationDate; //going to make this a real datetime objects at some point
        this.manufactureDate = manufactureDate; //going to make this a real datetime objects at some point
    }
    
    public int getSize() {
        return size;
    }
    
    public int getPrice() {
        return price;
    }
    
    public String getExpirationDate() {
        return expirationDate;
    }
    
    public String getManufactureDate() {
        return manufactureDate;
    }
}

```

```

//CocaCola class
public class CocaCola {
    private String name;
    
    //nutritional content
    private String PER;
    private String energy;
    private String carbohydrate;
    private String sugar;
    
    public CocaCola() {
        name = "Coca Cola";
        PER = "100ml";
        energy = "180KJ / 42kcal";
        carbohydrate = "10.6g";
        sugar = "10.6g";
    }
}
```

Thanks on advance :KS
Kind regards.

---

### Post by ofnuts on 2014-09-15
If "SoftDrink" represents a purchasable item, then maybe it should have a "content" attribute that references a specific liquid. 

But your naming scheme isn't too clear, IMHO your "SoftDrink" class should be a "Bottle", "Can" or "Container" class, and have an additional "content" attribute of class "SoftDrink" (this class with PER, energy, carbohydrate and sugar attributes), and CocaCola, Sprite, DrPepper being instances of SoftDrink (each with their own values for PER, energy, carbohydrate and sugar).

---

### Post by Drenriza on 2014-09-15
No doubt that your right ofnuts :) SoftDrink should be a bottle, can or something else in that regard as class. And than have the content in another class.
But what im kinda struggling with is the object merging concept. I cant find much on google, youtube or in my books about it.

---

### Post by ofnuts on 2014-09-15
You won't find anything because this concept doesn't really exist. Some languages (like C++, but not Java) support "multiple inheritance" so the object can be two things (for instance, a Dolphin can derive from "SwimmingAnimal" and "Mammal"). But in 99.99% of the case you use simple inheritance. In which case you would for instance define a Drink class  with just PER and energy attributes, and a SoftDrink class that derives the Drink class and adds to it carbohydrate and sugar attributes. But since it is a derived class it can still access the attribute of Drink (if they are "protected", not if they are "private") as done in the healthInformation() method of the SoftDrink class:

```

public class Drink {
    protected String per;
    protected String energy;
    
    public Drink(String per, String energy) {
        this.per=per;
        this.energy=energy;
    }
}

public class SoftDrink extends Drink {
    protected String sugar;
    protected String carbohydrate;

    public SoftDrink(String per, String energy, String sugar, String carbohydrate) {
        super(per, energy);
        this.sugar=sugar;
        this.carbohydrate=carbohydrate;
    }
    
    public void healthInformation() {
        System.out.println(per+"/"+energy+"/"+sugar+"/"+carbohydrate);
    }
}

```

---

