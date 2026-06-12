---
title: "c++ templates, operator overloading and const  will not compile"
date: 2009-07-10
forum: Programming Talk
---

### Post by arkangel on 2009-07-10
Hi ubuntians 
This piece of code is not working although I see no mistake , 

```


     Node2D<precType> operator+(const Node2D<precType>  &B_ ){
    	Node2D<precType> tmp(this->x()+B_.x(), y_+B_.y()) ;
        return  tmp;
    }


error: 
../src/main.cpp: In function ‘int main(int, char**)’:
../src/elements/node2d.hpp: In member function ‘Node2D<precType> Node2D<precType>::operator+(const Node2D<precType>&) [with precType = double]’:
../src/main.cpp:64:   instantiated from here
../src/elements/node2d.hpp:74: error: passing ‘const Node2D<double>’ as ‘this’ argument of ‘precType Node<precType>::x() [with precType = double]’ discards qualifiers
../src/main.cpp:64:   instantiated from here
../src/elements/node2d.hpp:74: error: passing ‘const Node2D<double>’ as ‘this’ argument of ‘precType Node2D<precType>::y() [with precType = double]’ discards qualifiers
../src/elements/node.hpp: In member function ‘precType Node<precType>::dot(const Node<precType>&) [with precType = double]’:
../src/main.cpp:101:   instantiated from here
../src/elements/node.hpp:46: warning: no return statement in function returning non-void
../src/elements/node.hpp: In member function ‘precType Node<precType>::dot(const Node<precType>&, const Node<precType>&) [with precType = double]’:
../src/main.cpp:101:   instantiated from here



```

Node2D is a 2d vector and precType =int/float/double , with coordinates x_ and y_

However this  works 

```


     Node2D<precType> operator+( Node2D<precType>  B_ ){
    	Node2D<precType> tmp(x_+B_.x(), y_+B_.y()) ;
        return  tmp;
    }


```


Am I messing with the constant-ness  by passsing the parameter 

Any Idea  thanks

---

### Post by Zugzwang on 2009-07-10
According to the error message, the problem is that the "x()" and "y()" functions are are not declared to be const.

---

### Post by arkangel on 2009-07-10
yes they are  

I still dont get it ?

---

### Post by Zugzwang on 2009-07-10
So in the class definition you really have some function of the following form: ?

```

precType x() const { return x_; };

```

---

### Post by arkangel on 2009-07-10
ah ok 

I had 
precType const  x() { return x_; };

thansk!

---

### Post by Sockerdrickan on 2009-07-10
a const member means it won't change the instance values

---

