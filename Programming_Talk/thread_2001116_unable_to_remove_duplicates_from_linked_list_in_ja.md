---
title: "unable to remove duplicates from linked list in java"
date: 2012-06-10
forum: Programming Talk
---

### Post by Mia_tech on 2012-06-10
hi guys, I have a linkedlist class that implements a method "remove" which removes duplicates; however, I'm unable to remove anything.. could anyone take a look at the code and make some suggestion in my "remove" method... Thanks...


```
public class LinkedList {
    
    private Node first;
    
    public LinkedList()
    {
        first = null;
    }
    
    //add students to the list
    public void add(Student s)
    {
        Node newNode = new Node(s);
        newNode.next = first;
        first = newNode;        
    }
    
    //remove duplicate records (return true if duplicate found)
    public boolean remove(String fn, String ln)
    {
        Student remove;
        boolean found = false;
        int duplicate = 0;
        
        for(Node iterator = first; iterator != null; iterator = iterator.next)
        {
            if(first.value.getFname().equals(fn) && first.value.getLname().equals(ln))
            {
                duplicate++;
                if(duplicate > 1)
                {
                    remove = first.value;
                    first = first.next;
                    return found = true;  
                    
                }                
            }
        }
        return found;
    }
      
    //display list of student
    public void display()
    {
        if(first == null)
            System.out.println("List is empty!");
        else
        {
            while(first != null)
            {
                System.out.println(first.value);
                first = first.next;
            }            
        }            
    }
    
}

```

```
public class Tester {
    
    public static void main(String[] args) {
        
        UnderGrad john = new UnderGrad("john", "doe", 2.7, "computer Science", "phisics");
        UnderGrad jorge = new UnderGrad("jorge", "vazquez", 3.8, "computer Science", "programming");
        UnderGrad john2 = new UnderGrad("john", "doe", 3.0, "Computer Engineering", "phisics");
        
        Advisor jim = new Advisor("jim", "smith");
        
        Grad jane = new Grad("jane", "mckee", 3.0, "Electric Engineering", jim);       
               
              
        LinkedList students = new LinkedList();
        
        students.add(john);
        students.add(jorge);
        students.add(john2);
        students.add(jane);
        
    
        System.out.println(students.remove("john", "doe"));
        
        students.display();  
        
    }
}
```

---

### Post by hyper2hottie on 2012-06-10
Inside of your for loop you arr using "first" when you need to use "iterator". 

Your if statement and inside of it are always checking against the firat node.

---

### Post by AnotherMuggle on 2012-06-10
Quick disclaimer: I am not a Java developer so appologies if any of my comments are incorrect or misleading.  I am just trying to help :D

It looks to me like there are a few issues with your code.  Firstly your head node, in your case the variable called "first" should not change, it should always point to the first element in the list...otherwise you will loose the start of the list and not be able to traverse it again in the future.  This means your display() function should use a temporarly local variable which is initialised with the "first" variable rather than using "first" itself.  With your current implementation try the following and I suspect the output will be different the second time:

```
students.display();  
students.display();  
```

As for the remove function, I think hyper2hottie is correct regarding the use of the variable "iterator" instead of "first". However I think there are a number of other issues which will cause the function to not work as you are expecting.  I'm affraid I don't have any better implementations without some playing with the code myself.

Hope that helps a little.
TK

---

### Post by hyper2hottie on 2012-06-10
I believe his add function works. It just inserts at the front instead of the end.

---

### Post by Mia_tech on 2012-06-10
> **hyper2hottie said:**
> Inside of your for loop you arr using "first" when you need to use "iterator". 

Your if statement and inside of it are always checking against the firat node.

