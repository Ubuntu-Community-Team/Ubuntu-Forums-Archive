---
title: "need to implement polymorphism in this project"
date: 2009-02-21
forum: Programming Talk
---

### Post by Mia_tech on 2009-02-21
guys I'm working on a project for homework, and I've been asked to use polymorphism, now I've implemented what the workerTester class wants in other words, I'm getting the right ouput printed to screen, but I'm not sure I'm implementing polymorphism.... could someone tell me if I'm doing any polymorphism and if not how could I implemented....
Worker Class
```
public class Worker {
    //variables
    double rate;
    String name;
    double weekSalary;
    //construct worker that takes in name and salary
    public Worker(String name, double rate)
    {
        this.name = name;
        this.rate = rate;
    }
    //method to compute week pay
    public double computePay(int hours)
    {
        this.weekSalary = this.rate * 40;
        return this.weekSalary;
    }
    //getters
    public String getName()
    {
        return name;
    }
}
```

HourlyWorker Class
```
public class HourlyWorker extends Worker{
    //construct HourlyWorker that takes name and rate
    public HourlyWorker(String name, double rate)
    {
        super(name, rate);
    }
    //method for calculating weekly pay
    @Override
    public double computePay(int hours)
    {
        if(hours <= 40)
        {
            this.weekSalary = this.rate * hours;
        }
        else
        {
           this.weekSalary = this.rate * 40;
           int excess = hours - 40;
           double overTime = (excess * 40) * 1.5;
           this.weekSalary += overTime;
        }
       return this.weekSalary;
    }
}
```

SalaiedWorker Class
```
public class SalariedWorker extends Worker{
    //construc SalariedWorker that takes in name and rate
    public SalariedWorker(String name, double rate)
    {
        super(name, rate);
    }
    //method to compute week pay
    @Override
    public double computePay(int hour)
    {
        return super.computePay(hour);
    }
}
```

WorkerTester Class
```
public class WorkerTester {

    public static void main(String[] args)
  {
     Worker s = new SalariedWorker("Sally", 40);
     Worker h = new HourlyWorker("Harry", 40);
     System.out.println(s.computePay(30));
     System.out.println("Expected: 1600");
     System.out.println(h.computePay(30));
     System.out.println("Expected: 1200");
     System.out.println(s.computePay(50));
     System.out.println("Expected: 1600");
     System.out.println(h.computePay(50));
     System.out.println("Expected: 2200");

  }
}
```

---

### Post by Reiger on 2009-02-21
Polymorphism in languages such as Java means that you have 1 method which can accept several types for parameters (super types!).

Consider:
```

public class Test {

 public static main(String [] args) {
   PolyA pa=new PolyA();
   PolyB pb=new PolyB();
   System.out.println("Polymorphism test A+B: "+pa.add(pb));
   pa=new PolyA();
   System.out.println("And A+A: "+pa.add(pa));
 }
}

class PolyB extends PolyB {
  base=17;
}

class PolyA extends Poly {
  base=15;
}

abstract class Poly implements Polymorph {
 public int base=5,value=base;
 public int getValue() { return value; }
 public int add(Polymorph in) { value=in.getValue() + base; return value; }
}

interface Polymorph{
public int base;
public int getValue();
public int add(Polymorph a);
}

```

---

### Post by dwhitney67 on 2009-02-21
While your design is fulfilling the basic principles of polymorphism, one could argue that the Worker class' computePay() method should be defined as 'abstract', thus making the class itself abstract.

One should not be able to instantiate a Worker class directly, since it makes no sense to do so; by defining the class as abstract you can prevent the following:
```

Worker worker = new Worker("Joe the Plumber", 75);

```

As far as I know, there are three types of workers:  Salaried Exempt, Salaried Non-Exempt, and Hourly.  You can read more about these type [here]("http://blogs.payscale.com/ask_dr_salary/2007/01/hourly_wage_vs_.html").

Btw, Salaried workers are not paid by the hour, so typically they are not provided their hourly rate.  Instead, they are given a yearly salary.  When constructing a Salaried Worker object, have the constructor accept the yearly salary; then take that value and divide it by 2080 (= 52 weeks * 40 hours) to yield the hourly rate as expected by your Worker class.

---

### Post by konqueror7 on 2009-02-21
you have fulfilled polymorphism in your code as i see it,,,there are two kinds of polymorphism, overloading and overriding...what you've done here is only overriding...

---

### Post by Mia_tech on 2009-02-21
> **konqueror7 said:**
> you have fulfilled polymorphism in your code as i see it,,,there are two kinds of polymorphism, overloading and overriding...what you've done here is only overriding...

Thanks to all for the help.... I was sure that overloading the methods was polymorphism, but I wasn't sure about overriding... since overloading is calling the same method with slight different method signatures

---

