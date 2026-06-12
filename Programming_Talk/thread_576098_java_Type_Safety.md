---
title: "java Type Safety"
date: 2007-10-14
forum: Programming Talk
---

### Post by keeler1 on 2007-10-14
I have written some java code and have about 20 of these warning

```
Severity and Description	Path	Resource	Location	Creation Time	Id
Type safety: The expression of type Polynomial needs unchecked conversion to conform to Polynomial<Complex>	Proj1/src/proj1	Proj1.java	line 267	1192408594606	529
```

Without posting my entire project I am working on it would be kind of hard to show why the warning is occuring. 

 Basically I have an interface called Number

I have a Real and Complex classes that implement the number interface.

Methods of the interface that are screwing me up are 

```
public Number add(Number n)
```
and
```
public Number multiply(Number n)
```

Then I have another Polynomial<T extends Number> class which extends Hashtable<Integer,Number>

There is casting to the desired type in both implementations of each classes add and multiply function.

The polynomial class has an add function which adds two like polynomials together.  It wont even compile if a polynomial of a different type is added because it is parameterized to only allow the same type as the one the method is being called on.

Therefore I know, that there is not a way to blow up the program by adding to unlike polynomials, but it keeps saying I need to convert things for type safety.  I also do not understand this because the polynomial add function returns a parameterized polynomial of the same type as the polynomial it was called on.

So there is really no way that the polynomial that gets the error is not the same.

Is there any easy way to get rid of the warnings.  I am writing the project for school and warnings get points taken off.  And I really dont want to get points off for nothing.

---

