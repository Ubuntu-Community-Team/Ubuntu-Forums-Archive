---
title: "Comments on this code are welcome"
date: 2008-06-28
forum: Programming Talk
---

### Post by luca.b on 2008-06-28
Hello, 

I've been writing a Python class which enbles text files to be seen as tables with columns and rows (akin to a similar implementation in the R programming language). I'm posting part of the class here since I'd like to know if my code can be improved. The final result will be GPL, so it's not a big deal.

```
class DataMatrix(object):
    
    """Pythonic implementation of R's data.frame structure.
    This class loads a file or a file-like structure then it 
    transforms it into a dictionary of (row name, value) tuples for
    each column. Optionally only column values can be retrieved and
    at the same time single lines can be queried.
    
    Notable methods are:
        - getColumn - returns a specific column
        - getRow - returns a specific row

    """
    
    def __init__(self,fh,row_names=None,header=True, delimiter="\t",
                lineterminator=os.linesep,quoting=csv.QUOTE_MINIMAL):
        
        self.__records = dict()
        self.filename = fh.name if hasattr(fh,"name") else None
        self.identifier = None
        row_names = row_names -1
        fh.seek(0) # to make sure
        heading = fh.next()
        fh.seek(0)
        
        heading = heading.strip()
        heading = heading.split(delimiter)
        
        if not header:
            heading = [str(item) for item in range(1,len(heading)-1)]
            heading.insert(0,"x")
        
        self.columns = copy.copy(heading)
        print self.columns
        count = 1
        
        if row_names is not None:
            self.identifier = heading[row_names]
            heading.remove(self.identifier) # remove the row identifier
        
        for field in heading:
            self.__records[field] = list()
        
        reader = csv.DictReader(fh,fieldnames=self.columns,
                    lineterminator=lineterminator,
                    delimiter=delimiter,quoting=quoting)
        
        for row in reader:
            if self.identifier is not None:
                row_id = row[self.identifier]
            for field in heading:
                if self.identifier is not None:
                    self.__records[field].append((row_id,row[field]))
                else:
                    self.__records[field].append((str(count),row[field]))
            count += 1
        
        self.__fields = self.__records.keys()
        
    def __str__(self):
        
        if self.__records:
            column_no = "No. of columns: %d" % len(self.__records)
            columns = ', '.join(self.columns)
            columns = ' '.join(("Columns:",columns))
            names = self.identifier if self.identifier is not None else \
                        "None (numeric)"
            row_name = "Column with identifier names: %s" % names
            rows = "No. of rows: %d" % len(self.__records[self.__fields[0]])
            name = ' '.join(("File name:", self.filename))
            output = os.linesep.join((name, row_name, rows, column_no, 
                        columns))
            return output   
    
    def __getitem__(self, key):
        
        if key not in self.__records:
            raise KeyError, unicode("No such column")
        elif key == self.identifier:
            raise KeyError, unicode("You cannot select the row names")
        
        return self.__records[key]
        
    def getColumn(self, key, heading=False):
        
        if key not in self.__records:
            raise KeyError, unicode("No such column")
            
        column_data = list()
        
        if heading:
            column_data.append(key)
        
        for record in self.__records[key]:
            column_data.append(record[1])
        return column_data
        
    def getRow(self, row_number,columns="all"):
        
        row = list()
        records = self.__records.keys() if columns == "all" else columns
        row_name = self.__records[self.__fields[0]][row_number-1]
        row_name = row_name[0] # Get the identifier out of the tuple
        row.append(row_name)
        
        for record in records:
            value = self.__records[record][row_number-1][1]
            row.append(value)
        
        return row

```

Thanks a lot!

---

### Post by cdekter on 2008-06-29
This is pretty trivial but... you don't need to use copy() to duplicate a list. Example:

```

l1 = list()
l1.append(someElement)
l2 = list(l1) # a new list containing someElement

```

This is only if you don't plan to modify any of the elements; in this case, using the above method is fine since you are copying a list of strings, which are immutable anyway.

---

### Post by luca.b on 2008-06-29
Problem is, it's actually modified later:

```
heading.remove(self.identifier)
```

And I need self.columns to remain constant. Hence the need for the copy.

---

### Post by raja on 2008-06-29
Was just testing the code and had a few comments - 

1. The necessary imports are os, csv and copy

2. line 21 can be written as 'row_names -= 1' and should actually come inside the 'if row_names is not None:' check. And this check itself can be written as 'if row_names:'

3. And shouldn't line 29 be 'if not header:' instead of 'if header:' ?

---

### Post by luca.b on 2008-06-29
Line 29 is "if not header" because if header is False I apply a "special" header in the manner R does, where "x" is the first column and the rest are just sequential number. I put a check like that because header is True by default.
Thanks for the rest of the suggestions, I'll put them in right away.

---

