---
title: "Strange problem with C++ string tokeniser"
date: 2009-01-09
forum: Programming Talk
---

### Post by bluedalmatian on 2009-01-09
Im trying to use the following code to split up a string into a vector of strings where ever it encounters ###XSWITCH### as a delimiter.

For example when in1 is passed in it should give a vector containing

1
2
3
192.168.254.1
5060
TCP
TCP

yet it gives

1
2
3
192.168.254.1
5060
P
P


in2 & in4 give other examples of its strange behaviour. in3 works as expected. Anyone any ideas why its doing this? I cant see the logic of it.

Thanks


Save the following as one .cpp file and try running it to see what i mean
```


#include <stdio.h>
#include <string>
#include <vector>
#include <iostream>
std::vector<std::string> deserialiseRPCString(std::string str);
int main()
{
	std::string in1("1###XSWITCH###2###XSWITCH###3###XSWITCH###192.168.254.1###XSWITCH###5060###XSWITCH###TCP###XSWITCH###TCP###XSWITCH###"); //TCP comes out as P both times
	std::string in2("1###XSWITCH###2###XSWITCH###3###XSWITCH###192.168.254.1###XSWITCH###5060###XSWITCH###UDP###XSWITCH###SIP###XSWITCH###"); //SIP comes out as P
	std::string in3("1###XSWITCH###2###XSWITCH###3###XSWITCH###192.168.254.1###XSWITCH###5060###XSWITCH###UDP###XSWITCH###sip###XSWITCH###");  //works
	std::string in4("1###XSWITCH###2###XSWITCH###3###XSWITCH###192.168.254.1###XSWITCH###5060###XSWITCH###TCP###XSWITCH###H248###XSWITCH###"); //TCP comes out as P, H248 comes out as 248
	
	std::vector<std::string> out;
     
	out=deserialiseRPCString(in4);  //change string passed in here to in1, in2, in3 etc

	std::vector<std::string>::iterator it;
	for (it = out.begin(); it !=out.end(); it++)
	{
		printf((*it).c_str());
		printf("\n");
	}
	
	
	return 0;
}

std::vector<std::string> deserialiseRPCString(std::string str)
{
	/*
	Given a string in the form 1###XSWITCH###1234###XSWITCH###xyz###XSWITCH###
	split it on ###XSWITCH### and return a vector with the 'real' strings in it

	*/
	std::vector<std::string> tokens;
	std::string delimiters = "###XSWITCH###";
	 // Skip delimiters at beginning.
       std:: string::size_type lastPos = str.find_first_not_of(delimiters, 0);
        // Find first "non-delimiter".
        std::string::size_type pos     = str.find_first_of(delimiters, lastPos);

        while (std::string::npos != pos || std::string::npos != lastPos)
       {
        // Found a token, add it to the vector.
        tokens.push_back(str.substr(lastPos, pos - lastPos));
        // Skip delimiters.  Note the "not_of"
        lastPos = str.find_first_not_of(delimiters, pos);
        // Find next "non-delimiter"
        pos = str.find_first_of(delimiters, lastPos);
       }
	return tokens;
}


```

---

### Post by andrewc6l on 2009-01-09
I think your tokenizer is using any character in ###XSWITCH### as a delimiter character. (That is, it's breaking at any of #,X,S,W,I,T,C or H.) Since the string "TCP" has two such delimiters, it's splitting them there.

---

### Post by dempl_dempl on 2009-01-09
andrewc6l is right. 

Although I can only recommend you the solution I use every day. 

The easiest thing for you would be to use boost::string libraries.
[http://www.boost.org/](http://www.boost.org/)   .   

 Among other things, I use **boost** for all kind of string processing , including parsing, and I can only tell you that the code you need would be written in only 2-3 lines using boost. 

If you haven't used boost libraries before, you should get acquainted with them. 

Cheers!

---

### Post by mdurham on 2009-01-09
what is deserialiseRPCString(std::string str) returning? Does it still exist when the function has returned to the caller?
Cheers, Mike

---

### Post by bluedalmatian on 2009-01-12
Thanks Ill have a look at Boost.

---

### Post by dwhitney67 on 2009-01-12
Learning to use Boost is a worthwhile venture.  I definitely recommend it.

However, if you want to stick to learning the nuts-n-bolts of how to do things yourself, consider the following:
[php]
std::vector<std::string> deserialiseRPCString(const std::string& str)
{
  std::vector<std::string> vecstr;

  const std::string delim("###SWITCH###");

  size_t beg = 0;

  while (beg != std::string::npos)
  {
    size_t end = str.find(delim, beg);

    if (end != std::string::npos)
    {
      vecstr.push_back(str.substr(beg, end - beg));

      beg = end + delim.size();
    }
    else
      break;
  }

  return vecstr;
}
[/php]

---

