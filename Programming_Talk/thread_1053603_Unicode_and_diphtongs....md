---
title: "Unicode and diphtongs..."
date: 2009-01-28
forum: Programming Talk
---

### Post by WitchCraft on 2009-01-28
Hi, question:

I use the following functions to convert ASCII to unicode and vice-versa.
```

std::string Unicode2ASCII( const std::wstring& wstrStringToConvert )
{
    size_t sze_StringLength = wstrStringToConvert.length()  ;

    if(0 == sze_StringLength)
        return "" ;

    char* chrarry_Buffer = new char[ sze_StringLength + 1 ] ;
    wcstombs( chrarry_Buffer, wstrStringToConvert.c_str(), sze_StringLength ) ; // Unicode2ASCII, const wchar_t* C-String 2 mulibyte C-String
    chrarry_Buffer[sze_StringLength] = '\0'     ;
    std::string strASCIIstring = chrarry_Buffer ;
    delete chrarry_Buffer ;

    return strASCIIstring ;
}


std::wstring ASCII2Unicode( const std::string& strStringToConvert )
{
    size_t sze_StringLength = strStringToConvert.length() ;

    if(0 == sze_StringLength)
        return L"" ;

    wchar_t* wchrarry_Buffer = new wchar_t[ sze_StringLength + 1 ] ;
    mbstowcs( wchrarry_Buffer, strStringToConvert.c_str(), sze_StringLength ) ; // Unicode2ASCII, const. mulibyte C-String 2 wchar_t* C-String
    wchrarry_Buffer[sze_StringLength] = L'\0'    ;
    std::wstring wstrUnicodeString = wchrarry_Buffer ;
    delete wchrarry_Buffer   ;

    return wstrUnicodeString ;
}

```

Now it works when I only use english alphabet characters...
But when the ASCII string contains some non-english characters, like the german umlauts (ä,ö,ü) then is stops at that characters.
```

std::string strTextToTranslate = "Bla bla bla ö ä ü blablabla." ;
std::wstring wstrTextToTranslate = ASCII2Unicode( strTextToTranslate ) ;
//std::wstring wstrTextToTranslate = L"Bla bla bla ö ä ü blablabla." ;

```

e.g. the above code results in wstrTextToTranslate = L"Bla bla bla "
cutting exactly where the umlauts begin.

Is there any way to fix that?
using the L"My text here" is no solution, because the input text comes from the user...

But interestingly enough L"My text äöü here" results in a correct string, so it should be possible, or not?

---

### Post by wmcbrine on 2009-01-28
Where to begin... There really are no non-English ASCII characters. ASCII covers only 0-127. Beyond that, you're looking at a variety of character sets. Which set you have to deal with depends on your OS and the language(s) it's configured for.

Ubuntu uses UTF-8, which is convenient, because it's the same everywhere, and it's really just another form of Unicode. But it can also be inconvenient, because characters have variable-length encodings.

Windows uses it own 8-bit character sets, which are minor variations of the standard ISO sets. Except when it uses old-style IBM code pages, or UTF-16. It's pretty much always inconvenient.

You're on the right track with mbstowcs() and wcstombs(). They already understand all of the above issues. But for these functions to work correctly, you first have to call setlocale().

---

