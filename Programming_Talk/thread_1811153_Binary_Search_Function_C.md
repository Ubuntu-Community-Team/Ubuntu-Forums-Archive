---
title: "Binary Search Function C"
date: 2011-07-24
forum: Programming Talk
---

### Post by stamatiou on 2011-07-24
I have the following code:

```
int binsearch(int x, int v[], int n)
{
    int low,high,mid;
    low = 0;
    high = n - 1;
    while(low<=high)
    {
        mid = (low + high) / 2;
        if(x < v[mid])
        {
            high = mid + 1;
        }else if(x > v[mid])
    {
        low = mid + 1;
    }else
    {
        return mid;
    }
    return -1;
    }
    }

```
It searches an array and it divides it by 2 and etc. Is it correct? Because if x is 7 and high is 10 mid  gets 8 all the time all the time. What am I mistaking?

---

### Post by Barrucadu on 2011-07-24
You have a typo here: "if(x < v[vid])". Also, indent your code, it makes it more readable.

---

### Post by stamatiou on 2011-07-24
I mean the logical part.

---

### Post by nema.arpit on 2011-07-24
I'd suggest that you change the iteration in high/low to = mid rather than = mid+1.
ie
```
high=mid
```instead of 
```
high=mid+1
```and
```
low=mid
```instead of 
```
low=mid+1
```Or if you insist on unnecessarily expanding your search region, in case of low iteration it should be 
```
low=mid-1
```
As to what is wrong, think about this : if x is < v[mid], then should the next high be **mid** or **mid+1? **Similar thought in case for low.

Of course this is all under the assumption that v is a sorted array..

---

### Post by Arndt on 2011-07-24
> **nema.arpit said:**
> I'd suggest that you change the iteration in high/low to = mid rather than = mid+1.
ie
```
high=mid
```instead of 
```
high=mid+1
```and
```
low=mid
```instead of 
```
low=mid+1
```

With your corrections, what happens if n == 1, v[0] == 5 and x == 6?

---

### Post by slavik on 2011-07-24
high = mid + 1;

shouldn't that be

high = mid - 1;

?

---

### Post by dwhitney67 on 2011-07-24
No high, no low.

```

int binSearch(const int value, const int array[], const int num)
{
   int mid = (num - 1) / 2;
   int index = -1;

   if (num > 0)
   {
      if (value < array[mid])
      {
         index = binSearch(value, array, mid);
      }
      else if (value == array[mid])
      {
         index = mid;
      }
      else if (value > array[mid])
      {
         index = binSearch(value, array + mid + 1, num - mid - 1);

         if (index >= 0)
         {
            index += (mid + 1);
         }
      }
   }

   return index;
}

```

---

### Post by Blackbug on 2011-07-25
> **dwhitney67 said:**
> No high, no low.
 
```

int binSearch(const int value, const int array[], const int num)
{
   int mid = (num - 1) / 2;
   int index = -1;
 
   if (num > 0)
   {
      if (value < array[mid])
      {
         index = binSearch(value, array, mid);
      }
      else if (value == array[mid])
      {
         index = mid;
      }
      else if (value > array[mid])
      {
         index = binSearch(value, array + mid + 1, num - mid - 1);
 
         if (index >= 0)
         {
            index += (mid + 1);
         }
      }
   }
 
   return index;
}

```
 
 
Recursion is always a best approach and makes it clean..

---

