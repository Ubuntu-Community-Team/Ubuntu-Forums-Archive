---
title: "[C++] Converting a DIR* back to a string?"
date: 2009-06-10
forum: Programming Talk
---

### Post by dodle on 2009-06-10
I am trying to create a class that scans a directory to find which files are in it and return the value as a string.  But I can't convert the value of "value2" back to a string.  How can I do this?

home.h:
[php]#include <dirent.h>
#include <iostream>
#include <cstring>
using namespace std;

class Templates
{
public:
    string getTemplateDir();
	void getTemplates();
private:
	char *home_path;
};
[/php]

home.cpp:
[php]#include "home.h"

string Templates::getTemplateDir()
{
    home_path = getenv("HOME"); //Retrieve user's home directory
	string home = home_path; //Convert to string
	string template_dir = home + "/Templates";
	
	char *value1 = NULL;
	strcpy(value1, template_dir.c_str()); //Convert back to char
	
	DIR *value2 = NULL;
	value2 = opendir(value1);
	struct dirent *pent = NULL;
	
    if (value2 == NULL)
    {
    }

    while (pent = readdir(value2))
    {
        if (pent == NULL)
        {
        }
    }
	string all_templates = value2; //Here is where I don't know how to convert back to a string
    cout << pent->d_name << endl;
    closedir (tmp_dir);
	
	return all_templates;
}
[/php]

---

### Post by Mirge on 2009-06-10
[COLOR=#000000][COLOR=#007700]    [/COLOR][COLOR=#0000BB]char [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000BB]value1 [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]NULL[/COLOR][COLOR=#007700];
    [/COLOR][COLOR=#0000BB]strcpy[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]value1[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]template_dir[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]c_str[/COLOR][COLOR=#007700]()); [/COLOR][COLOR=#FF8000]//Convert back to char

[/COLOR][/COLOR]You're creating a pointer to a char, but not allocating any memory for it... or referencing a char array (which would allocate memory). You are essentially copying data to memory to a random area. Might wanna fix that first :).

---

### Post by dodle on 2009-06-11
Here is what I've been able to come up with.  It works, but "." and ".." also show up in the resulting string.

home.cpp:
[php]#include "home.h"

string Templates::getTemplates()
{
    string all_templates; //Set the string that will be returned
	
    char *home_path;
    home_path = getenv("HOME"); //Get the user's home directory
	string home = home_path;  //Convert to std::string
	string template_path = home + "/Templates";  //Add Templates directory to the end of home directory
	
	const char *template_dir = template_path.c_str();  //Convert back to a const char
	
	DIR *directory = NULL;
	directory = opendir(template_dir);  //Open the resulting directory
	struct dirent *entry = NULL;
	
    if (directory == NULL)
    {
    }

    while (entry = readdir(directory))
    {
        if (entry == NULL)
        {
        }
		all_templates = all_templates + entry->d_name + "\n";  //Add all the values into one string
    }
    closedir (directory);
	return all_templates;
}
[/php]

---

### Post by dwhitney67 on 2009-06-11
> **dodle said:**
> Here is what I've been able to come up with.  It works, but "." and ".." also show up in the resulting string.

home.cpp:
[php]#include "home.h"

string Templates::getTemplates()
{
    string all_templates; //Set the string that will be returned
	
    char *home_path;
    home_path = getenv("HOME"); //Get the user's home directory
	string home = home_path;  //Convert to std::string
	string template_path = home + "/Templates";  //Add Templates directory to the end of home directory
	
	const char *template_dir = template_path.c_str();  //Convert back to a const char
	
	DIR *directory = NULL;
	directory = opendir(template_dir);  //Open the resulting directory
	struct dirent *entry = NULL;
	
    if (directory == NULL)
    {
    }

    while (entry = readdir(directory))
    {
        if (entry == NULL)
        {
        }
		all_templates = all_templates + entry->d_name + "\n";  //Add all the values into one string
    }
    closedir (directory);
	return all_templates;
}
[/php]

Defining template_dir is unnecessary; just use template_path.c_str() in the opendir() function.

Clean up the flow of the code wrt when the opendir() fails.  In your code, it continues with the while-loop, which is not what you want.  Try to write your method so that there is a single return point.

getTemplates() should accept a string path; the reason for this is that you may want to call it recursively if you find another directory within the current directory being searched.

As for the '.' and '..' entries, those are directories that can be ignored.  Add a conditional to ignore these:
```

void getTemplates(const std::string& path, std::string& all_templates)
  {
    DIR*    directory = opendir(path.c_str());
    dirent* entry     = NULL;
    
    if (directory != NULL)
    { 
      while (entry = readdir(directory))
      {
        std::string file(entry->d_name);

        if (file == "." || file == "..") continue;

        all_templates += file + "\n";

        if (entry->d_type == DT_DIR)
        {
          std::string newpath = path + "/" + file;
          getTemplates(newpath, all_templates);
        }
      }
    }
  }

```

P.S.  The effort you are attempting has been done by many developers before, including myself.  Unfortunately I did not have the time to reference my old code, or test the one presented above.  But the gist of it, as shown above, should work.

---

