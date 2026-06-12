---
title: "repeated character algorithm/puzzle"
date: 2009-10-28
forum: Programming Talk
---

### Post by A_Fiachra on 2009-10-28
I was asked to code this during a Phone Interview  :(

With the condition that it NOT be in Perl ... I chose Python but didn't get too far.


Write a function that takes a string and returns the longest substring of repeated characters.

E.g. string = "abarrrrug" would return "rrrr", "AAabccba" would return "cc", "quickbrownfox" would return the empty string.

We  never got to other edge conditions like "aaabbbb".

I was forced to ask, "How often is this a problem for you guys?  Or are you pulling this out of the ether?"  (I hate companies that act like they are Google)


```


#!  /usr/bin/python

import collections

def repeats ( a_string ) :
    repeat_dict = collections.defaultdict(int)
    
    ## I Had the start of an idea here ...
    
    prev_char = a_string[0]
    

    ### but never got further than this ...
    for c in a_string :
        repeat_dict[c] +=1

    return repeat_dict

a_string = "AABBBAA"
repeat_dict = repeats ( a_string )

for c in sorted(repeat_dict, key = repeat_dict.get, reverse = True):
    print '%s %6d' % (c, repeat_dict[c])


```

---

### Post by Arndt on 2009-10-28
> **A_Fiachra said:**
> I was asked to code this during a Phone Interview  :(

With the condition that it NOT be in Perl ... I chose Python but didn't get too far.


Write a function that takes a string and returns the longest substring of repeated characters.

E.g. string = "abarrrrug" would return "rrrr", "AAabccba" would return "cc", "quickbrownfox" would return the empty string.

We  never got to other edge conditions like "aaabbbb".

I was forced to ask, "How often is this a problem for you guys?  Or are you pulling this out of the ether?"  (I hate companies that act like they are Google)


```


#!  /usr/bin/python

import collections

def repeats ( a_string ) :
    repeat_dict = collections.defaultdict(int)
    
    ## I Had the start of an idea here ...
    
    prev_char = a_string[0]
    

    ### but never got further than this ...
    for c in a_string :
        repeat_dict[c] +=1

    return repeat_dict

a_string = "AABBBAA"
repeat_dict = repeats ( a_string )

for c in sorted(repeat_dict, key = repeat_dict.get, reverse = True):
    print '%s %6d' % (c, repeat_dict[c])


```

Think about how you would solve the problem purely with eyes and hands. Then try to formulate that in pseudo code - especially identify how much state you need while scanning the string - and try it out with a few cases. Show us the pseudo code and we can help with the formulation in Python.

(What do you mean by "act like they are Google"?)

---

### Post by Can+~ on 2009-10-28
Here's the simplest thing I could think of:

[PHP]#!/usr/bin/env python

inp = "abracadaaaaaabra!" # Word/sentence to be tested

prevchar = "" # Previous character
count = 1     # Count of current character
maxcount = 1  # Most frequent character count
maxchar = ""  # Most frequent character

for character in inp:
	
	# If the character is equal to the previous
	if character == prevchar:
		count += 1
	# If not, check if it was bigger than the previous
	elif count > maxcount:
		
		# Store the biggest
		maxcount = count
		maxchar = prevchar
		
		# Reset the count
		count = 1
	else:
		# Reset the count
		count = 1
	
	prevchar = character

if maxchar == "":
	print "No consecutive characters found"
else:
	print "Most repeated character was: '%c' (%d times)" % (maxchar, maxcount)
[/PHP]

Nothing fancy, just a plain iterative solution (could be done in C too).

---

### Post by unutbu on 2009-10-28
[PHP]#!/usr/bin/env python
from itertools import groupby
import sys
a_string = sys.argv[1]
max_len=0
max_str=''
for k,g in groupby(a_string):
    g=tuple(g)
    g_len=len(g)
    if max_len<=g_len and g_len!=1:
        max_len=g_len
        max_str=k*g_len
print(max_str)
[/PHP]
[PHP]
% test.py abarrrrug
rrrr
% test.py AAabccba
cc
% test.py quickbrownfox

% test.py aaabbbb
bbbb
% test.py AABBBAA
BBB[/PHP]


Can+~'s method might be quicker though... :)

---

### Post by PandaGoat on 2009-10-28
I surprised no one mentioned a recursive method.  I did it in C to emphasize the algorithm.  Basically you look for the first substring and recursively call the method on the rest of the string and if the size of the latter substring is larger than the former, replace the current longest substring with the latter.

[php]
#include <stdio.h>

void longest_ss (char * s, char ** loc, size_t * len)
{
  if (*s == '\0')
    return;

  char c = *s;
  char * b;
  size_t size = 0;

  for (b = s; *b != '\0'; ++b)
    {
      if (c != *b)
        break;

      ++size;
    }


  if (size > *len)
    {
      *len = size;
      *loc = s;
      printf ("%s\n", s);
    }

  longest_ss (b, loc, len);
}

int main (void)
{
  char s[] = "aaaabbb";
  size_t size = 0;
  char * p = NULL;
  int i;

  longest_ss (s, &p, &size);

  for (i = 0; i < size; ++i)
    printf ("%c", *(p+i));

  printf ("\n");
  return 0;
}
[/php]

---

### Post by A_Fiachra on 2009-10-28
> **unutbu said:**
> [php]#!/usr/bin/env python
from itertools import groupby
import sys
a_string = sys.argv[1]
max_len=0
max_str=''
for k,g in groupby(a_string):
    g=tuple(g)
    g_len=len(g)
    if max_len<=g_len and g_len!=1:
        max_len=g_len
        max_str=k*g_len
print(max_str)
[/php][php]
% test.py abarrrrug
rrrr
% test.py AAabccba
cc
% test.py quickbrownfox

% test.py aaabbbb
bbbb
% test.py AABBBAA
BBB[/php]
Can+~'s method might be quicker though... :)


That's elegant, though.

I never thought of group by

---

### Post by thornmastr on 2009-10-30
[HTML]def getrepstr(instring):
    j = len(instring)
    dknt={}
    ind = 0
    myknt = 1
    while ind <= j-2:
        if instring[ind] == instring[ind + 1]:
            myknt += 1
        else:
            if myknt > 1:
                dknt[myknt] = instring[ind]
                myknt = 1
        ind += 1
    if myknt > 1:
        dknt[myknt] = instring[ind]
        myknt = 1        
    if len(dknt) > 0:
        v = dknt.keys()
        v.sort(reverse = True)
        x = dknt[v[0]]
        x1 = [x] * v[0]
        return ''.join(x1)
    else: return None[/HTML]

---

### Post by dribeas on 2009-10-30
Just for the sake of it, in C++:

```

std::string longest( std::string const & str )
{
    std::string result;
    std::string::const_iterator beg_seq = str.begin();
    std::string::const_iterator end_seq = beg_seq;

    for (; end_seq != str.end(); ++end_seq )
    {
        if ( *beg_seq != *end_seq ) // character change
        {
            if ( end_seq - beg_seq > result.size() ) // length is the difference of iterators
            {
                result.assign( beg_seq, end_seq );
            }
            beg_seq = end_seq;
        }
    }
    if ( end_seq - beg_seq > result.size() )
    {
        result.assign( beg_seq, end_seq );
    }
    return result;
}

```

---

### Post by ghostdog74 on 2009-10-31
```

echo "abcrndddddde" | awk -vFS= '
{ temp=0
  for(i=1;i<=NF;i++){l[$i]++}
  for(i=1;i<=NF;i++){
    o=$0; pat=$i"+"; m=gsub(pat,"",o)
    if (l[$i]>temp) {
        temp=l[$i]
        t=$i; max=l[$i]
    }
  } 
}END{   print t,max }'

```
output
```

$ ./shell.sh
d 6


```

---

