---
title: "C# creating objects"
date: 2011-05-14
forum: Programming Talk
---

### Post by Drenriza on 2011-05-14
anyone who can tell me how to create objects when using a constructor and when NOT using a constructor?

Thanks on advance.
Kind regards.

---

### Post by cgroza on 2011-05-14
You have to use a constructor. If you do not define it, a default one is provided.

---

### Post by simeon87 on 2011-05-14
> **cgroza said:**
> You have to use a constructor. If you do not define it, a default one is provided.

That is not necessarily true. The object may have one or more [factory methods](http://en.wikipedia.org/wiki/Factory_method_pattern) from which the object can be created. If you wish to create an object but the constructor is private, look in the documentation if there are any factory methods available.

---

### Post by Drenriza on 2011-05-14
> **cgroza said:**
> You have to use a constructor. If you do not define it, a default one is provided.

what would the code look like? for example i have a little program, where i try to get better. The program is to make a machine that can give a refreshing drink :p when you put enough money in the machine.

And i'm having trouble to create a refreshing drink object. i cannot visualize it.
Where i then would put the drink in a array to track how many drinks are their, and such.

Any guides about object making?

---

### Post by simeon87 on 2011-05-14
> **Drenriza said:**
> what would the code look like? for example i have a little program, where i try to get better. The program is to make a machine that can give a refreshing drink :p when you put enough money in the machine.

And i'm having trouble to create a refreshing drink object. i cannot visualize it.
Where i then would put the drink in a array to track how many drinks are their, and such.

Any guides about object making?

What language are you programming in?

I suggest the following objects: a DrinkMachine and a Drink. The DrinkMachine could have a method called purchase with name and an amount of money.

The DrinkMachine could have a number called capacity which keeps track of the number of drinks in the machine. Whenever a drink is purchased, a Drink object could be created and returned to the caller of the purchase method.

---

### Post by PaulM1985 on 2011-05-14
Alternatively the DrinkMachine class could have an array of Drink objects.  To fill the DrinkMachine class you could have a method:
add(Drink drink)
which adds a drink to the DrinkMachine (like when a real person is filling it up).

When someone buys a drink the purchase method would take an amount of money for the drink and if the amount is enough, the Drink object would be removed from the array in DrinkMachine, and the object would be returned from the function.

Paul

---

### Post by Drenriza on 2011-05-14
> **simeon87 said:**
> what language are you programming in?



c#

---

### Post by cgroza on 2011-05-14
> **simeon87 said:**
> That is not necessarily true. The object may have one or more [factory methods]("http://en.wikipedia.org/wiki/Factory_method_pattern") from which the object can be created. If you wish to create an object but the constructor is private, look in the documentation if there are any factory methods available.
Those methods would be static. Not exactly my definition of constructor. If those methods have to use a private constructor, the user still uses a constructor indirectly.

---

### Post by simeon87 on 2011-05-14
> **cgroza said:**
> Those methods would be static. Not exactly my definition of constructor. If those methods have to use a private constructor, the user still uses a constructor indirectly.

Yes, which means that you don't have to use a constructor to create an object. Sometimes objects can only be created by calling a factory method. Internally, a constructor is still used but a constructor is therefore not the only way to create an object (it can be private by design).

---

### Post by cgroza on 2011-05-14
> **simeon87 said:**
> Yes, which means that you don't have to use a constructor to create an object. Sometimes objects can only be created by calling a factory method. Internally, a constructor is still used but a constructor is therefore not the only way to create an object (it can be private by design).
A constructor still has a crucial role in the creation of the object. So the constructor is still used. Hidden by the implementation or not, it is used.

---

### Post by simeon87 on 2011-05-14
> **cgroza said:**
> A constructor still has a crucial role in the creation of the object. So the constructor is still used. Hidden by the implementation or not, it is used.

It may be part of your current age that you wish to be right in a discussion. I'm merely pointing out that your initial answer that "you have to use a constructor" was wrong and that there are other ways to create an object.

---

### Post by cgroza on 2011-05-14
> **simeon87 said:**
> It may be part of your current age that you wish to be right in a discussion. I'm merely pointing out that your initial answer that "you have to use a constructor" was wrong and that there are other ways to create an object.
I do have better things to do than to dispute this subject. Be it your way, but the thing is that the object is created by the constructor, the object is only returned by the function.

---

### Post by simeon87 on 2011-05-14
> **cgroza said:**
> I do have better things to do than to dispute this subject. Be it your way, but the thing is that the object is created by the constructor, the object is only returned by the function.

Yes, I never said something to the contrary.

---

### Post by ve4cib on 2011-05-15
> **Drenriza said:**
> what would the code look like? for example i have a little program, where i try to get better. The program is to make a machine that can give a refreshing drink :p when you put enough money in the machine.

And i'm having trouble to create a refreshing drink object. i cannot visualize it.
Where i then would put the drink in a array to track how many drinks are their, and such.

Any guides about object making?


I would organize your data structures like this:

```

DrinkMachine
    .drinkArray      // the array of drinks in the machine
    .moneyInserted   // the amount of money inserted into the machine

    .insertMoney(int cents)    // insert some coins
    .refund()                  // return all coins
    .buyDrink()                // remove a drink from the array and return it

RefereshingBeverage
    .price           // how much does this drink cost?

```

The code itself would look something sort of like this:

```

class DrinkMachine {
    private int moneyInserted;
    private ArrayList<RefereshingBeverage> drinkArray;

    public DrinkMachine() {
        moneyInserted = 0;  //initially there is no money
        drinkArray = new ArrayList<RefereshingBeverage>();

        // stock the machine with its full capacity of drinks
        for(int i=0; i<MAX_DRINKS; i++) {
            drinkArray.insert(0, new RefereshingBeverage());
        }
    }

    public void insertMoney(int cents) {
        moneyInserted += cents;
    }

    public int refund() {
        int amt = moneyInserted;
        moneyInserted = 0;
        return amt;
    }

    public RefereshingBeverage buyDrink() {
        if(drinkArray.Length == 0) 
            throw new Exception("The machine is empty!");
        else if(moneyInserted < drinkArray[0].cost)
            throw new Exception("Insert more money");

        moneyInserted -= drinkArray[0].cost;

        return drinkArray.removeAt(0);
    }
}

class RefereshingBeverage {
    public int cost {
        get;
        private set;
    }

    public RefreshingBeverage() {
        cost = DRINK_COST;
    }
}

```

Basically, you create the full stock of drinks initially and store them in an array (or ArrayList in my example).  When you go to buy a drink you check if the machine contains enough money to buy the drink.  If it does you remove the drink from the array and return it.

That's one possible solution, anyway.  There are many others, but hopefully this might get you started.

---

### Post by Drenriza on 2011-05-15
Thanks for all the replies guys. Unfortunately i'm stuck on this one.

I got 3 classes, where in my first class i print all text, and insert "money" in the machine.
in the second class, which i made it a super class, where the third class inherits from the second one. Also the second class is the class that contains the constructor that i try to call from the third one.......

But i just get error on error and now i give up until tomorrow. And then i must ask some friends to explain it to me.

And its a bit annoying for if add the static option in my 3 methods, 1 in each class i get 0 errors. And everything just works. But as soon as i want to try and use a object all hell brakes loose :p :(

---

### Post by PaulM1985 on 2011-05-15
If you posted a bit of your code we could have a look and try to help you out :-)

---

### Post by simeon87 on 2011-05-15
> **PaulM1985 said:**
> If you posted a bit of your code we could have a look and try to help you out :-)

