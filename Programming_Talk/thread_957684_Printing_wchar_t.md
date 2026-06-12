---
title: "Printing wchar_t"
date: 2008-10-24
forum: Programming Talk
---

### Post by cl333r on 2008-10-24
Hi,

Does anyone know why this code doesn't print anything?:

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char** argv) {
    
    wchar_t *wmessage = L"&#1055;&#1088;&#1080;&#1074;&#1077;&#1090; &#1074;&#1089;&#1077;&#1084;!";
    printf("%ls\n\n", wmessage);

    return (EXIT_SUCCESS);
}

```

The website I learned from is:
[http://linuxprograms.wordpress.com/2008/03/07/c-printing-data-types-using-printf-short-wchar_t-long-double/](http://linuxprograms.wordpress.com/2008/03/07/c-printing-data-types-using-printf-short-wchar_t-long-double/)

---

### Post by Npl on 2008-10-24
does it work if you use an wide-string with ascii-Characters? (ie wchar_t *wmessage = L"Something"; )

I cant tell for sure whats the problem, but you shouldnt use non-ascii in sourcecode, compilers dont know much about character-encodings. If you want use non-ascii you should use hexcodes.

---

### Post by cl333r on 2008-10-24
Yeah, it works when using only ASCII. I thought that what it's designed for, to store unicode-like characters, I mean non-ascii.

---

### Post by Npl on 2008-10-24
nope, its used to convert ASCII into widechars( L"" takes every byte/char and encode it in wchars - your String probably aint using 1 byte/char per Character). If you write nonascii in sources you`re in a world of trouble, editors might use several encodings for your text.

---

### Post by cl333r on 2008-10-24
but interestingly enough, when I just use "char" the compiler works fine. The following works fine (even the Japanese glyphs) so it kinda tells a newbie to use char for unicode, I'm confused:

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char** argv) {
    
    char *message = "&#1055;&#1088;&#1080;&#1074;&#1077;&#1090; &#1074;&#1089;&#1077;&#1084;! &#26085;&#26412;&#22269;";
    printf("%s\n\n", message);
    return (EXIT_SUCCESS);
}

```

---

