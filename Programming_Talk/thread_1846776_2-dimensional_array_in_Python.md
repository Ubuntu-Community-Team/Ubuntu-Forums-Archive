---
title: "2-dimensional array in Python?"
date: 2011-09-19
forum: Programming Talk
---

### Post by fester225 on 2011-09-19
Using spreadsheet terminology....

In Python, how do I create an array 2 columns wide, with an infinite number of rows? (The idea is to start with a file with one row and add more rows, indefinitely, as needed.)

---

### Post by ofnuts on 2011-09-19
> **fester225 said:**
> Using spreadsheet terminology....

In Python, how do I create an array 2 columns wide, with an infinite number of rows? (The idea is to start with a file with one row and add more rows, indefinitely, as needed.)
As a list of  of 2-element lists:
```
array=[[1,2]]
```or even (because if you limit yourself to two columns, they might as well have some structure), as a list of 2-element tuples:
```
array=[(1,2)]
```

---

### Post by HarrisonNapper on 2011-09-19
Python has the ability to infinitely add data to arrays by default. So if I declare an empty array as such:

```
myArray = []
```

I can add to it like so:

```
myArray.append([1,2])
```

or

```
myArray.append((1,2))
```

to add a tuple, though note that tuples are immutable so to edit an existing tuple, you'd have to replace the whole thing.

Array of Arrays:
```
myArray = [['one', 2], ['two', 2]]
myArray[0][1] = 1 #sets myArray[0] to ['one', 1]
```

Array of Tuples:
```
myArray = [('one', 2), ('two', 2)]
myArray[0][1] = 1 #returns an error
myArray[0] = ('one', 1) #success, or try...
myArray[0] = (myArray[0][1], 1) #uses existing value
```

The restrictions with tuples are nice, especially for immutable data, but important to note the difference, as it can slow performance some and they are handled slightly differently. There are also dictionaries, but instead of continuing to open cans of worms here, the Python documentation covers them fairly well :)

---

### Post by Tony Flury on 2011-09-20
If you are going to implementing a sparesly populated aray - i.e. one where a significant number of "cells" will be empty, a dictionary would be good in my opinion :

The key for each entry would be a tuple specifying the cordinates, and the value for the entry would be what that cell actually contains.

Manipulation is easy : 
1) Clear a cell - delete the entry in the dictionary with the co-ordinates.
2) Add content to a call - add a new entry in the dictionay
3) Change a cell - change the value of a dictionary entry
4) Move the contents from one cell to another - a combination of Adding/Modifying and deleting.

Advantages : 
1) You only store the data you need - i.e. you are not stoing blank data
2) Access to a given cell is pretty quick - via hashes
3) your array is effectively unlimited.
4) Negative co-ordinates if you wish - and non-integer ones too.

Disadvantages : 
1) Output - if you need to output your "array" you need to fill in the blanks.
2) Finding blanks is a bit complicated, as you have to find an entry in your search range that does not exist in the dictionary.

It depends what you want to do with your data. I think NumPy supports multi dimesional arrays : [http://numpy.sourceforge.net/numdoc/HTML/numdoc.htm#pgfId-57315](http://numpy.sourceforge.net/numdoc/HTML/numdoc.htm#pgfId-57315)

---

### Post by simpleblue on 2011-09-20
Don't you have to extract the array each time just to use a value within it? If so, that could get really messy very fast. Let's not even mention using a 3d array.

---

### Post by fester225 on 2011-09-20
Egads! It looks like I've stumbled upon some high quality help!

The structure I'm looking for would look like this in memory,

entry -->  50EF 6623 | A90C 333D
entry -->  47C0 7851 | ADE1 16A6 
entry -->  B090 928D | 52E2 632D
                     .
                     .
                     .
                     .....and be of indefinite length.

Each entry needs to consist of two 32-bit words. There would be no sequential numbering of the entries. Rather, you just need the starting and ending memory addresses and look through what's in the middle. The absolute position of any individual entry is irrelevant.

Another problem is: Once this data structure is in place in memory, it will be accessed and modified by an unknown number of external files simultaneously. I can't use Tuples since none of the entries are permanent.

(All this would have been easy back in the old DOS days because I was working in assembly language. These days I'm better served by writing in a multi-platform langauge, which of course means a new langauge to learn.)

What kind of data structure do I want?
It seems likely I want to create the array with one file, and make that file a requirement for any other file accessing it. Correct?
Another thing, once the data has been entered, I really need to be able to store it as a file on a hard drive. Having stored it on the hard drive, I need to be able to put that file back into memory so I don't have to re-enter the data.

---

### Post by ofnuts on 2011-09-20
> **fester225 said:**
> Egads! It looks like I've stumbled upon some high quality help!

The structure I'm looking for would look like this in memory,

entry -->  50EF 6623 | A90C 333D
entry -->  47C0 7851 | ADE1 16A6 
entry -->  B090 928D | 52E2 632D
                     .
                     .
                     .
                     .....and be of indefinite length.

Each entry needs to consist of two 32-bit words. There would be no sequential numbering of the entries. Rather, you just need the starting and ending memory addresses and look through what's in the middle. The absolute position of any individual entry is irrelevant.

Another problem is: Once this data structure is in place in memory, it will be accessed and modified by an unknown number of external files simultaneously. I can't use Tuples since none of the entries are permanent.

(All this would have been easy back in the old DOS days because I was working in assembly language. These days I'm better served by writing in a multi-platform langauge, which of course means a new langauge to learn.)

What kind of data structure do I want?
It seems likely I want to create the array with one file, and make that file a requirement for any other file accessing it. Correct?
Another thing, once the data has been entered, I really need to be able to store it as a file on a hard drive. Having stored it on the hard drive, I need to be able to put that file back into memory so I don't have to re-enter the data.If you neded to control how your stuff is laid out in memory, forget Python... Use C.

But you requirements are a bit strange. Why do you need this?

---

