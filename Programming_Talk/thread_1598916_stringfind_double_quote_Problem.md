---
title: "string::find double quote Problem"
date: 2010-10-17
forum: Programming Talk
---

### Post by PirateMcplunder on 2010-10-17
I can't seem to understand why the code below enters the if statement:

```

#include string
#include stdio.h

int main(){
size_t found;
string after_token = "\"testing testing testing\"";

found=after_token.find("\"");
if (found==string::npos){
[INDENT]cerr << "Payload does not contain double quotes. check input:\n" << endl;
exit (1);[/INDENT]
}
after_token.erase(found);
}
```

I am trying to locate the first double quote in the string after_token so that I can erase it.  My understanding is that "\"" should be the correct representation of an escaped double quote string literal (it works during string initialization/assignment).  What am I doing wrong?

---

### Post by GeneralZod on 2010-10-17
The "if" statement is not entered on my machine, although note that the chosen overload of erase will erase the first double-quote, *and everything after that*.

Edit:

Also, please post the exact code you are using - this plainly isn't it (#include string ?!) :)

---

### Post by PirateMcplunder on 2010-10-17
erasing the whole line was my problem. Thank you again Zod!  You are more valuable than the rune that shares your name in Diablo 2! (and that's saying something!!).

---

