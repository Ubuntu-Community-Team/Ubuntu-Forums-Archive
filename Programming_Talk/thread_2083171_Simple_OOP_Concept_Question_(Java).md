---
title: "Simple OOP Concept Question (Java)"
date: 2012-11-11
forum: Programming Talk
---

### Post by kevinharper on 2012-11-11
I have attached a tip calculator that I just finished.

It is clean, up until the part where I start using CardLayouts. But my question has nothing to do w/ GUIs. So please don't judge me just yet on how I hacked it to work.

My question has to do with one of the ActionListeners.
```
/***
 * Action listener CalculateClicked gets values from form. Calls
 * 	chkBilledAmount(), chkTaxRate(), chkTip() to verify form input. If
 * 	invalid input is detected, it calls bgError() & returns (exits). If
 * 	all input is valid, it creates a Calculate object.
 **/
private class CalculateClicked implements ActionListener{
	private boolean isBilledAmountValid = true;
	private boolean isTaxRateValid      = true;
	private boolean isTipValid          = true;
	
	@Override
    public void actionPerformed(ActionEvent ae){			
		if(ae.getSource() == btnCalculate){
			isBilledAmountValid = chkBilledAmount();
			isTaxRateValid      = chkTaxRate();
			isTipValid          = chkTip();
			
			//display red backgrounds where errors found, return (exit)
			if(isBilledAmountValid == false || isTaxRateValid==false || isTipValid == false){
				bgError(isBilledAmountValid, isTaxRateValid, isTipValid);
				return;
			}
			
			//Create Calculate object. Only executed if all input is valid
			Calculate c = new Calculate(billedAmount, taxRate, tipInput, isTipRate);
			totalAmountDue = c.getTotalOwed();
			displayTotalAmountDue(totalAmountDue);
			bottomPanels.show(pnlBottom, "2");
		}
	}
}
```
Fourth line of code from the bottom creates a Calculate object. The next line assigns totalAmountDue, using a method within that Calculate object.

I thought that the c object got loaded into memory and I would be able to access c's methods from anywhere in my code AFTER it was created/declared/instantiated.

That wasn't the case however. I had to find ways to set vars in weird order. It works, but I really don't think what I did is the most efficient way to do this.

PS: I had to split the form in two because it was bigger than what the forum allows.

---

### Post by ofnuts on 2012-11-11
c only exists within the scope of the 'if (ae.getSource() == btnCalculate)' block. When this scope ends it is no longer accessible. If you want to keep it longer, declare it as a class attribute (you can initialize it later).

But IMHO an object for this is overkill. It could be replaced by a method.

---

### Post by r-senior on 2012-11-11
The scope of the c object is the block in which it is declared, i.e. the body if the if statement. If you wanted a wider scope, you would declare it as an instance variable.

In terms of OO design, I think you are missing the key business object: The object that represents the check (bill) that the tip is calculated on. I think that's really what your Calculate object is, but you are trying to use it like a service object -- to do something rather than be something. If your calculate object was called Check, it would naturally have properties like billedAmount and taxRate. You might model the thing that produced the Check as Dinner. Dinner might have a collection of Guest objects ...

Obviously how far you go with modelling things as objects depends on the complexity of the application. You can go too far. But at the moment I can see variables floating around independently when they should probably be inside objects. I'd be thinking about capturing the inputs for the check into a Check object and see where that leads you.

On a slightly different note, floats and doubles are not great for financial calculations. I know it's a learning application (and one that doesn't particularly require great accuracy -- what's a cent between friends?) but it's still worth looking into BigDecimal (or work in cents/pence, etc).

---

### Post by kevinharper on 2012-11-11
So I should be declaring the variable as
```
private Calculate c;
```
along with the method?

> But IMHO an object for this is overkill. It could be replaced by a method.
Yeah... But it was a requirement for the project.

> In terms of OO design, I think you are missing the key business object:
But I'm open to criticism and instruction. :) I know I'm missing a few points/concepts, but that will come with practice. And please, don't hold back. Tell me anything you can think of that I am doing wrong.

> you are trying to use it like a service object -- to do something rather than be something
You're very right. I struggled at the beginning of the semester A LOT with object-oriented model. I'm doing my best to get away from seeing objects/classes as methods or functions. And I agree... A more appropriate name for the class would have been MealCheck or MealBill (my first input is BilledAmount, how obvious is MealBill for the class name?).

> I'd be thinking about capturing the inputs for the check into a Check object and see where that leads you.
So I should do something like the following?
```
c.setBillAmount = Integer.parseInt(txtBilledAmount.getText());
```
So that I don't even save values to local variables? How would I instantiate the object w/out getting saving the values to local fields and then instantiating the class, passing these fields to the class being instantiated?

---

### Post by ofnuts on 2012-11-12
> **kevinharper said:**
> You're very right. I struggled at the beginning of the semester A LOT with object-oriented model. I'm doing my best to get away from seeing objects/classes as methods or functions. And I agree... A more appropriate name for the class would have been MealCheck or MealBill (my first input is BilledAmount, how obvious is MealBill for the class name?).


When you describe your problem, nouns are potential candidates for objects and attributes of objects, verbs for methods. Your "Calculate" object rings all sort of alarms :)

