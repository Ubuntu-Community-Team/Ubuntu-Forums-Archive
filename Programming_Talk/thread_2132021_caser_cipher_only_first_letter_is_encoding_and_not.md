---
title: "caser cipher: only first letter is encoding and not handling spaces!"
date: 2013-04-03
forum: Programming Talk
---

### Post by hatsoff on 2013-04-03
Here it is:
```

#include <iostream>
#include <stdio.h>
#include <string>
#include <ctype.h>
using namespace std;

int main()
{
    int s ;
    string g  ;
    int size;
    
    printf("key :");
    
    cin >> s;
    
    printf("Enter plain text ");
    
    cin >> g;
    
    

  
 for (int i = 0; i <strlen(g.c_str()) ; i++)
 {     
        char um = g[i];
        
     if(isalpha(um))
     {
         
         if(!islower(um))
         {
             int ascii = (int)um ;
             
            
             while(s!= 0)
             {
                 ascii = ascii + 1 ;
                 
                 if(ascii%122==0)
                 {
                     ascii = 97 ;
                 }
                 s--;
             }
         }else 
          { if(!isupper(um))       
             {int ascii = um ;
              
             while(s!= 0)
             {
                 ascii = ascii + 1 ;
                 
                 
                 if(ascii%122==0)
                 {
                     ascii = 97 ;
                     
                     
                 }
                 s--;
                 
             
             }
             char hj=(char)ascii;
                 printf("%c", hj);
     }}
     }else 
     {
         printf("%c",g[i]);
     }
 }
    system("PAUSE");
    return 0;
}



```

---

