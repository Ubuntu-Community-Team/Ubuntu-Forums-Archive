---
title: "Configuration Files Editing C++"
date: 2009-02-20
forum: Programming Talk
---

### Post by camper365 on 2009-02-20
I am writing a program that needs to use configuration files.
I know about fstream, and can do binary files, but can't figure out how to do text configuration files.
Is there a library that I need to include, or is there a function that I'm missing?

---

### Post by PandaGoat on 2009-02-20
I would almost say you are thinking about it incorrectly.  A way of writing configuration files--a library if you will--is built atop fstream. More specifically, you can use fstream and create your own, syntax, protocols, *et cetera* for configuration files or find a library that has done something like this already.

JSON is good: [http://www.json.org/](http://www.json.org/).  There are various libraries for C++.  Here is an example file that can be parsed by using a JSON library:
```

{
    "Tree1" : 
    {
        "Color" : "Green"
    }
}

```

---

### Post by camper365 on 2009-02-20
What I am trying to do is take the syntax of the linux configuration files (such as ones that end in rc) and make one for my program.

---

### Post by monkeyking on 2009-02-21
I don't think there is one golden standard configuration file syntax for windows.

I would just write the different pars on different lines.
And then just remember internally what is on which line.

something

[PHP]
10 times to calculate
5 times to sleep
outputfile.txt this is the output file
[/PHP]

Then I would only read until the first whitespace, and then typecast it to the correcttype. You can then fill all the information regarding the parameter on the rest of the line.

---

### Post by ynef on 2009-02-21
Like the first reply in the thread says, you should use some library that already does the job for you. Unless you set out to make the ultimate configuration file reader and for that reason **have to** do it yourself, using a library is much more efficient: both for you as a programmer and for the end user. Bugs are less likely in well-known professional libraries than in something written during a particularly boring afternoon, and if one is found, the library will be updated very quickly -- your code? Probably not for a long while, and then only if you feel like it.

---

