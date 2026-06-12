---
title: "Copying vector by reference"
date: 2009-09-05
forum: Programming Talk
---

### Post by krisfrajer on 2009-09-05
Hi all
I am struggling to copy a vector by reference. This is what I would like to do:



  vector<int> first (3,3);
  vector<int> second (5,5);


  cout << "Size of first: " << int (first.size()) << endl;
  cout << "Size of second: " << int (second.size()) << endl;
  cout << "first's first element: " << first[0] << endl;
  cout << "sec's first element: " << second[0] << endl;

  second = first;

  first[0]=15;  //I was expecting that both first[0] and second[0] equals to 
                //15. Not the case here :(

  cout << "first's first element: " << first[0] << endl;  //prinst 15
  cout << "sec's first element: " << second[0] << endl;   //prints 5

I was expecting to have both vectors' first element to be 15. I am aware the constructors only creates a copy of the vector.

I was hoping to be able to do something like 

  second = &first;

Again it does not work because of the definition of the operator=.
What is the proper way to do it?

Thxs,
Kris

---

### Post by scourge on 2009-09-05
> **krisfrajer said:**
> 
Again it does not work because of the definition of the operator=.
What is the proper way to do it?


Using a reference, maybe?
Like this:
```

vector<int> myVector;
vector<int>& referenceToMyVector = myVector;

```

You can also use a pointer:
```

vector<int> myVector;
vector<int>* pointerToMyVector = &myVector;

```

---

### Post by MadCow108 on 2009-09-05
misunderstood the question

---

### Post by krisfrajer on 2009-09-05
The pointer works perfectly for what I need!

Thxs a lot,
Kris

---

