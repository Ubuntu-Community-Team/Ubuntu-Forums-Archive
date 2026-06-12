---
title: "C++ structish template syntax problem"
date: 2008-12-22
forum: Programming Talk
---

### Post by tradet on 2008-12-22
A stumped version of my code. I'm having syntax problems.

```
template<typename T> 
class SomeTree {
	struct SomeNode {
		std::list<SomeNode*> children;
		T *obj;
		void Clear();
		
	};
	int Size();
};
```

```
template<typename T> 
int SomeTree<T>::SomeNode::Size()
{
	//won't find anything called 'SomeTree<T>::SomeNode
	for(std::list<SomeTree<T>::SomeNode*>::iterator it = children.begin(); it != children.end(); ++it)
	{
		//do stuff
	}
}
```
So how do I declare a 'SomeNode pointer' inside a list to be an iterator?
I've tried just 'SomeNode*' - "SomeNode *node;" works when not used with the list and some other different constructs but now I'm stuck and lost.

---

### Post by dwhitney67 on 2008-12-22
From the code you posted, Size() is not part of the struct SomeNode, but instead part of class SomeTree.

Also, you are attempting to use "children", but you have not instantiated an object for struct SomeNode; you have only defined struct SomeNode.

Perhaps you meant to have a member data object of type struct SomeNode in the class SomeTree??

---

### Post by tradet on 2008-12-24
Dang I was a bit unclear again.

```
template<typename T> 
class SomeTree {
	struct SomeNode {
		std::list<SomeNode*> children;
		T *obj;
		int Size();
		
	};
	int Size();
	SomeNode *topNode;
	SomeNode *insertNode;
};
```
```
template<typename T> 
int SomeTree<T>::SomeNode::Size()
{
        //works 	
        if(children.empty) return 1;
        //won't find anything called 'SomeTree<T>::SomeNode
	for(std::list<SomeTree<T>::SomeNode*>::iterator it = children.begin(); it != children.end(); ++it)
	{
		//do stuff
	}
}
```
I'm having a function Size() in both SomeTree and SomeNode. I actually have a lot more code than is shown so the copy paste went all bad, sorry about that.

I wanted to create a class which would only be defined for SomeTree, by declaring it inside of it. I'm sure it should work and it has been working fine up until I want to create a iterator to traverse children.

I guess I could declare SomeNode outside of SomeTree but that would be slightly sloppy. Also I'm curious where I've gone wrong and I would want to do it this way, if possible. If not just to see that it works.

---

### Post by dwhitney67 on 2008-12-24
The compile problem you are having is a nuance of GCC that is not explained well in all tutorials/documents.  If one digs enough, the workaround can be found.

So here's how to solve the problem.  First of all, since I hate messy code, I defined a typedef for your STL list definition (its called Children).  I also changed the definitions of your Size() methods to return a size_t and to be declared as const methods.

But the most important modification... which will interest you... is the use "typename" keyword for the declaration of your iterator in the for-loop.  I don't even pretend to understand why in the case of templates this keyword is necessary when declaring an iterator, but it is.

[php]
#include <list>

template<typename T>
class SomeTree {
        struct SomeNode {
                typedef std::list<SomeNode*> Children;

                Children children;
                T *obj;
                size_t Size() const;

        };
        size_t Size() const;
        SomeNode *topNode;
        SomeNode *insertNode;
};

template<typename T>
size_t SomeTree<T>::SomeNode::Size() const
{
        if (children.empty()) return 1;

        for(typename Children::const_iterator it = children.begin(); it != children.end(); ++it)
        {
                //do stuff
        }
}

int main()
{
  SomeTree<int> st;
}
[/php]

---

### Post by tradet on 2008-12-27
Wonderful, thanks a lot!

---

### Post by dribeas on 2008-12-27
> **dwhitney67 said:**
> 
But the most important modification... which will interest you... is the use "typename" keyword for the declaration of your iterator in the for-loop.  I don't even pretend to understand why in the case of templates this keyword is necessary when declaring an iterator, but it is.


Templates follow special compilation rules that differ from how the rest of the code is compiled. First a template method will only be compiled if it is used. The compiler will not even look at the code of those methods that are not used in the program.

When the compiler find that a method is used it will start the compilation process, that has a two step verification. During the first pass, the template code is checked for validity without considering the template parameters. Then, once it has been checked for validity, the template parameters are substituted and the compiler will check for correctness.

During the first pass, the compiler does not know what the templated parameter is. In particular:

```

template <typename T>
void f() {
   std::cout << T::x << std::endl; 
}

```

With the code above the compiler cannot know what T:: x is. It could be a member method pointer, a static  variable or a type defined inside type T. The compiler must assume that it is either a member method or a static variable (both of which are similar for the verification process). Now, in some cases it is a data type, and it is up to the programmer to inform the compiler.

```

template <typename T>
void f() {
   typename T::x tmp;
}

``` 

In this last case we inform the compiler that the type T must have an internal type T:: x.

Making the long story short, you must provide the typename keyword before any template argument dependant type (that is, any type that depends on the parameters of the template).

---

