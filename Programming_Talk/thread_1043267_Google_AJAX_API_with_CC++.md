---
title: "Google AJAX API with C/C++"
date: 2009-01-18
forum: Programming Talk
---

### Post by WitchCraft on 2009-01-18
Hi!

Question: I want to use the google translation API to translate some strings from C++.

Now, the way you do this from a website is:
[php]
<html>
<head>

<script type="text/javascript" src="http://www.google.com/jsapi">
</script>

<script type="text/javascript">

google.load("language", "1");

var antwort ;
var text = "Ich mag Linux!";

function initialize()
{
    google.language.detect(text, function(result)
    {
        if (!result.error && result.language)
        {
            google.language.translate(text, result.language, "en",
                function(result)
                {
                    if (result.translation)
                    {
                        antwort = result.translation;
            alert(antwort) ;
                    }
                }
            );
        }
    }
    );
}

google.setOnLoadCallback(initialize);

</script>
</head>

<body>
<INPUT TYPE="button" NAME="myButton" VALUE="Press This" onClick="initialize"> 
</body>

</html>
[/php]I now thought I could take the google v8 java engine, compile it, and let the java script run in there, and read the result back...

So I wrote this little program...
```

#include <v8.h>
#include <string>

//using namespace v8;

int main(int argc, char* argv[])
{

    // Create a stack-allocated handle scope.
    v8::HandleScope handle_scope;

    // Create a new context.
    v8::Persistent<v8::Context> context = v8::Context::New();

    // Enter the created context for compiling and
    // running the hello world script.&nbsp;
    v8::Context::Scope context_scope(context);

std::string strcommand1= "";

std::string strcommand2= "google.load(\"language\", \"1\");var antwort ;var text = \"Ich mag Linux!\";function initialize(){google.language.detect(text, function(result){if (!result.error && result.language){google.language.translate(text, result.language, \"en\",function(result){if (result.translation){antwort = result.translation;alert(antwort) ;}});}});}google.setOnLoadCallback(initialize);" ;

std::string strcommand= strcommand1 + strcommand2 ;


    // Create a string containing the JavaScript source code.
    //v8::Handle<v8::String> source = v8::String::New("'Hello' + ', World!'");
    v8::Handle<v8::String> source = v8::String::New(strcommand.c_str());

    // Compile the source code.
    v8::Handle<v8::Script> script = v8::Script::Compile(source);

    // Run the script to get the result.
    v8::Handle<v8::Value> result = script->Run();

    // Dispose the persistent context.
    context.Dispose();

    // Convert the result to an ASCII string and print it.
    v8::String::AsciiValue ascii(result);
    printf("%s\n", *ascii);
    return 0;
}

```g++ transl.cpp -Wall -I./include -L./lib -lv8 -lpthread -o transl

But executing it I get a:
> 
<unknown>:0: Uncaught ReferenceError: google is not defined
Segmentation fault
I think the problem is the 
```

<script type="text/javascript" src="http://www.google.com/jsapi">
</script>

```line from the html file. If I use the <> brackets, the java script engine won't compile it, and if I omit the line, the program gets the "google not found" error...

Any ideas? Anybody has experience with google's AJAX APIs?

