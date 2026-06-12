---
title: "C++ STL set, error:no match for 'operator&lt;' in '__x&lt;__y'"
date: 2010-12-11
forum: Programming Talk
---

### Post by AlGorism on 2010-12-11
Hi.

Here is my code:
[PHP]
typedef class term;

class base {
protected:
    string name;
public:
    base(string n);
};
base::base(string n) {
    name=n;
};

class term:base {
private:
    int doc_count;
public:
    term(string n);
};
term::term(string n) : base(n) {
    doc_count=0;
};

int main(int argc, char** argv) {
    set<term> a;
    set<term>::iterator it;
    a.insert(term("aaaa"));
    a.insert(term("cccc"));
    a.insert(term("gggg"));
    a.insert(term("bbbb"));
    for(it=a.begin(); it!=a.end();it++)
        cout << " " << *it;

}
[/PHP]And I'm getting the error which I described in the head.
How can I fix this? I googled a little: Some say that I should overload operator<. 
I just want to print the elements of set to screen, why should I overload the operator<?

---

### Post by MadCow108 on 2010-12-11
> **AlGorism said:**
> 
I just want to print the elements of set to screen, why should I overload the operator<?

because set is an ordered structure.
To build itself it needs to know how to (weakly) compare its elements so it can insert it in the right place internally.

When you don't give it a comparison function/functor as template argument it uses the less<T> which relies on operator< which your class does not have

---

### Post by AlGorism on 2010-12-11
Okay. I re-implemented my term class like this:

[PHP]class term:base {
private:
    int doc_count;
public:
    term(string n);
    bool operator< (const term& x) const{ return name< x.name;};
};[/PHP]

Now, program says that there is no match for 'operator<<'. Now what should I do?

---

### Post by Vaphell on 2010-12-11
you want to print out your class instance - you need to teach your class what to do with << so it can insert proper stuff into ostream

[http://msdn.microsoft.com/en-us/library/1z2f6c2k%28v=vs.80%29.aspx](http://msdn.microsoft.com/en-us/library/1z2f6c2k%28v=vs.80%29.aspx)

---

### Post by nvteighen on 2010-12-12
<rant>Ugh... C++ and its interesting ways...</rant>

There are multiple problems with your code. I'll go in order:

0. I guess this is because you cut and pasted the code from somewhere else, but you forgot:
```

#include <iostream>
#include <set>

using namespace std;

```

I wanted to point this out because of the **using namespace** part. Please, avoid that and use namespace prefixes... I know C++ is verbose and full of weird features and that namespaces make it even more verbose, but they are one of its good and useful features. Of course, they're somewhat irrelevant for a snippet like this, but they let you to define independent "packages" that implement different interfaces, thus adding modularity to your code and avoiding name clashing.

1.
```

typedef class term;

```

You don't need that. Classes are registered as types automatically. Such a typedef could be useful if you needed some type of forward declaration (make the type visible to the compiler before being able to define it), but this isn't the case as your first usage of term comes *after* the class definition.

2. There are syntax errors. Constructors are functions, so don't place a ; after the closing brace.

3. On the problem of printing: your idea seems to just print some objects, right? Ok, there are two approaches to this:

a) Make the class have a "printer" method term::printMe
b) Create a global function with signature:
```

std::ostream& operator<<(std::ostream&, const term&);
// *sigh*

```
that implements how a term should be converted in order to be printed to a ofstream... As you're accessing private/protected data from a procedure that's not part of the class, you'll have to declare it as friend... As cumbersome as this seems, it seems to be the most favored way for some C++ coders.

Your compiler is complaining because you're attempting to use approach b) without having told how a term object is going to be "sent" to std::cout. If you want my opinion, I'd go for approach a), but here's a way to do what you want:

```

#include <iostream> // This also #include's std::ostream
#include <set> // For std::set

class base {
protected:
    std::string name;
public:
    base(std::string n);
};

base::base(std::string n) {
    name = n;
}

class term: base {
private:
    int doc_count;
public:
    term(std::string n);
    bool operator< (const term& x) const;
    
    /* This gives the global procedure access to name member. Yeah, we're
     * "breaching" the interface... but that's how C++ likes to do stuff... */
    friend std::ostream& operator<<(std::ostream&, const term&);
};

term::term(std::string n) : base(n) {
    doc_count = 0;
}

bool term::operator< (const term& x) const {
    return name< x.name;
}

// Our "printer". Note that it isn't a method!
std::ostream& operator<<(std::ostream& out, const term& obj)
{
    /* You have to return an output stream so that you can chain them as:
     * std::cout << someStream << "something" << std::endl; */
    
    return out << obj.name;
}

int main() {
    std::set<term> a;
    std::set<term>::iterator it;
    a.insert(term("aaaa"));
    a.insert(term("cccc"));
    a.insert(term("gggg"));
    a.insert(term("bbbb"));
    for(it = a.begin(); it != a.end();it++)
        std::cout << " " << *it;

}

```

It's cumbersome and ugly. I really suggest you to avoid this "pattern" and just use a normal method...

---

