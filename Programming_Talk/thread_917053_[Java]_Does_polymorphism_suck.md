---
title: "[Java] Does polymorphism suck?"
date: 2008-09-11
forum: Programming Talk
---

### Post by mike_g on 2008-09-11
People seem to think polymorphism is amazing, but I dont really see why; probably because I am using it badly. I am converting a short bit C code to Java, but my Java version is starting to look as if it will be 50 x more code :/ 

Heres what I was doing in C:
```
typedef struct gate
{
    struct gate* one; 
    struct gate* two; 
    struct gate* next; 
    int (*func)(int, int);
    int a, b, result;
}Gate;

int and_gate(int a, int b) { return a&b; }
int or_gate(int a, int b)  { return a|b; }
int not_gate(int a, int b) { return (a)?0:1; }
int xor_gate(int a, int b) { return a^b; }
int nor_gate(int a, int b) { return !(a|b); }
int nand_gate(int a, int b){ return !(a&b); } 

```
Basically its a struct with a function pointer which is set in the constructor and causes the object to behave differently depending on its gate type.

Now this is what I have in Java. First off an abstract gate class
```
package logicgates;
public abstract class LogicGate 
{
    protected LogicGate source_a, source_b;
    protected int input_a, input_b, output;

    public LogicGate(){}
    public boolean evaluate(){return false;}
    
}
```
Then for each type of logic gate I have an inherted class. This is an AND gate:
```
package logicgates;

public class AndGate extends LogicGate
{
    
    public AndGate(LogicGate s1, LogicGate s2)
    {
        source_a = s1;
        source_b = s2;
        input_a = input_b = output = -1;
    }
    
    public AndGate(int a, int b)
    {
        input_a = a;
        input_b = b;
        output = -1;
        source_a = source_b = null;
    }
    
    public boolean evaluate()
    {  
        if(output !=-1) return false;
        int inputs = 0;
        inputs += (source_b != null)?(source_b.output == -1)?1:0:1;
        inputs += (source_a != null)?(source_a.output == -1)?1:0:1;
        if(inputs != 2) return true;
        if(source_a != null) input_a = source_a.output;
        if(source_b != null) input_b = source_b.output;
        output = input_a & input_b;
        return false; 
  }
  
}
```
All the classes would end up with more or less identical code; not what I want to be doing. Also, when creating new objects, I first need to determine what gate type it is then call the appropriate constructor. So in my list class I also have this ugly turd:
```
    public void add(int a, int b, int type)
    {
        switch(type)
        {
            case Globals.GATE_TYPE_AND: 
                 list.add(new AndGate(a, b));
                 break;
            default:
                 System.out.println("Unknown Gate Type");
        }
        
    }
    
    public void add(LogicGate a, LogicGate b, int type)
    {
        switch(type)
        {
            case Globals.GATE_TYPE_AND: 
                 list.add(new AndGate(a, b));
                 break;
            default:
                 System.out.println("Unknown Gate Type");
        }        
    }
```
Which will grow when more gate types are added. I'm sure it must be possible to generalise this somehow; I just dont really know how to with polymorphism/java. Can someone tell me what I can do to remove recurring code here?

Cheers.

---

### Post by Npl on 2008-09-11
you should throw the evaluate-function into the LogicGate class, and define a abstract function "binOp" as the only thing differing is likely the line with ```
 output = input_a & input_b;
```
replace it with ```
 output = binOp(input_a, input_b);
```

you then only have to implement a "int binOp(int a, int b)" for each Class.

* You should define the constructurs in the base class and then merely call them from the derived classes.

* You can simplify your code if you create "constant gates", ie one you inititalise to a integer. That way you dont have to treat those as special case.

* There are ways around such switch-statements, but the real problem is that you have the add function using an int as type. Either you use Classes from top to bottom or you will require such fixups anyway.

---

