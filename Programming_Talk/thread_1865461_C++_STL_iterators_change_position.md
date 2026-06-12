---
title: "C++ STL iterators: change position"
date: 2011-10-20
forum: Programming Talk
---

### Post by erotavlas on 2011-10-20
Hi all,

I have a question about the STL iterators on C++. For instance in the case of the map container. Is there a way to multiply the value of iteration to change its position?

```
 
for (int i = j; i < value*(j+1); ++i) // where j is an other index of for
{
...
}

```

for iterators
```

for (map<>::const_iterator it = myMap.begin() * j; it !=  myMap.begin() * (j+1); ++it) 
{
...
}

```

Thank you

---

### Post by karlson on 2011-10-20
> **erotavlas said:**
> Hi all,

I have a question about the STL iterators on C++. For instance in the case of the map container. Is there a way to multiply the value of iteration to change its position?

```
 
for (int i = j; i < value*(j+1); ++i) // where j is an other index of for
{
...
}

```

for iterators
```

for (map<>::const_iterator it = myMap.begin() * j; it !=  myMap.begin() * (j+1); ++it) 
{
...
}

```

Thank you

I am still not sure I understand your question.  If you want to start from Jth position then you need to do:
```

myMap.begin() + j

```
as your starting point.
If you want to step by j elements then
```

it += j

```
You should also consider what your terminating condition is.

In general I would suggest to reconsider using std::map as an underlying data structure and use std::vector instead.

---

### Post by erotavlas on 2011-10-20
Hi,

thank you for your fast reply. I want to use a std::vector but I can't.
I have a vector of element say std::vector<int> and I have a function that split it in equal pieces. I can realize it with the following code.

```

bool function(const std::vector<int>& myVector,const int& number_split)
{
	int number_elements = myVector.size() / number_split;

	for (int j = 0; j < number_split; ++j)
	{
		std::vector<int> myNewVector;
		for (int i = j*number_elements; i < (j+1)*number_elements; ++i)
		{
			myNewVector.push_back(myVector[i]);
		}
	}
}

``` 
The problem is that if I want to check if in the myNewVector is present a given element, I have to scan all the vector and it is tremendously slow.
For this reason I would like to use a map instead of the vector...


A possible solution is this...but it is not very elegant and I don't know if it works.
```

bool function(const std::map<std::string, int>& myMap,const int& number_split)
{
	int number_elements = myMap.size() / number_split;

	for (int j = 0; j < number_split; ++j)
	{
		std::map<std::string, int> myNewMap;

		int i = j*number_elements;
		int l = (j+1)*number_elements
		for (std::map<std::string, int>::const_iterator it = myMap.begin() + i; it != myMap.begin() + i; ++it)
		{
			myNewMap[it->first] = it->second;
		}
	}
}

```

---

### Post by karlson on 2011-10-20
> **erotavlas said:**
> Hi,

thank you for your fast reply. I want to use a std::vector but I can't.
I have a vector of element say std::vector<int> and I have a function that split it in equal pieces. I can realize it with the following code.

```

bool function(const std::vector<int>& myVector,const int& number_split)
{
	int number_elements = myVector.size() / number_split;

	for (int j = 0; j < number_split; ++j)
	{
		std::vector<int> myNewVector;
		for (int i = j*number_elements; i < (j+1)*number_elements; ++i)
		{
			myNewVector.push_back(myVector[i]);
		}
	}
}

``` 
The problem is that if I want to check if in the myNewVector is present a given element, I have to scan all the vector and it is tremendously slow.

I'm trying to figure you what is it that you're doing with myNewVector once done?  That notwithstanding your bounds are incorrect.  The inside of the j loop should look like this:
```

int starting_index = j * num_elements;
for(int i = 0 ; i < num_elements && starting_index + i < myVector.size() ; ++i)

```
Then the index of the element you push_back is starting_index + i.
> 
For this reason I would like to use a map instead of the vector...

[snip]

Don't do this.

---

### Post by erotavlas on 2011-10-20
I'm sorry if I'm not explained very well. So, I have a vector (myVector) and I would like to scan it block by block. Each block become a new vector (myNewVector).
For instance if myVector = {0, 1, 2, 3, 4, 5, 6, 7} and I have to create four new vectors, then each block is composed of two elements and the right way to do this is
```

int number_elements = myVector.size() / number_split;

for (int j = 0; j < number_split; ++j)
{
	std::vector<int> myNewVector;
	for (int i = j*number_elements; i < (j+1)*number_elements; ++i)
	{
		myNewVector.push_back(myVector[i]);
	}
}

```
Naturally each numbers must be congruent to get all the vectors of the same dimension, but this is another problem.
Is there a more clever way to do that? And with map?

