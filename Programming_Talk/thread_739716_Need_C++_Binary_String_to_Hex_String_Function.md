---
title: "Need C++ Binary String to Hex String Function"
date: 2008-03-30
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-03-30
I looked around on the web and I can find a few ways to convert a binary string to an integer, and an integer to a hex string.  However, this involves an unnecessary step and also limits my result to being smaller than the size that an integer can represent.

I want to convert a binary string to a hexadecimal string directly without needing to go through an integer or long.  I could write my own function to do this, but I figured that one might already exist, perhaps optimized.  Anyone know of one?

---

### Post by SNYP40A1 on 2008-03-30
Humm...no takers?  Here is one possible solution "brute-force"

```

#include <string>
#include <iostream>
using namespace std;

char getHexCharacter(std::string str)
{
	if(str.compare("1111") == 0) return 'F';
	else if(str.compare("1110") == 0) return 'E';
	else if(str.compare("1101")== 0) return 'D';
	else if(str.compare("1100")== 0) return 'C';
	else if(str.compare("1011")== 0) return 'B';
	else if(str.compare("1010")== 0) return 'A';
	else if(str.compare("1001")== 0) return '9';
	else if(str.compare("1000")== 0) return '8';
	else if(str.compare("0111")== 0) return '7';
	else if(str.compare("0110")== 0) return '6';
	else if(str.compare("0101")== 0) return '5';
	else if(str.compare("0100")== 0) return '4';
	else if(str.compare("0011")== 0) return '3';
	else if(str.compare("0010")== 0) return '2';
	else if(str.compare("0001")== 0) return '1';
	else if(str.compare("0000")== 0) return '0';
	else if(str.compare("111")== 0) return '7';
	else if(str.compare("110")== 0) return '6';
	else if(str.compare("101")== 0) return '5';
	else if(str.compare("100")== 0) return '4';
	else if(str.compare("011")== 0) return '3';
	else if(str.compare("010")== 0) return '2';
	else if(str.compare("001")== 0) return '1';
	else if(str.compare("000")== 0) return '0';
	else if(str.compare("11")== 0) return '3';
	else if(str.compare("10")== 0) return '2';
	else if(str.compare("01")== 0) return '1';
	else if(str.compare("00")== 0) return '0';
	else if(str.compare("1")== 0) return '1';
	else if(str.compare("0")== 0) return '0';
}

std::string getHexRowFails(string rowresult)
{
	std::string endresult = "";
	for(int i = 0; i < rowresult.length(); i = i+4)
	{
		endresult += getHexCharacter(rowresult.substr(i,4));
	}
	return endresult;
}

int main()
{
    std::string rowresult = "101001010101";
    cout << rowresult << " in hex is " << getHexRowFails(rowresult) << endl;
    rowresult = "10100101010";
    cout << rowresult << " in hex is " << getHexRowFails(rowresult) << endl;
    rowresult = "1010010101";
    cout << rowresult << " in hex is " << getHexRowFails(rowresult) << endl;
    rowresult = "101001010";
    cout << rowresult << " in hex is " << getHexRowFails(rowresult) << endl;
    rowresult = "10100101";
    cout << rowresult << " in hex is " << getHexRowFails(rowresult) << endl;
    return 0;
}

```

And the output is:
```

101001010101 in hex is A55
10100101010 in hex is A52
1010010101 in hex is A51
101001010 in hex is A50
10100101 in hex is A5

```

Does anyone see a better solution?  Performance kind of matters so I will replace the long if-tree with a Map based implementation -- just put all the strings and their corresponding values into a map for quicker lookup.  But is there a better solution?

---

### Post by CptPicard on 2008-03-30
Well, just quickly off the top off my head, just simply put all hex characters into an array, and take your binary string in blocks of four digits, converting that block directly into the index into your array...

---

### Post by SNYP40A1 on 2008-03-30
I am not quite sure that I understand what you mean by the array implementation idea...seems like it would require an array of length 1112, with most of the indexes empty.  Here's option #2, let me know if anyone sees a better way:

