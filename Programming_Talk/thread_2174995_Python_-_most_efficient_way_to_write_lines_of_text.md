---
title: "Python - most efficient way to write lines of text to file"
date: 2013-09-17
forum: Programming Talk
---

### Post by chrisall on 2013-09-17
Hi,

I have a python program something like:

```
for string in inputfile:
    output = myfunction(string)
    output = str(output)
    print output
    f = open(outputfile, 'a+')
    f.write(output+'\n')
    f.close()
```

As far as writing out the file is concerned, is there a more efficient way of doing this, rather than the explicit open/write/close for every line?

Cheers,
Chrisall

---

### Post by ofnuts on 2013-09-17
Well, if you open the output before looping on the input, you don't need to open/close around each line (at best you can use flush() but IMHO that would be overkill here).

You can also investigate using the ["with"](http://docs.python.org/2/reference/compound_stmts.html#grammar-token-with_stmt) syntax (some examples [here](http://stackoverflow.com/questions/1369526/what-is-the-python-keyword-with-used-for)).

---

### Post by r-senior on 2013-09-17
Do you even need to write to a file? If you write to stdout, you can redirect to a file when you run:

```
myscript.py > somefile
```

This could give you more flexibility with regard to the output, depending on what you are trying to do. For example you could append multiple runs or redirect errors elsewhere.

(The example above assumes the correct shebang line and executable permissions set).

---

