---
title: "c++ syntax doens't compile in g++"
date: 2009-11-21
forum: Programming Talk
---

### Post by lemonsf on 2009-11-21
Greetings, 

Just trying to compile some code, and I get a compiling error. The source and compilation commands are below. 
```

struct Vector3
{
        float x, y, z;
	Vector3( float _x, float _y, float _z )
	{
		x = _x;
		y = _y;
		z = _z;
	}
	Vector3 operator+( Vector3& b )
	{
		Vector3 result = *this;
		result.x + b.x;
		result.y + b.y;
		result.z + b.z;
		return result;
	}
};

int main( int argc, char** argv )
{
	Vector3 a( 1.0f, 2.0f, 3.0f );
	Vector3 result = a + Vector3( 2.0f, 3.0f, 4.0f ); 
	return 0;
}

```
To compile...
```

g++ test.cpp -o test

```
Which produces this lovely sonnet...
```

test.cpp: In function ‘int main(int, char**)’:
test.cpp:26: error: no match for ‘operator+’ in ‘a + Vector3(2.0e+0f, 3.0e+0f, 4.0e+0f)’
test.cpp:13: note: candidates are: Vector3 Vector3::operator+(Vector3&)

```
According to the error, the operator doesn't seem to support a constructor on the RHS, this seems like g++ being a bit picky, but I'm thinking there might be a reason for this. I'm surprised I haven't come across this before, but if anyone could enlighten me on this issue it would be greatly appreciated.

Many thanks.

---

### Post by johnl on 2009-11-21
I would guess that the problem is that your operator function accepts a reference.  When you call Vector3(/* ... */), that can't be coerced to a reference since it's a temporary variable.  



I could be wrong :)

---

### Post by jimi_hendrix on 2009-11-21
Keep this guide in your pocket for operator overloads: [http://en.wikibooks.org/wiki/C%2B%2B_Programming/Operators/Operator_Overloading#Arithmetic_operators]("http://en.wikibooks.org/wiki/C%2B%2B_Programming/Operators/Operator_Overloading#Arithmetic_operators")

---

### Post by lemonsf on 2009-11-21
You are correct johnl, I should have spotted that! Funny VC++ doesn't complain about it... 

But then again it doesn't complain about this either..
```

int main( int, char** )
{
}

```

Cheers jimi_hendrix, added to my notes... many thanks

---

### Post by dwhitney67 on 2009-11-21
> **lemonsf said:**
> You are correct johnl, I should have spotted that! Funny VC++ doesn't complain about it... 

About what?.... this?
```

result.x + b.x;
result.y + b.y;
result.z + b.z;

```
Perhaps you wanted (and have figured out), that this is needed:
```

result.x += b.x;
result.y += b.y;
result.z += b.z;

```
Btw, if you have no intention to modify object 'b', then you should declare it as a const; similarly if you do not intend to modify 'this', then define the method as const.
```

Vector3 operator+( const Vector3& b ) const

```

---

### Post by lemonsf on 2009-11-22
> **dwhitney67 said:**
> About what?.... this?
```

result.x + b.x;
result.y + b.y;
result.z + b.z;

```

Not quite, VC++ doesn't complain about 
```

Vector3 result = a + Vector3( 2.0f, 3.0f, 4.0f ); 

```
It seems that VC will just take the "Vector3( 2.0f, 3.0f, 4.0f );" part and reference it temporarily. Allowing it to compile, where as g++ requires another line....
```

Vector3 tmp( 2.0f, 3.0f, 4.0f );
Vector3 result = a + tmp; 

```  
Not too sure what the c++ standard says on this, and whether g++ is just being a bit fussy.

Many thanks

P.S As you said dwhitney67, and as I have read elsewhere... the addition operator should use a compound operator to perform its function.

---

### Post by dwhitney67 on 2009-11-22
> **lemonsf said:**
> Not quite, VC++ doesn't complain about 
```

Vector3 result = a + Vector3( 2.0f, 3.0f, 4.0f ); 

```
It seems that VC will just take the "Vector3( 2.0f, 3.0f, 4.0f );" part and reference it temporarily. Allowing it to compile, where as g++ requires another line....
```

Vector3 tmp( 2.0f, 3.0f, 4.0f );
Vector3 result = a + tmp; 

```  

gcc does not require anything different; only that you fix the warnings about non-effectual statements.  The code you originally posted works under Linux, with the fixes as I indicated earlier.

Try for yourself:
```

#include <iostream>

class Vector3
{
public:
   Vector3( float _x, float _y, float _z )
   {    
      x = _x;   
      y = _y;   
      z = _z;   
   }    

   Vector3 operator+( const Vector3& b ) const
   {    
      Vector3 result = *this;
      result.x += b.x;
      result.y += b.y;
      result.z += b.z;
      return result;
   }    

   friend std::ostream& operator<<(std::ostream& os, const Vector3& v)
   {    
      os << "x = " << v.x << ", "
         << "y = " << v.y << ", "
         << "z = " << v.z;
      return os;
   }    

private:
   float x, y, z;
};

int main()
{
   using namespace std;

   Vector3 a( 1.0f, 2.0f, 3.0f );
   cout << a << endl;

   Vector3 result = a + Vector3( 2.0f, 3.0f, 4.0f );
   cout << result << endl;

   return 0;
}

```

P.S.  The only thing that is missing from my/your code is a copy-constructor; fortunately the compiler provides one... let's just hope that the variables x, y, and z are always initialized to 0 (zero).

---

### Post by lemonsf on 2009-11-22
#-o ... well I stand corrected, I think I should change the title to be "can't use g++ with non-effectual statements" to which the answer would be "and?", never noticed before what bad coding practices MS pollutes me with...Many thanks again dwhitney67.

---

