---
title: "c ++ loading a file to string to send via socket"
date: 2014-05-16
forum: Programming Talk
---

### Post by brick2 on 2014-05-16
Ok so I have a client server program that I wrote in c++. Took me a while! As I am not really an expert.
The problem that I encountered was following:
When I read from a file in to a string it only loads the first line into a string and that that is what is will send.
If need be I can post the whole code but I figured it would be more efficient if I posted the part of the code where the problem is.

```
string readFile()
{
    ifstream read("LOG.TXT");
    string str;
    int index = 0;
    if (read.is_open())
    {
        while (!read.eof()) //Tried using read.good()
        {
            getline(read, str);
            cout << str << endl;
            return str;
        }
    }
    else
        cout << "\nEror file is closed\n";
}
```

Any help any advice is welcomed.

---

### Post by brick2 on 2014-05-16
Solved it like this if anybody needs it.

[CODE]string readFile()
{
    ifstream read("LOG.TXT");
    string str, str1;

    int index = 0;
    if (read.is_open())
    {
        getline(read, str);
        while (read)
        {
            str1 += str;
            getline(read, str);
        }
        //cout << str1 << endl;
        return str1;
    }
    else
        cout << "\nEror file is closed\n";
}[\CODE]

---

### Post by slickymaster on 2014-05-16
> **brick2 said:**
> Solved it like this if anybody needs it.
<...snip...>

Since you solved it, please mark your thread as solved. Scroll to the top of your thread and look for the Thread Tools menu item on the right of the toolbar, click on this menu item to produce a dropdown menu and then click "Mark this thread as solved".

---

### Post by dwhitney67 on 2014-05-17
> **brick2 said:**
> Solved it like this if anybody needs it.

```
string readFile()
{
    ifstream read("LOG.TXT");
    string str, str1;

    int index = 0;
    if (read.is_open())
    {
        getline(read, str);
        while (read)
        {
            str1 += str;
            getline(read, str);
        }
        //cout << str1 << endl;
        return str1;
    }
    else
        cout << "\nEror file is closed\n";
}
```

Remember that getline() returns the stream being used, which then can be used directly as your conditional statement (the stream's operator bool() method is implicitly called for the conversion to a bool value) in your while-loop.

```

string readFile()
{
    ifstream read("LOG.TXT");
    string str, str1;

    while (getline(read, str))
    {
        str1 += str;
    }

    return str1;
}

```

P.S.  I would recommend that you pass the file name as a parameter to the function, and that you take action (such as throw an exception) if you are unable to open the file.

---

