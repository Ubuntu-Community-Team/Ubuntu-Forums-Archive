---
title: "C,fgetc,fputc not working."
date: 2009-08-06
forum: Programming Talk
---

### Post by ericeclifford on 2009-08-06
Basically I am trying to translate 2 bits into 1 byte hex, Its not working out for me well and when rawdata.bin is created it just creates a symbol. Any help on this would be much appreciated.


//main.c
// This program will read a 8b's and translate it into 4 b's


#include <stdio.h>

int main ()
{
  FILE * iFile;
  FILE * oFile;
  int in;
  int out;
  int n;
  int ok_files = 1;
  
   
	iFile = fopen ("/home/sei/data.txt","rb");
	if(iFile <= 0) {
		ok_files = 0;
	       	printf ("Error");
		}  // end if ifile
	else
	printf("opened input file"); 
  
	oFile = fopen ("/home/sei/rawdata.bin","wb");
	if (oFile<=0) {
		ok_files = 0;
		printf("Error opening file");
		}  // end if ofile
	else
             printf("opened output file");


	if (ok_files==1) {
    

      		do {
        		n = 1;
	  		in = fgetc (iFile);
            		in = in & 0xFF;
			printf("input byte %X ", in);
           		while (in != EOF && n <= 4)
            			{  
              			if  (in >= 196)  
                   			out = 0xFD;
               			else if   (in >= 128) 
                          		out = 0xFF; 
                  		else if   (in >= 64)  
                             		out = 0x03;
  		    		else   out = 0x01;
	             		fputc ( out , oFile);
				printf("out%d %X ",n,out);
                     		in = in & 0x3F;
 	             		in << 2;
                     		n++;
            			}  /* end of while */
			printf("\n");
         		}  /* end of do loop */
   		while (in != EOF);
   		} // end of if ok_files

         fclose (iFile);
         fclose (oFile);
}  // end of main

---

### Post by Tony Flury on 2009-08-06
If you edit your post and use code tags then it preserve all the nice formatting - and get rid of the smileys.

Also it is not exactly clear to me what your code is actually trying to do - can you explan with an example of the input and what you expect the output should be ?

---

### Post by ericeclifford on 2009-08-06
sorry, this was my first program I ever written, I had helped to fix it.

 The EOF was not properly in, and the 196 was suppose to be a 192.

I debugged it and got it to work.

Sorry and I will post better for future code postings.

Also the in << 2; shift needed a = after the <<

I am excited I got my first program running !@ :0

---

