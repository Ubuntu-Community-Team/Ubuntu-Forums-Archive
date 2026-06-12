---
title: "C++ Ordering a const vector"
date: 2012-05-10
forum: Programming Talk
---

### Post by erotavlas on 2012-05-10
Hi,

I need to order a vector of element (int) passed to a function as constant so I cannot use sort algorithm without making a copy of the original vector.
```

const int sortFunction(const vector<int> myVector)
{
    vector<int> sortedVector = myVector;
    sort(sortedVector.begin(), sortedVector.end());
	return sortedVector.front();
}

``` 

Is there a way to order the vector without making a copy or passing it as non const?

---

### Post by PaulM1985 on 2012-05-10
You would have to pass it in as non-const.

What you are actually doing is passing in a const copy, since you are not passing in the vector by reference, so you are passing a copy of the vector in in the first place.

If you want to not make any copies, you could pass in the vector as a non-const reference:

```

void sortFunction(vector<int> &myVector)
{
    sort(myVector.begin(), myVector.end());
}

```

And in your calling code, you would have:
```

vector<int> myVector;
//..
//Populate it
//..

// Sort it
sortFunction(myVector);
//myVector is now sorted.

```

If you did want to copy the array, you could pass it in as a const reference and make a copy in your function which you return:
```

vector<int> sortFunction(const vector<int> &myVector)
{
    vector<int> sortedVector = myVector;
    sort(sortedVector.begin(), sortedVector.end());
    return sortedVector;
}

```

Paul

EDIT: The whole point of passing something in as const is like explicitly saying "I do not want to change this object in this function".  You do want to change it, so it needs to be non-const.

---

