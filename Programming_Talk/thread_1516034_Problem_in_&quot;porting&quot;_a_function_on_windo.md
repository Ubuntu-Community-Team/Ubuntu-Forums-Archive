---
title: "Problem in &quot;porting&quot; a function on windows to linux?"
date: 2010-06-23
forum: Programming Talk
---

### Post by jeremy28 on 2010-06-23
Hi all!
 
I use ubuntu 9.04;
I have a function called "isLogEnabled" in my project on windows, I wanna port it to linux. 
I know that I should have a "config.h" file in linux to get log from a specific Shared object and ..., but because I'm new to linux,
I don't know how this should be done, this is my function:
```
//This function return True if log policy is set in registry and False otherwise
   int isLogEnabled()
   {
     HKEY hKey;
     LONG lRes;
     DWORD dwType, dwSize = 0;
     int retVal = 0;
 
     if((RegOpenKeyEx(HKEY_LOCAL_MACHINE, "SOFTWARE\\MyCorp", 0, KEY_ALL_ACCESS, &hKey)) == ERROR_SUCCESS)
     {
        lRes = RegQueryValueEx(hKey, "SpecialMode", 0, &dwType, NULL, &dwSize );
 
        if(lRes == ERROR_SUCCESS)
           retVal = 1;
        RegCloseKey(hKey);
     }
     return retVal;
  }

```
  
Since I think we don't have registry concept in linux and this function uses registry APIs, I'm confused to change it to be compatible with linux;
 
Could you help me with this please?!
TIA.

---

### Post by slavik on 2010-06-23
use a config file.

---

### Post by nrs on 2010-06-23
They closest you'll get to something registry like on Linux is gconf. Don't use gconf. Config files ftw.

---

### Post by jeremy28 on 2010-06-30
Hi and thanks for your replies!

My config file would only contain "retVal = 1", because this is the return value of "isLogEnabled" function and in my main function it's checked as below:

if(isLogEnabled())
           initLogger(LOG_FILE);

 If I don't use the libconfig functions and just want to load the config file content(retval), what should I do?

I mean:
I should open a gedit text and only write "retval=1" in it, I name it "Mainconf" but I don't know what would I define it's extension(.cfg or .config or ...)?

I should save it in /etc directory, now how can I load it to my program to check it and what would be the alternative for the part:

if(isLogEnabled())
          initLogger(LOG_FILE);

in linux?

I'm new to software developing in linux. Please guide me!!

THX again.

---

### Post by dwhitney67 on 2010-06-30
The file extension you choose is hardly relevant, but most developers tend to choose ".cfg".

Your thoughts on adding "retVal = 1" seem simplistic.  Why not insert an entry in the config file like "EnableLogging = 1"?

Your app should read the config file, save the state of the values read from within it, and your functions (ie. isLogEnabled()) should request the state so as to generate a proper return value.

```

bool isLogEnabled()
{
   return configState[LOG_ENABLED] == 1;
}

```
configState is some container (an array or hash-table) that associates your config file entry with a value.

---

### Post by jeremy28 on 2010-06-30
Hi and thanks so much, your post was very helpful!
 
```
Why not insert an entry in the config file like "EnableLogging = 1"?
```
 
Yes, it's more rational. 
Well,
1- I open a gedit text and only write "EnableLogging = 1" in it, I name it "Mainconf.cfg" and save it in "/etc" directory.
 
2- I replace the function:
```
 int isLogEnabled()
   {
     HKEY hKey;
     LONG lRes;
     DWORD dwType, dwSize = 0;
     int retVal = 0;
 
     if((RegOpenKeyEx(HKEY_LOCAL_MACHINE, "SOFTWARE\\MyCorp", 0, KEY_ALL_ACCESS, &hKey)) == ERROR_SUCCESS)
     {
        lRes = RegQueryValueEx(hKey, "SpecialMode", 0, &dwType, NULL, &dwSize );
 
        if(lRes == ERROR_SUCCESS)
           retVal = 1;
        RegCloseKey(hKey);
     }
     return retVal;
  }
```
 
with this one:
```
bool isLogEnabled()
{
   return configState[LOG_ENABLED] == 1;
}
```
 
> Your app should read the config file, save the state of the values read from within it,
 
Excuse me, I don't know how my app (isLogEnabled function) should read the config file and save the state of the values read from within it? 
I mean with which linux APIs?
 
