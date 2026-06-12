---
title: "C++ passing around stack object"
date: 2010-09-16
forum: Programming Talk
---

### Post by ja660k on 2010-09-16
Hey all, 
okay... here's what i need.

i need to pass a std::stack into another class method, that method will then add data.
and i can then use that data in my class that called the method.

im not very good with pointers in C/C++ so any help is good.
what i have so far is

definition in caller class. 
[PHP]
std::stack<std::string> *st;
[/PHP]

calling
[PHP]
AnotherClass.getElements(&st);
[/PHP]

prototype in AnotherClass
[PHP]
void getElements(std::stack<std::string> *);
[/PHP]

and i get this error
```

void TreeNode::getElements(std::stack<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::deque<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >*)’:
treeNode.cpp:48: error: no matching function for call to ‘TreeNode::getElements(std::stack<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::deque<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >**)’
treeNode.cpp:45: note: candidates are: void TreeNode::getElements(std::stack<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::deque<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >*)
treeNode.cpp:54: error: no matching function for call to ‘TreeNode::getElements(std::stack<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::deque<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >**)’
treeNode.cpp:45: note: candidates are: void TreeNode::getElements(std::stack<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::deque<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >*)
make: *** [treeNode.o] Error 1

```

:(

---

### Post by dwhitney67 on 2010-09-16
Do not declare the STL stack object as a pointer; it buys you nothing.  Internally, the stack object will manage memory (from the heap) for items that you add to the stack.

As for passing it to a function, pass it by reference.  For example:
```

void AnotherClass::getElements(std::stack<std::string>& theStack)
{
}

```

If you want to save yourself a lot of typing, typedef the stack definition.  For example:
```

typedef std::stack<std::string> StringStack;

...

void AnotherClass::getElements(StringStack& theStack)
{
}

```

Usage would be something like:
```

...

StringStack  aStack;
AnotherClass ac;

ac.getElements(aStack);

...

```

---

### Post by NovaAesa on 2010-09-16
Another way to do it could be to have the other method just add its elements to an empty stack and then pass that stack back. Once it is back, then just merge the stacks. This could work if you're one of those people who are funny about having inout parameters.

---

### Post by dwhitney67 on 2010-09-16
> **NovaAesa said:**
> Another way to do it could be to have the other method just add its elements to an empty stack and then pass that stack back. Once it is back, then just merge the stacks. This could work if you're one of those people who are funny about having inout parameters.

In certain cases this might be appropriate, but in others it could be costly in terms of wasted CPU cycles to copy data.  For example, the following would **not** be wise if efficiency is required:
```

typedef std::stack<std::string> StringStack

...

StringStack getInput()
{
   StringStack theStack;

   // populate the stack with string data
   // ...

   return theStack;
}

```

---

### Post by pling on 2010-09-17
> **NovaAesa said:**
> Another way to do it could be to have the other method just add its elements to an empty stack and then pass that stack back. Once it is back, then just merge the stacks. This could work if you're one of those people who are funny about having inout parameters.

That question would be an instant fail at a job interview - I can understand why you'd make the suggestion if you're, say,  a Python programmer, but C++ is different in very important ways. If the return stack is large then C++ will create a large return object to pass back on the machine's stack. This isn't an issue with Java or scripting languages because they'd return a pointer instead; this isn't an option C++ because of the lack of a garbage collector. If you don't get this stuff and want to program in C++ read Meyer's "Effective C++". Being "funny about having inout parameters" isn't really an option in C++.

To program competently in C++ you have to understand the execution and memory models - if you don't your programs will be slow and buggy.

---

### Post by NovaAesa on 2010-09-17
> **pling said:**
> If the return stack is large then C++ will create a large return object to pass back on the machine's stack. This isn't an issue with Java or scripting languages because they'd return a pointer instead; this isn't an option C++ because of the lack of a garbage collector.
You are correct, you obviously wouldn't want to return the actual stack object, as its size could be indeterminately large depending on what the function creating the stack put into it. I was thinking more along the lines of creating the stack object on the heap and then returning (by value) a pointer to the stack object. Obviously it would have to be the responsibility of the calling function to clean up the heap memory used by the stack once it was done with it.

---

### Post by dwhitney67 on 2010-09-17
> **NovaAesa said:**
> You are correct, you obviously wouldn't want to return the actual stack object, as its size could be indeterminately large depending on what the function creating the stack put into it. I was thinking more along the lines of creating the stack object on the heap and then returning (by value) a pointer to the stack object. Obviously it would have to be the responsibility of the calling function to clean up the heap memory used by the stack once it was done with it.

Really?  Come on... what would be the point of such?

---

