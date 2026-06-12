---
title: "C/C++ save program options"
date: 2009-07-19
forum: Programming Talk
---

### Post by djbushido on 2009-07-19
I am trying to write a program in C++ right? So I need to save some options (like window size, etc.). What would be the easiest way to do this? I would like something to parse a file like this:```
FULLSCREEN = true
WINDOW_WIDTH = 640
WINDOW_HEIGHT = 480
``` And etc., etc.
I am thinking that I don't really need XML for this, but would like a way to be able to say something like: ```
int main(){
bool fullscreen = parse("FULLSCREEN")
bool width = parse("WINDOW_WIDTH")}
``` So it's not compilable, but I think you get the idea. Thanks for the help!

---

### Post by dwhitney67 on 2009-07-19
There's nothing wrong with what you are planning.  Parsing text files is nothing new.

You could use Boost's tokenizer object to simplify things quite a lot, or just write your own parser.  Either way, you will still need to open the file and read it line by line.

For the code you posted, the only thing "wrong" with it is that width should be an int, or better yet an unsigned int... not a bool.

Something like this is achievable (I know, because I just finished writing the code :) ).
```

int main(int argc, char** argv)
{
   OptionParser parser(argv[1]);   // parse options file.

   bool fullscreen = parser.value("FULLSCREEN");
   int  winWidth   = parser.value("WINDOW_WIDTH");
   int  winHeight  = parser.value("WINDOW_HEIGHT");

   ...
}

```

---

### Post by dribeas on 2009-07-20
Depending on what you want to do, and mostly how much time you want to invest in learning, you could take a look at boost:: program_options.

The library is meant to process program arguments, but can work with configuration files stored with a format similar (if not exactly) to .ini files.

---

### Post by djbushido on 2009-07-21
Alright, so the code was a little wacky. I would have eventually figured out that trying to assign 640 to a bool wouldn't work.

Anyway, I also found this: [http://www.boost.org/doc/libs/1_39_0/doc/html/boost/program_options/parse_config_file.html](http://www.boost.org/doc/libs/1_39_0/doc/html/boost/program_options/parse_config_file.html)

I didn't know if maybe that would work, I just don't know how to make it work.

EDIT: Maybe regex? Search for an option and then parse that way?

---

### Post by dribeas on 2009-07-21
It's been long since I first read the boost:: program_options docs (almost two years), and at the end we did not use it at all.

This is a test out of the tutorial modified with the docs in the page you reference. You should tailor it for your concrete requisites, enhance exception support (as it is if it encounters an unrecognized option it will die)...

```

#include <iostream>
#include <fstream>
#include "boost/program_options.hpp"

namespace po = boost::program_options;

int main( int argc, char** argv )
{
    bool fullscreen;
    int width, height;
    po::options_description desc( "Allowed options" );
    desc.add_options()
            ( "help", "produce help message" )
            ( "full_screen", po::value<bool>(&fullscreen)->default_value(false),
                    "start application in fullscreen mode" )
            ( "width", po::value<int>(&width)->default_value(640),
                    "screen width in pixels" )
            ( "height", po::value<int>(&height)->default_value(480),
                    "screen height in pixels" )
            ;

    po::variables_map vm;
//  po::store( po::parse_command_line( argc, argv, desc ), vm ); // to read command line options
    std::ifstream cfile( "test.cfg" );
    po::store( po::parse_config_file( cfile, desc), vm );
    po::notify( vm );

    if (vm.count("help") )
    {  
        std::cout << desc << std::endl;
    }
    else
    {  
        std::cout << "fullscreen=" << fullscreen << std::endl
            << "width=" << width << std::endl
            << "height=" << height << std::endl;
    }
}

