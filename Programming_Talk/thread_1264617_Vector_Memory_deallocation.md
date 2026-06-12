---
title: "Vector: Memory deallocation"
date: 2009-09-12
forum: Programming Talk
---

### Post by krisfrajer on 2009-09-12
Hi
I am working in my c++ program. I have been learning c++ on my own time and I never really understood the concept of deallocating memory for pointers. I never deallocate pointers mainly because it seems to me there are always other objects that own the data where the pointers are pointing to, or the pointer address is just transmitted into other functions. Let me illustrate this with an example. Next is a chunk of my code. 


[For the following code the lines of question are the beginning of the function AddFile2plot(handling ptr to CMBase file), the line label 500 and the call of AddFile2Plot(handling vectors)]

//%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
//Begin of sample data
//%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

void APIanalyzer::AddFile2Plot(CMBaseFile *CMFile, list<TMultiGraph *> &mg, 
			       int nCanvas, int nbins)
{
  vector<t_data> *rebinX=new vector<t_data>();  //Need to initialize pointer 
                                                //because of line 500 (further down)
  vector<t_data> *rebinY=&vector<t_data>();     //Another way to do it... it is legal 
                                                //but is it proper? I get a warning
                                                //when compiling:

// src/APIanalyzer.cxx: In member function ‘void APIanalyzer::AddFile2Plot(CMBaseFile*,
// std::list<TMultiGraph*, std::allocator<TMultiGraph*> >&, int, int)’:
// src/APIanalyzer.cxx:282: warning: taking address of temporary


  int totalSrcNchannels=CMFile->GetNoOfChannels();
  int totalNewNbins=0;

  //Are we plotting normalized data, or just count data. 
  //Also are we using calibrated data or channel axis?
  //This section is good for this. 
  vector<t_data> srcX(CMFile->GetChannelsData());
  vector<t_data> srcY(CMFile->GetCountsData());



  //CASE 1: no rebinning has been requested
  if(nbins==1){
    rebinX=&srcX;
    rebinY=&srcY;
  }

  //CASE 2: rebinning data has been requested
  if(nbins>1){
    if(nbins<totalSrcNchannels){

      if(totalSrcNchannels%nbins != 0){
	totalNewNbins=(totalSrcNchannels - (totalSrcNchannels%nbins))/nbins +1;
      }	
      else
	totalNewNbins=totalSrcNchannels/nbins;

      for(int i=0;i<totalNewNbins-1;i++){   //-1 to consider the cases of (totalNewNbins%nbins) != 0
	t_data YSum=0;
	for(int j=0;j<nbins;j++){
	  YSum+=srcY[(i*nbins)+j];
	}
	(*rebinX).push_back(i*nbins);   //LINE 500.... just a label
	(*rebinY).push_back(YSum);
      }

      //Taking care of calculating last bin in new rebinned array
      int binCounter=totalNewNbins-1;
      t_data YSum=0;
      if(totalSrcNchannels%nbins == 0){  //adds the last bin normally
	for(int j=0;j<nbins;j++){
	  YSum+=srcY[(binCounter*nbins)+j];
	}
      }	
      else{                          //last bin must be added taking care of truncation
	for(int j=0;j<totalSrcNchannels%nbins;j++){
	  YSum+=srcY[(binCounter*nbins)+j];
	}
      }
      (*rebinX).push_back(binCounter*nbins);
      (*rebinY).push_back(YSum);
    }
    else if(nbins>=totalSrcNchannels){
      cout << "Rebining parameter cannot be larger than the number of bins in original data array" << endl;
      cout << "Original size array=" << totalSrcNchannels << ". \"nbins\" requested=" << nbins << endl;
    }
  }
  
  if(nbins<1){
    cout << "WARNING: Rebining parameter must be bigger or equal to 1" << endl;
    cout << "Aborting rebining procedures..." << endl;
  }


  APIanalyzer::AddFile2Plot(*rebinX,*rebinY,CMFile->GetName(), mg, nCanvas);
}

//Notice in the last line I send the addresses of the vector into the next function.
//My question is, do I need to allocate the memory pointed by rebinX and rebinY?



