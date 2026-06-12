---
title: "Basic substring question..."
date: 2011-03-25
forum: Programming Talk
---

### Post by jason102 on 2011-03-25
Hi all,

I've got a basic question that I'm sure can be answered in two seconds (hopefully!) - so in the code below:

```
string before, after, temp;
    
    for (unsigned int i = 0; i < strUTF8encodedString.size(); i++) {
		temp = strUTF8encodedString.substr(i + 1);
		if (temp.find("%") == string::npos)
			break;
		if (strUTF8encodedString[i] == '%') {
			before = strUTF8encodedString.substr(0, i + 1);
			
			after = strUTF8encodedString.substr(temp.find_first_of("%") - 1);
			
			//strUTF8encodedString = before + after;
			//cout << strUTF8encodedString << endl;
		}
		cout << temp << endl;
		//strUTF8encodedString = strUTF8encodedString.substr(
	}
```

I'm getting the following error:
"terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted"

I want strUTF8encodedString = before + after, but my IDE hangs whenever I compile and run it. 

I want to get rid of the extra F's in the following string:
%FFFFFFE6%FFFFFF88%FFFFFF91%FFFFFFE6%FFFFFF98%FFFFFFAF%FFFFFFE5%FFFFFFAD%FFFFFFA6%FFFFFFE7%FFFFFF94%FFFFFF9F%FFFFFFE3%FFFFFF80%FFFFFF82

so it instead is
%E6%88%91%E6%98%AF%E5%AD%A6%E7%94%9F%E3%80%82

Any ideas?

---

### Post by johnl on 2011-03-25
You can read the hexadecimal integers from the string (using a stringstream) and mask off the high bits;  something like:

```

#include <iostream>
#include <string>
#include <sstream>

int main() {
    // ...
    string input = "%FFFFFFE6%FFFFFF88%FFFFFF91%FFFFFFE6%FFFFFF98%FFFFFFAF%FFFFFFE5%FFFFFFAD%FFFFFFA6%FFFFFFE7%FFFFFF94%FFFFFF9F%FFFFFFE3%FFFFFF80%FFFFFF82";

    stringstream ss(input);

    unsigned int value = 0;
    char c;

    while(!ss.eof()) {
        ss >> c;
        if (c == '%') {
            // read the integer
            ss >> std::hex >> value;
            // print it out, allowing only the bottom byte
            cout << std::hex << (value & 0x000000FF) << endl;
        } else {
            cerr << "bad character: " << c << endl;
            break;
        }
    }
    return 0;
}

```

---

### Post by jason102 on 2011-03-25
Wow, that's something I haven't done before! Does this work for cases where the characters I want to remove are other than F's? Essentially, to get the properly formatted UTF8 string, I think it needs to be a % sign followed by 2 characters (letters or numbers), right? I modified the input string by replacing one of the F's with another letter and the code returned different output, which could be problematic.  

Could this code be modified to fix this issue? 

Thanks for helping, John!

---

### Post by johnl on 2011-03-25
> **jason102 said:**
> Wow, that's something I haven't done before! Does this work for cases where the characters I want to remove are other than F's? Essentially, to get the properly formatted UTF8 string, I think it needs to be a % sign followed by 2 characters (letters or numbers), right? I modified the input string by replacing one of the F's with another letter and the code returned different output, which could be problematic.  

Could this code be modified to fix this issue? 

Thanks for helping, John!

```

(value & 0x000000FF)

```

Discards the first three bytes of the number, preserving only the last byte; it doesn't matter what the values of the first three bytes are; e.g.

```

0x12345678 & 
0x000000FF
---------- =
0x00000078 

0xFFFFFF78 &  
0x000000FF
---------- = 
0x00000078 

```
(The leading zeros above are just to show how exactly this works; they aren't significant)

Does that answer what you were asking?  I wasn't sure I understood completely :)

---

### Post by jason102 on 2011-03-25
Hi John,

The reason why I was using substrings was because I can't be sure if the leading characters before the 2 important utf8 ones (in this case the 6 F's) will always be F's and that there will always be 6 of them in each "batch", if you will.

For example, if the input string is
"%FFFuFFE4%FFFFFB8%FFFFFFBA%FFFFFFE4%FFFFFFBB%FFFFFF80%FFFFFFE4%FFFFFFB9%FFFFFF88"

