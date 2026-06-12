---
title: "get binary representation of char"
date: 2008-08-28
forum: Programming Talk
---

### Post by monkeyking on 2008-08-28
Hi,
I'm trying to make a datastructure used for holding data that can be understood as a matrix where every element in the matrix,
can only be 4 values. I will refer to these as VALS

The data is huge, so I wanted to check how much the speeddown is if I try to "compress" the data.

4 values can be represented by 2 bits,
1 int is 32 bits so in theory I should be able to cramp 16 VALS,
into 1 int.

The smallest datatype in c/c++ is char which is 1byte=8bit.
So I just need a way to handle the bit pattern of a char.

thanks in advance

---

### Post by cabalas on 2008-08-28
They following links should hopefull give you all the information you need to do what you want to do.

[http://www.cprogramming.com/tutorial/bitwise_operators.html](http://www.cprogramming.com/tutorial/bitwise_operators.html)

[http://www.cprogramming.com/faq/cgi-bin/smartfaq.cgi?id=1073086407&answer=1074727388](http://www.cprogramming.com/faq/cgi-bin/smartfaq.cgi?id=1073086407&answer=1074727388)

---

### Post by monkeyking on 2008-08-28
Hmm, i managed to do the following,
which doesn't work, can anyone tell me why?

thanks in advance
[PHP]

#include <iostream>

void printChar(char c){
  char bit_mask = 0x80 ; // this is 1000 0000
  for(int i=0;i<8;i++){
    if ((bit_mask & c)) //extract i'th bit
      printf("1\t");
    else
      printf("0\t");
    bit_mask = bit_mask >>1;
  }
  printf("\n");
    
}


int main(){
  char chr=0x02;
  printChar(chr);
}


[/PHP]

---

### Post by monkeyking on 2008-08-28
What's even more ackward is that,
If I just change the shift order,
it works.
What's wrong with the first version.
This version hovever print's out from right to left,
so the printf results are ofcause reversed.

[PHP]
#include <iostream>

void printChar(char c){
  char bit_mask = 0x01 ; //CHANGED FROM ABOVE
  for(int i=0;i<8;i++){
    if ((bit_mask & c)) //extract i'th bit
      printf("1\t");
    else
      printf("0\t");
    bit_mask = bit_mask <<1; // CHANGED FROM ABOVE
  }
  printf("\n");
    
}


int main(){
  char chr=0x02;
  printChar(chr);
}  
[/PHP]

---

### Post by mujambee on 2008-08-29
You are using signed chars, and when you right-shift a signed variable, it repeats the sign bit.

So, you start with bit_mask = 1000000

when you right-shift it as signed, you get bit_mask = 11000000, but if it is unsigned you get what you where looking for, bit_mask = 01000000.

Just for completeness, if you have bit_mask=01000000 as signed and right-shift, you get bit_mask = 00100000, because the sign bit is down.

This difference is only for right-shifts, left-shifts work the same for signed and unsigned values.


Try this:

[PHP code]
[COLOR=#000000][COLOR=#ff8000]#include <iostream> 

[/COLOR][COLOR=#0000bb]void printChar[/COLOR][COLOR=#007700](unsigned [/COLOR][COLOR=#0000bb]char c[/COLOR][COLOR=#007700]){ 
  [/COLOR][COLOR=#0000bb]unsigned char bit_mask [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]0x80 [/COLOR][COLOR=#007700]; [/COLOR][COLOR=#ff8000]// this is 1000 0000 
  [/COLOR][COLOR=#007700]for([/COLOR][COLOR=#0000bb]int i[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700];[/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700]<[/COLOR][COLOR=#0000bb]8[/COLOR][COLOR=#007700];[/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700]++){ 
    if (([/COLOR][COLOR=#0000bb]bit_mask [/COLOR][COLOR=#007700]& [/COLOR][COLOR=#0000bb]c[/COLOR][COLOR=#007700])) [/COLOR][COLOR=#ff8000]//extract i'th bit 
      [/COLOR][COLOR=#0000bb]printf[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"1\t"[/COLOR][COLOR=#007700]); 
    else 
      [/COLOR][COLOR=#0000bb]printf[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"0\t"[/COLOR][COLOR=#007700]); 
    [/COLOR][COLOR=#0000bb]bit_mask [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]bit_mask [/COLOR][COLOR=#007700]>>[/COLOR][COLOR=#0000bb]1[/COLOR][COLOR=#007700]; 
  } 
  [/COLOR][COLOR=#0000bb]printf[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"\n"[/COLOR][COLOR=#007700]); 
     
} 


[/COLOR][COLOR=#0000bb]int main[/COLOR][COLOR=#007700](){ 
  unsigned [/COLOR][COLOR=#0000bb]char chr[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000bb]0x02[/COLOR][COLOR=#007700]; 
  [/COLOR][COLOR=#0000bb]printChar[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]chr[/COLOR][COLOR=#007700]); 
}  [/COLOR][/COLOR]
[/PHP code]

---

