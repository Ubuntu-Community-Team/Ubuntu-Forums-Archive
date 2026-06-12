---
title: "cin or getline?"
date: 2006-06-14
forum: Programming Talk
---

### Post by era86 on 2006-06-14
Hey, I was wondering how I would take entire line of user input. For example:

cout << "Name:" << endl;
cin >> inName;

cout << "Address:" << endl;
cin >> inAddress;

yields:

Name:
test name
Address:
street city state

I want it to store the whole line "test name" in inName and "street city state" in inAddress.  Any thoughts? Am I crazy? 

Thanks!

---

### Post by mjm115 on 2006-06-14
No, this is simple.  First just declare your variables as strings, and they will be remembered once you input the information.  The rest of your code is correct.

---

### Post by era86 on 2006-06-14
Sorry I didn't mention. They are declared as strings. For some wierd reason, when I put more than one word on the line, it only stores one word in the first string and then another word on the same line in the next string. I don't understand this. Anyone know how to get around this?

---

### Post by mjm115 on 2006-06-14
Take a look at [http://cplus.about.com/od/cprogrammingtip1/l/aa030702a.htm](http://cplus.about.com/od/cprogrammingtip1/l/aa030702a.htm)

'getline' should work just fine.  The reason this happened is that the insertion operator, >>, considers any white space to be a delimiter between items of data. White space is any non-alphanumeric character, including spaces, tabs (\t) and end of lines (\n). The standard C++ library provides an additional nonmember function, getline, which is used to read an entire line of text up to a programmer specified delimiter. If no delimiter is specified the default delimiter is for an end of line (\n).

---

### Post by era86 on 2006-06-14
I'll try the getline() approach and see if that works. If not, I don't know what to do about it. We'll see what happens. Thanks for your help.

---

### Post by LordHunter317 on 2006-06-14
By default, iostreams is trained to be whitespace sensitive.  It will terminate reading on any whitespace character.  

The simpliest way to do this is with the string getline() non-member function.  It is what I would do.

The other option is to call ignore() on cin and pass it the whitespace you want ignored, like so:```
cin.ignore(cin.widen(' '));
```This only works for one character tho.  I could be mistaken, but I'm not certain there is an offical standard way to give an iostream the whitespace to ignore.  Which is why it's usually better to read whole lines and then do parsing in another way.

---

### Post by Demon012 on 2006-06-15
I would recommend using cin.getline() here is the syntax for this situation.

The syntax is:

cin.getline([charArrayVariable],[lengthOfCharArray]);

and for those who would like to see a nice example

int main()
{
char name[15];

cout << "Please enter your name: ";
cin.getline(name,15);
cout << "Hello " << name << endl;
return 0;
}

Sorry if this is an old post but atleast this will help anyone else who comes by this post at a later date.

---

### Post by LordHunter317 on 2006-06-15
No, you shouldn't use istream.getline if you're reading into a std::string.  You should use the non-member getline() function defined in <string> that's eaiser to use.

---

