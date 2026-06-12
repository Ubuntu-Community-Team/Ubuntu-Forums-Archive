---
title: "Ruby and class code execution"
date: 2010-09-11
forum: Programming Talk
---

### Post by cybo on 2010-09-11
i'm trying to learn ruby and ruby on rails. the book i'm reading has some code and i have a question about the output. here is the code:
```

class C
  puts "Just inside class definition block. Here is self:"
  puts self

  @v = "I'm an instance variable initialized to a string"
  puts "And here's the instance variable @v, belonging to self:"
  puts @v
  
  def show_var
    puts "Inside an instance method definition block. Here's self:"
    puts self
    puts "And here's the instance variable @v, belonging to self:"
    puts @v
  end
end

c = C.new

```

The output from this code is as follows:
> 
Just inside class definition block. Here is self:
C
And here's the instance variable @v, belonging to self:
I'm an instance variable initialized to a string


the question is why the code that is not in a method is executed? this code is not located in the initialize method, and yet it is still executed. can someone explain?

any help is appreciated.

---

### Post by dv3500ea on 2010-09-11
The code in the class is executed when the class is declared.
The code in an 'initialize' method is executed when the class is instantiated, creating an object instance. (C.new)

If you omit the ```
c = C.new
```, you will get the same output.

---

### Post by cybo on 2010-09-12
> **dv3500ea said:**
> The code in the class is executed when the class is declared.
The code in an 'initialize' method is executed when the class is instantiated, creating an object instance. (C.new)

If you emit the ```
c = C.new
```, you will get the same output.

any reason why? is that the way ruby does things? every time the class is created the code in the class is executed?

---

### Post by dv3500ea on 2010-09-12
> **cybo said:**
> any reason why? is that the way ruby does things? every time the class is created the code in the class is executed?

The class is created (declared) only once. The code within the body of the class is executed only when the class is declared. If this was not done then this code would never be executed.

---

### Post by cybo on 2010-09-12
thanks for the help. it helped

---

### Post by dv3500ea on 2010-09-12
> **cybo said:**
> thanks for the help. it helped

Help generally does ;)

---

