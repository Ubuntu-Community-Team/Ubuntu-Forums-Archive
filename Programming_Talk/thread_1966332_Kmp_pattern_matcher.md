---
title: "Kmp pattern matcher"
date: 2012-04-27
forum: Programming Talk
---

### Post by DaviesX on 2012-04-27
I have recreate a linear timed KMP pattern matching algorithm
But I still have trouble in understand the prefix computing function, Can you please tell me how does it work ?

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int *prefix = 0;

int PatternMatch ( char *mainString, char *subString );
void ComputePrefix ( char *subString, int length );

int main ( void )
{
    char mainStr[] = "bacbabababacaca";
    char pattern[] = "ababaca";

    int position = PatternMatch ( mainStr, pattern );

    if ( position != -1 )
        printf ( "Matched at %d\n", position );
    else
        printf ( "Pattern not matched\n" );

    return 0;

}// End Function


// Here we use KMP algorithm to implement a linear timed pattern matcher o(m + n)
int PatternMatch ( char *mainString, char *subString )
{
    int patLength = strlen ( subString );
    prefix = (int *)malloc ( patLength*sizeof ( int ) );

    // Precompute the equal prefixes exist in pattern string
    ComputePrefix ( subString, patLength );

    int position = -1;
    int mainLength = strlen ( mainString );

    // Traverse the main string
    for ( int iMainStr = 0, iSubStr = 0;
            iMainStr < mainLength; iMainStr++ )
    {
        // Backtracking to the nearest similiar prefix
        // while they are not matched
        while ( iSubStr > 0 && mainString[iMainStr] != subString[iSubStr] )
            iSubStr = prefix[iSubStr - 1];

        if ( mainString[iMainStr] == subString[iSubStr] )
            iSubStr++;

        // If we have found a match
        if ( iSubStr == patLength )
        {
            position = iMainStr - iSubStr + 1;
            break;

        }// End If

    }// End For ( Each main element )

    free ( prefix );
    return position;

}// End Function ( PatternMatch )


// This function is the mighty part of this algorithm,
// We compare the "PATTERN string" to itself, to find out all the equal substring (prefix)
void ComputePrefix ( char *subString, int length )
{
    // The first element never equals to any other former prefixes
    prefix[0] = 0;
    int former = 0;

    // Traverse the whole substring
    for ( int current = 1; current < length; current++ )
    {
        // Once the latter prefix and former prefix become unequaled
        // Backtracking to another former prefix
        // Untill we found one is equal or we have reached the first prefix
        while ( former > 0 && subString[current] != subString[former] )
            former = prefix[former - 1];

        // If there are equal check the next one next time
        if ( subString[current] == subString[former] )
            former++;

        prefix[current] = former;

    }// End For

}// End Function ( ComputePrefix )

```

---

### Post by DaviesX on 2012-04-27
For the time being, I just ambiguously understand the key point of this algorithm. 

for a non-repeated pattern such as
abcdefg
will never need to do backtracking because every element correspond to the main string is unique

But for a pattern that has duplicated substring is another story, we have to backtrack the whole pattern while missing matched, otherwise, we might miss the pattern. And KMP use another backtracking technique so that it's faster. It is the mighty prefix array, but I'm not clear how to find the duplicated substring of the pattern within linear time

---

### Post by DaviesX on 2012-04-28
I understand it now. Actually, there is a formula to represent the prefix array.
```

             -1,     (x = 0)
Prefix[x] =  max{k}  where k &#8712; {k| P0...Pk = Px-k...Px-1} (0 < x < len)
             0       (other conditions)

```

Pk means patternString[k], which also hints the value of k must be confined by the border of pattern string. 
And len = strlen ( patternString )

I think the second condition is the most confusing one. It doesn't mean that we can always find such k when 0 < x < len, if not, we are jumping to condition 3 then.

Some paper states that array as next function, but I think to call it prefix function is perfect, because we are really matching prefix with sub-string in the pattern itself.

---

### Post by DaviesX on 2012-04-28
I would like to show an example to show what is Max{k} like
Assumes that the pattern is "ababaca"

```

0 1 2 3 4 5 6 7
a b a b a c a '/0'

```

Now the prefix array should be
```

x       pattern[x-1]     prefix[x]
0       /               -1
1       a                0
2       b                0
3       a                1
4       b                2
5       a                3
6       c                0
7       a                1

