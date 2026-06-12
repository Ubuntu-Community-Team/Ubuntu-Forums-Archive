---
title: "c++ progam sorting...."
date: 2009-10-24
forum: Programming Talk
---

### Post by abhilashm86 on 2009-10-24
i created a class peaks, then when i sort the array so[], the others are not getting sorted,i've allocated memory dynamically, but variables are not sorted....
 ```
#include<iostream>
using namespace std;

class peaks
{
 public:
	int peak,so[10], ea[10], alti[10];
	char a[10];
};



int sort(int peakss)
{
peaks *p=new peaks();
p->peak=peakss;
int temp;
for(int i=0;i<p->peak;i++)
{
 cout<<"enter peak name, south-east, north-west, altitude"<<endl;
 cin>>p->a[i]>>p->so[i]>>p->ea[i]>>p->alti[i];
}

   
  for(int i=0;i<p->peak;i++)
 {
 	for(int j=i+1;j<p->peak;j++)
	{
 		if(p->so[j]<p->so[i])
		{
			temp=p->so[i];
			p->so[i]=p->so[j];
			p->so[j]=temp;
		}
	}
 }
 

cout<<" sorted peaks are"<<endl;
 for(int i=0;i<p->peak;i++)
 {
 	cout<<p->so[i]<<p->a[i]<<endl;
 }
}


int main()
{
 int temp; 
 cout<<"enter no of peaks"<<endl;
 cin>>temp;
 sort(temp);
}


```
everything works fine, but sorting wont change other objects?
```
ubuntu@ubuntu:~$ g++ pgma.cpp
ubuntu@ubuntu:~$ ./a.out 
enter no of peaks
3
enter peak name, south-east, north-west, altitude
e 3 2 1 
enter peak name, south-east, north-west, altitude
q 2 3 4 
enter peak name, south-east, north-west, altitude
f 1 2 3 
 sorted peaks are
1e
2q
3f
ubuntu@ubuntu:~$ gedit pgma


```

---

### Post by McNils on 2009-10-24
You sort only the array so. The other arrays are unchanged. 
one solution might be to have an array of an other class. Something like this.

```
class pos  {
 public:
    int so, ea, alti;
    char a;
};

class peaks {
 public:
        int peak;
        pos so[10];
};
```

you need to modify the rest of the code as well... you might use struct instead of class. all members of a struct is public.

---

### Post by abhilashm86 on 2009-10-24
> **McNils said:**
> You sort only the array so. The other arrays are unchanged. 
one solution might be to have an array of an other class. Something like this.

```
class pos  {
 public:
    int so, ea, alti;
    char a;
};

class peaks {
 public:
        int peak;
        pos so[10];
};
```

you need to modify the rest of the code as well... you might use struct instead of class. all members of a struct is public.

you are just creating array of classes, also its not able to give values to so[] array, i should declare class as

```

class pos
{
public: 
int so[20];
char a[20];

}

```
then too its not sorting.........

---

### Post by MadCow108 on 2009-10-24
it is not clear what you want to do. Please clarify

do you want to sort the arrays independently from each other?
then you have to sort them both:
```

std::sort(peak.so,peak.so+peaks);
std::sort(peak.ea,peak.ea+peaks);

```

if you want them sorted with some relative ordering add them to a compound data structure.
pseudo example with using std pair:
```

std::vector<std::pair<int,char> > values;

for (...)
peak.values[i]= make_pair(value1,value2);

std::sort(peak.values.begin(),peak,values.end());

```

sort also takes a function object or pointer to a user generated comparison function, otherwise it uses the default (if available)

---

### Post by abhilashm86 on 2009-10-24
> **MadCow108 said:**
> it is not clear what you want to do. Please clarify

do you want to sort the arrays independently from each other?
then you have to sort them both:
```

std::sort(peak.so,peak.so+peaks);
std::sort(peak.ea,peak.ea+peaks);

```

if you want them sorted with some relative ordering add them to a compound data structure.
pseudo example with using std pair:
```

std::vector<std::pair<int,char> > values;

for (...)
peak.values[i]= make_pair(value1,value2);

std::sort(peak.values.begin(),peak,values.end());

```