> **kevinharper said:**
> 
So I should do something like the following?
```
c.setBillAmount = Integer.parseInt(txtBilledAmount.getText());
```So that I don't even save values to local variables? How would I instantiate the object w/out getting saving the values to local fields and then instantiating the class, passing these fields to the class being instantiated?

Much simpler actually.... if you have all the amounts as strings, pass them in the constructor

```

class Bill {
    float amount;
    float tipPercent;
    float vatPercent;
    int guestsCount;


    public Bill(String amount,String tipPercent,String vatPercent,String guestsCount) {
        amount=Float.parseFloat(amount);
        // etc...
    }
}

```or
```

class Bill {
    float amount;
    float tipPercent;
    float vatPercent;
    int guestsCount;

    public Bill(){
        // default constructor
    }

    public initialize(String amount,String tipPercent,String vatPercent,String guestsCount) {
        amount=Float.parseFloat(amount);
        // etc...
    }
}

```
in fact your CalculateClicked (which IMHO would be a Calculator) doesn't need to know what the contents are... in the [MVC paradigm]("http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller"), it just moves the data between the View (the input dialog) and the Model (the Bill class) (Calculator is a Controller in that paradigm).

---

### Post by r-senior on 2012-11-12
> **ofnuts said:**
> in fact your CalculateClicked (which IMHO would be a Calculator) doesn't need to know what the contents are... in the [MVC paradigm]("http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller"), it just moves the data between the View (the input dialog) and the Model (the Bill class) (Calculator is a Controller in that paradigm).
This is a really good way of separating it. There are all sorts of advantages. Writing model classes without any reference to the user interface produces something that is easy to test (e.g. with JUnit), doesn't have all the confusion of the Swing stuff mixed with it and works for other presentations (e.g. if you decided to have a web interface or a web service accessed via a smartphone).

So you might create business object "noun" classes like ofnuts suggests and you might put a service object in front of it.

*Bill.java*
```

public class Bill {

    private float netAmount;
    private float taxRate;

    // Public constructors, getters and setters, etc.

    public float grossAmount() {
        return netAmount + netAmount * taxRate;
    }

    ...

```

*Event.java*
```

public class Event {

    private int numberOfGuests;

    // Public constructors, getters and setters, etc.

    ...

```

*TipService.java*
```

public class TipService {

    private Bill bill;
    private Event event;
    private float tipPercent;

    public TipService(Bill bill, Event event, float tipPercent) {
        self.bill = bill;
        self.event = event;
        self.tipPercent = tipPercent;
    }

    public float totalTip() {
        return bill.grossAmount() + bill.grossAmount() * tipPercent
    }

    public float individualTip() {
        return totalTip() / event.numberOfGuests();
    }

}

```

You can test these easily with JUnit:

```

public class TestTipService {

    @Test
    public void testIndividualTip() {
        Bill bill = new Bill(50.00, 20); // 30 + 20% tax
        Event event = new Event(3); // 3 guests
        TipService service = new TipService(bill, event, 10); // 10% tip
        assertEquals(22.00, service.individualTip()); // 66.00 by 3
    }

    ...
}

```

The beauty of sorting out the data model in isolation (and ideally unit tested) is that when you write the GUI, all you have to focus on is shunting data between the GUI and the model. You know the model works and you just use the services it provides. If you want a web interface, you just use the same model, etc.

For bonus points, declare the TipService as an interface and make an implementation so that you can create alternatives, e.g.

```

public class SimpleTipServiceImpl implements TipService

// Just divide by the number of guests

```

```

public class MeansTestedTipServiceImpl implements TipService

// Wealthy guests pay more ;)

```

Then based on a radio group in your user interface you might:

```

TipService service;
if (meansTested)
    service = new MeansTestedTipServiceImpl(bill, event, 10);
else
    service = new SimpleTipServiceImpl(bill, event, 10);

```

There's no right and wrong here. These are just ideas and suggestions. (And there are probably mistakes in the code -- it's just a guide).

---

### Post by Unterseeboot_234 on 2012-11-12
I put your code into NetBeans. The simple answer to your specific question was solved by making the constructor for ```
class Calculate
``` public

```
public class Calculate {
	private double  billedAmount;
	private double  taxRate;
	private double  tipDllOrRate;
	private boolean isTipRate;

	private double taxTotal;
	private double tipAmount;
	private double totalOwed;
	private int    numberOfGuests;
	private double amountPerGuest;
	
	***public*** Calculate(double bld, double tax, double tip, boolean tipRate){
		billedAmount = bld;
		taxRate      = tax;
...


```

Scope is also part of the package concept of java. You can think of package as nested folders.

And, it wasn't until I started coding with NetBeans that I gained insight with the access modifiers: default, public, private, protected along with the two modifiers for threads: synchronized and volitale.

My main advice to you would be to chunk the code into class blocks. Don't make big long lists of code statements. Easier to debug that way. Good luck.

---

### Post by kevinharper on 2012-11-12
:O Unterseeboot_234... HOW COULD I HAVE MISSED THAT?

Dooooooooooooooooooooooooood! I was going insane trying to figure out WHY I couldn't use my object anywhere!

ofnuts & r-senior: Thank you! You have given me a ton of information that I need to chew on for a few days. I need to take another look at interfaces and revisit scope. I will be reading this thread thoroughly over the next few days. Again, a ton of interesting and important info.

---

