---
title: "Java instantiate non static objects from main?"
date: 2012-12-04
forum: Programming Talk
---

### Post by flyingsliverfin on 2012-12-04
Hi! I'm about 3 months into java for my high school APCS class. I'm taking it far beyond what the book exercise asks, but since I'm already familiar with programming I thought I'd take the simple exercise into an expandable structure. 

Basically, what I'm aiming for is to have a program that will take input and do actions: there should be 'customer' objects, which have properties like maxCredit, accountNum, balance, and totalCharge. Then they need to have functions to access these numbers and to see if the customer has exceeded their credit limit.

My problem is that I need to want to make arbitrary numbers of customers. Whenever I try to make a new customer object inside main() it tells me I cannot do that since that is trying to make a non-static call in a static reference? 
Here is the code (which is not quite complete but i want to get this error sorted out because it seems pretty basic):
```
package ch4;
import java.util.ArrayList;
import java.util.Scanner;

public class exercise4$18 {
    private class customer {
        int acc, balance,total, credits,allowedCred;
        customer(int acc, int balance, int total, int credits, int allowedCred) {
            this.acc = acc;
            this.balance = balance;
            this.total = total;
            this.credits = credits;
            this.allowedCred = allowedCred;
        }
        void setAcc(int val){
            this.acc = val;
        }
        void setBalance(int val){
            this.balance = val;
        }
        void setTotal(int val){
            this.total = val;
        }
        void setCedits(int val){
            this.credits = val;
        }
        void setAllowedCred(int val){
            this.allowedCred = val;
        }
	int difference() {
	    return this.allowedCred - this.total;
	}
    }

    ArrayList<customer> c = new ArrayList<customer>();
    Scanner input = new Scanner(System.in);

    public static void main(String[] args) {
	while (true) {
            System.out.printf("1: new acc\n, 2: get total charged for acc\n, 3: get credit allowed: ");
            int i = input.nextInt();   //***"non static variable cannot be accessed from static context"
            if (i == 1) {
                makeCustomer();	//***"non static method cannot be referenced from static context
            }
            else if (i == 2) {
		System.out.println("account number: ");
		int j = input.nextInt(); //***"non static variable cannot be accessed from static context"
		printTotal(j);	//***"non static method cannot be referenced from static context
	    }
	    else if (i == 3) {
		System.out.println("account number: ");
		int j = input.nextInt(); //***"non static variable cannot be accessed from static context"
		printMaxCredit(j); //***"non static method cannot be referenced from static context
	    }
        }
    }
    void printTotal(int k) {
	System.out.printf("Current charged total: %d",c.get(customerIndex(k)).total);
    }
    void printMaxCredit(int k) {
	System.out.printf("Account's allowed credit is: %d", c.get(customerIndex(k)).allowedCred);
    }
    void makeCustomer() {
	int acc, balance,total, credits,allowedCred;
	System.out.println("New account #: ");
	acc = input.nextInt();
	System.out.println("New account startingbalance: ");
	balance = input.nextInt();
	System.out.println("New account starting credit: ");
	credits = input.nextInt();
	System.out.println("New account starting totalbalance: ");
	total = input.nextInt();
	System.out.println("New account allowed credit: ");
	allowedCred = input.nextInt();
	c.add(new customer(acc,balance,total,credits,allowedCred));
    }
    int customerIndex(int accNum) {
        int i;
        for (i = 0; i < c.size(); i++){
            if (c.get(i).getAcc() == accNum){
                return i;
            }
        }
        return i;
    }    
}

```

Thanks!

---

### Post by muteXe on 2012-12-04
Hiya,
Firstly, put your customer class in it's own file. That might make things a bit clearer.

---

### Post by slickymaster on 2012-12-04
muteXe is right, your customer class should be in it's own file, which will be the template for the creation of the various customers objects.
The difference between a class and an object parallels the difference between abstract and concrete. An object is an instantiation of a class, or one tangible example of a class.
The concept of a class is useful because of its reusability. Objects gain their attributes from their classes, and all objects have predictable attributes because they are members of certain classes.

---

### Post by spjackson on 2012-12-04
Because main is a static method, it does not have an object on which it operates. The methods you are calling and member variables you are using need an object of class exercise4$18, so you need to create one in main and use it. Something like this (untested):
```

    public static void main(String[] args) {
    exercise4$18 thing = new exercise4$18;

	while (true) {
            System.out.printf("1: new acc\n, 2: get total charged for acc\n, 3: get credit allowed: ");
            int i = thing.input.nextInt();
            if (i == 1) {
                thing.makeCustomer();
            }
            else if (i == 2) {
		System.out.println("account number: ");
		int j = thing.input.nextInt();
		thing.printTotal(j);
	    }
	    else if (i == 3) {
		System.out.println("account number: ");
		int j = thing.input.nextInt();
		thing.printMaxCredit(j);
	    }
        }
    }

```

