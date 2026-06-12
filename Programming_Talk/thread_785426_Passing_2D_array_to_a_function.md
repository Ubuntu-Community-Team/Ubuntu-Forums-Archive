---
title: "Passing 2D array to a function"
date: 2008-05-07
forum: Programming Talk
---

### Post by joebanana on 2008-05-07
The code is not working. I think I passed it right. Did I assign it wrong?

```

class Node{	
...
int state[4][4];
...
Node(int table[][4])
{
	Node(); 
	state = table;
}
....
}

```

compiler error:
```

make -k all 
Building file: ../Seminar.C
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"Seminar.d" -MT"Seminar.d" -o"Seminar.o" "../Seminar.C"
../Seminar.C: In constructor ‘Node::Node(int (*)[4])’:
../Seminar.C:25: error: incompatible types in assignment of ‘int (*)[4]’ to ‘int [4][4]’

```

---

### Post by mike_g on 2008-05-07
> state = table;
Unfortunately you cant copy an array like this in c++.

If its a 4*4 grid you could use 2 for loops to copy the content across. Something like:

```
for(int y=0; y<4 y++)
    for(int x=0; x<4; x++)
       state[x][y] = table[x][y];

```

---

### Post by joebanana on 2008-05-07
I didn't tried to copy an array. I tried to "give it" to the object by reference. Copying will take extra space and time...

---

### Post by escapee on 2008-05-07
In terms of passing a multidimensional array, this is correct.

Your error lies in trying to assign them one table to another entirely - it doesn't work like that.  To copy an array, you must go element by element.

Also, you are calling your default constructor from inside your parameterized constructor - if I remember correctly, all this does is create a temporary object, then destroy it outside of the constructor; not actually initializing your instance's variables.

---

### Post by joebanana on 2008-05-07
So what would be the the correct way to pass a 2D array, without copying? Is that possible?

And thanks for the constructor warning. I will make another function to call from both constructors.

---

### Post by hessiess on 2008-05-07
if you want, you can put the array into a struct, then you can just use object1 = object2.

---

### Post by dwhitney67 on 2008-05-07
Here are two possible ways.  Choose whichever you like best.  If you know that you will have fixed-sized arrays, then perhaps the style used in function2() is best.
[PHP]#include <iostream>

void function1( const int *array, const int width, const int length )
{
  int a[width][length];
  memcpy( a, array, sizeof( a ) );

  for ( int i = 0; i < width; ++i )
  {
    for ( int j = 0; j < length; ++j )
    {
      std::cout << "[" << i << "][" << j << "] = " << a[i][j] << std::endl;
    }
  }
}

void function2( const int array[][4] )
{
  int a[4][4];
  memcpy( a, array, sizeof( a ) );

  for ( int i = 0; i < 4; ++i )
  {
    for ( int j = 0; j < 4; ++j )
    {
      std::cout << "[" << i << "][" << j << "] = " << a[i][j] << std::endl;
    }
  }
}

int main()
{
  int array[4][4] = { {1,2,3,4},
                      {5,6,7,8},
                      {9,10,11,12},
                      {13,14,15,16}
                    };

  function1( &(array[0][0]), 4, 4 );
  function2( array );

  return 0;
}[/PHP]

---

### Post by Zugzwang on 2008-05-07
> **hessiess said:**
> if you want, you can put the array into a struct, then you can just use object1 = object2.

...which is still not what the OP wants.

To shed some more light on the issue: If you reserve some space in your class by taking int a[4][4], then every object of this class will not contain a pointer the "a" field, but the field itself, so you can't assign it like a pointer. If you specify the dimensions fully, you will end up with such a case. 

EDIT: My example didn't work. No idea how to fix it.

However, what you (the OP) are trying to do doesn't look like common practice.

---

### Post by joebanana on 2008-05-07
The thing is that I have an object that creates a couple of tables based on his data and creates some Nodes and then passes them the 4x4 tables. Of course it work if I copy an element by element in constructor so I will stick with that.

Comparison:
If you have one boat and you don't need it but your friend does. Do you copy the boat and give it to him or do you just give him your boat.

---

### Post by dwhitney67 on 2008-05-07
If I had to guess, the OP wants something like:

[PHP]
#include <cstring>
#include <iostream>

class Node
{
  public:
    Node()
    {
    }
.
    Node( const int table[][4] )
    {
      std::memcpy( state, table, sizeof( state ) );
    }

    // The following two methods are not necessary if the Node contains only
    // "simple" data that can easily be deep-copied.  If there are pointers,
    // etc then these methods needs to be augmented
    Node( const Node &node )
    {
      std::memcpy( state, node.state, sizeof( state ) );
    }