(notice the lowercase letter 'u' in the first batch), your code outputs "%ff", which is obviously wrong because of how short it is. If the 'u' is replaced with an 'F', your code works.

The correct output should be "%e4%b8%ba%e4%bb%80%e4%b9%88", regardless of whether or not the characters before the important 2 utf8 digits and after the % sign are F's or u's. 

Does that make sense?

EDIT: Oh, and I just realized that your code said that the 'u' was a "bad character". But that's part of the point - what if I get "bad characters" in the input string?

---

### Post by johnl on 2011-03-26
> **jason102 said:**
> Hi John,

The reason why I was using substrings was because I can't be sure if the leading characters before the 2 important utf8 ones (in this case the 6 F's) will always be F's and that there will always be 6 of them in each "batch", if you will.

For example, if the input string is
"%FFFuFFE4%FFFFFB8%FFFFFFBA%FFFFFFE4%FFFFFFBB%FFFFFF80%FFFFFFE4%FFFFFFB9%FFFFFF88"

(notice the lowercase letter 'u' in the first batch), your code outputs "%ff", which is obviously wrong because of how short it is. If the 'u' is replaced with an 'F', your code works.

The correct output should be "%e4%b8%ba%e4%bb%80%e4%b9%88", regardless of whether or not the characters before the important 2 utf8 digits and after the % sign are F's or u's. 

Does that make sense?

EDIT: Oh, and I just realized that your code said that the 'u' was a "bad character". But that's part of the point - what if I get "bad characters" in the input string?

The reason it fails when you change the F to a 'u' is because u is not a valid hexadecimal digit (0-9, a-f).   What happens is that the code I posted:

```

1. read '%'
2. read in hex integer; reads 'FFF' (next character is 'u' which cannot be part of the number, so stop)
3. move to next character 'u' (when '%' was expected)

```

If you replace your 'u' with any valid hex digit it should work.


Since what you are trying to decode is a hexadecimal number, I doubt that you will see a 'u' in any of the values :)  If you have, maybe I misunderstood the data you are trying to decode.

---

