---
title: "C++ Parsing a file."
date: 2007-09-15
forum: Programming Talk
---

### Post by Rasitiln on 2007-09-15
I'd like to parse a config file so that each option is stored with in the proper variable upon start of a program, it's a simple clock program and would have two variables in the config file.


```

Type = 24
# The display mode for the clock (24 ,12, binary)
Alarm = 12:00 
#always in twenty four hour format. hh:mm 

```

Thank you to anyone that can point  me to some tutorials or documentation that could help me in this aspect.

---

### Post by dwhitney67 on 2007-09-16
If you had a data file that was formatted simpler, it would be a cake walk to implement something easy for you.  And when I mean simpler, something like:

Type = 24 Alarm = 12:00

However, the example config file you provided shows the relevant data on separate lines, and comment-lines in between.  Thus the easiest I could come up with to parse a file is shown below, and that code assumes that the config file you provided does not have any additional entries.

I'm sure some niftier programmer will have an easier way to do this, so weigh in if you like.

[PHP]#include <string>
#include <iostream>
#include <fstream>
#include <sstream>

using namespace std;


int main( int argc, char** argv )
{
  // Ensure that the data file name is supplied on the command line.
  // If not, then exit.
  if ( argc != 2 )
  {
    cout << "Usage: " << argv[0] << " <data file>" << endl;
    exit( 1 );
  }

  // Attempt to open the data file.
  ifstream dataFile( argv[1] );

  // Verify the data file was opened; exit if not.
  if ( !dataFile )
  {
    cout << "Error:  Cannot open file " << argv[1] << endl;
    exit( 1 );
  }

  // Location where the relevant data will be stored.
  struct DataLayout
  {
    int    type;
    string alarm;
  };
  DataLayout theData;
  

  // Parse the data file
  while ( ! dataFile.eof() )
  {
    char buf[ 80 ] = {0};
    string firstField;
    string secondField;
    string data;

    dataFile.getline( buf, sizeof( buf ) );

    istringstream istr( string(buf), ios_base::out );

    istr >> firstField >> secondField >> data;

    if ( firstField == "Type" )
    {
      theData.type = atoi( data.c_str() );
    }
    else if ( firstField == "Alarm" )
    {
      theData.alarm = data;
    }
  }

  cout << "theData.type  = " << theData.type
       << endl
       << "theData.alarm = " << theData.alarm
       << endl;
}[/PHP]

---

### Post by slavik on 2007-09-16
I suggest this:
1. read the line into a buffer, strip beginning and ending whitespace
2. if the first character is a '#', go to 1.
3. split the string on equal sign and use a hash to store the two (and make any conversions needed).

if using another language in addition to C++ is an option.
another thing you can do is write a wrapper script in perl/ruby/python around your program and instead have it create commandline parameters. then add getopt to your program.

---

### Post by gnusci on 2007-09-16
This program read the file config.cfg

[PHP]
// configure.cxx
#include <iostream>
#include <fstream>

using namespace std;

// program main function
int main( int argc, char ** argv )
{
    char _buff[1024], _ch=' ', tag[24];
    float val;
    ifstream cfg("config.cfg");

    while( !cfg.eof() ){
        _ch = cfg.get();
        printf("[%c]\n",_ch);
        if(_ch != '#' && _ch != '\n'){
            cfg.getline(_buff,1024);
            //puts(_buff);
            sscanf(_buff,"%s %*s %f",tag,&val);
            printf("Tag: [%c]%s Value: %f\n",_ch,tag,val);
        }
        cfg.ignore(1024,'\n');
        _ch = cfg.peek();
        while(_ch==' ' && _ch=='\n'){
            cfg.ignore(1024,'\n');
            _ch = cfg.peek();
        }
    }
    cfg.close();
    return 0;
}

[/PHP]

here is the file: config.cfg
```

Type = 24
# The display mode for the clock (24 ,12, binary)
Alarm = 12:00
#always in twenty four hour format. hh:mm

```

It reads and looks for the not marked (with "**#**") lines within the config.cfg file, and then analyze the structure of line with the format:

```
[COLOR="Red"]TAG[/COLOR] = [COLOR="DeepSkyBlue"]VALUE[/COLOR]
```

Actually is an implementation to the algorithm described by **slavik** above.

EDIT: Because your are new I am giving you extra instructions:

1) save the program to the file **configure.cxx**

2) save the configuration to the file **config.cfg**

3) compile the code:

   **> gcc configure.cxx -o configure**

4) run the program:
   **> ./configure**

---

### Post by Rasitiln on 2007-09-16
Thanks everyone I'm pretty new so I'm currently decoding all this!

---

