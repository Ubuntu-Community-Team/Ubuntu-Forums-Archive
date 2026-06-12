---
title: "reading file"
date: 2012-05-03
forum: Programming Talk
---

### Post by ewanewbie on 2012-05-03
Hello !

i can read the file in C++ but don't know how to read it between two points

to read the whole file

[HTML]
string STRING;
ifstream infile;
infile.open("file");

while(!infile.eof())
{
           getline(infile,STRING);
           cout<<STRING <<endl;
}
[/HTML]

what will be logic to stop reading the file when program finds -1 character? if you do not want to write down the code just show me the logic

thanks in advance.

---

### Post by souravc83 on 2012-05-03
Something like this should do (I didn't test the program, but just to give you the logic)

```
string STRING;
ifstream infile;
infile.open("file");

while(!infile.eof() || STRING!="-l" )
{
           infile>>STRING;   
           cout<<STRING <<endl;
}
```

Basic idea is that you can overload the ">>" operator to take in formatted input.Also, by using getline, you are reading a whole line at a time, and not a single word string.

Also, are you looking for a "String" or a "character"? They are not the same in C++. A string is an array of char variables.If you are looking for a character (i.e. a char variable), then read one character at a time by defining a character instead of a string.

---

### Post by ewanewbie on 2012-05-03
Hi !

thanks for reply, i fixed it and your instruction was very helpful

it was && instead of ||

while(!infile.eof() && STRING.compare("-1")){
                    getline(infile,STRING);
                    cout<<STRING<<endl;
}

but anyways thanks for the logic it worked
Regards,

Ewa

---

### Post by souravc83 on 2012-05-03
You are welcome. Indeed, it should be and '&&'. Sorry about that.
BTW, you can mark it as solved,if you feel that this has been solved.

---

### Post by lisati on 2012-05-03
*Thread moved to **Programming Talk**.*

---

