---
title: "c++ distinguish between a text file and a binary file"
date: 2010-02-22
forum: Programming Talk
---

### Post by Woody1987 on 2010-02-22
My program needs to open files and check if it is a binary or a text file.

```
int search(string rootDir)
{
    DIR *dir; //the directory
    struct dirent *dp;
    struct stat st;

    string tempDir = rootDir; //temp directory

    //open the directory
    if((dir  = opendir(rootDir.c_str())) == NULL)
    {
        //if directory isnt found
        cout << "Error(" << errno << ") opening " << rootDir << endl;
        return errno;
    }

    //traverse the directory
    while ((dp = readdir(dir)) != NULL)
    {
        const char *path = tempDir.append(dp->d_name).c_str(); //create path
        stat(path, &st); //get information about the current file/directory

        if(st.st_mode & S_IFREG) //if a file
        {
            //NEED HELP HERE!!!
            if(binary)
            {
            }
            if(text)
            {
            }
        }
        else
        {
            if(strcmp(dp->d_name, ".") != 0 && strcmp(dp->d_name, "..") != 0) //if a valid folder
            {
                
            }
        }
    }

    closedir(dir);
    return 0;
}
```

Code above shows what i want to achieve.

How do i do this?

---

### Post by Some Penguin on 2010-02-22
What is your definition of 'binary file'?

If it's something like 'file which contains any characters outside a desired set', then the solution is clear:  verify that the file is a normal file and not a named pipe or symbolic link or directory or what-have-you; open the file; and check every byte (loading in 8K chunks or so, nice and digestable), until you either hit a byte that falls outside the set or there aren't any more bytes to read.

---

### Post by Woody1987 on 2010-02-22
> **Some Penguin said:**
> What is your definition of 'binary file'?

If it's something like 'file which contains any characters outside a desired set', then the solution is clear:  verify that the file is a normal file and not a named pipe or symbolic link or directory or what-have-you; open the file; and check every byte (loading in 8K chunks or so, nice and digestable), until you either hit a byte that falls outside the set or there aren't any more bytes to read.

I assumed binary files were executable files, music, video, images etc, and text files were simply string of characters that i could open in for example gedit.

---

### Post by Some Penguin on 2010-02-22
The filesystem doesn't label them as such, and they're not stored any differently.  For what you want to do, open and read the file.  

If you wanted, you could load the Linux kernel or the contents of DVD's VOB file into a text editor.  It wouldn't be very comprehensible, and any edits you made would almost certainly break things, but you could.   You could also attempt to load a configuration file into a DVD player -- it's up to the application (or more likely, a library that it uses) to begin reading the file and rapidly determine that the bytes aren't what it's expecting, based on headers and the like.

Scripts are also both readable and executable.  Unicode text can have bytes that are not easily readable ASCII characters, IIRC.  Do these qualify as binary or text?  The decision affects the definition and you will need to consider how to handle it.

---

### Post by falconindy on 2010-02-22
Ahh, but every non-ascii file definition has a 'magic number' associated with it. For example, any ELF binary will start with the following:
```
$ hexdump `which mplayer` | head -1
0000000 457f 464c 0102 0001 0000 0000 0000 0000
```

A jpeg will always start with:
```
0000000 d8ff e0ff 1000 464a 4649 0100 0101 6000
```
However, the last 32 bits can vary depending on the jpeg version. 

An ascii file will not have this header, and dives directly into the data.

You may want to poke around the source code for the program 'file', which determines file type based on this magic number.

---

### Post by Some Penguin on 2010-02-22
Formats don't have to have magic numbers registered in that file.  It's a reasonable test to detect some common file types, but failure to match doesn't mean that it's text -- it's entirely possible that it simply isn't listed.  Try running 'file /etc/ld.so.cache', for instance:  it's simply 'data', which means that it doesn't know the format and probably found non-ASCII bytes.

---

### Post by Lux Perpetua on 2010-02-23
> **Some Penguin said:**
> Formats don't have to have magic numbers registered in that file.  It's a reasonable test to detect some common file types, but failure to match doesn't mean that it's text -- it's entirely possible that it simply isn't listed.  Try running 'file /etc/ld.so.cache', for instance:  it's simply 'data', which means that it doesn't know the format and probably found non-ASCII bytes.Exactly. The `file' utility may be relevant here, but you can be sure that its algorithm is perfectly ad-hoc. The bottom line is that on Linux, there is no fundamental difference between "text files" and "binary files," as on some other systems. Every file is binary.

---

