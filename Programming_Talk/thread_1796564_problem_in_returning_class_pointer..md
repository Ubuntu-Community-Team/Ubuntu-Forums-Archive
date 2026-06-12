---
title: "problem in returning class pointer."
date: 2011-07-04
forum: Programming Talk
---

### Post by c2tarun on 2011-07-04
```

#include <iostream>
using namespace std;
class loc {
int longitude, latitude;
public:
loc() {}
loc(int lg, int lt) {
longitude = lg;
latitude = lt;
}
void show() {
cout << longitude << " ";
cout << latitude << "\n";
}
loc operator+(loc op2);
};
// Overload + for loc.
loc loc::operator+(loc op2)
{
loc temp;
temp.longitude = op2.longitude + longitude;
temp.latitude = op2.latitude + latitude;
return temp;
}
int main()
{
loc ob1(10, 20), ob2( 5, 30);
ob1.show(); // displays 10 20
ob2.show(); // displays 5 30
ob1 = ob1 + ob2;
ob1.show(); // displays 15 50
return 0;
}

```

In the above code in operator overloading function we are creating a local class object and returning its reference. But since we are not creating this object on heap there should be a segmentation fault error while executing. But its not happening. Can anyone please explain me why is this happening?

---

### Post by Arndt on 2011-07-04
> **c2tarun said:**
> ```

#include <iostream>
using namespace std;
class loc {
int longitude, latitude;
public:
loc() {}
loc(int lg, int lt) {
longitude = lg;
latitude = lt;
}
void show() {
cout << longitude << " ";
cout << latitude << "\n";
}
loc operator+(loc op2);
};
// Overload + for loc.
loc loc::operator+(loc op2)
{
loc temp;
temp.longitude = op2.longitude + longitude;
temp.latitude = op2.latitude + latitude;
return temp;
}
int main()
{
loc ob1(10, 20), ob2( 5, 30);
ob1.show(); // displays 10 20
ob2.show(); // displays 5 30
ob1 = ob1 + ob2;
ob1.show(); // displays 15 50
return 0;
}

```

In the above code in operator overloading function we are creating a local class object and returning its reference. But since we are not creating this object on heap there should be a segmentation fault error while executing. But its not happening. Can anyone please explain me why is this happening?

Why do you want or expect a segmentation fault to happen?

Please use CODE tags to enclose the code, so that its indentation remains visible.

Is this homework?

---

### Post by c2tarun on 2011-07-04
> **Arndt said:**
> Why do you want or expect a segmentation fault to happen?

Please use CODE tags to enclose the code, so that its indentation remains visible.

Is this homework?

I used code but it was like this in book :( sorry for that.
This is not a homework. I was just having doubt. Because if we create a variable on stack inside a function then that variable gets destroyed when function ends and we cannot use its address outside, if we return that variable than its value gets copied.
But in case of object when we return its values are not copied.
This is my doubt, since we are creating object temp on stack it will get destroyed when the function will end. On returning its reference will be passed, since it is deallocated how can we use its reference?

---

### Post by nvteighen on 2011-07-04
> **c2tarun said:**
> 
Because if we create a variable on stack inside a function then that variable gets destroyed when function ends and we cannot use its address outside, if we return that variable than its value gets copied.But in case of object when we return its values are not copied.This is my doubt, since we are creating object temp on stack it will get destroyed when the function will end. On returning its reference will be passed, since it is deallocated how can we use its reference?

You have a misconception there. When you return an object, you copy it... because objects are variables. temp is a new loc object, not a reference, so when returning it, you're returning a new object.

Remember, references in C++ are always declared explicitly as *type& variable*. If something isn't declared like that, it is passed around by value.

Now, even if you had a reference, the segfault may not occur, depending on the compiler and how memory is laid down. Stritcly speaking, a dangling reference or pointer produces undefined behaivor, which may lead to a segfault or not (e.g. accessing garbage values).

---

### Post by c2tarun on 2011-07-04
> **nvteighen said:**
> You have a misconception there. When you return an object, you copy it... because objects are variables. temp is a new loc object, not a reference, so when returning it, you're returning a new object.

Remember, references in C++ are always declared explicitly as *type& variable*. If something isn't declared like that, it is passed around by value.

Now, even if you had a reference, the segfault may not occur, depending on the compiler and how memory is laid down. Stritcly speaking, a dangling reference or pointer produces undefined behaivor, which may lead to a segfault or not (e.g. accessing garbage values).


Got it sir :) thanks a lot. I was in misconception that whenever we return objects we return its reference.

---