### Post by mike_g on 2008-09-11
Ok, cool I shifted the evaluate function to the abstract class. Now, I originally  tried to run the constructor content in the abstract class, but could not get it to play. Heres what I got:
```
package logicgates;

public abstract class LogicGate 
{
    protected LogicGate source_a, source_b;
    protected int input_a, input_b, output;

[COLOR="DarkRed"]    public LogicGate(LogicGate s1, LogicGate s2)
    {
        source_a = s1;
        source_b = s2;
        input_a = input_b = output = -1;
    }
    
    public LogicGate(int a, int b)
    {
        input_a = a;
        input_b = b;
        output = -1;
        source_a = source_b = null;
    }[/COLOR]
    
    public boolean evaluate()
    {
        if(output !=-1) return false;
        int inputs = 0;
        inputs += (source_b != null)?(source_b.output != -1)?1:0:1;
        inputs += (source_a != null)?(source_a.output != -1)?1:0:1;
        if(inputs != 2) return true;
        if(source_a != null) input_a = source_a.output;
        if(source_b != null) input_b = source_b.output;
        output = binOp();
        return false;
    }
    
    public int binOp(){return 0;}
    
    public void print() 
    {
        System.out.println("["+this+"] A:"+input_a+" B:"+input_b+" R:"+output);
    }
}
```
And:
```
package logicgates;

public class AndGate extends LogicGate
{
 
    public AndGate(LogicGate s1, LogicGate s2)
    {
       [COLOR="DarkRed"]//What goes here?[/COLOR]
    }
    
    public AndGate(int a, int b)
    { 
        [COLOR="DarkRed"]// and here[/COLOR]
    }
    
    public int binOp()
    {  
        return input_a & input_b;
    }
  
```
<edit> Ok I figured out the constructor thing:
```
    public AndGate(LogicGate s1, LogicGate s2)
    {
        super(s1, s2);
    }
    
    public AndGate(int a, int b)
    {
        super(a, b);
    }
```
</edit>


> * You can simplify your code if you create "constant gates", ie one you inititalise to a integer. That way you dont have to treat those as special case.

Sorry I'm not quite getting what you mean here.
> * There are ways around such switch-statements, but the real problem is that you have the add function using an int as type. Either you use Classes from top to bottom or you will require such fixups anyway.
Well I started out using an enumerator, but I did not like that so I switched to integer constants. Is there any way I can call the correct function constructor w/o the switch statment?

---

### Post by ilrudie on 2008-09-11
I think he means you would make a class called TrueGate that inherits from logic gate.  TrueGate's binOp simply returns true always.  Make a similar FalseGate that always returns false.  Then use these gates as the leaf nodes instead of overloading so that a logic gate can have other gates as inputs OR ints as inputs.  Then gates only need to understand other gates at that point instead of having to understand gates and ints.

Not sure that is what he is saying but I think it is.

---

### Post by Npl on 2008-09-11
> **mike_g said:**
> Sorry I'm not quite getting what you mean here. You coud create a LogicGate which always returns the same integer. that way instead of creating a Gate with "AndGate(1,1)" which always returns 1 you create a "ConstantGate(1)". This should allow you get rid of checking source_a|b == null and using input_a|b conditionally, just use a "ConstantGate" instead.

> **mike_g said:**
> Well I started out using an enumerator, but I did not like that so I switched to integer constants. Is there any way I can call the correct function constructor w/o the switch statment?Well, depends on how you gonna use those classes, but just creating the class directly add( new AddGate(a,b) ) would be easiest.

---

### Post by mike_g on 2008-09-11
Yeah, that makes sense. I'll have a go at it.

---

### Post by tinny on 2008-09-11
Hi mike_g

You dont need this "Globals" class. (This is a very C thing you are doing here :-) )
```

Globals.GATE_TYPE_AND

```

Instead you should use "instanceof" to take advantage of the type hierarchy you are creating.

E.g. something like...

[PHP]
    public void connect(LogicGate a, LogicGate b, LogicGate gate) {
        if (gate instanceof AndGate) {
        	gate.setA(a);
        	gate.setB(b);
        	list.add(gate);
        } else {
        	System.out.println("Unknown Gate Type");
        }      
    }