```

#include <string>
#include <iostream>
#include <map>
using namespace std;

map<string, char> hexcharmap;

void initMap()
{
	hexcharmap.insert(std::pair<string, char>("1111", 'F'));
	hexcharmap.insert(std::pair<string, char>("1110", 'E'));
	hexcharmap.insert(std::pair<string, char>("1101", 'D'));
	hexcharmap.insert(std::pair<string, char>("1100", 'C'));   
	hexcharmap.insert(std::pair<string, char>("1011", 'B'));
	hexcharmap.insert(std::pair<string, char>("1010", 'A'));  
	hexcharmap.insert(std::pair<string, char>("1001", '9'));
	hexcharmap.insert(std::pair<string, char>("1000", '8'));
	hexcharmap.insert(std::pair<string, char>("0111", '7'));
	hexcharmap.insert(std::pair<string, char>("0110", '6'));
	hexcharmap.insert(std::pair<string, char>("0101", '5'));
	hexcharmap.insert(std::pair<string, char>("0100", '4'));
	hexcharmap.insert(std::pair<string, char>("0011", '3'));
	hexcharmap.insert(std::pair<string, char>("0010", '2'));
	hexcharmap.insert(std::pair<string, char>("0001", '1'));
	hexcharmap.insert(std::pair<string, char>("0000", '0'));
	hexcharmap.insert(std::pair<string, char>("111", '7'));
	hexcharmap.insert(std::pair<string, char>("110", '6'));
	hexcharmap.insert(std::pair<string, char>("101", '5'));
	hexcharmap.insert(std::pair<string, char>("100", '4'));
	hexcharmap.insert(std::pair<string, char>("011", '3'));
	hexcharmap.insert(std::pair<string, char>("010", '2'));
	hexcharmap.insert(std::pair<string, char>("001", '1'));
	hexcharmap.insert(std::pair<string, char>("000", '0'));
	hexcharmap.insert(std::pair<string, char>("11", '3'));
	hexcharmap.insert(std::pair<string, char>("10", '2'));
	hexcharmap.insert(std::pair<string, char>("01", '1'));
	hexcharmap.insert(std::pair<string, char>("00", '0'));
	hexcharmap.insert(std::pair<string, char>("1", '1'));
	hexcharmap.insert(std::pair<string, char>("0", '0'));
}

char getHexCharacter(std::string str)
{
	return hexcharmap.find(str)->second;
}

std::string getHexRowFails(string rowresult)
{
	std::string endresult = "";
	for(int i = 0; i < rowresult.length(); i = i+4)
	{
		endresult += getHexCharacter(rowresult.substr(i,4));
	}
	return endresult;
}

int main()
{
    initMap();
	std::string rowresult = "101001010101";
	cout << rowresult << " in hex is " << getHexRowFails(rowresult) << endl;
	rowresult = "10100101010";
	cout << rowresult << " in hex is " << getHexRowFails(rowresult) << endl;
	rowresult = "1010010101";
	cout << rowresult << " in hex is " << getHexRowFails(rowresult) << endl;
	rowresult = "101001010";
	cout << rowresult << " in hex is " << getHexRowFails(rowresult) << endl;
	rowresult = "10100101";
	cout << rowresult << " in hex is " << getHexRowFails(rowresult) << endl;
	return 0;
}

```

Same output as before.

---

### Post by CptPicard on 2008-03-30
It requires an array of size 16, one for each of your hex digits :)

Then you just take the first 4 binary digits of your binary string, interpret that as a number, (for example "0010" -> 2) and index into your array, getting your hex digit. Then you take the next 4 binary digits of your binary string... etc

---

### Post by heikaman on 2008-03-30
you can use a bitset like this

```
#include <iostream>
#include <string>
#include <bitset>

using namespace std;
int main(){
	string binary_str("11001111");
	bitset<8> set(binary_str);	
	cout << hex << set.to_ulong() << endl;
}
```

---

### Post by SNYP40A1 on 2008-03-30
Ah, I see.  Then all that I need is a way to convert 4-digit binary strings into integers.  Although the only way that I know how to do that involves adding powers of a*2^0+b*2^1+c*2^3, simpler to implement, but I suspect that might require more computations than using the map.  This operation will be done quite a bit.  That's why I asked if there was a C++ STL or Boost library specifically for doing this, something optimized as much as possible.

---

### Post by CptPicard on 2008-03-30
The implementation can be very quick...

```

int i = 0;

for each digit in binary string:
  if digit == 1
    i++         (alternative: i = i | 1)
  i = i << 1  (bit shift to the left)

```

Actually, it won't get much faster than this. :)

---

### Post by SNYP40A1 on 2008-03-30
How about this:

```

#include <string>
#include <iostream>
using namespace std;

const char lookuparrbin2hex[] = {'0','1','2','3','4','5','6','7','8','9','A','B','C','D','E','F'};

char convert_bin2hex(string bits)
{
	unsigned int result = 0;
	unsigned int shifter0 = 0;
	unsigned int shifter1 = 1;

	for(int n=0; n < bits.length(); n++)
	{
		result <<= 1; //shift result to the left by 1
		if(bits[n] == '1') result = (result | shifter1);
		else result = (result | shifter0);
	}
	return lookuparrbin2hex[result];
}

std::string getHexRowFails(string rowresult)
{
	std::string endresult = "";
	for(int i = 0; i < rowresult.length(); i = i+4)
	{
		endresult += convert_bin2hex(rowresult.substr(i,4));
	}
	return endresult;
}

int main()
{
	std::string rowresult = "101001010101";
	cout << rowresult << " in hex is " << getHexRowFails(rowresult) << endl;
	rowresult = "10100101010";
	cout << rowresult << " in hex is " << getHexRowFails(rowresult) << endl;
	rowresult = "1010010101";
	cout << rowresult << " in hex is " << getHexRowFails(rowresult) << endl;
	rowresult = "101001010";
	cout << rowresult << " in hex is " << getHexRowFails(rowresult) << endl;
	rowresult = "10100101";
	cout << rowresult << " in hex is " << getHexRowFails(rowresult) << endl;
	return 0;
}

```

