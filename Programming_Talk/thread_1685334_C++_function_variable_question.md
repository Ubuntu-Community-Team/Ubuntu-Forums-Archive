---
title: "C++ function variable question"
date: 2011-02-10
forum: Programming Talk
---

### Post by cguy on 2011-02-10
This is from "Advanced C++. Practical Programming by Example" by Andrew Koenig and Barbara E. Moo

```
[COLOR="SeaGreen"]The most straightforward approach to solving our overall problem is to examine
each student record and push it onto one of two vectors, one for students with passing
grades and the other for students with failing grades:

// separate passing and failing student records: first try[/COLOR]
vector<Student_info> extract_fails(vector<Student_info>& students)
{
    vector<Student_info> pass, fail;

    for (vector<Student_info>::size_type i = 0;
        i != students.size(); ++i) 
       if (fgrade(students[i]))
           fail.push_back(students[i]);
       else
           pass.push_back(students[i]);

     students = pass;
     return fail;
}

```

1. Won't *pass* be deleted upon the return of the function, hence *students* will point at a piece of memory no longer allocated?

2. Won't there be a memory leak caused by the reallocation of *students* without first deleting its elements?

3. Won't *fail* be deleted upon return, hence the variable returned by the function point to a location no longer owned by the program?

---

### Post by worksofcraft on 2011-02-10
> **cguy said:**
> This is from "Advanced C++. Practical Programming by Example" by Andrew Koenig and Barbara E. Moo

```
[COLOR="SeaGreen"]The most straightforward approach to solving our overall problem is to examine
each student record and push it onto one of two vectors, one for students with passing
grades and the other for students with failing grades:

// separate passing and failing student records: first try[/COLOR]
vector<Student_info> extract_fails(vector<Student_info>& students)
{
    vector<Student_info> pass, fail;

    for (vector<Student_info>::size_type i = 0;
        i != students.size(); ++i) 
       if (fgrade(students[i]))
           fail.push_back(students[i]);
       else
           pass.push_back(students[i]);

     students = pass;
     return fail;
}

```

1. Won't *pass* be deleted upon the return of the function, hence *students* will point at a piece of memory no longer allocated?

2. Won't there be a memory leak caused by the reallocation of *students* without first deleting its elements?

3. Won't *fail* be deleted upon return, hence the variable returned by the function point to a location no longer owned by the program?

1. Yes pass will be deleted, but the contents of it will have been asigned (i.e. copied) to the referenced vector "students".

2. When a vector is destroyed the destructor is called for all the elements in the vector.

3. No, the return by value syntax means that conceptually the pass vector is copied out of the function before it's local copy is destroyed, but often the compiler optimizes this so that the pass vector is actually constructed in the return result space.

I would say it is not a good way to program as copying vectors is very inefficient.

p.s. There are quite a lot of other constructs there I would not recommend and if this is a typical example of what is in that book I would say to find another book asap.

---

### Post by cguy on 2011-02-10
Which are the constructs that you wouldn't recommend and why?

---

### Post by MadCow108 on 2011-02-10
the only problem I see is the slightly weird semantics that it modifies student, but thats fine when its documented
I would do it like this:
[PHP]
vector<student> failed, passed;
remove_copy_if (students.begin(), students.end(), failed.begin(), fgrade);
remove_copy_if (students.begin(), students.end(), passed.begin(), not1(fgrade)); // stupid standard does not have a copy_if -.-
[/PHP]
using lists instead of vectors would allow a more efficient implementation by directly removing from students.

---

### Post by cguy on 2011-02-10
Well, this is a code example in the first pages of this chapter; it continues by improving the algorithm and introducing new concepts (incl. lists).

---

### Post by DZ* on 2011-02-10
> **cguy said:**
> Well, this is a code example in the first pages of this chapter; it continues by improving the algorithm and introducing new concepts (incl. lists).

