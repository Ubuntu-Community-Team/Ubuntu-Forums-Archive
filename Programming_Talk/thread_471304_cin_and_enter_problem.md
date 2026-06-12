---
title: "cin and enter problem"
date: 2007-06-11
forum: Programming Talk
---

### Post by Redscare on 2007-06-11
Hello again. Sorry for all the questions:(, but I need help on this one. In a C++ function I wrote, the user is asked for input. When the user wants to stop reading in data, he inputs a blank line and he is done. Also, if the user inputs a blank line before he inputs any data at all, an error message is shown and he is forced to input again. This all works except for one part: while when no data is entered and the user inputs a blank line it is detected immediately, but if the user inputs data, he inputs a blank line and it is not detected, but the second blank line is.
Here's a skeleton of the code (all namespaces are correct and all the included headers are correct as well):
```
while(getline(cin, str) && done == false)
{
     if(str.empty() == false)
           {
                   vec_strings.push_back(str);
           }
      else
         {
               if (vec_strings.empty() == true)
                         cout << "Error!!!! Please input data" << endl;
               else
                    done = true;
          }
}
cout << "done" << endl;
```
Output:
```

                 <-----note only one blank line
"Error!!!! Please input data"
Example
               <------note two blank lines
               <-----------------------------
"Done"
```
Also, I would rather use cin >> str in place of getline(cin, str), but that never detects an empty string (so no amount of blank lines would have any effect). If there is a way to do this using cin >> str that would be even better, but please explain the method to use with both functions (I know cin is an object, but it's simpler to say that way).

---

### Post by samjh on 2007-06-11
Try using cin.ignore() at the end of your while loop.  This is clear out any EOL that might play havoc next time you try to get user input.

So your code will look like (with cin.ignore() in bold text):
```
while(getline(cin, str) && done == false)
{
     if(str.empty() == false)
           {
                   vec_strings.push_back(str);
           }
      else
         {
               if (vec_strings.empty() == true)
                         cout << "Error!!!! Please input data" << endl;
               else
                    done = true;
          }
      **cin.ignore();**
}
cout << "done" << endl;
```

---

### Post by Redscare on 2007-06-11
Thank you for the quick reply, but this does not work...still have extra lines. Actually, there is more now: 3 extra lines after input before it is recognized as a blank line!!!

---

### Post by samjh on 2007-06-11
[EDIT: wrong answer]

---

### Post by Redscare on 2007-06-11
I'm sorry, but I think you misunderstood the way the code has to work. If there is nothing in vec_strings, then the error message should be displayed after a blank line, but if there is data in vec_strings, then there should be no error and the loop should exit. Also, the user should be able to input more than one string if they wish.

---

### Post by samjh on 2007-06-11
> **Redscare said:**
> I'm sorry, but I think you misunderstood the way the code has to work. If there is nothing in vec_strings, then the error message should be displayed after a blank line, but if there is data in vec_strings, then there should be no error and the loop should exit. Also, the user should be able to input more than one string if they wish.

Oh I see.  My apologies for the wrong answer then.

[EDIT: I got what you mean.]

---

### Post by samjh on 2007-06-11
OK, this should do the trick:
```
while(getline(cin, str)) {
    if(str.empty() == false) {
        vec_strings.push_back(str);
    } else {
        if(vec_strings.empty()) 
            cout << "Error!!!! Please input data" << endl;
        else
            break;
    }
}
cout << "done" << endl;
return 0;
```If str is not empty, it will add to vec_string.  If str is empty and vec_string empty, it will display the error and make the user input something.  If str is empty and vec_string has data in it, it will quit.

Basically the same as what I said before about testing done in the while loop.  You don't need to test it.  If you try to test it as the while-loop condition, then it will go through the whole loop again just to see if done is true or not.

---

### Post by Redscare on 2007-06-11
Thanks alot, that worked like a charm, but I have two more questions. First of all, can you please explain in more detail why my way didn't work (using a bool instead of break) and how one would do this with cin >> filename;?
Thanks again.

---

### Post by the_unforgiven on 2007-06-12
> **Redscare said:**
> Thanks alot, that worked like a charm, but I have two more questions. First of all, can you please explain in more detail why my way didn't work (using a bool instead of break) and how one would do this with cin >> filename;?
Thanks again.
That is because getline() will block for you to enter something and only when it returns will it actually do the check on the "done == false".
That is also the reason why you had to hit enter twice (resulting in 2 blank lines) to terminate the loop.
HTH ;)

---

### Post by samjh on 2007-06-12
Since I'm not a C++ programmer, I have no hope of being able to explain it properly myself! :o   I only know basic C++ to port code into other languages, rather than programming in C++ itself.

Here is a Google find with someone having similar problems, and an explanation about the behaviour of cin, which your getline uses:
[http://www.computing.net/programming/wwwboard/forum/11362.html](http://www.computing.net/programming/wwwboard/forum/11362.html)

---

### Post by Redscare on 2007-06-12
Thanks for the explanation the_unforgiven, now instead of the bool being the second condition I just made it the first and everything works fine. The only problem that remains unsolved is how to accomplish my goal using cin >> filename in place of getline(cin, filename). Samjh, thanks again for the reply, but that code doesn't work at all (the only way to flush the input stream in C++ is with cin.ignore()). Please, can someone solve this?

---

### Post by samjh on 2007-06-12
> **Redscare said:**
> The only problem that remains unsolved is how to accomplish my goal using cin >> filename in place of getline(cin, filename).?

I assume filename is a file you want to get inputs from.

As far as I know, you cannot directly use cin with files (you cannot use cout either).  This is because cin (and cout) use standard input/output, which most systems treat as keyboard input/output.

You will need to create an ifstream object, like this:
```
ifstream filename("inputfile.txt");
```
and then read information from it using one of several functions, such as getline:
```
string str;
getline(filename, str);
```

To write to a file, create an ofstream object, and then use it like cout:
```
ofstream filename("outputfile.txt");
filename << "I am writing this to filename.\n";
```
Notice that in both examples I've given, the ifstream and ofstream objects replace cin and cout, respectively.  This is because ifstream and ofstream are child objects of istream and ostream, respectively, for dealing with files; while cin and cout are child objects of istream and ostream, respectively, for dealing with standard i/o - ie. keyboard.




Gosh, all this is starting to inspire me into learning more C++. ;)

---

### Post by LaRoza on 2007-06-12
This inspired me too, as I was reading it.

I found this useful tutorial, Tips and tricks for using C++ I/O (input/output), at

 [http://www.augustcouncil.com/~tgibson/tutorial/iotips.html](http://www.augustcouncil.com/~tgibson/tutorial/iotips.html)

I found it informative, maybe you all will too.

---

### Post by the_unforgiven on 2007-06-12
The following 2 books are one of the greatest resources on C++:
[Effective C++]("http://www.amazon.com/Effective-C%2B%2B-Addison-Wesley-Professional-Computing/dp/0321334876/ref=pd_bbs_sr_1/104-1036018-1590345?ie=UTF8&s=books&qid=1181651981&sr=1-1")
[More Effective C++]("http://www.amazon.com/More-Effective-C%2B%2B-Improve-Programs/dp/020163371X/ref=pd_bbs_sr_2/104-1036018-1590345?ie=UTF8&s=books&qid=1181651981&sr=1-2")

Both are by Scott Meyers.

These two books are essential (whether you do serious C++ programming or not).

---

### Post by Redscare on 2007-06-12
samjh, I'm sorry, but when I said cin >> filename, I meant cin >> str. So what I want to do is in this code:
```
while (done == false && getline(cin, str))
	{
		//Check to make sure not a blank line
		if (str.empty() == false)
		{
			vec_strings.push_back(filename);
		}
		//If a blank line is inputted...
		else
		{
			if (vec_strings.empty() == true)
				cout << "At least one valid string must be read." << endl;
			else
				done = true;
		}
	}
```
What this code does (it's a skeleton of the actual function, but it has all the important parts) is it waits for user input. If the user inputs characters, then the program reads them into a string vector. If the user inputs a blank line and there is already data, no more data is inputted into the vector. But if a blank line is used as input, then an error message is displayed and the program asks for at least one piece of valid input. What I want to do is instead of using getline(str, cin) use cin >> str. Thanks for being interested.

---

### Post by samjh on 2007-06-12
> **Redscare said:**
> What I want to do is instead of using getline(str, cin) use cin >> str. Thanks for being interested.

I'm afraid that's probably impossible.

cin >> str will stop reading when it encounters spaces.  So for cin >> str to work, the user will have to input something without spaces.

You will continue having to use getline(cin, str), which is designed to read input from cin until EOL is reached.

---

### Post by Redscare on 2007-06-12
Yes, I never said the input had to have spaces. I may want the user to just input "example". No spaces at all. Is there really no way to do this with cin >> str? Thanks again for the replies.

---

### Post by samjh on 2007-06-12
I don't think C++ likes having cin >> str inside a while-loop test condition with another test.

This works fine, and is very common:
```
while (cin >> str) {
    // do whatever
}
```

But I've never seen this in any code:
```
while ((cin >> str) && test = true) {
    // do whatever
}
```

You could use break instead of testing for done instead, so you can just have cin >> str as the only test condition for your while-loop.  That will allow you to use cin >> str, instead of getline(cin, str).

---

### Post by Redscare on 2007-06-13
This code does not work. No amount of enters ends the input.

---

### Post by slavik on 2007-06-14
no offense, but I think your code is somewhat "inefficient" (since youa re doing a comparison everytime.

I would suggest the following:
1. read lines until a non-blank line is read (output errors or such for every blank line as needed/wanted)
2. read lines until a blank line is encountered. :)

this way, when you are in state #2 (first line is not blank), you do not keep checking if the line is blank.

Also, while (cin>>str) {} will only stop when an EOF is encountered, since operator>>() returns istream& (cin) or 'false' when EOF has been encountered.

psuedocode:
//state 1
cin>>str;
while(str.length == 0) { print error message; cin>>str; }
//state 2
while(str.length != 0) { process string; other stuff; cin>> str; }

---

### Post by PandaGoat on 2007-06-14
>> is the input operator in streaming objects basically.  somestream >> somevariable.  Streams define >> as the string of letters in the stream from its current position to the next terminating character. For instance, in a stream that read "Hello\0world", >> would first read "Hello" and secondly read "world".  istream::getline() can be thought of as another operator that gets the line begenning at the current position to the end of the line--untill "\n" is met.

Summary:  You can't use >> to get the entire line.

```

string s;

while(getline(cin, s))
{
// The next lines will wait untill user inputs somethings and hits enter

		//Check to make sure not a blank line
		if (!s.empty())
		{
			vec_strings.push_back(s);
		}
		//If a blank line is inputted...
		else
		{
			if (vec_strings.empty()e)
				cout << "At least one valid string must be read." << endl;
			else
				break; // End any more iterations of the loop
		}

}



```

---

### Post by samjh on 2007-06-14
> **Redscare said:**
> This code does not work. No amount of enters ends the input.

If you are going to use cin >> str as the only test condition for your while loop, you will need to use break in order to exit the loop.  Otherwise, it will be endless as long as cin >> str returns a non-EOF character.

I think for sanity's sake, you're best off sticking to getline. :)  It's more flexible and there aren't any disadvantages to using it.

---

