---
title: "[SOLVED] C++: Vector iterator won't work in templates"
date: 2008-07-13
forum: Programming Talk
---

### Post by Zugzwang on 2008-07-13
Hey all,

I must admit that I have no clue what's wrong with the following code:
[PHP]
1 #include <vector>
2 
3 template<typename A> void addAllVector(std::vector<A> &dest, std::vector<A> &src) {
4    std::vector<A>::iterator it;
5    for (it = src.begin();
6      it!=src.end();
7      it++) {
8	    dest.push_back(*it);
9    }
10 }
12
13 int main() {
14    return 0;
15 }
[/PHP]

The error from g++ 4.1.3 I get when trying to compile (command: "g++ test.cpp") is:
```

test.cpp: In function 'void addAllVector(std::vector<A,  std::allocator<_CharT> >&, std::vector<A, std::allocator<_CharT> >&)':
test.cpp:4: error: expected `;' before 'it'
test.cpp:5: error: 'it' was not declared in this scope

```

Does anyone have an idea why the compiler doesn't want to accept the iterator declaration?

---

### Post by hod139 on 2008-07-13
Change line 4 to:
```

typename std::vector<A>::iterator it;

```You need to add the keyword typename because the type of the iterator is unknown until instantiation, since it depends on the type A.

**Edit:**
As an aside, may I also suggest the following changes:
[php]
template<typename A> 
void addAllVector(std::vector<A> &dest, const std::vector<A> &src) {
    typename std::vector<A>::const_iterator it;
    for (it = src.begin(); it!=src.end();  ++it) {
        dest.push_back(*it);
    }
}
[/php]Since you are not changing the source vector, you should protect it with const, and use a const_iterator.  More importantly, you should do ++it, not it++.  The latter has to call srs's copy constructor, and if A is a complicated class that could be an expensive call.  A good rule of thumb is to always us ++itr, never itr++ unless you really want the side effect involved with the post increment.

---

### Post by StOoZ on 2008-07-13
are you sure that calling an iterator of a class with the post ++ calls the copy contructor? why is that?
never seen that documented anywhere.

---

### Post by hod139 on 2008-07-13
Yep, I'm really sure.  See faq [13.15]("http://www.parashift.com/c++-faq-lite/operator-overloading.html#faq-13.15") for more details.  If you are still uncertain why itr++ calls the copy constructor feel free to post back here. General rule of thumb, always use ++i unless you really don't want to.

---

### Post by issih on 2008-07-13
Basically the expression i++ returns the value of i before it is incremented, then increments it, whereas ++i increments i then returns the value.

For primitive types like ints this really makes chuff all difference, but if you are using these operators on objects, then a copy of the current object has to be made in order to return it in the state prior to being incremented.

Hence the technical possibility of ++i being more efficient. It all depends on how the operators are implemented really though, but as you generally don't know that, its safer to assume that ++i is a better bet.

That said I still tend to do loops like:

for(int i=0;i<n;i++)

Just because...no good reason, its just what I do.

---

### Post by Zugzwang on 2008-07-14
Thanks for your answers. I finally got it. Regarding to the const-issue: I forgot about that since that was just a rewritten "minimal example" of the problem I was having.

---

### Post by dribeas on 2008-07-15
> **Zugzwang said:**
> Hey all,

[PHP]
1 #include <vector>
2 
3 template<typename A> void addAllVector(std::vector<A> &dest, std::vector<A> &src) {
4    std::vector<A>::iterator it;
5    for (it = src.begin();
6      it!=src.end();
7      it++) {
8	    dest.push_back(*it);
9    }
10 }
12
13 int main() {
14    return 0;
15 }
[/PHP]

The error from g++ 4.1.3 I get when trying to compile (command: "g++ test.cpp") is:
```

test.cpp: In function 'void addAllVector(std::vector<A,  std::allocator<_CharT> >&, std::vector<A, std::allocator<_CharT> >&)':
test.cpp:4: error: expected `;' before 'it'
test.cpp:5: error: 'it' was not declared in this scope

```

Does anyone have an idea why the compiler doesn't want to accept the iterator declaration?

Correct answer has already been posted before, but going just a little off-topic, std library already has this functionality even if it is not so well known:

```

int main() {
   std::vector<X> source;
   std::vector<X> dest;
   // populate source and/or dest
   std::copy( source.begin(), source.end(), std::back_inserter(dest));
}

```

David Rodríguez Ibeas

---

### Post by MattPhillips on 2009-03-03
hod139,

Thanks!  Had exactly the same problem, your post solved it.

Best,
Matt

---

### Post by menego on 2009-08-24
Yay!!! Me too =)

---

### Post by menego on 2009-08-24
yay!!! me too =) ops sorry I did it 2 times..

---

### Post by phanidee on 2009-10-18
Thanks very much. Banging my head for 1 hr to solve this thing in my code.

---

### Post by jrop on 2009-12-29
Phew!  So all I needed was the typename keyword eh?

I would never have guessed that!

---

### Post by CptPicard on 2009-12-29
> **jrop said:**
> Phew!  So all I needed was the typename keyword eh?

I would never have guessed that!

Welcome to the wonderful world of C++ -- the language that manages to create a lot of situations "you will just have to know" because, well, it's C++ ;)

---

### Post by piyush.kumar on 2011-09-13
thanks :)

---