```

---

### Post by djbushido on 2009-07-21
I think I'll make this it's own file, but yeah, I can encapsulate that with like a bool parse() option instead of int main, but yeah, that will work. Thanks!

---

### Post by dribeas on 2009-07-21
> **djbushido said:**
> I think I'll make this it's own file, but yeah, I can encapsulate that with like a bool parse() option instead of int main, but yeah, that will work. Thanks!

One of the advantages of using the library is that you can override the configuration file values with command line options. Say you have in your config that the application should not run in full screen mode but at one time you want to try it: combine the config file and arguments to override the configuration values:

```

$ ./my_program --full_screen=1

```

---

### Post by djbushido on 2009-07-21
would I just move the commented command-line parsing to after the infile parsing?

---

### Post by dribeas on 2009-07-22
> **djbushido said:**
> would I just move the commented command-line parsing to after the infile parsing?

Check the docs, I have never really used program_options.

---

### Post by dwhitney67 on 2009-07-22
Here's the non-Boost approach I tinkered with the other day:
```

#include <fstream>
#include <map>
#include <string>
#include <sstream>
#include <stdexcept>
#include <iostream>
#include <cstdlib>
#include <cstring>

class OptionParser
{
public:
   OptionParser(const char* optionsFile);

   class OptVal
   {
   public:
      OptVal(const std::string& val) : m_optVal(val) {}

      inline operator bool() const { return strncmp(m_optVal.c_str(), "true", m_optVal.size()) == 0; }
      inline operator int() const { return atoi(m_optVal.c_str()); }
      inline operator std::string() const { return m_optVal; }

   private:
      std::string m_optVal;
   };

   const OptVal& value(const std::string& optName) const;

private:
   typedef std::map<std::string, OptVal> Options;

   Options m_options;
};

OptionParser::OptionParser(const char* optionsFile)
{
   using namespace std;

   fstream file(optionsFile, ios::in);

   if (file)
   {
      string line;

      while (getline(file, line))
      {
         if (line.size() == 0 || ((line[0] == '#' || line[0] == '\n'))) continue;

         // get option name
         size_t beg = 0;
         size_t end = line.find_first_of(' ');
         string optName = line.substr(beg, line.size() - line.substr(end).size());

         // find assignment operator; ignore line if not found.
         if ((beg = line.find_first_of('=')) == string::npos) continue;

         // get value; ignore line if not found.
         if ((beg = line.find_first_not_of(' ', beg + 1)) == string::npos) continue;
         string optVal = line.substr(beg);

         m_options.insert(make_pair(optName, OptVal(optVal)));
      }
   }
   else
   {
      throw runtime_error("Error: options file could not be opened.");
   }
}

const OptionParser::OptVal&
OptionParser::value(const std::string& optName) const
{
   Options::const_iterator it = m_options.find(optName);

   if (it == m_options.end())
   {
      throw std::runtime_error("Error: unknown option name given.");
   }

   return it->second;
}


int main(int argc, char** argv)
{
   try
   {
      OptionParser parser(argv[1]);

      const bool fullscreen = parser.value("FULLSCREEN");
      const int  winWidth   = parser.value("WINDOW_WIDTH");
      const int  winHeight  = parser.value("WINDOW_HEIGHT");

      std::cout << "fullscreen = " << (fullscreen ? "true" : "false") << std::endl;
      std::cout << "winWidth   = " << winWidth   << std::endl;
      std::cout << "winHeight  = " << winHeight  << std::endl;
   }
   catch (std::exception& e)
   {
      std::cerr << e.what() << std::endl;
      return 1;
   }
}

```

The options file looks like:
```

# This line is a comment

FULLSCREEN    = true
WINDOW_WIDTH  = 640
WINDOW_HEIGHT = 480

```

---

### Post by djbushido on 2009-08-01
I think that would work well - that way the parser module is dynamic and I don't have to keep changing it. I'm down for this. Thanks! Probably will do ios::binary just for the sake of making sure that it won't get tinkered with by anything but the program. Also have to figure out how to write out said file. That's for later though. Shouldn't be too hard anyway.

EDIT: I can compile ok, but the test program you gave me always produces an "unknown option name" error.

---

