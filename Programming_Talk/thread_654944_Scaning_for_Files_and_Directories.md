---
title: "Scaning for Files and Directories"
date: 2007-12-31
forum: Programming Talk
---

### Post by WastingBody on 2007-12-31
I'm using this code to list all of the files in a directory, but it also lists the other directories. I want to put the directories that are found into different array. I don't know how to determine whether the current entry is a directory or a file.
[PHP]int getdir(string dir, vector<string> &files)
{
	DIR *dp;
	struct dirent *dirp;
	
	if((dp  = opendir(dir.c_str())) == NULL) 
	{
        cout << "Error(" << errno << ") opening " << dir << endl;
        return errno;
    }

    while ((dirp = readdir(dp)) != NULL)
	{
        files.push_back(string(dirp->d_name));
    }
    closedir(dp);
    return 0;
}[/PHP]

---

### Post by stroyan on 2007-12-31
You want to use stat and the S_ISDIR macro as discussed in this thread-
[http://ubuntuforums.org/showthread.php?t=653346](http://ubuntuforums.org/showthread.php?t=653346)

---

### Post by Majorix on 2007-12-31
Why not use system() calls? You can check the OS of the user and run a system("ls") or system("dir") accordingly. Then you can parse the results.

---

### Post by ghostdog74 on 2007-12-31
> **Majorix said:**
> Why not use system() calls? 
try not to do this. Its less flexible, and not portable.

---

### Post by Majorix on 2007-12-31
It is in my opinion much more convenient than a 50-liner. And any code can be portable, you just have to know how to make it one. In my example, you have to check the OS of the user and act accordingly. Basically, actually any code can be made portable that way.

---

### Post by ghostdog74 on 2007-12-31
> **Majorix said:**
> It is in my opinion much more convenient than a 50-liner. And any code can be portable, you just have to know how to make it one. In my example, you have to check the OS of the user and act accordingly. Basically, actually any code can be made portable that way.
1) How many OSes are out there? 
2) ls(*nix) and dir(windows) have many different switches and options and output formats. Say if you want to get the file timestamps using ls and dir. You have to write separate set of codes for both commands because their output are not the same. In the end, you write more code.
3) versions of ls are not the same on different distros. 
4) what if there are no ls or dir commands presents on the system?
5) (fill in the blanks here)

---

### Post by WastingBody on 2008-01-01
What I ended up doing was searching the string for the file type that I wanted. I don't know why I didn't think about it earlier.

---

