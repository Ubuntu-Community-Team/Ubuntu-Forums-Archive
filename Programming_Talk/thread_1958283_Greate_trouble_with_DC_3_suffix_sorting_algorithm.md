---
title: "Greate trouble with DC 3 suffix sorting algorithm"
date: 2012-04-13
forum: Programming Talk
---

### Post by DaviesX on 2012-04-13
I am trying to learn a linear time suffix sorting algorithm who uses suffix array that save a bunch of memory. But I have difficulties understand the its radix sorting, Can you explain to me how it works ?
And I have got a c++ implementation, but I don't even know how to call the interface =,=, 
Here is the code, 

```

// This programme is proposed to implement a o(n) time complexity DC3 algorithm
#include <stdio.h>
#include <stdlib.h>

void suffixArray ( int* s, int* SA, int n, int K );

int main ( int argv, char *argc[] )
{
    // I know the author tried to write comprehensive code
    // but I still don't get it, even to call it =,=
    return 0;

}

inline bool leq ( int a1, int a2, int b1, int b2 )   // lexic. order for pairs
{
    return (a1 < b1 || a1 == b1 && a2 <= b2);
}
                                                  // and triples
inline bool leq ( int a1, int a2, int a3, int b1, int b2, int b3 )
{
    return ( a1 < b1 || a1 == b1 && leq ( a2, a3, b2, b3 ) );
}

// stably sort a[0..n-1] to b[0..n-1] with keys in 0..K from r
static void radixPass ( int* a, int* b, int* r, int n, int K )
{
    // count occurrences
    int* c = new int[K + 1];                        // counter array

    for (int i = 0;  i <= K;  i++)
        c[i] = 0;                                     // reset counters

    for (int i = 0;  i < n;  i++)
        c[ r[ a[i] ] ]++;                            // count occurrences

    // exclusive prefix sums
    for ( int i = 0, sum = 0; i <= K; i++ )
    {
        int t = c[i];
        c[i] = sum;
        sum += t;
    }

    for (int i = 0;  i < n;  i++)
        b[ c[ r[ a[i] ] ]++ ] = a[i];                  // sort

    delete [] c;
}

// find the suffix array SA of s[0..n-1] in {1..K}^n
// require s[n] = s[n + 1] = s[n + 2] = 0, n >= 2
void suffixArray ( int* s, int* SA, int n, int K )
{
    // Here I think n might be the length of orginal suffix
    int n0 = (n + 2)/3,
        n1 = (n + 1)/3,
        n2 = n/3,
        n02 = n0 + n2;                // (2n + 2)/3 can be seen as the number of triples whose
                                    // pos mod 3 != 0

    // I think s12 might be the array that holds the suffixes whose
    // pos mod 3 != 0
    int* s12  = new int[n02 + 3];
    s12[n02] = s12[n02 + 1] = s12[n02 + 2] = 0;    // Last 3 would end up with 0

    int* SA12 = new int[n02 + 3];    // suffix array for pos mod 3 != 0
    SA12[n02] = SA12[n02 + 1] = SA12[n02 + 2] = 0;

    int* s0   = new int[n0];    // whose pos mod 3 = 0
    int* SA0  = new int[n0];    // suffix array for pos mod 3 = 0

    // generate positions of mod 1 and mod  2 suffixes
    // the "+(n0-n1)" adds a dummy mod 1 suffix if n%3 == 1
    for ( int i = 0, j = 0; i < n + (n0 - n1); i++ )
        if ( i % 3 != 0 )
            s12[j++] = i;

    // lsb radix sort the mod 1 and mod 2 triples
    radixPass ( s12 , SA12, s + 2, n02, K );
    radixPass ( SA12, s12 , s + 1, n02, K );
    radixPass ( s12 , SA12, s + 0, n02, K );

    // find lexicographic names of triples
    int name = 0, c0 = -1, c1 = -1, c2 = -1;

    for ( int i = 0; i < n02; i++ )
    {
        if ( s[ SA12[i] + 0 ] != c0 ||
             s[ SA12[i] + 1 ] != c1 ||
             s[ SA12[i] + 2 ] != c2 )
        {
            name ++;
            c0 = s[ SA12[i] + 0 ];
            c1 = s[ SA12[i] + 1 ];
            c2 = s[ SA12[i] + 2 ] ;
        }

        if ( SA12[i] % 3 == 1 )
        {
            s12[ SA12[i]/3 ]      = name;    // left half
        }
        else
        {
            s12[ SA12[i]/3 + n0 ] = name;    // right half
        }
    }

    // recurse if names are not yet unique
    if ( name < n02 )
    {
        suffixArray ( s12, SA12, n02, name );

        // store unique names in s12 using the suffix array
        for ( int i = 0; i < n02; i++ )
            s12[SA12[i]] = i + 1;
    }
    else
    {
        // generate the suffix array of s12 directly
        for ( int i = 0; i < n02; i++ )
            SA12[s12[i] - 1] = i;
    }

    // stably sort the mod 0 suffixes from SA12 by their first character
    for ( int i=0, j=0; i < n02; i++ )
        if ( SA12[i] < n0)
            s0[j++] = 3*SA12[i];

    radixPass ( s0, SA0, s, n0, K );

    // merge sorted SA0 suffixes and sorted SA12 suffixes
    for ( int p = 0, t = n0 - n1, k = 0; k < n; k++ )
    {
        int i = GetI(); // pos of current offset 12 suffix
        int j = SA0[p]; // pos of current offset 0  suffix

        if ( SA12[t] < n0 ?
            leq ( s[i],             s12[SA12[t] + n0],       s[j],             s12[j/3] ) :
            leq ( s[i], s[i + 1], s12[SA12[t] - n0 + 1], s[j], s[j + 1], s12[j/3 + n0] ) )
        {
#define GetI()             (SA12[t] < n0 ? SA12[t]*3 + 1 : (SA12[t] - n0)*3 + 2)
            // suffix from SA12 is smaller
            SA[k] = i;
            t ++;

            if ( t == n02 )   // done --- only SA0 suffixes left
            {
                for ( k++; p < n0; p++, k++ )
                    SA[k] = SA0[p];
            }
        }
        else
        {
            SA[k] = j;
            p ++;

            if (p == n0)    // done --- only SA12 suffixes left
            {
                for ( k ++; t < n02; t++, k++ )
                    SA[k] = GetI();
            }
        }
    }

    delete [] s12;
    delete [] SA12;
    delete [] SA0;
    delete [] s0;
}

```
I have studied it for days, but doesn't make sense with it, I don't want to give up, can you please tell me what is what ?
Thank you !

