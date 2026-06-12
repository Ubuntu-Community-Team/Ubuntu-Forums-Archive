---
title: "How do I implement toupper()? (in C)"
date: 2007-03-11
forum: Programming Talk
---

### Post by raul_ on 2007-03-11
I have to implement this function that does exactly what toupper() does. How can i convert 'a' to 'A' ? Is it with a shift? I honestly have no idea. I'm not looking for code, just an explanation :) thanks

---

### Post by lnostdal on 2007-03-11
[http://en.wikipedia.org/wiki/Ascii#ASCII_printable_characters](http://en.wikipedia.org/wiki/Ascii#ASCII_printable_characters)

```

cl-user> (char-code #\a)
97
cl-user> (char-code #\A)
65
cl-user> (- (char-code #\a) (char-code #\A))
32
cl-user> ;; which means ...
; No value
cl-user> (code-char (- (char-code #\b) 32))
#\B
cl-user> (code-char (- (char-code #\c) 32))
#\C
cl-user> (code-char (- (char-code #\d) 32))
#\D
cl-user> (code-char (- (char-code #\e) 32))
#\E
cl-user> (code-char (- (char-code #\f) 32))
#\F

```

---

### Post by hod139 on 2007-03-11
lnostdal, the problem with your solution is that you assumed ascii.  What if the encoding is different?

---

### Post by raul_ on 2007-03-11
Thank you very much! :)

---

### Post by lnostdal on 2007-03-11
> **hod139 said:**
> lnostdal, the problem with your solution is that you assumed ascii.  What if the encoding is different?

then the user will find himself in a tar pit trap of endless sufferings and torment

(or:  i haven't done much unicode/wide-char-stuff in c/c++ .. :)  edit: but have done some in lisp: [http://nostdal.org/~lars/programming/lisp/aromyxo/web/url.lisp](http://nostdal.org/~lars/programming/lisp/aromyxo/web/url.lisp) very nasty code though :/  )

---

### Post by raul_ on 2007-03-11
This seems to be working. 

```

#include <stdio.h>

char upper(char c){
	
	if( c>='a' && c<='z')
	return (c = c +'A' - 'a');
		else
	return c;
	
}

int main(){
	printf("%c\n", upper('c'));
	return 0;
}

```

---

### Post by j_g on 2007-03-11
Just a few minor points, you don't need that "else" in there. A return ends the function right there. Many compilers will insert unneeded jmp or other branch instructions when you insert unnecessary "else" statements.

But if you want to minimize code size, then try to use only one return instruction like so:

if( c>='a' && c<='z')
   c += ('A' - 'a');
return c;

The reason for this is because a return instruction typically resolves to numerous machine codes that pop registers, readjust the stack frame, and put any return value in the EAX register (assuming 80x86). And all this is duplicated for each return.

Also, I used += because that usually helps a compiler optimize the machine code to avoid unnecessary fetches (ie, mov instructions in Intel lingo). Finally, judicious use of register variables can also reduce code size and improve speed since many opcodes are faster when using registers.

---

### Post by raul_ on 2007-03-12
You're right :) thanks for the reply

---

### Post by Kardelen on 2013-01-17
Hi,

Here is my function to convert a string to uppercase.

```

char *to_upper(char *src)
{
    int len = strlen(src),
        i;
    
    for (i = 0; i < len; i++)
        if (*(src + i) >= 'a' && *(src + i) <= 'z')
            *(src + i) -= ('a' - 'A');
    
    return src;
}

```

While it builds fine, when I run it I receive this error:

> Signal received: SIGSEGV (?) with sigcode ? (?)
From process: ?
For program socket_deneme, pid 19,242

You may discard the signal or forward it and you may continue or pause the process
To control which signals are caught or ignored use Debug->Dbx Configure

when I debug the code, error occurs at

```
*(src + i) -= ('a' - 'A');
```

What is this error, how did I do it, and how can I avoid it?

Addendum: I use Netbeans 7.0.1 on Ubuntu.

---

### Post by ofnuts on 2013-01-17
I'm pretty sure that you are testing your code using constant strings like "abcdefg". But the compiler allocates them in a read-only part of the memory and you are trying to overwrite them so your code segfaults. Have the code copy them first and it should work.

However, having  function that changes its input argument that way is bad style. The function should make a copy and uppercase it.

And by the way, "*(str+i)" can be written using the much more readable "str[i]".

---