I do agree that some code would help. This shouldn't be a difficult problem but without code we can't see what's going on.

---

### Post by Drenriza on 2011-05-15
Sure thing. Code from class 1

```
static void Main(string[] args)
        {
            //LaeskedrikKlasse soda = new LaeskedrikKlasse();

            //fields
            String valg0;
            valg0 = String.Empty;
            int valg1 = 0;

            String valg0dot1;
            valg0dot1 = string.Empty;
            int valg1dot1;
            
            string insert1;
            byte insert2;

            Console.WriteLine("Vaelg den laeskedrik type du gerne ville have");
            Console.WriteLine("1: Sodavand");
            Console.WriteLine("2: Juice");
            Console.WriteLine("3: ØL");
            valg0 = Console.ReadLine();
            valg1 = Int32.Parse(valg0);
            switch (valg1)
            {
                case 0:
                    {
                        Console.Clear();
                        string secret;
                        int password;
                        Console.WriteLine("This is the administration section");
                        Console.WriteLine("trespassing this section will result in police reporting");
                        Console.WriteLine("type security code");//000
                        secret = Console.ReadLine();
                        password = Int32.Parse(secret);
                        if (password == 000)
                        {
                            Console.WriteLine("1: Print all arrays");
                            Console.WriteLine("2: print specific array");
                        }
                        else
                        {
                            Console.WriteLine("contacting administrator about trespassing");
                        }
                        valg0dot1 = Console.ReadLine();
                        valg1dot1 = Int32.Parse(valg0dot1);

                            switch (valg1dot1)
                            {
                                case 1:
                                    {
                                        Console.WriteLine("dette er test under administration case 1");
                                        
                                        //Sodavand.afleasningAfArrays();
                                        break;
                                    }
                            }//switch ends

                        break;
                    }
                case 1:
                    {
                            Console.WriteLine("Indtast belob");
                            insert1 = Console.ReadLine();
                            insert2 = byte.Parse(insert1);
                            //purchaseProduct(insert2);//temp2 = insert belob
                            break;
                    }
                case 2:
                    {
                        Console.WriteLine("ikke defineret");
                        break;
                    }
                case 3:
                    {
                        Console.WriteLine("ikke defineret");
                        break;
                    }
            }//switch ends
        }//main methode ends

        private void purchaseProduct(byte insert)//methode starts
        {
            int totalAmount = 0;
            byte testProduct;
            byte test = 10;

            totalAmount = totalAmount + insert;
            testProduct = test;
           
            if (totalAmount >= testProduct)//then
            {
                //pushing out drink
                Console.WriteLine("enjoy our drink");
                if (totalAmount - test > 0)
                {
                    Console.WriteLine(("pushing out drink " + (totalAmount - test) + " ddk"));
                    totalAmount = 0;
                }
                else
                {
                    totalAmount = 0;
                }
            }//if main statement ends
                if (test - totalAmount < test && test - totalAmount > 0)
                {
                    Console.WriteLine(("please add another " + (test - totalAmount) + " ddk"));
                }//if statement ends

        }//methode ends
```

