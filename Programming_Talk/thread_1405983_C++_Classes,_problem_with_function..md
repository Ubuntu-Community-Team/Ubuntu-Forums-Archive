---
title: "C++ Classes, problem with function."
date: 2010-02-13
forum: Programming Talk
---

### Post by Enrui on 2010-02-13
When I run my code through G++ I get the following error. I recently re-wrote my code on the advice of DWhitney and found that I'm not sure how to use certain features. 

Here's my problem...


error: request for member 'returnModel' in 'Ferrari' which is of non-class type 'car*'

now I'm aware that I have the following function defined within the class. 

returnModel()
{
return (carModel);
}

I have also defined Ferrari within main()

car* ferrari = new car ( ...data here...)

Now I entered this code. 

cout << ferrari.returnModel() 

and got the above error, could someone supply a hint.

---

### Post by dwhitney67 on 2010-02-13
See if you can put the following to use:
```

#include <string>
#include <iostream>

class Car
{
public:
   ...

   std::string getModel() const
   {
      return carModel;
   }

   ...

private:
   std::string carModel;
   ...
};

int main()
{
   using namespace std;

   Car* ferrari = new Car("Ferrari", 280, 250, 275000);

   cout << ferrari->getModel() << endl;

   delete ferrari;
}

```

---

### Post by Enrui on 2010-02-13
apart from

delete ferrari; 

It seems to like it. 

-> is new to me, what is it? (so I can go and research)

delete ferrari gives an error

undefined reference to 'cars::~cars()'
collect2: ld returned 1 exit status.

---

### Post by Zugzwang on 2010-02-13
> **Enrui said:**
> undefined reference to 'cars::~cars()'


This means that you declared a destructor for the class "cars", but didn't define it.

---

### Post by dwhitney67 on 2010-02-13
If you declare a destructor for your class, then you need to implement it as well.

I presume you have something like this in your class:
```

class Cars
{
public:
   ...

   ~Cars();
};

```
You can implement the destructor within the class, or outside of it, the choice is yours.  Here are the two ways:
```

class Cars
{
public:
   ...

   ~Cars() {}
};

// or

Cars::~Cars() {}

```

---

### Post by Enrui on 2010-02-13
Perfect, thanks.

---

