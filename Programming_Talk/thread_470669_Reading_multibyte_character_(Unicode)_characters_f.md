---
title: "Reading multibyte character (Unicode) characters from a file."
date: 2007-06-11
forum: Programming Talk
---

### Post by moma on 2007-06-11
Hello all,

I have programmed (in C++) an error-tolerant XML parser. Now I want to give this parser ability to handle (multibyte) [unicode]("http://www.unicode.org/") characters in XML-files.

[ The XML standard says that XML files can contain unicode characters such as UTF-8, -16 and -32 ]

I have started to experiment with std::wifstream class and wchar_t and wstring data types. But this wchar_t, utf-? and wstring stuff is not so easy to understand.

I started to create a simple example that reads text from a unicode file.   It's not ready yet. I need your help.  

```

#include <iostream>
#include <fstream>
#include <string>
#include <locale>

using namespace std;

int main()
{
    std::wifstream ffile;
    wchar_t wbuf[128];

    char *s;
    unsigned short utf_mode = 0;

    std::string fileName = "test1.txt";

    if  (((s = getenv("LC_ALL"))   && *s) ||
        ((s = getenv("LC_CTYPE")) && *s) ||
        ((s = getenv("LANG"))     && *s))
    {
            if (strstr(s, "UTF-8"))
                utf_mode = 8;
            else if (strstr(s, "UTF-16"))
                utf_mode = 16;
            else if (strstr(s, "UTF-32"))
                utf_mode = 32;
    }

    wcout << L"UTF mode is " << utf_mode << endl;

    // if (!setlocale(LC_CTYPE, ""))
    // {
    //    wcout << L"Cannot set locale  !" << endl;
    // }


    ffile.open(fileName.c_str() , wifstream::in);

    if (!ffile.is_open()) {
        wcerr << L"Cannot open file" << endl;
        return 0;
    }


    while (!ffile.eof())
    {
        // how to read any UTF (8,16,32) characters from the file  ???

    }
    // code.read(&wbuf[0], sizeof(wchar_t) * 100);
    // code.getline(wbuf, sizeof(wchar_t) * 100);




    ffile.close();

    return 0;

}
```


**Questions:**

How do I know what encoding mode the file has?   Do I have to test the BOM code at the beginning of the file . See:  [http://www.i18nguy.com/unicode/c-unicode.html](http://www.i18nguy.com/unicode/c-unicode.html)

Can I assume that wifstream and its read() function call does detect unicode characters automatically?

This is a new subject and I cannot even ask all the relevant questions. [COLOR="Red"]So please, 
come up with tips, advice and links.  Give me ANYTHING,  EXAMPLES etc.[/COLOR].

Here is a good UTF-8 example with text from various languages
[http://www.futuredesktop.org/tmp/utf8-test1.txt](http://www.futuredesktop.org/tmp/utf8-test1.txt)
Picture: [http://www.futuredesktop.org/tmp/utf8-test1.png](http://www.futuredesktop.org/tmp/utf8-test1.png) 

Of course,  if you save it (eg. in the gedit editor) as UTF-32 file it will not print correctly in a terminal window.
[http://www.futuredesktop.org/tmp/utf32-test1.txt](http://www.futuredesktop.org/tmp/utf32-test1.txt)

My current settings are:

$ set | grep LANG
LANG=en_US.UTF-8
LANGUAGE=en_US:en
---------------------

I do not want to use any GUI or other additional libraries such as Pango / GTK2, QT or WxWidgets.

---

### Post by bboozzoo on 2007-06-11
neither read nor wifstream detects anything. you may want to try browsing through libxml code for handling utf characters

---

