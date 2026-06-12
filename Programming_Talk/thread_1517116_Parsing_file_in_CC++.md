---
title: "Parsing file in C/C++"
date: 2010-06-24
forum: Programming Talk
---

### Post by Le-Froid on 2010-06-24
Hello there,

I am working on a little project, written in C++, and I'm sort of stuck right now. The application I'm writing is supposed to read a configuration file when it starts up, but I'm not that great at parsing text files :\

This is the way I'm writing the parser:

config.h
[php]
#ifndef _CONFIG_H
#define	_CONFIG_H

#include "Common.h"

enum ConfigType
{
    TYPE_INT = 0,
    TYPE_STRING = 1,
    TYPE_FLOAT = 2,
    TYPE_NONE = 3,
};

typedef struct
{
    const char* Name;   //Name of config var.
    ConfigType  Type;   //Type of config var.
    int32       MinVal; //Minimum value
    int32       MaxVal; //Maximum value
    //Values we fill depending on ConfigFormat.Type
    int32       IntVal;
    float       FloatVal;
    const char* StringVal;
} ConfigFormat;

class Config
{
public:
    Config(const char* file);
    ~Config();
    ConfigFormat* GetVal(const char* Name, ConfigType Type);
    ConfigFormat* GetVal(const char* Name, ConfigType Type, int32 Min, int32 Max);
private:
    FILE* pFile;
};

#endif	/* _CONFIG_H */
[/php]

config.cpp
[php]
#include "Config.h"


Config::Config(const char* file)
{
    pFile = fopen(file, "r");
}

ConfigFormat* Config::GetVal(const char* Name, ConfigType Type)
{
    int size; //size of file

    //get the size of the file
    fseek(pFile, 0L, SEEK_END);
    size = ftell(pFile);
    fseek(pFile, 0L, SEEK_SET);

    char buffer[size]; // where to store text
    
    //do this as long as the file hasn't reached the end of the stream
    while(!feof(pFile))
    {
        //read everything
        while(fgets(buffer, size, pFile))
        {
            //if it's more than 2 chars and the first char isn't a comment (#)
            if( ( sizeof(buffer) > 2) && (buffer[0] != '#') )
            {
                //    what now?
                printf(buffer);
            }
        }
        puts(buffer);
    }
}

ConfigFormat* Config::GetVal(const char* Name, ConfigType Type, int32 Min, int32 Max)
{

}

Config::~Config()
{
    fclose(pFile);
}
[/php]

And an example config file
```

# Mysql Information
DB Host = localhost
DB User = root
DB Password = password

```

and this is how you use the code:
[php]
Config* cfg = new Config("world.conf");
// read config
ConfigFormat* dbhost = cfg->GetVal("DB Host", TYPE_STRING);
// print its value (should say localhost if using config file shown above)
std::cout << dbhost->StringVal << std::endl;
[/php]

If anyone could give some pointers, it would be greatly appreciated :)

BTW I know my code is really sloppy, get over it :p

---

### Post by MadCow108 on 2010-06-24
Can't you just use a library which does this?
e.g. boost program_options or libconfig

And why are you using the C api when wrting c++ code?

c++ streams are easier to handle, especially for this kind of problem.
you can just fetch a whole line with getline
[http://www.cplusplus.com/reference/string/getline/](http://www.cplusplus.com/reference/string/getline/)
split it at the = into two parts e.g. by using getline with delimiter + stringstreams 
[http://www.cplusplus.com/reference/iostream/stringstream/](http://www.cplusplus.com/reference/iostream/stringstream/)
(or strtok)
and you have your key value pair (after trimming the spaces)

This could then be inserted into a map or a boost property_tree like structure for easy and fast lookup

---

### Post by SledgeHammer_999 on 2010-06-25
If by any chance you're using Gtkmm then you should take a look at [Glib::Keyfle](http://library.gnome.org/devel/glibmm/unstable/classGlib_1_1KeyFile.html)

---

### Post by dwhitney67 on 2010-06-25
> **Le-Froid said:**
> 
If anyone could give some pointers, it would be greatly appreciated :)

Make your programming life easier by defining a configuration file that is easier to parse.  Then the code will be easier.  For example:
```

# Mysql Information
DB_HOST     = localhost
DB_USER     = root
DB_PASSWORD = password

```
Note how white-space only exists before and after the equal sign.  With this approach, tokenizing a line read from the file becomes much easier.

Btw, as Madcow pointed out, you need to decide if you will be programming in C or C++.  Avoid doing both, for they are distinct languages, each with their own capabilities and shortcomings.

I should also add that I agree with the concept of using a map to store Key and Value pairs.  It makes the look-up of a value very easy.  You could also provide a function (or method within the Config class) that allows one to look-up a Value in the format they desire.  For example:
```

template <typename T>
T getVal(const char* keyID) const
{
   std::map<std::string, std::string>::const_iterator it = myValues.find(keyID);

   if (it != myValues.end())
   {
      std::stringstream iss(it->second);

      T rtn;

      iss >> rtn;

      return rtn;
   }

   throw std::runtime_error("KeyID not found!");
}

```

---

### Post by trent.josephsen on 2010-06-25
> **dwhitney67 said:**
> Btw, as Madcow pointed out, you need to decide if you will be programming in C or C++.  Avoid doing both, for they are distinct languages, each with their own capabilities and shortcomings.

On top of this, please don't ever use the phrase "C/C++".

---

### Post by nvteighen on 2010-06-25
Even if you want to follow your own approach instead of following dwhitney67's advice on improving the config file's format, please unify that struct with that class into a class. It's absurd to have a single "unit of meaning" (i.e. a concept) split in two pieces that way (data in struct, methods in class) for no reason.

---

### Post by Le-Froid on 2010-06-26
Well thanks for the advice everyone :)
I'm gonna go with what MadCow108 and dwhitney67 said and program only in c++. I used the mixed c and c++ method because I don't know much of the c++ standard library :\

---

