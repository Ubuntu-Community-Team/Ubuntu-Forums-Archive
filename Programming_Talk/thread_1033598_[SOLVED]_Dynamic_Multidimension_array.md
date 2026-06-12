---
title: "[SOLVED] Dynamic Multidimension array?"
date: 2009-01-07
forum: Programming Talk
---

### Post by Zeotronic on 2009-01-07
C++: Recently, I have come to need (or at least think I do) to put a resizable multidimensional array into a class. Now I *know* that using vector arrays isn't a good way to do this... what would be a good way to do this?

---

### Post by hod139 on 2009-01-07
> **Zeotronic said:**
> C++: Recently, I have come to need (or at least think I do) to put a resizable multidimensional array into a class.

First step is to know what you need.

> 
 Now I *know* that using vector arrays isn't a good way to do this... what would be a good way to do this?I would always suggest using STL vectors instead of C style arrays, so I don't know what you mean here.  For an example:

[php]
template <typename T>
class Matrix{
  private:
     std::vector<std::vector<T> > multiArray;  
};
[/php]

---

### Post by Zeotronic on 2009-01-07
> I would always suggest using STL vectors instead of C style arrays, so I don't know what you mean here. For an example:
I've searched the subject rather thoroughly trying to solve my problem myself, and I'm pretty sure your example turns out like crap. Each array contained in an array (in your example) would have to be resized to the proper size to have a standard sized second dimension, would they not? And I need to work with up to 3 or 4 dimensions, so this approach simply would not do.

But that is... as I said... to my knowledge.

---

### Post by hundredwatt on 2009-01-07
> **Zeotronic said:**
> C++: Recently, I have come to need (or at least think I do) to put a resizable multidimensional array into a class. Now I *know* that using vector arrays isn't a good way to do this... what would be a good way to do this?

Perhaps something like this:
```
//create 5x5 array
int** array = new int*[5];
int row1[5] = {1,2,3,4,5};
int row2[5] = {6,7,8,9,10};
...
array[0]= &row1[0];
array[1] = &row2[0];

cout << array[0][1]; //2
cout << array[1][2]; //8

//change to 6x6 array;
int** temp = array;
delete[] array;
array = new int*[6];
...//copy data

```

Does this help? With this model, its easy to make a 5 dimensional array where each branch is a different length. You can also generalizes this to more dimensions with int*** array or int**** array:

```
int*** array = new int**[5];
int** branch1 = new int*[5];
int branch1row1[5] = {1,2,3,4,5};
branch1[0] = &branch1row1[0];
array[0] = &branch1[0];
cout << array[0][0][2]; //3

```

---

### Post by Wybiral on 2009-01-07
How about a hashtable that takes some two-value X,Y object as keys? In this case, you could expand it indefinitely, and you can just assume some default value for all the keys that aren't set.

---

### Post by escapee on 2009-01-07
What are you doing that you think you need 3-4 dimensions for?  If you let us know what it is that you're aiming for we can likely be of more help to you.

And the thing with vectors is that they resize themselves, you don't have to manage it.  If you need another item, push it on.

---

### Post by dwhitney67 on 2009-01-07
> **Zeotronic said:**
> I've searched the subject rather thoroughly trying to solve my problem myself, and I'm pretty sure your example turns out like crap. 
Ouch; tough remark to make to someone considering that person was trying to help you.

---

### Post by dwhitney67 on 2009-01-07
The easiest solution when dealing with multidimensional arrays is to use the array type as defined in the boost libraries.

Here's an example:
[php]
#include <boost/array.hpp>
#include <iostream>

int main()
{
  typedef boost::array<int,    3> OneD;
  typedef boost::array<OneD,   3> TwoD;
  typedef boost::array<TwoD,   3> ThreeD;
  typedef boost::array<ThreeD, 3> FourD;

  FourD array4D;

  array4D[0][0][0][0] = 10;
  array4D[1][1][1][1] = 20;
  array4D[2][2][2][2] = 30;

  std::cout << "array4D[0][0][0][0] = " << array4D[0][0][0][0] << std::endl;
  std::cout << "array4D[1][1][1][1] = " << array4D[1][1][1][1] << std::endl;
  std::cout << "array4D[2][2][2][2] = " << array4D[2][2][2][2] << std::endl;

  return 0;
}
[/php]

---

### Post by Zeotronic on 2009-01-07
> Ouch; tough remark to make to someone considering that person was trying to help you. 
I'm sorry I'm so blunt.