    Node& operator=( const Node &node )
    {
      std::memcpy( state, node.state, sizeof( state ) );
      return *this;
    }

    friend std::ostream & operator<<( std::ostream& os, const Node &node )
    {
      for ( unsigned int i = 0; i < 4; i++ )
      {
        for ( unsigned int j = 0; j < 4; ++j )
        {
          os << "state[" << i << "][" << j << "] = " << node.state[i][j] << std::endl;
        }
      }
      return os;
    }

  private:
    int state[4][4];
};

int main()
{
  int array[4][4] = {{1,2,3,4},{5,6,7,8},{9,10,11,12},{13,14,15,16}};

  Node n1 = Node( array );
  Node n2( n1 );
  Node n3;
  n3 = n2;

  std::cout << n1 << std::endl;
  std::cout << n2 << std::endl;
  std::cout << n3 << std::endl;

  return 0;
}
[/PHP]

P.S.  Sorry for reorganizing the code; my belief is that the public section should come first, the private section last.

---

### Post by joebanana on 2008-05-07
Thanks for the info. Really appreciated. I just thought that I could just throw a pointer from Node on the table. You know like passing by reference. But copying memory is more elegant solution than copying element by element.

---

### Post by WW on 2008-05-07
A combination of dwhitney67's code and hessiess's suggestion for using a struct.  By wrapping the matrix in a struct, it allows the use of the default C++ copy mechanism, so now you *can* say **state = m;** instead of using memcpy.

```

#include <cstring>
#include <iostream>

typedef struct
{
    int matrix[4][4];
} matrix_t;

class Node
{
  public:
    Node()
    {
    }
    
    Node( const matrix_t &m )
    {
      state = m;
    }

    Node( const Node &node )
    {
      state = node.state;
    }

    friend std::ostream & operator<<( std::ostream& os, const Node &node )
    {
      for ( unsigned int i = 0; i < 4; i++ )
      {
        for ( unsigned int j = 0; j < 4; ++j )
        {
          os.width(3);
          os << node.state.matrix[i][j] << " ";
        }
        os << std::endl;
      }
      return os;
    }

  private:
    matrix_t state;
};

int main()
{
  matrix_t m1 = { {{1,2,3,4},{5,6,7,8},{9,10,11,12},{13,14,15,16}} };
  matrix_t m2 = m1;

  Node n1 = Node(m1);
  Node n2(n1);
  Node n3;
  n3 = n2;
  Node n4(m2);

  std::cout << "n1 =\n" << n1 << std::endl;
  std::cout << "n2 =\n" << n2 << std::endl;
  std::cout << "n3 =\n" << n3 << std::endl;
  std::cout << "n4 =\n" << n4 << std::endl;

  return 0;
}

```

Compile and run:
```

$ g++ -Wall statetest.cpp -o statetest
$ ./statetest 
n1 =
  1   2   3   4 
  5   6   7   8 
  9  10  11  12 
 13  14  15  16 

n2 =
  1   2   3   4 
  5   6   7   8 
  9  10  11  12 
 13  14  15  16 

n3 =
  1   2   3   4 
  5   6   7   8 
  9  10  11  12 
 13  14  15  16 

n4 =
  1   2   3   4 
  5   6   7   8 
  9  10  11  12 
 13  14  15  16 

$ 

```

I don't know if this is really preferable or not, but I found it educational to try it out. :)

---

### Post by dwhitney67 on 2008-05-07
> **WW said:**
> 
I don't know if this is really preferable or not, but I found it educational to try it out. :)
He He!  That's why I am always on this forum.  On a day to day basis I don't spend too much time thinking of the basics of C or C++ programming, but these little exercises keep things fresh in my head.

---

### Post by Fixman on 2008-05-07
If you want to pass it by reference, you can

```

class Node{	
...
int *state[4][4];
...
Node(int *table[][4])
{
	Node(); 
	state = table;
}
....
}

```

So, to see state[a, b] you must use *state[a][b], and to call the function you can call it as

```

int thing[4][4] ;
Node (&thing) ;

```

Note that if you want to pass a pointer (like state) you must not &.

---

### Post by dwhitney67 on 2008-05-07
Fixman -

I am quite certain that what you have proposed will not work.  Please review your work and post again if you have another solution.

P.S.  It is my understanding that you are proposing:
[PHP]class Node
{
  public:
    Node ( int *array[][4] )
    {
       //...
    }
};

int main()
{
  int array[4][4];

  Node node( &array );
}[/PHP]

This code will NOT compile.

---