[/PHP]

Also is your "list" variable generic?

[PHP]
List<LogicGate> list = new ArrayList<LogicGate>();
[/PHP]

---

### Post by mike_g on 2008-09-11
Thanks, I have used getInstance() when working with singletons, but not "instanceof" I'll have a read about it; sounds useful.

> Also is your "list" variable generic?
Yep, and its looking quite a bit tidier now I have added a Constant gate:
```
package logicgates;
import java.util.ArrayList;

public class GateList
{
    ArrayList <LogicGate> list;
    
    public GateList()
    {
        list = new ArrayList<LogicGate>();
    }
    
    public LogicGate get(int i)
    {
        return list.get(i);
    }
    
    public void add(LogicGate a, LogicGate b, int type)
    {
        switch(type)
        {
            case Globals.GATE_TYPE_AND: 
                 list.add(new AndGate(a, b));
                 break;
            case Globals.GATE_TYPE_OR: 
                 list.add(new OrGate(a, b));
                 break;
            case Globals.GATE_TYPE_NOT: 
                 list.add(new NotGate(a, b));
                 break;
            case Globals.GATE_TYPE_XOR: 
                 list.add(new XorGate(a, b));
                 break;
            default:
                 System.out.println("Unknown Gate Type");
        }        
    }
    
    public void add(int state)
    {
        list.add(new BoolGate(state));
    }
    
    public void evaluate(boolean print)
    {
        boolean todo;
        do{
           todo = false;
           for(LogicGate g: list) 
                if(g.evaluate())
                    todo = true;
                else if(print == true) 
                    g.print();
        }while(todo); 
    }
}
```

---

### Post by dribeas on 2008-09-11
> **mike_g said:**
> Thanks, I have used getInstance() when working with singletons, but not "instanceof" I'll have a read about it; sounds useful.

If your design is correct, you should not need to call instanceof an can depend on polymorphism to detect what you need. Avoiding construction of the tree, I would design this as:

```

public abstract class LogicElement
{
   public abstract bool eval();
}

public class BoolElement // true / false elements
{
   boolean value;
   public BoolElement( bool val )
   {
      value = val;
   }
   bool eval()
   {
      return value;
   }
}

public abstract class UnaryGate extends LogicElement
{
   protected LogicElement leaf;
   public UnaryGate( LogicElement theLeaf ) 
   {
      leaf = theLeaf;
   }
}

public class NotGate extends UnaryGate
{
   public NotGate( LogicElement theLeaf )
   {
      super( theLeaf );
   }
   bool eval()
   {
      return ! theLeaf.eval();
   }
}

public abstract class BinaryGate extends LogicGate
{
   protected LogicElement lhs;
   protected LogicElement rhs;
   public BinaryGate( LogicElement left, LogicElement right )
   {
      lhs = left;
      rhs = right;
   }
}

public class AndGate extends BinaryGate
{
   public AndGate( LogicElement left, LogicElement right )
   {
      super( left, right );
   }
   bool eval()
   {
      return lhs.eval() && rhs.eval();
   }
}

// Same with nand, or, nor...

```

When you build your tree (logic operation) you know what you need at each moment. After the tree is built, each node only knows about its operation and calls on each of the subtrees. AndGate does not need to know if its left hand side is a constant, a unary gate, or a binary gate, just that after evaluating its left and right hand sides the result is applying operator && to both results.

One of the advantages is that you can extend your system at any time with, say an n-ary gate and your AndGate can operate with those new objects just as it does with the rest.

EDIT: If you want to edit less code, you could make all constructors parameter less and add setLeaf() and setRight/LeftLeaf() at UnaryGate and BinaryGate levels. Then for each one of the derived classes you would only need to code eval(). Note that int he code above there are no safety checks (verify that references are not null). Those checks could be implemented at Unary/BinaryGate level and be called from eval() before trying to operate on the subtrees.

---

