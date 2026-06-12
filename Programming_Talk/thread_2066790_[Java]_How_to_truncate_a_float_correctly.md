---
title: "[Java] How to truncate a float correctly?"
date: 2012-10-05
forum: Programming Talk
---

### Post by epicoder on 2012-10-05
I am by-in-large a python programmer, so I thought it would be a good idea to get some practice in a statically-typed language. I've been learning basic Java, so to test out what I've learned so far I decided to make the obvious joke and make a coffee-based class named Java. Har har har.
My question has to do with this particular bit of code:
```
float pct = delta/capacity;
int heatdelta = 180*pct;
//int heatdelta = 180 * (delta/capacity);
heat+=heatdelta;
```The basic idea is to calculate a percentage, then truncate the resulting float. If I use the above code, I get the following error:
```
main.java:94: error: possible loss of precision
                        int heatdelta=180*pct;
                                         ^
  required: int
  found:    float
1 error
```However, if I use the commented out line (notice that it is the same operations condensed into 1 line) it compiles fine and behaves as expected.

Here is the rest of the code sans the main class I use to test the Java class:
```
class JavaException extends Exception {
    private String msg;
    public JavaException(String err) {
        super(err);
        msg=err;
    }
    public String getError() {
        return msg;
    }
}

class HotException extends JavaException {
    private String msg;
    public HotException(String err) {
        super(err);
        msg=err;
    }
    public HotException() {
        super("Ouch!");
        msg="Ouch!";
    }
    public String getError() {
        return msg;
    }
}
        
class ColdException extends JavaException {
    private String msg;
    public ColdException(String err) {
        super(err);
        msg=err;
    }
    public ColdException() {
        super("Eww!");
        msg="Eww!";
    }
    public String getError() {
        return msg;
    }
}

class Java {

    private int ounces;
    private int capacity;
    private int heat=180; //in F

    public void cool() {
        heat-=20;
    }

    public void drink(int amount) throws HotException, ColdException {
        int delta=0;
        System.out.println("Mmm, caffeine!");
        if (ounces == 0) {
            System.out.println("What? None left? Preposterous!");
            return;
        }
        if (amount == 0) {
            delta=ounces;
            ounces=0;
        } else {
            delta=amount;
            ounces-=delta;
            if (ounces < 0) {
                delta+=ounces;
                ounces=0;
            }
        }
        if (heat > 160) {
            //System.out.println("Ow, this java is hot!");
            throw new HotException();
        } else if (heat < 100) {
            //System.out.println("Eww, this java is lukewarm!");
            throw new ColdException();
        }
        if (heat > 70) {
            heat-=10;
        }
        System.out.println(delta + " ounce(s) consumed");
        System.out.println(ounces + " ounce(s) remaining");
    }

    public void refill() {
        if (ounces == capacity) {
            System.out.println("Your coffee is already full, sir...");
            return;
        }
        int delta=capacity-ounces;
        if (delta == capacity) {
            heat=180;
        } else {
            float pct = delta/capacity;
            int heatdelta = 180*pct;
            //int heatdelta = 180 * (delta/capacity);
            heat+=heatdelta;
        }
        ounces=capacity;
        System.out.println("Here you go, sir. Enjoy.");
    }

    public Java(int iounces) {
        ounces=iounces;
        capacity=iounces;
    }

}
```

So, what is the proper way to truncate a float to an int?

---

### Post by dwhitney67 on 2012-10-05
When you multiple (or divide) a float by an int, the result is a float.  If you want to yield an int, you must cast the result to the desired type.

For example:
```

int heatdelta = (int)(180 * pct);

```
Note that this Java feature does not apply to C or C++, where the operation would indeed yield an int (thus obviating the need to perform the cast).

P.S.  An int divided by an int will yield an int.  Thus if you are assigning this result to a float, you will implicitly lose precision.  In other words, if delta = 22 and capacity = 10, delta/capacity is equal to 2, not 2.2.  You may want to revisit your code with respect to how your variables are declared.

---

### Post by epicoder on 2012-10-05
Hmm. Guess my question should have been "How do I type cast?" :P
Since I'm not too interested in precision or performance for this one, I simply casted delta and capacity to floats for the division, and then casted back to an int for heatdelta.
Here is the final snippet of code:
```
float pct = (float)delta/(float)capacity;
int heatdelta = (int)(180*pct);
heat+=heatdelta;
```

---

### Post by trent.josephsen on 2012-10-05
You don't have to cast every operand to make the operation use floating point arithmetic. Operators will promote their operands and do the math in the wider type as necessary; this is the same as in C. This is actually why you're encountering the problem in the first place: 180 is an int, pct is a float. 180 gets promoted (converted) to a float, then the multiplication is done, so the entire expression has type float. It's only when you attempt to put the result into an integer that javac borks.

I'd write "heatdelta = (int)(180.0*delta/capacity)" 180.0 is a float. The multiplication is done first, with float arithmetic. Then the division is done, and since one of its operands is also a float, it's also done with float arithmetic. The entire result is a float, which is then converted to int.

Edit -- actually, that last operation is done with double arithmetic, not float. Same result, barring marginal rounding errors.

---