---

### Post by DaviesX on 2012-04-15
[http://www.cs.cmu.edu/afs/cs/project/pscico-guyb/realworld/www/papersS04/KaSa03.pdf](http://www.cs.cmu.edu/afs/cs/project/pscico-guyb/realworld/www/papersS04/KaSa03.pdf)
This code comes from this paper, can anyone tell me how to comprehend this algorithm, please.

---

### Post by satsujinka on 2012-04-16
[http://en.wikipedia.org/wiki/Radix_sort](http://en.wikipedia.org/wiki/Radix_sort)

So this is what you're having problem with right?

Let's say I'm sorting decimal integers. Since it's decimal all the digits will be some number 0-9 inclusive. The idea behind radix sort is to create an array for each possible digit (int array_*[num], where num is the number of things to sort and * is a number 0-9 e.g. array_zeros.)(1) Then you start with the least significant digit and put each number into the array that matches the digit. You now have the first pass done and you can return the numbers to where you're storing them (starting with the first number in array_zeros.)(1) You then repeat with every other digit. At the end the numbers should be sorted.

*Alternately, you can make array_*[num] be array_*[passes][num] where passes is the largest number of digits in a number (e.g. the number of passes it will take) and num is the number of numbers to sort. In which case, you can leave the numbers in array_*[pass] and just sort them into array_*[pass+1] based on the next digit.

---

### Post by DaviesX on 2012-04-16
But a string has many characters and every characters has 256 possible value, I think that would consume a lot of memory, it is different for decimal, so the algorithm above seems uses different way isn't it ?

---

### Post by satsujinka on 2012-04-16
Radix may be a stable sort, but that doesn't mean that it doesn't use a lot of memory.

For strings try converting characters into their ascii/unicode values and use that as an index to an array (obviously you could use integers directly in my previous example.)

So:
char radix_array[256][number_to_sort][longest_length];

assuming that you're storing the strings somewhere else between passes:
source[number_to_sort][longest_length];

---

### Post by DaviesX on 2012-04-16
Now, I have made more sense about that algorithm now, 
I first separate a string into two part, the first part is the sub-string whose subscript mod 3 = 0, the others are whose subscript mod 3 != 0. And then for those whose subscript mod 3 != 0 would be characterized by its first 3 characters.

For example, 
mississippi 
sub mod 3 == 0
mississippi
sissippi
sippi
pi

sub mod 3 == 1
ississippi ->iss
issippi -> iss
ippi -> ipp
i -> i00

mississippi
sub mod 3 == 2
ssissippi -> ssi
ssippi -> ssi
ppi -> ppi

---

### Post by DaviesX on 2012-04-16
And then, concatenate those three characters elements
iss iss ipp i00 ssi ssi ppi

and sort those elements by using radix sort.
radix sort that engaged by DC 3 dose not consume a lot of memory, it uses two buffer, I would like to note those as 
int buffer0[256], int buffer1[256];

It first sort by the first character of each element, and it is done in buffer0, and they will be stored as a ranking array, and the information will be stored in buffer1, 
then it sorts the second character of each element by using buffer1, and stores the ranking information in buffer0, 
the last time, it sort the last character by using buffer0, and stores the final ranking back in buffer1.
I still not quite clear with the detail, but it is likely to be like this: 

buffer0->buffer1
buffer1->buffer0
buffer0->buffer1

---

### Post by DaviesX on 2012-04-22
The detail is clear now
It's a really good algorithm that it consumes only very little memory

Code below is radix sorting for those 3-character string (I made the name of those variables more meaningful)
```

// Global Variable
int bin[256];

void RadixSort ( int *source, int *dest, char *string, int numGroup )
{
    // Initialize the counter
    for ( int i = 0; i < 256; i++ )
    {
        bin[i] = 0;

    }// End For ( Each group )

    // Count the occurrence
    for ( int i = 0; i < numGroup; i++ )
    {
        bin[string[source[i]]]++;

    }// End For ( Each group )

    // Give each group its name
    for ( int i = 0, offset = 0; i < 256; i++ )
    {
        int temp = bin[i];
        bin[i] = offset;
        offset += temp;

    }// End For ( Each Group )

    // Sort it to the array
    for ( int i = 0; i < numGroup; i++ )
    {
        dest[bin[string[source[i]]]] = source[i];

        // Lower rank for next occurence (rearer in suffix array)
        bin[string[source[i]]]++;

    }// End For ( Each Group )

}// End Function

```

The idea is to count the occurrence of a character instead of listing all of them. For example, 
iss iss ipp i00 ssi ssi ppi

we sort the first character in the first place
for bin['i'] we have 4 occurrences
bin['p'] we have 1
bin['s'] we have 2
while the others are all zero occurrence

Then we have to do the ranking stuff (smaller subscript has higher ranking if ascending)
For each bin, we use a base to define where it starts, then incrementally puts every occurrences of the same character into a name array.
For example, 
bin['a'] = 4, bin['b'] = 1, bin['c'] = 2, ...
the base of 'a' baseA is 0, 'b' baseB is 0 + 4, 'c' baseC is 0 + 4 + 1, ...
then rank of the first occurrence of 'c' is baseC + 0, the second occurrence should be baseC + 1 ...

Therefore, 
'a': 0, 1, 2, 3
'b': 4
'c': 5, 6
...

By using this technique, we can save a lot of memory from avoiding listing all the elements like a linked list or a two-dimensional array and filling time too :)

And then, sorts the second character with almost the same way.

---

### Post by DaviesX on 2012-04-22
We use the ranking generated by the first-character radix sorting, and sort the second character of each group using exact the same method we did in the first pass. And do the same thing for the last charater

```

    // Do the radix sorting for the first character and stores those's
    // ranking into array
    RadixSort ( group3, array, string, numGroup );

    // Sort the second character depending on the already sorted
    // first character ranking, and then stores those's ranking into group3
    RadixSort ( array, group3, string + 1, numGroup );

    // Do the radix sorting for the third character from group3, and stores the
    // result back to array eventually
    RadixSort ( group3, array, string + 2, numGroup );

```

---

