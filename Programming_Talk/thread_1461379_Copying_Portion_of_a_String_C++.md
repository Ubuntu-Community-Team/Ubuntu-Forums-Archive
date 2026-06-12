---
title: "Copying Portion of a String C++"
date: 2010-04-24
forum: Programming Talk
---

### Post by StunnerAlpha on 2010-04-24
Ey guys, yes it is me again. Hopefully with a not-so-stupid question this time.

I have a string like so:
```

"     hello world! "

```
and I wish to remove ONLY the '"' characters, while leaving the spaces intact.
After some googling this is what I ended up concocting:
```

std::string evaluate::cleanStr(std::string rawStr){
	std::string cleanStr;
	cleanStr.assign(rawStr);
	std::remove(cleanStr.begin(), cleanStr.end(), '"');
	return cleanStr;
}//cleanStr()

```
And the output:
```

   hello world!  "

```
It appears that the remove is not removing the last '"' character. How do I get around this? Thanks in advance!

---

### Post by dwhitney67 on 2010-04-24
An alternate approach:
```

#include <string>
#include <iostream>

std::string removeChar(const std::string& str, const char ch)
{
   std::string mod(str);

   size_t pos = std::string::npos;

   while ((pos = mod.find(ch)) != std::string::npos)
   {
      mod.erase(pos, 1);
   }

   return mod;
}

int main()
{
   const std::string orig("\"....Hello World!....\"");

   const std::string mod = removeChar(orig, '\"');

   std::cout << "orig str = " << orig << std::endl;
   std::cout << "mod str  = " << mod  << std::endl;
}

```

Or easier yet... I should have thought of this in the first place:
```

#include <string>
#include <algorithm>
#include <iostream>

std::string removeChar(const std::string& str, const char ch)
{
   std::string mod(str);

   mod.assign(mod.begin(), std::remove(mod.begin(), mod.end(), ch));

   return mod;
}

int main()
{
   const std::string orig("\"....Hello World!\"....\"\"");

   const std::string mod = removeChar(orig, '\"');

   std::cout << "orig str = " << orig << std::endl;
   std::cout << "mod str  = " << mod  << std::endl;
}

```

---

### Post by Some Penguin on 2010-04-24
> **StunnerAlpha said:**
> Ey guys, yes it is me again. Hopefully with a not-so-stupid question this time.

It appears that the remove is not removing the last '"' character. How do I get around this? Thanks in advance!

[http://www.dreamincode.net/forums/topic/32349-stl-remove-algorithm-c/](http://www.dreamincode.net/forums/topic/32349-stl-remove-algorithm-c/)

Read it carefully.

---

### Post by dribeas on 2010-04-24
The solution by dwithney67 will remove all " from the input. If you have more knowledge of how the input is (for example you know that the " are the first and last character, then you can use that information to your advantage:

```

std::string input = "\"This begins and ends in double quotes\"";
std::string clean = input.substr(1,input.size()-2); // remove first and last characters
// or:
std::string clean2( input.begin()+1, input.end()-1);

```

---

