---
title: "Reading in a file in C++"
date: 2013-03-02
forum: Programming Talk
---

### Post by Amulon on 2013-03-02
[COLOR=#000000][FONT=verdana]Here is the code to do sorting by insertion. I am getting an 'out of range error'. How do I better read in the text file and store it in the Vector without running into this problem?[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Thanks in advanced

[/FONT][/COLOR]```
[COLOR=#000000]    
 [/COLOR]       cout << "please enter the address of the file: " << endl;[COLOR=#000000]
[/COLOR]        getline(cin, file1);	ifstream textFile1 (file1);


	//Tests the file
	if (textFile1.fail())
	{
		cout << "File was not found"<< endl;
		system("PAUSE");
		exit (1);
	}
	else

		cout << "\nFile opened successfully" << endl;
	do
	{
		textFile1 >> insertion[count1];
		count1 ++;
	}while(!textFile1.eof());


	//Insertion Sort1
	for(first_unsorted1 = 1; first_unsorted1 < count1; first_unsorted1++)
	{
		if(insertion[first_unsorted1] < insertion[first_unsorted1 - 1])
		{
			position1 = first_unsorted1;
			current1 = insertion[first_unsorted1];
			do
			{
				insertion[position1] = insertion[position1 - 1];
				position1--;
			}while(position1 > 0 && insertion[position1 - 1] > current1);
			insertion[position1] = current1;
		}
	}



```[COLOR=#000000][FONT=verdana]
[/FONT][/COLOR]

---

### Post by DougB1958 on 2013-03-02
Do you initialize count1 anywhere? If not, doing so is the first thing I'd try.

---

### Post by Amulon on 2013-03-02
Yeah, all of the variables have been previously declared. Do you want me to provide that too?

---

### Post by trent.josephsen on 2013-03-02
> **Amulon said:**
> Yeah, all of the variables have been previously declared. Do you want me to provide that too?

declaration != initialization

But when you're asking for help finding an error in your code, it's always good to provide a compilable example.

---

### Post by spjackson on 2013-03-03
> **Amulon said:**
> [COLOR=#000000][FONT=verdana]Here is the code to do sorting by insertion. I am getting an 'out of range error'. How do I better read in the text file and store it in the Vector without running into this problem?[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]
[/FONT][/COLOR]```
[COLOR=#000000]
[/COLOR]    do
    {
        textFile1 >> insertion[count1];
        count1 ++;
    }while(!textFile1.eof());

```


In the absence of complete code, I'm going to guess that insertion is a std::vector<std::string>. If so, you need to grow the size of the vector, then write to the new element. push_back() does this.

```

    do
    {
        std::string s;
        textFile1 >> s;
        insertion.push_back(s);
        count1 ++;
    }while(!textFile1.eof());

```

---

### Post by dwhitney67 on 2013-03-03
Use a set, not a vector, if you want your string entries sorted.

```

#include <set>
#include <iterator>
#include <iostream>

int main()
{
    using namespace std;

    set<string> myStrings;

    myStrings.insert("fum");
    myStrings.insert("fee");
    myStrings.insert("fi");
    myStrings.insert("fo");

    copy(myStrings.begin(), myStrings.end(), ostream_iterator<string>(cout, "\n"));
}

```
If you must use a vector, then I "smell" homework.

As for your do-while loop, there's an issue there as well:
```

do
{
    textFile1 >> insertion[count1];
    count1 ++;
}while(!textFile1.eof());

```
Do not attempt to insert into your container until you know that you have a valid entry to insert.  eof() will NOT return true until you have actually attempted to read past the end of the file.  Thus if the last entry in the file has successfully been read, then eof() will report false.  It will take another read (and it will be unsuccessful) for eof() to return true.

This may be a better style loop to use:
```

string s;
while (textFile1 >> s)
{
    // do something with s
}

```
P.S.  If you anticipate having duplicate strings, then use a multiset.

---

