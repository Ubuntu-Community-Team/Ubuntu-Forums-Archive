---
title: "Programming Challenge 11: Serialization"
date: 2008-05-12
forum: Programming Talk
---

### Post by Verminox on 2008-05-12
[SIZE="4"]**The Challenge**[/SIZE]

Write a program implementing methods to [serialize and unserialize]("http://en.wikipedia.org/wiki/Serialization") data, specifically, **Associative Arrays**.

[size="4"]**Description**[/size]
You have to be able to take any variable, whether integer, float, string, or array, and serialize it to a string which can be stored somewhere and later unserialized to construct the same variable again. 

Although this would seem simple for primitive data types, the main challenge is that your variable might very well be a complex array structure. For example it could be a 2D associative array with each array element having a varying data type. 

Your serialize() function should create the string in such a way that your unserialize() function should restore the variable as it was, complete with having the same data types as before. 

For an example, see PHP's built in serialize function. 
```
echo serialize(5) . "\n"; // Integer
echo serialize( array( 'foo' => 'bar', 'eggs' => 'spam' ) ); // Associative array
```
```
i:5;
a:2:{s:3:"foo";s:3:"bar";s:4:"eggs";s:4:"spam";}
```

Of course, your format does not have to be like the one above. You can let your serialized string be of any format as long as you can safely unserialize it (see next section).

Needless to say, you can't use built-in functions such as the one above.

[size="4"]**String Format**[/size]

There are two paths you can take when creating your own format to store the serialized variables.

1. **Compact**. Reduce the size of the output string as much as possible. Basically, optimize the serialization process. This strategy is useful for large amounts of data. Your format does not have to human-readable at all. In fact, if you want to go extreme you can even work on the bit level if you are good with binary data handling.

2. **Human Readable**. If you choose this category your string format has to be neat and readable so that one can understand what the data is without even having to use the unserialize() function (you still have to implement that though :p). Here string size is not of importance. Human readable format includes anything from a simple comma separated list to a full fledged XML document. It's your choice, go wild!

Choose any one path and go with it. No technnique is given special preference. But whichever technique you use, do it well :)

The PHP format as shown above is a hybrid. It tries to be human readable (but it's really not). It tries to be compact (but it's really not). You can use this format if you are not able to make your own but you will loose points for that.


[size="4"]**Judging**[/size]

Each entry will be graded for:

1. The Format. You can choose either of the above two techniques, no partiality here. But the strength of your technique gets you points. If you choose compact, it has to be really efficient. If you choose readable, it has to be clear and legible.

2. Coding style. If your code is neat and tidy and maybe documented with comments then you are at an advantage.

**Bonus Points**: (Optional, Not Required)
1. Can handle serialization of Objects. This is easy to do in languages such as PHP which support variable variables for dynamic data member access, but in some languages it might just be impossible.
2. Error reporting for badly formatted strings.

[size="4"]**Rules**[/size]

1. You cannot use external libraries or inbuilt functions for serializing, unserializing, or parsing formats (if you choose XML, parse it yourself!)

2. You *may* use an external library for implementing associative arrays if your language does not support it (for example, usage of std::map in C++ is allowed)

3. You *may* use inbuilt functions for typecasting between primitives and strings (such as float to string, and string to float for the reverse process). But if a function exists to typecast arrays to strings and vice versa, you *may not* use that, as that would lose the point of making your own string format.

4. Your program must pass the primary test (see below). If it fails the test, it is disqualified regardless of how good the format is.

[size="4"]**Primary Test**[/size]

Your program **must** be able to serialize the following array structure and later unserialize it to recover the array structure as it was previously (complete with the same data types).

For dynamically typed programming languages: (2D associatve hybrid structure)

```
array (
	'squares' => array (
				'one' => 1,
				'two' => 4,
				'three' => 9
			) ,
	'roots' => array (
				'four' => 2.0,
				'three' => 1.732
			) ,
	'foo' => array (
				'bar' => 'baz',
				'eggs' => 'spam'
			)
);
```


For statically typed langauges (array of array of integers)

```
array (
	'squares' => array (
				'one' => 1,
				'two' => 4,
				'three' => 9
			) ,
	'roots' => array (
				'four' => 2,
				'nine' => 3
			)
);
```