The methode purchaseProduct(byte insert) is where i test if the "customer" has putted enough "money" in the machine. All the switches work just fine.
Also because i dont have a object, my insert money dosent work 100%, this works tho just fine if i use the static commands.

This is the constructor ive been working on in my super class. I have commented alot out. I do such if i want to try and change some code without deleting the old one. So i can "roll" back if i screw it up ,)
```
class LaeskedrikKlasse
    {
        //fields
        public double Storrelse;
        private String Embalage;
        private byte Pant;
        private String plast;
        //private string navn;
        //fields ends

        //konstruktør for laeskedriks klassen //genopfyldning?
       //---->>current working on this //public LaeskedrikKlasse(string navn)
        //{
            //Storrelse = 0.50;
           // Embalage = plast;
           // Pant = 1;
            //navn = null;//lav metode
        //}

         //protected Array[] maxStorrelseForSodavand = new Array[10];   <--ignore
        //Array[] maxStorrelseForJuice = new Array[20];    <--ignore
        //Array[] maxStorrelseForOL = new Array[20];   <--ignore
    }//class ends
```

in my third class i try to call my constructor and put its object it create in the array
```
class Sodavand : LaeskedrikKlasse//denne klasse arver fra en super klasse
    {
        //array
        public String[] fakseKondi = new String[10];
```
```
//public void setFyldEnFakseKondiI()
        //{
            //string nyFakseKondi = string.Empty;
            //string navn = nyFakseKondi;
            //LaeskedrikKlasse nySodavand = null;
            //nySodavand = new LaeskedrikKlasse(navn);
            
            
            //for (int plus1 = 0; plus1 <= fakseKondi.Length - 1; plus1++)
            //{
            //    //fakseKondi[plus1] = "Fakse Kondi" + plus1;
            //    fakseKondi[0] = "FakseKondi er Godt";
        //}//metode ends
```

I also have a method to read my array. This works just fine as i've tested it with the static commands.

Just so all know, im no way near "pro" at all. Ive only been working with C# for almost two weeks. So bare with me.

---