### Post by mike_g on 2008-09-11
Looks cool, but I am unsure if it would work. Ususally a set of logic gates are not laid out like a perfect tree, so recursion does not work; or at least to make it work would be over-complicating things.

Still, the use of polymorphism may be better than what I am currently doing. its getting late here, so I'm off to bed now, but I'll get back to this tomorrow :)

Cheers.

---

### Post by drubin on 2008-09-11
> **tinny said:**
> Hi mike_g
Instead you should use "instanceof" to take advantage of the type hierarchy you are creating.
[PHP]
    public void connect(LogicGate a, LogicGate b, LogicGate gate) {
        if (gate instanceof AndGate) {
        	gate.setA(a);
        	gate.setB(b);
        	list.add(gate);
        } else {
        	System.out.println("Unknown Gate Type");
        }      
    }
[/PHP]

*drubin is not a fan of  instanceof. shows the lack of understanding of inheritance it should never matter what the supper type the object is of.

I would prefer to have something like this with this
[PHP]
    public void connect(LogicGate a, LogicGate b, AndGate gate) {
        gate.setA(a);
        gate.setB(b);
        list.add(gate);   
    }
[/PHP]

Where is the connect method located?

---

### Post by tinny on 2008-09-11
> **rubinboy said:**
> 
*drubin is not a fan of  instanceof. shows the lack of understanding of inheritance it should never matter what the supper type the object is of.


"lack of understanding of inheritance"......really? ;)

It is completely valid to sometimes identify a class by its parent type. If you never do this then you are not using polymorphism. 

Wikipedia
> 
polymorphism lets you treat derived class members just like their parent class' members.


> **rubinboy said:**
> 
I would prefer to have something like this with this
[PHP]
    public void connect(LogicGate a, LogicGate b, AndGate gate) {
        gate.setA(a);
        gate.setB(b);
        list.add(gate);   
    }
[/PHP]

Where is the connect method located?

So its better to do mass method overloading?

Given your example above you would need to create a "connect" method for every subclass of "LogicGate".

Anyway it doesnt really matter, there are MANY ways to solve this problem.

EDIT: Im not saying instanceof is an amazing feature that everyone should use, its just useful sometimes.

If the LogicGate interface defined "setA" and "setB" this would be better.
[PHP]
 public void connect(LogicGate a, LogicGate b, LogicGate gate) {
     
         gate.setA(a);
         gate.setB(b);
         list.add(gate);    
    }
[/PHP]

---

### Post by CptPicard on 2008-09-12
> **tinny said:**
> It is completely valid to sometimes identify a class by its parent type. If you never do this then you are not using polymorphism. 

In practice one sometimes has to resort to instanceof and it's completely understandable, but IMO the Wikipedia quote really means that you can use the supertype instead of derived type, and generally should.

That said, yes, polymorphism, does sometimes suck and that's why interfaces are often preferable. The issue is that changes in base classes tend to break your entire codebase if their actual implementation is relied on heavily. That has little to do with this particular issue though.

---

### Post by drubin on 2008-09-12
> **tinny said:**
> "lack of understanding of inheritance"......really? ;)
[PHP]
 public void connect(LogicGate a, LogicGate b, LogicGate gate) {
     
         gate.setA(a);
         gate.setB(b);
         list.add(gate);    
    }
[/PHP]

This example seems nicer to me. 

On the point of 

> Anyway it doesnt really matter, there are MANY ways to solve this problem.

Yes there are MANY MANY ways of doing things that seems to work. But I have been trying for the last few weeks to concentrate of better practices. I have found that when things are coded neatly and with a thought out process they are MUCH easier to maintain in the long run.  Most of a programs life span is spend doing maintenance not with development. 

Like every thing that is ever expressed on forums it is almost always an opinion and not a fact. This was my opinion. 

The easiest route is not often the best route.

[/flameoff]

---

### Post by pmasiar on 2008-09-12
> **CptPicard said:**
> In practice one sometimes has to resort to instanceof and it's completely understandable, but IMO the Wikipedia quote really means that you can use the supertype instead of derived type, and generally should.

