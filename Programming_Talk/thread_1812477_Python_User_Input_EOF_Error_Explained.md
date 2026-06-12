---
title: "Python User Input EOF Error Explained"
date: 2011-07-26
forum: Programming Talk
---

### Post by monkeywrench10 on 2011-07-26
Hello All,
    I am trying to make sense of what is probably a standard python idiom for collecting user input put I just don't get it.  I have code that iterates a list.  It a particular condition is true for any one of the items in the list I want the program to stop and wait on user input.  Instead, it throws an EOFError.  The code basically looks like this:

```
for invoice in parsedlist:
     if invoice[-1] == 3:
          sys.stderr.write("triple duplicate at " + invoice[2] + ' : ' + invoice[3] + "\n" )
          sys.stderr.write("continue Y or N \n")
          answer = raw_input("Type your answer here")
          if answer == 'N':
              sys.exit(1)
          else: 
               pass
```Of course, it does not work because program does not wait for input.  Rather it gets the EOF character some how.  I understand that this is somehow solved by using a try/except block but it is not clear to me how this works.  I have looked through quite a few postings on this issue and I still don't get it. Thank you in advance.

---

### Post by Bachstelze on 2011-07-26
Weird, it works fine for me...

```
firas@aoba ~ % cat test.py 
import sys

parsedlist = [["1", "2", "3", "4", 3],
              ["a", "b", "c", "d", 4],
              ["5", "6", "7", "8", 3],
              ["9", "10", "11", "12", 3]]

for invoice in parsedlist:
     if invoice[-1] == 3:
          sys.stderr.write("triple duplicate at " + invoice[2] + ' : ' + invoice[3] + "\n" )
          sys.stderr.write("continue Y or N \n")
          answer = raw_input("Type your answer here")
          if answer == 'N':
              sys.exit(1)
          else: 
               pass
firas@aoba ~ % python test.py
triple duplicate at 3 : 4
continue Y or N 
Type your answer herey
triple duplicate at 7 : 8
continue Y or N 
Type your answer hereN

```

---

### Post by monkeywrench10 on 2011-07-26
Does it matter that the program reads in a text file from standard input?  A text file was read in as in:

```
cat text.txt | ./mypython.py
```

---

### Post by cgroza on 2011-07-26
> **monkeywrench10 said:**
> Does it matter that the program reads in a text file from standard input?  A text file was read in as in:

```
cat text.txt | ./mypython.py
```
Yes!:)

---

### Post by monkeywrench10 on 2011-07-26
Hmmmm......Go on........

---

### Post by Bachstelze on 2011-07-26
There can be only one standard input. ;) Either your file or the keyboard, not both.

---

### Post by monkeywrench10 on 2011-07-26
That makes sense.  However, at the point of the script in question, the reading from the "cat file | my script" part is already complete.  All lines of text have been processed and put into a list.  I am iterating through that list when I attempt to get user input.  Does the fact that the initial read is over make a difference here?

---

### Post by Bachstelze on 2011-07-26
Yes. You have reached the end of file, there is no more data to read from stdin. Since raw_input reads from stdin, it has nothing to read and raises EOFError

---

### Post by monkeywrench10 on 2011-07-26
So is there no way to re-assign the stdin back to the keyboard or to otherwise deal with the problem?

---

### Post by Bachstelze on 2011-07-26
There might be a way but it would be terribly kludgy. Why not have your script read the file from the disk, instead of passing it on stdin?

---

### Post by monkeywrench10 on 2011-07-26
Like from a temp file?  The current reason is that the script takes in raw input (a text version of a pdf report) processes it and converts results to a csv all in one module.  The part with the user input comes right at the end before output to screen.

Are you saying write the list to a temp file and then read it back in to ask the "triple duplicate" question to get around the "already used" stdin problem here?

---

### Post by Bachstelze on 2011-07-26
Right now your script reads the file from stdin. Instead, you could make it read the file directly from the disk, then you get the data and parse it in exactly the same way you do it when reading from stdin, except that you read from the disk instead.

---

### Post by Arndt on 2011-07-26
You can read from the tty instead of from stdin, like this:

```
f=open("/dev/tty","r+")
f.write("string")
f.readline()
```

There may be better ways to do it.

---

### Post by Chayak on 2011-07-26
It would help to know why you chose to pipe data into the script rather than having the script get the data.  Are you going to pipe the output of other programs into it, or is that just the way you knew how to pass data to a script?

If it's not something you intend to regularly pipe into then you'd be better off passing the file name as an argument like this.

```
import sys

def get_file( file_name ):
    f = open( file_name, "r")
    file_buffer = f.read()
    f.close()
    return file_buffer

def your_function( buffer ):
    # your code goes here

def main():
    file_name = sys.argv[1]
    buffer = get_file( file_name )
    your_function( buffer )

main()
```



That way you can do this.

```
> myscript.py <filename>
```

---

### Post by cgroza on 2011-07-26
You can read from sys.stdin instead. It will act as raw_input in this case and will allow you to manipulate the input as a file.

---

