---
title: "[C++] ofstream vector"
date: 2007-06-10
forum: Programming Talk
---

### Post by Redscare on 2007-06-10
Hey all. I was just trying to create a vector of ofstreams so that my programs doesn't eat up resources opening and closing files one by one. The first cache is that the ofstream class has no copy constructor, so I had to make a vector of pointers:
```
std::vector<std::ofstream*> o
```
 In the function that gets the individual filenames, the elements of the ofstream vector were added as follows: 
```
o.push_back(new ofstream(filename.c_str(), std::ios::app)
```
Finally, the file was written to by (I used the iterator iter):
```
*(*iter) << output << endl;
```
(*iter)->is_open() returned true. The whole program works and compiles fine but for one problem: when I add text to a file, rather than appending it as it should, it erases the whole file and rewrites it with only the data provided. So if "output" is "asdf" and the file contains "lala" already, the file will be written to, but only "asdf" will be in the file. I know that this happens because of the "new ofstream(...)". This creates a new pointer to a memory location without any prior information about the file. I was wondering if anyone could suggest a way around this problem and append the strings rather than overwriting the file. Thanks in advance.
Note: &ofstream(...) compiles but gives "segmentation fault (core dumped)" at runtime

---

### Post by PandaGoat on 2007-06-11
Before you write to the file use seek to set the place in the text's buffer to write it.  If the file is new and you use << without setting the position to write, then it will overwrite it.

```

std::vector<std::ofstream*> o;
o.push_back(new ofstream(filename.c_str(), std::ios::app);

// Loopy through
*(*iter)->seekp(0, ios_base::end); // 0 from the end
*(*iter) << output << endl;

```

---

### Post by Redscare on 2007-06-11
I haven't tested the code, but it appears correct but for one error: 
this:
```
*(*iter)->...
```
should be this
```
(*iter)->...
```
Thank you for the quick reply.
I am sorry, but the code above does not work. Thank you anyway, but can someone please help? By the way, it seems that the problem is not with writing, but with the actual creation of the **new** ofstream.

---

### Post by Redscare on 2007-06-11
I finally found the simple solution. PandaGoat's post is (I hope this does not come out wrong, and I am very grateful to you for sharing) irrelevant because of the std::ios::app in the new ofstream(...). The problem was I was checking the validity of the filestream with
```
if (ofstream(filename.c_str()))...
```
and I forgot to close the file. Now I have a new problem (sorry). It will write anything and it appends correctly, but the only way it will write is if I have an <<std::endl; at the end of the output, which causes every consequent output to be on a new line. There is no output without an std::endl. How can I remove this and still have output? Thanks again.

---

### Post by WW on 2007-06-11
Try calling [flush()]("http://www.cplusplus.com/reference/iostream/ostream/flush.html") after writing to the file.

---

### Post by Redscare on 2007-06-11
Thank you very much!!! It worked perfectly.

---

