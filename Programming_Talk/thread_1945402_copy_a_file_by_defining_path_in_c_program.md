---
title: "copy a file by defining path in c program"
date: 2012-03-23
forum: Programming Talk
---

### Post by sneha09 on 2012-03-23
I am working on a C program to copy file from location to another.The program i have mentioned below is running successfully,but only when i keep my source and target files open side by side. 
I want to modify this program in such a way..that it copies the file without any need to open it and i just define the path of source and target file (ex- C:\\program files\\new folder..) in the program itself and the file gets copied.Please help...Program is:

#include <stdio.h>
#include <stdlib.h>
 
main()
{
   char ch, source_file[20], target_file[20];
   FILE *source, *target;
 
   printf("Enter name of file to copy\n");
   gets(source_file);
 
   source = fopen(source_file, "r");
 
   if( source == NULL )
   {
      printf("Press any key to exit...\n");
      exit(EXIT_FAILURE);
   }
 
   printf("Enter name of target file\n");
   gets(target_file);
 
   target = fopen(target_file, "w");
 
   if( target == NULL )
   {
      fclose(source);
      printf("Press any key to exit...\n");
      exit(EXIT_FAILURE);
   }
 
   while( ( ch = fgetc(source) ) != EOF )
      fputc(ch, target);
 
   printf("File copied successfully.\n");
 
   fclose(source);
   fclose(target);
 
   return 0;
}

---

### Post by Bachstelze on 2012-03-23
This is probably going to be OS-dependent, so I suggest you ask somewhere else. As you were already told, this forum is Linux-centered, and while questions about other OSes are allowed in Programming Talk, this is probably not the place where you have the best chances of getting an answer.

---

### Post by ofnuts on 2012-03-23
> **sneha09 said:**
> I am working on a C program to copy file from location to another.The program i have mentioned below is running successfully,but only when i keep my source and target files open side by side. 
I want to modify this program in such a way..that it copies the file without any need to open it and i just define the path of source and target file (ex- C:\\program files\\new folder..) in the program itself and the file gets copied.Please help...

You can't copy a file without reading it, and you can't read it without opening it. Or you use a CP command under the hood, but something is still opening the file. What are you trying to achieve?

---

### Post by CynicRus on 2012-03-23
and in windows console - spaces in path can't reading, use path: C:\program /files\etc..

---

### Post by sneha09 on 2012-03-24
> **ofnuts said:**
> You can't copy a file without reading it, and you can't read it without opening it. Or you use a CP command under the hood, but something is still opening the file. What are you trying to achieve?

thanxx...
Actually i have to relocate a file from one location to another. when i am running my program i have to open the source file.but i want to copy it just by specifying its location in the program..at present my program asks for the file name during execution,but i want to program it in a way that i define the location of source file and target file in the program itself. so that it copies the file without any need of opening source file.  i hope you are understanding.please send modifications in the above mentioned program...

---

### Post by ofnuts on 2012-03-25
> **sneha09 said:**
> thanxx...
Actually i have to relocate a file from one location to another. when i am running my program i have to open the source file.but i want to copy it just by specifying its location in the program..at present my program asks for the file name during execution,but i want to program it in a way that i define the location of source file and target file in the program itself. so that it copies the file without any need of opening source file.  i hope you are understanding.please send modifications in the above mentioned program...Generating the file name in the program will never exempt you from opening it if you need to access the file data (whihc you have to do to copy the file). However, if you are "relocating" the file within the same filesystem, you don't need to copy it, just use 
```

int rename(const char *oldpath, const char     *newpath);

```

---

### Post by sneha09 on 2012-03-26
> **ofnuts said:**
> Generating the file name in the program will never exempt you from opening it if you need to access the file data (whihc you have to do to copy the file). However, if you are "relocating" the file within the same filesystem, you don't need to copy it, just use 
```

int rename(const char *oldpath, const char     *newpath);


```

Hey thanks a ton!! It works ! Now I am close to what i wanna achieve. Till now,what i have done is...


#include <stdio.h>
#include <stdlib.h>
 
main()
{
**int rename(const char *oldpath, const char *newpath);**
   char ch, source_file[20], target_file[20];
   FILE *source, *target;
 
   printf("Enter name of file to copy\n");
   gets(source_file);
 
   source = fopen(source_file, "r");
 
   if( source == NULL )
   {
      printf("Press any key to exit...\n");
      exit(EXIT_FAILURE);
   }
 
   printf("Enter name of target file\n");
   gets(target_file);
 
   target = fopen(target_file, "w");
 
   if( target == NULL )
   {
      fclose(source);
      printf("Press any key to exit...\n");
      exit(EXIT_FAILURE);
   }
 
   while( ( ch = fgetc(source) ) != EOF )
      fputc(ch, target);
 
   printf("File copied successfully.\n");
 
   fclose(source);
   fclose(target);
 
   return 0;
}

