---
title: "I'm lost: question on C++ with templates"
date: 2009-11-15
forum: Programming Talk
---

### Post by fr4nko on 2009-11-15
Hi,

I'm lost with a problem compiling a C++ file that use templates. 

Here the code that does not compile:
[PHP]template<class num_type>
void units<num_type>::get_limits (std::vector<num_type> &x, num_type &inf, num_type &sup)
{
  std::vector<num_type>::iterator j = x.begin();
    
  inf = x[j];
  sup = x[j];
[/PHP]

The error is given by the line that declares the 'iterator' j. If I write:

std::vector<int>::iterator j = x.begin();

the compilator does not complain but if I use 'num_type' it does show an error. It seems that it does not want to take the ::iterator on vector<num_type>.

Please help me, I'm lost!!!

Francesco

---

### Post by johnl on 2009-11-15
Try:

```

template<class num_type>
void units<num_type>::get_limits (std::vector<num_type> &x, num_type &inf, num_type &sup)
{
  typename std::vector<num_type>::iterator j = x.begin();
    
  inf = x[j];
  sup = x[j];  

```

With templates,  the compiler sometimes can't tell what's what.  You have to help it sometimes, by telling it that  'std::vector<num_type>::iterator' names a type.

Hope this helps.

---

### Post by fr4nko on 2009-11-15
It works!! Thank you very much.

C++ complexity kills me :-)
I believe this is the reason I prefer ocaml or C to C++.

Francesco

---

### Post by dribeas on 2009-11-16
To add a little precision to the discussion.

Templates go through a two step verification process. In the first step the instantiating parameters are not used for anything but template deduction (determining if available, what specialization to use). During this step, the compiler cannot know what dependent names are (a name is dependent if it 'depends' (duh!) on a template argument).

Note that since the instantiating arguments are not used, the compiler cannot really know what a dependent name is:

```

template <typename T>
struct test {
   typedef T t;
};
template <>
struct test<int> {
   static const int t = 0;
};
template <typename T>
void f() {
   test<T>::t a; // this is dependent on T, what is it?? well, it depends... on T
}

```

At this point there are a fixed set of rules, and the compiler will assume that 'test<T>::t' is an static member of the template (as in test<int>), and will fail to compile as you are using it in place of a type. You must instruct the compiler during the first pass to consider that dependent name as a type by using the 'typename' keyword. 

```

template <typename T> void f() {
   typename test<T>::t a;
}

```

This template will go over the first compilation pass successfully as its syntax is correct, but will fail to compile if the template argument is an integer. After the first pass is completed the real type is substituted into the template and then the template is compiled:

```

int main() {
   f<double>(); // correct
   //f<int>();  // compilation error in the second pass.

```

Note that 'std::vector<int>::iterator' is not a dependent name, as all types are fixed. At this point the compiler can instantiate the vector template with int as argument and check that iterator is a type.

---

