---
title: "[C++] Vector &amp; segmentation fault !"
date: 2009-07-05
forum: Programming Talk
---

### Post by credobyte on 2009-07-05
I've a string vector which contains full paths to all files, collected in process of reading directory contents recursively.
When I try to read /home directory, I get like 1500 files and everything works just great, but, if I try to read /, "segmentation fault" error comes up and application exits.

First idea was that int ( used to loop trough my vector elements ) might be too short for this operation, tough, it's not ( double & long still returns segmentation fault ).

Any ideas ? What could be the reason of this "error" ?

```
vector<string> filelist;
``````
for (int i = 0; i < filelist.size(); i++) {
     cout << i << ": " << filelist[i] << endl;
}
```

---

### Post by MadCow108 on 2009-07-05
how big is the size?
maybe you're running out of memory
try catching the exception
```

 try
  {
    //vector filling
  }
  catch (exception& e)
  {
//will probably be a bad_alloc exception
    cout << e.what() << endl;
  }

```

you could also use the .at() operator of vector which does boundary checking and throws exceptions to debug

---

### Post by fr4nko on 2009-07-05
It is difficult to say anything if you don't include your code. The fragment you've included look ok.

Francesco

---

### Post by credobyte on 2009-07-05
> **MadCow108 said:**
> how big is the size?
maybe you're running out of memory
try catching the exception

you could also use the .at() operator of vector which does boundary checking and throws exceptions to debug

```
try {
    filelist.push_back(full_path);
} catch (exception &e) {
    cout << e.what() << endl;
}
``````
dainis@credobyte:~/Programm&#275;šana/Cpp$ ./main
Segmentation fault
```Even with try/catch it gives me a plain "segmentation fault" ( no additional error messages or warnings ) :(

---

### Post by MadCow108 on 2009-07-05
then your bug is somewhere else in the code

---

### Post by credobyte on 2009-07-05
Ok, here's the code ! Any ideas ?

```
#include <iostream>
#include <string>
#include <dirent.h>
#include <string.h>
#include <vector>

using namespace std;

// declare functions
void scandir(string basedir);
void show_filelist();

// declare global variables
unsigned char isFolder = 0x4;
unsigned char isFile = 0x8;
vector<string> filelist;

int main()
{
    scandir("/");
    show_filelist();
    return 0;
}

void scandir(string basedir)
{
    DIR *dhandle;
    struct dirent *dentry;
    
    dhandle = opendir(basedir.c_str());
    
    while ((dentry = readdir(dhandle)) != NULL) {
        if (strcmp(dentry->d_name, ".") != 0 && strcmp(dentry->d_name, "..") != 0) {
            string full_path = basedir + dentry->d_name;
            
            if (dentry->d_type == isFolder) {
                string cpath = full_path + "/";
                scandir(cpath);
            } else {
                try {
                    filelist.push_back(full_path);
                } catch (exception& e) {
                    cout << e.what() << endl;
                }
            }
            
        }
    }
}

void show_filelist()
{
    cout << "Vector contains " << filelist.size() << " elements : \n";
    
    for (int i = 0; i < filelist.size(); i++) {
        cout << i << ": " << filelist[i] << endl;
    }
}

```

---

### Post by MadCow108 on 2009-07-05
youre not checking if dhandle = opendir(basedir.c_str()); was successful
so it currently probably fails because you haven't got read permissions on every folder in root

also your not closing the directory with closedir(handle)
so you probably also get t"too many open files" errors

---

### Post by credobyte on 2009-07-05
> **MadCow108 said:**
> youre not checking if dhandle = opendir(basedir.c_str()); was successful
so it currently probably fails because you haven't got read permissions on every folder in root

also your not closing the directory with closedir(handle)
so you probably also get t"too many open files" errors

Excellent ! Works like a charm ( and yes, there was a problem with read permissions for the first 5-10 directories ).
Woops, I'm not really sure why closedir() is not where it should be ( probably deleted ), but .. thnx again - added :)

---

### Post by fr4nko on 2009-07-05
For the moment the only problem I see is that you put everything on the stack with a recursive functions. Probably, since you have a lot of files in / you encour in a stack overflow.

Your code does not works on my system, I believe your definition for 'isFolder' is not ok.

Francesco

---

### Post by credobyte on 2009-07-05
> **fr4nko said:**
> For the moment the only problem I see is that you put everything on the stack with a recursive functions. Probably, since you have a lot of files in / you encour in a stack overflow.

Your code does not works on my system, I believe your definition for 'isFolder' is not ok.

Francesco

Updated code should work ( would be nice if you could try it & report back ) :) Also, how to get around to this so called "stack overflow" ?

```
#include <iostream>
#include <string>
#include <dirent.h>
#include <errno.h>
#include <string.h>
#include <vector>

using namespace std;

// declare functions
void scandir(string basedir);
void show_filelist();

// declare global variables
unsigned char isFolder = 0x4;
unsigned char isFile = 0x8;
vector<string> filelist;

int main()
{
    scandir("/");
    show_filelist();
    return 0;
}

void scandir(string basedir)
{
    DIR *dhandle;
    struct dirent *dentry;
    
    if ((dhandle = opendir(basedir.c_str())) == NULL) {
        cout << "ERROR (" << errno << ") opening " << basedir << endl;
        return;
    }
    
    while ((dentry = readdir(dhandle)) != NULL) {
        if (strcmp(dentry->d_name, ".") != 0 && strcmp(dentry->d_name, "..") != 0) {
            string full_path = basedir + dentry->d_name;
            
            if (dentry->d_type == isFolder) {
                string cpath = full_path + "/";
                scandir(cpath);
            } else {
                try {
                    filelist.push_back(full_path);
                } catch (exception& e) {
                    cout << e.what() << endl;
                }
            }
            
        }
    }
    
    closedir(dhandle);
}

void show_filelist()
{
    cout << "Vector contains " << filelist.size() << " elements : \n";
    
    for (int i = 0; i < filelist.size(); i++) {
        cout << i << ": " << filelist[i] << endl;
    }
}
```

---

### Post by fr4nko on 2009-07-05
It does not works, it is strange. Actually I think you should use the constant DT_DIR to verify if is a directory but in my system I always get DT_UNKNOWN.

I'm very perplexed... may be it is because I've a reiserfs filesystem ? Probably we should ask to a linux guru... :-)

Francesco

---

### Post by credobyte on 2009-07-05
That's weird :-k Anyway, reading the whole *HDD* was a test drive - I'm not going to use it as a part of my application :) I simply needed a way to read any directory recursively, no matter how many sub-directories or files are inside.

Indeed, I'm quite surprised - 200k files reported in about 1min :)

---

