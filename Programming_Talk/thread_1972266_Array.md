---
title: "Array"
date: 2012-05-03
forum: Programming Talk
---

### Post by ewanewbie on 2012-05-03
Hi Guys !

I am new to C++ and i'm trying to store data into Array, so need help, if anyone is kind.

my data is stored in a file and each line contains a number, a tab (space) and then text.

for example

1 this is first line
1 continuity of first line
2 second line
3 third line
4 forth line
4 continuity of forth line
4 still a forth line
5 fifth line
.
.
.
so on

so i'm trying to store states
numbers are the identifiers and text is description
 
for example: 1 is identifier and "this is first line" is description

and when i required identifier i write state.id 
for description i write state.text or state.desc

in short want to make a class of it



thanks in advance

Regards,

Ewa

---

### Post by sisco311 on 2012-05-03
Thread moved to **Programming Talk**.

Sounds like homework. From the [code of conduct](http://ubuntuforums.org/index.php?page=policy) that you agreed to when you created your account:

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.




Where did you get stuck?

---

### Post by ewanewbie on 2012-05-03
Hi!

Sorry this is not assignment, i'm working on project but the problem is we don't have tokenizer class in C++ and i'm feeling comfortable in java. so only needed help but thank i worked it out myself..

and here is the code what i asked here on the forum and you were thinking it was a homework.. posting here to help others.

```
#include<iostream>
#include<fstream>
#include<string>
#include<limits>
using namespace std;

int main(){
          string STRING;
          ifstream infile;
          infile.open("data.txt);

          while(infile>>STRING){
                        court<<STRING<<endl;
         infile.ignore(numeric_limits<streamsize>::max(),'\n');
          }
         infile.cose()
}
```


anyways thanks

Best Regards,

Ewa

---

### Post by ewanewbie on 2012-05-03
Hi Guys!

Is there any such a method in which I can use before or after this file.ignore(), to actually keep the rest of the line? I mean, the rest of the line shall be used.

Considering that the first column of the text file is an integer, something inside of the while loop like:

```
 value = atoi(str.c_str());
(if value==1){
cout <<restOfTheLine<<endl;
}

```

Regards,

Ewa

---

### Post by DaviesX on 2012-05-03
I think you need to wrap your code within code tag so that everyone could understand what you had written :)

["CODE"]
// You code goes here
["/CODE"]
without quotation mark

---

### Post by DaviesX on 2012-05-03
There is a C function that can complement your requirement if you don't care about mixing
**int sscanf(const char ****str***, const char ****format*[B], ...);
[/B][http://linux.die.net/man/3/scanf](http://linux.die.net/man/3/scanf)

ie. 
```

sscanf ( stringToken, "%d %s", &id, &description );

```

---

