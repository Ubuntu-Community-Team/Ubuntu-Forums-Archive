---
title: "Conversion woes - c++ outputting differently on ubuntu"
date: 2007-08-08
forum: Programming Talk
---

### Post by CryptiniteDemon on 2007-08-08
Hah, well this is starting to grate on my nerves.  I finally got my makefile working and compiled one of my programs using the command line.  What's irritating me so badly is that when I use syntax like this:

```
cout << bookowner << "\'s list" << endl;
```

Whatever information is in bookowner is automatically overlapped by the "s list" text portion of the code.  Which I really don't understand.

However, when i used the following syntax it worked just fine.  But I don't want a new line in my text formatting.
```
cout << bookowner << endl;
cout << "\'s list" << endl;
```

book owner is a string by the way.

So why is it doing this?  I've used Visual Studio the since i started programming, but now that I'm switching to linux there's a whole bunch of stuff I have to get used to in my c++ programming.  I just don't understand why it truncates parts of the book owner variable.  Is there anyway to flush the buffer without a new line?

This isn't the only mistake in the program either.  Some other stuff is wrong, but I'll expand on that after I get an answer for this.  It compiles and displays perfectly within windows.  I'm just curious as to why my string variable is over lapped by the text.

---

### Post by [h2o] on 2007-08-08
Does
```
cout << bookowner << "'s list" << endl;
``` work better?

I don't think the \' is required if you use " to construct the string. At least I didn't need to a few hours ago :)

Also, you could try:
```
cout << bookowner << flush;
cout << "\'s list" << endl;
``` In case there is some kind of weird flushing error.

Good luck!

---

### Post by mgoblue on 2007-08-08
Can you try removing the \?

---

### Post by hod139 on 2007-08-08
I'm not sure what your trouble is.

```

#include<iostream>

int main(void){
  std::string bookowner("Steve");
  std::cout << bookowner << "\'s list" << std::endl;

  return 0;
}

```

when I run it, I get
```

./a.out
Steve's list

```

Are you putting a \n at the end of the bookowner string?
```

#include<iostream>

int main(void){
  std::string bookowner("Steve\n"); **//bad**
  std::cout << bookowner << "\'s list" << std::endl;

  return 0;
}

```
This produces:
```

Steve
's list

```

---

### Post by Soybean on 2007-08-08
Like h2o mentioned, flush gives you the flushing power of endl, without the newline.

But that seems like a bit of a band-aid solution... you really want to know WHY it's happening, right?

Naturally, the code you posted isn't SUPPOSED to overwrite the contents of the variable, in Linux or anywhere. Something is going wrong, and it's not within the code you've shown us.

So... can you give us a bit more information? Say, an example of what the contents of bookowner might be, or the code you used to declare bookowner, or some information about what was printed most recently before that bit... or anything else you think might be related. When you say it's a string, you do mean a std::string, right?

One thing to watch out for is mixing C-style output (like printf) with C++-style output streams (like cout). Combining them isn't supported by the standard, so it's the sort of thing that might work on one compiler and do something crazy and weird on another.

---

### Post by CryptiniteDemon on 2007-08-08
I guess I should say that I'm reading the book owner from a text file.  

The thing is I'm just using regular ifstream.  I can get it to work with and without the escape character by just declaring a string and setting it's value, but when I set the value using getline it doesn't print out correcty.


Here's the main function I'm using.  It's significantly cut down and all of my classes and everything are taken out for simplification purposes, but I still get the same result no matter waht

```
#include <iostream>

using namespace std;

#include <string>

#include <fstream>



int main(){

     //1. Access the text file containing the list of books.

    ifstream indata;

    indata.open("inputFile.txt");





    //2. Take the first line (the person whose 

    //   book list it is) and store it.

    //3. Skip the blank line in the file.

    string bookOwner;

    string blankLine;

    getline(indata, bookOwner);

    getline(indata, blankLine);

    cout << bookOwner << flush << "'s myBook List \n \n";

    indata.close();



    return 0;



}

```

This is my text file.  It's just plain format txt.
```
Adam



Perfectly Legal:  The Covert Plan to rig America's tax system

Some guy

$24.99



Mythology

Edith Hamilton

$18.00



Dunkarre

Shakespeare

$11.95



Some book1

Some guy 1

$ 3.85
```

No matter what I do I just end up getting "'s book list" instead of "Adam's Book list"  That is unless I use endl but that's not what I want.

flush didn't work either for whoever suggested it.

---

### Post by hod139 on 2007-08-08
Your code snippet ran fine for me.
```

$./a.out
Adam's myBook List

```

---

### Post by GeneralZod on 2007-08-08
If you're reading from a file, you're not accidentally keeping a "\r" on the end of the read strings, are you? This is both a likely occurrence and would account for what you are seeing here.

---

### Post by Soybean on 2007-08-08
I think Zod is probably right... sounds like linefeeds.

In Windows, text files terminate each line with a carriage-return + a linefeed, while Linux and similar systems only use a linefeed. Since your text file was (I assume) created in Windows, at the end of each line it probably has "\r\n" instead of just the "\n" that Linux expects. So, after the getline, your bookowner variable would contain "Adam\r". The \r returns the cursor to the beginning of the line, so anything printed after that overwrites what was already printed.

So, options:
1) Convert the text file to unix format. According to the wikipedia "Newline" entry, the following should work:
```
tr -d '\r' < inputfile > outputfile
```
Where "inputfile" would be inputFile.txt, and "outputfile" would be whatever you want to call the converted version.

2) Strip out the \r in your program. A little trickier (not sure of the best way off the top of my head, but there are many ways), but this way you could use the same input file in Linux and Windows.

---

### Post by CryptiniteDemon on 2007-08-08
Yep, it was formatted in windows.  I rewrote the file in linux and it worked just fine.

Thanks guys.

---

