---
title: "overloading the comparison operator in c++ problems"
date: 2010-06-22
forum: Programming Talk
---

### Post by Baerun on 2010-06-22
I have a class 'fgSymbolNode' which I want to compare with other fgSymbolNode objects, so I am trying to overload its comparison operator.

Here are the relevant parts of the code:

```

//fgSymbol.cpp
fgSymbol* fgSymbolNode::getSymbol() const
{
    return symbol;
}

bool fgSymbolNode::operator==(fgSymbolNode* s)
{
    cout << "Trying to get here.\n";
    return (getSymbol() == s->getSymbol());
}

bool fgSymbolNode::operator==(const fgSymbolNode& s) const
{
    cout << "Trying to get here.\n";
    return (getSymbol() == s.getSymbol());
}

//tester.cpp
int main(int argc, char** argv)
{
    ......
    fgSymbolNode* node = new fgSymbolNode(pattern->getToken(0, 0));
    fgSymbolNode* test = new fgSymbolNode(pattern->getToken(0, 0));
    if (node == test)
    {
        cout << "Success.\n";
        return 0;
    }

    cout << "Failure.\n";
    return 1;
}

```

So, with this code, the result is always 'Failure' and I never see the prints inside the overloaded comparison operator method. 

Why is this? Is it using a built-in method or something?

---

### Post by PaulM1985 on 2010-06-22
You are testing values of both pointers, not the objects.  I think if you used:

if (*thisOne == *thatOne)
{
// success
}

It should work.

Paul

---

### Post by Baerun on 2010-06-22
Oh jeez, that makes me feel stupid. Thanks for that, it was puzzling me for a while. I was expecting something much more complicated. :P

---

