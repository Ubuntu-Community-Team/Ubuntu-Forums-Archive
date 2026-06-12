---
title: "[C++]Comparing Strings Using Equality Operators."
date: 2011-12-15
forum: Programming Talk
---

### Post by Carpentr on 2011-12-15
I'm reading an example and I am trying to think about how this would make sense. It's probably something simple, I just am a little confused.I'm trying to figure out if one of my strings in greater than the other using the method above. The program compiles and runs, but I don't understand the result I am getting.

```
#include <iostream>
#include <string>
using namespace std;

int main(){
    string first, second;
    
    cin >> first >> second;
    
    if(first > second)
    cout << "Correct." << endl;
    else
    cout << "Incorrect." << endl;
    
    system("Pause");
    return 0;
}

```

My input was "country" and "applesauce" respectively. 

The output is saying "Correct." but I don't understand how "country" is greater than "applesauce." I've tested it with other words as well and sometimes the shorter word is greater and sometimes the larger word is greater. How is it determined?

Thank you for reading.

---

### Post by Hetepeperfan on 2011-12-15
My modification should give you the hint.
I commented you system function since neither iostream or string should define it and try it with capital Letters.

```
#include <iostream>
#include <string>
using namespace std;

int main(){
    string first, second;
    
    cin >> first >> second;

    cout << first << endl << second << endl;

    cout << (int) first[0] << '\t'+first << endl;
    cout << (int) second[0] << '\t'+second << endl;
    
    if(first > second)
    cout << "Correct." << endl;
    else
    cout << "Incorrect." << endl;
    
    //system("Pause");
    return 0;
}
```

---

### Post by matt_symes on 2011-12-15
Hi

It does not compare the length of the string (what i think you were expecting) but the value of the characters of the  string.

c > a in string comparison.

Kind regards

---

### Post by Tony Flury on 2011-12-15
> **Carpentr said:**
> I'm reading an example and I am trying to think about how this would make sense. It's probably something simple, I just am a little confused.I'm trying to figure out if one of my strings in greater than the other using the method above. The program compiles and runs, but I don't understand the result I am getting.

```
#include <iostream>
#include <string>
using namespace std;

int main(){
    string first, second;
    
    cin >> first >> second;
    
    if(first > second)
    cout << "Correct." << endl;
    else
    cout << "Incorrect." << endl;
    
    system("Pause");
    return 0;
}

```

My input was "country" and "applesauce" respectively. 

The output is saying "Correct." but I don't understand how "country" is greater than "applesauce." I've tested it with other words as well and sometimes the shorter word is greater and sometimes the larger word is greater. How is it determined?

Thank you for reading.

The comparison operators are looking at dictionary order (or strictly speaking character set ordering) rather than string length so : 

country > applesauce when you think about the order of the words in an dictionary.

Similarly : 
cat > boat 

and in extreme
zebra > aardvark

but also : 
zebra > Zebra
since Upper case letters come before lower case in the character Sequence.

and also : 
"1" > "one" - numeric digit characters come before letters characters.
"2" > "twenty" - for the same reason.

---

### Post by muteXe on 2011-12-15
Just to add to the excellent replies, if you want to compare how long the strings are use the size() method on the strings.

---

### Post by stchman on 2011-12-15
> **Carpentr said:**
> I'm reading an example and I am trying to think about how this would make sense. It's probably something simple, I just am a little confused.I'm trying to figure out if one of my strings in greater than the other using the method above. The program compiles and runs, but I don't understand the result I am getting.

```
#include <iostream>
#include <string>
using namespace std;

int main(){
    string first, second;
    
    cin >> first >> second;
    
    if(first > second)
    cout << "Correct." << endl;
    else
    cout << "Incorrect." << endl;
    
    system("Pause");
    return 0;
}

```My input was "country" and "applesauce" respectively. 

The output is saying "Correct." but I don't understand how "country" is greater than "applesauce." I've tested it with other words as well and sometimes the shorter word is greater and sometimes the larger word is greater. How is it determined?

Thank you for reading.

Can someone define to me a String being greater than another String???

I can see if one String has a greater length than another.

---

### Post by karlson on 2011-12-15
> **stchman said:**
> Can someone define to me a String being greater than another String???

I can see if one String has a greater length than another.

If you do a character by character comparison of the strings.  Something like this:

```

for(int i = 0 ; i < max(len(str1), len(str2)) ; ++i)
{
    if(str1[i] != str2[i])
        return (str1[i] - str2[i]);
    if( str1[i] = '\0' )
        return 0;
}

```
If this function returns value < 0 then str1 < str2, if value > 0 then str1 > str2, otherwise they are equal.

---

### Post by Carpentr on 2011-12-16
Thanks a lot for the replies everyone; it is appreciated.

If you compare both strings without specifying a particular character then it will always determine the value by the first character of the string (string[0])?

---

### Post by ofnuts on 2011-12-16
> **Carpentr said:**
> Thanks a lot for the replies everyone; it is appreciated.

If you compare both strings without specifying a particular character then it will always determine the value by the first character of the string (string[0])?It runs down both strings, comparing the characters until it finds two that don't' match and then it returns the difference. Like good old strcmp() in C, which you can find written as:

```

int strcmp(const char *s1, const char *s2)
{
  int ret = 0;

  while (!(ret = *(unsigned char *) s1 - *(unsigned char *) s2) && *s2) ++s1, ++s2;

  if (ret < 0)
    ret = -1;
  else if (ret > 0)
    ret = 1 ;

  return ret;
}
```

---

### Post by karlson on 2011-12-16
> **Carpentr said:**
> Thanks a lot for the replies everyone; it is appreciated.

If you compare both strings without specifying a particular character then it will always determine the value by the first character of the string (string[0])?

Not sure I understand the question.  In C a string is an array of characters with terminating character being '\0'.  In the comparison function the comparison will start from the first character in that array which is string[0], but it may not be the first character in the original string.

---

