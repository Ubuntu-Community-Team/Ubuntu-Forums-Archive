---
title: "valgrind debug errors"
date: 2011-02-17
forum: Programming Talk
---

### Post by matrronchi on 2011-02-17
Hy there, I'm using valgrind to debug some memory allocation errors..

I'f kind of solved everything, I'm just missing these errors..

any clue?

```


==3050== Invalid write of size 1
==3050==    at 0x4C28FD9: strcat (mc_replace_strmem.c:176)
==3050==    by 0x404DC3: LzwDecode(char*, char*, std::unordered_map<int, std::string, std::hash<int>, std::equal_to<int>, std::allocator<std::pair<int const, std::string> > >, std::unordered_map<std::string, int, std::hash<std::string>, std::equal_to<std::string>, std::allocator<std::pair<std::string const, int> > >) (My_LZW_decode_FAST.cc:500)
==3050==    by 0x401489: main (My_LZW_decode_FAST.cc:85)



==3050==  Address 0x595c286 is 0 bytes after a block of size 6 alloc'd
==3050==    at 0x4C2815C: malloc (vg_replace_malloc.c:236)
==3050==    by 0x404A0A: LzwDecode(char*, char*, std::unordered_map<int, std::string, std::hash<int>, std::equal_to<int>, std::allocator<std::pair<int const, std::string> > >, std::unordered_map<std::string, int, std::hash<std::string>, std::equal_to<std::string>, std::allocator<std::pair<std::string const, int> > >) (My_LZW_decode_FAST.cc:366)
==3050==    by 0x401489: main (My_LZW_decode_FAST.cc:85)
==3050== 



==3050== Invalid read of size 1
==3050==    at 0x4C292AD: __GI_strlen (mc_replace_strmem.c:284)
==3050==    by 0x4ECCE1F: std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string(char const*, std::allocator<char> const&) (in /usr/lib/libstdc++.so.6.0.14)
==3050==    by 0x404DE9: LzwDecode(char*, char*, std::unordered_map<int, std::string, std::hash<int>, std::equal_to<int>, std::allocator<std::pair<int const, std::string> > >, std::unordered_map<std::string, int, std::hash<std::string>, std::equal_to<std::string>, std::allocator<std::pair<std::string const, int> > >) (My_LZW_decode_FAST.cc:509)
==3050==    by 0x401489: main (My_LZW_decode_FAST.cc:85)



==3050==  Address 0x595c286 is 0 bytes after a block of size 6 alloc'd
==3050==    at 0x4C2815C: malloc (vg_replace_malloc.c:236)
==3050==    by 0x404A0A: LzwDecode(char*, char*, std::unordered_map<int, std::string, std::hash<int>, std::equal_to<int>, std::allocator<std::pair<int const, std::string> > >, std::unordered_map<std::string, int, std::hash<std::string>, std::equal_to<std::string>, std::allocator<std::pair<std::string const, int> > >) (My_LZW_decode_FAST.cc:366)
==3050==    by 0x401489: main (My_LZW_decode_FAST.cc:85)
==3050== 



==3050== Invalid read of size 1
==3050==    at 0x4C292AD: __GI_strlen (mc_replace_strmem.c:284)
==3050==    by 0x404F2B: LzwDecode(char*, char*, std::unordered_map<int, std::string, std::hash<int>, std::equal_to<int>, std::allocator<std::pair<int const, std::string> > >, std::unordered_map<std::string, int, std::hash<std::string>, std::equal_to<std::string>, std::allocator<std::pair<std::string const, int> > >) (My_LZW_decode_FAST.cc:524)
==3050==    by 0x401489: main (My_LZW_decode_FAST.cc:85)



==3050==  Address 0x595c286 is 0 bytes after a block of size 6 alloc'd
==3050==    at 0x4C2815C: malloc (vg_replace_malloc.c:236)
==3050==    by 0x404A0A: LzwDecode(char*, char*, std::unordered_map<int, std::string, std::hash<int>, std::equal_to<int>, std::allocator<std::pair<int const, std::string> > >, std::unordered_map<std::string, int, std::hash<std::string>, std::equal_to<std::string>, std::allocator<std::pair<std::string const, int> > >) (My_LZW_decode_FAST.cc:366)
==3050==    by 0x401489: main (My_LZW_decode_FAST.cc:85)
==3050== 


```The code lines which give problems are:

