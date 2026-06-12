---
title: "C++: map with custom compare"
date: 2013-07-19
forum: Programming Talk
---

### Post by erotavlas on 2013-07-19
#include <iostream>
#include <map>


class MapCompare { // a more complicated comparison function which varies according to specified parameter s
   public:
      MapCompare(const int size_) : size(size_) {};        
      bool operator()(const int* x,const int* y) 
      {
          for(int i = 0; i < size; i++)
          {
              if(x[i] < y[i])
              {
                  return true;
              }
              else if(x[i] > y[i])
              {
                  return false;
              }
              return true; // if they are equal
          }
      } 
   private:
      int size;
};


int main ()
{
    static int N=4;
    int array1[N];
    int array2[N];
      
    int * array1_ptr=array1;  
      
    int * array2_ptr=array2;  
    for (int i = 0; i < N; i++)
    {
        array1_ptr[i] = 2;
        array2_ptr[i] = 3;
    } 
    
        for (int i = 0; i < N; i++)
    {
        std::cout << array1_ptr[i] << " ";
    } 
    
    
  std::map<int*, int, MapCompare> myMap(MapCompare(N));
 
     myMap[array1_ptr] = 3;
  
      myMap[array2_ptr] = 4;
      
      for(std::map<int*, int, MapCompare>::const_iterator it = myMap.begin(); it != myMap.end(); it++)
     {
         std::cout << "my map " << it->second << std::endl;
     } 
  return 0;
}

---

### Post by MG&amp;TL on 2013-07-19
What's your question? If you're just showing some code, cool, but you might want to say as much.

---

### Post by erotavlas on 2013-07-19
My code does not compile:

```

code.c:51:19: error: invalid types ‘std::map<int*, int, MapCompare>(MapCompare)[int*]’ for array subscript
code.c:53:20: error: invalid types ‘std::map<int*, int, MapCompare>(MapCompare)[int*]’ for array subscript
code.c:55:67: error: request for member ‘begin’ in ‘myMap’, which is of non-class type ‘std::map<int*, int, MapCompare>(MapCompare)’
code.c:55:88: error: request for member ‘end’ in ‘myMap’, which is of non-class type ‘std::map<int*, int, MapCompare>(MapCompare)’

```

Where us the error?

---

### Post by GeneralZod on 2013-07-19
Please use code tags!

The error is in the line:

```

std::map<int*, int, MapCompare> myMap(MapCompare(N));

```

Google for "most vexing parse".

Edit:

Also, install clang and try compiling with clang++ for a further hint :)

---

### Post by erotavlas on 2013-07-19
Ok, thank you. Now the comparator works.
I have updated my code. I cannot understand why if I try to find inside the map I don't find anything. The map contains as key the address of the array. 

```

#include <iostream>
#include <map>


class MapCompare { // a more complicated comparison function which varies according to specified parameter s
   public:
      MapCompare(const int size_) : size(size_) {};        
      bool operator()(const int* x,const int* y) 
      {
          for(int i = 0; i < size; i++)
          {
              if(x[i] < y[i])
              {
                  return true;
              }
              else if(x[i] > y[i])
              {
                  return false;
              }
              return true; // if they are equal
          }
      } 
   private:
      int size;
};


int main ()
{
    static int N=4;
    int array1[N];
    int array2[N];
      
    int * array1_ptr=array1;  
      
    int * array2_ptr=array2;  
    for (int i = 0; i < N; i++)
    {
        array1_ptr[i] = 2;
        array2_ptr[i] = 2;
        array1_ptr[0] = 1;
        array2_ptr[0] = 3;
        array2_ptr[N-1] = 1;
    } 
    
        for (int i = 0; i < N; i++)
    {
        std::cout << array1_ptr[i] << " ";
    } 
    std::cout << std::endl;
    
        for (int i = 0; i < N; i++)
    {
        std::cout << array2_ptr[i] << " ";
    } 
    std::cout << std::endl;
        
  std::map<int*, int, MapCompare> myMap((MapCompare(N)));
 
     myMap[array1_ptr] = 3;
  
      myMap[array2_ptr] = 4;
      
      for(std::map<int*, int, MapCompare>::const_iterator it = myMap.begin(); it != myMap.end(); it++)
     {
         std::cout << "my map " << it->first << " " << it->second << std::endl;
     } 
          
     std::map<int*, int, MapCompare>::const_iterator it = myMap.find(array2_ptr);
     if(it != myMap.end())
     {
         std::cout << "my map " << it->first << " " << it->second << std::endl; 
     }
     else
         std::cout << "not found" << std::endl;
     
     
     
     
  return 0;
}

```

---

### Post by GeneralZod on 2013-07-19
In your "for" loop, you only ever compare one pair of elements.

Edit:

Also, read this: you are disobeying the contract.

[http://www.cplusplus.com/reference/map/map/key_comp/](http://www.cplusplus.com/reference/map/map/key_comp/)

---

### Post by erotavlas on 2013-07-20
Of course, I want to compare less pairs as possible to speed up the key comparison. It seems that the error was in the return value when the elements are equal.

```


class MapCompare { // a more complicated comparison function which varies according to specified parameter s
   public:
      MapCompare(const int size_) : size(size_) {};        
      bool operator()(const int* x,const int* y) 
      {
          for(int i = 0; i < size; i++)
          {
              if(x[i] < y[i])
              {
                  return true;
              }
              else if(x[i] > y[i])
              {
                  return false;
              }
          }
          return false; // if they are equal -> The error
      } 
   private:
      int size;
};


```

Thank you for your help.

---

### Post by erotavlas on 2013-07-20
My final question. It is legal to declare a class that contains a map with custom compare like this?
```

class MyClass {
    public:
    MyClass(const int N_):N(N_){
        myMap.clear();
    
    };

    private:
        int N;
    
        typedef std::map<unsigned int*, int, MapCompare> MyMap;
         MyMap myMap(MapCompare(N));    
};
        
};

```

I get the following error:

```

In constructor &#8216;MyClass::MyClass(int)&#8217;:
error: &#8216;((MyClass*)this)->MyClass::myMap&#8217; does not have class type

```

---

### Post by GeneralZod on 2013-07-20
```

class MyClass { 
    public: 
    MyClass(const int N_):N(N_), myMap(MapCompare(N)) { 
        myMap.clear(); 
     
    }; 
 
    private: 
        int N; 
     
        typedef std::map<unsigned int*, int, MapCompare> MyMap;
         MyMap myMap;    
};


```

---