void APIanalyzer::AddFile2Plot(vector<t_data> &x, vector<t_data> &y, string plotName, 
			       list<TMultiGraph *> &mg, int nCanvas)
{
  TGraph *gr;
  TMultiGraph *myMg;
  int n;

  //Defines the total number of points to load in the graph.
  //The total number of points is the smallest size value between x and y data arrays.
   if(x.size() > y.size())
     n=y.size();
   else
     n=x.size();

   gr=new TGraph(n);
   //Load X-Y points to graph
   for(int i=0;i<n;i++)
     gr->SetPoint(i,x[i],y[i]);
   
   gr->SetName(plotName.c_str());
   gr->SetMarkerColor(colour_marker++);
   gr->SetMarkerStyle(21);
   gr->SetMarkerSize(0.4);
   
   //Adds file to proper TMultiGraph container.
   //Notice since it is a list container, there is no direct access to each element in the
   //list. Hence, here we traverse the list searching for the object we want.
   list<TMultiGraph *>::iterator it=mg.begin();
   for(int i=0;i<TOTALCANVAS;i++){
     if(it==mg.end()) {
       cout << "End of list reached!!!!" << endl;
       exit(1);
     }
     if(i==nCanvas){
       myMg = *it;
       myMg->Add(gr);
     }
     it++;
   }
}

//%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
//End of sample data
//%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%


So in a nutshell, I create a couple of pointer vectors which I had to initialize. The data gets stored in these vectors and then I send this vectors to another function. In that function the pointer's data is copied to a graph object. At that point I could deallocate the memory... maybe c++ does it for me?

This is a very specific example of my application. I hope it is not to confusing...

Thxs for your comments!
kris

---

### Post by dribeas on 2009-09-12
Writting big blocks of (even worse, unformatted use the [ CODE ] tag) code does not help you or others. Focus on the part of the code where you have a problem that will focus and make life nicer to everyone. If you have more than one question just ask as many as you wish. I will answer about the first part (I just got to read a couple of lines)...

```

void f()
{
   std::vector<int>* x = new std::vector<int>();
}
void g()
{
   std::vector<int>* x = &std::vector<int>();
}
void h()
{
   std::vector<int> x;
}

```

In the first function you are loosing memory. You are requesting memory from the system in the heap. That memory must be released by the program (either manually or through RAII). When the function goes out of scope the vector and all its contents will still be alive and unreacheable.

In the second function there is a different problem (and that is what the compiler is trying to warn you about). The right hand side of the equals is creating an std::vector in the stack as an unnamed temporary and you are then obtaining the address. The scope of the unnamed temporary is really thin, and it will be freed right after the execution unit has completed (the ; ), thus you will have a pointer that points to an already deleted vector.

The third case is what you should usually do: declare the vector variable directly in the stack (do not create a pointer to it, just use the object itself). As the vector is a named variable, its scope will be that of the block of code ({ ... }) and after the closing curly brace is hit, the vector will be deleted and the memory released.

In C++ you should avoid dealing with pointers, limit the usage to where you cannot use other things (arguments should be passed by reference instead of pointer, locals should be declared in the stack whenever possible). If you need to use heap allocated memory, use smart pointers to take care of resource management.

Each time a raw pointer appears in code, you have to consider who is the owner of that object and who is responsible of deleting it or if you are leaking memory.

P.S: Your code could use some refactoring... long functions are harder to read and keep track of. Divide into smaller functions that take care of smaller subproblems.

---

### Post by krisfrajer on 2009-09-12
Thanks for making things clear. I can totally see how using

void h()
{
   std::vector<int> x;
}


seems to be the best approach since the compiler will take care of the allocation and deallocation of memory. However there will be some times where pointers are really needed (right?). What is the proper way of deleting the pointer and to make sure the memory got deallocated properly.

Example:


void f()
{
   std::vector<int>* x = std::vector<int>();
   for(int i=0;i<x.size();i++)
      (*x).push_back(i);                

   myPrint(*x);

//delete[] x;  ///Can't do that here... it segments fault. It seems like the vector's
               ///memory got deallocated at the end of myPrint function.

}
void myPrint(std::vector<int> &x)
{
   for(int i=0;i<x.size();i++)
      cout << i << '=' << x[i] << endl;
}

Actually, it this last code I am totally illustrating my first question in my post but in simpler way (I will keep that in mind for any future post. Thxs for the advise :)

Last question, is there a way to find/locate memory leaks in my program? I am learning how to use ddd. Could  use it for this task?

Thxs,
kris

---

### Post by MadCow108 on 2009-09-12
in c++ you mostly don't use pointers, you use references.
they are indicated with the & symbol in function definitions.

