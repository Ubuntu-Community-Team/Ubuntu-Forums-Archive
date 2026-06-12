---
title: "C++ reading text configuration files"
date: 2010-11-12
forum: Programming Talk
---

### Post by barisurum on 2010-11-12
Hi there I've a problem reading a conf file with this function:

```
#include <iostream>
#include <fstream>
#include <string>
using namespace std;
............
blablablabla
............

    bool read_conf_file()
    {
        //VAR
            string lineBuf;
            string optionBuf;
            ifstream confFile( "myconffile.conf" );

        if ( confFile.is_open() )
        {
            while ( confFile.good() )
            {
                getline( confFile, lineBuf );
                cout << endl << lineBuf << endl;

                optionBuf = "Screen Width : ";
                if ( lineBuf.find( optionBuf ) )
                {
                    lineBuf.erase( 0, optionBuf.length() );
                    SCREEN_WIDTH = atoi( lineBuf.c_str() );
                }
            }
            confFile.close();
        }
    }
```

Whatever I do the lineBuf output ( cout << lineBuf ) is blank and SCREEN_WIDTH is = 0.. 
The first line of myconffile.conf is: 
```
Screen Width : 1440
```

What am I doing wrong here?

---

### Post by barisurum on 2010-11-12
Oooops my bad.. believe it or not I've edited the wrong myconffile.conf with gedit! and the one with the project working dir was empty.. Sorry :D

Now lineBuf output is correct, but SCREEN_WIDTH is still 0.. how can I correctly extract the int inside the string?

---

### Post by barisurum on 2010-11-12
Alright sorted it out myself. The correct code if you want to sneak a peek:

```
bool read_conf_file()
    {
        //VAR
            string lineBuf;
            string optionBuf;
            ifstream confFile( "myconffile.conf" );

        if ( confFile.is_open() )
        {
            while ( getline( confFile, lineBuf ) )
            {
                optionBuf = "Screen Width : ";
                if ( ( ( int )lineBuf.find( optionBuf ) ) != -1 )
                {
                    lineBuf.erase( 0, optionBuf.length() );
                    SCREEN_WIDTH = atoi( lineBuf.c_str() );
                }

            confFile.close();
            return true;
        }
        return false;
    }
```

---

### Post by dwhitney67 on 2010-11-12
Assuming all of you configuration items have a ":" separating the attribute and the value, then I would have gone with:
```

#include <string>
#include <sstream>
#include <iostream>

int main()
{
   std::string lineBuf = "Screen Width : 1440";

   size_t      pos   = lineBuf.find_first_of(":");
   std::string attr  = lineBuf.substr(0, pos - 1);
   size_t      value = 0;

   std::stringstream ss(lineBuf.substr(pos + 1));
   ss >> value;

   std::cout << attr << " is " << value << std::endl;
}

```
The tricky part w/ configuration files is when you allow a value to be either numeric or character string.  For example:
```

Screen Width : 1440
Allow Resize : False

```
If you have hundreds of configuration items, you can see that both your approach, and mine too, will fail and/or be too cumbersome to program.

Look into using the Boost Library for possible simplicity in parsing your configuration file.  Read more here: [http://www.boost.org/doc/libs/1_39_0/doc/html/program_options.html](http://www.boost.org/doc/libs/1_39_0/doc/html/program_options.html)

P.S.  Choose the version of Boost that is applicable to your system if v1.39 is not the correct version for your system.

---

### Post by barisurum on 2010-11-12
Ummm.. Not another library please. :D But you gave me a good idea. Thanks a lot. I'll try to program the configuration parser based on value types. I have three of them: integers, booleans and strings. The parser will make three different loops based on them.

1. get integers and assign them
2. get bools and assign them
3. get strings and assign them.

Maybe boost or another library is a much better idea, but using standart tools is allways better and the final product will be more portable to different environments.

---

### Post by nvteighen on 2010-11-13
> **barisurum said:**
> 
Maybe boost or another library is a much better idea, but using standart tools is allways better and the final product will be more portable to different environments.

That's a myth. Libraries are there to be used and to not have you lose your valuable time by reimplementing something that's been already implemented in a general solution, whereas you'll be probably implementing a solution particular to your specific needs.

---

### Post by barisurum on 2010-11-13
OK the new function is like this:

```
    bool read_conf_file( int optionIndexSize[3], int optionVarInt[], bool optionVarBool[], string optionVarStr[],
                         string optionIndexInt[], string optionIndexBool[], string optionIndexStr[] )
    {
        //VAR
            string lineBuf;
            int totalLines;
            string optionBuf;
            ifstream confFile( "myconffile.conf" );

        if ( confFile.is_open() )
        {
            while ( getline( confFile, lineBuf ) )
            {
                totalLines++;
            }

            confFile.clear();
            confFile.seekg(0);

            for ( int cnt = 0; cnt <= totalLines; cnt++ )
            {
                getline( confFile, lineBuf );

                for ( int cnt_2 = 0; cnt_2 < optionIndexSize[0], cnt_2++ )
                {
                    if ( ( ( int ) lineBuf.find( optionIndexInt[ cnt_2 ] ) != -1 ) )
                    {
                        lineBuf.erase( 0, optionIndexInt[ cnt_2 ].length() );
                        optionVarInt[ cnt_2 ] = atoi( lineBuf.c_str() );
                    }
                }

                for ( int cnt_2 = 0; cnt_2 < optionIndexSize[1], cnt_2++ )
                {
                    if ( ( ( int ) lineBuf.find( optionIndexBool[ cnt_2 ] ) != -1 ) )
                    {
                        lineBuf.erase( 0, optionIndexBool[ cnt_2 ].length() );
                        optionVarBool[ cnt_2 ] = ( lineBuf == "1" ? true : false );
                    }
                }

                for ( int cnt_2 = 0; cnt_2 < optionIndexSize[2], cnt_2++ )
                {
                    if ( ( ( int ) lineBuf.find( optionIndexStr[ cnt_2 ] ) != -1 ) )
                    {
                        lineBuf.erase( 0, optionIndexStr[ cnt_2 ].length() );
                        optionVarStr[ cnt_2 ] = lineBuf;
                    }
                }
            }
            
            confFile.close();
            return true;
        }
        return false;
    }
```

there may be off by one errors :) hope it will work... I await your valuable thoughts.

