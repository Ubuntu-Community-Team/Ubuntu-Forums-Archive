---
title: "for loop in calss constructor c++"
date: 2008-11-20
forum: Programming Talk
---

### Post by abraxas334 on 2008-11-20
My problem is the following:
I have a class and if i try to assign a 3 dimensional dynamical array with in the constructor i get a segmentation fault and stepping through the for loops as shown below with gdb does not work.

However if i instead intialise the 3 d array in a class member function i have no problem to initalise the array. Why is this? it doesn't matter too much, but it would be nice to have the array initialised in the constructor.


[PHP]

class cMonteCarlo3D
{
public:
    static const int size = 256; //in my actual program this is definited in a parent class cMonteCarlo and cMonteCarlo3D is public of cMonteCarlo
    void setArray();
    cMonteCarlo3D();
    ~cMonteCarlo3D();
private:
    int ***_array;

};
cMonteCarlo3D::cMonteCarlo3D() //constructor
{
    
    int arraysize = size;
   
    cout<<"Initialising 3D lattice space"<<endl;
    for (int i = 0; i<size; i++)
    {
        cout<<i<<endl;
    }
    if(_array!=0){
        _array  = NULL;cout<<"pointer is not null"<<endl;}
    _array = new int** [arraysize];
    
    for(int i = 0; i<arraysize; i++)
    {
       _array[i]= new int* [arraysize];
    
        for (int j =0; j<arraysize; j++)
        {
            _array[i][j] = new int[arraysize];
            for (int k = 0; k<256; k++)
            {
                cout<<i<<" "<<j<<" "<<k<<endl;
                _array[i][j][k] = -10;
            }
        }
    }
}
//this fails and when i step through with gdb and i j and k don't seem to get any values assigned and i get a seg fault

//if however i initialise the array in a function and not in the constructor (i.e. and exmpty constructor it works just fine)
void cMonteCarlo3D::setArray()
{
    int arraysize = size;
      if(_array!=0){
        _array = NULL;cout<<"pointer is not null"<<endl;}
    _array = new int** [arraysize];
    
    for(int i = 0; i<arraysize; i++)
    {
       _array[i]= new int* [arraysize];
    
        for (int j =0; j<arraysize; j++)
        {
            _array[i][j] = new int[arraysize];
            for (int k = 0; k<256; k++)
            {
                //cout<<i<<" "<<j<<" "<<k<<endl;
                _array[i][j][k] = -10;
            }
        }
    }

}


[/PHP]

Anyone got any ideas why this could be?
Thanks

---

### Post by SledgeHammer_999 on 2008-11-20
> **abraxas334 said:**
> My problem is the following:
I have a class and if i try to assign a 3 dimensional dynamical array with in the constructor i get a segmentation fault and stepping through the for loops as shown below with gdb does not work.

However if i instead intialise the 3 d array in a class member function i have no problem to initalise the array. Why is this? it doesn't matter too much, but it would be nice to have the array initialised in the constructor.


[PHP]

class cMonteCarlo3D
{
public:
    static const int size = 256; //in my actual program this is definited in a parent class cMonteCarlo and cMonteCarlo3D is public of cMonteCarlo
    void setArray();
    cMonteCarlo3D();
    ~cMonteCarlo3D();
private:
    int ***_array;

};
cMonteCarlo3D::cMonteCarlo3D() //constructor
{
    
    int arraysize = size;
   
    cout<<"Initialising 3D lattice space"<<endl;
    for (int i = 0; i<size; i++)
    {
        cout<<i<<endl;
    }
    if(_array!=0){
        _array  = NULL;cout<<"pointer is not null"<<endl;}
    _array = new int** [arraysize];
    
    for(int i = 0; i<arraysize; i++)
    {
       _array[i]= new int* [arraysize];
    
        for (int j =0; j<arraysize; j++)
        {
            _array[i][j] = new int[arraysize];
            for (int k = 0; k<256; k++)
            {
                cout<<i<<" "<<j<<" "<<k<<endl;
                _array[i][j][k] = -10;
            }
        }
    }
}
//this fails and when i step through with gdb and i j and k don't seem to get any values assigned and i get a seg fault

//if however i initialise the array in a function and not in the constructor (i.e. and exmpty constructor it works just fine)
void cMonteCarlo3D::setArray()
{
    int arraysize = size;
      if(_array!=0){
        _array = NULL;cout<<"pointer is not null"<<endl;}
    _array = new int** [arraysize];
    
    for(int i = 0; i<arraysize; i++)
    {
       _array[i]= new int* [arraysize];
    
        for (int j =0; j<arraysize; j++)
        {
            _array[i][j] = new int[arraysize];
            for (int k = 0; k<256; k++)
            {
                //cout<<i<<" "<<j<<" "<<k<<endl;
                _array[i][j][k] = -10;
            }
        }
    }

}


[/PHP]

Anyone got any ideas why this could be?
Thanks

Don't know what is the problem. I tried to run your program but it took too long to print the numbers so I set size to "56". After some time it crushed. I then set the size to "10" and it worked. Maybe it is a "not enough memory" problem?

