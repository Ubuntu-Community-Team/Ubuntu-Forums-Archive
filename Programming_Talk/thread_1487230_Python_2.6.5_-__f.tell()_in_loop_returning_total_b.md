---
title: "Python 2.6.5 -  f.tell() in loop returning total bytes in file"
date: 2010-05-18
forum: Programming Talk
---

### Post by patchwork on 2010-05-18
I am new to Python (and programming in general), so bear with me.  I am searching a file for a matching term, and would like to have the location of the matched term returned for future processing.  

Here is the relevant portion of the code:
[PHP]f = open(file_list[i], 'r')
        for id_ in f:
            # Remove unwanted whitespace and split line into fields
             id_ = id_.strip()
             fields = id_.split('\"')
             fields = [fields[1] ,fields[3], fields[5]] 

             # Search within newly created list for matching ID number
              if ( fields[0].count(new_id) ):
              print 'fields[0]', fields[0]
              print 'f.tell()', f.tell()
              matches.append(f.tell())[/PHP]This is probably something simple that I am completely missing, but shouldn't the f.tell() in the above loop return the location of the match?  

My output as written returns the matched item (in fields[0]), and the total size of the file--not the location where the match was found.



EDIT:  It seems that f.tell() is returning the full file size anywhere I place it in the iteration.  Is this because of the read ahead buffer the file iterator uses?
If so, how might I return the location of the matched term (perhaps manually reading the file line by line instead?)?

---

### Post by StephenF on 2010-05-18
> **patchwork said:**
> EDIT:  It seems that f.tell() is returning the full file size anywhere I place it in the iteration.  Is this because of the read ahead buffer the file iterator uses?
If so, how might I return the location of the matched term (perhaps manually reading the file line by line instead?)?
Lets say you make a subclass of file and redesign the iterator to only take one character at a time (by which I mean construct a line from reads a single character in length). If you did that the file pointer would still be pointing at the beginning of the next line which is not what you want but you can note down the position for the next iteration.

```

class myfile_iter(object):
    def __init__(self, fileobj):
        self.fileobj = fileobj
        
    def __iter__(self):
        return self
        
    def next(self):
        f = self.fileobj
        l = []
        while 1:
            c = f.read(1)
            if c:
                l.append(c)
                if l[-1] == "\n":
                    break
            else:
                break
        if l:
            return "".join(l)
        raise StopIteration


class myfile(file):
    def __iter__(self):
        return myfile_iter(self)


# Usage example.
if __name__ == "__main__":
    offset = 0
    f = myfile("data.txt", "r")
    for line in f:
        print "%4d %s" % (offset, line.rstrip())
    
        offset = f.tell()

```

---

### Post by patchwork on 2010-05-18
That looks promising, thank you.  I will delve into this and see what I can find.

---

### Post by patchwork on 2010-05-18
I apologize if my amateurish code is 'non-pythonic', but by using the mmap module as suggested I was easily able to both find my match, and replace the line in the file.  

[PHP]f = open(file_list[i], 'r+')
        data = mmap.mmap(f.fileno(),0)
        search = data.find('"' + new_id + '"')
        search_end = data.find('"' + str(int(new_id) + 1) + '"')
        data.seek(search)
        data[search:search_end]= ('"' + str(new_id) + '"' + '\t' + '"' + entry_list[i].get() + '"' + '\t' + '"' + entry_list[i + 1].get() + '"' + '\n').ljust(search_end - search, ' ')
        data.close()
        f.close()[/PHP]

Thanks Again!

---