[size="4"]**Presentation**[/size]

1. Mention which technique you are using, compact or readable.

2. Post your code that defines the serialize() and unserialize() functions (of course you can name them differently if you want).

3. Post the test script.
3.1. Construct the array of the primary test (above).
3.2. Call the serialize() method and store the string in a variable.
3.3. Print the serialized string to standard output.
3.4. Call unserialize() on the string which should return the same array that you created.
3.5. Prove that the returned array is same as before either by calling a variable dump function if it exists (such as var_dump() in PHP) or just print some test calls (such as print $array['squares']['two'] should print 4)

4. Post the output of the test script. This will contain the serialized string (for me to judge your format) and the variable dump (for me to be convinced that you passed the test). 

5. If you implemented any of the Bonus features or if you put some of your own extra goodies into it then show an example of that too (with output).

[size="4"]**Languages**[/size]

You can use any language you want since you will be providing the output also. But don't try to cheat, as I will also test whatever I can myself. Just because I can't compile it doesn't mean I can't get a friend to do it ;)

[size="4"]**Deadline**[/size]

The deadline for this challenge is:
**May 20, 2008. 12:00 (noon) GMT** (5:30PM Indian Standard Time). I will then judge for the rest of the evening and announce the winner.

You may post queries or clarifications if required. Happy coding :D

Notes:
If you post one version first, then maybe fix some bugs or something and repost your updated code, please edit your previous post and mention at the top that there is a newer version so that I don't judge the wrong code.

---

### Post by bobbocanfly on 2008-05-12
Looks like quite a fun challenge. Will attempt this in Python later tonight.

---

### Post by nvteighen on 2008-05-13
(Hey, that "C unfriendly" tag is discriminatory! ;))

Let me see if I understood this correctly: you basically want us to write a parser that gets the test data, stores in an efficient/readable way and restores it properly. Have I lost something?

Probably won't participate on this challenge, but that doesn't prevent me to try this by my own when I've got some more time :). I'll be surely watching what people came up with.

---

### Post by Bichromat on 2008-05-13
**Edit : new version posted in msg #8**

OK, here's my first shot, in the 'compact' category. No tinkering with binary representation so there's room for improvement. But converting to binary and removing every superfluous bit is just too much for me !

Also, I don't know if the 'zlib' module is authorized but I can gain some characters if I compress the string...

