---
title: "Problem With Vector Erase C++"
date: 2010-03-13
forum: Programming Talk
---

### Post by StunnerAlpha on 2010-03-13
Ey guys, I have a function that takes in two positions and a vector and removes those positions from the vector, like so:
```

void removeFromTo(vector<string>& vect, long begPos, long endPos){
	cout << "beg, end: " << begPos << ", " << endPos << endl;
	vect.erase(vect.begin()+begPos, vect.begin()+endPos);
}//removeFromTo

```

But it fails to remove the first element from the vector, here is some program output:
```

//elements in the vector:
/ *   * /   $# 
^^^^^^^^^^^^^
0 1 2 3 4 5 6 
//beg and end are printed from within the function
beg, end: 0, 4
AFTER REMOVE!!!!!
/   $# 

```
So I still have that first '/'. Here is another example:
```

e / *   * /   $# 
^^^^^^^^^^^^^^^
0 1 2 3 4 5 6 7
beg, end: 1, 5
AFTER REMOVE!!!!!
e /   $# 

```
Yeah, so I don't know what I should do, any help appreciated and thank you.

EDIT:
Another odd thing, I changed the call of the function to:
```

removeFromTo(actualLine, charTypeAstrkBegCmnt(line, tokensVect[lineNum-1])-1, \
						 charTypeAstrkEndCmnt(line, tokensVect[lineNum-1])+1);

```
from:
```

removeFromTo(actualLine, charTypeAstrkBegCmnt(line, tokensVect[lineNum-1]), \
						 charTypeAstrkEndCmnt(line, tokensVect[lineNum-1])+1);

```
and this is my output:
```

e / *   * /   $# 
beg, end: 0, 5
AFTER REMOVE!!!!!
/   $# 

```
So it seems like it REALLY wants to keep the '/' for some reason.

---

### Post by era86 on 2010-03-13
Sorry, my post was useless.

vector.erase(iterator beg, iterator end) will delete from beg to end INCLUDING beg and NOT INCLUDING end.

In other words, what is being displayed is your second /.

Got that from here: [http://www.cplusplus.com/reference/stl/vector/erase/](http://www.cplusplus.com/reference/stl/vector/erase/)

---

### Post by MadCow108 on 2010-03-13
to me your output is working correctly (assuming the three spaces in your data indicate a space token)
the / is not the first but the second in your array

erase (as all other STL algorithms) takes a past-end iterator for its second argument. Its not the last element removed to be removed, it is the element which comes after the last removee!
so erase 0,4 removes: / * space * but not the next /

also a vector is no structure you usually want to call erase on if its not the end of the vector. Random location erases  trigger reallocations.
list may be a more appropriate structure.

---

### Post by StunnerAlpha on 2010-03-13
Oh wow, you were right, thanks man. You are probably right about the lists thing but I have my entire code implemented with vectors, if I run into problems, I will consider your advice. Thanks again.

---