---

### Post by dwhitney67 on 2010-11-13
Rethinking what I originally posted, I believe better solution would be to store both key and value pairs as strings.  Only when the data is needed for use, should it be converted to the appropriate type (ie int, string, bool, etc).

Taking this notion a bit further, we can consider storing the value as a "universal" data object, which can be readily converted to the desired type.

Take the following for example:
```

#include <fstream>
#include <map>
#include <stdexcept>
#include <sstream>
#include <iostream>

class Data
{
public:
   Data(const std::string& data = "") : myData(data) {}

   operator int() const
   {
      std::stringstream ss(myData);
      int val = 0;
      ss >> val;

      if (ss.fail())
      {
         throw std::runtime_error("Cannot convert to int.");
      }
      return val;
   }

   operator const char*() const
   {
      return myData.c_str();
   }

   operator std::string() const
   {
      return myData;
   }

   operator bool() const
   {
      return myData == "true" || myData == "True" || myData == "TRUE";
   }

private:
   std::string myData;
};



class Config
{
public:
   Config(const char* filename, const char fieldSeparator = ':')
   {
      using namespace std;

      fstream file(filename, ios::in);

      if (file)
      {
         string line;

         while (getline(file, line))
         {
            size_t sep = line.find_first_of(fieldSeparator);

            if (sep != string::npos)
            {
               string key   = trim(line.substr(0, sep));
               string value = trim(line.substr(sep + 1));

               if (!key.empty() && !value.empty())
               {
                  myConfigItems[key] = Data(value);
               }
               else
               {
                  throw runtime_error("Error within configuration file.");
               }
            }
            else
            {
               throw runtime_error("Error within configuration file.");
            }
         }
      }
      else
      {
         throw runtime_error("Cannot open config file.");
      }
   }

   Data get(const std::string& key) const
   {
      std::map<std::string, Data>::const_iterator it = myConfigItems.find(key);

      if (it != myConfigItems.end())
      {
         return it->second;
      }
      else
      {
         throw std::runtime_error("Cannot find config item.");
      }
   }

   friend std::ostream& operator<<(std::ostream& os, const Config& config)
   {
      for (std::map<std::string, Data>::const_iterator it = config.myConfigItems.begin();
           it != config.myConfigItems.end();
           ++it)
      {
         const std::string& key = it->first;
         const std::string  val = it->second;

         std::cout << key << "\t" << val << std::endl;
      }

      return os;
   }

private:
   std::string trim(std::string str)
   {
      size_t pos = str.find_first_not_of(" \t\n");

      if (pos != std::string::npos)
      {
         str.erase(0, pos);
      }

      pos = str.find_last_not_of(" \t\n");

      if (pos != std::string::npos)
      {
         str.erase(pos + 1);
      }

      return str;
   }

   std::map<std::string, Data> myConfigItems;
};


int main(int argc, char** argv)
{
   try
   {
      const char* cfgFilename = argv[1];

      Config cfg(cfgFilename);

      int         width       = cfg.get("Screen Width");
      int         height      = cfg.get("Screen Height");
      std::string monitorType = cfg.get("Monitor Type");
      bool        dpmsEnabled = cfg.get("DPMS Enabled");

      std::cout << "Screen Width : " << width       << "\n"
                << "Screen Height: " << height      << "\n"
                << "Monitor Type : " << monitorType << "\n"
                << "DPMS Enabled : " << (dpmsEnabled ? "true" : "false")
                << std::endl;
   }
   catch (std::exception& e)
   {
      std::cerr << e.what() << std::endl;
      return -1;
   }
}

```

I tested the code above with the following configuration file:
```

Screen Width  : 1600
Screen Height : 900
Monitor Type  : LCD
DPMS Enabled  : false

```

---

### Post by barisurum on 2010-11-13
WOW You have some good abstraction there! I'll follow your lead.. thank you soooo much! :)

---

