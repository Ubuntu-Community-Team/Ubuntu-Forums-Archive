---
title: "efficient searching in STL containers"
date: 2010-10-19
forum: Programming Talk
---

### Post by abraxas334 on 2010-10-19
Hi,
this may be a very simple question, but i don't know how to solve it efficiently.
I have a very large 2-D vector (vector <vector <long> >), of size matrix[n][2];
n>500000.
The vector is sorted according to entry matrix [n][0];
Now I want to find all the occurances of each number in the vector. Say a small example looks like this:
[HTML]
0 1
0 8
1 0
1 7
1 17
2 10
3 4
3 19
4 3
4 14
5 14
[/HTML]
Therfore occurance numbers go as:
0 -> 3
1 -> 4
2 -> 1 etc 
This is the information I would like to print to a file. May naive way of doing things is by iterating over the vector and count...but I guess or hope there is a more efficient way?
My other thought was to change it to a 1-d array/vector (which would only be possible after having created the full 2-vector with its pairs as I need that info) sort that and then do something like: 
Now Vertex is a 1-d sorted array.
[PHP]
//iterate over vector
if(Vertex.at(i)==Vertex.at(i+1))
{
    counter ++;
}
else
{
    counter++;
    //print to file or record some other way the following:
    //Value of Vertex.at(i) and the counter 
    counter=0;
}
[/PHP]

only problem with this I couldn't hold Vertex and Matrix both in memory at the same time. Any thoughts on that or how to do it right?

---

### Post by GeneralZod on 2010-10-19
> Now I want to find all the occurances of each number in the vector

*Each* number (as in, every number) or a set of specific numbers?

Are there any sensible bounds on the range (or set of possible values) of numbers that can be held in the matrix?

PS - vector::at is range-checked, so if you know that you are never de-referencing an out of range index, you might want to use plain old [] instead - with such a large data-set, this probably will make a difference.

Edit:

> only problem with this I couldn't hold Vertex and Matrix both in memory at the same time.

That's somewhat surprising - what value of n did you use to verify this? Is this a desktop PC or a very constrained environment?

---

### Post by worksofcraft on 2010-10-19
Depending on how accurate you want your result and the range of possible numbers that you store, you might try the Monte-Carlo method: You take a statistically significant randomly chose sample and extrapolate from that.

---

### Post by MadCow108 on 2010-10-19
you could fill it into a multiset and use the count method.
This would be O(NlogN) complexity

if you use an unordered multiset (not available in standard c++ but e.g. in boost) you could get it down to O(N)

but you have the same (or worse) memory problem :/

---

### Post by abraxas334 on 2010-10-19
> **GeneralZod said:**
> *Each* number (as in, every number) or a set of specific numbers?

Are there any sensible bounds on the range (or set of possible values) of numbers that can be held in the matrix?



The range of numbers is somewhere between 0 and 2^28 all integers obviously. But for each number there is in that range, i want to know how often it occurs and it needs to be accurate.

---

### Post by PaulM1985 on 2010-10-19
Are all the numbers positive integers?

You could create a vector of a size which is the largest number in the set and then have something like the following:

```

int *myVector = new int[MAX_VALUE_IN_RANGE];
for (int i = 0; i < n; i++)
{
   for (int j = 0; j < 2; j++)
   {
      myVector[myMatrix[i][j]]++;
   }
}

```

After this each index of the myVector array will tell you how many times that number occurred in the matrix.

Paul

---

### Post by GeneralZod on 2010-10-19
Is there anything about the distribution of numbers that suggests it is statistically likely that there will often be "many of a given number" rather than "usually, each number occurs either once or not at all"?

---

### Post by abraxas334 on 2010-10-19
> **GeneralZod said:**
> Is there anything about the distribution of numbers that suggests it is statistically likely that there will often be "many of a given number" rather than "usually, each number occurs either once or not at all"?

Well each number will occur at least once. The pairs actually represent edges on a graph (network) and I am trying to work out the degree distribution of it. Everything suggests, that it has a scale free degree distribution, i.e. the distribution follows a powerlaw. Which suggests most vertices have a small number of connections (i.e. a large number of the numbers will only occur a few times.)

---

### Post by GeneralZod on 2010-10-19
If memory is the main constraint, here, you might be able to get away with a variation of the following.  The basic idea is to count the numbers in the first column (using much the same idea as your "Vertex.at(i)==Vertex.at(i+1) blah"), and write the results to a file straight away, not keeping them around in precious memory.

Then sort the matrix in place so that it is ordered by the second column; hopefully, this will require little or no extra memory, and ~O(NlogN) time.  Then repeat the process and count the numbers in the second column in the same way you counted them in the first, and write them to a second file as you go along.

Now you have two files which contain, respectively:

a) the list of numbers in the 1st column (in sorted order) and the number of times they occur in the 1st column; and

b) the list of numbers in the 2nd column (in sorted order) and the number of times they occur in the 2nd column.

It's now a relatively simple matter of using an algorithm similar to the merge sort to read from the two files and combine the results, writing them to your ultimate destination file as you go (you'll only need one entry from the first file and one from the second in memory at once i.e. the memory usage is tiny).

How does that sound?

---

### Post by abraxas334 on 2010-10-19
> **GeneralZod said:**
> If memory is the main constraint, here, you might be able to get away with a variation of the following.  The basic idea is to count the numbers in the first column (using much the same idea as your "Vertex.at(i)==Vertex.at(i+1) blah"), and write the results to a file straight away, not keeping them around in precious memory.

Then sort the matrix in place so that it is ordered by the second column; hopefully, this will require little or no extra memory, and ~O(NlogN) time.  Then repeat the process and count the numbers in the second column in the same way you counted them in the first, and write them to a second file as you go along.

Now you have two files which contain, respectively:

a) the list of numbers in the 1st column (in sorted order) and the number of times they occur in the 1st column; and

b) the list of numbers in the 2nd column (in sorted order) and the number of times they occur in the 2nd column.

It's now a relatively simple matter of using an algorithm similar to the merge sort to read from the two files and combine the results, writing them to your ultimate destination file as you go (you'll only need one entry from the first file and one from the second in memory at once i.e. the memory usage is tiny).

How does that sound?

Yep that is pretty much what my idea was as well. I guess i just wanted to avoid the io and see if there was a more elegant solution which i am not quite aware of.
Thanks for the input :)

---