Produces the same output as above.  I think that's about as fast as possible.

---

### Post by heikaman on 2008-03-30
> **heikaman said:**
> you can use a bitset like this

```
#include <iostream>
#include <string>
#include <bitset>

using namespace std;
int main(){
	string binary_str("11001111");
	bitset<8> set(binary_str);	
	cout << hex << set.to_ulong() << endl;
}
```

what's wrong with just using a bitset ?

---

### Post by CptPicard on 2008-03-30
If your binary digit is 0, you don't need to do an or with it... just skip straight to the shift.

@heikaman, probably nothing... actually looks like quite an elegant solution :)

---

### Post by heikaman on 2008-03-30
> **CptPicard said:**
> 
@heikaman, probably nothing... actually looks like quite an elegant solution :)

Finally thank you  :)

---

### Post by WW on 2008-03-30
> **heikaman said:**
> what's wrong with just using a bitset ?
In the first post, SNYP40A1 said
> However, this involves an unnecessary step and also limits my result to being smaller than the size that an integer can represent.
Doesn't the bitset solution also limit the number of binary digits to the number of bits in a long integer?

---

### Post by heikaman on 2008-03-31
> **WW said:**
> Doesn't the bitset solution also limit the number of binary digits to the number of bits in a long integer?

No, not at all, you can process the binary string in chunks of say 8 bits at a time.

---

### Post by slavik on 2008-03-31
mixing C code into C++ ???

```

while ((ch = getch()) != EOF) {
  printf("%0X",ch);
}
```

---

### Post by heikaman on 2008-03-31
> **slavik said:**
> 
```

while ((ch = getch()) != EOF) {
  printf("%0X",ch);
}
```

wouldn't this convert one char at a time so you'll get either a 0 or 1 or the hex value of the  ASCII  char ?

here's a simple example,  it works fine i think :)

```
#include <iostream>
#include <string>
#include <bitset>

#define SETSIZE 4

using namespace std;

void to_hex_str(string& binary);

int main(){
	string binary_str("11101111011111000011101010101101");
	to_hex_str(binary_str);	
}

void to_hex_str(string& binary){
	size_t idx=0, size=binary.size();
	
	cout << hex ;
	
	for( int i=0; i < (size/SETSIZE) ; i++, idx+=SETSIZE){
		bitset<SETSIZE> set(binary.substr(idx, idx+SETSIZE));
		cout << set.to_ulong();
	}

	cout << dec << endl;
}
```

---

### Post by slavik on 2008-03-31
No, you'll get 0 padded hex of the char (1 byte) and it will stop when there is an EOF.

---

### Post by heikaman on 2008-03-31
> **slavik said:**
> No, you'll get 0 padded hex of the char (1 byte) and it will stop when there is an EOF.

yes but each 0 or 1 in the binary string is a char (1 byte) holding the value 0 or 1 in ASCII 48 and 49, in hex 30 and 31 
that apply to parsing a string or a cstring  or using getc "which returns the char cast to int which is the same"

try to actually run the code

---

### Post by slavik on 2008-03-31
oh, I misunderstood the OP, I thought it was a string of bytes ... oops :P

---

### Post by Sporkman on 2008-03-31
...

---

### Post by SNYP40A1 on 2008-03-31
> **heikaman said:**
> Finally thank you  :)

Heikaman, your solution looks good.  But I did not pursue it because I wanted to return the hex value, not print it out.  Not sure how to return the value.  I could process the result in groups of 4 bits at a time so that ulong is sufficient for holding the result.

Everyone, thanks for all your suggestions.  On the good side, once this thread concludes, there will be an optimal way to convert binary strings into hex strings so that no one needs to reinvent the wheel as I was about to do!

---

### Post by heikaman on 2008-03-31
> **SNYP40A1 said:**
> Heikaman, your solution looks good.  But I did not pursue it because I wanted to return the hex value, not print it out.  Not sure how to return the value.  

```
#include <iostream>
#include <string>
#include <bitset>
#include <sstream>

#define SETSIZE 4

using namespace std;

void to_hex_str(string& binary, ostringstream& hex_str);

int main(){
	string binary_str("11101111011111000011101010101101");
	ostringstream hex_str;
	to_hex_str(binary_str, hex_str);	
	cout << hex_str.str()<< endl;
}

void to_hex_str(string& binary_str, ostringstream& hex_str){
	size_t idx=0, size=binary_str.size();
	
	hex_str << hex ;
	
	for( int i=0; i < (size/SETSIZE) ; i++, idx+=SETSIZE){
		bitset<SETSIZE> set(binary_str.substr(idx, idx+SETSIZE));
		hex_str << set.to_ulong();
	}

	hex_str << dec << endl;
}
output: 
ef7c3aad

```

this is sort of a high level solution, u should also check the other posts.

---

