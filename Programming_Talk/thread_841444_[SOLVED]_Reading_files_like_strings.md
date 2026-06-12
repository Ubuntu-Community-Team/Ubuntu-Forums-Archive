---
title: "[SOLVED] Reading files like strings?"
date: 2008-06-26
forum: Programming Talk
---

### Post by Zeotronic on 2008-06-26
C++/fstream: First off, you must forgive me... I'm going to have a hard time with this for I do not think I know the proper terminology.

Since I started programming a year and a half ago (and note that I am basically self taught), for reasons that I cannot recall at the moment, I have only ever been reading files in binary... the only files I have ever tried to read that weren't binary were obj files, and I had a hard time of it. Could someone direct me to information related to, or give me pointers on, reading files like strings... or as strings, or whatever?

---

### Post by dwhitney67 on 2008-06-26
Here's a simple example where the /etc/hosts file is opened, and its contents are dumped to a terminal (using cout).
[PHP]#include <fstream>
#include <iostream>

int main()
{
  std::fstream fs("/etc/hosts", std::ios::in);

  if (fs)
  {
    char buf[80] = {0};

    while (fs.getline(buf, sizeof buf))
    {
      std::cout << buf << std::endl;
    }
  }
  else
  {
    std::cout << "Error:  Cannot open file /etc/hosts" << std::endl;
  }
  return 0;
}[/PHP]

---