> configState is some container (an array or hash-table) that associates your config file entry with a value. 
 
Where should the configState container be defined and also about "LOG_ENABLED"?
 
 
I think in function "isLogEnabled", the config file should be read and the value of "EnableLogging" be returned and then in the "main" function, the returned value would be checked:
 
```
if(isLogEnabled())
       initLogger(LOG_FILE);
```
 
 
BTW, I apologize if my questions are clumsily! 
I'll appreciate if you reply again.
 
TIA.
[SIZE=5] [/SIZE]

---

### Post by dwhitney67 on 2010-06-30
Reading of the configuration file should take place during the start-up of the application (perhaps in the main() function).

If you specify which language you are using, C or C++, then maybe I can assist you with opening/parsing the configuration file.

---

### Post by jeremy28 on 2010-06-30
I use C++;
 
THX.

---

### Post by dwhitney67 on 2010-06-30
Assuming the configuration file has contents with a format like:
```

EnableLogging = 1

```
then the following code could be used.

Config.h:
```

#include <map>
#include <string>
#include <sstream>

class Config
{
public:
   static Config& instance();

   bool initConfig(const char* cfgFilename);

   template <typename T> T lookupValue(const std::string& cfgID)
   {
      ConfigMap::const_iterator it = myConfig.find(cfgID);

      T rtn;

      if (it != myConfig.end())
      {
         std::stringstream iss(it->second);

         iss >> rtn;
      }

      return rtn;
   }

private:
   typedef std::map<std::string, std::string> ConfigMap;

   Config() {}

   // declared, but not implemented.
   Config(const Config& other);
   Config& operator=(const Config& other);

   // map for storing configuration items.
   ConfigMap myConfig;
};

```

Config.cpp:
```

#include "Config.h"
#include <fstream>
#include <iostream>

Config&
Config::instance()
{
   static Config theInstance;
   return theInstance;
}


bool
Config::initConfig(const char* cfgFilename)
{
   using namespace std;

   bool    status = true;
   fstream file(cfgFilename, ios::in);

   if (file)
   {
      string line;
      size_t lineNum = 0;

      while (getline(file, line))
      {
         ++lineNum;

         stringstream iss(line);
         string       key, equals, value;

         iss >> key >> equals >> value;

         if (!iss.fail())
         {
            myConfig.insert(pair<string, string>(key, value));
         }
         else
         {
            cerr << "Error in configuration file, line " << lineNum << endl;
            status = false;
            break;
         }
      }
   }
   else
   {
      cerr << "Cannot open configuration file " << cfgFilename << endl;
      status = false;
   }

   return status;
}

```

Main.cpp:
```

#include "Config.h"
#include <iostream>

bool isLoggingEnabled();

int main()
{
   //const char* CONFIG_FILE = "/etc/MyProgram.cfg";
   const char* CONFIG_FILE = "foo.cfg";

   if (Config::instance().initConfig(CONFIG_FILE) != true)
   {
      return -1;
   }

   // continue with app...
   std::cout << "Logging is " << (isLoggingEnabled() ? "enabled." : "disabled.") << std::endl;

   return 0;
}


bool isLoggingEnabled()
{
   return Config::instance().lookupValue<bool>("EnableLogging");
}

```

There's probably a dozen or more other ways this could be done.  This idea was the first that popped into my mind.

---

### Post by jeremy28 on 2010-07-01
Hi dear "dwhitney67";
 
I really don't know how should I thank you!
 
Your codes are very well, complete and professional.
 
 
Now I have a question:
 
Is it possible to ignore and remove "Config.cpp & Config.h" and only in the "main" function, we open the config file and read the it's value(EnableLogging) and check it using "isLogEnabled()" function to simplify the operation?
 
 
Sincerely.

---

### Post by nvteighen on 2010-07-01
> **dwhitney67 said:**
> Assuming the configuration file has contents with a format like:
```

EnableLogging = 1

```
then the following code could be used.

[...]

There's probably a dozen or more other ways this could be done.  This idea was the first that popped into my mind.

A singleton was the first thing that popped out from your mind? :D

---

### Post by slavik on 2010-07-01
Boost doesn't have a Config library?

---

### Post by slavik on 2010-07-01
Boost doesn't have a Config library?

---

### Post by dwhitney67 on 2010-07-01
.

---

### Post by dwhitney67 on 2010-07-01
.

---

