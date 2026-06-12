---
title: "Python Dictionary"
date: 2009-09-03
forum: Programming Talk
---

### Post by Stackee on 2009-09-03
Basically for my program, i need to take information from a txt file and turn it into a dictionary.
extract from text file:
___
TR202,  Mountain Bike Tire,             2000
TU277,  Mountain Bike Tube,             2000
___

my code so far:


```
def load_parts(filename):
    """Load file containing parts information and return a dictionary which
    associates each part ID with a pair - name of
    part and cost of part (in cents).
    load_parts(str) -> {str:[str,int]}
    """

    parts_file = open(filename,'U')
    parts_text = parts_file.read()
    parts_file.close
    parts_dict = {partID:(partName,cost)}

    for line in parts_text:
        for string in line.split(',',0):
                parts_dict[partID].append(word)
        for string in line.split(',',1):
                parts_dict[partName].append(word)
        for string in line.split(',',2):
                parts_dict[cost].append(word)

    print parts_dict
```i understand this is wrong (it produces the following error:
Traceback (most recent call last):
  File "<pyshell#82>", line 1, in <module>
    load_parts('C:\Documents and Settings\user\My Documents\University\CSSE1001\Assignment 1\parts.txt')
  File "C:\Documents and Settings\user\My Documents\University\CSSE1001\Assignment 1\assign1.py", line 21, in load_parts
    parts_dict = {partID:(partName,cost)}
NameError: global name 'partName' is not defined)
but this is my first month coding python and don't know how to fix it, could anyone help me out?

edit:
dict should be formatted like
{TR202:['Mountain Bike Tyre',2000], etc}

---

### Post by Bodsda on 2009-09-03
> **Stackee said:**
> Basically for my program, i need to take information from a txt file and turn it into a dictionary.
extract from text file:
___
TR202,  Mountain Bike Tire,             2000
TU277,  Mountain Bike Tube,             2000
___

my code so far:


```
def load_parts(filename):
    """Load file containing parts information and return a dictionary which
    associates each part ID with a pair - name of
    part and cost of part (in cents).
    load_parts(str) -> {str:[str,int]}
    """

    parts_file = open(filename,'U')
    parts_text = parts_file.read()
    parts_file.close
    parts_dict = {partID:(partName,cost)}

    for line in parts_text:
        for string in line.split(',',0):
                parts_dict[partID].append(word)
        for string in line.split(',',1):
                parts_dict[partName].append(word)
        for string in line.split(',',2):
                parts_dict[cost].append(word)

    print parts_dict
```i understand this is wrong (it produces the following error:
Traceback (most recent call last):
  File "<pyshell#82>", line 1, in <module>
    load_parts('C:\Documents and Settings\user\My Documents\University\CSSE1001\Assignment 1\parts.txt')
  File "C:\Documents and Settings\user\My Documents\University\CSSE1001\Assignment 1\assign1.py", line 21, in load_parts
    parts_dict = {partID:(partName,cost)}
NameError: global name 'partName' is not defined)
but this is my first month coding python and don't know how to fix it, could anyone help me out?

edit:
dict should be formatted like
{TR202:['Mountain Bike Tyre',2000], etc}

Well, with regards to your error, unless you have only pasted some of your code then the problem is that you are trying to use variables that do not exist. partID and partName will both cause errors because you never declare them in your code. 

If you have more code and those variables are declared outside of this function then the issue is due to scope. When you create variables they are specific to the scope they were created in. If you create a variable outside of a function then call it with function b, function b will not be able to reference this variable unless you tell it to. You can do this with global variables. 

Add the name of the variable from the global scope at the top of your function, preceded by the word 'global', this will tell it to use the global version of that variable and not create a local variable.

```

def load_parts(filename):
    global partID
    global partName

    <rest of code>

```

Hope this helps,

Kind regards,
Bodsda

---

### Post by jpkotta on 2009-09-03
Where is word defined?  Do you mean string instead?  You probably want something more like:
```

parts_list = {}
for line in parts_text:
    id, name, cost = line.split(',')
    parts_list[id] = (name, cost) # list or tuple, either have advantages
        

```