366. new_dictionary_string = (char*)malloc((MAX_STRING_LENGTH + 1) * sizeof(char));

500. strcat(new_dictionary_string, char_string);

509. string_entry = string_dictionary.find(new_dictionary_string);

524. if(strlen(new_dictionary_string) <= MAX_STRING_LENGTH){

really looks like there's something wrong with the char* variable new_dictionary_string,
but i checked thousands of times and memory allocation seems correct to me..

Any advice will be very appreciated!
Thks folks..

Bye

---

### Post by Arndt on 2011-02-17
> **matrronchi said:**
> Hy there, I'm using valgrind to debug some memory allocation errors..

I'f kind of solved everything, I'm just missing these errors..

any clue?

```


==3050== Invalid write of size 1
==3050==    at 0x4C28FD9: strcat (mc_replace_strmem.c:176)
==3050==    by 0x404DC3: LzwDecode(char*, char*, std::unordered_map<int, std::string, std::hash<int>, std::equal_to<int>, std::allocator<std::pair<int const, std::string> > >, std::unordered_map<std::string, int, std::hash<std::string>, std::equal_to<std::string>, std::allocator<std::pair<std::string const, int> > >) (My_LZW_decode_FAST.cc:500)
==3050==    by 0x401489: main (My_LZW_decode_FAST.cc:85)



==3050==  Address 0x595c286 is 0 bytes after a block of size 6 alloc'd
==3050==    at 0x4C2815C: malloc (vg_replace_malloc.c:236)
==3050==    by 0x404A0A: LzwDecode(char*, char*, std::unordered_map<int, std::string, std::hash<int>, std::equal_to<int>, std::allocator<std::pair<int const, std::string> > >, std::unordered_map<std::string, int, std::hash<std::string>, std::equal_to<std::string>, std::allocator<std::pair<std::string const, int> > >) (My_LZW_decode_FAST.cc:366)
==3050==    by 0x401489: main (My_LZW_decode_FAST.cc:85)
==3050== 



==3050== Invalid read of size 1
==3050==    at 0x4C292AD: __GI_strlen (mc_replace_strmem.c:284)
==3050==    by 0x4ECCE1F: std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string(char const*, std::allocator<char> const&) (in /usr/lib/libstdc++.so.6.0.14)
==3050==    by 0x404DE9: LzwDecode(char*, char*, std::unordered_map<int, std::string, std::hash<int>, std::equal_to<int>, std::allocator<std::pair<int const, std::string> > >, std::unordered_map<std::string, int, std::hash<std::string>, std::equal_to<std::string>, std::allocator<std::pair<std::string const, int> > >) (My_LZW_decode_FAST.cc:509)
==3050==    by 0x401489: main (My_LZW_decode_FAST.cc:85)



==3050==  Address 0x595c286 is 0 bytes after a block of size 6 alloc'd
==3050==    at 0x4C2815C: malloc (vg_replace_malloc.c:236)
==3050==    by 0x404A0A: LzwDecode(char*, char*, std::unordered_map<int, std::string, std::hash<int>, std::equal_to<int>, std::allocator<std::pair<int const, std::string> > >, std::unordered_map<std::string, int, std::hash<std::string>, std::equal_to<std::string>, std::allocator<std::pair<std::string const, int> > >) (My_LZW_decode_FAST.cc:366)
==3050==    by 0x401489: main (My_LZW_decode_FAST.cc:85)
==3050== 



==3050== Invalid read of size 1
==3050==    at 0x4C292AD: __GI_strlen (mc_replace_strmem.c:284)
==3050==    by 0x404F2B: LzwDecode(char*, char*, std::unordered_map<int, std::string, std::hash<int>, std::equal_to<int>, std::allocator<std::pair<int const, std::string> > >, std::unordered_map<std::string, int, std::hash<std::string>, std::equal_to<std::string>, std::allocator<std::pair<std::string const, int> > >) (My_LZW_decode_FAST.cc:524)
==3050==    by 0x401489: main (My_LZW_decode_FAST.cc:85)



==3050==  Address 0x595c286 is 0 bytes after a block of size 6 alloc'd
==3050==    at 0x4C2815C: malloc (vg_replace_malloc.c:236)
==3050==    by 0x404A0A: LzwDecode(char*, char*, std::unordered_map<int, std::string, std::hash<int>, std::equal_to<int>, std::allocator<std::pair<int const, std::string> > >, std::unordered_map<std::string, int, std::hash<std::string>, std::equal_to<std::string>, std::allocator<std::pair<std::string const, int> > >) (My_LZW_decode_FAST.cc:366)
==3050==    by 0x401489: main (My_LZW_decode_FAST.cc:85)
==3050== 


```The code lines which give problems are:

366. new_dictionary_string = (char*)malloc((MAX_STRING_LENGTH + 1) * sizeof(char));

500. strcat(new_dictionary_string, char_string);

509. string_entry = string_dictionary.find(new_dictionary_string);

524. if(strlen(new_dictionary_string) <= MAX_STRING_LENGTH){

really looks like there's something wrong with the char* variable new_dictionary_string,
but i checked thousands of times and memory allocation seems correct to me..

Any advice will be very appreciated!
Thks folks..

Bye

Does it perhaps mean something that line 500 comes before line 366 in the valgrind output?

Apart from that, the code snippets themselves look fine to me.

---

### Post by matrronchi on 2011-02-17
> Does it perhaps mean something that line 500 comes before line 366 in the valgrind output?

What do you mean?

> Apart from that, the code snippets themselves look fine to me.

Then what do you suggest me to do?

Thks..

---

### Post by Arndt on 2011-02-17
> **matrronchi said:**
> What do you mean?



Then what do you suggest me to do?

Thks..

If they are executed in that order, it may mean that it is used before it has been allocated.

---

### Post by MadCow108 on 2011-02-17
there is to little information to debug it.
please post more context

is new_dictionary_string initialized with ...[0] = '\0'?
can it be that char_string is too long or not null terminated?

---

### Post by matrronchi on 2011-02-17
> is new_dictionary_string initialized with ...[0] = '\0'?
 can it be that char_string is too long or not null terminated?I checked exactly these 2 things..

I allocated memory for new_dictionary_string and then used sprintf to initialize it

```

    char *new_dictionary_string;
    new_dictionary_string = (char*)malloc((MAX_STRING_LENGTH + 1) * sizeof(char));
    sprintf(new_dictionary_string, " ");

```since sprintf automatically appends null character that shouldn't be the problem..

this is how i defined and initialized char_string

```

    char *char_string;
    char_string = (char*)malloc(2 * sizeof(char));
    char_string[0] = ' ';
    char_string[1] = '\0';

```so also char_string variable should be ok..

I'm just getting mad..
cause strcpy and strcat always append the null character of src string

[http://www.cplusplus.com/reference/clibrary/cstring/strcpy/](http://www.cplusplus.com/reference/clibrary/cstring/strcpy/)
[http://www.cplusplus.com/reference/clibrary/cstring/strcat/](http://www.cplusplus.com/reference/clibrary/cstring/strcat/)

so i can't understand why valgrind will continue giving these errors

```


==4013== Invalid write of size 1
==4013==    at 0x4C28FD9: strcat (mc_replace_strmem.c:176)
==4013==    by 0x404E8F: LzwDecode(char*, char*,  std::unordered_map<int, std::string, std::hash<int>,  std::equal_to<int>, std::allocator<std::pair<int const,  std::string> > >, std::unordered_map<std::string, int,  std::hash<std::string>, std::equal_to<std::string>,  std::allocator<std::pair<std::string const, int> > >)  (My_LZW_decode_FAST.cc:515)
==4013==    by 0x4014C9: main (My_LZW_decode_FAST.cc:85)

==4013==  Address 0x595c236 is 0 bytes after a block of size 6 alloc'd
==4013==    at 0x4C2815C: malloc (vg_replace_malloc.c:236)
==4013==    by 0x404A43: LzwDecode(char*, char*,  std::unordered_map<int, std::string, std::hash<int>,  std::equal_to<int>, std::allocator<std::pair<int const,  std::string> > >, std::unordered_map<std::string, int,  std::hash<std::string>, std::equal_to<std::string>,  std::allocator<std::pair<std::string const, int> > >)  (My_LZW_decode_FAST.cc:374)
==4013==    by 0x4014C9: main (My_LZW_decode_FAST.cc:85)
==4013== 


==4013== Invalid read of size 1
==4013==    at 0x4C292AD: __GI_strlen (mc_replace_strmem.c:284)
==4013==    by 0x4ECCE1F: std::basic_string<char,  std::char_traits<char>, std::allocator<char>  >::basic_string(char const*, std::allocator<char> const&)  (in /usr/lib/libstdc++.so.6.0.14)
==4013==    by 0x404F16: LzwDecode(char*, char*,  std::unordered_map<int, std::string, std::hash<int>,  std::equal_to<int>, std::allocator<std::pair<int const,  std::string> > >, std::unordered_map<std::string, int,  std::hash<std::string>, std::equal_to<std::string>,  std::allocator<std::pair<std::string const, int> > >)  (My_LZW_decode_FAST.cc:530)
==4013==    by 0x4014C9: main (My_LZW_decode_FAST.cc:85)

==4013==  Address 0x595c236 is 0 bytes after a block of size 6 alloc'd
==4013==    at 0x4C2815C: malloc (vg_replace_malloc.c:236)
==4013==    by 0x404A43: LzwDecode(char*, char*,  std::unordered_map<int, std::string, std::hash<int>,  std::equal_to<int>, std::allocator<std::pair<int const,  std::string> > >, std::unordered_map<std::string, int,  std::hash<std::string>, std::equal_to<std::string>,  std::allocator<std::pair<std::string const, int> > >)  (My_LZW_decode_FAST.cc:374)
==4013==    by 0x4014C9: main (My_LZW_decode_FAST.cc:85)
==4013== 


==4013== Invalid read of size 1
==4013==    at 0x4C292AD: __GI_strlen (mc_replace_strmem.c:284)
==4013==    by 0x405058: LzwDecode(char*, char*,  std::unordered_map<int, std::string, std::hash<int>,  std::equal_to<int>, std::allocator<std::pair<int const,  std::string> > >, std::unordered_map<std::string, int,  std::hash<std::string>, std::equal_to<std::string>,  std::allocator<std::pair<std::string const, int> > >)  (My_LZW_decode_FAST.cc:545)
==4013==    by 0x4014C9: main (My_LZW_decode_FAST.cc:85)

==4013==  Address 0x595c236 is 0 bytes after a block of size 6 alloc'd
==4013==    at 0x4C2815C: malloc (vg_replace_malloc.c:236)
==4013==    by 0x404A43: LzwDecode(char*, char*,  std::unordered_map<int, std::string, std::hash<int>,  std::equal_to<int>, std::allocator<std::pair<int const,  std::string> > >, std::unordered_map<std::string, int,  std::hash<std::string>, std::equal_to<std::string>,  std::allocator<std::pair<std::string const, int> > >)  (My_LZW_decode_FAST.cc:374)
==4013==    by 0x4014C9: main (My_LZW_decode_FAST.cc:85)
==4013== 


```374. new_dictionary_string = (char*)malloc((MAX_STRING_LENGTH + 1) * sizeof(char));
515. strcat(new_dictionary_string, char_string);
530. string_entry = string_dictionary.find(new_dictionary_string);
545. if(strlen(new_dictionary_string) <= MAX_STRING_LENGTH){

it's clear that the problem is writing in new_dctionary_string (515)
and reading from it (530 - 545)

---

### Post by Zugzwang on 2011-02-17
One suggestion: Add one line in front of line 515, stating "assert(strlen(new_dictionary_string)+strlen(char_string)<=MAX_STRING_LENGTH);". Also add "#include <assert.h>" or "#include <cassert>" at the top of your source file".

Compile your program with "-g", see if it stops due to an assumption failure when executing it and if yes, use a debugger to inspect the contents of the local variables at the time of the assertion failure.

EDIT: Strange: The forum editor always automatically adds a blank to the command written above. So please fix this after pasting.

---

### Post by matrronchi on 2011-02-17
> 
Add one line in front of line 515, stating "assert(strlen(new_dictionary_string)+strlen(char_  string)<=MAX_STRING_LENGTH);"


the output of execution is

```

void LzwDecode(char*, char*, CodeDictionary, StringDictionary):  Assertion `strlen(new_dictionary_string)+strlen(char_string)<=5'  failed.

```

so there is a boundaries problem..

gdb gave me this output on command info locals

```

info locals
iter =  {<std::__detail::_Hashtable_iterator_base<std::pair<std::basic_string<char,  std::char_traits<char>, std::allocator<char> > const,  int>, false>> = {_M_cur_node = 0x0, 
    _M_cur_bucket = 0x0}, <No data fields>}
finished = 0
check_string_insertion = {first =  {<std::__detail::_Hashtable_iterator_base<std::pair<std::basic_string<char,  std::char_traits<char>, std::allocator<char> > const,  int>, false>> = {_M_cur_node = 0x626ce0, 
      _M_cur_bucket = 0x624450}, <No data fields>}, second = true}
dictionary_word_bits = 9
init = 0
new_dictionary_string = 0x612e80 "ation"
old_code_translation_string = 0x612ea0 "t"
code_iter =  {<std::__detail::_Hashtable_iterator_base<std::pair<int const,  std::basic_string<char, std::char_traits<char>,  std::allocator<char> > >, false>> = {_M_cur_node =  0x0, 
    _M_cur_bucket = 0x0}, <No data fields>}
initial_c = 115 's'
char_string = 0x612ec0 "s"
output_file_p = 0x612ee0
iter1 =  {<std::__detail::_Hashtable_iterator_base<std::pair<std::basic_string<char,  std::char_traits<char>, std::allocator<char> > const,  int>, false>> = {_M_cur_node = 0x0, 
    _M_cur_bucket = 0x0}, <No data fields>}
decoded_string = 0x612e60 "s."
binary_input_file_p = 0x613120
old_code = 19
j = 0
input_file_p = 0x61
old_code_entry =  {<std::__detail::_Hashtable_iterator_base<std::pair<int const,  std::basic_string<char, std::char_traits<char>,  std::allocator<char> > >, false>> = {_M_cur_node =  0x61a1d0, 
    _M_cur_bucket = 0x6230d8}, <No data fields>}
new_code = 325
string_entry =  {<std::__detail::_Hashtable_iterator_base<std::pair<std::basic_string<char,  std::char_traits<char>, std::allocator<char> > const,  int>, false>> = {_M_cur_node = 0x1000, 
    _M_cur_bucket = 0x6256d8}, <No data fields>}
k = 0
check_code_insertion = {first =  {<std::__detail::_Hashtable_iterator_base<std::pair<int const,  std::basic_string<char, std::char_traits<char>,  std::allocator<char> > >, false>> = {_M_cur_node =  0x626c90, 
      _M_cur_bucket = 0x623278}, <No data fields>}, second = true}
dictionary_length = 512
last_index_used = 485
__PRETTY_FUNCTION__ = "void LzwDecode(char*, char*, CodeDictionary, StringDictionary)"
new_code_entry =  {<std::__detail::_Hashtable_iterator_base<std::pair<int const,  std::basic_string<char, std::char_traits<char>,  std::allocator<char> > >, false>> = {_M_cur_node =  0x61eeb0, 
    _M_cur_bucket = 0x622d78}, <No data fields>}


```
```

new_dictionary_string = 0x612e80 "ation"
char_string = 0x612ec0 "s"

```

in fact the sum is more than 5...

i corrected this stuff and the code seems working...thks so much!!!!
if there are other problems i'll post them in a while.. ;D

---

### Post by matrronchi on 2011-02-17
everything is solved!!!!!!!!!!!

thanks for help guys ;D

---

