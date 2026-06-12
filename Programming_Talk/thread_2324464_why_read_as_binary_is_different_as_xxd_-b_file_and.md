---
title: "why read as binary is different as xxd -b file and how to read as binary like xxd"
date: 2016-05-14
forum: Programming Talk
---

### Post by zerop2 on 2016-05-14
why read as binary is different as xxd -b file and how to read as binary like xxd


```
#include <stdio.h> 
 
unsigned char mask = 1; 
unsigned char bits[8]; 
int main() 
{ 
unsigned char buffer[1000]; 
FILE *ptr; 
 
ptr = fopen("readasbinary.csv","rb");  // r for read, b for binary 
 
fread(buffer,sizeof(buffer),1,ptr); // read 10 bytes to our buffer 
 
int i = 0; 
int j = 0; 
for(i = 0; i<1000; ++i) 
{ 
 for (j = 0; j < 8; ++j) 
 { 
  bits[j] = (buffer[i] & (mask << j)) != 0; 
 } 
 for (j = 0; j < 8; ++j) 
 { 
  printf("%d", bits[j]); // prints a series of bytes 
 } 
 printf(" "); 
} 
 
FILE *write_ptr; 
 
write_ptr = fopen("readasbinary2.csv","wb");  // w for write, b for binary 
 
fwrite(buffer,sizeof(buffer),1,write_ptr); // write 10 bytes to our buffer 
}
```

---

### Post by spjackson on 2016-05-14
You are printing each byte with the least significant bit on the left. The normal convention is to print it with the most significant bit on the left. One way to correct this is:
```

 //for (j = 0; j < 8; ++j) 
 for (j = 7; j >= 0 ; --j) 
 { 
  printf("%d", bits[j]); // prints a series of bytes 
 } 

```

---

