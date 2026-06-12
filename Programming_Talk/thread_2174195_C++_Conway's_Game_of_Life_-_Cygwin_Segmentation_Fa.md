---
title: "C++ Conway's Game of Life - Cygwin Segmentation Fault (Core Dumped)"
date: 2013-09-13
forum: Programming Talk
---

### Post by homeofmatt on 2013-09-13
Hey guys,
I'm new to this forum but I could really use some help.
I've been tasked with programming Conway's Game of Life in C++ and compiling in Cygwin (with a makefile). I'm not asking anybody to complete the program for me or anything like that, but I am totally stuck on this one part...
One of the facets of the program is to allow a user to input a text file as a map for the initial grid, rather than using a randomly generated grid.
Here is an example of the format of the .txt file (the numbers and 'X' are purely for example, a file can be any variation of this format):

5 (rows)
6 (columns)
-----X
X--X--
------
-XX---
------

The 'X' represent spaces with live bacteria, and the '-' represent dead spaces.
Although my program compiles just fine through cygwin, when I run the .exe I get a "Segmentation Fault (Core Dumped)" error. I've done extensive google searching to this point, but I've found that this error is generally very specific to the program which it concerns, so other solutions aren't of much help to me.
I don't want to spam you guys with a ton of code, so I'm only including my loadFile function for now. If you need more of the code to help, let me know and I'll post it immediately.
Here's what I have so far in my loadFile function:

```

void GamePlay::loadFile(int r, int c, char** newBoard){
  int i;
  //int r;
  //int c;
  //char** newBoard;


  int len;
  int k;
    
  do{
    r = 0;
    c = 0;
    string filePath;
    cout << "Please enter a file path" << endl;
    cin >> filePath;
    DIR* path = opendir(filePath.c_str());
    string fpath = filePath.c_str();
    dirent* openIn = readdir(path);
    string line;
    string ext = ".txt";
    i = 0;
        
    while(openIn && i != -1){
        if(openIn->d_type == DT_REG){
            string fileName = openIn->d_name;
            string filePath = fpath + fileName;
            int begExt = fileName.find_last_of(".");
            int endExt = fileName.find_last_of("t");
            string extension = fileName.substr(begExt, endExt);
                
            ifstream in(filePath.c_str());
            k = 0;
                
            if(in && ext == extension){
                getline(in,line);
                istringstream(line) >> r;
                getline(in,line);
                istringstream(line) >> c;
                newBoard = new char*[r]; //create multi-d array
                for(int a = 0; a < r; ++a){
                    newBoard[a] = new char[c];
                }
                    
                while(in.good() && i != -1){
                    if(k <= r){
                        if(len == c){
                            for(int g = 0; g < r; ++g){
                                getline(in,line);
                                len = line.size();
                                char* arr = new char[len];
                                memcpy(arr,line.c_str(),len);
                                for(int h = 0; h < c; ++h){
                                    newBoard[g][h] = arr[h];
                                }
                            }
                        }
                        /*if(len == c){
                        //newBoard = len*sizeof(char*);
                        for(int a = 0; a < len; ++a){
                        newBoard[a] = r;
                        memcpy(newBoard[a], line, r);
                        }
                        }*/
                        else{
                            cout << "Your column number does not match your grid." << endl;
                            cout << "Please try again with a new file." << endl;
                            i = -1;
                        }
                    }
                    else{
                        cout << "Your row number does not match your grid." << endl;
                        cout << "Please try again with a new file." << endl;
                        i = -1;
                    }
                    k++;
                }
            }
            else{
                cout << "File invalid. Please try again with a new file." << endl;
                i = -1;
            }
            return;
        }
        else{
            cout << "Invalid file path. Please try again with a new file." << endl;
            i = -1;
        }
    }
  }while(i = -1);
}

```

Thanks!!!

---

### Post by GeneralZod on 2013-09-13
First step: run it in gdb and find out what line it crashes on :)

---

### Post by homeofmatt on 2013-09-15
I've been trying to figure GDB out this past weekend, but it's just over my head and I don't have the time to really sit down and figure it out. Sadly all I'm used to using are the debugging components in GUIs like Visual Studio and Eclipse...
Is there any alternative way to figure this out?

---

### Post by dwhitney67 on 2013-09-15
> **homeofmatt said:**
> I've been trying to figure GDB out this past weekend, but it's just over my head and I don't have the time to really sit down and figure it out.

Make the time.

> **homeofmatt said:**
> Sadly all I'm used to using are the debugging components in GUIs like Visual Studio and Eclipse...
So why aren't you using one of these tools?

As for the issue in your code, you may want to examine the error here:
```

len = line.size();
**char* arr = new char[len];**
memcpy(arr,line.c_str(),len);

```

Btw, why are you using primitive char-array strings in a C++ program?  If you would simply stick to the STL string class, you could simplify your application quite a lot.

---

### Post by homeofmatt on 2013-09-15
Yea I don't know why I haven't thought of that... haha thanks, and yea that's where I was assuming it might be to begin with (considering most google searches have shown that the error has something to do with going out of bounds of an array). I'll try debugging in Eclipse and post back what I find.

---

### Post by homeofmatt on 2013-09-15
Actually, I'm pretty sure I can't debug in a GUI like that because it's not a linux-based environment like Cygwin is and I'm using dirent.h for my file access.

---

### Post by spjackson on 2013-09-16
> **homeofmatt said:**
> Actually, I'm pretty sure I can't debug in a GUI like that because it's not a linux-based environment like Cygwin is and I'm using dirent.h for my file access.
It's a long time since I've used Cygwin, but I have run X on Cygwin and Google tells me that the graphical front end to gdb, ddd has been available for Cygwin (and possibly other graphical front ends too). So that's one option.

If you want to write "linux-based" code, then why not do it on Linux?

Your function does too much. I suggest that you at least separate the prompting and file finding and opening from the file reading. Then you could debug the reading function in Eclipse on Windows if you wanted to.

Note that your outer loop will never terminate:
```

  }while(i = -1);
```
I guess you mean '=='.

---