### Post by dwhitney67 on 2010-07-01
> **nvteighen said:**
> A singleton was the first thing that popped out from your mind? :D

Yes, I was thinking that the configuration information would contain more than just one item, and it may be referenced in other areas of the application.  Since only *one* configuration object is required, I chose a singleton.

---

### Post by jeremy28 on 2010-07-02
> **jeremy28 said:**
> Hi dear "dwhitney67";
 
I really don't know how should I thank you!
 
Your codes are very well, complete and professional.
 
 
Now I have a question:
 
Is it possible to ignore and remove "Config.cpp & Config.h" and only in the "main" function, we open the config file and read the it's value(EnableLogging) and check it using "isLogEnabled()" function to simplify the operation?
 
 
Sincerely.
 
Any suggestion dear "dwhitney67" please?

---

### Post by jeremy28 on 2010-07-02
Hi Dear dwhitney67!
 
I wish to know your opinion about this:
```
int main(int argc, char **argv)
{
 
 string szCfgFileName = "MainConfig.cfg";
 if(argc > 1)
 {
  if(strstr(argv[1], "-c"))
  {
   if(argc > 2)
    szCfgFileName = string(argv[2]);
  }
 }
``` 
 
I mean, when in the command line we write "main -c MainConfig.cfg", the config file with the name in "szCfgFileName" parameter is opened and parsed and the "EnableLogging" is checked and then the remainder of main is run...
 
Without using "isLogEnabled" function!
 
How is it possible please?!
 
I do apologize again because of my too much questions!
 
I hope your help again...
 
Best Regards.

---

### Post by dwhitney67 on 2010-07-02
> **jeremy28 said:**
> 
I mean, when in the command line we write "main -c MainConfig.cfg", the config file with the name in "szCfgFileName" parameter is opened and parsed and the "EnableLogging" is checked and then the remainder of main is run...

No, the file is not opened using the code you posted above.  You have merely checked to see if two command line arguments have been provided to indicate the configuration filename.  The usage of getopt() would have been better in this case, but for now, I wouldn't worry about it.  Either way, all you are doing is saving the name of the default configuration filename in the variable 'szCfgFileName', and if the proper command line args exist, then resetting the variable to equal the value of argv[2].

> **jeremy28 said:**
>  
Without using "isLogEnabled" function!
 
How is it possible please?!

As stated above, the code you presented does not open the configuration file, thus it cannot know the state of whether logging should be enabled or not.

If you want to forgo the use of a configuration file, and instead pass the logging enabled flag via the command line, then you could easily do that.  But I was under the impression that you wanted to use a configuration file.

You need to think of isLogEnabled() as an "accessor" function; it merely reports the **state** of whether logging is enabled.  You have yet to determine this state.  If you use the code I offered earlier, it does determine this state.  Unfortunately you cannot cut corners in this effort.

To recap, you have two options:  1) use a configuration file which your code will have to _open and read_ to obtain the desired logging enabled state, or 2) pass the logging state via the command line.

---

### Post by jeremy28 on 2010-07-03
> **jeremy28 said:**
> 
I mean, when in the command line we write "main -c MainConfig.cfg", **the config file with the name in "szCfgFileName" parameter is opened and parsed and the "EnableLogging" is checked and then the remainder of main is run...**

 Hi
 
No, my intention from the BOLD section and "is opened" is "**to be open****ed and parsed and EnableLogging to be checked...**" 
Sorry, I wrote it in ambiguous form!!
 
I've not implemented it and as you mentioned, that piece of code only get the config file name from command line.
 
> To recap, you have two options: 1) use a configuration file which your code will have to _open and read_ to obtain the desired logging enabled state, or 2) pass the logging state via the command line. 
 
I want option "one", but I have still problem in opening and reading and parsing file to obtain the state?!
 
What would be the proper remainig of that code to do so please? 
 
>  The usage of getopt() would have been better in this case
Right, I saw the getopt() definition.That piece of code could be replaced with this function and checking options could be done in a switch!
 
> If you use the code I offered earlier, it does determine this state. Unfortunately you cannot cut corners in this effort.
 
Yes, I just wanted to know is it possible to simplify it, thanks.

---

### Post by dwhitney67 on 2010-07-03
> **jeremy28 said:**
> 
I want option "one", but I have still problem in opening and reading and parsing file to obtain the state?!


Earlier I offered you the code to accomplish this.  Why don't you use it?

---