But am I not correct in that, using so may vector arrays just to get a 3 dimensional array would incur *vast* amounts of waste? We're talking all the extra data required by a vector, multiplied by *what*?
> What are you doing that you think you need 3-4 dimensions for?
As far as the 3 dimensions goes. I'm storing voxel information... I think I've taken the instance where I needed 4 dimensions out of my code.
> How about a hashtable that takes some two-value X,Y object as keys?
I'm not familiar with hashtables.
> Perhaps something like this:
I'll toy around with that, but wouldn't "int** temp = array;" merely point to what's contained by array, and then, of course, it would be deleted in the next line?
> The easiest solution when dealing with multidimensional arrays is to use the array type as defined in the boost libraries.
Array handles multidimensional arrays? I thought only Multi_Array did!.. and I couldn't get that to work in a structure... this will work?

...Oh wait... I see. Wouldn't that be almost as bad as vector?

---

### Post by Wybiral on 2009-01-07
> **Zeotronic said:**
> I'm not familiar with hashtables.

You can use std::map as the hashtable, and std::pair for the keys of a 2-dimensional table.

```

#include <map>
#include <iostream>

typedef std::pair<int,int> vec2;

int main() {
	std::map<vec2, int> grid;
	grid[vec2(10, 10)] = 10;
	grid[vec2(10000, 10000)] = 7;
	std::cout << grid[vec2(10, 10)] << std::endl;
	std::cout << grid[vec2(10000, 10000)] << std::endl;
	return 0;
}

```

For larger dimensions you can just make your own key class or use something like boosts tuple.

---

### Post by hundredwatt on 2009-01-07
> **Zeotronic said:**
> I'll toy around with that, but wouldn't "int** temp = array;" merely point to what's contained by array, and then, of course, it would be deleted in the next line?

Yes it would :) Sorry about that, I didn't actually try the code before I posted. You'd want

int* temp = *array;

or something similar to store the reference until you create the new "array" and put temp back in it.

---

### Post by hod139 on 2009-01-08
> **Zeotronic said:**
> I've searched the subject rather thoroughly trying to solve my problem myself, and I'm pretty sure your example turns out like crap. Each array contained in an array (in your example) would have to be resized to the proper size to have a standard sized second dimension, would they not? And I need to work with up to 3 or 4 dimensions, so this approach simply would not do.

