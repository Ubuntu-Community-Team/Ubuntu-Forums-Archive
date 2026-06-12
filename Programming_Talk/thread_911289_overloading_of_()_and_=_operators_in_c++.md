---
title: "overloading of () and = operators in c++"
date: 2008-09-05
forum: Programming Talk
---

### Post by monkeyking on 2008-09-05
Hi, I've written my own low-mem implementation of a matrix class.
The matrix only handles values from 0-4. which is enough for my program.

The underlying datastructures are (*char)[], arrays of array.

```

class snp{
private:
  unsigned char **alloc(int x, int y);
  unsigned char **m_data;
  size_t numItems; //this is the number of snps in each row
  size_t x; //number of rows.
  size_t y; // this is the number of hole used chars
  size_t offset; //offset

public:
  snp(int a,int b);
  snp(iMatrix *imat);
  ~snp()          {delete [] *m_data; delete [] m_data;}
  void print(bool doInt=1,char s=' ');
  int get(int a, int b);
  int items() {return ((int) numItems);}
  int height() {return (int) x;}
};

```

I've implemented the ".get()", as a charelement bitpattern extractor.
And now I want to implement a ",set" method, that should work like.

```
obj.set(a,b)=c
```

This should change the value at column=a,elemen=b to c.

I can't really figure out what I'm overloading.
I guess it would be the "=" but still, i'm using two values in a "()".

Can someone give me a hint in the right direction.

thanks

---

### Post by Martin Witte on 2008-09-05
see [this link]("http://www.parashift.com/c++-faq-lite/operator-overloading.html#faq-13.10")

---

### Post by dribeas on 2008-09-06
> **monkeyking said:**
> ```
obj.set(a,b)=c
```

There's no overloading there. Just:

```
class snp { // ...
   unsigned char& get( size_t x, size_t y ); // [*]
};
```

Of course you could overload operator () (follow the link Martin gave you) and get a more user friendly syntax:

```
class snp {
   unsigned char operator() ( size_t x, size_t y ) const; // 1
   unsigned char& operator() { size_t x, size_t y ); // 2
};
snp obj;
obj( 1, 5 ) = 6; // calls 2
int x = obj( 1 , 5 ) + 1; // calls 1, can be used through a constant reference.

```

Note that if you want to return references, these must be of the internal stored type (unsigned char in your example).

---

### Post by monkeyking on 2008-09-06
Thanks, It thought it was possible to return a bitpattern from a char in overloading, but it seems not.

---

### Post by dribeas on 2008-09-07
> **monkeyking said:**
> Thanks, It thought it was possible to return a bitpattern from a char in overloading, but it seems not.

I don't really understand what you want. What is a bitpattern to you? You can return anything that you can represent with a type. Now, you need your data type to be at least one char big. Given that, for a 4 bit pattern you will be using twice as much memory (is that a problem?). If it is a problem, you can modify your interface into something like:

```

class snp {
   void set( size_t x, size_t y, unsigned char pattern );
};

```

And internally map into the higher/lower bits of the char.

