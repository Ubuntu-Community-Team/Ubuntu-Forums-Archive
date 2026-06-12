---
title: "g++: Cannot compile template class functions"
date: 2011-05-07
forum: Programming Talk
---

### Post by Kentucky88 on 2011-05-07
I am trying to compile the ESP library located here: [http://nn.cs.utexas.edu/?esp](http://nn.cs.utexas.edu/?esp).  The code is old and I had to make some modifications to it in order to compile.  However, I am stumped on how to get the Population class to compile:

Population.h
[PHP]
#ifndef _POPULATION_H_
#define _POPULATION_H_

/*! \file Population.h
 */

//! A NeuronPop class
#include <typeinfo>
#include <stdio.h>
#include <vector>
#include <functional>
#include "Network.h"

using namespace std;

class Neuron;
class Network;


template<class T>
class Population {

public:
  Population(int, T&);
  ~Population();
  //  Population(const Population &s);
  void create();
  //  virtual void create(int, int, int); // creates a random subpopulation of neurons
  struct max_fit : public std::binary_function<T*, T*, bool> {
    bool operator()(T *x, T *y) { return x->getFitness() > y->getFitness(); }
  };  
  void destroyIndividuals();

  void map( double (*map_fn)(T*))
  {
      typename std::vector<T*>::iterator i;
    for(i = individuals.begin(); i != individuals.end(); ++i)
      map_fn(i);
  }
  void mapv( void (T::*map_fn)())
  {
      typename std::vector<T*>::iterator i;
    for(i = individuals.begin(); i != individuals.end(); ++i)
      (*i->*map_fn)();
  }

  T* operator[](int i);
  void evalReset();
  T* selectRndIndividual(int i = -1);
  void average();
  void qsortIndividuals();
  void mutate(double);
  void deltify(T*);
  void popIndividual();
  void pushIndividual(T*);
  double getAverageFitness();
  inline unsigned int getNumIndividuals() { return individuals.size(); }
  inline T* getIndividual( int i ) { return individuals[i]; }
  inline unsigned int getNumBreed() { return numBreed; }
  inline void setNumBreed( int n ) { if(n > 0) numBreed = n; }
  inline int getMaxID() { return maxID; }

  std::vector<T*> individuals;  

protected:
  T &exemplar;
  bool evolvable; 
  T *bestIndividual;
  // std::vector<T*> elite;
  bool created;
  unsigned int numBreed;  //make this an Esp member of NE as percent breed
  int maxID;
};

/*

class ProbNeuron;


template< class T >
class NeuronCluster: public NeuronPop< T > {//change to public NeuronPop?
public:
  int id;
  NeuronCluster() 
    : NeuronPop<T>(0,0)
  {
    static int counter = 0;
    id = counter++;
  }
  void create() {}  //!< cannot create
  void empty();
  void pushNeuron(ProbNeuron *n);
  void deltify(Neuron *) {} 
  //These must gooooooooo
  void crossoverAvg(const std::vector<double> &parent1, 
            const std::vector<double> &parent2, 
            std::vector<double> &child1, 
                std::vector<double> &child2);
};
 
*/ 
typedef Population<Neuron> NeuronPop;
typedef Population<Network> NetworkPop;

#include "Population.C"
#endif

[/PHP]Population.c:
[PHP]
//////////////////////////////////////////////////////////////////////
//
// Population
//
//////////////////////////////////////////////////////////////////////

#include <iostream>
#include <algorithm>
#include <numeric>
#include <typeinfo>
#include "Neuron.h"
#include "Population.h"

///////////////////////////////////////////////////////////////////////
/*!  We leave method \a create to 
     actually create the neurons.
     \todo mentioned elsewhere: numBreed needs to be a percentage 
     that is set by the algorithm
*/
template< class T >
Population<T>::Population(int size, T &ex)  
  : exemplar(ex),
    evolvable(true),
    individuals(size),
    //elite(),
    created(false),
    maxID(0)
{
  //T* tmp;
  //assert(NULL != dynamic_cast<Neuron*>(tmp) ||
  //     NULL != dynamic_cast<Network*>(tmp) );
  // T *tmp = new T();
  //assert(NULL != dynamic_cast<Neuron*>(tmp));
  numBreed =  (unsigned int) individuals.size()/4;
}

//-----------------------------------------------------------------------------------
//---------------------------------------------------------------------
//! Create the Population.
/*! Create the random Population set the member \a created to \c true.  
    \todo { get rid of \c evolvable; return \c bool; output message to stderr
    if called when created = \c true}
*/
template< class T >
void Population<T>::create() 
{
  if(!created)
    if(evolvable){
      for (unsigned int i = 0; i < individuals.size(); ++i) {
    individuals[i] = exemplar.clone();
    individuals[i]->create();
      }
      created = true;
    }
  maxID = individuals.back()->getID();
  bestIndividual = individuals.front();
}


//---------------------------------------------------------------------
//! destructor
template< class T >
Population<T>::~Population()
{
  destroyIndividuals();
}


//--------------------------------------------------------------------
//! Destroy the Neurons in the Population.
/*! The Neurons are destroyed without deleting the
    Population.  If \a create is called after calling
    this method new neurons will be create and placed
    in the Population.
 */
template< class T > 
void Population<T>::destroyIndividuals()
{
  cout << "destroying individuals\n"; 
  
  for (unsigned int i = 0; i < individuals.size(); ++i)    
    delete individuals[i];
  created = false;
}


//----------------------------------------------------------------------
template< class T >
T* Population<T>::operator[](int i)
{
  if((i >= 0) && (i < individuals.size()))
    return individuals[i];
  else
    cerr << "Index out of bounds\n ";
}


//----------------------------------------------------------------------
//! reset fitness and test vals of all Neurons
/*! \todo Change name to reset? Change \c Network::resetFitness() to
    \c Network::reset() or change \c Neuron::reset() to \c 
    Neuron::resetFitnes()
 */
template< class T >
void Population<T>::evalReset()
{
  mapv(&T::resetFitness);
}
/*
  for(unsigned int i=0; i < individuals.size(); ++i)  {
    individuals[i]->resetFitness();
  }
}
*/


//----------------------------------------------------------------------
//! select an individual at random
template< class T >
T* Population<T>::selectRndIndividual(int i)
{
  if((i > 0) && (i < (int) individuals.size()))
    return individuals[lrand48() % i];
  else
    return individuals[lrand48() % individuals.size()];
}


//----------------------------------------------------------------------
//! Sort the neurons by fitness in each NeuronIndividuals. 
/*!
    using quicksort.
 */
template< class T >
void Population<T>::qsortIndividuals()
{
  sort(individuals.begin(), individuals.end(), max_fit() );
  bestIndividual = individuals.front(); 
}


//----------------------------------------------------------------------
//! Mutate half of the neurons with cauchy noise.
/*! \todo Should be a \a NeuroEvolution or \a Neuron method
 */
template< class T >
void Population<T>::mutate(double mutrate)
{
  for (unsigned int i = numBreed*2 ; i < individuals.size(); ++i) 
    if (drand48() < mutrate) 
      individuals[i]->mutate();
}


//---------------------------------------------------------------------
//! Used to perform "delta-coding" like burst mutation.
/*! Make each Neuron a perturbation of the neuron in 
    the best network that corresponds to that \a subIndividuals.
\todo { change name to burst mutation }
*/
template< class T >
void Population<T>::deltify(T *best)
{
  //  Neuron tmp = *individuals[0];
  for(unsigned int i= 0; i < individuals.size(); ++i){
    individuals[i]->perturb( best );  
  }
}


//! Remove an individual from the \a Population.
/*!
   */


template< class T >
void Population<T>::popIndividual()
{
  if(individuals.size() > 0){
    delete  individuals.back();
    individuals.pop_back();
  }
}

//! Add an individual to the \a Population.
/*!
  The individual is added to the \a Population by pushing the pointer to it
  onto the back of the std::vector \c individuals.  
 */
template< class T >
void Population<T>::pushIndividual(T *n)
{
  if(n->getID() > maxID) maxID = n->getID(); // keep track of newest indiv.

  individuals.push_back( n );
}

template< class T >
double Population<T>::getAverageFitness()
{
  double sum = 0;

  for (unsigned int i = 0 ; i < individuals.size(); ++i) 
    sum += individuals[i]->getFitness();
  return sum/individuals.size();
}


//-----------------------------------------------------------------------------
template <class T>
ostream& operator<<(ostream& os, Population<T> &p)
{
  for(unsigned int i=0; i < p.getNumIndividuals(); ++i)
    os << *p.getIndividual(i) << endl;
  
  return os;
}

[/PHP]When I include Population.h as shown above, every single function in the .c file claims that it has been previously defined.  If I remove Population.h, I get an error on the constructor claiming that Population does not define a type.  Every function below also errors as follows.  I did some reading on this issue and it seems to be related to typedef / typename.  But I don't see anything wrong.

Description    Path    Resource    Location    Type
‘Population’ does not name a type    /ESPcpp    Population.C    line 21    C/C++ Problem
expected unqualified-id before ‘template’    /ESPcpp    Population.C    line 44    C/C++ Problem
‘Population’ does not name a type    /ESPcpp    Population.C    line 63    C/C++ Problem
expected unqualified-id before ‘template’    /ESPcpp    Population.C    line 76    C/C++ Problem
expected initializer before ‘<’ token    /ESPcpp    Population.C    line 89    C/C++ Problem
expected initializer before ‘<’ token    /ESPcpp    Population.C    line 105    C/C++ Problem
expected initializer before ‘<’ token    /ESPcpp    Population.C    line 120    C/C++ Problem
expected initializer before ‘<’ token    /ESPcpp    Population.C    line 135    C/C++ Problem
expected initializer before ‘<’ token    /ESPcpp    Population.C    line 147    C/C++ Problem
expected initializer before ‘<’ token    /ESPcpp    Population.C    line 162    C/C++ Problem
expected initializer before ‘<’ token    /ESPcpp    Population.C    line 177    C/C++ Problem
expected initializer before ‘<’ token    /ESPcpp    Population.C    line 191    C/C++ Problem
expected initializer before ‘<’ token    /ESPcpp    Population.C    line 199    C/C++ Problem
‘Population’ has not been declared    /ESPcpp    Population.C    line 211    C/C++ Problem
expected ‘,’ or ‘...’ before ‘<’ token    /ESPcpp    Population.C    line 211    C/C++ Problem
‘p’ was not declared in this scope    /ESPcpp    Population.C    line 213    C/C++ Problem

---

### Post by GeneralZod on 2011-05-07
First things first: rename population.c to population.cpp, and update all the references to population.c.

What is the command-line call you are using to compile it?

Edit: 

With the change I suggested, and after removing #include "Neuron.h" and "Network.h" (which you probably need to do as you likely have those files), I can get it to compile via

```

g++ population.h

```

Edit2:

Actually, that apparently compiles it into a pre-compiled header - no errors, though :)