---

### Post by flyingsliverfin on 2012-12-04
> **slickymaster said:**
> The difference between a class and an object parallels the difference between abstract and concrete. An object is an instantiation of a class, or one tangible example of a class.
The concept of a class is useful because of its reusability. Objects gain their attributes from their classes, and all objects have predictable attributes because they are members of certain classes.

I understand that the difference between a class and an instance of the class is that the instance is a build off of the 'blueprint', as i like to think about it. Also, as far as I can understand, "static" means that there doesn't have to be (or you can't make) an instance of that class to access its variables and functions.

---

### Post by flyingsliverfin on 2012-12-04
> **muteXe said:**
> Hiya,
Firstly, put your customer class in it's own file. That might make things a bit clearer.

Is this required? What's the difference between having a public class inside the main class and instantiating that and having it made from a separate file?

---

### Post by flyingsliverfin on 2012-12-04
> **spjackson said:**
> Because main is a static method, it does not have an object on which it operates. The methods you are calling and member variables you are using need an object of class exercise4$18, so you need to create one in main and use it. Something like this (untested):
```

    public static void main(String[] args) {
    exercise4$18 thing = new exercise4$18;

	while (true) {
            System.out.printf("1: new acc\n, 2: get total charged for acc\n, 3: get credit allowed: ");
            int i = thing.input.nextInt();
            if (i == 1) {
                thing.makeCustomer();
            }
            else if (i == 2) {
		System.out.println("account number: ");
		int j = thing.input.nextInt();
		thing.printTotal(j);
	    }
	    else if (i == 3) {
		System.out.println("account number: ");
		int j = thing.input.nextInt();
		thing.printMaxCredit(j);
	    }
        }
    }

```

What I don't understand here is how making a new instance of exercise4$18 inside main like you did is any different from just making an instance of my customer...

Also, to me it seems quite a roundabout way to make a scanner by making a an instance of a class that contains the scanner and then accessing the instance's scanner via thing.input; what's the reasoning behind not allowing a global scanner to be declared/used everywhere?

---

### Post by flyingsliverfin on 2012-12-04
One last thing, I just realized that when you created an instance of exercise4$18:
```
exercise4$18 thing = new exercise4$18;
```

Does this not need () to work? like
```
exercise4$18 thing = new exercise4$18();
```

Because if I add the parentheses it gives me the non-static error again...

EDIT: Did a bit of experimenting with putting it in another file. If i put the exercise4$18 class in another file, and call it with ```
exercise4$18 thing = new exercise4$18();
``` there is no non-static error. Confused?

---

### Post by flyingsliverfin on 2012-12-04
An hour later I feel like I have reached enlightenment!

The reason I can't declare a class (and instantiate it) inside the class containing the main method is that the class containing the main method has to have purely static methods and classes!

Therefore, it is mandatory to move the classes that need to be instantiated into a new file!

This still feels really redundant but makes sense at least!

---

### Post by muteXe on 2012-12-04
Glad to see you're getting the hang of it, but it's not the fact you've moved your class to another file that's magically fixed it. It's the fact you have instantiated your object from your class and call methods on this object.

---

### Post by slickymaster on 2012-12-04
> **flyingsliverfin said:**
> I understand that the difference between a class and an instance of the class is that the instance is a build off of the 'blueprint', as i like to think about it. Also, as far as I can understand, "static" means that there doesn't have to be (or you can't make) an instance of that class to access its variables and functions.


Only nested classes can be static. All top-level class, e.g. a class that corresponds to its own java file sporting the same name as the class name is by definition already top-level, so there is no point in declaring it static, it is an error to do so. The compiler will detect and report this error.

---

### Post by slickymaster on 2012-12-04
> **slickymaster said:**
> Only nested classes can be static. All top-level class, e.g. a class that corresponds to its own java file sporting the same name as the class name is by definition already top-level, so there is no point in declaring it static, it is an error to do so. The compiler will detect and report this error.

A static inner class can have instances but they don't have enclosing instances, which a non-static inner class have.

---

### Post by spjackson on 2012-12-05
> **flyingsliverfin said:**
> One last thing, I just realized that when you created an instance of exercise4$18:
```
exercise4$18 thing = new exercise4$18;
```

Does this not need () to work? like
```
exercise4$18 thing = new exercise4$18();
```

Yes. Sorry about the C++ism. I did say "Something like this (untested)".

---

### Post by Jason80513 on 2012-12-05
The confusion you are having has to do with the difference between inner classes and static inner classes. If you had declared your inner class with the static keyword, the whole thing would have worked in the first place.

The best thing to do, to get started, is to declare every class in a separate file and stay away from inner classes at first. And before you use inner classes, you really need to study up on them, static inner classes, and anonymous inner classes, and where they are useful. They come in handy, but they are also easy to abuse. And you can do everything with regular classes in separate files anyway.

Hope that helps point you in the right direction.

---