Try browsing for std::vector<bool> and the problems it has. First reference that came to mind was [GOTW#50]("http://www.gotw.ca/gotw/050.htm")

---

### Post by monkeyking on 2008-09-07
I think what I wan't to do is impossible,
but I'll elaborate on what I'm doing,
so it doesn't seem to far fetched.:)

I need store huge amount of data(dna data).
These are only of type {a,c,t,g}, or just 4 different values.
Since I only need to store 4 values, I only need 2bits for each datapoint.

There a 8bit in one char, so I'll input 4 values into one char.

an example: {2,1,3,0} is {10,01,11,00} is 10011100
So if I wanted to get the second value I would use bitwise AND with 0x30 and shift 4 to the right.

In this way I can effectively store 16 times the amount of data in memory, which will be a huge benefit, when I need to access the data.

I've implemented all the normal accessors and mutatators.
But for the sake of completeness and interface sharing with my other matrix classes, I wanted to overload the "()",
both as a mutator and an accessor.

I've spend so much time trying to write an interface wrapper function, that I've found that it is empirical impossible.
I did manege to write the accessor "()".

It seems you can't use overloading in mutators 
if your return value contain anything that depends on bitpatters,
[PHP]
class snp{
private:
  unsigned char **alloc(int x, int y);
  unsigned char **m_data;
  size_t numItems; //this is the number of snps in each row
  size_t x; //number of rows.
  size_t y; // this is the number of hole used chars
  size_t offset; //offset

public:
  snp();
  snp(int a,int b);
  snp(iMatrix *imat);
  ~snp()          {delete [] *m_data; delete [] m_data;}
  void print(bool doInt=1,char s=' ');
  void printInfo(){printf("x:%d\ty:%d\toffset:%d\tnumItems:%d\n",(int)x,(int)y,(int)offset,(int)numItems);}
  int get( uint a, uint b) const;
  void set(uint a,uint b,uint c);
  int items() {return ((int) numItems);}
  int height() {return (int) x;}
  int& operator() (uint r, uint c);//NOT IMPLEMENTED
  int operator() (uint r, uint c) const;
};

int& snp::operator() (uint r, uint c){
  //not working
}
int snp::operator() (uint r, uint c) const{
  return get(r,c);
}
[/PHP]
btw, I wouldn't make sense using bools for this.
The size of a bools is the same as a char.

---

### Post by dribeas on 2008-09-08
> **monkeyking said:**
> btw, I wouldn't make sense using bools for this.
The size of a bools is the same as a char.

Well, there is a problem in there. You can change your mutator into regular functions (.set( x, y, value ) ) and perform your operations in there. The problem with the approach you are trying is that you cannot return a reference to a temporary (if you extract, say bits 5 and 6, there is no way that you can return a reference to those two bits separate from the other 6 bits in the same char.

std::vector<bool> is space optimized, that is, the size of the structure is a constant (internal control data) plus a bit for each one of the stored values, so you could use that as an example if it just were any good. But even if it was meant to be an example to follow, it was proven to have more problems than advantages (just read the link above or search for articles on it).

Finally, using your approach will reduce your data size by a factor of 4, but it will have a runtime penalty unless you are able to come up with operations that can be parallelized to blocks of four consecutive data.

---

### Post by Zugzwang on 2008-09-08
Well, if I understand you correctly, what you are trying to do is *not* impossible. Here's a minimal example:

```
[color=#BC7A00]#include <iostream>
[/color]
[color=#008000]**class**[/color] [color=#0000FF]**Testing**[/color];

[color=#008000]**class**[/color] [color=#0000FF]**Testing_XS**[/color] {
[color=#008000]**private**[/color][color=#666666]:[/color]
    [color=#B00040]int[/color] bitpos;
    Testing [color=#666666]&[/color]parent;
    Testing_XS(Testing [color=#666666]&[/color]_parent, [color=#B00040]int[/color] _bitpos) [color=#666666]:[/color] parent(_parent) {
        bitpos [color=#666666]=[/color] _bitpos;
    };
[color=#008000]**public**[/color][color=#666666]:[/color]
    [color=#008000]**friend**[/color] [color=#008000]**class**[/color] [color=#0000FF]**Testing**[/color];
    Testing_XS [color=#008000]**operator**[/color][color=#666666]=[/color]([color=#B00040]int[/color] newvalue);
};


[color=#008000]**class**[/color] [color=#0000FF]**Testing**[/color] {
    [color=#B00040]int[/color] data;
    [color=#008000]**friend**[/color] [color=#008000]**class**[/color] [color=#0000FF]**Testing_XS**[/color];
[color=#008000]**public**[/color][color=#666666]:[/color]
    Testing() { data [color=#666666]=[/color] [color=#666666]0[/color]; };    
    Testing_XS [color=#008000]**operator**[/color]()([color=#B00040]int[/color] pos) {
        [color=#008000]**return**[/color] Testing_XS([color=#666666]*[/color][color=#008000]**this**[/color],pos);
    };
    [color=#B00040]void[/color] printValue() {
        std[color=#666666]::[/color]cout [color=#666666]<<[/color] [color=#BA2121]"The value is: "[/color] [color=#666666]<<[/color] data [color=#666666]<<[/color] [color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color];
    };
};

Testing_XS Testing_XS[color=#666666]::[/color][color=#008000]**operator**[/color][color=#666666]=[/color]([color=#B00040]int[/color] newvalue) {
    [color=#B00040]int[/color] mask [color=#666666]=[/color] ([color=#666666]1[/color] [color=#666666]<<[/color] bitpos)[color=#666666]+[/color]([color=#666666]1[/color] [color=#666666]<<[/color] (bitpos[color=#666666]+[/color][color=#666666]1[/color]));
    parent.data [color=#666666]=[/color] parent.data [color=#666666]&[/color] ([color=#666666]~[/color]mask);
    parent.data [color=#666666]+=[/color] newvalue [color=#666666]<<[/color] bitpos;
}

[color=#B00040]int[/color] main([color=#B00040]char[/color] [color=#666666]*[/color]args, [color=#B00040]int[/color] argv) {
    Testing test;
    test([color=#666666]3[/color]) [color=#666666]=[/color] [color=#666666]2[/color];
    test([color=#666666]0[/color]) [color=#666666]=[/color] [color=#666666]3[/color];
    test.printValue();
}

```

What you are trying to implement is a so-called Property. There's an article about that in C++: [http://www.codeguru.com/cpp/cpp/cpp_mfc/article.php/c4031]("http://www.codeguru.com/cpp/cpp/cpp_mfc/article.php/c4031") Basically, you don't return a reference to some bits of your object but to some object that will behave as an accessor and will look like you are actually dealing with those two individual bits by overloading the right operators.

---

### Post by dribeas on 2008-09-08
> **Zugzwang said:**
> Basically, you don't return a reference to some bits of your object but to some object that will behave as an accessor and will look like you are actually dealing with those two individual bits by overloading the right operators.

That is exactly what std::vector<bool> does. Its iterators are proxy objects into the internal data structure. But that path comes to expense of performance (time) and other problems, enough of them that some people in the C++ standard regret nowadays having pushed that implementation into STL. Note that is was meant to be _the example_ for proxied containers. But time and experience proved them wrong up to the point where some of those authors (Herb Sutter, among others) suggest using std::vector<int> to hold bool instead of the specialized std::vector<bool>. And ints take as much as 32x the memory.

---

### Post by Zugzwang on 2008-09-08
> **dribeas said:**
> That is exactly what std::vector<bool> does. Its iterators are proxy objects into the internal data structure. But that path comes to expense of performance (time) and other problems, enough of them that some people in the C++ standard regret nowadays having pushed that implementation into STL. Note that is was meant to be _the example_ for proxied containers. But time and experience proved them wrong up to the point where some of those authors (Herb Sutter, among others) suggest using std::vector<int> to hold bool instead of the specialized std::vector<bool>. And ints take as much as 32x the memory.

Whether the time penalty is OK depends on the application of the OP. Since he/she seems to be concerned with scientific applications, it's often OK to take some extra overhead (time-wise) for being able to implement an algorithm in a way looking more like the one on paper. Likewise, DNA data tends to be quite huge, so compressing the data in memory might be absolutely necessary. Also, by declaring the stuff inline and turning optimization on, good compilers should be able to optimize *some* of the overhead away. Maybe the Intel compiler will do a good job here.

The other problem mentioned in your post (and the referenced webpage) doesn't occur here, since never a reference to a non Testing_XS-object is returned, so when trying the following:

```
[color=#BC7A00]#include <iostream>
[/color]
[color=#008000]**class**[/color] [color=#0000FF]**Testing**[/color];

[color=#008000]**class**[/color] [color=#0000FF]**Testing_XS**[/color] {
[color=#008000]**private**[/color][color=#666666]:[/color]
    [color=#B00040]int[/color] bitpos;
    Testing [color=#666666]&[/color]parent;
    Testing_XS(Testing [color=#666666]&[/color]_parent, [color=#B00040]int[/color] _bitpos) [color=#666666]:[/color] parent(_parent) {
        bitpos [color=#666666]=[/color] _bitpos;
    };
[color=#008000]**public**[/color][color=#666666]:[/color]
    [color=#008000]**friend**[/color] [color=#008000]**class**[/color] [color=#0000FF]**Testing**[/color];
    Testing_XS [color=#008000]**operator**[/color][color=#666666]=[/color]([color=#B00040]int[/color] newvalue);
    [color=#008000]**operator**[/color] [color=#B00040]int[/color]();
};


[color=#008000]**class**[/color] [color=#0000FF]**Testing**[/color] {
    [color=#B00040]int[/color] data;
    [color=#008000]**friend**[/color] [color=#008000]**class**[/color] [color=#0000FF]**Testing_XS**[/color];
[color=#008000]**public**[/color][color=#666666]:[/color]
    Testing() { data [color=#666666]=[/color] [color=#666666]0[/color]; };    
    Testing_XS [color=#008000]**operator**[/color]()([color=#B00040]int[/color] pos) {
        [color=#008000]**return**[/color] Testing_XS([color=#666666]*[/color][color=#008000]**this**[/color],pos);
    };
    [color=#B00040]void[/color] printValue() {
        std[color=#666666]::[/color]cout [color=#666666]<<[/color] [color=#BA2121]"The value is: "[/color] [color=#666666]<<[/color] data [color=#666666]<<[/color] [color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color];
    };
};

Testing_XS Testing_XS[color=#666666]::[/color][color=#008000]**operator**[/color][color=#666666]=[/color]([color=#B00040]int[/color] newvalue) {
    [color=#B00040]int[/color] mask [color=#666666]=[/color] ([color=#666666]1[/color] [color=#666666]<<[/color] bitpos)[color=#666666]+[/color]([color=#666666]1[/color] [color=#666666]<<[/color] (bitpos[color=#666666]+[/color][color=#666666]1[/color]));
    parent.data [color=#666666]=[/color] parent.data [color=#666666]&[/color] ([color=#666666]~[/color]mask);
    parent.data [color=#666666]+=[/color] newvalue [color=#666666]<<[/color] bitpos;
}

Testing_XS[color=#666666]::[/color][color=#008000]**operator**[/color] [color=#B00040]int[/color]() {
        [color=#008000]**return**[/color] (parent.data [color=#666666]>>[/color] bitpos) [color=#666666]&[/color] [color=#666666]3[/color];
}

[color=#B00040]int[/color] main([color=#B00040]char[/color] [color=#666666]*[/color]args, [color=#B00040]int[/color] argv) {
    Testing test;
    test([color=#666666]3[/color]) [color=#666666]=[/color] [color=#666666]2[/color];
    test([color=#666666]0[/color]) [color=#666666]=[/color] [color=#666666]3[/color];
    test.printValue();
    std[color=#666666]::[/color]cout [color=#666666]<<[/color] [color=#BA2121]"Value at position 0 is: "[/color] [color=#666666]<<[/color] test([color=#666666]0[/color]) [color=#666666]<<[/color] [color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color];
    
    [color=#B00040]int[/color] [color=#666666]&[/color]mem [color=#666666]=[/color] test([color=#666666]0[/color]);
    [color=#B00040]int[/color] [color=#666666]&[/color]mem2 [color=#666666]=[/color] [color=#666666]&[/color](test([color=#666666]0[/color]));
}

```

... the last two lines simply won't work.

---

### Post by dribeas on 2008-09-08
> **Zugzwang said:**
> 
```

// all the same up to main, well, maybe change operator= return type to Testing_XS&
[color=#B00040]int[/color] main([color=#B00040]char[/color] [color=#666666]*[/color]args, [color=#B00040]int[/color] argv) {
    Testing test;
    test([color=#666666]3[/color]) [color=#666666]=[/color] [color=#666666]2[/color];
    test([color=#666666]0[/color]) [color=#666666]=[/color] [color=#666666]3[/color];
    test.printValue();
    std[color=#666666]::[/color]cout [color=#666666]<<[/color] [color=#BA2121]"Value at position 0 is: "[/color] [color=#666666]<<[/color] test([color=#666666]0[/color]) [color=#666666]<<[/color] [color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color];
    
// modified:
    const int& mem = test(0);
    std::cout << mem << std::endl; // 3
    test(0) = 0; 
    std::cout << mem << std::endl; // 3

    std::vector<int> v;
    v.push_back( 3 );
    const int& mem2 = v[0];
    std::cout << mem2 << std::endl; // 3
    v[0] = 0;
    std::cout << mem2 << std::endl; // 0
}

```

The modified version shows that while you cannot keep a reference, you can create a constant reference, and the behavior is different from standard containers (vector as an example).

As long as you know what you are up to, you can do anything you want, but if at any time you try to keep an external reference (constant in this case) you'll get to really fun to debug problems.

Also, adding a readonly operator() to the Testing class so that you can access to the data through a constant reference is not so simple (don't have time to actually try it, I'll try tonight).

---