---

### Post by Kentucky88 on 2011-05-07
It shouldn't compile into a pre-compiled header.  I renamed .C to .cpp and it didn't make a difference.  I'm trying to compile this project through Eclipse CDT.  It executes a makefile which produces the following output:

**** Build of configuration Debug for project ESPcpp ****

make all 
Building file: ../Population.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"Population.d" -MT"Population.d" -o"Population.o" "../Population.cpp"
In file included from ../Population.cpp:11:0:
../Neuron.h: In member function &#8216;int Neuron::newID()&#8217;:
../Neuron.h:61:53: warning: no return statement in function returning non-void
../Population.cpp: At global scope:
../Population.cpp:21:1: error: &#8216;Population&#8217; does not name a type
../Population.cpp:44:1: error: expected unqualified-id before &#8216;template&#8217;
../Population.cpp:63:1: error: &#8216;Population&#8217; does not name a type
../Population.cpp:76:1: error: expected unqualified-id before &#8216;template&#8217;
../Population.cpp:89:14: error: expected initializer before &#8216;<&#8217; token
../Population.cpp:105:16: error: expected initializer before &#8216;<&#8217; token
../Population.cpp:120:14: error: expected initializer before &#8216;<&#8217; token
../Population.cpp:135:16: error: expected initializer before &#8216;<&#8217; token
../Population.cpp:147:16: error: expected initializer before &#8216;<&#8217; token
../Population.cpp:162:16: error: expected initializer before &#8216;<&#8217; token
../Population.cpp:177:16: error: expected initializer before &#8216;<&#8217; token
../Population.cpp:191:16: error: expected initializer before &#8216;<&#8217; token
../Population.cpp:199:18: error: expected initializer before &#8216;<&#8217; token
../Population.cpp:211:34: error: &#8216;Population&#8217; has not been declared
../Population.cpp:211:44: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;<&#8217; token
../Population.cpp: In function &#8216;std::ostream& operator<<(std::ostream&, int)&#8217;:
../Population.cpp:213:29: error: &#8216;p&#8217; was not declared in this scope
make: *** [Population.o] Error 1

