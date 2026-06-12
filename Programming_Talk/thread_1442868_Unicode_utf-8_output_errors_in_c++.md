---
title: "Unicode utf-8 output errors in c++"
date: 2010-03-30
forum: Programming Talk
---

### Post by ep_ on 2010-03-30
First off, I don't really care about other environments, only my own.  Unicode has a set of domino tile characters and I'd like to use em to test the core of a game I'm developing.  This saves me from messing with a GUI for the time being.

I'm having some troubles displaying things correctly in a linux-x console (konsole actually).  The user environment here is "en_US.UTF-8".  Also, I am able to output a utf-8 demonstation file (cat Utf-8-demo.txt) and get nice results.

I use a library to encode the code points to but I get unexpected double chars displaying em. Note, utf-8 should be backwards compatible with ASCII.  I can sum up the problem with a code snippet:

    
```

    // Domino tile code point U-1F030, encoded utf8

    const unsigned char uc[4] = { 0xf0, 0x9f, 0x80, 0xB0 };
    std::string tile(uc, uc + 4);

    std::cout << uc[0] << uc[1]
              << uc[2] << uc[3]
              << 'a' << 'b' << std::endl;

    std::cout << tile << 'a' << 'b' << std::endl;

    // Output ERROR (double chars) for either of the above:  [domino]aab

```

What am I doing wrong?

---

### Post by LKjell on 2010-03-30
Not quite sure in c++ but in c you need to set you LC_CTYPE (Code file) to utf8 by using the setlocale() function. You also need to check your locale is set right.

---

### Post by ep_ on 2010-03-31
User locale en_US.UTF-8
std::cout<<"User locale "<< std::locale("").name()<< std::endl;

Just to clarify, piping the output to file (Ubuntu 9.10) gives:

 F0 9F 80 B0 61 62 0A  F0 9F 80 B0 61 62 0A

No repeats there. I believe this is valid Utf-8. I opened the file in kate  and it displays each domino followed by "aa" (should be "ab").  Still unexpected, but different from what konsole does eg "aab"

Also strange (to me) is that konsole will display a wild and crazy utf-8 demo file  flawlessly but not a domino followed by two simple characters (it screws up the simple characters) Perhaps I've stumbled upon a better utf-8 test file?

---

### Post by LKjell on 2010-03-31
I get no error when running the domino sign but I use a space between letters since the domino sign is actually taking two spaces.

```
#include <iostream>

using namespace std;

int main() {
//	char *locale = setlocale(LC_CTYPE,"");
//
//	if (locale == NULL) {
//		cout << "Please set the locale" << endl;
//		return 0;
//	}

	const unsigned char uc[4] = {0xf0, 0x9f, 0x80, 0xb0};
	string tile(uc, uc + 4);

	cout << uc[0] << uc[1] << uc[2] << uc[3]
		<< " "
		<< "a" << "b" << endl;

	cout << tile << " ab" << endl;
}

```

---

### Post by ep_ on 2010-03-31
Thanks for testing LKjell.  Just curious, do you get mangled output if leave the space off, as per my original demonstration?   Also, it displays correctly for me sometimes, for instance if I do: 

cout << line "  ab" << endl; // two spaces before ab

I was just trying to supply something simple, demonstrating the problem.  In my actual program I get occasional double chars throughout on arrows and other types of chars.  Maybe, between flushes, I can do some padding so total (non dbl chars) modulo 2 is always zero. This would be a temporary fix.

I was just wondering what's going on.  Whether this is a bug in konsole and kate (fixed width fonts?) or whether once you use a "double-wide char" (if that's the term) in utf-8, you're expected to use double-wide throughout.  Which seems crazy but I'm just now beefing up on unicode.

---

### Post by LKjell on 2010-03-31
Well those domino signs are taking two space per sign on my terminal. So when you have a horizontal domino sign you need to have a space otherwise the next character will be under the domino sign.

You also need to check that the konsole output is really set to utf8 and not other. Some character encoding are super seeded of other. Give us the test file and a screenshot too.

---

### Post by ep_ on 2010-04-01
I've now come to the conclusion, this is just a simply a matter of Unicode functionality on a given terminal emulator or whatever. Certainly not a c++ issue.  Here's a quote from Markus Kuhn's excellent [UTF-8 and Unicode FAQ]("http://www.cl.cam.ac.uk/~mgk25/unicode.html"). 
> 
Full Unicode functionality with all bells and whistles (e.g. high-quality typesetting of the Arabic and Indic scripts) can only be expected from sophisticated multi-lingual word-processing packages. What Linux supports today on a broad base is far simpler and mainly aimed at replacing the old 8- and 16-bit character sets. Linux terminal emulators and command line tools usually only support a Level 1 implementation of ISO 10646-1 (no combining characters), and only scripts such as Latin, Greek, Cyrillic, Armenian, Georgian, CJK, and many scientific symbols are supported that need no further processing support. At this level, UCS support is very comparable to ISO 8859 support and the only significant difference is that we have now thousands of different characters available, that characters can be represented by multibyte sequences, and that ideographic Chinese/Japanese/Korean characters require two terminal character positions (double-width).


By the way, the bones display nicely in Open Office.  For the curious, here's the source and screen shots you requested.  Also encl is the Open Office screen shot.

```
#include <string>
#include <clocale>
#include <iostream>

int main()
{
    char *locale = setlocale(LC_CTYPE,"");

    if (locale == NULL)
    {
        std::cout << "Please set the locale" << std::endl;
        return 0;
    }
    else
        std::cout << "The user locale is " << locale << std::endl;
        
    // UTF-8 encodes each character (code point) in 1 to 4 octets,
    // with the single octet encoding used only for the
    // 128 US-ASCII characters.  
    const unsigned char octetsTileLeft[4]   = {0xF0, 0x9F, 0x81, 0x80};
    const unsigned char octetsTileMid[4]    = {0xF0, 0x9F, 0x81, 0xAB};
    const unsigned char octetsTileRight[4]  = {0xF0, 0x9F, 0x80, 0xBB};
    
    std::string tile1(octetsTileLeft, octetsTileLeft + 4);
    std::string tile2(octetsTileMid, octetsTileMid + 4);
    std::string tile3(octetsTileRight, octetsTileRight + 4);
    std::string twoCharacters("ab");
    
    // mangled output on Konsole (Ubuntu 9.10) (Konsole 2.3.2) (Kde 4.3.2)
    std::cout << tile1 << twoCharacters << std::endl;
    std::cout << tile1 << tile2 << tile3 << twoCharacters << std::endl;
    
    return 0;
  
}    

```

---

### Post by LKjell on 2010-04-01
It appears that there are some problems with konsole when it comes to render domino stuff. The same with gnome-terminal.

---

