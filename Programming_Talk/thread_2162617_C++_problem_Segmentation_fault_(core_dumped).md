---
title: "C++ problem: Segmentation fault (core dumped)"
date: 2013-07-15
forum: Programming Talk
---

### Post by Pghg022 on 2013-07-15
ok i've been working on this program that takes from a string the part that was bracketed. and i've got this output when i compiled it([COLOR=#ff0000]without any warnings or errors[/COLOR]):confused:
here is the code:
```
#include <iostream>
#include <cstdio>

using namespace std;

void formula_devider(char input[128]){
        char bracket_formula[128];
        int rmb_brk[2];
        int brk,n;
        bool mark = false;
        for(int i = 128; i < 0; i--){
                if(!mark){
                        if(input[i] == ')' ){    //scan for brackets
                        rmb_brk[1] == i;
                        mark = true;
                        }
                }
                if(input[i] == '('){
                        rmb_brk[0] == i;
                        }
                }
        n = rmb_brk[1] - rmb_brk[0];
        for(int j = 0; j > n; j++){
                bracket_formula[j] = input[rmb_brk[0] + j];
                }
        puts(bracket_formula);
        }

int main(){
        puts("TEST! TEST! TEST! TEST!");
        char input[128];
        formula_devider(input);
        }

```

---

### Post by oldos2er on 2013-07-15
Moved to Programming Talk.

---

### Post by ofnuts on 2013-07-15
Looks like mostly C to me.

What do you expect to get in 'input" in main?

---

### Post by trent.josephsen on 2013-07-15
The conditional of a 'for' loop is a "while" condition, not an "until" condition. Neither for loop is executed because both your conditionals are always false, so rmb_brk's contents are uninitialized when you try to use them, which leads to undefined behavior.

You may have other bugs, but fix those for loops first.

---

