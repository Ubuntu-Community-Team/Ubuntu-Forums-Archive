---
title: "C++ File I/O"
date: 2007-08-17
forum: Programming Talk
---

### Post by Yes on 2007-08-17
Is it possible to open a file like this?

```
void openFile (string fileName)
{
fstream myfile;
myfile.open (fileName);
}
```

Because that's what I have now, and I keep getting a compilation error, "no matching function call for call to 'std::basic_fstream<char, std::char_traits<char> >::'open(std::string&)'".

Thanks.

---

### Post by Paul820 on 2007-08-17
It has to be a cstyle string, so it should be

```
myfile.open( filename.c_str() );
```

---

### Post by Yes on 2007-08-17
Great, thank's!

---