Here's the module serialize.py :
```

class UnsquashError(Exception):
   """Standard error when unsquashing an incorrect string."""
   pass

def squash(data):
   """
   Returns a compact string containing 'data'
   
   A block of squashed data consists of a data identifier,
   possibly followed by a length indicator (for sequences types and strings),
   and then the data itself.
   Because the output is itself a string, strings have a special header.
   Booleans have the particularity of being directly encoded in their identifier
   
   Examples :
   * 45 => 'i45' where 'i' is the identifier for ints
   
   * 'spam' => 's4sspam' where 's4s' is the identifier for a
               string of length 4
   
   * [1,2,3] => 'l3i1i2i3' where 'l3' indicates a list of 3 elements,
                and 'i1i2i3' are the three corresponding data blocks
   """
   
   dictype={'int':'i', 'float':'f', 'list':'l', 'set':'e',
            'frozenset':'r', 'tuple':'t', 'str':'s', 'dict':'d'} # Data identifier in the squashed data string

   data_type=type(data).__name__
   if dictype.has_key(data_type): squashed = dictype[data_type] # The string that will contain the data

   if data_type in ['int','long']:
      squashed += str(data)

   elif data_type == 'float':
      str_dat = str(data)
      
      # str() is shorter, but has a limited precision of 12 digits
      # use it only if there's no loss of precision :
      if float(str_dat) == data:
         squashed += str_dat
      else:
         squashed += repr(str_dat)
         
   elif data_type == 'bool':
      if data:
         squashed = 'T'
      else:
         squashed = 'F'

   elif data_type in ['list','tuple','set','frozenset']:
      squashed += str(len(data))
      for element in data:
         squashed += squash(element)

   elif data_type == 'dict':
      squashed += str(len(data))
      for key,value in data.items():
         squashed += (squash(key)+squash(value))

   elif data_type == 'str':
      squashed += str(len(data)) + dictype[data_type] + data
   else:
      raise TypeError("%s not serializable !" % type(data))

   return squashed




def unserializer(string):
   """
   Recursive parser for squashed strings
   """
   str_len = len(string)
   if str_len == 0: raise UnsquashError("End of string reached before end of data !")
   
   type_ID = 'iflertsdTF'
   data_type = string[0]


   if data_type == 'i':        # integers and longs
      if str_len<2: raise UnsquashError("End of string reached before end of data !")
      
      content_end = 1
      while content_end<str_len and (string[content_end] not in type_ID): content_end += 1

      return (int(string[1:content_end]), string[content_end:])

   elif data_type == 'f':      # floats
      if str_len<2: raise UnsquashError("End of string reached before end of data !")
      
      content_end = 1
      while content_end<str_len and (string[content_end] not in type_ID): content_end += 1

      return (float(string[1:content_end]), string[content_end:])
      
   elif data_type in 'TF':     # booleans
      return (data_type == 'T', string[1:])

   elif data_type in 'lert':   # lists, sets and tuples
      unsquashed = []
      content_start = 1
      while string[content_start] not in type_ID: 
         content_start += 1
         if content_start == str_len:
            raise UnsquashError("End of string reached before end of data !")
         
      nb_elements = int(string[1:content_start])
      string = string[content_start:]

      for i in xrange(nb_elements):
         (decoded,string) = unserializer(string)
         unsquashed.append(decoded)

      if data_type == 't': unsquashed = tuple(unsquashed)
      elif data_type == 'e': unsquashed = set(unsquashed)
      return (unsquashed,string)

   elif data_type == 's':      # strings
      if str_len<3: raise UnsquashError("End of string reached before end of data !")
      
      content_start = string.find('s',1) + 1
      content_length = int(string[1:content_start-1])
      content_end = content_start + content_length
      if content_end>str_len: raise UnsquashError("End of string reached before end of data !")

      return (string[content_start:content_end],string[content_end:])
   
   elif data_type == 'd':      # dictionaries
      unsquashed={}
      content_start = 1
      while string[content_start] not in type_ID:
         content_start += 1
         if content_start == str_len:
            raise UnsquashError("End of string reached before end of data !")
         
      nb_elements = int(string[1:content_start])
      string = string[content_start:]
      
      for i in xrange(nb_elements):
         (key,string) = unserializer(string)
         (value,string) = unserializer(string)
         unsquashed[key] = value
         
      return (unsquashed,string)
      
   else:
      raise UnsquashError("'%s' is not a correct type identifier. Data is corrupted !" % data_type)



def unsquash(string):
   """
   Wrapper around the unserializer, which returns
   only the unserialized data
   """
   return unserializer(string)[0]

```

It can "squash" and "unsquash" basic python types : integers, floats, booleans, strings, lists, tuples, sets, frozensets and dictionaries. You can nest as many dimensions of sequences as you want.
I have put in some error checking, I think it can give understandable error messages for every possible bad string you may want to throw at it :D

A test script :
```

#!/usr/bin/env python

"""
This script tests the features of the serializer
"""

import serialize as se

dic = { 'squares' : {'one': 1,
                     'two': 2,
                     'three': 9
                     },
                     
        'roots' : {'four' : 2.0,
                   'three' : 1.732
                  },
                   
        'foo' : {'bar' : 'baz',
                 'eggs' : 'spam'
                }
      }

print("Dictionary :")
print(dic)

squashed_dic=se.squash(dic)

print("\nSquashed version :")
print(squashed_dic)

print("\nLength of the squashed version : %i" % len(squashed_dic))

unsquashed_dic=se.unsquash(squashed_dic)

print("\nUnsquashed :")
print(unsquashed_dic)

print("\nDoes it preserve the original content ? %s" % (dic == unsquashed_dic))

```

---

### Post by Verminox on 2008-05-14
Bichromat: Nice. I havn't done any custom testing on it yet but I executed your example and it looks good.And no, you can't use zlib compression libraries because that would be unfair to other languages that don't have built-in features to compress data. You can of course write your own compression scheme if you want...

I'm surprised there's only one entry so far. Come on guys... you chicken? :p

