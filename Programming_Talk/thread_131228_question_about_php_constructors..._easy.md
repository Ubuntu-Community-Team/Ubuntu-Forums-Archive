---
title: "question about php constructors... easy"
date: 2006-02-16
forum: Programming Talk
---

### Post by oldmanstan on 2006-02-16
Just a really simple, probably not important question...

I never really did much with OOP, I'm not a programmer so I never had a project big enough for it to make a difference.  However, I've started playing with it in PHP.

So here's the question, in PHP 5 should I declare __construct and __destruct methods in classes using the protected keyword.  It seems like it would be good practice but the tutorials, etc. don't mention it really.  Anyway, just curious.

Also, the PHP documentation is a little... well, short.  Are there any better online references out there?

Thanks

---

### Post by LordHunter317 on 2006-02-16
You should only have protected constructors if you have some special constructor form that you want subclasses to call **and** you don't want the public to have access to.

Otherwise, child classes can just use the public constructors.  

As a general rule, protected methods aren't used very often in any OO language, at least correctly.

I would be curious to know what lead you to this belief.

---

### Post by oldmanstan on 2006-02-16
Well it seemed to make sense that you'd want to hide the constructor from the user (of the class) since it is not necessary (as far as I know) to explicitly call a constructor, it just does it on its own.  However, making it private seemed overkill since then child classes couldn't make use of it.  Therefore I figured people probably declared them protected.

I'm not a "real" programmer so it's probably just my limited knowledge of OOP showing... :)

---

### Post by LordHunter317 on 2006-02-16
> **oldmanstan]Well it seemed to make sense that you'd want to hide the constructor from the user (of the class) since it is not necessary (as far as I know) to explicitly call a constructor, it just does it on its own. [/quote]Yes, you always call the constructor, when you instaniate the object via new:```
class Foo {
    private $name
    
    public function __construct($name) {
        $this-> name = $name said:**
> However, making it private seemed overkill since then child classes couldn't make use of it.  Therefore I figured people probably declared them protected.There's a logical contradiction in your reasoning that would have made it obvious something was wrong ;)  If users don't call constructors, why do protected classes?

---

### Post by oldmanstan on 2006-02-16
Ok, I think I see your point.  But is there anything to stop someone from doing this?

```
$my_class_object->__construct()
```

Because that is what I was trying to avoid.  Also, what would protected be used for exactly? Just curious. Ironically I originally had everything declared public but then I read your post about OOP and decided to try to minimize public declarations since they can introduce bugs... the post was very helpful by the way! I like the traffic analogy.

---

### Post by LordHunter317 on 2006-02-16
[QUOTE=oldmanstan]Ok, I think I see your point.  But is there anything to stop someone from doing this?

```
$my_class_object->__construct()
```[/quote]In PHP?  I don't know.  I don't think it's possible to call the constructor directly, or if they do, you're so far in the realm of undefined behavior it's safe to not care.

> Also, what would protected be used for exactly? Just curious.Protected would be used when you have an interface you want to provide to inherited classes only, but not the public.  An example would be if you had a class hiearchy that all needed to compute a value using the same alogrithm, you might put in the class and use protected inheritance to grant them access.  Realistically, the cases where you want to give just inherited classes the ability to see something are rather small.   Usually it's all or nothing.
 
> Ironically I originally had everything declared public but then I read your post about OOP and decided to try to minimize public declarations since they can introduce bugs...Well, they don't introduce bugs, but they prevent you from controlling data.

Consider a simple case:```
class A {
   public $name;
}
```Let's imagine that the value of $name cannot ever be NULL or empty; maybe it's being stored in an database and it's the primary key for it's records.  Maybe it's used elsewhere and that code require that value.

As this class is written, you have no way of enforcing that.  Code using the A  class must be careful to enforce it by itself.  This is error-prone because people will forget to write the check.

Better is:```
class A {
   private $name;

   public function getName() {
        return $this->name;
   }

   public function setName($name) {
       if ("" == $name)
           throw new Exception("name cannot be empty");
       else
           $this->name = $name;
   }
}
```This is better, because it prevents $name from being set to a null/empty value, when it is changed.  But it doesn't force the value to be set in the first place.  This can be done through a public constructor:```
class A {
   private $name;

   public function getName() {
      return $this->name;
   }

  public function setName($name) {
     if ("" == $name)
         throw new Exception("name cannot be empty");
     else
        $this->name = $name;
  }

  public function __construct($name) {
     if ("" == $name)
       throw new Exception("name cannot be empty");
     else
       $this->name = $name;
   }
}
```Now, there's no way to create A without giving a valid value for A.  It's simply impossible.  

This is one of two reasons to use access levels in OOP: to enforce semantic correctness on your data or operations.  By forbidding direct access to data and using an accessor, you can enforce whatever behavior you want.  You can also wrap an unmanged object (e.g., a database connection) to enforce/limit the allowed behaviors.

The second reason is abstract implementation from contract: now you can write a version of A that gets $name from the database instead of storing it in a variable, if you choose.  With the field, you can't do that.

---

### Post by oldmanstan on 2006-02-16
Ahhhh, gotcha, thank you very much.  I now understand.  OOP is kinda cool now that I'm learning more about it, me likey.

Thanks

---

### Post by sapo on 2006-02-16
I dont use much OOP in php cause i think that php oop is too poor, btw i always used a constructor like this:

[php]class foo {
	var $name;
	function foo($name) {
		$this->name = "This constructor works!";
	}
	function bar() {
		echo $this->name;
	}
}

$test = new foo();
$test->bar();[/php]

This will output: This constructor works!

---

### Post by LordHunter317 on 2006-02-16
That is old style (PHP4) OOP.  It was radically overhauled for PHP5.

---

### Post by oldmanstan on 2006-02-16
So here's another probably easy question... assuming that both methods would work... would it be smarter to have an object's properties set by the constructor (values passed when the instance of the object is created) or would be be smarter to use methods to set the properties one at a time.

It seems to me that the first method would be superior because it would require less code (again, assuming that both options are available).  Also it would force the user to fill all properties.

---

### Post by LordHunter317 on 2006-02-16
[QUOTE=oldmanstan]So here's another probably easy question... assuming that both methods would work... would it be smarter to have an object's properties set by the constructor (values passed when the instance of the object is created) or would be be smarter to use methods to set the properties one at a time.[/quote]It depends on the field.  If a value for the field is mandatory, then not only should the constructor take a value for it, **all constructors** must take a value for it.

If the field value isn't mandatory, then providing overloaded constructors makes the class eaiser for it's users.  That is a good thing: classes should be easy to use and hard to break.  

But it's more work for the programmer.  Sometimes, this work is unwarrented.  For example, in my current application, my classes have "internal" (constructors that can only be called by members of the same library in .NET) constructors that the factory methods use for initalizing the objects they read from the database.  They don't bother with arguments for non-mandatory fields because:[list][*]It's not a public interface[*]Adding the constructors wouldn't save me any work.[/list]

So before jsut providing constructors for every single publically-accessible field, think about whether it matters if this value can be changed at initialization or not.

> Also it would force the user to fill all properties.And if that's the requirement of your class, then you should have only one constructor that enforces this.

---

