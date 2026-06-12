---
title: "RAR file library for c++/java/perl/python help"
date: 2009-01-25
forum: Programming Talk
---

### Post by SadaraX on 2009-01-25
I want to make a password cracking program using brute force against RAR files. I need help getting a library to extract (or at least test passwords) on RAR files. I also need help using the library.

I downloaded unrarsrc from RarLabs but I am completely baffled how to write my own program to include their code and use their functionality.

If anyone knows how to use that, please help.

But any RAR library in C++ or Java or Perl or Python will fine. Though C++ is preferred for speed purposes.

A code example like this would be wonderful:

```

#include<rarlib>
...
int main()
{
  ...
  Rar my_rar("input.rar");
  my_rar.setPassword("password1");
  my_rar.extractTo("output_directory/");
  ...
}

```

---

### Post by bruce89 on 2009-01-25
As rar is a non-free format, you'll struggle to find a library that can do this.

---

### Post by Reiger on 2009-01-25
You don't require a library for this (of course, performance wise it will likely be better if you use one) because all you need to know is if your program 'got it right'. Any simple extraction test will therefore suffice, hence any archive extractor capable of handling RAR archives (preferably one that can inspect archives without decompressing the entire thing) at a decent speed will suffice provided it has a commandline option for the job. You could try 7zip.

EDIT: Come to think of it, 7zip being Open Source you can check out how 7zip communicates with its unRAR functions and make a wrapper for that in your program: [http://www.7-zip.org/download.html](http://www.7-zip.org/download.html).

---

### Post by slavik on 2009-01-25
I suggest you start at the rar format specs ...

---

