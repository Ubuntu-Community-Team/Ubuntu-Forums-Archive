---
title: "C++ read text file two times"
date: 2008-11-25
forum: Programming Talk
---

### Post by Nergar on 2008-11-25
lets suppose I need something like this:

[PHP]
while (! myfile.eof() )
    {
      getline (myfile,line);
      cout << line << endl;
    }
    myfile.close();
//then agian
while (! myfile.eof() )
    {
      getline (myfile,line);
      cout << line << endl;
    }
    myfile.close();
[/PHP]

I need to read the file again but from the beginning.

What I'm doing is closing the file and opening it again before the second read but I'm pretty sure theres a better way.

Thanks a lot in advance.

---

### Post by dwhitney67 on 2008-11-25
Do *not* close the file.  To reset the "get" pointer to the beginning of the file:
[php]
myfile.seekg(0, ios_base::beg);
[/php]

---

### Post by Nergar on 2008-11-25
> **dwhitney67 said:**
> Do *not* close the file.  To reset the "get" pointer to the beginning of the file:
[php]
myfile.seekg(0, ios_base::beg);
[/php]

hmmm, do I need anything else? it isn't working.

---

### Post by dwhitney67 on 2008-11-26
Sorry about that; I did not realize that seekg() would fail to operate properly if the eof-flag was set.

I've verified that the following sequence of statements will solve the issue of resetting the file pointer:
[php]
...
    std::string line;

    while (getline(file, line))
    {
      std::cout << line << std::endl;
    }

    std::cout << "\n\n**** reading file again ****\n\n";

    file.clear();
    file.seekg(0, std::ios_base::beg);

    while (getline(file, line))
    {
      std::cout << line << std::endl;
    }
...
[/php]

P.S.  Specifying file.seekg(0) also works just fine.  Using the format shown above tells the fstream how many bytes to offset from the beginning of the file.

---