[You'd hope so]("http://en.wikipedia.org/wiki/Andrew_Koenig_(programmer)") :-)

---

### Post by worksofcraft on 2011-02-10
> **cguy said:**
> Which are the constructs that you wouldn't recommend and why?

Student_info record is probably quite a large structure, perhaps containing name strings and phone numbers and grades etcetera. Thus copying them from one vector to another takes a lot of processing and memory. It would be better to work with pointers or references.

When iterating in containers one should use the container iterators instead of indexing, that way it will use the most efficient method of iterating for that container type and you can change which container class you use (e.g. to one that does not support indexing) without rewriting the code.

You want to delete items from the list of students, but vectors are far from optimal for deletions and you probably want to be able to locate students by a key value such as their name or student number so a map would be more appropriate and would allow you to efficiently extract the failed student's records directly from the original container.

I could explain more about techniques for working with pointers and references and memory management because when you store pointers in a container then what they point to does not get deleted when the container is disposed of (as they may still be in use in other containers)... but if I'm not careful I'll end up rewriting the whole book :shock:

---

### Post by MadCow108 on 2011-02-10
> **worksofcraft said:**
> Student_info record is probably quite a large structure, perhaps containing name strings and phone numbers and grades etcetera. Thus copying them from one vector to another takes a lot of processing and memory. It would be better to work with pointers or references.

unless student_info is really large (say > 500bytes) and the code is not very performance sensitive this kind of optimization is very dangerous.
It makes maintenance harder and can introduce many many bugs.
The mostly small performance gain is not worth that.

My position is that you should not use vectors of (raw) pointers unless absolutely necessary, by doing that you lose many advantages of C++ with STL (mainly the automatic memory management and applying algorithms becomes more tedious).
If you do need references you better use shared pointers.

But I guess this is also all covered in the book ^^

---

### Post by worksofcraft on 2011-02-10
> **cguy said:**
> Well, this is a code example in the first pages of this chapter; it continues by improving the algorithm and introducing new concepts (incl. lists).

This book gets a "thumbs down" from me (*), because IMO they have not chosen appropriate examples for the topic they are introducing. If they want to show you how vectors work then they should choose an illustration that is appropriate to vectors and do "vectorish" things with them.

Later they can introduce lists and maps and iterators with examples that genuinely benefit from those new concepts. That way you gain a real understanding of why there are different container constructs and how to use them properly.

* p.s. clarification: This is NOT to be construed as a proper book review. It is based exclusively on the example posted here and I have no actual knowledge of the rest of that book or the full context in which the example is presented.

---

### Post by worksofcraft on 2011-02-10
> **MadCow108 said:**
> unless student_info is really large (say > 500bytes) and the code is not very performance sensitive this kind of optimization is very dangerous.
It makes maintenance harder and can introduce many many bugs.
The mostly small performance gain is not worth that.

My position is that you should not use vectors of (raw) pointers unless absolutely necessary, by doing that you lose almost all advantages of C++ with STL (mainly the automatic memory management and applying algorithms becomes more tedious).
If you do need references you better use shared pointers.

But I guess this is also all covered in the book ^^

I agree, in principle but I don't agree about using shared pointers which have a hideous overhead on every access and neither do I agree about the dangers. That is only when you try to use C++ as if it was Java.

e.g. One technique I use with containers of pointers is to use them as transient structures for manipulating variable sets of objects. Those objects (regardless of size) are actually stored only once in a single big container (appropriate to the type of object) for which the life span exceeds that of all the ones involved in the processing.

---

### Post by Simian Man on 2011-02-10
I haven't read that book, but I have read "Accelerated C++" by the same authors, and it was the best C++ book I've ever read.  Rather than introduce a bunch of concepts and then dump a bunch of code on you, like most books, they present a problem and iteratively arrive at a good solution.  This is a *much* better approach IMHO, because it is the way code is actually written.  Nobody bangs out an efficient, well-working solution on the first go.  And if they do they clearly are not working on very interesting problems :).

The fact that this example says "The most straightforward approach to solving our overall problem..." suggests to me that they will rectify the inefficiencies of the code with further examples.  This too, sounds like a great programming book, and I recommend the OP to stick with, and continue thinking critically about the code :).

---

### Post by DZ* on 2011-02-10
It's the same book. The OP misspelled the title.

---

### Post by Simian Man on 2011-02-10
> **DZ* said:**
> It's the same book. The OP misspelled the title.

Then I even more strongly support their reading it :).

---

