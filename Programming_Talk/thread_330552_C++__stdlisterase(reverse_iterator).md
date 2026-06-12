---
title: "C++:  std::list::erase(reverse_iterator)"
date: 2007-01-03
forum: Programming Talk
---

### Post by Verminox on 2007-01-03
I am iterating through a std::list backwards using the reverse_iterator. Inside the loop, I want to erase the element the iterator is curently pointing to, if it satisfies a given condition.

eg. (Just example code, not really what I am working with)

```
 for( std::list<int>::reverse_iterator i = nums.rbegin(); i != nums.rend(); ){
        if( *i == 0 ){
        nums.erase(i);
}
```

However, the STL only defines erase(iterator) and not erase(reverse_iterator).

How do I erase the element that the reverse_iterator is pointing to? My best bet would be to turn it into a normal iterator first and then call erase() but I dont know how.

PS: Two options that I cannot use:

remove() - because I am using complex objects and I dont want to check for equality with these objects each time, plus they may be duplicates.

reverse_iterator.base() - I keep getting an error with glibc... "invalid pointer"

---

### Post by Verminox on 2007-01-03
Well after trial and errror I found I achieve what I want with this:

```
    for( std::list<int>::reverse_iterator i = nums.rbegin(); i != nums.rend(); i++ ){
        std::cout << *i << std::endl;
        std::list<int>::iterator j = i.base();
        j--;
        nums.erase(j);
        i--;
    }
```

Output:
4
3
2
1

End result: empty list

hmmm....

But if you guys have any better ideas then please post

---

### Post by kaamos on 2007-01-03
(Nevermind)

---