### Post by simeon87 on 2011-05-15
So how exactly do you want it to be? With ```
LaeskedrikKlasse soda = new LaeskedrikKlasse();
``` you can create a new LaeskedrikKlasse. You can also modify purchaseProduct to:

```
private LaeskedrikKlasse purchaseProduct(byte insert) {
    LaeskedrikKlasse soda = new LaeskedrikKlasse();
    // ...
    return soda;
}
```

to return an object when it is purchased. You can return null when no object has been purchased.

---

### Post by Drenriza on 2011-05-15
> **simeon87 said:**
> So how exactly do you want it to be? With ```
LaeskedrikKlasse soda = new LaeskedrikKlasse();
``` you can create a new LaeskedrikKlasse. You can also modify purchaseProduct to:

```
private LaeskedrikKlasse purchaseProduct(byte insert) {
    LaeskedrikKlasse soda = new LaeskedrikKlasse();
    // ...
    return soda;
}
```

to return an object when it is purchased. You can return null when no object has been purchased.

the ```
LaeskedrikKlasse soda = new LaeskedrikKlasse();
``` in the first class was an attemp to solve the puzzel. What i would like was to create a constructor in the second class (the super class) that i could call from the third class to create the new soda object, and return that when purchased in the first class.

Does that make sense?

---

### Post by simeon87 on 2011-05-15
> **Drenriza said:**
> the ```
LaeskedrikKlasse soda = new LaeskedrikKlasse();
``` in the first class was an attemp to solve the puzzel. What i would like was to create a constructor in the second class (the super class) that i could call from the third class to create the new soda object, and return that when purchased in the first class.

Does that make sense?

That's also possible, it would be something like this then:

```
LaeskedrikKlasse soda = new Sodavand();
```

You can do this because Sodavand is a subclass of LaeskedrikKlasse. To have arguments, you can do:

```
LaeskedrikKlasse soda = new Sodavand(123);
```

with

```
public Sodavand(int value) {
    super(value); // this calls the constructor of LaeskedrikKlasse with value.
}
```

and the constructor of LaeskedrikKlasse could be:

```
public LaeskedrikKlasse(int value) {
    this.value = value;
}
```

---

### Post by Drenriza on 2011-05-15
cool thanks mate.

ive seen it a couple of times, but what exactly does it do?

codent my constructor also look like
```

       public LaeskedrikKlasse(string navn)
       {
            Storrelse = 0.50;
            Embalage = plast;
            Pant = 1;
            navn = null;//lav metode
        }

```
To give some default values to an object. And then the navn = null will be added a value by a methode (not yet created)

but i dont understand why my Sodavand class says (see picture)
[ATTACH]192245[/ATTACH]

---

### Post by simeon87 on 2011-05-15
> **Drenriza said:**
> cool i must look at this abit later, but what does the command this do?

ive seen it a couple of times, but what exactly does it do?

this refers to the current object (of that class). So when I do "this.value = 10" then you're setting the variable value of that object to 10. It's not a command, it just refers to the current object.

---

### Post by Drenriza on 2011-05-15
simeon87, i think i edited my post before you read it and didnt save it in time :p so i dunno if you saw my last entry.
in post #22

---

### Post by simeon87 on 2011-05-15
> **Drenriza said:**
> cool thanks mate.

ive seen it a couple of times, but what exactly does it do?

codent my constructor also look like
```

       public LaeskedrikKlasse(string navn)
       {
            Storrelse = 0.50;
            Embalage = plast;
            Pant = 1;
            navn = null;//lav metode
        }

```
To give some default values to an object. And then the navn = null will be added a value by a methode (not yet created)

Right now the given value string navn of the constructor won't be used or stored.

> **Drenriza said:**
> but i dont understand why my Sodavand class says (see picture)
[ATTACH]192245[/ATTACH]

If a class provides a constructor with arguments then the default constructor (without arguments) won't be automatically created. So when you create public LaeskedrikKlasse(string navn) then LaeskedrikKlasse won't have a default constructor without arguments.

That means the subclass Sodavand must also have a constructor with arguments (because if C# would create a default constructor without arguments for Sodavand then it can't call the constructor without arguments in LaeskedrikKlasse because it doesn't exist).

So the short version is that if you don't have a constructor without arguments in a class then you must always provide a constructor with arguments in subclasses. That's why you're getting that message for Sodavand.

---

