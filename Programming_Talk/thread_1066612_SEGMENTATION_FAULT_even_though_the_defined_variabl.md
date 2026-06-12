---
title: "SEGMENTATION FAULT even though the defined variable is very small"
date: 2009-02-11
forum: Programming Talk
---

### Post by bhaskar_goel on 2009-02-11
i am writing code in geany, as soon as i define the data_info[50] character array or any other array greater than size 8 the output reads segmentation fault. here is the code:-
#include <stdio.h>
 int main()
    {
     
       int i,j,k,x,y,z=0;
      char c,temp;
      char d_info[50]; //segmentation fault due to this definition
                       //other variables work fine till now.
      char timestamp[15];
      char mac_source[20];
      char mac_destination[20];
      char protocol_type[5];
      char length[5];
       FILE *fptr;
      fptr=fopen("/etc/init.d/C_collect.txt","r");
 
      
      
            
       while((c=getc(fptr))!=' ')
       	timestamp[i++]=c;
	    timestamp[i]='\0';
	     printf("%s",timestamp);
	   
	    while((c=getc(fptr))!=' ')
	    mac_source[j++]=c;
	    mac_source[j]='\0';
	    printf("  %s",mac_source); 
	     getc(fptr);
	     getc(fptr);
	     while((c=getc(fptr))!=',')
             mac_destination[k++]=c;
             mac_destination[k]='\0';
             printf("  %s",mac_destination);
	    
         getc(fptr);
         
         
         while((c=getc(fptr))!=' ');	 
	    
	    while((c=getc(fptr))!=' ')
	     protocol_type[x++]=c;
	     protocol_type[x]='\0';
	     printf("   %s",protocol_type); 
         temp=protocol_type[x-1];
        switch(temp)
          {
          	 case 'P' :
          	 		
          	     while((c=getc(fptr))!=',') ;
          	     	
          	     c=getc(fptr);//space
          	     
          	     while((c=getc(fptr))!=' ') ;
          	      	
          	    while((c=getc(fptr))!=':')
          	    {	
          	       	length[y++]=c;
          	    }
          	    length[y]='\0';
          	    printf("  %s",length);
          	    
          	    
          	    getc(fptr);
          	  while((c=getc(fptr))!='\n')
          	    d_info[z++]=c;
          	     d_info[z]='\0';
          	     printf("   %s",d_info);
          	    
          	    break;
                     
           }  

can someone please point the way , this is really frustrating :(

---

### Post by Victor Liu on 2009-02-11
It would help if you could post the input file. Also, you can probably figure it out by compiling with debugging (add -g to the gcc invocation), and running it under gdb:

```

gcc -g yourcode.c -o yourcode
gdb yourcode

```

Then type 'run' and let it crash, and you will hopefully see where it is crashing. Use the 'bt' command to get a stack trace.

---

### Post by weresheep on 2009-02-11
Without the input data it is hard to debug your program. I don't think the problem(s) lie with the declaration of a 50 character array though. As a starting point I would look at the variable i. It is being used without being initialised. As are j, k, x and y.

-weresheep

---

### Post by The Cog on 2009-02-11
I reduced it to this and it still segfaults:```
int main()
{

    int i=0,j,k,x,y,z=0;
    char c,temp;
    char timestamp[15];
    
    c = 3;
    printf("one i = %d\n", i);
    timestamp[i++]=c;
    printf("two\n");
}

```Notice the output:
> one i = -1081015528
Segmentation fault

It seems that you are not initialising i to 0, and indexing way out of range. This line fixes my cut-down version:
```
int i=0,j,k,x,y,z=0;
```
P.S. this also fixes the snippet:
```
    int i,j,k,x,y,z;
    i=j=k=x=y=z=0;
```

---

### Post by bhaskar_goel on 2009-02-11
i tried your suggestion and it still segfaults, here is the input file:-

10:06:56.220436 00:15:17:98:d0:9e > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: arp who-has 15.15.151.15 (ff:ff:ff:ff:ff:ff) tell 15.15.151.15
	0x0000:  0001 0800 0604 0001 0015 1798 d09e 0f0f
	0x0010:  970f ffff ffff ffff 0f0f 970f 0000 0000
	0x0020:  0000 0000 0000 0000 0000 0000 0000
10:06:56.563181 00:17:31:70:cb:e6 > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 92: 172.31.5.55.137 > 172.31.255.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
	0x0000:  4500 004e 4bc3 0000 8011 9166 ac1f 0537
	0x0010:  ac1f ffff 0089 0089 003a 9553 8322 0110
	0x0020:  0001 0000 0000 0000 2046 4546 4444 4144
	0x0030:  4143 4f45 4646 4445 4646 4543 4f45 4445
	0x0040:  5045 4e43 4143 4141 4100 0020 0001
10:06:56.646740 00:1e:8c:cd:ea:03 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: arp who-has 172.31.0.141 tell 172.31.2.4
	0x0000:  0001 0800 0604 0001 001e 8ccd ea03 ac1f
	0x0010:  0204 0000 0000 0000 ac1f 008d 0000 0000
	0x0020:  0000 0000 0000 0000 0000 0000 0000
10:06:56.713152 00:30:48:28:ca:82 > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 92: 172.31.1.137.137 > 172.31.255.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
	0x0000:  4500 004e fae5 0000 8011 e5f1 ac1f 0189
	0x0010:  ac1f ffff 0089 0089 003a 2526 fdfd 0110
	0x0020:  0001 0000 0000 0000 2046 4845 5046 4345
	0x0030:  4c45 4846 4345 5046 4646 4143 4143 4143
	0x0040:  4143 4143 4143 4142 4d00 0020 0001

thank you for trying anyway, but i still need help

---

### Post by bhaskar_goel on 2009-02-12
FOR VICTOR LIU,
i tried the debugging thing and got this as output

Program received signal SIGSEGV, Segmentation fault.
0xb7ec464d in getc () from /lib/tls/i686/cmov/libc.so.6

cant understand what it means, any ideas?

---

### Post by eye208 on 2009-02-12
```
#include <stdio.h>
 int main()
    {
     
       int i,j,k,x,y,z=0;
      char c,temp;
      char d_info[50]; //segmentation fault due to this definition
                       //other variables work fine till now.
      char timestamp[15];
      char mac_source[20];
      char mac_destination[20];
      char protocol_type[5];
      char length[5];
       FILE *fptr;
      fptr=fopen("/etc/init.d/C_collect.txt","r");
```
Missing check for fptr == NULL.

```
       while((c=getc(fptr))!=' ')
       	timestamp[i++]=c;
	    timestamp[i]='\0';
```
Variable i not initialized. Missing array bounds check for timestamp[]. Endless loop and buffer overflow if getc() returns EOF.

```
	     printf("%s",timestamp);
	   
	    while((c=getc(fptr))!=' ')
	    mac_source[j++]=c;
	    mac_source[j]='\0';
```
Variable j not initialized. Missing array bounds check for mac_source[]. Endless loop and buffer overflow if getc() returns EOF.

```
	    printf("  %s",mac_source); 
	     getc(fptr);
	     getc(fptr);
	     while((c=getc(fptr))!=',')
             mac_destination[k++]=c;
             mac_destination[k]='\0';
```
Variable k not initialized. Missing array bounds check for mac_destination[]. Endless loop and buffer overflow if getc() returns EOF.

```
             printf("  %s",mac_destination);
	    
         getc(fptr);
         
         
         while((c=getc(fptr))!=' ');	 
```
Endless loop if getc() returns EOF.

```
	    while((c=getc(fptr))!=' ')
	     protocol_type[x++]=c;
	     protocol_type[x]='\0';
```
Variable x not initialized. Missing array bounds check for protocol_type[]. Endless loop and buffer overflow if getc() returns EOF.

```
	     printf("   %s",protocol_type); 
         temp=protocol_type[x-1];
        switch(temp)
          {
          	 case 'P' :
          	 		
          	     while((c=getc(fptr))!=',') ;
```
Endless loop if getc() returns EOF.

```
          	     c=getc(fptr);//space
          	     
          	     while((c=getc(fptr))!=' ') ;
```
Endless loop if getc() returns EOF.

```
          	    while((c=getc(fptr))!=':')
          	    {	
          	       	length[y++]=c;
          	    }
          	    length[y]='\0';
```
Variable y not initialized. Missing array bounds check for length[]. Endless loop and buffer overflow if getc() returns EOF.

```
          	    printf("  %s",length);
          	    
          	    
          	    getc(fptr);
          	  while((c=getc(fptr))!='\n')
          	    d_info[z++]=c;
          	     d_info[z]='\0';
```
Missing array bounds check for d_info[]. Endless loop and buffer overflow if getc() returns EOF.

---

### Post by abdusamed on 2010-09-18
After my geany starts, I try to create a new file from the toolbar. Old->C++... the program crashes. 


I then checked the terminal log, it comes up with 'Segmentation fault'

Am I missing something? What should I install?

---

