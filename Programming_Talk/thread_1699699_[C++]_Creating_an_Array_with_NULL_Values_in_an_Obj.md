---
title: "[C++] Creating an Array with NULL Values in an Object"
date: 2011-03-04
forum: Programming Talk
---

### Post by dodle on 2011-03-04
If I create an array from within the main function any values that I don't specified are set to 0 (NULL):

[php]int main()
{
    int bagged_items[3] = {10};
    
    for (int x = 0; x < 3; x++)
    {
        cout << "Item " << x << " = " << bagged_items[x] << endl;
    }
    
    return 0;
}[/php]

output:
```
Item 0 = 10
Item 1 = 0
Item 2 = 0
```

But If I create an array within a class the unspecified values are not NULL:

[php]class Bag
{
  public:
    Bag();
    int GetItems();
  private:
    int bagged_items[3];
};

Bag::Bag()
{
    bagged_items[0] = 10;
}

int Bag::GetItems()
{
    for (int x = 0; x < 3; x++) cout << "Item " << x << " = " << bagged_items[x] << endl;
}

int main()
{
    Bag bag;
    bag.GetItems();
    
    return 0;
}[/php]

The output is:
```
Item 0 = 10
Item 1 = 134514699
Item 2 = 10526708
```

Why is this? In order to get the desired output I have to use a for loop in the constructor to set each value in the array to 0:

[php]Bag::Bag()
{
    for (int x = 0; x < 3; x++) bagged_items[x] = 0;
    bagged_items[0] = 10;
}[/php]

---

### Post by An Sanct on 2011-03-04
Maybe its due to optimization or something.

Anyhow, null is not a number, it is a pointer, thus it can point to anything random.

[B]Null != 0

[/B]PS. Addition to the "optimization" I mentioned. Does it give the same result while debugging and while not? If so, then the compiler handles bad code, that is optimization.

---

### Post by nickleboyblue on 2011-03-04
It's a bit more complicated when you declare the array and fill it in two different places.  For example, in c++:

```
int array[5] = {1};
```

will fill array[0] with the one available number and, since we're already looking at the array, it will automatically be filled the rest of the way with 0's.

```
int array[5];
```

This will reserve memory for the array, but it won't do anything to the values that already existed in the memory assigned to the array.  At this point, the compiler/interpreter will not understand what you are trying to do if you try to assign values to the array using curly braces, because that can only be done on the same line as the array is declared, because in that case, the index number you use defines the size of the array and not an actual index number.  After that, the index number can never mean the same thing to the compiler.

Moral of the story:  If you want to auto fill an array with 0s in a class, you have to do it with a loop.

And please, if I'm wrong, don't be nice about it.

---

### Post by dwhitney67 on 2011-03-04
> **An Sanct said:**
> Maybe its due to optimization or something.

Anyhow, null is not a number, it is a pointer, thus it can point to anything random.

[B]Null != 0

[/B]PS. Addition to the "optimization" I mentioned. Does it give the same result while debugging and while not? If so, then the compiler handles bad code, that is optimization.

In C++, NULL is defined as 0.  Don't believe me?  Look at /usr/include/linux/stddef.h.

---

### Post by dwhitney67 on 2011-03-04
> **dodle said:**
> 
Why is this? In order to get the desired output I have to use a for loop in the constructor to set each value in the array to 0:

You could initialize the array using memset(), or std::fill(), or std::fill_n().

For example:
```

const size_t ARR_SIZE = 3;

int array[ARR_SIZE];

array[0] = 10;

std::fill(array + 1, array + ARR_SIZE, 0);

```

---

### Post by An Sanct on 2011-03-04
> In C++, NULL is defined as 0.  Don't believe me?  Look at /usr/include/linux/stddef.h.

Hm :) my mistake, sorry!

(From the time I was a windows developer, that was a pointer)

---

### Post by foxmuldr on 2011-03-04
> **dodle said:**
> [php]int main()
{
    int bagged_items[3] = {10};
    
    for (int x = 0; x < 3; x++)
    {
        cout << "Item " << x << " = " << bagged_items[x] << endl;
    }
    
    return 0;
}[/php]

output:
```
Item 0 = 10
Item 1 = 0
Item 2 = 0
```

The {n} declaration identifies elements by position.  When you specify {n} explicitly, and leave off the 2nd and 3rd elements, you are implicitly specifying that the remaining elements are NULL, which means 0.

If you leave off the initializer altogether, the compiler may leave all three elements undefined.  Also, it will likely make a difference if you're generating code in debug or optimization mode.  For the purposes of speed, unnecessary optimizations are often left off.  There are also rules governing partial initializers like this, which are defined by spec, and the compiler you use may or may not adhere to them.

> But If I create an array within a class the unspecified values are not NULL:

[php]class Bag
{
  public:
    Bag();
    int GetItems();
  private:
    int bagged_items[3];
};

Bag::Bag()
{
    bagged_items[0] = 10;
}

int Bag::GetItems()
{
    for (int x = 0; x < 3; x++) cout << "Item " << x << " = " << bagged_items[x] << endl;
}

int main()
{
    Bag bag;
    bag.GetItems();
    
    return 0;
}[/php]

The output is:
```
Item 0 = 10
Item 1 = 134514699
Item 2 = 10526708
```

It's unlikely to always be those values.  The memory the class uses is allocated on the stack when you declare "Bag bag;".  Whatever happens to be there already on the stack is what's shown through, and if you run this program 10x through you'll get 10 different numbers for Items 1 and 2.

Also, in your code you explicitly set the [0] value, but the values [1] and [2] are left to be whatever happened to be there are their next locations in memory.

> Why is this? In order to get the desired output I have to use a for loop in the constructor to set each value in the array to 0:

Without the loop, you'll see the effects of the speedup.  Everything that's not explicitly initialized in the constructor remains as whatever it was on the heap or local memory area when it was created.  That's the purpose of the constructor, to prepare the class just the way you like it.

Hope this helps.

- Rick C. Hodgin

---

