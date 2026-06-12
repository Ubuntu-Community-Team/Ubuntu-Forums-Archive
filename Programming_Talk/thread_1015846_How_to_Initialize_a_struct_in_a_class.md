---
title: "How to Initialize a struct in a class"
date: 2008-12-19
forum: Programming Talk
---

### Post by jeevanmgp on 2008-12-19
class aaa
{
protected:
struct bbb
{
   int ccc;
   float ddd;
};
aaa();
};

How shall I initialize the struct elements from the class constructor?

---

### Post by digitalvectorz on 2008-12-19
```

class aaa
{
  protected:
  struct bbb
  {
    int ccc;
    float ddd;
  };
  aaa();
};

```

my C is a little rusty, forgive me.
I think you first need to instantiate an instance of the struct, in order to initialize values to it, i.e.
```

bbb myBbb;
myBbb.ccc = someint
myBbb.ddd = somefloat

```

and you also need to create a constructor for the class to do that.

---

### Post by dwhitney67 on 2008-12-19
> **jeevanmgp said:**
> class aaa
{
protected:
struct bbb
{
   int ccc;
   float ddd;
};
aaa();
};

How shall I initialize the struct elements from the class constructor?

Can you please rephrase your question, or provide additional code.  All you have presented so far is a class definition that contains a struct definition.  The class' constructor is defined (as protected), thus the class cannot be instantiated as it.  Furthermore, you do not have an instantiation of the struct, thus what is there to set?

If your code were:
[php]
class aaa
{
  public:
    aaa(int c = 0, float d = 0.0);

  protected:
    struct bbb
    {
      bbb(int c, float d) : ccc(c), ddd(d) {}

      int   ccc;
      float ddd;
    };

  private:
    bbb m_bbb;
};

aaa::aaa(int b, float d)
  : m_bbb(b, d)
{
}
[/php]

P.S.  A little trivia:  The only difference between a class and a struct is that by default, declarations in a class are private whereas in a struct they are public.

---

### Post by jeevanmgp on 2008-12-20
Thanks guys.. I think I got what I want.. thanks..

---

