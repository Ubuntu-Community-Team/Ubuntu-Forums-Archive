---
title: "infix to postfix conversion in java"
date: 2012-06-27
forum: Programming Talk
---

### Post by Mia_tech on 2012-06-27
I'm trying to convert from infix to postfix; however, I'm having problem displaying the operators

input 2 + 3 
output should be 2 3 +

here's the code.. any help appreciated

```
package postfixstack;

import java.io.*;
import java.util.*;

public class Main {
    
    static Stack<String> optor = new Stack();
    static Stack<Integer> oprand = new Stack();
    
    public static void main(String[] args) throws FileNotFoundException
    {       
        
        File inFile = new File("datafile.txt");
        
        Scanner in = new Scanner(inFile);
        
        while(in.hasNext())
        {
            String next = in.next();
            do
            {
                if(optor.isOperator(next))
                {
                    //process operator
                    processOptor(next);
                }                
                else
                {
                    oprand.push(Integer.parseInt(next));
                    System.out.print(next+" ");
                }
                next = in.next();
            }while(!next.equals("$"));                 
        }     
        
    }
    
    //processing operators
    public static void processOptor(String op)
    {
        do
        {
            if(optor.isEmpty())
            {
                optor.push(op);
                return;
            }
            if(optor.priority(op) > optor.priority(optor.top()))
            {
                optor.push(op);
                return;
            }
            if(optor.priority(op) == optor.priority(optor.top()))
            {
                if(optor.associativity(optor.priority(op)).equals("right"))
                {
                    optor.push(op);
                    return;
                }
            }
            System.out.println(optor.top());
            optor.pop();            
            
        }while(true);
    }
    
}
```

```
run:
2 3 BUILD SUCCESSFUL (total time: 1 second)
```

---

### Post by trent.josephsen on 2012-06-27
> **Mia_tech said:**
> 
```
import java.util.*;

public class Main {
    
    static Stack<String> optor = new Stack();
    static Stack<Integer> oprand = new Stack();
    
<snip>
                if(optor.isOperator(next))
        
<snip>
            if(optor.priority(op) > optor.priority(optor.top()))
<snip>
            if(optor.priority(op) == optor.priority(optor.top()))
<snip>
                if(optor.associativity(optor.priority(op)).equals("right"))

```

Am I missing something here? Granted I'm not 100% on Java, but you haven't defined priority(), associativity(), or isOperator() anywhere and they're certainly not in java.util.Stack. This code shouldn't even compile...

---

### Post by Mia_tech on 2012-06-27
> **trent.josephsen said:**
> Am I missing something here? Granted I'm not 100% on Java, but you haven't defined priority(), associativity(), or isOperator() anywhere and they're certainly not in java.util.Stack. This code shouldn't even compile...

node class

package postfixstack;

```
public class Node<T> {
    
    T value;
    Node next;
    
    //constructor
    public Node(T a)
    {
        value = a;
        next = null;
    }    
}
```

```
package postfixstack;


public class Stack<T> {
    
    public Node<T> head;
        
    //constructor
    public Stack()
    {
        head = null;
    }
    
    //adding to stack
    public void push(T a)
    {
        Node p = new Node(a);
        p.next = head;
        head = p;
    }
    
    //removing from stack
    public void pop()
    {
        head = head.next;
    }
    
    //getting top element
    public T top()
    {
        return head.value;
    }
    
    public boolean isEmpty()
    {
        return head == null;
    }
    
    //dispaly stack
    public void display()
    {
        if(head == null)
            System.out.println("Stack is empty!...");
        else
        {
            Node s = head;
            while(s != null)
            {
                System.out.println(s.value);
                s = s.next;
            }
        }
    }
    
    //checking for operators
    public boolean isOperator(String s)
    {
        String operator = "-+*/^()";
        if(operator.indexOf(s) != -1)
            return true;
        else
            return false;
    }
    
    //returning level of priority
    public int priority(String s)
    {
        int pri = 0;
        if(s.equals("-") || s.equals("+"))
            pri = 1;
        if(s.equals("*") || s.equals("/"))
            pri = 2;
        if(s.equals("^"))
            pri = 3;    
        return pri;
    }
    
    //return associativity (left or right)
    public String associativity(int level)
    {               
        if(level <= 2)
            return "left";
        else
            return "right";            
    }
    
}


```

---

### Post by trent.josephsen on 2012-06-27
That's a good reason not to import $PACKAGE.* by the way, especially if $PACKAGE is a standard package with tons of stuff in it like java.util is. Same for java.io in fact. Also, if you insist on putting those methods in Stack (which seems odd to me... they don't do anything stack-related), you should at least make them static.

Anyway, I took a look and your algorithm terminates with an undisplayed operator(s) still on the stack. You need to go back after your main while loop and pop off and display each operator in order. You'll notice (if your version suffers the same bug as mine) that "2 + 3 * 4 ^ 5" doesn't result in any operators displayed at all, while "4 ^ 5 * 3 + 2" displays all of them but the final '+'. I think that's your only bug though.

---

