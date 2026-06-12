---
title: "incompatible types, I'm sure this has been asked before..."
date: 2010-02-23
forum: Programming Talk
---

### Post by bartre on 2010-02-23
alright, so i'm working on a program that's using a generic stack that i'm pushing chars onto.
the thing is, when i try to pop the chars off, i get this 

mConvert.java:55: incompatible types
found   : java.lang.Object
required: char
                    search = charStack.pop();

now, i know what this means, which is basically that even though i'm pushing chars onto the stack, they convert to objects once they become a part of the stack, and in order to get them back as chars, i'll need to do some conversion myself.

does anyone know how i would fix this?

---

### Post by Some Penguin on 2010-02-23
If your Stack is only meant to contain objects of one type, you'd use 
```

Stack<Character> charStack = new Stack<Character>();

```

assuming you're using Java 5 or later.   

If it's designed to hold other types, you'd want to instead class-cast when you pop -- 
```

Character c = (Character) charStack.pop();

```

That said, you may be better off using LinkedList instead of Stack for efficiency reasons.

---

### Post by bartre on 2010-02-23
well, the stack only needed to hold one data type, so i tried that first example.

now i get this error:

```
Convert.java:25: type Stack does not take parameters
        mlarkin_Stack<Character>  charStack = new mlarkin_Stack<Caracter>();
                     ^
```

I probably should mention that part of the assignment is to use a general stack, written by us, and here's my code for that

```

public class mlarkin_Stack
{
    private ArrayList stack = new ArrayList();

//add obj to the "top" of the stack
    public void push( Object obj )
    {
        stack.add(obj);
    }

//checks if the stack is empty, then removes and returns the "top" of
//the stack
    public Object pop()
    {
        if ( stack.isEmpty() )
            throw new EmptyStackException();
        return stack.remove( stack.size() - 1 );
    }

//check if the stack is empty
    public boolean isEmpty()
    {
        return stack.isEmpty();
    }
}

```

---

### Post by Some Penguin on 2010-02-23
You might be permitted to genericize your stack class.

Otherwise, simply do the class casting thing.  This is a fairly odd assignment, anyway -- I suppose you were directed to use an ArrayList?

Incidentally, class names conventionally start with capital letters and don't use punctuation.  MLarkinStack, for instance.

---

### Post by bartre on 2010-02-23
yeah, my teacher's not really what most call "conventional"

anyway, I tried to do the class casting like you suggested.
that seems to have worked, but now i get this when i compile 

```
Note: ./mlarkin_Stack.java uses unchecked or unsafe operations.
Note: Recompile with -Xlint:unchecked for details.

```

then, if i recompile like it says, i get nothing.

---

### Post by Some Penguin on 2010-02-23
That is to be expected.  The stack doesn't guarantee that the contents will actually be of any particular type, and most Objects cannot be cast to Characters, so the compiler is choosing to warn you.

The exception that would be thrown is an unchecked exception, meaning that technically you don't have to catch it or to declare it as a thrown exception.  You could try/catch it anyway if you care to, or alternately suppress it using the suppress-warning annotations.  Or you could wrap the code using some instanceOf check, perhaps.    There's almost always more than one way to do it.

---

### Post by bartre on 2010-02-23
alright, sweet.

now, there's a second part.
same issue, incompatible types and all that.
only now i'm pushing doubles onto the stack.
I've tried casting and using Double.parseDouble() and it's told me no.
what should i do about it?

here's a snippet of the offending code:

```
                
numB = Double.parseDouble( dblStack.pop() );
numA = Double.parseDouble( dblStack.pop() );
numC = numA + numB;

dblStack.push( numC );

```

---

### Post by Simon17 on 2010-02-23
I'm not a java person, but I think parseDouble parses a STRING to a double.
If you want to convert a generic object back to a double, you need to do a TYPE CAST.

---