Can I do this? If no, is there a workaround?

```

int l = j*number_elements;
int u = (j+1)*number_elements
for (std::map<std::string, int>::const_iterator it = myMap.begin() + l; it != myMap.begin() + u; ++it)
{
}

```

Thank you

---

### Post by karlson on 2011-10-20
> **erotavlas said:**
> I'm sorry if I'm not explained very well. So, I have a vector (myVector) and I would like to scan it block by block. Each block become a new vector (myNewVector).
For instance if myVector = {0, 1, 2, 3, 4, 5, 6, 7} and I have to create four new vectors, then each block is composed of two elements and the right way to do this is
```

int number_elements = myVector.size() / number_split;

for (int j = 0; j < number_split; ++j)
{
	std::vector<int> myNewVector;
	for (int i = j*number_elements; i < (j+1)*number_elements; ++i)
	{
		myNewVector.push_back(myVector[i]);
	}
}

```
Naturally each numbers must be congruent to get all the vectors of the same dimension, but this is another problem.

> 
Is there a more clever way to do that?

Yes but forgive my saying so you don't seem to be anywhere near a point where you could use it.
> 
And with map?

Any reason to?
> 
Can I do this? If no, is there a workaround?

```

int l = j*number_elements;
int u = (j+1)*number_elements
for (std::map<std::string, int>::const_iterator it = myMap.begin() + l; it != myMap.begin() + u; ++it)
{
}

```


You can but again why would you be doing this with a map?

---

### Post by erotavlas on 2011-10-20
1) If you have understood that I need to split a vector in a subvectors of equal dimension, but at the same time I need to do it in clever way i.e. I have to "check" the element that I insert in the subvector.
2) I would like to use a map instead of a vector to make the "check" faster than the search inside a vector. So I need to scan a map block by block.

```

typedef std::map<std::string, int> myMap;
    myMap mymap;
    mymap["a"]=2;
    
    int number_elements = 2;
    
    int l = number_elements;
    int u = number_elements;
    for (myMap::const_iterator it = mymap.begin() + l; it != mymap.begin() + u; ++it)
    {
        std::cout << "";
    }

```

This is doesn't work if I don't redefine the operator=+ for the iterator. How can I do?

Thank

---

### Post by karlson on 2011-10-20
> **erotavlas said:**
> 1) If you have understood that I need to split a vector in a subvectors of equal dimension, but at the same time I need to do it in clever way i.e. I have to "check" the element that I insert in the subvector.
2) I would like to use a map instead of a vector to make the "check" faster than the search inside a vector. So I need to scan a map block by block.



What do you "check"?  If you are talking about look-up for existence this operation for GNU(SGI/HP) implementation of the std::map (someone needs to check the standard to see if this is the same across the board) using a Red-Black Tree would be as fast as search in a sorted vector.

My suggestion would be to get it working in a straightforward way before you start getting "clever".

> 

```

typedef std::map<std::string, int> myMap;
    myMap mymap;
    mymap["a"]=2;
    
    int number_elements = 2;
    
    int l = number_elements;
    int u = number_elements;
    for (myMap::const_iterator it = mymap.begin() + l; it != mymap.begin() + u; ++it)
    {
        std::cout << "";
    }

```


This code will not iterate over anything and it may cause additional problems if the map size < number_of_elements.

> 
This is doesn't work if I don't redefine the operator=+ for the iterator. How can I do?

Thank

Not sure what =+ is but += should be defined for the iterators.  If not then it = it + <step>.

---

### Post by SevenMachines on 2011-10-20
Just as a note, vector begin() returns a random access iterator, which supports operator+/-. Whereas a map returns a bidirectional one, which doesnt.
See [http://www.cplusplus.com/reference/std/iterator/](http://www.cplusplus.com/reference/std/iterator/)

---

### Post by karlson on 2011-10-20
> **SevenMachines said:**
> Just as a note, vector begin() returns a random access iterator, which supports operator+/-. Whereas a map returns a bidirectional one, which doesnt.
See [http://www.cplusplus.com/reference/std/iterator/](http://www.cplusplus.com/reference/std/iterator/)

I stand corrected.  But my original point still stands why use map for this?

---

### Post by erotavlas on 2011-10-21
> **karlson said:**
> I stand corrected.  But my original point still stands why use map for this?


Yes, the map doesn't allow to use random access iterator.
I have solved using duplicated data:a map for direct search and a vector for iteration. 


Thank

---