after running this program,i dont have  to keep my source and target files open in the side window. I just fill up the names of files and the files are copied.Thanks to you for that!!!
But next thing i wanna ask is that..can i modify it so that now i just give the location and name of the file  somewhat like=(ex- fopen(C:\\programfiles\\File1.cpp)and it gets copied..??
I am beginner in C..so please excuse me for lack of understanding in it.

---

### Post by ofnuts on 2012-03-26
> **sneha09 said:**
> Hey thanks a ton!! It works ! Now I am close to what i wanna achieve. Till now,what i have done is...


#include <stdio.h>
#include <stdlib.h>
 
main()
{
**int rename(const char *oldpath, const char *newpath);**
   char ch, source_file[20], target_file[20];
   FILE *source, *target;
 
   printf("Enter name of file to copy\n");
   gets(source_file);
 
   source = fopen(source_file, "r");
 
   if( source == NULL )
   {
      printf("Press any key to exit...\n");
      exit(EXIT_FAILURE);
   }
 
   printf("Enter name of target file\n");
   gets(target_file);
 
   target = fopen(target_file, "w");
 
   if( target == NULL )
   {
      fclose(source);
      printf("Press any key to exit...\n");
      exit(EXIT_FAILURE);
   }
 
   while( ( ch = fgetc(source) ) != EOF )
      fputc(ch, target);
 
   printf("File copied successfully.\n");
 
   fclose(source);
   fclose(target);
 
   return 0;
}

after running this program,i dont have  to keep my source and target files open in the side window. I just fill up the names of files and the files are copied.Thanks to you for that!!!
But next thing i wanna ask is that..can i modify it so that now i just give the location and name of the file  somewhat like=(ex- fopen(C:\\programfiles\\File1.cpp)and it gets copied..??
I am beginner in C..so please excuse me for lack of understanding in it.


Your code doesn't use the function I hinted... it only declares it (and improperly). See "man 2 rename".

But I think there is a problem of vocabulary here. What do you mean by "keep my source and target files open in the side window"? What has this got to do with your C code? What do you really mean by "open"?

---

### Post by sneha09 on 2012-03-26
> **ofnuts said:**
> Your code doesn't use the function I hinted... it only declares it (and improperly). See "man 2 rename".

But I think there is a problem of vocabulary here. What do you mean by "keep my source and target files open in the side window"? What has this got to do with your C code? What do you really mean by "open"?

sory..''i dont have  to keep my source and target files open in the side window'' By this i meant that initially (before using this,int rename(const char *oldpath, const char     *newpath);when i compiled it , it stopped running after entering the source name).But when i kept the source 'file1'and target 'file2' open in the Dev C compiler(screen where we write code,)..it copied successfully.
Its just like i am writing 3 programs on DEV.thats what i have done,To open these files ; i clicked DEV -->Wrote my code mentioned already-->clicked on Files-->Open files-->>browse file name...and then compiled my code--->Run.
AFTER USING THE ABOVE CODE,i don't have to open those files.I hope ,Now i am able to make you understand.

---

### Post by ofnuts on 2012-03-26
> **sneha09 said:**
> sory..''i dont have  to keep my source and target files open in the side window'' By this i meant that initially (before using this,int rename(const char *oldpath, const char     *newpath);when i compiled it , it stopped running after entering the source name).But when i kept the source 'file1'and target 'file2' open in the Dev C compiler(screen where we write code,)..it copied successfully.
Its just like i am writing 3 programs on DEV.thats what i have done,To open these files ; i clicked DEV -->Wrote my code mentioned already-->clicked on Files-->Open files-->>browse file name...and then compiled my code--->Run.
AFTER USING THE ABOVE CODE,i don't have to open those files.I hope ,Now i am able to make you understand.No...

Let's separate issues... you are mixing up problems with your IDE, problems in your source code, understanding of file handling.... I don't even know what DEV is... Are you writing this code on a Linux system or are you on Windows? Can you run your executable outside of your development environment?

---

### Post by sneha09 on 2012-03-27
> **ofnuts said:**
> No...

Let's separate issues... you are mixing up problems with your IDE, problems in your source code, understanding of file handling.... I don't even know what DEV is... Are you writing this code on a Linux system or are you on Windows? Can you run your executable outside of your development environment?
I am using windows to write my code,Dev-C++ is an IDE for the C/C++ programming language.

---

### Post by ofnuts on 2012-03-27
> **sneha09 said:**
> I am using windows to write my code,Dev-C++ is an IDE for the C/C++ programming language.OK, so after compilation you should have a .EXE file, and you can start a command prompt and run the .EXE from it. And this .EXE should work whether DEV-C++ is started or not.

---

### Post by sneha09 on 2012-03-27
> **ofnuts said:**
> OK, so after compilation you should have a .EXE file, and you can start a command prompt and run the .EXE from it. And this .EXE should work whether DEV-C++ is started or not.
Thank you!!!!!!!! You have been very Patient and Kind to me.Actually i have just basic knowledge of C and still i have been given a C program that includes: 
1)
copy a file from one location to another.
2) changing the extension of files from text to excel.
3) Automatic transferring of these files without need of entering the name of files,because my system will be receiving files from satellite every hour.So i just will need to define the location of Folder in the program; where these files will be received and stored.

---

