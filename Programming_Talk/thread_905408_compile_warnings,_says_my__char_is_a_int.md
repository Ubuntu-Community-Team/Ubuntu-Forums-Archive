---
title: "compile warnings, says my  char is a int"
date: 2008-08-30
forum: Programming Talk
---

### Post by monkeyking on 2008-08-30
The following code gives this warning.
Btw, this is just a small snippet from a much larger program.


```

vars.cpp: In member function ‘void snp::print(char)’:
vars.cpp:15: warning: format ‘%s’ expects type ‘char*’, but argument 3 has type
‘int’

```

[PHP]
#include <iostream>
class snp{
private:
  unsigned char **alloc(int x, int y);
  unsigned char **m_data;
public:
  void print(char s='\t');
  size_t x;
  size_t y;
};

void snp::print(char s){
  unsigned char tmp=m_data[0][0];
  unsigned char bits= 0x03;
  printf("%x%s",tmp & bits,s); //extract 1100 0000

}
[/PHP]

---

### Post by mike_g on 2008-08-30
Maybe try:
```
 printf("%x[COLOR="Red"]%c[/COLOR]",tmp & bits,s);
```
As %s is for strings not a single char

---

### Post by monkeyking on 2008-08-30
thanks,
no warnings now.

---

