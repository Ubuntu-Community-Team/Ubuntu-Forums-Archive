---
title: "nested loops in python"
date: 2008-09-28
forum: Programming Talk
---

### Post by slentzen on 2008-09-28
I am trying to make a function that reads a fastafile and returns a dictionary having the header as key, and the corresponding sequence as the respective value.
My problem is that the fasta file format is rather loosely defined. All I know for sure is that the header containing the name of the sequence starts with a ">" followed by any number of any alphanumeric character and then any number of newlines.
The sequence can be a long continous string of characters, or it may be formatted with newline characters or other whitespacings.

An abstract fastafile having both possibilities could look like:
>Header_1
SEQUENCE_1_AS_ONE_LONG_STRING

>Header_2
SEQUE
NCE_IS_IN_
SEVERAL
_LINES

I am aware that the solution is to use a nested loop that can handle both possibilities. Here is how far I have come:
```
#!/usr/bin/python
def readFasta(filename):
    import re
    if '.fasta' in filename: # if filename is given
        input = open(filename,'r')
        fastalist = input.readlines()
        input.close()
    else:
        fastalist = filename
    print fastalist
    print "\n"
    header = re.compile(r'(>\w+)')
    sequence = re.compile(r'[^>](\w+)(\s?)')
    fastadict = {}
    for element in range(len(fastalist)):
        if header.search(fastalist[element]):
            matchH = header.match(fastalist[element])
            H = matchH.group(1)
        elif sequence.search(fastalist[element]):
            matchS = sequence.match(fastalist[element])
            S = matchS.group(1)
            fastadict[H] = S
    print fastadict
if __name__ == '__main__': # read the default testfile to test if script is working
    readFasta("Ecoli.prot.fasta")
    print "\n"

```

The function reads the file, and produces a list. The problem is that in the dictionary, only the first line of the sequence is taken along with my loop.

How can I make a nested loop (or if the solution is something else) that would catch the remaining of my second sequence?

Any help is very appreciated.

---

### Post by pp. on 2008-09-28
How is it that you are so uncertain about the format for a 'fastafile', whatever that might be?

I strongly suggest that you hunt down a reasonably accurate definition of the syntax of the file type you are trying to parse.

Until you're certain about the set of valid contents for a file of the desired type, you can code loops in Python until you are blue in the face.

---

### Post by tomchuk on 2008-09-28
Looking at the format on Wikipedia, it seems the '>' character is uniquely used to introduce the header. Splitting the file about occurences of '>' then taking the first line as the description, then the rest as the data should do the trick.
```

#!/usr/bin/python

def readFasta(filename):
    fasta = open(filename, 'r').read()
    d = dict()
    for item in fasta.split('>'):
        if item.strip():
            d[item.split('\n')[0]] = ''.join(item.split('\n')[1:])
    return d

print readFasta('Ecoli.prot.fasta')

```

---

### Post by pmasiar on 2008-09-28
biopython might have some FASTA format parser. It's common format, someone did it before.

---