sort also takes a function object or pointer to a user generated comparison function, otherwise it uses the default (if available)

as i'm having peaks of different sizes....
i need to sort so(south-east), finally using that so array, i need to output the names ,that is shown in char a, 
there should be common relation among so and names char a, so that i output names of peak according to variable so........

---

### Post by abhilashm86 on 2009-10-24
i'e got till so far, sorting is working fine......
whats about with names char a
```
#include<iostream>
using namespace std;

class pos
{
public: 
	char so[20], ea[20], alti[20];
 	char a[20];
};

class peaks
{
 public:
	int peak;
	pos pa;
};



int sort(int peakss)
{
peaks p;
p.peak=peakss;
int temp;
for(int i=0;i<p.peak;i++)
{
 cout<<"enter peak name, south-east, north-west, altitude"<<endl;
 cin>>p.pa.a[i]>>p.pa.so[i]>>p.pa.ea[i]>>p.pa.alti[i];
}

   
  for(int i=0;i<p.peak;i++)
 {
 	for(int j=i+1;j<p.peak;j++)
	{
 		if(p.pa.so[j]<p.pa.so[i])
		{
			temp=p.pa.so[i];
			p.pa.so[i]=p.pa.so[j];
			p.pa.so[j]=temp;
		}
	}
 }
 

cout<<" sorted peaks are"<<endl;
 for(int i=0;i<p.peak;i++)
 {
 	cout<<p.pa.so[i]<<p.pa.a[i]<<endl;
 }
}


int main()
{
 int temp; 
 cout<<"enter no of peaks"<<endl;
 cin>>temp;
 sort(temp);
}

```

---

### Post by MadCow108 on 2009-10-24
using separate arrays is the wrong approach if I understand correctly
put related stuff into a single data structure and sort the whole thing

have a look at my std::pair example above again

also you should use the generic std:sort algorithm instead of very inflexible (and inefficient) O(N^2) algorithm

---

### Post by abhilashm86 on 2009-10-24
please help with my code, i'm stuck, i used similar data strucutre,
but the sorting is just with numerals but not with so[] array.......
```

#include<iostream>
using namespace std;

struct pos
{
 
	int peak;
	int so[20], ea[20], alti[20];
 	char a[20];
};

 
int main()
{
 int temp; 
 cout<<"enter no of peaks"<<endl;
 int peakss;
 cin>> peakss;
 struct pos p;
 for(int i=0;i<peakss;i++)
{
 cout<<"enter peak name, south-east, north-west, altitude"<<endl;
 cin>>p.a[i]>>p.so[i]>>p.ea[i]>>p.alti[i];
}

   
  for(int i=0;i<peakss;i++)
 {
 	for(int j=i+1;j<peakss;j++)
	{
 		if(p.so[j]<p.so[i])
		{
			temp=p.so[i];
			p.so[i]=p.so[j];
			p.so[j]=temp;
		}
	}
 }



cout<<" sorted peaks are"<<endl;
 for(int i=0;i<peakss;i++)
 {
 	cout<<p.so[i]<<p.a[i]<<endl;
 }

}



```

its good if you can edit my code and point at my mistake, its giving a lot trouble, even its simpler problem.........

---

### Post by MadCow108 on 2009-10-24
you keep posting the same code
have you even tried my suggestions?

if they don't account to your problem please provide some clear information on what you want
what is the problem? whats the input? what should be the output? by which means should the output be archived? which side effects should the operation have except form the output? etc.

