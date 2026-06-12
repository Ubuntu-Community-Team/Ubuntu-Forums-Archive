---
title: "Compiling errors Overloading operator&gt;&gt; in c++"
date: 2008-03-23
forum: Programming Talk
---

### Post by supernick on 2008-03-23
I just started learning c++ and i'm currently stuck on the chapter on overloading functions. I'm having compiling errors when I compile this program, i'm using ubuntu os with g++ compiler. I removed the use of some variables to reduce the error messages.

> 
error:
overloading.cc: In function &#8216;std::istream& operator>>(std::istream&, const PhoneNumber&)&#8217;:
overloading.cc:32: error: no match for &#8216;operator>>&#8217; in &#8216;std::operator>> [with _CharT = char, _Traits = std::char_traits<char>](((std::basic_istream<char, std::char_traits<char> >&)((std::istream*)input)), std::setw(4)) >> num->PhoneNumber::areaCode&#8217; ............etc


```

#include <iostream>

using std::cout;
using std::cin;
using std::endl;
using std::ostream;
using std::istream;

#include <iomanip>

using std::setw;


class PhoneNumber{
public:
	friend ostream &operator<<(ostream&, const PhoneNumber &);
	friend istream &operator>>(istream&, const PhoneNumber &);
	
private:
	char areaCode[ 4];
	char exchange[ 4];
	char line[ 5];
};

ostream &operator<<(ostream &output, const PhoneNumber &num){
	output << "(" << num.areaCode << ") ";
	return output;
}

istream &operator>>(istream &input, const PhoneNumber &num){
	input >> setw(4) >>num.areaCode;
	return input;
}

int main(){
	PhoneNumber phone;
	
	cout << " Enter phone number ";
	
	cin >> phone;
	
	cout << phone << endl;
	return 0;
}

```

---

### Post by Jucato on 2008-03-23
```
friend istream &operator>>(istream&, const PhoneNumber &);
```

Why is the PhoneNumber parameter a const? >> (stream insertion) needs to be able to modify the variable, doesn't it? That's probably the source of the error.

---

### Post by supernick on 2008-03-23
oh geez! how careless! thanks for pointing that out.

---