```

---

### Post by DaviesX on 2012-04-28
Why it works ?
While pattern string Pk+1 mismatches the main string S at some place j+1, and x = prefix[k]

```

Sj-k ... Sj-k+x = P0 ... Px

```
According to the formula above, 
```

[COLOR="red"]P0 ... Px = Pk-x+1 ... Pk-1[/COLOR]

```
So we have
```

Sj-k ... Sj-k+x = [COLOR="red"]Pk-x+1 ... Pk-1[/COLOR]

```
This means a lot, if we shift the pattern for x-1 unit, it still match the first x elments in the pattern string.

And here is the example, I use the pattern whose prefix array is computed in the last post
```

S: b a c b [COLOR="Red"]a b a b a[/COLOR] b a c a c a
P:         [COLOR="Red"]a b a b a[/COLOR] c a

```

prefix[5] = 3 as the result showed on the table in the last post
equals to
```

S: b a c b [COLOR="Red"]a b a b a[/COLOR] b a c a c a
P:             [COLOR="Red"]a b a b a[/COLOR] c a

```

---

### Post by DaviesX on 2012-04-28
To be simple, they key to this idea is that we use the PREFIX of the pattern to replace the duplicated SUB-STRING, then, keep matching the rest of the pattern behind that prefix. On the other hand, if there is no duplicated string in the pattern, we never need to replace anything, just start from the beginning of the pattern string when mismatched. However, if there is a duplicated sub-string of the prefix, this is the only factor to cause missing matcher.

And here is the implementation of this algorithm
```

#include <stdio.h>
#include <stdlib.h>

// Global Functions
void ComputePrefix ( const char *pattern, int *prefix );

void MatchPattern ( const char *mainString, const char *pattern, int *prefix, int *position );


int main ( void )
{
    char *mainString = "bacbabababacaca";
    char *pattern = "ababaca";

    int prefix[256];
    ComputePrefix ( pattern, prefix );

    int position;
    MatchPattern ( mainString, pattern, prefix, &position );

    if ( position != -1 )
    {
        printf ( "Pattern matched at %d\n", position );
    }
    else
    {
        printf ( "Pattern doesn't match\n" );

    }// End If

    return 0;

}// End Function ( main )

void ComputePrefix ( const char *pattern, int *prefix )
{
    int current = 0, former = -1;
    prefix[0] = -1;

    // Within the border of the pattern
    while ( pattern[current] != 0 )
    {
        // Condition 2 and 3
        // Max{x} and no such K
        if ( former == -1 || pattern[current] == pattern[former] )
        {
            current ++;
            former ++;
            prefix[current] = former;		// Assign K

        }
        else
        {
            former = prefix[former];

        }// End If

    }// End While

}// End Function ( ComputePrefix )


void MatchPattern ( const char *mainString, const char *pattern, int *prefix, int *position )
{
    *position = -1;

    int iMainStr = 0,
                   iPattStr = 0;

    while ( mainString[iMainStr] != 0 )
    {
        if ( iPattStr == -1 ||		// -1 means matched fail
                mainString[iMainStr] == pattern[iPattStr] )	// Keep matching the rest of the pattern
        {
            iPattStr ++;
            iMainStr ++;

            // Matched ?
            if ( pattern[iPattStr] == 0 )
            {
                *position = iMainStr - iPattStr;
                break;

            }// End If
        }
        else
        {
            iPattStr = prefix[iPattStr];		// Shift #prefix[x] elements

        }// End If

    }// End While

}// End Function ( MatchPatter )



```

---

### Post by DaviesX on 2012-04-28
The average time complexity of this algorithm is O(n + m), but the worst case is O(m*(n-m+1))
that is when the pattern have too many duplicated sub-string, for example,
 aaaaaaaaaab
the prefix array will be, 
-101234567890

When matching, 
 aaaaaaaaacaaaaaaaaaab
we have to backtrack 9 times for character 'c', Obviously, it is gross

---

### Post by DaviesX on 2012-04-28
Hopefully, if we can have it backtracked to the P0 immediately, that could be much faster! Indeed, there is such algorithm -- an improved KMP pattern matching algorithm.

It uses almost the same concept but changed the formula a little bit.

---

### Post by DaviesX on 2012-04-29
```

#include <stdio.h>
#include <stdlib.h>

// Global Functions
void ComputePrefix ( const char *pattern, int *prefix );