Can you compile with the g++ arguments that I used above?


> **GeneralZod said:**
> First things first: rename population.c to population.cpp, and update all the references to population.c.

What is the command-line call you are using to compile it?

Edit: 

With the change I suggested, and after removing #include "Neuron.h" and "Network.h" (which you probably need to do as you likely have those files), I can get it to compile via

```

g++ population.h

```Edit2:

Actually, that apparently compiles it into a pre-compiled header - no errors, though :)

---

### Post by dwhitney67 on 2011-05-08
The implementation of the code for a template class _must_ be included within the header file; you cannot place the code in a separate .cpp file.

For example:
```

#ifndef FOO_H
#define FOO_H

// Declare class here
//
template <typename T>
class Foo
{
public:
   Foo(T& item);

   //...

   T getItem() const;

private:
   T myItem;
};


// Implement class here
//
template <typename T>
Foo<T>::Foo(T& item)
   : myItem(item)
{
}

template <typename T>
T Foo<T>::getItem() const
{
   return myItem;
}

#endif

```


P.S.  An alternative is to place the implementation code in a .impl file which will not be compiled directly.  This file is included in the header file.
```

#ifndef FOO_H
#define FOO_H

// Declare class here
//
template <typename T>
class Foo
{
public:
   Foo(T& item);

   //...

   T getItem() const;

private:
   T myItem;
};

**#include "Foo.impl"**

#endif

```

---

