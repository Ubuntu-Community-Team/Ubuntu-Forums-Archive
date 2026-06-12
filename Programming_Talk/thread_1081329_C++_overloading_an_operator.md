---
title: "C++ overloading an operator"
date: 2009-02-26
forum: Programming Talk
---

### Post by theb3s7 on 2009-02-26
Hello!

I've just started to learn classes and I kinda got stuck into something..

I created a "rational" class, where I store "a" and "b" from a fraction "a/b". What I did managed to do is to compare, using the overloaded operators, two "rational" objects or a "rational" object with an integer.
What I **can't** do, is comparing an integer to a "rational" object. In less words, assuming q,r - "rational" and i - int, I can do q==r, q==i but I can't do an i==q.

Can anyone help me?

This is a small portion, not the whole class:
[PHP]
class rational
{
    double nr,num;
    public:
    rational(int a) { nr=a; num=1; }
    bool operator==(rational);
    bool operator==(int);
};
bool rational::operator==(rational a) { return (nr==a.nr&&num==a.num);}
bool rational::operator==(int a) { return (nr/num == (double)a); }
[/PHP]

---

### Post by geirha on 2009-02-26
The int == rational operator will need to be defined outside the class. If you make it a friend function of the class, the function can use the private members of the class.
E.g.
```

class rational
{
    ...
    friend bool operator==(int, rational);
};

bool operator==(int a, rational b) 
{
    ...
}

```

---

### Post by theb3s7 on 2009-02-26
Thank you very much :)

I tried to define it outside the class but I didn't know I had to also declare it as a friend in my class.

Thanks again for the great answer and.. the greater( as in small :D ) response time :)

---

