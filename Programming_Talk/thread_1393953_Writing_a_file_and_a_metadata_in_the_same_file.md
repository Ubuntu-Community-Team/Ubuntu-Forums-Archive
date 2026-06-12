---
title: "Writing a file and a metadata in the same file"
date: 2010-01-30
forum: Programming Talk
---

### Post by DiegoTc on 2010-01-30
Hi everyone again.
I am trying another file exercise in c++
This one goes like this.
I have the following file video.mp4
I want to copy this video.mp4 to a file name hard.DTC.
But also I want to add the size of the file and the name of the user name of the computer. So I think i right what I did
```

#include <cstdio>
#include <iostream>
#include <unistd.h>
#include <string>
#include <stdio.h>
#include <stdlib.h>

using namespace std;
int main(){[COLOR="Red"]
 int buffer_size=4096;
 char *buffer=new char[buffer_size];
 char *name=new char[25];

  name = getenv ("LOGNAME");

 FILE *orig=fopen("BarcampUNITEC20UsingUbuntuinUniversity.mp4","rb");
 FILE *dest=fopen("DiegoTc.DTC","a");
    int tamano=ftell(orig);
    fwrite(name,1,25,dest);
    fwrite(&tamano,1,4,dest);
    while(!feof(orig)){
        int leido=fread(buffer,1,buffer_size,orig);
        fwrite(buffer,1,leido,dest);
    }
    fclose(orig);
    fclose(dest);
    cout<<"se ejecuto\n";[/COLOR]

//----------------------------------------------------
    char *names=new char [25];
    char *buffer1=new char[buffer_size];
 FILE *origen=fopen("DiegoTc.DTC","r");
 FILE *destino=fopen("copy.mp4","w");
    int tamano1=ftell(orig);
    fread(names,1,25,origen);
    cout<<names;
    fread(&tamano1,1,4,origen);
    cout<<tamano1;
    while(!feof(orig)){
        int leido=fread(buffer1,1,buffer_size,origen);
        fwrite(buffer1,1,leido,destino);
    }
    fclose(orig);
    fclose(dest);
    cout<<"se ejecuto\n";



```  
The red part of the code is the first part.
I think thats fine what i did. But now on the same program, I want to open DiegoTc.DTC and write a new file with only the mp4 with the name other.mp4

The black part of the code is that

When i go check the DiegoTc.DTC creteas with the size of the video. But on the second part it saids to me segmentation default

---