yeah, I tried that too, but b/c iterator is a local variable, when I use the "display" method which uses a class variable it prints all nodes... (didn't remove anything)

these are the changes you mean?

```
//remove duplicate records (return true if duplicate found)
    public boolean remove(String fn, String ln)
    {
        Student remove;
        boolean found = false;
        int duplicate = 0;
        
        for(Node iterator = first; iterator != null; iterator = iterator.next)
        {
            if(iterator.value.getFname().equals(fn) && iterator.value.getLname().equals(ln))
            {
                duplicate++;
                if(duplicate > 1)
                {
                    remove = iterator.value;
                    iterator = iterator.next;
                    return found = true;                    
                }                
            }            
        }
        return found;
    }
```

---

### Post by clayton2 on 2012-06-10
For your display method, I believe that you should create a local Node variable, which I will call "p" for the sake of example. This is so that, as AnotherMuggle pointed out, you wouldn't want first to point to any other Node except for the actual first Node.
So here is what I'm thinking for the display method:

```
    public void display()
    {
        Node p = first;
        if(first == null)
            System.out.println("List is empty!");
        else
        {
            while(p != null)
            {
                System.out.println(p.value);
                p = p.next;
            }            
        }            
    }
```


Edit:
For the remove() method, is it supposed to remove ALL occurrences of a given record? Because the way you have it, if it has 3 or more occurrences of a record, it will just return after it removes the 2nd occurrence.
Maybe it should be something like this. Note: I haven't ran it, so I'm not guaranteeing it. I'm just looking at the code:

```
    //remove duplicate records (return true if duplicate found)
    public boolean remove(String fn, String ln)
    {
        Student remove;
        boolean found = false;
        int duplicate = 0;
        
        for(Node iterator = first; iterator != null; iterator = iterator.next)
        {
            if(iterator.value.getFname().equals(fn) && iterator.value.getLname().equals(ln))
            {
                duplicate++;
                remove = iterator.value;
                iterator = iterator.next;
            }
        }

        if(duplicate > 0)
        {
             found = true;
        }
        return found;
    }
```

Also, you have that Student remove variable declared, and it isn't really used for anything in that method, so any line involving that remove variable, including the declaration line itself, can be removed.
Let me know if that helps!

---

### Post by Mia_tech on 2012-06-10
yeah, the remove method is supposed to remove duplicates, so if a record exists more than once it removes all instance of that records... that been said how should I declare the "remove" variable? instead of a student object should I make it a Node object? And one more thing your display method is not different than mine, all you're doing is using a local Node, and that is find as long as I find a way of transferring the linkedlist after records have been removed to to local variable Node P....

---

### Post by clayton2 on 2012-06-10
In regards to the remove variable in the remove method... it simply is not needed. Your method just returns true or false, and what your current code does with the remove variable is that it just assigns the value of that Node to that remove variable, and does nothing else at all with it, so it's not needed.


In regards to the display method.... Mine is very different than yours. The way you had it, it would loop through, and change which Node first is pointing to, which would give you no way to reference the first element anymore. MY method created a local Node p to traverse the LinkedList, so that the variable first always points to the first element.

I'm not sure what you mean by "as long as I find a way of transferring the linkedlist after records have been removed to to local variable Node P".
Because Node p is just a pointer that points to a Node. There is no need to "transfer" anything.

I hope I explained that good enough.
Let me know.

---

### Post by Mia_tech on 2012-06-11
> **clayton2 said:**
> In regards to the remove variable in the remove method... it simply is not needed. Your method just returns true or false, and what your current code does with the remove variable is that it just assigns the value of that Node to that remove variable, and does nothing else at all with it, so it's not needed.


In regards to the display method.... Mine is very different than yours. The way you had it, it would loop through, and change which Node first is pointing to, which would give you no way to reference the first element anymore. MY method created a local Node p to traverse the LinkedList, so that the variable first always points to the first element.

I'm not sure what you mean by "as long as I find a way of transferring the linkedlist after records have been removed to to local variable Node P".
Because Node p is just a pointer that points to a Node. There is no need to "transfer" anything.

I hope I explained that good enough.
Let me know.

yeah, b/c I call first "remove()" and the "display()"... after I remove duplicate the list contains less nodes, and if I use local variable in both methods how would one knows what the other contains

---

### Post by hyper2hottie on 2012-06-11
You dont quite seem to understand a linked list. The correctikn you made helps but your code is still broken. 

The line: iterator =iterator.next just moves the iterator along. 
You need last.next = iterator.next

That would remove iterator.  Also. Can you explain why you have the variable remove at all? It does nothing. Your prior explanations dont make sense.

Can you post your node class as well. Im on my phone atm and will try fix your code tonight.

---

### Post by AnotherMuggle on 2012-06-11
Here is my, untested, implemenation.  Again I am not a Java developer but I have loosely translated what I would do in C++ to what I believe to be Java syntax.  I hope it points you in the right directon.

```
public int remove(String s) {
  Node current = head;
  Node previous = null;
  
  boolean removedOne = false;
  int matchCount = 0;
  
  while(current != null) {
    removedOne = false;
    if(current.value == s) {
      ++matchCount;
      if(matchCount > 1) {
        removedOne = true;
        current = current.next;
        previous.next = current;
      }
    }
    
    if(removedOne == false) {
      previous = current;
      current = current.next;
    }
  }
  
  return matchCount;
}
```

---

### Post by clayton2 on 2012-06-11
I realized that for the code that I had for your remove method, I had the line:
```
iterator = iterator.next
```But I shouldn't have had that there, because that is what the post-condition of the for-loop already does. I also didn't take into account the case where the last Node is a duplicate.

Also, I seem to have miss understood what the remove method actually does. I had it removing ALL occurrences of the values, but instead I think you want it to leave ONE occurrence in the LinkedList. So here is my modified remove method.

```
    //remove duplicate records (return true if duplicate found)
    public boolean remove(String fn, String ln)
    {
        boolean found = false;
        int duplicate = 0;
        
        for(Node iterator = first; iterator.next != null; iterator = iterator.next)
        {
            if(iterator.next.value.getFname().equals(fn) && iterator.next.value.getLname().equals(ln))
            {
                duplicate++;
                if(duplicate > 1)
                {
                     iterator.next = iterator.next.next;
                }
            }
        }

        if(duplicate > 1)
        {
             found = true;
        }
        return found;
    }
```And the display method that I didn't make any changes to since my last post of it:
```
    public void display()
    {
        Node p = first;
        if(first == null)
            System.out.println("List is empty!");
        else
        {
            while(p != null)
            {
                System.out.println(p.value);
                p = p.next;
            }            
        }            
    }
```Also, Mia_tech, the methods don't need to know what each other contains, since they both modify or access the same LinkedList: [FONT=Courier New]this[/FONT]

Also, hyper2hottie, the LinkedList class doesn't appear to have a last variable, so you couldn't do that.

---

### Post by hyper2hottie on 2012-06-12
@clayton2 - I guess I was not quite clear in my post.  When I said "last" I meant the node previous to the current iterator.  I was actually suggesting what you have done.  Also, your code looks like it would perform well in the middle of the list, but will fail on the boundary.

Problem 1 - You never check the value of "first" in you for loop.  Your first test is going to be on first.next.  So you would miss counting the value of the head node.

Problem 2 - You will have a null pointer error if your the last value is a duplicate.  If the last value is a duplicate then the line "iterator.next = iterator.next.next;" makes iterator.next point to null.  The loop updates with iterator = iterator.next;.  This make iterator=null.  Then it checks the loop condition, iterator.next != null.  But iterator is null and so you have a null pointer exception.

Let me know if you disagree or need a better explanation.

Onto the problem at hand.  I think this code should solve the problem with the boundary conditions.
```

    //remove duplicate records (return true if duplicate found)    
    public boolean remove(String fn, String ln)     
    {
         boolean found = false; 
         int duplicate = 0;         
         Node previous = null;
         for(Node iterator = first; iterator != null; iterator = iterator.next) 
         {
             if(iterator.value.getFname().equals(fn) && iterator.value.getLname().equals(ln))             {
                 duplicate++;
                 if(duplicate > 1)
                 {
                      previous.next = iterator.next;
                     //This is the point where the current element actually gets deleted
                     iterator = previous;
                 }
             }
             previous = iterator;
        }
        if(duplicate > 1)
         {
              found = true;
         }
         return found;
     }

```
Hopefully that works.

I haven't read the display() code so I don't know if it works.

---

### Post by clayton2 on 2012-06-12
Good catch.
I figured that it wasn't correct yet, because I had kept thinking of ways that it wasn't working.
Hopefully the original author will respond if your solution works or not.

---

### Post by AnotherMuggle on 2012-06-12
My solution in post #11 works.  I installed the openjdk and tested it :D

---

### Post by Mia_tech on 2012-06-12
I have not tested post #11, but for a fact the right solution is post #13... is the right answer, and is much cleaner code... I had figured it out anyway, but I wanted to let everyone interested what was the right answer... thanks

---

### Post by AnotherMuggle on 2012-06-13
> **Mia_tech said:**
> I have not tested post #11, but for a fact the right solution is post #13... is the right answer, and is much cleaner code... I had figured it out anyway, but I wanted to let everyone interested what was the right answer... thanks

What do you mean by the "right solution"?  If you are after fast code you will probably find the while loop gives better performance than the iterator.

As for clean code I'm not sure either.  For readability I find it really helps to use curley braces in a consistent manner.  Post #13 uses 3 different styles in a single function.

Glad you got it working :D

---