here's my calling code:
[php]
#include <iostream>
using namespace std;
class cMonteCarlo3D
{
public:
    static const int size = 10; //in my actual program this is definited in a parent class cMonteCarlo and cMonteCarlo3D is public of cMonteCarlo
    void setArray();
    cMonteCarlo3D();
    ~cMonteCarlo3D();
private:
    int ***_array;

};
cMonteCarlo3D::cMonteCarlo3D() //constructor
{

    int arraysize = size;

    cout<<"Initialising 3D lattice space"<<endl;
    for (int i = 0; i<size; i++)
    {
        cout<<i<<endl;
    }
    if(_array!=0){
        _array  = NULL;cout<<"pointer is not null"<<endl;}
    _array = new int** [arraysize];

    for(int i = 0; i<arraysize; i++)
    {
       _array[i]= new int* [arraysize];

        for (int j =0; j<arraysize; j++)
        {
            _array[i][j] = new int[arraysize];
            for (int k = 0; k<256; k++)
            {
                cout<<i<<" "<<j<<" "<<k<<endl;
                _array[i][j][k] = -10;
            }
        }
    }
}

cMonteCarlo3D::~cMonteCarlo3D()
{
}
//this fails and when i step through with gdb and i j and k don't seem to get any values assigned and i get a seg fault

//if however i initialise the array in a function and not in the constructor (i.e. and exmpty constructor it works just fine)
void cMonteCarlo3D::setArray()
{
    int arraysize = size;
      if(_array!=0){
        _array = NULL;cout<<"pointer is not null"<<endl;}
    _array = new int** [arraysize];

    for(int i = 0; i<arraysize; i++)
    {
       _array[i]= new int* [arraysize];

        for (int j =0; j<arraysize; j++)
        {
            _array[i][j] = new int[arraysize];
            for (int k = 0; k<256; k++)
            {
                //cout<<i<<" "<<j<<" "<<k<<endl;
                _array[i][j][k] = -10;
            }
        }
    }

}

int main ()

{
cMonteCarlo3D pf;
cout << "Class created!!!!\n";
}
[/php]

---

### Post by Tony Flury on 2008-11-20
just a thought - when you debug it i,j & k might be getting optimised away - I have seen odd things like that.

try putting printfs in the code at the start of each loop - and see how i,j,k are changing.

Also you might want to use asserts to ensure that new is returning real pointers and not NULLs.

---

### Post by Zugzwang on 2008-11-21
Search for the cause of the segfault first. Use [valgrind]("http://ubuntuforums.org/showthread.php?t=828018") for that. Did you added the "-g" compile switch? Otherwise, you cannot debug properly. Also add "-O0" in order to prevent all optimisations.

---

### Post by Kazade on 2008-11-21
I'm gonna go ahead and give some constructive criticism :)

OK, firstly.. dynamically managing your own memory in a 3D array is a bit crazy. It makes everything require more code and more difficult to maintain. Especially seeing as the size is fixed to 256 at the point of compilation (I'm assuming the one in the parent class is static const?). You could do this:

```

int myarray[size][size][size]; 

```

(I think that should work as it's an integral type, I might be wrong). That way you reduce the code, the risk of memory leaks and crashes. The problem is that the array might get too big for the stack IIRC. 

So instead you can make use of nested std::vectors, e.g.:

```

#include <vector>
using std::vector;

class cMonteCarlo3D
{
public:
        static const int size = 256; 
        void setArray();
        cMonteCarlo3D();
        ~cMonteCarlo3D();
private:
	typedef vector<vector<vector<int> > > MyArrayType;
    	MyArrayType _array;
};

cMonteCarlo3D::cMonteCarlo3D() //constructor
{
	_array.resize(size);
	
	for (int i = 0; i < size; ++i) {
		_array[i].resize(size);

		for (int j = 0; j < size; ++j) {
			_array[i][j].resize(size);
			
			for (int k = 0; k < size; ++k) {
				_array[i][j][k] = -10;
			}
		}
	}   
}
```

This way you don't need to worry about leaks (vectors clean up after themselves), you can resize the arrays dynamically and you can use the arrays with STL functions. 

Secondly, this check is not going to work:
```

    if(_array!=0){
        _array  = NULL;cout<<"pointer is not null"<<endl;}

```

The reason being that, you never set it to NULL. If it *is* NULL it's likely that you are running in debug mode, or your compiler just happened to do it for you. This isn't guaranteed, chances are pointers will be initialized to something random. You won't need to worry about this if you use vectors anyway.

---

### Post by abraxas334 on 2008-11-21
> 
So instead you can make use of nested std::vectors, e.g.:


yep you are so right, i prefer vectors by far, have changed it to a 3d vector now, my only hesitation was that i need the program to be fairly fast, as i am doing MC simulation, tho i guess vectors don't slow down the program that much, as i won't ever have to loop over the entire 3d _lattice apart from the start, when setting initial values.

Thanks

---

### Post by Kazade on 2008-11-21
Vectors store their elements contiguously (in the same was as normal arrays) and if you use iterators to access the data, because the iterators are bidirectional, your compiler may actually use pointers and pointer arithmetic to move between elements. So if there is any performance decrease it will be marginal.

---

### Post by hod139 on 2008-11-21
If your data is going to be sparse you can consider using a map to store the values instead of the 3D vector:
```

std::map<std::pair<int,int>, int> sparseMatrix;

```This will be more memory efficient, but less processor efficient.  Use whichever is more applicable for you :)

---

### Post by psusi on 2008-11-21
> **Tony Flury said:**
> just a thought - when you debug it i,j & k might be getting optimised away - I have seen odd things like that.

Compile with -O0 ( that's an upper case o and a zero ) to disable optimization, and -g for full debugging symbols if you plan on using gdb.

> **Tony Flury said:**
> 
Also you might want to use asserts to ensure that new is returning real pointers and not NULLs.

No need; new can not return NULL.  If it can't allocate the memory, it throws an exception.

---

