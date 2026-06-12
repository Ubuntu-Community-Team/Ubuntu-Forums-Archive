---
title: "help with C++ data reading"
date: 2010-04-08
forum: Programming Talk
---

### Post by smdawson on 2010-04-08
I am trying to figure out how to read two different variables from a txt document side by side. For instance,

123, 3.43
423, 2.14
etc.

How can I read the two values and set the first column as variable1 and the second as variable2?

---

### Post by smdawson on 2010-04-08
bump

---

### Post by MadCow108 on 2010-04-09
[http://www.cplusplus.com/reference/iostream/fstream/](http://www.cplusplus.com/reference/iostream/fstream/)
```

ifstream file("file")
string strdump; // for the comma
double a,b;
while (file >> a >> strdump >> b) {
  .. do stuff
}
//do error handling with good() bad() fail() and eof()

```
if you want to save the whole column use a vector or some other container

you could also read it with getline and the comma as delimiter
[http://www.cplusplus.com/reference/string/getline/](http://www.cplusplus.com/reference/string/getline/)

---

### Post by smdawson on 2010-04-09
Ok, thanks. Now, is the code vastly different if there is no comma between the numbers, I would just take out the string variable right? Also, can I put the numbers into an array? I guess I would have to know how many numbers there are because I would have to specify the length of the array, right? I haven't learned about vectors yet, so I do not know if I could competently use them...

---

### Post by Xender1 on 2010-04-09
If there was no comma then you would just get rid of the strdump because if it was left in there file >> a = the first num, >> strbump would get the second number, and >> b would then get the number from the next line.

You could use a dynamic array but a vector would be much easier and they are extremely easy to use. Do some googling and i found plenty of good tutorials for some basic vector methods.

---

### Post by MadCow108 on 2010-04-09
vectors save you the problem of unknown length of the file. vectors grow dynamically when they exceed their capacity and they are very easy to use. It is strongly recommended to use vectors instead of old C arrays

if the number of columns is variable or unknown it is probably easiest to read a whole line with getline and copy the line into a stringstream and extract from that entry by entry similar to above code (adding them to a vector if needed)
not the fastest but very quick and easy
[http://www.cplusplus.com/reference/string/getline/](http://www.cplusplus.com/reference/string/getline/)
```

// assuming no comma between the numbers, again now error handling
ifstream file("..");
string line;
while(getline (file, line)) {
  stringstream ss(line);
  vector<double> row;
  double a;
  while(ss >> a) // add a strdump for commas or even use getline again with a comma as delimiter
    row.push_back(a); // adds a entry to the vector, increasing its size if necessary
  // do something,
  unsigned int nColumns = row.size()
  double firstcolumn = row[0]; // like with C arrays
}

```

---

### Post by smdawson on 2010-04-12
Alright, this is my code to read two numbers into vectors on the same line with no comma between them. Please let me know if I did something wrong, or the code is not very efficient.

 If my code is correct at this point I then need to sort it (sorting algorithm i guess?), list the range of the angles, and then output corresponding coefficients when the user inputs an angle inside the range. However, I want to make sure that what I have now is correct before I build on top of it.
```

#include <iostream>
#include <fstream>
#include <vector>
using namespace std;

int main()
{
    int data_pairs;
    vector<double> angle;
    vector<double> coef;
    ifstream fin;
    
        
    cout << "Please enter the number of data pairs to be read." << endl;
    cin >> data_pairs;

    angle.resize (data_pairs);
    coef.resize (data_pairs);

    fin.open ("tunnels.txt");
    if(!fin) 
    {
       cerr << "Error: file could not be opened." << endl;
       exit(1);
    }

    while ( !fin.eof() ) 
    {
       fin >> angle >> coef;
    }
    
    fin.close();
    
    return 0;
} 
```

By the way, I appreciate all the advice.

---

### Post by MadCow108 on 2010-04-12
this should not even compile except you have overloaded the >> operator for vectors somewhere

you either have to add a counter in the loop and read in similar to this:
fin >> angle[counter];
counter++;

or as shown above using push_back. this has the advantage that you don't overflow your vector to easily.

when you want to read a pair of values and sort them you should use a compound data structure holding both values, e.g. a class or struct.
C++ also has a pair built in:
std::pair<double, double> angle_coef;
[http://www.cplusplus.com/reference/std/utility/pair/](http://www.cplusplus.com/reference/std/utility/pair/)

add this to a vector and you can then sort them with the sort algorithm
[http://www.cplusplus.com/reference/algorithm/sort/](http://www.cplusplus.com/reference/algorithm/sort/)
the default comparison for the std::pair should be fine if you order your variables correctly in the pair

---

### Post by smdawson on 2010-04-12
I don't know how I overloaded the >> operator, but is that a bad thing? From what I have read overloading is useful, but I am still not completely sure what it is...  

I added the counter to the vectors. I didn't initially realize that I need the counter or push_back to keep expanding the vector. Here is the section I changed. 

```
int counter = 0;

while ( !fin.eof() ) 
    {
       fin >> angle[counter] >> coef[counter];
       counter++;
    }
```

I took a look at the vector link that uses the .begin() and .end() iterators for sorting. Is it more efficient to split up the numbers in half, or more sections, and then sort them that way? As opposed to sorting the entire catalog of numbers at once?

---

### Post by MadCow108 on 2010-04-12
you only need to use begin and end when you want to sort the entire vector/container, the algorithm takes any range (represented by start and end iterators)

the sort algorithm is already a O(NlogN) algorithm. that is the best you can get for generic sorting
internally it is probably a quicksort algorithm which is very efficient for most common datasets.
try it first and only when you have determined from profiling that it is to slow consider investigating the cause and solutions.
remember the rule:
premature optimization is the root of all evil

---

### Post by smdawson on 2010-04-12
with the pairs, would I have to initialize them all?
(i.e.)
pair <double, double> data_pair1;
pair <double, double> data_pair2;
pair <double, double> data_pair3;
pair <double, double> data_pair4;
pair <double, double> data_pair5;....

What if I don't know how many there will be? can I just use a counter to number all of the different pairs?

Can I sort the pairs based on only the first term, or based on only the second term?

---

### Post by MadCow108 on 2010-04-12
you can make a vector of almost everything, also pairs, to safe typing you can make typedefs of the structures your using:
```

vector<pair<double, double> > data; // the space after the > is necessary
data.push_back(make_pair(1.5,2.5));
// define a shortcut:
typedef vector<pair<double, double> > DataVector;
// easier to type:
DataVector data2;
data2.push_back(make_pair(32.,23.));
data2.resize(5);
data2[4] = make_pair(2.3,.3);

```

by default pairs compare the first element, and only if these are equal it compares the second
if you don't want that define your own comparison function (or function object):
```

typedef pair<double,double> MyPair;
// compare only the second element;
bool paircompare(const MyPair & a, const MyPair b) {
  return a.second < b.second;
} 
...

DataVector data; // see typedef above
// fill it with some pairs
sort(data.begin(), data.end(), paircompare);

```

---

### Post by smdawson on 2010-04-12
ok. that does seem like an easier way to write things. I tried to apply some of these things but I am doing quite a few things wrong. Any pointers?

```
#include <iostream>
#include <fstream>
#include <vector>
#include <algorithm>
#include <iterator>
using namespace std;

int main()
{
    int data_pairs;
    int i = 0;
    ifstream fin;
    vector<pair<double, double> > data();
    typedef vector<pair<double, double> > DataVector;
    DataVector::iterator it;

    cout << "Please enter the number of data pairs to be read." << endl;
    cin >> data_pairs;

    data.resize(data_pairs);

    fin.open ("tunnels.txt");
    if(!fin)
    {
       cerr << "Error: file could not be opened." << endl;
       return(1);
    }

    while ( !fin.eof() )
    {
       fin >> data(i).first >> data(i).second
       i++;
    }

    fin.close();

    sort (data.begin(), data.end() )

    cout << "The data pairs in order are:\n";
    for (it=data.begin(); it!=data.end(); ++it)
       cout << " " << *it; << endl;

    return 0;
}
```

---

### Post by smdawson on 2010-04-12
maybe this would solve some of my problems?

```
double a = 0;
double b = 0;
while ( !fin.eof() )
    {
       fin >> a >> b;
           data(i) = make_pair (a, b);
       i++;
    }
```

---

### Post by MadCow108 on 2010-04-12
vector elements are access with the [] operator not ()
alternatively you can use at(number) this function includes runtime boundary checking

i still recommend push_back(make_pair(...))
this saves you the asking for the max number of entries
for efficiency put a data.reserve(number) in the beginning to reserve some memory beforehand

and your output is wrong,
you have to do: it->first << " " << it->second;

(or overload the << operator for pairs)

you can put the typedef in the beginning (or even global) and still initialize a vector:
typedef .. DataVector
DataVector data();

---

### Post by smdawson on 2010-04-12
Ok, more changes.
I am not sure if I am using push_back correctly. My compiler says I am not defining the iterator properly. I am also not sure if the output section is correct now. When do I use the typedef "DataVector"? Because right now I don't use it anywhere in the code.

```
#include <iostream>
#include <fstream>
#include <vector>
#include <algorithm>
using namespace std;

typedef vector<pair<double, double> > DataVector;

int main()
{

    double a;
    double b;
    ifstream fin;
    vector<pair<double, double> > data;
    vector<pair<double, double>::iterator it;

    data.reserve(15);

    fin.open ("tunnels.txt");
    if(!fin)
    {
       cerr << "Error: file could not be opened." << endl;
       return(1);
    }

    while ( !fin.eof() )
    {
       fin >> a >> b;
           data.push_back(make_pair (a, b));
    }

    fin.close();

    sort (data.begin(), data.end() );

    cout << "The data pairs in order are:\n";
    for (it=data.begin(); it!=data.end(); ++it)
       cout << it->first<< " " << it->second;

    return 0;
}

```

---

### Post by MadCow108 on 2010-04-13
there is a closing bracket > missing at the iterator declaration

you don't need to use the typedef, it just can be more convenient to use and easier to read than long nested templates

---

### Post by smdawson on 2010-04-13
Perfect. Now what can I use to display the first and last pair? so I can show the range of the first number of the pairs. 

I also need to find a way to have the user choose the first number of a pair between the range and then display the corresponding second number of the pair.

---

### Post by MadCow108 on 2010-04-13
I have posted enough links so should be able to solve these problems yourself
my favorite reference is [www.cplusplus.com/reference](www.cplusplus.com/reference)

look at the member functions of vector for the first question, and the algorithms for the second
(for performance you can use a binary search instead of a linear find, as your vector is sorted)

---

### Post by smdawson on 2010-04-13
Ok, thank you. I appreciate all of the help.

---

### Post by smdawson on 2010-04-13
Sorry to bother you again, but I cannot seem to find an algorithm that works. "binary_search" finds the value, and so does "find". But after I find the value I do not know it's placement. I need to know where it is in the vector so I can display the pair.

---

### Post by smdawson on 2010-04-13
right now I have something like this.

```
sort (data.begin(), data.end() );

    cout << "The range of flight-path angles is: ";
    cout << data.begin() " to " << data.end() " degrees" << endl;

    while ( again=='y' || again=='Y' )
    {
       cout << "Please enter a flight-path angle in degrees" << endl;
       cin >> i;
           
           if (binary_search (data.begin(), data.end(), i))
           {
           cout << "The flight-path coeffecient for " << i
           cout << " degrees is " << ?? << endl;
           }
           else
               cout << "That value is not within the range." << endl;
        }

```

---

### Post by MadCow108 on 2010-04-13
find returns the iterator to the element, use that to access the elements just as you did to output the pairs before

binary search is a bit more tricky
if you look at the bottom of the reference of binary_search you find
lower_bound	Return iterator to lower bound (function template)
upper_bound	Return iterator to upper bound (function template)
equal_range	Get subrange of equal elements (function template)

these functions return iterators to the elements like find.
Read the documentation carefully, upper and lower_bound differ in their return value a little

these are too binary searches, thus O(logN) when used with random access iterators like those of the vector

I suggest you spend a little time looking at the reference and familiarize yourself with all the functions.
When you have the next problem have a look around the reference if you find something and try that before asking.
I'm happy to help but you I don't want to describe your whole program.

---

### Post by smdawson on 2010-04-13
Oh, I see. You use the iterator that points to the element when "find" finds the value. You said use the members of the pair, like data.first and data.second. But I cannot write *it.first or *it.second. Is there a way around that?

Nevermind, I will look around the reference site. Sorry, my class isn't on this topics so I am trying to teach myself, but that is a little more difficult than I thought.

---

### Post by MadCow108 on 2010-04-13
as this is technical details I'll help :)
unfortunately C++ is full of this which makes it hard to learn.

iterator overload the -> and * operators for access to the element and the dereference operator * acts all the way to the right
so *it.first is equivalent to this: *(it.first) what is not what you want

so you have to use parentheses:
(*it).first
or the -> operator directly
it->first

---

### Post by smdawson on 2010-04-13
That helped me very much! I will try and only ask technical questions from now on and figure out the concepts on my own.;) 

My compiler will not let me compile because of a few errors I don't understand. However, I think everything is close to working...

```
#include <iostream>
#include <fstream>
#include <vector>
#include <algorithm>
#include <utility>
using namespace std;

typedef vector<pair<double, double> > DataVector;

int main()
{

        double b;
        double a;
        ifstream fin;
        DataVector data;
        DataVector::iterator it;
        DataVector::iterator it2;
        DataVector::iterator it3;
        int i;
        char again = 'y';

    data.reserve(15);

    fin.open ("tunnels.txt");
    if(!fin)
    {
       cout << "Error: file could not be opened." << endl;
       return(1);
    }

    while ( !fin.eof() )
    {
       fin >> a >> b;
           data.push_back(make_pair (a, b));
    }

    fin.close();

    sort (data.begin(), data.end() );

        it2 = data.begin();
        it3 = data.end();

    cout << "The range of flight-path angles is: ";
    cout << (*it2).first << " to " << (*it3).first << " degrees." << endl;

    while ( again == 'y' || again == 'Y' )
    {
       cout << "Please enter a flight-path angle in degrees" << endl;
       cin >> i;
           
           it = find(data.begin(), data.end(), i);
           ++it;
           
           if (it <= data.end() || it >= data.begin() )
           {
               cout << "The flight-path coefficient for " << (*it).first;
               cout << " degrees is " << (*it).second << endl;
           }
           else
               cout << "The value entered is not within range" << endl;

           cout << "Would you like to find more flight-path values?" << endl;
           cin >> again;
        }

    return 0;
}
```

---

### Post by kcode on 2010-04-13
Considering reading data from files, input/output redirection can be of great help, if the program knows well how the data is formatted in the file.

---

### Post by smdawson on 2010-04-13
I just realized another problem. If "find" doesn't find the value "i" in the vector then it defaults to the "data.end()" value. But I am using " data.begin() <= it >= data.end() " to see if the value is  within the range. So even if the value is not found in the vector my if statement will never go to the "else" because the default "data.end()" is always within the range.

---

### Post by MadCow108 on 2010-04-13
the end() functions always return a so called past-end-iterator
this is a iterator pointer to a position one greater the the last element. As this element is never in the container it is used as a failure indicator by most algorithms.
This means you should never use the value it points to, it is undefined.
replace the <= with <

at the compile problem:
the algorithms compare with the type pointed to by the iterator.
you are trying to compare with an integer.
you have to create a new pair with which the algorithm should compare the pairs in the vector
find(it1, it2, make_pair(double1, double2));
The using find is unfortunate in this case for three reasons:
find uses the == operator, this bad because:
1. it compares both elements of the pair by default, so you can't search for the first element only unless you change the default (see a few pages earlier)
2. == is a bad idea when dealing with floats because of rounding errors. To avoid problems you should provide a comparison function which compares floats with a certain precision and not binary exact.
3. your wasting the fact that the vector is sorted, thus its slow.

because your vector is sorted consider using upper/lower_bound/equal_range which uses the < operator
this solves all three problems, the first problem because it only compares the first element and the second only when the firsts are equal:
[http://www.cplusplus.com/reference/std/utility/pair/](http://www.cplusplus.com/reference/std/utility/pair/)
see global operator section

---

### Post by smdawson on 2010-04-13
I see. I fixed most of the problems but I still think I have compiling problems with my if statement. I thought the comparison I changed it to would fix it. This gets a little confusing.:)

```
DataVector data;
        DataVector::iterator it2;
        DataVector::iterator it3;
        DataVector::iterator up;
        int up2;
        int i;

 it2 = data.begin();
        it3 = data.end();

    cout << "The range of flight-path angles is: ";
    cout << (*it2).first << " to " << (*it3).first << " degrees." << endl;

    while ( again == 'y' || again == 'Y' )
    {
       cout << "Please enter a flight-path angle in degrees" << endl;
       cin >> i;
           
           up = upper_bound(data.begin(), data.end(), i);
           up2 = (up - data.begin());
           
           if ( i < (*it3).first || i >= (*it2).first )
           {
               cout << "The flight-path coefficient for " << data[up2].first;
               cout << " degrees is " << data[up2].second << endl;
           }
           else
               cout << "The value entered is not within range" << endl;

           cout << "Would you like to find more flight-path values?" << endl;
           cin >> again;
        }
```

---

### Post by MadCow108 on 2010-04-14
the if is unnecessary, the search does that for you,
and you are again using the value of the past end iterator, this is not allowed!
the first and last elements can be accessed directly with front() and back()

binary equality (very bad in many situations!):
```

double i;
pair<DataVector::iterator, DataVector::iterator> res;
res = equal_range(data.begin(), data.end(), make_pair(i, 0.));
cout << "found " << distance(res.first, res.second) << " elements" << endl;
while (res.first != res.second) {
  cout << res.first->first << " " << res.first->second << endl;
  res.first++;
}

```

approximate equality:
```

double i;
DataVector::iterator low, up;
low = lower_bound(data.begin(), data.end(), make_pair(i - 0.001, 0.));
up =  upper_bound(data.begin(), data.end(), make_pair(i + 0.001, 0.));
cout << "found " << distance(low, up) << " elements" << endl;
while (low != up) {
  cout << low->first << " " << low->second << endl;
  low++;
}

```

note that i is a double no integer

---

### Post by smdawson on 2010-04-14
What is the rule about not using the previous end iterator?

So you added the (i - .001) to up and (i - .001) to low so that (low!=up) in the while statement and it outputs the values, correct?

what will happen to low and up if the input value "i" is not in the vector? The cplusplus/reference says the comparison will return false if in upper_bound or lower_bound do not find the number less than the value or the first number greater than the value.

Can I then use an if statement on the upper_bound and lower_bound searched like binary_search does?

```
if (binary_search (v.begin(), v.end(), 6, myfunction))
    cout << "found!\n"; else cout << "not found.\n";

```

---

### Post by smdawson on 2010-04-14
Maybe something like this...or do I need lower_bound too..

```
up = upper_bound(data.begin(), data.end(), make_pair(i ,0));
           
           if ( up ) 
           {   cout << "The flight-path coefficient for " << low->first;
               cout << " degrees is " << low->second << endl;
           }
           else
              cout << "The value entered is not within range" << endl;
```

---

### Post by MadCow108 on 2010-04-14
if the value is not in the range then low == up (either both the first element or both the past-end element) and
while (low != up) is false
so the loop never gets executed
and distance(low, up) evaluates to zero

---

### Post by smdawson on 2010-04-14
Ah, I see. 

By the way, does your job entail using programming or is it just a hobby for you? I'm a computer science major at the University, but my classes are not getting as advanced as what we have been talking about. They don't talk about producing "efficient code" either.

I am not sure how proficient I should strive to be in programming languages to find a good job. I would like to do well just to be accomplished, but I don't know many programmers I can ask questions.

---

