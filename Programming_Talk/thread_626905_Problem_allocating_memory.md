---
title: "Problem allocating memory"
date: 2007-11-29
forum: Programming Talk
---

### Post by theotick on 2007-11-29
I'm new to linux and learning C++. I'm working on a project that requires a dynamic two dimensional array. I wrote the following class but when I compile (compiles fine) and run I can't allocate an array larger than 5x5( 25 integers):

```
class vectorArray{
   private:
      int nRow, nCol;
      int * localArray;
   public:
      int pRow, pCol;
      int arraySize;
      vectorArray( int, int );
      ~vectorArray();
      int accessArray( int, int);
      void modifyArray( int, int, int );
};
vectorArray::vectorArray( int a, int b ){
   localArray = new (nothrow) int[nRow*nCol];
   if( localArray == 0 ){
      cout << "Memory not allocated:: Exiting"<< endl;
      exit(1);
   }
   nRow = a;
   nCol = b;
   pRow = nRow;
   pCol = nCol;
   arraySize = (nRow*nCol)-1;
}
int vectorArray::accessArray( int arow, int acolumn){
   return( localArray[(arow*nCol)+acolumn] );
}
void vectorArray::modifyArray( int arow, int acolumn, int nvalue){
   localArray[(arow*nCol)+acolumn] = nvalue;
}
vectorArray::~vectorArray(){
   delete localArray;
}

```

The laptop I'm using isn't a powerhouse but free -m shows 40mb of free memory so shouldn't I be able to allocate up to 10million integers? Can anyone help?

---

### Post by hod139 on 2007-11-29
Your problem is that you are using nRow and nCol before setting them.  Also, using exceptions with new is better than checking for 0. Try
```

vectorArray::vectorArray( int a, int b ) {
   //**Set nRow and nCol before using in new**
   nRow = a;
   nCol = b;
   localArray=NULL;  // should always have pointers point to NULL
   try
   {
      localArray = new int[nRow*nCol];
   }
   catch (std::bad_alloc &ba) 
   { 
       std::cout << "Memory not allocated:: Exiting"<< std::endl;        
       exit(1);
   }
...

```

---

### Post by theotick on 2007-11-29
Yes that was it, thank you :)

---

### Post by hod139 on 2007-11-29
No problem.  Can you please mark the thread as resolved.  

Also, I should also point out that your code leaks.  Your destructor should be
```

delete[] localArray

```

---

### Post by iharrold on 2007-11-29
You should get in the habit of putting the class variables in the class constructor implementation... like this from hod's help

```
class vectorArray
{
   private:
      int nRow, nCol;
      int * localArray;
   public:
      int pRow, pCol;
      int arraySize;
      vectorArray( int, int );
      ~vectorArray();
      int accessArray( int, int);
      void modifyArray( int, int, int );
};

vectorArray::vectorArray( int a, int b ):
    nRow(a),
    nCol(b),
    localArray(NULL),
    pRow(a),
    pCol(b),
    arraySize((a*b)-1)
{
   try
   {
      localArray = new int[nRow*nCol];
   }
   catch (std::bad_alloc &ba)
   {
      cout << "Memory not allocated:: Exiting"<< endl;
      exit(1);
   }
}
int vectorArray::accessArray( int arow, int acolumn){
   return( localArray[(arow*nCol)+acolumn] );
}
void vectorArray::modifyArray( int arow, int acolumn, int nvalue){
   localArray[(arow*nCol)+acolumn] = nvalue;
}
vectorArray::~vectorArray(){
   delete[] localArray;
}
```

---