Also have a look at the readlines method for file handles.

---

### Post by smartbei on 2009-09-03
The variable 'partName' is not defined, so you cannot use it. Here is how you use a dictionary:
```

## initialize a dictionary:
d = {}

## Add something to it:
d["abc"] = 3
d["bcd"] = [1,2,3]

## And let's print it to get an understanding of what we just did:
print d
## Looks like: {"abc": 3, "bcd": [1, 2, 3]}

```
It looks like what you want to do is this:
```

def load_parts(filename):
    """Load file containing parts information and return a dictionary which
    associates each part ID with a pair - name of
    part and cost of part (in cents).
    load_parts() -> {}
    """

    parts_file = open(filename,'U')
    parts_dict = {}

    for line in parts_file:
        split_line = line.strip().split(',')
        parts_dict[split_line[0]] = split_line[1:]

    parts_file.close()

    return parts_dict

```
Here are explanatons for the changes:
[list]
[*] If you want to iterator over lines in a file, use the file object itself.
[*] When you split a string, it returns a list. There is no need to split it multiple times.
[*] The second argument for split is the maximum number of times to split a string. For example:
```

'1 2 3 4 5 6'.split(' ', 2) ## => ['1', '2', '3 4 5 6']

```
[*] I assume the file is in the format id,name,price. If so, I don't have to seperate the list created by split.
[*] strip() removes whitespace from the beginning and end of the string. I use it to remove the newline at the end.
[*] This I didn't change, but you might want to change this yourself - you will have a space at the beginning of the name and number because in the file there is a space after the comma. You can change the split to work with ', ' and that should solve the problem.
[/list]

One thing I would recommend is to play around in the python shell some more - you will get a better feel for how to use the basic python objects (list, dict, string, int, etc.).

---

### Post by jpkotta on 2009-09-03
> **Bodsda said:**
> 
Add the name of the variable from the global scope at the top of your function, preceded by the word 'global', this will tell it to use the global version of that variable and not create a local variable.


Python is kind of weird about globals. If you don't assign a variable and only read it, it will use the global scope.  After you assign it, it will make the variable local.  Obviously, you can assign globals if you have declared them with the global keyword in your function.

```

foo = 1
def bar():
    print foo
def baz():
    foo = 2
    print foo
bar() # prints '1'
baz() # prints '2'
bar() # still prints '1'
foo = 3
bar() # now prints '3'
baz() # still prints '2'

```

---

### Post by Stackee on 2009-09-03
Thanks so much for all the help!
I'm trying to get it working at the moment and it's created a dictionary (but done something quite strange). Currently I'm changing around the code:
    ```
parts_dict = {}
    for line in parts_text:
        split_line = line.strip().split(',')
        parts_dict[split_line[0]] = split_line[1:]
```and when i print parts_dict it outputs:
{'': [], '1': [], '0': [], '3': [], '2': [], '5': [], '4': [], '7': [], '6': [], '9': [], 'B': [], 'G': [], 'F': [], 'H': [], 'M': [], 'S': [], 'R': [], 'U': [], 'T': [], 'W': [], 'a': [], 'c': [], 'b': [], 'e': [], 'd': [], 'g': [], 'i': [], 'h': [], 'k': [], 'm': [], 'l': [], 'o': [], 'n': [], 's': [], 'r': [], 'u': [], 't': []}
i feel that i'm getting pretty close to getting this to happen but not sure where the code's going wrong

(i deleted the four for-loops i had previously)

i should use the .append thing in my loop somewhere shouldn't I? I thought that because I'm adding extra dictionary entries into it, I should use .append.

oh also, the reason i'm using the 'U' mode to get the file is because it was asked so it'd work on other operating systems(something to do with independent processing of new lines). it doesn't matter anyway because it's working right.

---

### Post by Tony Flury on 2009-09-03
Why not print out "split_line" each time round the loop, as it looks like you might be splitting the line incorrectly.

---

### Post by Stackee on 2009-09-03
yea i tried that just now and it just prints out each letter in it's own list. i have a feeling this is because the for line in parts_text: is looping for every letter instead of every line but unsure how to get it to loop every line instead =/

---

