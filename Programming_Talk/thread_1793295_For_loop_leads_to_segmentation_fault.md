---
title: "For loop leads to segmentation fault"
date: 2011-06-29
forum: Programming Talk
---

### Post by sakishrist on 2011-06-29
Hello everyone,

I would like a little help with some code of mine. The problem is not just what is written at the title of the thread, there is some more. 

First of all, here is the code  (if you need to know what the file that I process contains, then I will post that information too):
```
#include <iostream>
#include <zlib.h>
#include <fstream>

using namespace std;

z_stream z;

int _decompress(Bytef * in_data, long in_size, Bytef * out_data, long * out_size){

    int status;
    
    z.avail_in = in_size;
    z.next_in = in_data;
    
    z.avail_out = *out_size;
    z.next_out = out_data;

    status = inflateInit(&z);   **[COLOR=Red] //SEGMENTATION FAULT[/COLOR]**

    if ( status != Z_OK )
        return status;
    
    if ( z.avail_in != 0 && *out_size != 0 ) {
        status = inflate( &z, Z_NO_FLUSH );    **[COLOR=Red]//SEGMENTATION FAULT[/COLOR]**
        if ( status < 0 ){
            cout << "Error: " << status << endl;
            return -11;
        }
        else if ( status == Z_OK && *out_size > 0 ){
            cout << "Not enough output space!\n";
            return -12;
        }

    }else if( *out_size != 0 ){
        cout << "No input?\n";
        return -10;
    }
    
    while ( status == Z_OK  ) {
        
        *out_size += 1024;
        z.avail_out = *out_size;
        delete out_data;
        out_data = new Bytef[*out_size];
        z.next_out = out_data;
        
        status = inflate( &z, Z_NO_FLUSH );    **[COLOR=Red]//SEGMENTATION FAULT[/COLOR]**
    }
    
    if ( status != Z_STREAM_END );
        cout << "Final Error: " << status << endl;

    (void)inflateEnd(&z);
    
    return status;
} 



int main(){
    ifstream fp_in;
    fp_in.open("r.0.0.mcr", ios::in);
    
    char *a = new char[5]; 


    for(int i = 0; i<1024; i++){ 
        
        fp_in.seekg(i*4);
        fp_in.read(a, 4); 
        cout << i << ":";
        
        if((int)a[0]!=0 || (int)a[1]!=0 || (int)a[2]!=0 || (int)a[3]!=0){
            
            cout     << (i+1)%32 
                    << "x" 
                    << (i+1)/32 
                    << " ( Pos: " 
                    << (  (int)(unsigned char)a[0]*65536 
                        + (int)(unsigned char)a[1]*255 
                        + (int)(unsigned char)a[2]            )*4096 
                    << " Size: ";

            fp_in.seekg((      (int)(unsigned char)a[0]*65536 
                             + (int)(unsigned char)a[1]*256 
                             + (int)(unsigned char)a[2]            )*4096);
            

            fp_in.read(a,5);

            long size =   (int)(unsigned char)a[0]*16777216 
                        + (int)(unsigned char)a[1]*65536 
                        + (int)(unsigned char)a[2]*256 
                        + (int)(unsigned char)a[3];
            
            cout << (int)(unsigned char)a[0] << ":" ;        **[COLOR=Red]//PROBLEM WITH COUT[/COLOR]**
            cout << (int)(unsigned char)a[1] << ":" ;
            cout << (int)(unsigned char)a[2] << ":" ;
            cout << (int)(unsigned char)a[3] << " = "; 
            cout << size << " ) \t:";

            char *buff = new char[size-1];

            long out_size = 0; 
            Bytef *out;
            
            fp_in.read(buff,size-1);
            int status = _decompress((Bytef*)buff,size-1,out,&out_size);

            if(status>=0)
                cout << "Decompressed size: " << out_size << " bytes.";
            else
                cout << "Error: " << status;
        }
        cout << endl;
    }

    for(int i = 0; i<1024; i++)        **[COLOR=Red]//SEGMENTATION FAULT[/COLOR]**
        cout << "Anything";

    
    fp_in.close();

    return 0;
}
```So, here are the problems I have

1) [Solved] [s]I do not understand why I can not put ***z_stream z; ***inside the ***int _decompress*** function. If I do, the 3 methods inside it that have the "segmentation fault" comment produce that kind of error (during runtime.)[/s]

2) At the five lines with the "Problem with cout" comment, if I attempt to do that in one line I get a weird error that I think is from zlib, and not g++.

3) At the end, there is a for loop. That loop produces a Segmentation Fault as well. If I remove it, everything is fine. I also tried to remove all the contents of the for loop above it. The Segmentation Fault is gone then as well.

I appreciate any help with any of these problems!

Thanks in advance!

---

### Post by GeneralZod on 2011-06-29
> **sakishrist said:**
> 
1) I do not understand why I can not put ***z_stream z; ***inside the ***int _decompress*** function. If I do, the 3 methods inside it that have the "segmentation fault" comment produce that kind of error (during runtime.)


A struct defined at global scope will be automatically zero-initialised; one defined in a function body will not.  Zero-initialising will presumably set zalloc and zfree to NULL rather than the undefined values they will have if they are not zero-initialised (note that the zlib docs state that zalloc and zfree *must* be set prior to the call to inflateInit(...), and that NULL is an acceptable value for them.)

Edit:

Also, "out" doesn't seem to be initialised inside main().

---

### Post by sakishrist on 2011-06-29
Thanks a lot!!! I didn't know that.

Now the first error is gone. :)

---

### Post by sakishrist on 2011-06-29
I narrowed down problem 3 to the first three lines that have the "Segmentation fault" comment. I am really lost here. I either have to delete the for loop or to delete those three lines for the code to execute without any runtime errors. 

Well, I guess that might mean it's something to do with zlib but ... 

That is really strange. :(

---

### Post by sakishrist on 2011-06-29
Well, it seams that the last two errors happen because I try ***delete out_data; ***when it is not initialized. 

But I still don't get it why this problem occurs when I have that long ***cout*** or the ***for*** loop.

---

### Post by GeneralZod on 2011-06-29
> **sakishrist said:**
> Well, it seams that the last two errors happen because I try ***delete out_data; ***when it is not initialized. 


That's what I said :)

Also, you want to use delete[] when deleting arrays.

> 
But I still don't get it why this problem occurs when I have that long ***cout*** or the ***for*** loop.

delete'ing an uninitialised pointer is [Undefined Behaviour](http://en.wikipedia.org/wiki/Undefined_behaviour).  It can screw up immediately, or at an arbitrary point in the future (including not at all).  If you want a concrete reason why it crashes when executing this (apparently unrelated) cout code: it probably tramples over some important bit of memory that cout relies on to be untrampled, or something.

---

### Post by sakishrist on 2011-06-29
Oh ... I didn't see that, sorry. 

Thanks a million!

---

### Post by sakishrist on 2011-06-29
> **GeneralZod said:**
> Also, you want to use delete[] when deleting arrays.
That gave me an error: ```
zlib.cpp: In function ‘int _decompress(Bytef*, long int, Bytef*, long int*)’:
zlib.cpp:51:19: error: expected primary-expression before ‘]’ token

```

---

### Post by GeneralZod on 2011-06-29
> **sakishrist said:**
> That gave me an error: ```
zlib.cpp: In function ‘int _decompress(Bytef*, long int, Bytef*, long int*)’:
zlib.cpp:51:19: error: expected primary-expression before ‘]’ token

```

Are you doing

```

delete[] out_data;

```

?

---