### Post by jason102 on 2011-03-26
Oh, ok, I see what you're saying. So I guess at this point I might provide a little more information on what I'm doing. I need to get the UTF8 encoded strings for Chinese characters, and I'm shooting the characters through the following code which is producing the UTF8 input string which has all those hexadecimal F's:
```

#define ToUnicode(x) L ## x

char* RADIX_itoa(int value, char* str, int radix)
{
    const static char dig[] = "0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    int n = 0, neg = 0;
    unsigned int v;
    char* p, *q;
    char c;

    if (radix == 10 && value < 0)
    {
        value = -value;
        neg = 1;
    }

    v = value;
    do
    {
        str[n++] = dig[v%radix];
        v /= radix;
    } while (v);

    if (neg)
        str[n++] = '-';

    str[n] = '\0';

    for (p = str, q = p + (n-1); p < q; ++p, --q)
        c = *p, *p = *q, *q = c;

    return str;
}

string UTF8encode(const wchar_t* mytext)
{
    // endian-independant
    char chrarry_HexNumber[10] ;
    string strUTF8encodedString = "" ;
    wchar_t* newtext ;
    int intCharacterBinaryValue ;

    for (newtext = (wchar_t*) mytext ; *newtext!= 0; newtext++)
    {
        intCharacterBinaryValue = (int) *newtext ;
        if ( (ToUnicode('a') <= intCharacterBinaryValue && intCharacterBinaryValue <= ToUnicode('z') ) \
                || (ToUnicode('A') <= intCharacterBinaryValue && intCharacterBinaryValue <= ToUnicode('Z')) \
                || (ToUnicode('0') <= intCharacterBinaryValue && intCharacterBinaryValue <= ToUnicode('9')) )
        {
            strUTF8encodedString += (char) intCharacterBinaryValue ;
        }
        else
        {

            int intUTFbyte1 = 0 ;
            int intUTFbyte2 = 0 ;
            int intUTFbyte3 = 0 ;
            int intUTFbyte4 = 0 ;
            int intUTFbyte5 = 0 ;
            int intUTFbyte6 = 0 ;

            if (intCharacterBinaryValue < 128)
                intUTFbyte1 = intCharacterBinaryValue ;

            if (intCharacterBinaryValue >127 && intCharacterBinaryValue < 2048)
            {
                intUTFbyte1 = 192 + (intCharacterBinaryValue / 64);
                intUTFbyte2 = 128 + (intCharacterBinaryValue % 64);
            }

            if ( intCharacterBinaryValue > 2047 && intCharacterBinaryValue < 65536)
            {
                intUTFbyte1 = 224 + (intCharacterBinaryValue / 4096) ;
                intUTFbyte2 = 128 + ((intCharacterBinaryValue / 64) % 64) ;
                intUTFbyte3 = 128 + (intCharacterBinaryValue % 64) ;
            }

            if ( intCharacterBinaryValue > 65535 && intCharacterBinaryValue < 2097152)
            {
                intUTFbyte1 = 240 + (intCharacterBinaryValue / 262144) ;
                intUTFbyte2 = 128 + ((intCharacterBinaryValue / 4096) % 64) ;
                intUTFbyte3 = 128 + ((intCharacterBinaryValue / 64) % 64) ;
                intUTFbyte4 = 128 + (intCharacterBinaryValue % 64) ;
            }

            if ( intCharacterBinaryValue > 2097151 && intCharacterBinaryValue < 67108864)
            {
                intUTFbyte1 = 248 + (intCharacterBinaryValue / 16777216) ;
                intUTFbyte2 = 128 + ((intCharacterBinaryValue / 262144) % 64) ;
                intUTFbyte3 = 128 + ((intCharacterBinaryValue / 4096) % 64) ;
                intUTFbyte4 = 128 + ((intCharacterBinaryValue / 64) % 64) ;
                intUTFbyte5 = 128 + (intCharacterBinaryValue / 64) ;
            }

            if ( intCharacterBinaryValue > 67108863 && intCharacterBinaryValue <= 2147483647)
            {
                intUTFbyte1 = 252 + (intCharacterBinaryValue / 1073741824) ;
                intUTFbyte2 = 128 + ((intCharacterBinaryValue / 16777216) % 64) ;
                intUTFbyte3 = 128 + ((intCharacterBinaryValue / 262144) % 64) ;
                intUTFbyte4 = 128 + ((intCharacterBinaryValue / 4096) % 64) ;
                intUTFbyte5 = 128 + ((intCharacterBinaryValue / 64) % 64) ;
                intUTFbyte6 = 128 + (intCharacterBinaryValue % 64) ;
            }




            if (intUTFbyte1)
            {
                strUTF8encodedString += "%" ;
                strUTF8encodedString += RADIX_itoa(intUTFbyte1, chrarry_HexNumber, 16);
            }
            if (intUTFbyte2)
            {
                strUTF8encodedString += "%" ;
                strUTF8encodedString += RADIX_itoa(intUTFbyte2, chrarry_HexNumber, 16);
            }
            if (intUTFbyte3)
            {
                strUTF8encodedString += "%" ;
                strUTF8encodedString += RADIX_itoa(intUTFbyte3, chrarry_HexNumber, 16);
            }

            if (intUTFbyte4)
            {
                strUTF8encodedString += "%" ;
                strUTF8encodedString += RADIX_itoa(intUTFbyte4, chrarry_HexNumber, 16);
            }

            if (intUTFbyte5)
            {
                strUTF8encodedString += "%" ;
                strUTF8encodedString += RADIX_itoa(intUTFbyte5, chrarry_HexNumber, 16);
            }

            if (intUTFbyte6)
            {
                strUTF8encodedString += "%" ;
                strUTF8encodedString += RADIX_itoa(intUTFbyte6, chrarry_HexNumber, 16);
            }
        }
    }
    
    stringstream ss(strUTF8encodedString);
    string final;
    unsigned int value = 0;
    char c;
    
    while(!ss.eof()) {
        ss >> c;
        if (c == '%') {
            // read the integer
            ss >> hex >> value;
            
            // add the hex values and 
            ostringstream oss;
            oss << "%" << hex << (value & 0x000000FF);
            final += oss.str();
        } else {
            cerr << "bad character: " << c << endl;
            break;
        }
    }

    return final;
}
```

I got this code from another ubuntuforums thread:
[http://ubuntuforums.org/showpost.php?p=6692126&postcount=5](http://ubuntuforums.org/showpost.php?p=6692126&postcount=5)

Think any Chinese characters I send through the UTF8encode function will produce values other than valid hexadecimal digits? I'm going to take a guess and say no, but in case this code wasn't designed to process the Chinese character set, it's nice to have someone else's take on it...

---

