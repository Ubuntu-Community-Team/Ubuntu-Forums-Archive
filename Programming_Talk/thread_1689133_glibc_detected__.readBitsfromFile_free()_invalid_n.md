---
title: "*** glibc detected *** ./readBitsfromFile: free(): invalid next size (fast): 0x000000"
date: 2011-02-16
forum: Programming Talk
---

### Post by matrronchi on 2011-02-16
Hi there, I'm writing a program that should read from a binary file a certain number of bits and write the corrispondent decimal number..

The conversion must be done untill all the bits in the file have been read.

All works fine for the first itaration of my loop but when i free the memory I allocated to keep trace of the read bits I get a glibc detection

I found several posts about this problem on many forum but I still couldn't fix my problem..
...plz help...i have to give my task tomorrow to my teacher...

```
    

dimension = 7;
    
    while(bit_read != EOF){
        
        binary_number = (int*)malloc((dimension + 1) * sizeof(char));
    
        for(i = 0; i < dimension; i++){
            
            bit_read = BitFileGetBit(binary_input_file_p);
            if(bit_read == EOF){
                
                printf("\nRead EOF character Input binary file terminated\n");
                continue;
            }
            printf("\nread bit [%d]\n", (int)bit_read);
            binary_number[i] = (int)bit_read;
            
        }
    
        for(i = dimension - 1; i >= 0; i--){
        
            if(binary_number[i] != 0 && binary_number[i] != 1){
            
                printf("\nBinary numbers have only [0] or [1]\n");
                exit(1);
            }
        
            number += (int)pow(2, i) * binary_number[i];
        
        }
        
        printf("\nNumber is [%d]\n", number);
        
        
        
        printf("\nDEBUG\n");
        
        printf("\nchoose new number of bits to read\n");
        scanf("%d", &dimension);
        
        free(binary_number);
    }
```Any help and suggestion will be very appreciated!!! 

Thanks a lot..

Bye

---

### Post by MadCow108 on 2011-02-16
```
binary_number = (int*)malloc((dimension + 1) * sizeof(char));
```
this looks suspicious
you reserve space for some chars but the array is of type integer which is larger than chars.
in the loop you then exceed the bounds of the allocated memory (sizeof(int)*dim > sizeof(char)*dim)

in future use valgrind to pinpoint the location of memory corruption

---

### Post by Arndt on 2011-02-16
> **MadCow108 said:**
> ```
binary_number = (int*)malloc((dimension + 1) * sizeof(char));
```
this looks suspicious
you reserve space for some chars but the array is of type integer which is larger than chars.
in the loop you then exceed the bounds of the allocated memory (sizeof(int)*dim > sizeof(char)*dim)

in future use valgrind to pinpoint the location of memory corruption

One habit which makes it less likely to allocate using the wrong size is to always write something like

```
binary_number = (int*)malloc((dimension + 1) * sizeof(binary_number[0]));
```

---

### Post by matrronchi on 2011-02-16
...what stupid I was!!!Thks a lot!!Really..
Bye.. ;D

---

