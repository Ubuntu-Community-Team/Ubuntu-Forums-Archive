---
title: "problem with working with firstfind() in C++"
date: 2010-07-08
forum: Programming Talk
---

### Post by bahador.saket on 2010-07-08
[SIZE=2]I want to find files name that are included in a specific  address. 

for example:
   I want to get file names that are  existed in "c:\myproject" 

I have searched on internet and I  found this part of code but unfortunately I do not know how to show the  list of files. 
       

        HANDLE hFind;
        BOOL  bContinue = TRUE;
        WIN32_FIND_DATA data;

        hFind =  FindFirstFile("szCurDir\*.*", &data);
        // If we have no  error, loop thru the files in this  dir
        while (hFind && bContinue) 
         {
                  bContinue = FindNextFile(hFind, &data);
         }
         FindClose(hFind); // Fre[/SIZE]

---

### Post by PaulM1985 on 2010-07-08
I found this really useful for dealing with files in Linux C/C++ programs.  This is a C lib but you will be able to use it in your C++ app.

Paul

---

### Post by Milliways on 2010-07-08
> **bahador.saket said:**
> [SIZE=2]I want to find files name that are included in a specific  address. 

for example:
   I want to get file names that are  existed in "c:\myproject" 

I have searched on internet and I  found this part of code but unfortunately I do not know how to show the  list of files. 
       

        HANDLE hFind;
        BOOL  bContinue = TRUE;
        WIN32_FIND_DATA data;

        hFind =  FindFirstFile("szCurDir\*.*", &data);
        // If we have no  error, loop thru the files in this  dir
        while (hFind && bContinue) 
         {
                  bContinue = FindNextFile(hFind, &data);
         }
         FindClose(hFind); // Fre[/SIZE]

This is obviously an incomplete code snippet from a windows program.
I doubt it would work - "szCurDir\*.*" doesn't seem right.

However, It is easy to access the WIN32_FIND_DATA structure to get details of the found files.

The following code snippet from one of my programs gets the file attributes:-

```

    hFindFile = FindFirstFile(szwFindPath, &FindFileData);  // First search supplied path
    if(hFindFile!=INVALID_HANDLE_VALUE)
    {
	mCreationTime = FindFileData.ftCreationTime;
	mLastWriteTime = FindFileData.ftLastWriteTime;
	mLastAccessTime = FindFileData.ftLastAccessTime;
	mFileSizeHigh = FindFileData.nFileSizeHigh;
	mFileSizeLow = FindFileData.nFileSizeLow;
	mFileAttributes = FindFileData.dwFileAttributes;
	FindClose(hFindFile);
	return true;
    }

```

---

### Post by PaulM1985 on 2010-07-09
Just realized I replied earlier without actually pasting a link into the post.

Here it is:

[http://www.gnu.org/s/libc/manual/html_node/File-System-Interface.html#File-System-Interface](http://www.gnu.org/s/libc/manual/html_node/File-System-Interface.html#File-System-Interface)

Sorry.

Paul

---