if you really want to use pointers (for example for polymorphism), then match you new's with equal amount of deletes.
If you don't need that then use the capabilities of c++ and write code without new's and deletes
but here's your code with new:
```

void f()
{
std::vector<int> *x  = new std::vector<int>();
for(int i=0;i<5;i++)
x->push_back(i); 

myPrint(x);

delete x; // no [], because you just allocated one vector not array of vectors

}
void myPrint(std::vector<int> *x)
{
for(int i=0;i<x->size();i++)
cout << i << '=' << x->at(i) << endl;
}

```

doing that without the new is much simpler and you don't have to worry about deleting.
especially with vectors this makes limited sense. I can't think of a situation were you need a dynamically allocated vector (the memory of vectors is dynamic anyway)

I also recommend that you have a look at smart pointers: what you should have a look at are smart pointers: [http://www.boost.org/doc/libs/1_40_0/libs/smart_ptr/smart_ptr.htm](http://www.boost.org/doc/libs/1_40_0/libs/smart_ptr/smart_ptr.htm)
they allow you to nearly forget about delete even in situations where you need pointers.

a good tool to find memory leaks is valgrind.

btw copying stuff from a vector into a TGraph can done like this too (I suspect your working with ROOT):
```
TGraph * gr = new TGraph(vecX.size(),&vecX[0],&vecY[0]);
```
this works because the vector internally saves the data in a C style array, so the pointer to the first element is equivalent to a pointer to C style array.

---

### Post by dribeas on 2009-09-12
> **krisfrajer said:**
> However there will be some times where pointers are really needed (right?). What is the proper way of deleting the pointer and to make sure the memory got deallocated properly.

In general RAII, in particular smart pointers. First smart pointers: they are objects that are stack allocated and keep pointers to heap allocated memory. They receive the memory during construction and will release it on destruction. They have slight differences in behavior, and each can be a little more suited for each particular problem. I most often use the boost smart pointers even though many compilers already support TR1 smart pointers:

```

struct T {};
void f()
{
   boost::shared_ptr< T > p( new T() );  // equivalently std::tr1::shared_ptr with STLs that implement TR1
   boost::scoped_ptr< T> p2( new T() ); // std::tr1::scoped_ptr

   std::auto_ptr< T > p3( new T() ); // good old standard... not recommended
}
// in all cases memory will be freed when they smart pointer goes out of scope.

```

The main difference is in the semantics. auto_ptr has the weirdest semantics: only one auto_ptr has responsibility for management. The managed memory can be passed from one auto_ptr to another, the receiving auto_ptr will release the memory at the end. It cannot be used in standard containers and that limits usage. 

Scoped pointer has unique owner semantics and ownership cannot be passed from one pointer to another. It should be used whenever the ownership will not be changed from one smart pointer to another (a class that holds its own resources, as the implementation of a container, or temporary heap allocated memory inside a function).

Shared pointer implements shared ownership. Many different shared pointers can share ownership of an object. When the last existing shared_ptr goes out of scope the memory will be freed. While there is at least one shared pointer holding the resource it will be alive. It is the most common smart pointer to use, and while slightly less efficient than the others (during construction, copying and destruction) it can be used in all contexts. All smart pointers are about the same in all other usage contexts (dereferencing...)

Resource Acquisition Is Initialization is  a technique in that each object gets its resources during construction and releases then during destruction. That is what is happening with all smart pointers, and in containers as std::vector. During construction the vector implementation requests memory from the heap for the stored objects (the real contents of a vector are always heap allocated). When the vector goes out of scope, the destructor is called and it takes care of releasing the allocated memory.

A naive implementation of a smart pointer could look like this: (notice that this is just as an exercise):

```

template <typename T>
class single_ownership_ptr
{
public:
   single_ownership_ptr( T * data ) : data_( data ) {}
   ~single_ownership_ptr() { delete data_; }
   T& operator*() { return *data_; }
   T* operator->() { return data_; }
private:
   T * data_;
};

// usage
struct Data {};
void f()
{
   single_ownership_ptr<Data> p( new Data ); // the smart pointer takes ownership of the data
   // ..
} // ~single_ownership_ptr() is called and it deletes the pointer received in construction.

```

Real implementations of smart pointers are more complex, but in principle equivalent.

---

### Post by dribeas on 2009-09-12
> **MadCow108 said:**
> 
```
TGraph * gr = new TGraph(vecX.size(),&vecX[0],&vecY[0]);
```
this works because the vector internally saves the data in a C style array, so the pointer to the first element is equivalent to a pointer to C style array.

True, just to put a little more emphasis in that: the standard requires all implementations of vector to store data in a contiguous block of memory.

---

### Post by MadCow108 on 2009-09-12
```
vector<t_data> *rebinY=&vector<t_data>(); //Another way to do it... it is legal 
//but is it proper? I get a warning
//when compiling:
```
edit: this is wrong, see dribeas post below
here you create a temporary vector<t_data>() which usually get destroyed at the semicolon. but because you assign it to a pointer it exists until the scope of the pointer ends. so this is equivalent to:
editend
```

vector<t_data> rebinY_;
vector<t_data> * rebinY = &rebinY_;

```
this is again a stack allocated vector object. It gets deleted when the scope ends

It is not the same as this:
```
vector<t_data>* rebinY = new std::vector<t_data>();
```
this vector you have to delete to retrieve the memory.

---

### Post by krisfrajer on 2009-09-13
Thanks a lot for your comments. They are really useful. I have tried using 

vector* v = &vector();

It work fine except for the warning and the danger of operation on a thin scope as previously described in a  former post. I was able to follow the behavior of this vector using ddd and the destruction of the object happened at the end of the scope of the pointer. My next step is to learn valgrind. Hopefully it will assist me finding memory leaks in my program. As a final note, just to try to keep my code clear and neat I will lean to use proper object allocation and use references instead of pointers, again as advise in a former post. I am sure pointer will come handy sooner or later. Would it be true the following statement: if I use pointers in c++ is technically considered mixing c and c++ in my programs? 


Thxkss for the Graph tip. Yes I am using ROOT. I am in my final stage of my program were my data is being passed to ROOT environment for analysis and display. That comment makes things more clear and it will come handy.

Cheers,
Kris

---

### Post by dwhitney67 on 2009-09-13
> **krisfrajer said:**
> Thanks a lot for your comments. They are really useful. I have tried using 

vector* v = &vector();
...

Just because something can be done, it is not sufficient justification to actually do it.  I can think of no reason why the pointer to a vector should ever be used, when it is easier/safer to pass it by reference.

In C++, always declare your objects on the stack unless you meet one of the following criteria:  1)  The object you require is very large (ie. occupies a lot of memory), or 2) requires information only available _after_ the application is running (ex. you need to allocate N items, where N is not known until runtime). 

