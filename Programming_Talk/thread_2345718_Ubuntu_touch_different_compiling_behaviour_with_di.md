---
title: "Ubuntu touch: different compiling behaviour with different GCC versions"
date: 2016-12-07
forum: Programming Talk
---

### Post by erotavlas on 2016-12-07
Hi,
I'm compiling ubuntu touch by using [URL="https://ubports.com/"]ubport project.
[/URL]I found a strange behaviour of GCC. In few words, I can successfully compile with GCC 5 or GCC 4 while I cannot compile with GCC 6.
From GCC manual: *In GCC 6 the default mode for C++ is now -std=gnu++14 instead of -std=gnu++98 while GCC 5 the default mode for C is now -std=gnu11 instead of -std=gnu89*.
I think that using c++14 causes different behaviour with the same code with respect to previous GCC versions.
I found the source of problem at least for one error during compiling with GCC 6:
```
system/core/adb/transport.c:807:9: error: this ‘if’ clause does not guard... [-Werror=misleading-indentation]  if (error_out)
```
is detected by GCC 6 thank to a new warning -Wmisleading-indentation added to -Wall option [https://gcc.gnu.org/gcc-6/porting_to.html](https://gcc.gnu.org/gcc-6/porting_to.html) while is not detected by GCC 5 or lower version.
The current source code:
```

if (error_out)
  *error_out = "insufficient permissions for device";
    continue;

```
it should be:
```

  if (error_out)
  {
    *error_out = "insufficient permissions for device";
  }
    continue;
```
with brackets for a better clearness [https://stackoverflow.com/questions/2125066/is-it-bad-practice-to-use-an-if-statement-without-brackets#2125207](https://stackoverflow.com/questions/2125066/is-it-bad-practice-to-use-an-if-statement-without-brackets#2125207)
After that I corrected this small error, another error appears related to invalid type conversion from const uint16_t* to const char16_t*:
```

frameworks/base/libs/androidfw/AssetManager.cpp: In member function ‘android::String8 android::AssetManager::getPkgName(const char*)’:
frameworks/base/libs/androidfw/AssetManager.cpp:480:63: error: invalid conversion from ‘const char16_t*’ to ‘const uint16_t* {aka const short unsigned int*}’ [-fpermissive]
             const uint16_t* str = tree.getAttributeStringValue(idx, &len);
                                   ~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~
frameworks/base/libs/androidfw/AssetManager.cpp:481:46: error: invalid conversion from ‘const uint16_t* {aka const short unsigned int*}’ to ‘const char16_t*’ [-fpermissive]
             pkgName = (str ? String8(str, len) : String8());
                                              ^
In file included from frameworks/base/include/androidfw/Asset.h:30:0,
                 from frameworks/base/libs/androidfw/AssetManager.cpp:26:
system/core/include/utils/String8.h:56:33: note:   initializing argument 1 of ‘android::String8::String8(const char16_t*, size_t)’
     explicit                    String8(const char16_t* o, size_t numChars);


```
In this case the error is related to android utils library android::String8 which uses different return type. So, I think that such problem should be not related to ubuntu touch, but to general android and CM. Is there a way to compile android or CM with GCC 6? In your opinion, have I to report such behaviour to ubport?
I search on the web about this behaviour without success.

Thank you

---

### Post by erotavlas on 2016-12-10
> **erotavlas said:**
> Hi,
I'm compiling ubuntu touch by using [URL="https://ubports.com/"]ubport project.
[/URL]I found a strange behaviour of GCC. In few words, I can successfully compile with GCC 5 or GCC 4 while I cannot compile with GCC 6.
From GCC manual: *In GCC 6 the default mode for C++ is now -std=gnu++14 instead of -std=gnu++98 while GCC 5 the default mode for C is now -std=gnu11 instead of -std=gnu89*.
I think that using c++14 causes different behaviour with the same code with respect to previous GCC versions.
I found the source of problem at least for one error during compiling with GCC 6:
```
system/core/adb/transport.c:807:9: error: this &#8216;if&#8217; clause does not guard... [-Werror=misleading-indentation]  if (error_out)
```
is detected by GCC 6 thank to a new warning -Wmisleading-indentation added to -Wall option [https://gcc.gnu.org/gcc-6/porting_to.html](https://gcc.gnu.org/gcc-6/porting_to.html) while is not detected by GCC 5 or lower version.
The current source code:
```

if (error_out)
  *error_out = "insufficient permissions for device";
    continue;

```
it should be:
```

  if (error_out)
  {
    *error_out = "insufficient permissions for device";
  }
    continue;
```
with brackets for a better clearness [https://stackoverflow.com/questions/2125066/is-it-bad-practice-to-use-an-if-statement-without-brackets#2125207](https://stackoverflow.com/questions/2125066/is-it-bad-practice-to-use-an-if-statement-without-brackets#2125207)
After that I corrected this small error, another error appears related to invalid type conversion from const uint16_t* to const char16_t*:
```

frameworks/base/libs/androidfw/AssetManager.cpp: In member function &#8216;android::String8 android::AssetManager::getPkgName(const char*)&#8217;:
frameworks/base/libs/androidfw/AssetManager.cpp:480:63: error: invalid conversion from &#8216;const char16_t*&#8217; to &#8216;const uint16_t* {aka const short unsigned int*}&#8217; [-fpermissive]
             const uint16_t* str = tree.getAttributeStringValue(idx, &len);
                                   ~~~~~~~~~~~~~~~~~~~~~~~~~~~~^~~~~~~~~~~
frameworks/base/libs/androidfw/AssetManager.cpp:481:46: error: invalid conversion from &#8216;const uint16_t* {aka const short unsigned int*}&#8217; to &#8216;const char16_t*&#8217; [-fpermissive]
             pkgName = (str ? String8(str, len) : String8());
                                              ^
In file included from frameworks/base/include/androidfw/Asset.h:30:0,
                 from frameworks/base/libs/androidfw/AssetManager.cpp:26:
system/core/include/utils/String8.h:56:33: note:   initializing argument 1 of &#8216;android::String8::String8(const char16_t*, size_t)&#8217;
     explicit                    String8(const char16_t* o, size_t numChars);


```
In this case the error is related to android utils library android::String8 which uses different return type. So, I think that such problem should be not related to ubuntu touch, but to general android and CM. Is there a way to compile android or CM with GCC 6? In your opinion, have I to report such behaviour to ubport?
I search on the web about this behaviour without success.

Thank you

I corrected all the errors: one was located in file system/core/adb/transport.c, another one in frameworks/base/libs/androidfw/AssetManager.cpp and the other four were located in file frameworks/base/libs/androidfw/ResourceType.cpp. Now I can compile with GCC 4,5,6. In few words, since c++11 has been introduced the type char16_t and GCC 6 supports -std=gnu++14 instead of -std=gnu++98. So since all the warnings are considered as errors due to -Werror a cast from const uint16_t* to const char16_t* solved all the problems. I do not why android developers did not change this.
I filed a bug to CM, in particular the involved version is 12.1 aka android 5.1.

---

