---
title: "UML - Sequence Diagrams"
date: 2010-01-13
forum: Programming Talk
---

### Post by PaulM1985 on 2010-01-13
Hi

I want to do a sequence diagram to demonstrate the behaviour of a system I am working on.  I know the basics of how to create a sequence diagram (objects across the top, their lifelines running down and activation rectangles on these lifelines when processing is being completed).  The problem I have got is that I want to show an object which, when executing a method, calls lots of private methods.

As a very basic example

```

class Counter()
{
    int m_current;

    void AddOne()
    {
        int current = GetCurrentCount();
        current++;
        SetCurrentCount(current);
    }

    int GetCurrentCount()
    {
        return m_current;
    }

    void SetCurrentCount(int aCurrent)
    {
       m_current = aCurrent;
    }
}

```

How would I show what happens when AddOne is called on a Counter object, showing all the calls to itself, eg the call to GetCurrentCount and SetCurrentCount?

I hope I have made this idea clear.

The reason I want to do this is I have a very complicated class which I would like to break out into simpler processes higher up, rather than having lots of messy if()'s splitting off for different behaviour.

Paul

---