v8:
[http://code.google.com/apis/v8/build.html](http://code.google.com/apis/v8/build.html)
svn checkout [http://v8.googlecode.com/svn/trunk/](http://v8.googlecode.com/svn/trunk/) v8-read-only

you need the scons build tools
apt-get install scons

[http://www.json.org/](http://www.json.org/)
[http://blog.insicdesigns.com/2008/10/parsing-json-string/](http://blog.insicdesigns.com/2008/10/parsing-json-string/)

---

### Post by WitchCraft on 2009-01-18
Would need something like this:

> 
If you're going to use any of the AJAX APIs, including translation,  
from C++ (or any other non-Javascript environment), it will be far  
easier to use the RESTful interface.  All you have to do is set up a  
System.Net.WebClient object.  You can then send your input and receive  
the JSON response.  To parse the JSON, you will want one of the  
parsers that's available through [http://www.json.org]("http://www.json.org/") .


---

### Post by WitchCraft on 2009-01-19
OK, got it via curl.
see below program.

Anybody knows a good curl tutorial?
I want to integrate it with statically linked libcurl, so the user doesn't need curl installed.


```

#include <iostream>
#include <cstdlib>
#include <cstring>

#if ( defined (_WIN32) || defined (_WIN64) )
    // popen in Microbosoft C++: _popen
    #define POPEN(x,y)           _popen (x, y)
    #define PCLOSE(x)            _pclose(x)
#else // LINUX / UNIX / OS X
    #define POPEN(x,y)            popen (x, y)
    #define PCLOSE(x)             pclose(x)
#endif

int main()
{
    char chrptr_GoogleResponse [0x1000];
    char chrarray_GoogleCommand[2048] ;
    /*
    #if defined (_WIN32) || defined (_WIN64)
        sprintf(chrarray_GoogleCommand, "%s -q \"%s\" -silent --batch -x %s", GDB_PATH, chrarray_Buffer, chrptr_GDBinstructionfilename) ;
    #else // LINUX / UNIX
        sprintf(chrarray_GoogleCommand, "gdb -q \"%s\" -silent --batch -x \"%s\"", chrarray_Buffer, chrptr_GDBinstructionfilename) ;
    #endif
    */
    //sprintf(chrarray_GoogleCommand, "%s", "uname -r");
    //'http://ajax.googleapis.com/ajax/services/language/translate?v=1.0&q=hallo%20welt&langpair=de%7Cen'

    strcpy(chrarray_GoogleCommand, "curl -e http://www.urbanterror.net \
           'http://ajax.googleapis.com/ajax/services/language/translate?v=1.0&q=Hallo%20englischsprachige%20Welt!&langpair=de%7Cen' 2> /dev/null") ;

    FILE* fileptrFile = POPEN(chrarray_GoogleCommand, "r") ;

    if (fileptrFile == NULL)
    {
        printf("Error on opening pipe\n.");
        exit(EXIT_FAILURE);
    }

    char chrptr_temp[200]   ;
    char* chrptr_pos1 = NULL ;
    char* chrptr_pos2 = NULL ;
    bool boNoError = true    ;

    while ( !feof (fileptrFile) )
    {
        fgets (chrptr_GoogleResponse , 0x1000 , fileptrFile) ;

        chrptr_pos1 = strstr(chrptr_GoogleResponse, "{\"translatedText\":\"") ;
        if ( chrptr_pos1 )
        {
            chrptr_pos1 = chrptr_pos1 + strlen("{\"translatedText\":\"") ;
            chrptr_pos2 = strstr(chrptr_GoogleResponse, "\"}, \"responseDetails\": null, \"responseStatus\": 200}") ;
            if ( chrptr_pos2 )
            {
                memcpy(chrptr_temp, chrptr_pos1, chrptr_pos2 - chrptr_pos1);
                memset((void*) ((unsigned long) chrptr_temp + (unsigned long) chrptr_pos2 - (unsigned long) chrptr_pos1), 0, 1);
            }
            else
                boNoError = false ;
        }
        else
            boNoError = false ;

        if (feof (fileptrFile))
            break;
    }
    PCLOSE(fileptrFile) ;

    if (boNoError)
        printf("temp: %s\n", chrptr_temp);

    return EXIT_SUCCESS ;
}

```

---

### Post by WitchCraft on 2009-01-20
Hmm, feels good when nobody can answer my questions :D:D:D

In the meantime, I've written my own Curl wrapper for C++...

I can now announce translation support for my aimbot ;-)))

If anybody is interested, I attached the files for backup purposes.

But I have a last question:

Is there any library that can parse an input text to a html-request compatible string?
That is to say replace WHITESPACES with %20, and special signs with their respective encoding.

eg. given text: "Hello World ÄÖÜ"
html-compatible string: "Hello%20World%20%C3%84%C3%96%C3%9C"

---

### Post by WitchCraft on 2009-02-07
here's how to utf8 encode in C++



```

 #define ToUnicode(x) L ## x

char* RADIX_itoa(int value, char* str, int radix);

std::string UTF8encode(const wchar_t* mytext)
{
    // endian-independant
    char chrarry_HexNumber[10] ;
    std::string strUTF8encodedString = "" ;
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
    return strUTF8encodedString;
}

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

```

---