But that is... as I said... to my knowledge.
I'm not sure what your level of knowledge is, but STL vectors incur minimal overhead over C style arrays (especially when optimizations are enabled), and the added benefits significantly outway any small overhead.  We've also had this conversation before, see [http://ubuntuforums.org/showthread.php?t=691162](http://ubuntuforums.org/showthread.php?t=691162) for example comparing speed, starting at around post 29.

As for your second statement, "Each array contained in an array (in your example) would have to be resized to the proper size to have a standard sized second dimension, would they not?"
What data structure are you looking for here?  You want variable sized arrays, but you want all of them to be the same size?  There is not multidimensional array data strucutre that will do this.  You will have to write it yourself.

And your last statement, "And I need to work with up to 3 or 4 dimensions, so this approach simply would not do".  This is incorrect, you can nest vectors as many levels as you want.  Although the boost multi-array class will become easier to use.


> **Zeotronic said:**
> I'm sorry I'm so blunt.

But am I not correct in that, using so may vector arrays just to get a 3 dimensional array would incur *vast* amounts of waste? We're talking all the extra data required by a vector, multiplied by *what*?

Instead of just thinking, you can test.  But let me assure you, the vector solution will be better.  For instance, if you have a vector of bools, the STL will automagically bit pack for you.

---

### Post by hod139 on 2009-01-08
double post

---

### Post by Zeotronic on 2009-01-08
> I'm not sure what your level of knowledge is, but STL vectors incur minimal overhead over C style arrays (especially when optimizations are enabled), and the added benefits significantly outway any small overhead.
I'm aware that STL Vectors incur minimal overhead... however, in this use, you have the overhead for each of those vectors, and it adds up (unless they have some mechanisms in place that seem rather unlikely). It could be done better by something actually intended for this purpose... rather than, essentually, throwing vectors at it until you get something that resembles a solution.

If I have to actually use vectors for this... I won't be kidding myself by trying to make them multi-dimensioned... I'll just access them using math to impose artificial dimensions to them. I'd just do that, but on resizing the array, the contents would (predictably) get slopped into something that does not resemble the previous state of the array.

> And your last statement, "And I need to work with up to 3 or 4 dimensions, so this approach simply would not do". This is incorrect, you can nest vectors as many levels as you want.
I know this, I'm talking about the previously mentioned overhead buildup. I'm sure I don't need to tell you that it becomes considerably worse with the increasing number of dimensions? Things like that bother me, I cant imagine why they wouldn't bother you.
> Although the boost multi-array class will become easier to use.
I would just use it, but it doesn't seem to work in structures, and I cant (personally) devise a way around this.

---

### Post by hod139 on 2009-01-08
lots of double posts

---

### Post by hod139 on 2009-01-09
removed duplicate post

---

### Post by eye208 on 2009-01-09
> **Zeotronic said:**
> I'm aware that STL Vectors incur minimal overhead... however, in this use, you have the overhead for each of those vectors, and it adds up (unless they have some mechanisms in place that seem rather unlikely). It could be done better by something actually intended for this purpose... rather than, essentually, throwing vectors at it until you get something that resembles a solution.
Let me put it this way: The STL was not implemented by hobby programmers like you. Rest assured that the overhead of a vector is exactly as large as it absolutely needs to be in order to provide the additional functionality of vectors over fixed-size arrays.

If you manage to come up with an implementation that is even more efficient than std::vector, please submit it to the C++ standards committee for peer review and inclusion into future revisions of the STL. Thank you.

---

### Post by dwhitney67 on 2009-01-09
> **Zeotronic said:**
> I'm aware that STL Vectors incur minimal overhead... however, in this use, you have the overhead for each of those vectors, and it adds up (unless they have some mechanisms in place that seem rather unlikely). It could be done better by something actually intended for this purpose... rather than, essentually, throwing vectors at it until you get something that resembles a solution.

IYO, do vectors incur overhead or not?  Make a decision; you seem to waffle in your statement above.

> **Zeotronic said:**
> 
If I have to actually use vectors for this... I won't be kidding myself by trying to make them multi-dimensioned... I'll just access them using math to impose artificial dimensions to them. I'd just do that, but on resizing the array, the contents would (predictably) get slopped into something that does not resemble the previous state of the array.

Have you implemented any solution yet?  Or are you just floating ideas?  Anytime you resize a vector, of course the state will change!  The data contained within the vector should still remain the same, and still be accessible in the same manner, using the same indexes as before, unless of course you happened to truncate the vector by resizing it to something smaller.

> **Zeotronic said:**
> 
I know this, I'm talking about the previously mentioned overhead buildup. I'm sure I don't need to tell you that it becomes considerably worse with the increasing number of dimensions? Things like that bother me, I cant imagine why they wouldn't bother you.

You definitely seemed bothered by something, but until you post some code, I can't imagine what it is.

> **Zeotronic said:**
> 
I would just use it, but it doesn't seem to work in structures, and I cant (personally) devise a way around this.
Once again, post some code.  Getting the boost::array or boost::multi_array set up is not that difficult; even when the object type contained within it is a structure/class.

---

### Post by pmasiar on 2009-01-09
> **Zeotronic said:**
> I'm sorry I'm so blunt.

You are not blunt but **rude** ... and to people who are more experienced than you are, and who spend their own free time to help you to solve your problems. 

You are lucky that CoC here protects you from flames, in many other forums you would fare far worse. Read 'how to ask questions' - in my sig - and not only sanitized version for UF, but the original version too. really, do it.

---

### Post by Zeotronic on 2009-01-09
> Let me put it this way: The STL was not implemented by hobby programmers like you. Rest assured that the overhead of a vector is exactly as large as it absolutely needs to be in order to provide the additional functionality of vectors over fixed-size arrays.

If you manage to come up with an implementation that is even more efficient than std::vector, please submit it to the C++ standards committee for peer review and inclusion into future revisions of the STL. Thank you.
I understand this... but *I* can only accept this to be so in a single dimension... it just seems to me like a bit of a rigging job to get multiple dimensions out of this, and without some proof otherwise in the form of documentation or (some such) I cannot accept, at an end-user's word that these are designed to perform even *this* function with the absolute minimum required for it, because, quite simply, it does not appear to have been designed with this function in mind (unless, perhaps, as a passing thought). But as you have said, who am I?

> IYO, do vectors incur overhead or not? Make a decision; you seem to waffle in your statement above.
My statement seemed rather straightforward to me, be it incorrect or not... I was stating, quite simply, that vectors have a small amount of overhead, but if you have a 16x16x16 array, then surely they would have the overhead of what? 256 vectors? Forgive me if I incorrectly believe the same can be done more efficiently.

> You definitely seemed bothered by something, but until you post some code, I can't imagine what it is.
Even if I were to post the code you wouldn't understand it. To needlessly let you in on it: I'm designing for a platform with limited processing power and ram... and it stresses me out that I might actually make something, only to have it not work on it, and have to go back and either figure out why, or redesign it so it does (which could, in worst case scenario, turn out to simple not be possible). Somewhere along the line, I gained the likely ill-conceived notion that if I pour my guts into it the first time, this simple will not happen.

> Once again, post some code. Getting the boost::array or boost::multi_array set up is not that difficult; even when the object type contained within it is a structure/class.
Perhaps sadly, while preparing some rather straightforward code to post up here, demonstrating my problem, I realized what my problem was, and have corrected it, with everything now working as it should. Perhaps the saddest part, is that I had considered that this might have been my problem days ago, and I forgot that consideration before I could test it. To quit being ambiguous: I needed to resize my multi_array, rather than trying to declare it's size like I was just making it. The most frustrating part of this whole thing, being that I could have sworn that I saw somewhere that multi_arrays *couldn't* work in structures.

> You are not blunt but **rude**
Rude is a perceived behaviour. I know what I am, don't tell me I'm not. I often perceive those responding as rude, so I think it is indetermineable, save for popular consensus, as to who is actually being rude.

---

### Post by dwhitney67 on 2009-01-09
> **Zeotronic said:**
> ...

My statement seemed rather straightforward to me, be it incorrect or not... I was stating, quite simply, that vectors have a small amount of overhead, but if you have a 16x16x16 array, then surely they would have the overhead of what? 256 vectors? Forgive me if I incorrectly believe the same can be done more efficiently.
...

I was reading through your post, and stopped after this paragraph.  It seems that you do not understand vectors that well.  For a 16x16x16 array, all you need are three vectors, one for each dimension.

[php]
#include <vector>
#include <cassert>

int main()
{
  typedef std::vector<int>  OneD;
  typedef std::vector<OneD> TwoD;
  typedef std::vector<TwoD> ThreeD;

  // declare array
  ThreeD myArray;

  // resize to 16x16x16, and add values while at it
  int value = 0;

  myArray.resize(16);

  for (int i = 0; i < 16; ++i)
  {
    myArray[i].resize(16);

    for (int j = 0; j < 16; ++j)
    {
      myArray[i][j].resize(16);

      for (int k = 0; k < 16; ++k)
      {
        myArray[i][j][k] = value++;
      }
    }
  }

  // verify the size of myArray; should be 12 bytes
  assert(sizeof(myArray) == 12);

  // verify contents
  int verify = 0;
  for (int i = 0; i < 16; ++i)
  {
    for (int j = 0; j < 16; ++j)
    {
      for (int k = 0; k < 16; ++k)
      {
        assert(myArray[i][j][k] == verify++);
      }
    }
  }

  return 0;
}
[/php]
Btw, there should be 16^3 values in the 3-D vector, or 4096 values.  Each of these values occupies 4-bytes, thus for a total of 16384 bytes.  With the vector occupying 12 bytes in itself, the total bytes consumed by this container are 16396 bytes.  Whoopty doo.

---

### Post by Zeotronic on 2009-01-09
> Btw, there should be 16^3 values in the 3-D vector, or 4096 values. Each of these values occupies 4-bytes, thus for a total of 16384 bytes. With the vector occupying 12 bytes in itself, the total bytes consumed by this container are 16396 bytes. Whoopty doo.
Well you brush it off as unconcerning, but I find it of concern. By compairison though, how much would multi-array use for the same 3d array?

---

### Post by dwhitney67 on 2009-01-09
> **Zeotronic said:**
> Well you brush it off as unconcerning, but I find it of concern. By compairison though, how much would multi-array use for the same 3d array?

I'll leave your query as an exercise for you to figure out.

---------

Edit.... The answer is 16464 bytes (4096 * 4 + 80).  Hence a vector is more compact than a boost::multi_array, but by only 68 bytes.  Woo hoo.

P.S.  Zeotronic... please don't look for C++ help again!

---

