---
title: "question on inheritance"
date: 2009-08-18
forum: Programming Talk
---

### Post by ooobooontooo on 2009-08-18
Hi,

I've been wondering why this works the way it does. I have 2 classes:
> class Super {
    private void hi() {
        System.out.println("hi");
    }

    public void doit() {
        hi();
    }
}

class Sub extends Super {
    private void hi() {
        System.out.println("hi from sub");
    }
}

Then in main say I do this:
> Sub sub = new Sub();
sub.doit();
Why does it print "hi" and not "hi from sub"? I'm looking for a somewhat detailed answer. Thank you.

Please explain why/how it point to the super class's hi method.

In addition, when the hi methods are made public, it prints "hi from sub". I would also like to know how/why this happens as well. Thank you.

---

### Post by lisati on 2009-08-18
I might be mistaken, but my guess is that because doit is defined in Super, then Super's hi() will be used.

---

### Post by ooobooontooo on 2009-08-18
> **lisati said:**
> I might be mistaken, but my guess is that because doit is defined in Super, then Super's hi() will be used.

I agree and thank you for your speedy answer. But because Sub inherits Super, and it has its own hi method, I sometimes think that it should point to the subclass's hi method instead. So, is this reference to Super.hi built at compile time, or ... how does it end up pointing to the superclass's hi method?

Also, if you make the hi methods public. Then it will print "hi from sub". Why might this be?

---

### Post by c0mput3r_n3rD on 2009-08-18
It's because you're calling the super classes doit function, which in turn calls it's own hi() function, not the subs.  You have to override the supers doit() function to call it's own hi() function.

---

### Post by ooobooontooo on 2009-08-18
> **c0mput3r_n3rD said:**
> It's because you're calling the super classes doit function, which in turn calls it's own hi() function, not the subs.  You have to override the subs doit() function to call it's own hi() function.

Thank you too for your answer. But I would like to why/how it does this. Thank you.

---

### Post by c0mput3r_n3rD on 2009-08-18
Because when you inherit a supers class, it takes the supers functions as is.  If you want them to do something, you have to override the supers functions.  So, when you call the inherited doit() function, it looks up a class to the supers, and looks at the supers hi() function.

---

### Post by ooobooontooo on 2009-08-18
> **c0mput3r_n3rD said:**
> Because when you inherit a supers class, it takes the supers functions as is.  If you want them to do something, you have to override the supers functions.  So, when you call the inherited doit() function, it looks up a class to the supers, and looks at the supers hi() function.

Yes, but why does it look at the super's hi method instead of the subclass's hi method? Also, why does this change when the hi methods are made public?

---

### Post by nmccrina on 2009-08-18
> **ooobooontooo said:**
> Also, why does this change when the hi methods are made public?

That is actually a good question. I'm playing around with it, but right now I'm confused too! :popcorn:

---

### Post by nmccrina on 2009-08-18
[http://home.cogeco.ca/~ve3ll/jatutor5.htm]("http://home.cogeco.ca/~ve3ll/jatutor5.htm")

OK, at this place ^, I found an obscure statement that says "you cannot override private methods". So I guess when both of your hi methods were private, you were not actually overriding it in your subclass (I guess the compiler just ignored it when looking for a hi method, maybe?), so the hi method in the superclass executed. When they were both public, you could then override the hi method, so the hi method in the subclass was called. Hope this makes sense, you can always check out that tutorial I guess :)

---

### Post by dwhitney67 on 2009-08-18
As it has been already stated, if you are going to allow one to override a base-class' function, the function needs to be made public or protected; not private.

If you want to develop a base class such that you want to force sub-classes to define/implement a particular method, then you would go with the "abstract" concept.

Here's a sample:
```

bstract class Base
{
   public void doit() {
      doSomething();
      doSomethingElse();
   }

   protected Base() {}

   protected void doSomething() {
      System.out.println("Base.doSomething()");
   }

   // declare abstract method... no implementation provided.
   protected abstract void doSomethingElse();
}

public class Sub extends Base
{
   public Sub() {
      super();
   }

   protected void doSomething() {
      System.out.println("Sub.doSomething()");
   }

   // declare abstract method, and provide implementation.
   protected void doSomethingElse() {
      System.out.println("Sub.doSomethingElse()");
   }

   public static void main(String[] args) {
      Sub sub = new Sub();
      sub.doit();
   }
}

```

---

### Post by issih on 2009-08-18
Its about scoping, the whole point of a private method/field is that it is only available to be used by other members of that class.

You can't call it from outside the class, from a subclass, a superclass, ONLY from within the class that the private method is defined on.

By setting its access modifier as protected you allow members of the class hierarchy to access the method, and consequently the "hi" methods on the different classes become accessible to each other, and you will get the behaviour you expect.

You still won't be able to access the "hi" methods from outside the classes (e.g. from a variable typed as one of the classes) for that you need to set the methods to public.

All been said above, but that is the logic behind the behaviour.

---