and have a look at this:
(out of place)
[http://www.cplusplus.com/reference/algorithm/sort/](http://www.cplusplus.com/reference/algorithm/sort/)
[http://www.cplusplus.com/reference/algorithm/stable_sort/](http://www.cplusplus.com/reference/algorithm/stable_sort/)
[http://www.cplusplus.com/reference/algorithm/partial_sort/](http://www.cplusplus.com/reference/algorithm/partial_sort/)
(in place)
[http://www.cplusplus.com/reference/algorithm/sort_heap/](http://www.cplusplus.com/reference/algorithm/sort_heap/)
these algorithms should solve all your sorting needs

---

### Post by dwhitney67 on 2009-10-24
I think that the OP wants to sort the peaks by name, and meanwhile keep the stats about each peak together with the peak name, as it is sorted.

The OP's problem stems from inexperience.  He hasn't envisioned the problem scope fully enough, much less considered a design.  He simply leaped for the keyboard and started writing (hacking) code.

Here's a solution (albeit perhaps not the best), that prompts the user for the necessary information, and then displays the data in a sorted fashion.  It would be better if the data were to come from a file rather than from user input.
```

#include <iostream>
#include <string>
#include <map>
#include <iterator>


struct PeakStats
{
   std::string peakName;
   std::string southEast;
   std::string northWest;
   std::string altitude;
   //int         peak;         // this is never used

   friend std::ostream& operator<<(std::ostream& os, const PeakStats& ps)
   {
      os << "Peak Name : " << ps.peakName << "\n"
         << "South-East: " << ps.southEast << "\n"
         << "North-West: " << ps.northWest << "\n"
         << "Altitude  : " << ps.altitude;

      return os;
   }
};

typedef std::map<std::string, PeakStats>  Peaks;
typedef std::pair<std::string, PeakStats> PeakPair;


std::ostream& operator<<(std::ostream& os, const PeakPair& pp)
{
   os << pp.second;
   return os;
}

int main()
{
   using namespace std;

   Peaks peaks;

   while (true)
   {
      string input;

      cout << "\n\nEnter peak name (or <RTN> if done): ";
      getline(cin, input);

      if (input.size() == 0) break;

      PeakStats ps;
      ps.peakName = input;

      cout << "Enter South-East: ";
      getline(cin, ps.southEast);

      cout << "Enter North-West: ";
      getline(cin, ps.northWest);

      cout << "Enter altitude: ";
      getline(cin, ps.altitude);

      // Insert new record in the map; if this record is not
      // unique, the previous record will be overwritten.
      // The map automatically sorts its records using the key,
      // which in this case, I've elected to use the Peak Name.
      peaks.insert(make_pair(ps.peakName, ps));
   }

   cout << "\n\n" << "Sorted List of Peaks:\n\n";
   copy(peaks.begin(), peaks.end(), ostream_iterator<PeakPair>(cout, "\n\n"));
}

```

@ OP -- Noticed that I refrained from using the tab-key in my code, and instead utilized the big key at the center of my keyboard... the space bar.  It makes the code more readable.  Ditto for the naming convention I chose for the variables of the structure.

Let me know if this solution fails to meet your requirements.

---

### Post by abhilashm86 on 2009-10-26
> **dwhitney67 said:**
> I think that the OP wants to sort the peaks by name, and meanwhile keep the stats about each peak together with the peak name, as it is sorted.

The OP's problem stems from inexperience.  He hasn't envisioned the problem scope fully enough, much less considered a design.  He simply leaped for the keyboard and started writing (hacking) code.

 
  
Let me know if this solution fails to meet your requirements.
thanks a lot.......
yes it was same what i needed, using arrays in a strucutre and then sorting one didn't solve my problem?
i thought when we create an object of class, in heap the memory is shared, even the variables memory, so if i sort one object, other gets automatically sorted:) 
i've no experince in programming!! just still student, sorry for long delay in replying, i'd other work:)

---

### Post by dwhitney67 on 2009-10-26
> **abhilashm86 said:**
> thanks a lot.......
yes it was same what i needed, using arrays in a strucutre and then sorting one didn't solve my problem?
i thought when we create an object of class, in heap the memory is shared, even the variables memory, so if i sort one object, other gets automatically sorted:) 
i've no experince in programming!! just still student, sorry for long delay in replying, i'd other work:)

What you need to define is a record (ie a struct or class) in which the data is kept together as one unit.  Then, if required, you define an array of these records, or use some other type of container (ie vector, map, etc).

I chose a map because it performs the sorting for me as I insert a new record.  If you are taking a C++ class, the intent of the exercise may be for you to implement a sorting algorithm.  Thus using the built-in sorting algorithm of the STL map may not be permissible in your situation.

You can continue to use the inefficient bubble-sort that you have employed earlier, or try some other sorting algorithm.  For now, just do whatever is easiest.  And whatever you do, for your strings, do not use the C-style char*; use the C++ STL string class.  It saves a lot of headaches.

---