If you must allocate, there are "smart pointers" available for use.  Available to use are the auto_ptr and the TR1 shared-pointer.  If you have Boost installed, then you have even more types available.  Click here for [Boost Smart Pointers]("http://www.boost.org/doc/libs/1_37_0/libs/smart_ptr/smart_ptr.htm"), and here for [Boost Pointer Containers]("http://www.boost.org/doc/libs/1_37_0/libs/ptr_container/doc/ptr_container.html").

P.S.  The syntax you provided above is incorrect, but I understand the gist of what you were trying to state.

---

### Post by dribeas on 2009-09-13
> **MadCow108 said:**
> ```
vector<t_data> *rebinY=&vector<t_data>(); 
```
here you create a temporary vector<t_data>() which usually get destroyed at the semicolon. but because you assign it to a pointer it exists until the scope of the pointer ends.

That is not correct. Temporaries bound to a constant reference to either the type or a base type will have their lifetimes extended (and this is explicitly stated in the standard and a not well known fact), but when you bind them to non-const references or you take the address into a pointer the lifetime of the temporary is not extended. Now, it might just seem that it was extended as the stack memory is not overwritten and as such the bits are already there.

Here is a small test to check the lifetimes of objects. We write a class that sets a value in construction and resets it to a different value on destruction. This way we can test whether the object is alive or not. The test itself is working on undefined behavior, as the second block of code is incorrect. The result of trying to get the value of X::alive after destruction of the object is undefined.

```

#include <iostream>
struct X*{
   X() : alive(true) {}
   ~X() { alive=false; }
   bool alive;
};
int main()
{
   {
      std::cout << "Block1:" << std::endl;
      X const & cr = X();
      std::cout << "still alive?" << cr.alive << std::endl;
   }
   {
      std::cout << "Block2:" << std::endl;
      X *xp = &X();
      std::cout << "still alive2?" << xp->alive << std::endl;
   }
}

```

The output of the program will be:
```

Block1
still alive?1

Block2
still alive?0

```

If you care to add traces (logs) to the destructors you will see that in the second case the destructor gets called right after the line where the pointer is created and assigned and before the message is printed.

---