That said, yes, polymorphism, does sometimes suck and that's why interfaces are often preferable. The issue is that changes in base classes tend to break your entire codebase if their actual implementation is relied on heavily. That has little to do with this particular issue though.

That's why Python's way (dynamic 'duck' typing, checking for availability of the method instead of who is the parent) is more flexible (and also more democratic 8-) : if you can handle the task, it does not matter who your father was).

You can use supertype only if you use overriden methods, and no methods specific for this type only.

Polymorphism is dynamic in nature, so obviously it sucks much more in statically typed languages.

---

### Post by tinny on 2008-09-12
> **rubinboy said:**
> 
Yes there are MANY MANY ways of doing things that seems to work. But I have been trying for the last few weeks to concentrate of better practices. I have found that when things are coded neatly and with a thought out process they are MUCH easier to maintain in the long run.  Most of a programs life span is spend doing maintenance not with development. 

Like every thing that is ever expressed on forums it is almost always an opinion and not a fact. This was my opinion. 

The easiest route is not often the best route.

[/flameoff]

Yeah this is very true. The problem for me is that I have very strict deadlines in my job and because of this I become quite frustrated with discussions about optimal technical solutions.

For me suboptimal code that delivers the feature is always better than optimal code that never delivers because its always being tuned.

Sometimes good enough is good enough.

Having said all this I do work on a couple of OSS projects in my free time and I really enjoy the opportunity to do things properly without being influenced by a cardboard cutout manager.

</LetOffSteam>

(Its been a hard week)

---

### Post by Reiger on 2008-09-12
> **pmasiar said:**
> Polymorphism is dynamic in nature, so obviously it sucks much more in statically typed languages.

```

id :: a -> a

```
Yeah, that's right the identity function in Haskell (and it's trivial).

---

### Post by drubin on 2008-09-12
> **tinny said:**
> Yeah this is very true. The problem for me is that I have very strict deadlines in my job and because of this I become quite frustrated with discussions about optimal technical solutions.

For me suboptimal code that delivers the feature is always better than optimal code that never delivers because its always being tuned.

I don't know... I have not got the work exprience of most people (2.5years). What I have seen and read about is that most of the time/development with an application is NOT design/implementation it is fixing bugs and maintenance an application/project that is designed in a way "to meet deadlines" will normally always require MORE work in the long run. 

I have a policy work smart not hard. Care full planing and design leads to the code just fitting into place. 

If there are deadlines that are unrealistic then there is more issues with the project then with the development/code and those should be fixed.

---

### Post by tinny on 2008-09-12
> **rubinboy said:**
> I don't know... I have not got the work exprience of most people (2.5years). What I have seen and read about is that most of the time/development with an application is NOT design/implementation it is fixing bugs and maintenance an application/project that is designed in a way "to meet deadlines" will normally always require MORE work in the long run. 

I have a policy work smart not hard. Care full planing and design leads to the code just fitting into place. 

If there are deadlines that are unrealistic then there is more issues with the project then with the development/code and those should be fixed.

(your right)

Yeah, but my project managers aren't that smart. We develop our projects using "Agile". Agile for them is only about delivering small incremental software features. To them it is not worth putting development effort in if you are not able to get some sort of immediate gain in functionality.

Designing and actually thinking about your code is time wasting to them.

When im hacking at home I get to design, unit test etc... My hacking at home is soooo much better than my code at work.

---

### Post by drubin on 2008-09-13
> **tinny said:**
> (your right)

Yeah, but my project managers aren't that smart. We develop our projects using "Agile". Agile for them is only about delivering small incremental software features. To them it is not worth putting development effort in if you are not able to get some sort of immediate gain in functionality.

Designing and actually thinking about your code is time wasting to them.

When im hacking at home I get to design, unit test etc... My hacking at home is soooo much better than my code at work.

Shame!! I have this policy with them they let me take my time with the design so they see slower results at the start but the end product is normally finished in the same time or even faster.

I guess I am lucky with this regard. small company you can kinda get your say in.

---

