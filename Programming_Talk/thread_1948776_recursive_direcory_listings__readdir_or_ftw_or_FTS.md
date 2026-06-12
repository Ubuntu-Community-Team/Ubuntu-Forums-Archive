---
title: "recursive direcory listings : readdir or ftw or FTS or glob"
date: 2012-03-28
forum: Programming Talk
---

### Post by UncleRoy on 2012-03-28
In Windows C++ I would use (findfirst + findnext) recursively to list all (patterned) files in a directory.
Having found some Linux doco it seems

1) use (opendir readdir closedir) to read ALL names , fnmatch() reject and recurse.
   Would likely work but would be slow. 
2) ftw will file tree walk (recurse) but has no pattern matcher built in.
3) FTS also has no patten matcher.
4) glob asserts greater efficiency. But no built in recursion. I could call glob twice. 
    Once with "*" for directories.Once with "*.cpp" for files. Each time (directory or file) 
    compares must be made (after using GLOB_MARK). This seems slower than others.
5) One could always exec ls, or something i don't know yet.

If no recursion is needed using glob seems best. If recursion is needed using FTS appears best.
All this is guesswork. Can someone tell me if my analysis is flawed.

Is there some thing else better ??  Why doesnt glob recurse as a bitflag

what don't I know ??

---

### Post by CynicRus on 2012-03-29
```

[FONT=Courier New][SIZE=2][COLOR=black]#ifndef _VIEW_H
[COLOR=#0000ff]#define[/COLOR]  _VIEW_H

#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <dirent.h>
#include <[COLOR=#0000ff]string[/COLOR].h>
#include <iostream>
#include <pwd.h>
#include <grp.h>
#include <errno.h>

[COLOR=#0000ff]using[/COLOR] [COLOR=#0000ff]namespace[/COLOR] std;

[COLOR=#0000ff]int[/COLOR] myView([COLOR=#0000ff]bool[/COLOR] l,[COLOR=#0000ff]bool[/COLOR] r,[COLOR=#0000ff]const[/COLOR] [COLOR=#0000ff]char[/COLOR]* path)
{
  DIR* dir = opendir(path);
  [COLOR=#0000ff]if[/COLOR](!dir)
    [COLOR=#0000ff]return[/COLOR] 1;

  [COLOR=#0000ff]struct[/COLOR] dirent *rd;

  [COLOR=#0000ff]while[/COLOR]((rd = readdir(dir)))
  {
    [COLOR=#0000ff]if[/COLOR](!strcmp(rd->d_name,[COLOR=#A31515]"."[/COLOR]) || !strcmp(rd->d_name,[COLOR=#A31515]".."[/COLOR]))
    {
      [COLOR=#0000ff]continue[/COLOR];
    }
    [COLOR=#0000ff]struct[/COLOR] stat entryInfo;
    [COLOR=#0000ff]char[/COLOR] pathName[PATH_MAX+1];

    strncpy(pathName,path,PATH_MAX);
    strncat(pathName,[COLOR=#A31515]"/"[/COLOR],PATH_MAX);
    strncat(pathName,rd->d_name,PATH_MAX);

    [COLOR=#0000ff]if[/COLOR](!lstat(pathName,&entryInfo))
    {
      [COLOR=#0000ff]if[/COLOR](l)
      {
        [COLOR=#0000ff]switch[/COLOR](entryInfo.st_mode & S_IFMT)
        {
          [COLOR=#0000ff]case[/COLOR] S_IFDIR:
          {
            cout << [COLOR=#A31515]"d"[/COLOR];
            [COLOR=#0000ff]break[/COLOR];
          }
          [COLOR=#0000ff]case[/COLOR] S_IFIFO:
          {
            cout << [COLOR=#A31515]"p"[/COLOR];
            [COLOR=#0000ff]break[/COLOR];
          }
          [COLOR=#0000ff]case[/COLOR] S_IFSOCK:
          {
            cout << [COLOR=#A31515]"s"[/COLOR];
            [COLOR=#0000ff]break[/COLOR];
          }
          [COLOR=#0000ff]case[/COLOR] S_IFLNK:
          {
            cout << [COLOR=#A31515]"l"[/COLOR];
            [COLOR=#0000ff]break[/COLOR];
          }
          [COLOR=#0000ff]default[/COLOR]:
            cout << [COLOR=#A31515]"-"[/COLOR];
        }

        [COLOR=#008000]//owner[/COLOR]
        [COLOR=#008000]//read[/COLOR]
        [COLOR=#0000ff]if[/COLOR](entryInfo.st_mode & S_IRUSR)
          cout << [COLOR=#A31515]"r"[/COLOR];
        [COLOR=#0000ff]else[/COLOR]
          cout << [COLOR=#A31515]"-"[/COLOR];
        [COLOR=#008000]//write[/COLOR]
        [COLOR=#0000ff]if[/COLOR](entryInfo.st_mode & S_IWUSR)
          cout << [COLOR=#A31515]"w"[/COLOR];
        [COLOR=#0000ff]else[/COLOR]
          cout << [COLOR=#A31515]"-"[/COLOR];
        [COLOR=#008000]//execute[/COLOR]
        [COLOR=#0000ff]if[/COLOR](entryInfo.st_mode & S_IXUSR)
          cout << [COLOR=#A31515]"x"[/COLOR];
        [COLOR=#0000ff]else[/COLOR]
          cout << [COLOR=#A31515]"-"[/COLOR];

        [COLOR=#008000]//group[/COLOR]
        [COLOR=#008000]//read[/COLOR]
        [COLOR=#0000ff]if[/COLOR](entryInfo.st_mode & S_IRGRP)
          cout << [COLOR=#A31515]"r"[/COLOR];
        [COLOR=#0000ff]else[/COLOR]
          cout << [COLOR=#A31515]"-"[/COLOR];
        [COLOR=#008000]//write[/COLOR]
        [COLOR=#0000ff]if[/COLOR](entryInfo.st_mode & S_IWGRP)
          cout << [COLOR=#A31515]"w"[/COLOR];
        [COLOR=#0000ff]else[/COLOR]
          cout << [COLOR=#A31515]"-"[/COLOR];
        [COLOR=#008000]//execute[/COLOR]
        [COLOR=#0000ff]if[/COLOR](entryInfo.st_mode & S_IXGRP)
          cout << [COLOR=#A31515]"x"[/COLOR];
        [COLOR=#0000ff]else[/COLOR]
          cout << [COLOR=#A31515]"-"[/COLOR];

        [COLOR=#008000]//other[/COLOR]
        [COLOR=#008000]//read[/COLOR]
        [COLOR=#0000ff]if[/COLOR](entryInfo.st_mode & S_IROTH)
          cout << [COLOR=#A31515]"r"[/COLOR];
        [COLOR=#0000ff]else[/COLOR]
          cout << [COLOR=#A31515]"-"[/COLOR];
        [COLOR=#008000]//write[/COLOR]
        [COLOR=#0000ff]if[/COLOR](entryInfo.st_mode & S_IWOTH)
          cout << [COLOR=#A31515]"w"[/COLOR];
        [COLOR=#0000ff]else[/COLOR]
          cout << [COLOR=#A31515]"-"[/COLOR];
        [COLOR=#008000]//execute[/COLOR]
        [COLOR=#0000ff]if[/COLOR](entryInfo.st_mode & S_IXOTH)
          cout << [COLOR=#A31515]"x"[/COLOR];
        [COLOR=#0000ff]else[/COLOR]
          cout << [COLOR=#A31515]"-"[/COLOR];

        cout << [COLOR=#A31515]" "[/COLOR];
        [COLOR=#0000ff]struct[/COLOR] passwd* pwd = getpwuid(getuid());
        [COLOR=#0000ff]struct[/COLOR] group* grp = getgrgid(pwd->pw_gid);
        cout << [COLOR=#A31515]" "[/COLOR] << grp->gr_name << [COLOR=#A31515]" "[/COLOR] << pwd->pw_name << [COLOR=#A31515]" "[/COLOR];
      }

      [COLOR=#0000ff]if[/COLOR](S_ISDIR(entryInfo.st_mode))
      {
        cout << rd->d_name << endl;
        [COLOR=#0000ff]if[/COLOR](r)
        {
          myView(l,r,pathName);
        }
      }[COLOR=#0000ff]else[/COLOR]
      [COLOR=#0000ff]if[/COLOR](S_ISREG(entryInfo.st_mode))
      {
        cout << rd->d_name;
      }[COLOR=#0000ff]else[/COLOR]
      [COLOR=#0000ff]if[/COLOR](S_ISLNK(entryInfo.st_mode))
      {        
        [COLOR=#0000ff]char[/COLOR] targetName[PATH_MAX+1];
        [COLOR=#0000ff]if[/COLOR](readlink(pathName,targetName,PATH_MAX))
        {
          cout << rd->d_name << [COLOR=#A31515]" link: "[/COLOR]
              << targetName;
        }
      }[COLOR=#0000ff]else[/COLOR]
      [COLOR=#0000ff]if[/COLOR](S_ISSOCK(entryInfo.st_mode))
      {
        cout << rd->d_name;
      }
      cout << endl;
    }
   [/COLOR][/SIZE][/FONT]/ / Added check here, to prevent the fall of the stack, details below[FONT=Courier New][SIZE=2][COLOR=black][COLOR=#008000][/COLOR]
    [COLOR=#0000ff]else[/COLOR]
    {
      cout << rd->d_name << [COLOR=#A31515]" "[/COLOR] << strerror(errno) << endl;
      exit(1);
    }
  }
  closedir(dir);
}

[COLOR=#0000ff]#endif[/COLOR]  [COLOR=#008000]/* _VIEW_H */[/COLOR][/COLOR][/SIZE][/FONT]



```
The function displays a list of files in a directory, including recursively.

Options:

 1) Displays information about the file (true / false)

 2) recursive (true / false)

 3) The path (if not specified, ".")

if i understand the question.

---

### Post by ofnuts on 2012-03-29
> **UncleRoy said:**
> In Windows C++ I would use (findfirst + findnext) recursively to list all (patterned) files in a directory.
Having found some Linux doco it seems

1) use (opendir readdir closedir) to read ALL names , fnmatch() reject and recurse.
   Would likely work but would be slow. 
What makes you think so? What do you think findfirst()/findnextt() do under the hood?

---

### Post by CynicRus on 2012-03-29
opendir(S), closedir(S), readdir(S) - - system calls can not slow down. So, if you use these functions - and the code is running slow, there is an opinion - that the error in the algorithm,  rather than in the slow work of the calls.

---

