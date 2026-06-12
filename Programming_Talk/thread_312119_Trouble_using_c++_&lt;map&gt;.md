---
title: "Trouble using c++ &lt;map&gt;"
date: 2006-12-03
forum: Programming Talk
---

### Post by mkppk on 2006-12-03
I'm a Python programmer learning to write an extension in C++. I've got a working extension, but it doesn't use any special C++ modules yet.. Tried to add a basic Map variable and started running into compilation errors. So,now I just trying to get a very basic C++ program that uses Map.. 

*[SIZE="1"](I do not know a whole lot of C++, but want to use a data type similar to a Python dictionary. After some research I believe maps are the way to go, please correct me if I am wrong.)[/SIZE]*

Any ideas what I'm doing wrong or what is not setup correctly on my system (Ubuntu 6.06 LTS on a G3 PPC powerbook)?

Here is a full example of what I'm trying to do, this is /home/mkp/pytest/test.cpp:

```
  #include <string>
 #include <map>
 #include <iostream>
   

main() { 

	map<string,int> count; string word;

	while (cin >> word) count[word]++;

		cout << count << endl; 
}  
```

Here is the compilation error:

```
mkp@mac:~/pytest$ gcc test.cpp
test.cpp: In function &#8216;int main()&#8217;:
test.cpp:8: error: &#8216;map&#8217; was not declared in this scope
test.cpp:8: error: &#8216;string&#8217; was not declared in this scope
test.cpp:8: error: expected primary-expression before &#8216;int&#8217;
test.cpp:8: error: expected `;' before &#8216;int&#8217;
test.cpp:8: error: expected `;' before &#8216;word&#8217;
test.cpp:10: error: &#8216;cin&#8217; was not declared in this scope
test.cpp:10: error: &#8216;word&#8217; was not declared in this scope
test.cpp:10: error: &#8216;count&#8217; was not declared in this scope
test.cpp:12: error: &#8216;cout&#8217; was not declared in this scope
test.cpp:12: error: &#8216;count&#8217; was not declared in this scope
test.cpp:12: error: &#8216;endl&#8217; was not declared in this scope
mkp@mac:~/pytest$


```

---

### Post by duff on 2006-12-03
1) gcc is a C compiler, use g++ instead

2) just like you need to prefix modulename.attribute in Python, you need "std::" in front of map, string, cin, cout, and endl.

3) you can't send a map to cout like that.

---

### Post by Angry on 2006-12-04
> **duff said:**
> 
2) just like you need to prefix modulename.attribute in Python, you need "std::" in front of map, string, cin, cout, and endl.


Alternatively, you could type: 

```
using namespace std;
```

after your header declarations.  Saves on typing...

---

