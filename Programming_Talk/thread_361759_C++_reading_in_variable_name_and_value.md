---
title: "C++ reading in variable name and value"
date: 2007-02-14
forum: Programming Talk
---

### Post by xtacocorex on 2007-02-14
This is going to be pretty complex, so I'll hopefully explain it as best as I can.  The title doesn't do this justice and I couldn't think of anything better.

I'm trying to read in a FORTRAN namelist into C++ which looks like this:
[php]&CONF1  NSPDIM=5000,    NNPDIM=500,     NPDIM=100,      NBPDIM=100,     NWPDIM=2000,    NWCDIM=100,     &END[/php]I am able to get it into a string and split is with a stringstream at the whitespace and dump everything to a vector.  I know that the first and last elements in the vector aren't needed, but the content between is.

My current code gets the string like this (dumped to std::cout)
[php]
&CONF1
NSPDIM=5000,
NNPDIM=500,
NPDIM=100,
NBPDIM=100,
NWPDIM=2000,
NWCDIM=100,
&END
[/php]For example, I need to get the variable nspdim set to it's value of 5000 (which I can convert to an int) by looking at what the variable name is.  Pretty much this is taking the first part of that string (before the =) in the vector element and getting that to be a variable in the program.  

It'd be nice to do this on the fly as to not waste space pre-defining variables.  Is this even possible?

Here is my current code
```

#include<iostream>
#include<string>
#include<fstream>
#include<sstream>
#include<vector>
#include<iterator>

int main()
{
    std::string t1, t2;
    std::ifstream fin;
    std::vector<std::string> s1, s2;
    std::stringstream st1;
    int p[6];

    fin.open("pmarc.conf");

    std::getline(fin,t1);
    std::getline(fin,t2);

    std::cout << "file contents" << std::endl;
    std::cout << t1 << std::endl;
    std::cout << t2 << std::endl;
    
    st1 << t1;
    while(st1 >> t1)
    {
        s1.push_back(t1);
    }
    
    st1 << t2;
    while(st1 >> t2)
    {
        s2.push_back(t2);
    }
    
    for (int i=0;i<s1.size();i++)
    {
        std::cout << s1[i] << std::endl;
    }

    fin.close();

    return 0;
}

```

---

### Post by Mirrorball on 2007-02-14
You can't create named variables on the fly, but you can use a std::map<std::string, int> like this:
```

std::map<std::string, int> vars;
vars['NSPDIM'] = 5000; // but the actual values would be from the file

```
But predefining the variables would be more efficient.

---

### Post by lnostdal on 2007-02-14
> It'd be nice to do this on the fly as to not waste space pre-defining variables. Is this even possible?

no, this is, within reasonable context - not possible in c/c++ (#1)

well, you could generate c/c++ code from your c/c++ program, then call gcc and have stuff compiled "at runtime" then execute the result .. but .. uhm .. i doubt you actually want to do this (?)

..sticking with c/c++ you are most likely best off doing something like the poster above shows


#1:
here, for instance, is how you can do something like this is lisp:
```

(defparameter *data-input* "
nspdim 5000
nnpdim 500
npdim 100
nbpdim 100
nwpdim 2000
nwcdim 100")



(defmacro withImportedVariables (data-string &body body)
  (let ((bindings nil))
    (with-input-from-string (ss data-string)
      (do ((name  (read ss nil nil) (read ss nil nil))
           (value (read ss nil nil) (read ss nil nil)))
          ((not (or name value)))
        (push `(,name ,value) bindings)))
    `(let ,bindings
       ,@body)))
  


(defun test ()
  (withImportedVariables #.*data-input* ;; Here you could refer to a file with text-data in instead of a variable with text-data in!
    ;; After some "magic" -- you can now refer to the imported variables:
    (format t "nspdim: ~A~%" nspdim)
    (format t "nnpdim: ~A~%" nnpdim)
    (format t "npdim: ~A~%" npdim)
    (format t "nbpdim: ~A~%" nbpdim)
    (format t "nwpdim: ~A~%" nwpdim)
    (format t "nwcdim: ~A~%" nwcdim)))


#|
Testing it:

cl-user> (test)
nspdim: 5000
nnpdim: 500
npdim: 100
nbpdim: 100
nwpdim: 2000
nwcdim: 100
nil
|#

```

---

### Post by LordHunter317 on 2007-02-14
> **xtacocorex said:**
> It'd be nice to do this on the fly as to not waste space pre-defining variables.  Is this even possible?I'm confused why these need to be variables in C++.  Are you calling FORTRAN code from this and need them set?  In that case, the rules of however you're doing the calling will probably impose requirements on you.

