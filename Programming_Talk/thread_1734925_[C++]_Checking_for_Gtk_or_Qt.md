---
title: "[C++] Checking for Gtk or Qt"
date: 2011-04-20
forum: Programming Talk
---

### Post by dodle on 2011-04-20
I was wondering if there was a way to check which GUI library was being using in the operating system. I want to use native dialogs for an app. I thought about preprocessors, but I don't think that is possible. I'm not on Linux right now, so I can't test any of this.

[php]#ifdef GTK
...
#elif defined QT
...
#endif[/php]

I don't think that is possible becuase the compiler is desktop independent.

Is there a way to check for header file existence before including them?

---

### Post by dodle on 2011-04-21
I figured out a way to test for a header file's existence. Here is a header that I wrote for it:

fexists.h:
[php]// Tests if a specified file exists

/* The author claims no copyright on this work
 * It is free to use for any purpose
 */

#ifndef _FEXISTS_H_
    #define _FEXISTS_H_

#include <fstream>
#include <string>
using namespace std;

#include <cstdlib>
#include <vector>

int FileExists(string filename)
{
    fstream file(filename.c_str());
    
    if (file.is_open())
    {
        file.close();
        return 1;
    }
    
    file.close();
    return 0;
}

int FileExistsInPath(string filename)
{
    vector<string> dirs(0); // Will contain all the directories that are in the PATH environment variable
    int dircount; // The number of directories contain in the PATH environment variable
    string tempstr; // String for storing each directory individually
    string path = getenv("PATH");
    
    while (path.length() > 0)
    {
        if (path[0] == ';')
        {
            // Add an extra "/" to the end of the string
            tempstr.push_back('/');
            // If we have reached the end of a directory name add the temp string to the vector list
            dirs.push_back(tempstr);
            tempstr.clear();
        }
        // Add each character to the temporary string if it is not ";"
        else tempstr.push_back(path[0]);
        // remove the character so the while loop can eventually end
        path.erase(0, 1);
    }
    
    // Here is where we test each directory for for the desired file
    dircount = dirs.size(); // Get the number of directories we have found
    
    for (int x = 0; x < dircount; x++)
    {
        // We will use the temporary string again for the testing
        tempstr = dirs.at(x) + filename;
        // Now the actual test
        if (FileExists(tempstr)) return 1;
    }
    
    return 0;
}

#endif /* _FEXISTS_H_ */[/php]

test.cpp:
[php]#include <iostream>
using namespace std;

#include "fexists.h"

int main()
{
    if (FileExistsInPath("../include/string.h")) cout << "File Exists!\n";
    else cout << "File does not exist.\n";
    
    return 0;
}[/php]

The first function checks for a files existence, the second function check for a files existence in the PATH environment variable. Since the default "include" directory is not in the PATH I use "../include/filename" to check it. So when it looks in "/usr/bin" it is actually looking in "/usr/bin/../include/filename".

If anyone want's to point out any improvements or errors please do so. Also, I have only tested this on Windows, so if someone wants to test it on Linux and let me know if it works that would be great.

---

### Post by JupiterV2 on 2011-04-21
If you are able to build your project using the GNU autotools, use autoconf to check for the headers you are looking for and/or add an --enable-xyz feature to turn specific front-ends on/off.

---

