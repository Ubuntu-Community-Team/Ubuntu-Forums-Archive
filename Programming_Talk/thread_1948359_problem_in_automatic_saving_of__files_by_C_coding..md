---
title: "problem in automatic saving of  files by C coding."
date: 2012-03-28
forum: Programming Talk
---

### Post by sneha09 on 2012-03-28
):P hi..i am working on win xp and dev C++ IDE.
till now,i have done the following.

#include <stdio.h>
#include <stdlib.h>
 
main()
{
   int rename(const char *oldpath, const char *newpath);
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

This  program helps me to copy file from one place to another within the same  location where my EXE file is present.But i want a code in which i  don't have to enter source and target file name,instead of doing this, i just  have to define the path of the source folder (ex - D:\New folder) where those  files are being saved(This folder receive files from satellite every hour,that is why i can not give the file name). So when i run the program it automatically saves  the files present in that folder to the destination folder.Please help..i am just beginner in C.

---

### Post by CynicRus on 2012-03-28
```

#include <windows.h>

void Copy(LPCTSTR szInDirName, LPCTSTR szOutDirName, bool flag = false)
{
    WIN32_FIND_DATA ffd;
    HANDLE hFind;

    TCHAR szFind[MAX_PATH + 1];
    TCHAR szInFileName[MAX_PATH + 1];
    TCHAR szOutFileName[MAX_PATH + 1];

    lstrcpy(szFind, szInDirName);
    lstrcat(szFind, "\\*.*"); //find any files

    hFind = FindFirstFile(szFind, &ffd);

    do
    {
        //format path
        lstrcpy(szInFileName, szInDirName);
        lstrcat(szInFileName, "\\");
        lstrcat(szInFileName, ffd.cFileName);

        //format result
        lstrcpy(szOutFileName, szOutDirName);
        lstrcat(szOutFileName, "\\");
        lstrcat(szOutFileName, ffd.cFileName);

        if(flag) //&#1077;&#1089;&#1083;&#1080; flag == true, copy only files
        {
            if(ffd.dwFileAttributes & 0x00000010)
            {
                if(lstrcmp(ffd.cFileName, ".") == 0 ||
                    lstrcmp(ffd.cFileName, "..") == 0) continue;

                CreateDirectory(szOutFileName, NULL);
                Copy(szInFileName, szOutFileName);
            }
        } //otherwise, skip folders
        else
            if(ffd.dwFileAttributes & 0x00000010) continue;

        CopyFile(szInFileName, szOutFileName, TRUE);
    }
    while(FindNextFile(hFind, &ffd));

    FindClose(hFind);
}

int main()
{
    //At the end of the folder paths do not need to add "\"
    Copy("C:\\1", "C:\\2", true); //if subdirectory include for copy
    Copy("C:\\1", "C:\\2"); //only files
}

```
if i understand the problem.

---

### Post by sneha09 on 2012-03-28
Thanks for replying first of all !! But can u please tell me that how does it work? i mean where in this program i need to give source folder and destination folder's path? This program is too difficult for me to understand,cause i am learning C. 
Let me again explain my problem ...suppose i have a source folder located in (D:\new folder),this is the location where all the files are being stored.
i want these files to be copied to another location (C:\program files\data files) . i want this as automatic process...
i mean i don't want to give file name every hour.The moment files come in D disk,it automatically gets copied in Disk C. Hope you are understanding.

---

### Post by CynicRus on 2012-03-28
You want to specify a directory one time, and the program will be every hour to synchronize two directories?

---

### Post by sneha09 on 2012-03-28
> **CynicRus said:**
> You want to specify a directory one time, and the program will be every hour to synchronize two directories?
yes...i want to specify it one time only in the code. So whenever a file is received in the source folder through satellite, the program automatically runs.. and that file is saved in the destination folder.

---

### Post by CynicRus on 2012-03-28
```
#include <windows.h>
#include <stdlib.h>
#include <stdio.h>
#include <tchar.h>
DWORD dwThreadId,dwThreadFN;//thread id
//copy file thread
DWORD WINAPI CopyFuncThread(LPVOID lpCOM);

//directory watch
DWORD WINAPI ChangeNotyfic(LPVOID)
{
HANDLE hd;
hd = FindFirstChangeNotification("C:\\dir", TRUE, FILE_NOTIFY_CHANGE_FILE_NAME);
if (hd == INVALID_HANDLE_VALUE){ShowMessage("can't do it");return 0;}
do
{
if(WaitForSingleObject(hd,INFINITE)==WAIT_OBJECT_0)
//ShowMessage("catch change");
Copy("C:\\dir", "D:\\new_dir", true); //if subdirectory include for copy
}
while(FindNextChangeNotification(hd));
FindCloseChangeNotification(hd);
return 1;
}

//file copy, using winapi
//Get input and output dir path
//if flag - true, cpoying dir with subdirs
//else - only files
void Copy(LPCTSTR szInDirName, LPCTSTR szOutDirName, bool flag = false)
{
    WIN32_FIND_DATA ffd;
    HANDLE hFind;

    TCHAR szFind[MAX_PATH + 1];
    TCHAR szInFileName[MAX_PATH + 1];
    TCHAR szOutFileName[MAX_PATH + 1];

    lstrcpy(szFind, szInDirName);
    lstrcat(szFind, "\\*.*"); //find any files

    hFind = FindFirstFile(szFind, &ffd);

    do
    {
        //format path
        lstrcpy(szInFileName, szInDirName);
        lstrcat(szInFileName, "\\");
        lstrcat(szInFileName, ffd.cFileName);

        //format result
        lstrcpy(szOutFileName, szOutDirName);
        lstrcat(szOutFileName, "\\");
        lstrcat(szOutFileName, ffd.cFileName);

        if(flag) //if flag == true, copy only files
        {
            if(ffd.dwFileAttributes & 0x00000010)
            {
                if(lstrcmp(ffd.cFileName, ".") == 0 ||
                    lstrcmp(ffd.cFileName, "..") == 0) continue;

                CreateDirectory(szOutFileName, NULL);
                Copy(szInFileName, szOutFileName);
            }
        } //otherwise, skip folders
        else
            if(ffd.dwFileAttributes & 0x00000010) continue;

        CopyFile(szInFileName, szOutFileName, TRUE);
    }
    while(FindNextFile(hFind, &ffd));

    FindClose(hFind);
}

DWORD WINAPI ThreadFunc(LPVOID lpCOM)
{
          for(;;)
     {
        Sleep(3600000);
         Copy("C:\\dir", "D:\\new_dir", true); //if subdirectory include for copy
         //Copy("C:\\1", "C:\\2"); //only files
        printf("Copy\n");
     }
}

int main()
{
 CreateThread(NULL,0,CopyFuncThread,NULL,0,&dwThreadId);
 CreateThread(NULL,0,ChangeNotyfic,0,0,&dwThreadFN);
 Sleep(INFINITE);
 return 0;
    
}
```The program hangs in an endless loop, creates a second thread - which is every hour synchronizes two directories. Copying files is implemented using the functional WINAPI. Check unfortunately I can not, because I do not have windows-( 
PS: I have not used WINAPI Timer, because - not sure if it will work in win32console.

UPD: Now, even watching a directory on a separate thread, and in the event of a change in the source - copy file of  in target dir.

---

### Post by sneha09 on 2012-03-29
> **CynicRus said:**
> ```
#include <windows.h>
#include <stdlib.h>
#include <stdio.h>
#include <tchar.h>
DWORD dwThreadId,dwThreadFN;//thread id
//copy file thread
DWORD WINAPI CopyFuncThread(LPVOID lpCOM);

//directory watch
DWORD WINAPI ChangeNotyfic(LPVOID)
{
HANDLE hd;
hd = FindFirstChangeNotification("C:\\dir", TRUE, FILE_NOTIFY_CHANGE_FILE_NAME);
if (hd == INVALID_HANDLE_VALUE){ShowMessage("can't do it");return 0;}
do
{
if(WaitForSingleObject(hd,INFINITE)==WAIT_OBJECT_0)
//ShowMessage("catch change");
Copy("C:\\dir", "D:\\new_dir", true); //if subdirectory include for copy
}
while(FindNextChangeNotification(hd));
FindCloseChangeNotification(hd);
return 1;
}

//file copy, using winapi
//Get input and output dir path
//if flag - true, cpoying dir with subdirs
//else - only files
void Copy(LPCTSTR szInDirName, LPCTSTR szOutDirName, bool flag = false)
{
    WIN32_FIND_DATA ffd;
    HANDLE hFind;

    TCHAR szFind[MAX_PATH + 1];
    TCHAR szInFileName[MAX_PATH + 1];
    TCHAR szOutFileName[MAX_PATH + 1];

    lstrcpy(szFind, szInDirName);
    lstrcat(szFind, "\\*.*"); //find any files

    hFind = FindFirstFile(szFind, &ffd);

    do
    {
        //format path
        lstrcpy(szInFileName, szInDirName);
        lstrcat(szInFileName, "\\");
        lstrcat(szInFileName, ffd.cFileName);

        //format result
        lstrcpy(szOutFileName, szOutDirName);
        lstrcat(szOutFileName, "\\");
        lstrcat(szOutFileName, ffd.cFileName);

        if(flag) //if flag == true, copy only files
        {
            if(ffd.dwFileAttributes & 0x00000010)
            {
                if(lstrcmp(ffd.cFileName, ".") == 0 ||
                    lstrcmp(ffd.cFileName, "..") == 0) continue;

                CreateDirectory(szOutFileName, NULL);
                Copy(szInFileName, szOutFileName);
            }
        } //otherwise, skip folders
        else
            if(ffd.dwFileAttributes & 0x00000010) continue;

        CopyFile(szInFileName, szOutFileName, TRUE);
    }
    while(FindNextFile(hFind, &ffd));

    FindClose(hFind);
}

DWORD WINAPI ThreadFunc(LPVOID lpCOM)
{
          for(;;)
     {
        Sleep(3600000);
         Copy("C:\\dir", "D:\\new_dir", true); //if subdirectory include for copy
         //Copy("C:\\1", "C:\\2"); //only files
        printf("Copy\n");
     }
}

int main()
{
 CreateThread(NULL,0,CopyFuncThread,NULL,0,&dwThreadId);
 CreateThread(NULL,0,ChangeNotyfic,0,0,&dwThreadFN);
 Sleep(INFINITE);
 return 0;
    
}
```The program hangs in an endless loop, creates a second thread - which is every hour synchronizes two directories. Copying files is implemented using the functional WINAPI. Check unfortunately I can not, because I do not have windows-( 
PS: I have not used WINAPI Timer, because - not sure if it will work in win32console.

UPD: Now, even watching a directory on a separate thread, and in the event of a change in the source - copy file of  in target dir.
Thanks...but It means i need to learn  WINAPI as well for it? Whole project is about copying  files automatically to destination and there's another thing i have to do ...its automatic conversion of those source 'TEXT' files into 'EXCEL' while saving. 
so what do i need to do..learn WINAPI? Or doing this project in any other language which makes it easier for me. any advice?????

---

### Post by CynicRus on 2012-03-29
If you need programming for windows - learn winapi, for *nix - learn POSIX. If you need just synchronize two directory use -  Microsoft SyncToy.

---

### Post by sneha09 on 2012-03-29
> **CynicRus said:**
> If you need programming for windows - learn winapi, for *nix - learn POSIX. If you need just synchronize two directory use -  Microsoft SyncToy.
thank you for letting me know. I know i am  costing you a lot of brain cycles. But Can you please tell me about SyncToy...does it copy files automatically from one location to other.I mean if i have a folder in D drive,then will it automatically copy that folder in C ??????i just have to specify the source and target location for once and those files whenever received in source folder, automatically transferred to Target disk like C,E...

---

### Post by CynicRus on 2012-03-29
Yep.
[http://www.techrepublic.com/blog/project-management/configure-automated-backups-using-synctoy-and-windows-7s-scheduled-task/4292](http://www.techrepublic.com/blog/project-management/configure-automated-backups-using-synctoy-and-windows-7s-scheduled-task/4292)

---

### Post by sneha09 on 2012-03-29
> **CynicRus said:**
> Yep.
[http://www.techrepublic.com/blog/project-management/configure-automated-backups-using-synctoy-and-windows-7s-scheduled-task/4292](http://www.techrepublic.com/blog/project-management/configure-automated-backups-using-synctoy-and-windows-7s-scheduled-task/4292)
Dhanyavaad (Thanks) :D :D

---

### Post by sneha09 on 2012-03-29
> **sneha09 said:**
> Dhanyavaad (Thanks) :D :D
hey i have downloaded that software..but i have to run it everytime. If i am adding any file to source ,it doesn't get copied automatically to target folder,but i have to click on Run everytime. I want something that senses the new files in source folder and automatically transfers it to target folder. Does it work like this also?

---

### Post by CynicRus on 2012-03-29
just start task every minutes...or 30 sec

---

### Post by sneha09 on 2012-03-30
> **CynicRus said:**
> just start task every minutes...or 30 sec
sorry i didn't get what u said...please explain. is there any option in the software that will start this task every 30 sec or 1 minute??????

---