If you just need to preserve the name <-> value mapping, use a map.  I'm not sure why these need to variables with matching names in C++.  Unless you have a really good reason (like what I said above) they almost certainly do not.

---

### Post by xtacocorex on 2007-02-14
Well to answer LordHunter317's question I'm working on porting an old FORTRAN 77 code to either FORTRAN 90 or C++, and I'm weighing the options.  The programs input file uses namelists for most all the data, so the problem with porting to C++ would be tackling the reading of the input file.

I guess I was trying to recreate the FORTRAN namelist in C++ to keep reading the input file simpler, but that could be way more advanced than what I know with the language.  

std::map seems like an option, but I'll need to research it more.  

Thanks for the help.

---

### Post by Wybiral on 2007-02-14
I love C++ map's... VERY usefuly.

[http://www.cppreference.com/cppmap/index.html](http://www.cppreference.com/cppmap/index.html)

---

### Post by xtacocorex on 2007-02-14
Thanks Wybiral.

I did have another idea, so here is part code/part idea.
```

// skipping first and last vector elements
for (int i=1;i<vec.size()-1;i++)
{
    // vec[1]='NSPDIM=5000,'
    // code to parse vec[i] into variable name and value
    // vname = 'NSPDIM' <- string
    // vvalue = 5000 <- int
    if (vname == somehow check against defined variable without having one for each variable given)
    {
        predefined variable from above = vvalue
    }
}

```
Would this be a use for a map? Map the variable name and use it in the if statement, but how would that work in a loop?

---

### Post by Wybiral on 2007-02-14
I'm not sure I understand (sorry, I'm incredibly tired... On the edge of sleepdom)

What exactly are you trying to do?

---

### Post by Mirrorball on 2007-02-14
You won't need a vector anymore if you use a map. Suppose you have read a line from the file and parsed it. The variable name is stored in std::string vname and the vvalue in int vvalue. Just do:
```

map[vname] = vvalue;

```

---

### Post by xtacocorex on 2007-02-14
> **Wybiral said:**
> I'm not sure I understand (sorry, I'm incredibly tired... On the edge of sleepdom)

What exactly are you trying to do?
This is where I realize that it's not going to work and I'll have to do stuff manually, which isn't bad, but will take a lot more code if I go the C++ route. 

I have to think on this more.

---

### Post by xtacocorex on 2007-02-14
> **Mirrorball said:**
> You won't need a vector anymore if you use a map. Suppose you have read a line from the file and parsed it. The variable name is stored in std::string vname and the vvalue in int vvalue. Just do:
```

map[vname] = vvalue;

```
If I do this, how will this work if I have a variable that has what is stored in vname?

Example:
int NSPDIM, vvalue;
string vname;
vname = "NSPDIM";
vvalue = 5000;
NSPDIM = vvalue;

How could that be done automatically and with a loop and no prior knowledge of variables?

---

### Post by Mirrorball on 2007-02-14
You can always write a program that writes C++ code from Fortran code. At least it won't be as boring as doing it manually.

---

### Post by Mirrorball on 2007-02-14
> **xtacocorex said:**
> How could that be done automatically and with a loop and no prior knowledge of variables?
No, it can't be done. Your only two options are: either store them in a map or predefine the variables yourself and assign their values in a switch statement.
**Edit: **Let me be a bit clearer. If you go the map route, you won't need  int NSPDIM anymore. This is how you'll be getting the value of NSPDIM:
```

map['NSPDIM'];

```

---

### Post by Mirrorball on 2007-02-14
Here is the general algorithm for a map:
```

std::map<std::string, int> vars;
std::string line;
// open file
while(std::getline(file, line)) {
  std::string vname; // variable name
  int vvalue; // its value
  // parse the line
  vars[vname] = vvalue;
}

```Later, if you want to add NSPDIM to NNPDIM for instance, you'll do:
```

int sum = vars['NSPDIM'] + vars['NNPDIM'];

```

---

### Post by LordHunter317 on 2007-02-14
Use a map, the syntax is similar to what mirrorball suggested.  This will likely be the best way, though understand that if you feed programs that are buggy into this thing, you may run into issues.

---

### Post by xtacocorex on 2007-02-14
Thanks Mirrorball for the good instruction on the map, it was a long day at work and just wasn't understanding.

Thanks again LordHunter317 and Wybiral for your help.

I don't know what route I'm going to take, but I do have a better understanding of what I can and can't do with C++ with respect to the old FORTRAN code.

---