### Post by Jacks0n on 2009-09-03
Hm...

Try this:
[PHP]
def load_parts(filename):
	f = open(filename, 'r')
	d = {}
	for line in f:
		l = line.strip().split(', ')
		d[l[0]] = (l[1], int(2))
	f.close()
	return d

dictionary_returned = load_parts('filename.txt')
print dictionary_returned
[/PHP]

---

### Post by Stackee on 2009-09-03
> **Jacks0n said:**
> Hm...

Try this:
[php]
def load_parts(filename):
    f = open(filename, 'r')
    d = {}
    for line in f:
        l = line.strip().split(', ')
        d[l[0]] = (l[1], int(2))
    f.close()
    return d

dictionary_returned = load_parts('filename.txt')
print dictionary_returned
[/php]
Traceback (most recent call last):
  File "<pyshell#61>", line 1, in <module>
    load_part('C:\Documents and Settings\user\My Documents\University\CSSE1001\Assignment 1\parts.txt')
  File "C:\Documents and Settings\user\My Documents\University\CSSE1001\Assignment 1\assign1.py", line 24, in load_part
    d[l[0]] = (l[1], int(2))
IndexError: list index out of range

not sure what that one does

---

### Post by smartbei on 2009-09-03
@stackee - you missed an important change - you need to iterate over parts_file, not parts_text - check out the whole example above.

---

### Post by Can+~ on 2009-09-03
> **jpkotta said:**
> Where is word defined?  Do you mean string instead?  You probably want something more like:
```

parts_list = {}
for line in parts_text:
    id, name, cost = line.split(',')
    parts_list[id] = (name, cost) # list or tuple, either have advantages
        

```

Also have a look at the readlines method for file handles.

I like that solution, uses the natural unpacking into variables and put them inside.

Now, this is the first thing I thought:

[PHP]def load_parts(filename):
	
	parts_file = open(filename, "r")
	parts_dict = {}
	
	def packer(id, name, cost):
		parts_dict[id.strip()] = (name, int(cost))
	
	for line in parts_file:
		packer(*line.strip().split(",", 3))
	
	parts_file.close()
	
	return parts_dict[/PHP]

I might be spoiled by the functional paradigm, as I try to minimize the amount of temporary variables and just shoot everything trough arguments.

Oh, and as a bonus, this is how it looks on python3 with the "with" statement:

[PHP]def load_parts(filename):
	parts_dict = {}
	
	def packer(id, name, cost):
		parts_dict[id.strip()] = (name, int(cost))
	
	with open(filename, "r") as parts_file:
		for line in parts_file:
			packer(*line.strip().split(",", 3))
	
	return parts_dict[/PHP]

It closes the file after being used.

---

### Post by Stackee on 2009-09-03
Thanks Can+~. When I tried this though, I got the error:

>>> load_parts('C:\Documents and Settings\user\My Documents\University\CSSE1001\Assignment 1\parts.txt')
Traceback (most recent call last):
  File "<pyshell#9>", line 1, in <module>
    load_parts('C:\Documents and Settings\user\My Documents\University\CSSE1001\Assignment 1\parts.txt')
  File "C:\Documents and Settings\user\My Documents\University\CSSE1001\Assignment 1\test.py", line 11, in load_parts
    packer(*line.strip().split(",", 2))
TypeError: packer() takes exactly 3 arguments (1 given)

---

### Post by Can+~ on 2009-09-03
> **Stackee said:**
> Thanks Can+~. When I tried this though, I got the error:

Then fix it, what do you expect? I tested with a file like:

```
key, name, cost
key, name, cost
key, name, cost
key, name, cost
key, name, cost
```

---

### Post by jpkotta on 2009-09-03
> **Stackee said:**
> yea i tried that just now and it just prints out each letter in it's own list. i have a feeling this is because the for line in parts_text: is looping for every letter instead of every line but unsure how to get it to loop every line instead =/

Yeah, it's because parts_text is a string.  You need to either split() it on newlines, or better yet use readlines() instead of read(), like I already said.

Even though strings don't have the __iter__ attribute, they are still iterable in a for loop.  I think this is dumb, because it sends mixed messages.

---

