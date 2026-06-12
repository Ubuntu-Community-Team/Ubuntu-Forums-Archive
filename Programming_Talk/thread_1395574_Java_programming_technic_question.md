---
title: "Java programming technic question"
date: 2010-02-01
forum: Programming Talk
---

### Post by hoboy on 2010-02-01
I was ready some Android codes, then I saw this:
findViewById(R.id.myButton).setOnClickListener(new View.OnClickListener() {
    public void onClick(View v) {
        // Do stuff
    }
});
I just don't understand how you can have  onClick(View v) inside
public void onClick(View v) {
        // Do stuff
    }
because to me findViewById(R.id.myButton).setOnClickListener(new View.OnClickListener() {
  
}); is a method, how can one have one method inside an other ?
I am aware that one can call a method inside another, this is not the case, or I am wrong.
So i am confused by this.

---

### Post by nvteighen on 2010-02-01
Ok, I don't know any Java and less about Android, so take this post with caution. 

It reminds me to a closure-like construction... but according to the SDK docs ([http://developer.android.com/reference/android/view/View.OnClickListener.html](http://developer.android.com/reference/android/view/View.OnClickListener.html)), it's just that onClick is an abstract void (= virtual void, in C++ lingo... I guess) method you just can override to serve your will during the object's construction.

I see this as closure-like because your defining an anonymous function and assigning it as "onClick" on a particular **instance** (not class, which would have been regular polymorphism). Inside onClick I bet you'll be able to catch bindings from the outside and therefore have a closure... :) (unless Java places some stupid restriction here I'm unaware of).

---

### Post by CptPicard on 2010-02-01
If you used the [ CODE ] tags it would be much easier to read... but, what you have there is the anonymous inner class, a very typical Java idiom. Google for them. In essence, you can provide an ad hoc implementation of some class/interface *in situ* where you need it. Typically used for callbacks and the like, and I really wish C++ had something similar...

@nvteighen, it looks like a closure but is not quite, and that's just a dumb design decision on Java's part. Namely there is a kind of "read only" closure -- if you want to alter state in it, you need to resort to a wrapper hack...

---

### Post by hoboy on 2010-02-01
> **CptPicard said:**
> If you used the [ CODE ] tags it would be much easier to read... but, what you have there is the anonymous inner class, a very typical Java idiom. Google for them. In essence, you can provide an ad hoc implementation of some class/interface *in situ* where you need it. Typically used for callbacks and the like, and I really wish C++ had something similar...

@nvteighen, it looks like a closure but is not quite, and that's just a dumb design decision on Java's part. Namely there is a kind of "read only" closure -- if you want to alter state in it, you need to resort to a wrapper hack...

Thanks CptPicard.
I have payed attention to your great contribution to this forum.

I have google and here is a good link about the topic

[http://mindprod.com/jgloss/anonymousclasses.html](http://mindprod.com/jgloss/anonymousclasses.html)

---

### Post by CptPicard on 2010-02-01
By the way, once you get used to writing code in terms of anonymous classes, you *really* start appreciating a good IDE such as Netbeans or Eclipse that knows most of what you want from the code you've already written, fills in the blanks, keeps your code correct and allows for fast refactoring.

My typical Java programming methodology has become much more "agile" since adopting that style of coding -- whenever I need some kind of interface/class in some method invocation, my first instinct these days is to just hack up a quick anonymous class in that spot and let the IDE fill it in according to what is required. If it seems like the class grows into something bigger, I just crack it out in the IDE into a "proper" top-level class and either extract the interface or create some sort of inheritance hierarchy by pushing up stuff into a base class.

This way, I find my object model of the program grows organically instead of me having to design it completely before programming (which is IMO an insane way of viewing programming)...

---

### Post by nvteighen on 2010-02-01
> **CptPicard said:**
> 
@nvteighen, it looks like a closure but is not quite, and that's just a dumb design decision on Java's part. Namely there is a kind of "read only" closure -- if you want to alter state in it, you need to resort to a wrapper hack...

It looked to good to be real... :(

---

### Post by CptPicard on 2010-02-01
> **nvteighen said:**
> It looked to good to be real... :(

The saddest part there is that AFAIK there is no real reason to not allow writing into the visible variables. Java's powers that be just decided that it's too "dangerous" to possibly allow different threads to alter each others' stacks, so they "protected the programmers" by prohibiting it.

---

### Post by Reiger on 2010-02-01
I am not sure I follow you entirely there, though. You can do anything and everythin with the object as you could with its supertype. Furthermore you can also access methods of the enclosing class.

```

public abstract class Test {
  public abstract void test1();
  public void test2(Test t) { 
    String old = this.s; 
    this.s = t.toString(); 
    t.setString(old);
  }
  private Test innerTest() { 
     public void test1() {
       System.out.pritnln("Before:");
       System.out.println(this);
       test2(this);
       System.out.println("After:");
       System.out.println(this);
     }
     
  };
  private String s="Test";
  public void setString(String newString) { this.s = newString; }
  public String toString() { return s; }
}
class Test2 implements Runnable() {
  void test() { System.out.println("Enclosing object method"); }
  Object test = new Object() { 
    public String toString() {
      test();
      return "Returns from inner object method";
    } 
  };
  public void run() { System.out.println(test); }
}

```

---