> **nvteighen said:**
> Let me see if I understood this correctly: you basically want us to write a parser that gets the test data, stores in an efficient/readable way and restores it properly. Have I lost something?

Yup that would be right.

---

### Post by Delever on 2008-05-14
I wrote something like that with C# for many different variables, and capable of serializing objects in the mix too (using standart serializer). It had different compacting modes which could remove most repeating 1111 or 0000 sequences, and support for Big/Little endian processors. I end up never actually using that code.

However, arrays there were treated like objects, so... no use for it :)

---

### Post by Verminox on 2008-05-16
> **nvteighen said:**
> (Hey, that "C unfriendly" tag is discriminatory! ;))

Let me see if I understood this correctly: you basically want us to write a parser that gets the test data, stores in an efficient/readable way and restores it properly. Have I lost something?

Probably won't participate on this challenge, but that doesn't prevent me to try this by my own when I've got some more time :). I'll be surely watching what people came up with.


:o How did that tag get there? I didn't put it :o

---

### Post by Bichromat on 2008-05-16
Where are the competitors? :popcorn:

I finally did what I didn't want to do at first: binary fiddling. It was fun actually :)

The serialize_bin module has more limitations than the other : it only "squashes" integers, floats, booleans, strings, lists and dicts (no tuples, sets, frozensets). Moreover, the maximum length of the elements is fixed (although the user can select the number of bits that code the length).

The good thing is that it produces a shorter string for the test dictionary than the string of the first version, even when I compress the latter.

---

### Post by Verminox on 2008-05-22
Either this was a boring challenge or it was too difficult. I don't know. But the deadline is long over and we have only one entry :\

Well, in any case, **Bichromat** is the winner of Programming Challenge 11. And I must add, that although this victory was out of defaults, I also really liked Bichromat's code and it would have been on my top candidates if there were more entries.

So then, Bichromate, it's your turn to post the next Programming Challenge. Hopefully it would be more fun than this one.

---

### Post by slavik on 2008-05-22
it's very difficult to serialize 'any' variable (what if it's a struct in C which has pointers to malloced data?) without writing a specific serializer for your specific structure.

---

### Post by Verminox on 2008-05-22
> **slavik said:**
> it's very difficult to serialize 'any' variable (what if it's a struct in C which has pointers to malloced data?) without writing a specific serializer for your specific structure.

The problem statement stated that object serialization is optional because it is hard to serialize references, I know. The main goal was to be able to achieve serialization of associative arrays, arrays, strings and primitive data, with any combination of the above (as in nested arrays). Yes, I agree with whoever put the "C unfriendly" tag on this thread, but I suppose with C++ and std::map this wouldn't have been too hard. Bichromat did a good job in python.

---

### Post by Zugzwang on 2008-05-22
> **Verminox said:**
> The problem statement stated that object serialization is optional because it is hard to serialize references, I know. The main goal was to be able to achieve serialization of associative arrays, arrays, strings and primitive data, with any combination of the above (as in nested arrays). Yes, I agree with whoever put the "C unfriendly" tag on this thread, but I suppose with C++ and std::map this wouldn't have been too hard. 

It *is* hard using C++ (and even Java) since in C++, you cannot match against an std::map<*> type. You would have to write extra methods for all combinations like "std::map<int,bool>", "std::map<bool,std::map<int,int> >" (and so on). If you want to get all the combinations, you would have to write infinitely many methods.

Now you would wonder why C++ is so limited. Every language has it's own ways how certain tasks are meant to be done. In this case, normally each class that is meant to be serialized would provide its own serialisation method & deserialization constructor. So one would have to derive std::serializable_map from std::map to make it work *or* just create serialization/deserialization methods for the types that are actually being used. But that's a different approach and it also requires the method receiving some object from deserialization to know its type in advance. This is usually not a problem (since that's the case in practice, anyway), but is incompatible with the challenge given.

---

### Post by Bichromat on 2008-05-22
Thank you Verminox :)
I'm  a bit disappointed that nobody else tried this challenge. I'm sure a Perl hacker or a Lisp genius could have done something very nice...

My challenge will be up ASAP !

---

### Post by slavik on 2008-05-22
that's the thing, in Perl, this would be very easy, since the most complicated thing is a hash, and that is what objects are made of.

---

