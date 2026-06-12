---
title: "[C++] STL vector compare"
date: 2011-02-17
forum: Programming Talk
---

### Post by erotavlas on 2011-02-17
Hi,

I have to compare the elements that are contained inside two vectors of pointers. I have a class that manages the vector and one method of this class that receives an other instance of this class. The method has to compare the two vectors (passed and owned by the class). All code is very long, I have reported only the interesting part.
```

Class CompareClass
{
private:
  vector<OtherClass*> vectorPointer;


public:

bool Compare(CompareClass* p)
{
  for(vector<OtherClass*>::const_iterator it = p->vectorPointer.begin(); it != p->vectorPointer.end(); ++it) {

/* How can I search inside the vector owned by the class? */


}


}



}



```My question is how to search inside the vector passed to a method and the one owned by the class for compare the pointed values. I hope that I was enough clear.
Thank you

---

### Post by worksofcraft on 2011-02-17
> **erotavlas said:**
> Hi,
...
/* How can I search inside the vector owned by the class? */



Do you mean you want to compare the vectors element by corresponding element? If so you can use two iterators, one in each vector like so:
[php]
 for (
     vector<OtherClass*>::const_iterator iT1 = vectorPointer.begin(),
     vector<OtherClass*>::const_iterator iT2 = p->vectorPointer.begin();
     iT1 != vectorPointer.end() && iT2 != p->vectorPointer.end();
     ++iT1, ++iT2
 ) {
     if (**iT1 != **iT2) cout << "vector values are different\n";
 }
[/php]
... but I'm not quite sure what you trying to do.

---

### Post by erotavlas on 2011-02-17
> **worksofcraft said:**
> Do you mean you want to compare the vectors element by corresponding element? If so you can use two iterators, one in each vector like so:
[php]
 for (
     vector<OtherClass*>::const_iterator iT1 = vectorPointer.begin(),
     vector<OtherClass*>::const_iterator iT2 = p->vectorPointer.begin();
     iT1 != vectorPointer.end() && iT2 != p->vectorPointer.end();
     ++iT1, ++iT2
 ) {
     if (**iT1 != **iT2) cout << "vector values are different\n";
 }
[/php]... but I'm not quite sure what you trying to do.

Thank you very much for your answer. I have learned a new thing about the iterators. I didn't know that I can use two of them inside a for loop.
How many iterators can I use?
Can I use two int variables for the for loop?

```

for (int i = 0; i < vectorPointer.size(); ++i; int j = 0; j < p->vectorPointer.size(); ++j)

```

---

### Post by forrestcupp on 2011-02-17
You should use nested for loops to make your code readable.

---

### Post by worksofcraft on 2011-02-17
> **erotavlas said:**
> Thank you very much for your answer. I have learned a new thing about the iterators. I didn't know that I can use two of them inside a for loop.
How many iterators can I use?
Can I use two int variables for the for loop?

```

for (int i = 0; i < vectorPointer.size(); ++i; int j = 0; j < p->vectorPointer.size(); ++j)

```

You can use as many as you want. You can think of them as a kind of pointers as if you were pointing in an array.
If you use -std=c++0x compile switch you can use the following easier syntax:
[php]
for (auto iT = vectorPointer.begin(); iT != vectorPointer.end(); ++iT) ...
[/php]
You can also use numeric indices with vectors, but there is no point having two that are both the same value... it is completely different from having two nested loops! I am advancing both iterators at the same time there .i.e. it's like comparing vectorA[i]  with vectorB[i] each time.

---

### Post by forrestcupp on 2011-02-17
> **worksofcraft said:**
> 
You can also use numeric indices with vectors, but there is no point having two that are both the same value... it is completely different from having two nested loops! I am advancing both iterators at the same time there .i.e. it's like comparing vectorA[i]  with vectorB[i] each time.

It all depends on whether you need to compare the vectors at the same points or if you need to look through the entire vector to see if it has a certain value. If you need to search through two entire vectors, you would have to have nested loops, wouldn't you? If not, you could just advance both iterators at the same time.

---

### Post by PaulM1985 on 2011-02-18
I agree that nested loops are not the way to go.  If I had two vectors containing chars, so two strings, I would not expect "hello" and "elloh" to be considered as equal.

Additionally, I think this post is related to equality, rather than comparison.  Equality, "are these equal" and returning a boolean is different to comparing where you say if they are the same or one is greater than the other.

Since it looks like we are discussing equality, why not use std::equal?

Here is a link to a reference page with some example code: [http://www.cplusplus.com/reference/algorithm/equal/](http://www.cplusplus.com/reference/algorithm/equal/)

You essentially pass in interators and a function that you want to use to compare each of the individual elements.

Paul

---

### Post by forrestcupp on 2011-02-18
> **PaulM1985 said:**
> I agree that nested loops are not the way to go.  If I had two vectors containing chars, so two strings, I would not expect "hello" and "elloh" to be considered as equal.

Additionally, I think this post is related to equality, rather than comparison.
But the OP actually said that he was trying to compare the elements of two vectors. He didn't say he was trying to determine if the vectors are equal. I'd say we need a lot more clarity about the OP's intent before we can give a proper solution.

---