void MatchPattern ( const char *mainString, const char *pattern, int *prefix, int *position );


int main ( void )
{
    char *mainString = "bacbabababacaca";
    char *pattern = "ababaca";

    int prefix[256];
    ComputePrefix ( pattern, prefix );

    int position;
    MatchPattern ( mainString, pattern, prefix, &position );

    if ( position != -1 )
    {
        printf ( "Pattern matched at %d\n", position );
    }
    else
    {
        printf ( "Pattern doesn't match\n" );

    }// End If

    return 0;

}// End Function ( main )

void ComputePrefix ( const char *pattern, int *prefix )
{
    int current = 0, former = -1;
    prefix[0] = -1;

    // Within the border of the pattern
    while ( pattern[current] != 0 )
    {
        // Condition 2 and 3
        // Max{x} and no such K
        if ( former == -1 || pattern[current] == pattern[former] )
        {
            current ++;
            former ++;

            [COLOR="Red"]if ( pattern[current] == pattern[former] )
                prefix[current] = prefix[former];
            else
                prefix[current] = former;		// Assign K
[/COLOR]
        }
        else
        {
            former = prefix[former];

        }// End If

    }// End While

}// End Function ( ComputePrefix )


void MatchPattern ( const char *mainString, const char *pattern, int *prefix, int *position )
{
    *position = -1;

    int iMainStr = 0,
                   iPattStr = 0;

    while ( mainString[iMainStr] != 0 )
    {
        if ( iPattStr == -1 ||		// -1 means matched fail
                mainString[iMainStr] == pattern[iPattStr] )	// Keep matching the rest of the pattern
        {
            iPattStr ++;
            iMainStr ++;

            // Matched ?
            if ( pattern[iPattStr] == 0 )
            {
                *position = iMainStr - iPattStr;
                break;

            }// End If
        }
        else
        {
            iPattStr = prefix[iPattStr];		// Shift #prefix[x] elements

        }// End If

    }// End While

}// End Function ( MatchPatter )

```

---

### Post by DaviesX on 2012-04-30
Actually, I don't know why it can be optimized like that ... :mad:

---

### Post by 11jmb on 2012-05-02
So algorithms aren't exactly my strong suit, and this is the frst time I've actually ever seen this improvement, but I'll give it a shot: basically, this will cause less backtracking in the search algorithm. The character that "breaks" the search is the only one that should require a backtrack.

So I will show a test string with the original KMP table and the improved table:

```

SLOTHS ARE SLOW AND SLEEPY
X0000000000012300000012000  (KMP)
X0000000000000300000002000  (improved)

```

With the improved algorithm, "SLOTHS ARE SNAZZY DRESSERS" will not require any backtracking, even though there is another 'S', but "SLOTHS ARE SLOPPY EATERS" will require a backtrack of 3 characters after the first 'P' in "SLOPPY" because the entire sub-pattern has been matched.

Hope that helps some. Again, algorithms aren't my strong suit, so maybe somebody else here can fill in any gaps which I may have left.

---

### Post by DaviesX on 2012-05-02
Thank you very much !
Because of your test, now I get it :)
(Actually, the array would have 1 more elements then the strings one)

Because once the element become unequal, for example, 
SLOW and
SLA....

although I can backtrack to 2, but it still using "O" compare to "A" untill it backtracks to the original point :mad:(if using the original method). So the improved one cleverly backtrack one more time before they used to do the actual compare.(Every equal element do so)
```

prefix[current] = form;  vs
prefix[current] = prefix[form]; 

```

That is my thought about it. Thank you one more time ^_^

---

### Post by 11jmb on 2012-05-02
> **DaviesX said:**
> Thank you very much !
(Actually, the array would have 1 more elements then the strings one)



I think you can implement the algorithm with a backtracking array the same length as your character array (nut including the null). Perhaps I misunderstood the algorithm, and did not sufficiently test with a case which required an extra value in the backtracking array. 

Also, note that in my previous post, the X in the backtracking arrays woulds be implemented as a -1. I wanted the text to line up, and didn't do a good job of explaining that.

---

### Post by DaviesX on 2012-05-02
Yeah, the last one may needed in real implementation to avoid border checking or you have to -1 when mismatched, although it is useless...

---

### Post by DaviesX on 2012-05-02
Btw, this algorithm is worthy to read rather than worthy to use. It is slower than the plain algorithm when the pattern is short although its theoretical time complexity is linear LOL

---

