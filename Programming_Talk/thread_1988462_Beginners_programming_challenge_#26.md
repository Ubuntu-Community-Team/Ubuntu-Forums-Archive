---
title: "Beginners programming challenge #26"
date: 2012-05-27
forum: Programming Talk
---

### Post by Bodsda on 2012-05-27
_[SIZE=4][COLOR=Red]Welcome to the 26th Beginners programming challenge.[/COLOR][/SIZE]_

First off, I need to once again apologise for not keeping up with this. The last few months have been giving me some challenges that programming just can't solve. Anyway, here is challenge #26. 


_**Task**_

The challenge is to write a program that can take a valid integer and output the english name of that number. For example

100 - One Hundred
72 - Seventy two
7655 - Seven thousand six hundred fifty five

_**Cookie points**_

Cookie points will be awarded for the following extras

[LIST=1]
[*]Allowing multiple input choices - e.g. command line switch, interactive, file
[*]Correctly handle integers including separators (1,345  66,700 500,81,500 etc)
[*]Correctly handle negative numbers
[*]Grammatically correct output (566 being Five hundred **and** sixty six)
[/LIST]

_***Disqualified Entries:***_

Any overly obfuscated code will be immediately disqualified without    account for programmers skill. Please remember that these challenges are    for beginners and therefore the code should be easily readable and   well  commented.

Any non-beginner entries will not be judged. Please use common sense    when posting code examples. Please do not give beginners a copy paste    solution before they have had a chance to try this for themselves.


_***Assistance:***_

If you require any help with this challenge please do not hesitate to    come and chat to the development focus group. We have a channel on    irc.freenode.net #ubuntu-beginners-dev
Or you can pm me

Have fun,
Happy coding

Bodsda
Ubuntu Beginners Team

---

### Post by kingtaurus on 2012-05-30
> **Bodsda said:**
> _[SIZE=4][COLOR=Red]Welcome to the 26th Beginners programming challenge.[/COLOR][/SIZE]_

First off, I need to once again apologise for not keeping up with this. The last few months have been giving me some challenges that programming just can't solve. Anyway, here is challenge #26. 


_**Task**_

The challenge is to write a program that can take a valid integer and output the english name of that number. For example

100 - One Hundred
72 - Seventy two
7655 - Seven thousand six hundred fifty five

_**Cookie points**_

Cookie points will be awarded for the following extras

[LIST=1]
[*]Allowing multiple input choices - e.g. command line switch, interactive, file
[*]Correctly handle integers including separators (1,345  66,700 500,81,500 etc)
[*]Correctly handle negative numbers
[*]Grammatically correct output (566 being Five hundred **and** 66)
[/LIST]

_***Disqualified Entries:***_

Any overly obfuscated code will be immediately disqualified without    account for programmers skill. Please remember that these challenges are    for beginners and therefore the code should be easily readable and   well  commented.

Any non-beginner entries will not be judged. Please use common sense    when posting code examples. Please do not give beginners a copy paste    solution before they have had a chance to try this for themselves.


_***Assistance:***_

If you require any help with this challenge please do not hesitate to    come and chat to the development focus group. We have a channel on    irc.freenode.net #ubuntu-beginners-dev
Or you can pm me

Have fun,
Happy coding

Bodsda
Ubuntu Beginners Team

Couple of quick questions:
(1) Should we also handle separators that correspond to different localizations (i.e. comma separators (en_CA.utf8), period separators (de_DE.utf8 for example), ... is there anymore?)?
(2) Should we assume simple newline (or tab) separation between entries in the file?

Cheers,

---

### Post by kingtaurus on 2012-05-31
My solution is below (this challenge is similar to,[ Project Euler #17]("http://projecteuler.net/problem=17")). It relies upon a few boost libraries [program_options]("http://www.boost.org/doc/libs/1_49_0/doc/html/program_options.html") and [lexical_cast]("http://www.boost.org/doc/libs/1_49_0/doc/html/boost_lexical_cast.html");

The logic required to convert a integral type (in this case a long) is relatively simple. However the parsing is a little more troublesome;

```

//Compiles with g++/clang++
//g++  number_to_string_number.cpp -lboost_program_options -g3
//clang++  number_to_string_number.cpp -lboost_program_options -g3
#include <string>
#include <iostream>
#include <iomanip>
#include <map>
#include <cmath>
#include <stdexcept>
#include <limits>

#include <sstream>
#include <fstream>

#include <cxxabi.h>
//wrote some a custom simple converter
//it relies upon std::type_info to output template class info.
//NOTE: __not__ used currently in the code below
//
#include <locale>
//BELOW is a listing of localizations available on my computer
//TO install a new one:
//sudo aptitude install language-pack-de
//sudo aptitude install language-pack-fr
//-------
//locale -a
//C
//C.UTF-8
//en_AG
//en_AG.utf8
//en_AU.utf8
//en_BW.utf8
//en_CA.utf8
//en_DK.utf8
//en_GB.utf8
//en_HK.utf8
//en_IE.utf8
//en_IN
//en_IN.utf8
//en_NG
//en_NG.utf8
//en_NZ.utf8
//en_PH.utf8
//en_SG.utf8
//en_US.utf8
//en_ZA.utf8
//en_ZM
//en_ZM.utf8
//en_ZW.utf8
//POSIX


#include <boost/program_options.hpp>
#include <boost/program_options/variables_map.hpp>
#include <boost/lexical_cast.hpp>

#include <boost/program_options.hpp>
#include <boost/program_options/variables_map.hpp>
#include <boost/lexical_cast.hpp>

const long hundred  = 100L;
const long thousand = 1000L;
const long million  = 1000000L;
const long billion  = 1000000000L;

std::map<long, std::string> number_to_name_string;

void populate_map()
{//simple lookup
  number_to_name_string[0L] = "zero";
  number_to_name_string[1L] = "one";
  number_to_name_string[2L] = "two";
  number_to_name_string[3L] = "three";
  number_to_name_string[4L] = "four";
  number_to_name_string[5L] = "five";
  number_to_name_string[6L] = "six";
  number_to_name_string[7L] = "seven";
  number_to_name_string[8L] = "eight";
  number_to_name_string[9L] = "nine";
  number_to_name_string[10L] = "ten";
  number_to_name_string[11L] = "eleven";
  number_to_name_string[12L] = "twelve";
  number_to_name_string[13L] = "thirteen";
  number_to_name_string[14L] = "fourteen";
  number_to_name_string[15L] = "fifteen";
  number_to_name_string[16L] = "sixteen";
  number_to_name_string[17L] = "seventeen";
  number_to_name_string[18L] = "eighteen";
  number_to_name_string[19L] = "nineteen";
  number_to_name_string[20L] = "twenty";

  number_to_name_string[30L] =  "thirty";
  number_to_name_string[40L] =  "forty";
  number_to_name_string[50L] =  "fifty";
  number_to_name_string[60L] =  "sixty";
  number_to_name_string[70L] =  "seventy";
  number_to_name_string[80L] =  "eighty";
  number_to_name_string[90L] =  "ninety";
  number_to_name_string[hundred]     = "hundred";
  number_to_name_string[thousand]    = "thousand";
  number_to_name_string[million]     = "million";
  number_to_name_string[billion]     = "billion";
  //figured the farthest I need to go was billions
}

std::string convert_to_word(const long & number);
//driver of the converter;
//handles 0 and negative numbers;
//calls convert_to_word_core(number);

std::string convert_to_word_core(const long & number);
//postive number handler
//calls sub-handlers depending on size of the number

std::string process_large(const long & number, const long mod)
{
  //Throw a runtime_error (if arguements are incorrectly used)
  if (mod < thousand)
  {
    throw std::runtime_error(std::string("Invalid use of function " ) + __PRETTY_FUNCTION__ + "\n\t2nd arguement is too small;" );
  }
  if (number < mod)
  {
    throw std::runtime_error(std::string("Invalid use of function " ) + __PRETTY_FUNCTION__ + "\n\t1st argument must be larger than 2nd;");
  }

  std::string large_number_string = convert_to_word_core( number / mod ) + " " + number_to_name_string[mod];

  if (number % mod == 0)
    return large_number_string;

  if (number % mod < hundred)
    return large_number_string + " and " + convert_to_word_core(number%mod);

  return large_number_string + " " + convert_to_word_core(number%mod);
}

std::string process_hundred(const long & number)
{
  if (number < 100)
  {
    throw std::runtime_error(std::string("Invalid use of function " ) +  __PRETTY_FUNCTION__ + "\n\t1st arguement must be larger than 100;");
  }
  std::string hundred_string = number_to_name_string[number/100] + " " + number_to_name_string[hundred];
  
  if (number % 100 == 0)
    return hundred_string;
  return hundred_string +=(" and " + convert_to_word_core(number % 100));
}

std::string process_tens(const long & number)
{
  if (number < 10 || number > 99) throw std::runtime_error(std::string("Invalid use of function " ) + __PRETTY_FUNCTION__ + "\n\t1st arguement must be between 10 and 99;");
  if (number < 20)
    return number_to_name_string[number];

  std::string ten_string = number_to_name_string[number - number%10];

  if (number % 10 == 0)
    return ten_string;

  return ten_string += " " + number_to_name_string[number%10];  
}

std::string convert_to_word(const long & number)
//remove simple cases
{
  if (number == 0)
  {
    return number_to_name_string[0L];
  }
  if (number < 0)
  {
    return "negative " +  convert_to_word_core( - number);
  }
  return convert_to_word_core(number);
}

std::string convert_to_word_core(const long & number)
{
  if (number >= billion)
  {
    return process_large(number,billion);
  }
  else if (number < billion && number >= million)
  {
    return process_large(number,million);
  }
  else if (number < million && number >= thousand)
  {
    return process_large(number,thousand);
  }
  else if (number < thousand && number >= hundred)
  {
    return process_hundred(number);
  }
  else if (number < hundred && number >= 10L)
  {
    return process_tens(number);
  }
  else
  {
    return number_to_name_string[number];
  }
}

namespace po = boost::program_options;

//REMOVED for brevity: __test__ code:
// (1) checks throws in process_large, process_tens, process_hundred
// (2) checks that boost::lexical_cast<long> throws when using wrong locale
//     ["de_DE.utf8" throws when using commas as a numerical thousand separator]
// (3) unit tests on a series of numbers

int main(int argc, char * argv[])
{
  std::locale current_global_locale();//grab locale (programs default locale)
  std::locale::global(std::locale("en_CA.utf8"));//set locale to one with comma seperated locale
  populate_map();

  po::positional_options_description positional;
  positional.add("number",-1);//treat anything not after a switch as number
  
  std::vector<long>       nums;//numbers to parse
  std::vector<std::string> files;//files to open and attempt to parse

  po::options_description desc("Allowed options");
  desc.add_options()
    ("help,h", "Produces a help message")
    ("files",      po::value<std::vector<std::string> >(&files)->multitoken(), "Converts numbers listed in a file")
    ("user-entry", "Converts numbers entered by a user")
    ("number",     po::value<> (&nums)->multitoken(),  "Converts a number (seperated by spaces); \n Quote negative numbers; like \"-1\";")
  ;

  po::variables_map vm;   //default vm (uses en_CA.utf8)
  po::variables_map vm_de;//alternate vm (uses de_DE.utf8)
  po::parsed_options parsed = 
     po::command_line_parser(argc, argv).options(desc).positional(positional).allow_unregistered().run();
  //technically I could write my own validator (that would handle either case);
  //but I will assume that only one type of locale is used for commandline numerical input

  try
  {
    std::cerr << "Trying with en_CA.utf8." << std::endl;
    po::store( parsed, vm);
    std::cerr << "Success!" << std::endl;
  }
  catch(const po::validation_error & ex)
  {
    std::cerr << "Caught-> " << ex.what() << std::endl;
    std::cerr << "Numerical values are not valid in locale en_CA.utf8;" << std::endl;
    std::cerr << "Can't store values found on the command line in std::vector<long>;" << std::endl;
    std::cerr << "Trying with de_DE.utf8." << std::endl;
    std::locale::global(std::locale("de_DE.utf8"));
    try
    {
      po::store(parsed,vm_de);
      std::cerr << "Success!" << std::endl;
      vm = vm_de;
    }
    catch(const po::validation_error & de_ex)
    {
      std::cerr << "Numerical values are not valid in locale de_DE.utf8" << std::endl;
      std::cerr << "Can't store values found on the command line in std::vector<long>" << std::endl;
      throw std::runtime_error("Values on the command line are not valid numbers in either de_DE.utf8 or en_CA.utf8");
    }
  }
  po::notify(vm);

  if (vm.count("help"))
  {
    std::cout << desc << std::endl;
    return 1;
  }

  std::vector<std::string> to_pass_further = collect_unrecognized(parsed.options, po::include_positional);

  for(size_t i = 0; i < to_pass_further.size(); ++i)
  {
    std::cerr << "Unrecognized switch " << to_pass_further[i] << std::endl;
    std::cerr << "Quote negative numbers; like \"-1\";" << std::endl;
    std::cout << "Trying to convert " << to_pass_further[i] << " using en_CA.utf8." << std::endl;
    long number;
    try
    {
      std::locale::global(std::locale("en_CA.utf8"));
      number = boost::lexical_cast<long>(to_pass_further[i]);
      std::cout << number << "\t--> " << convert_to_word(number) << std::endl;
    }
    catch (boost::bad_lexical_cast& en_error)
    {
      try
      {
        std::cerr << "Unable to convert " << to_pass_further[i] << " to a long (using en_CA.utf8). Trying with de_DE.utf8." << std::endl;
        std::locale::global(std::locale("de_DE.utf8"));
        number = boost::lexical_cast<long>(to_pass_further[i]);
        std::cout << number << "\t--> " << convert_to_word(number) << std::endl;
      }
      catch (boost::bad_lexical_cast& de_error)
      {
        std::locale::global(std::locale("en_CA.utf8"));//revert back to original
        std::cerr << "Unable to convert " << to_pass_further[i] << " to a long (using en_CA.utf8 or de_DE.utf8)." << std::endl;
        continue;
      }
    }
  }//negative numbers look like switches

  if (vm.count("number"))
  {
    //std::cout << vm.count("number") << std::endl;
    vm["number"].as< std::vector<long> >();
    for(size_t i = 0; i < nums.size(); ++i)
    {
      std::cout << nums[i] << "\t--> " << convert_to_word(nums[i]) << std::endl;
    }
  }

  if (vm.count("files"))
  {
    //std::cout << vm.count("files") << std::endl;
    vm["files"].as<std::vector<std::string> > ();
    for(size_t i = 0; i < files.size(); ++i)
    {
      long number;
      std::cout << "Attempting to read from " << files[i] << std::endl;
      std::ifstream infile(files[i].c_str());
      infile.imbue(std::locale("en_CA.utf8"));
      if (!infile)
      {
        std::cout << "Failed to open file " << files[i] << std::endl;
        try
        {
          std::cout << "Trying to use " << files[i] << " as numerical input!" << std::endl;
          number = boost::lexical_cast<long>(files[i]);
          std::cout << number << "\t--> " << convert_to_word(number) << std::endl;
        }
        catch(boost::bad_lexical_cast & e)
        {

        }
        continue;//ignore the file
      }

      while (infile.good())
      {
        infile >>  number;//attempt to read a number
        if ((infile.rdstate() & std::ifstream::failbit ) != 0 && !infile.eof())
        {
          std::cerr << "Error reading number from " << files[i] << std::endl;
          infile.close();//read failed, so close the file;
          break;
        }//check the state of the stream
        if (infile.eof()) break;//if we are now at the EOF (need to leave the loop)
        std::cout << number << "\t--> " << convert_to_word(number) << std::endl;
      }
      infile.close();//close the file
    }
  }

  if(vm.count("user-entry"))
  {
    std::cout << "Requested user entry (type quit to terminate)" << std::endl;
    std::string number;
    long a;
    do
    {
      std::cin >> number;
      if (number == "quit")
      {
        std::cout << "Goodbye" << std::endl;
        return 0;
      }

      try
      {
        std::locale::global(std::locale("en_CA.utf8"));
        std::cout << "Trying to convert " << number << " using en_CA.utf8." << std::endl;
        a = boost::lexical_cast<long>(number);
        std::cout << "Conversion successful." << std::endl;
        std::cout << a << "\t--> " << convert_to_word(a) << std::endl;
        continue;
      }
      catch(boost::bad_lexical_cast& e)//lexical_cast failed
      {
        std::cerr << "Unable to convert " << number << " to a long (using en_CA.utf8). Trying with de_DE.utf8." << std::endl;
        std::locale::global(std::locale("de_DE.utf8"));
        try
        {
          a = boost::lexical_cast<long>(number);
          std::cout << "Conversion successful." << std::endl;
          std::cout << a << "\t--> " << convert_to_word(a) << std::endl;
          continue;
        }
        catch(boost::bad_lexical_cast& e)
        {
          std::locale::global(std::locale("en_CA.utf8"));//revert back to original
          std::cerr << "Unable to convert " << number << " to a long (using en_CA.utf8 or de_DE.utf8)." << std::endl;
          continue;
        }
      }
    }
    while (std::cin.good());
  }  
  return 0;
}

```

Using the file, test_file:
```

1512
1516
128086507
120701

```

The following commandline arguements
```

./a.out --files test_file  test_file  test_file 10249 --user-entry -1 -204.045 --number 100.000

```
the program responds:
```

Trying with en_CA.utf8.
Caught-> in option 'number': invalid option value
Numerical values are not valid in locale en_CA.utf8;
Can't store values found on the command line in std::vector<long>;
Trying with de_DE.utf8.
Success!
Unrecognized switch -1
Quote negative numbers; like "-1";
Trying to convert -1 using en_CA.utf8.
-1	--> negative one
Unrecognized switch -204.045
Quote negative numbers; like "-1";
Trying to convert -204.045 using en_CA.utf8.
Unable to convert -1 to a long (using en_CA.utf8). Trying with de_DE.utf8.
-204045	--> negative two hundred and four thousand and forty five
100000	--> one hundred thousand
Attempting to read from test_file
1512	--> one thousand five hundred and twelve
1516	--> one thousand five hundred and sixteen
128086507	--> one hundred and twenty eight million eighty six thousand five hundred and seven
120701	--> one hundred and twenty thousand seven hundred and one
Attempting to read from test_file
1512	--> one thousand five hundred and twelve
1516	--> one thousand five hundred and sixteen
128086507	--> one hundred and twenty eight million eighty six thousand five hundred and seven
120701	--> one hundred and twenty thousand seven hundred and one
Attempting to read from test_file
1512	--> one thousand five hundred and twelve
1516	--> one thousand five hundred and sixteen
128086507	--> one hundred and twenty eight million eighty six thousand five hundred and seven
120701	--> one hundred and twenty thousand seven hundred and one
Attempting to read from 10249
Failed to open file 10249
Trying to use 10249 as numerical input!
10249	--> ten thousand two hundred and forty nine
Requested user entry (type quit to terminate)
100.002
Trying to convert 100.002 using en_CA.utf8.
Unable to convert 100.002 to a long (using en_CA.utf8). Trying with de_DE.utf8.
Conversion successful.
100002	--> one hundred thousand and two
100,002
Trying to convert 100,002 using en_CA.utf8.
Conversion successful.
100002	--> one hundred thousand and two
100002
Trying to convert 100002 using en_CA.utf8.
Conversion successful.
100002	--> one hundred thousand and two
quit
Goodbye

```

---

### Post by papibe on 2012-06-04
Hi Bodsda.

I want to participate, if I can.

I have a working draft. I expect to be done and post it in the next 24hrs.

Best Regards.

---

### Post by Odexios on 2012-06-04
C entry.

I wrote it during a break from studying, so I didn't test it thoroughly; at first glance everything seems to work, though.

It works with stdin input, file input and command line input, and I think I implemented all the cookie points.

If I find a little more time in the future I'm going to comment it a little bit more.

Any comment / critic / advice is appreciated!

(Be patient if something sounds strange, as you can probably see I'm not from an English-speaking country)

EDIT: I added some comments, took care of the negative case and checked if the given number is in range.

Usage (taken from the help built in the program):

```
./int_to_words [expression]
Where 'expression' is constituted by:
- Integers
- -f or --file followed by the name of the file from wich you want to get the numbers to be printed
- -s or --stdin if you want the integers to be taken from stdio
You can combine these options in any way you'd like;
Example:
./int_to_words 1235 123,456 --file nameofile 45678 -s 12
```

It ignores any string which isn't numeric; if the input is taken from stdin, it goes on until it meets a newline, while if it's taken from a file it goes on until it meets an EOF.

File example:
```
kk 1234 pp asd 
123

sd
1234,56
123,456
2147483647
10000000000
```

Output:
```

./int_to_words -f file
One Thousand, Two Hundred and Thirty-Four
One Hundred and Twenty-Three
One Hundred and Twenty-Three Thousand, Four Hundred and Fifty-Six
Two Billion, One Hundred and Fourty-Seven Million, Four Hundred and Eighty-Three Thousand, Six Hundred and Forty-Seven
Out of range

```

[php]#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <limits.h>

#define FILE_INPUT "-f"
#define FILE_INPUT_EXT "--file"
#define HELP "-h"
#define HELP_EXT "--help"
#define STDIN_INPUT "-s"
#define STDIN_INPUT_EXT "--stdin"
#define INVALID (0)
#define VALID (1)
#define EOL (2) /*End Of Line*/
#define EON (4) /*End Of Number*/
#define FILE_END (8) /*file ended*/
#define OOR (16)
#define CHUNK (30)

#define is_number(c) ( ((c) >= '0') && ((c) <= '9') )
#define is_acceptable(c) ( (is_number(c)) || ((c) == ',') || ((c) == '-'))
#define char_to_int(c) ( (c) - '0' )

int number_of_digits(int num);

int get_number_string(int *num, char *string);
/* gets a number from string and stores it in num; if the string has invalid characters
 * it returns INVALID, if it's out of range it returns INVALID | OOR and if everything went ok it returns VALID
 */

int get_number_stream(int *num, FILE *stream);
/* takes character from stream as long as they are valid for a string and stores the number
 * it gets in num and returns a flag. If the last character taken was EOF, turns on in flag FILE_END bit;
 * otherwise, if the string
 * taken is invalid returns a flag wit INVALID turned on, while if the string was valid it returns a flag with
 * VALID turned on and EOL if the last
 * character was '\n', EON in all the other cases
 */

#define get_number(num) (get_number_stream((num), stdin))
void print_number(int number);
/* prints as an English numeral the number number */
void print_number_rec(int number);
/* recursive function to be used in print_number */
void print_help();
/* help summary if the program is called without arguments or with help switches */

char *PROG_NAME;

int main(int argc, char *argv[]) {

  int num;
  int retval;
  int i;
  FILE *stream;

  PROG_NAME = argv[0];


  if (argc == 1) { /*If there were no arguments*/
    print_help();
    return 0;
  }
  
  for (i = 1; i < argc; i++) { /*Start to scan the arguments*/
    if (!strcmp(argv[i], HELP) ||
        !strcmp(argv[i], HELP_EXT)) { /* If a help switch is met */
      print_help(); /* print help menu */
      return 0;
    }
    if (!strcmp(argv[i], STDIN_INPUT) ||
        !strcmp(argv[i], STDIN_INPUT_EXT)) { /*If a stdin switch is met*/
      do {
        retval = get_number(&num);
        if (retval & VALID) /*if the string was a number*/
          print_number(num);
      } while (!(retval & EOL)); /*as long as the user doesn't input a newline*/

    }
    else
    if (!strcmp(argv[i], FILE_INPUT) ||
        !strcmp(argv[i], FILE_INPUT_EXT)) { /*If the file input switch is met,*/
      i++;
      stream = fopen(argv[i], "r");/*open the named stream*/
      if (stream == NULL)
        printf("Error with file %s\n", argv[i]);
      else {
        do {
          retval = get_number_stream(&num, stream);
          if (retval & VALID) /*if the string is a number */
            print_number(num);
        } while (!(retval & FILE_END)); /*
          take strings as long as the stream doesn't end*/
      }
    }
    else { /*if argv[i] wasn't a switch, consider it a string to be interpreted*/
      retval = get_number_string(&num, argv[i]);
      if (retval & VALID)
        print_number(num);
      else if (retval & OOR)
        printf("Out of range\n");
    }
  }   

  return 0;

}

void print_help() {
  
  printf("Use:\n");
  printf("%s [expression]\n", PROG_NAME);
  printf("Where 'expression' is constituted by:\n");
  printf("- Integers\n");
  printf("- %s or %s followed by the name of the file from wich you want to get the numbers to be printed\n",
         FILE_INPUT, FILE_INPUT_EXT);
  printf("- %s or %s if you want the integers to be taken from stdio\n", STDIN_INPUT, STDIN_INPUT_EXT);
  printf("You can combine these options in any way you'd like;\n");
  printf("Example:\n");
  printf("%s 1235 123,456 --file nameofile 45678 -s 12\n", PROG_NAME);

}

int number_of_digits(int num) {
  
  int digits;

  for (digits = 0; num != 0; num /= 10)
    digits++;

  return digits;

}

int get_number_string(int *num, char *string) {
  
  int i;
  int first_comma;/*position of the first comma; 0 if no one has been met*/ 
  int coefficient;
  int flag = 0;
  int almost_max = 0; /*to be put on if we get near to INT_MAX */

  coefficient = 1;/*for now used in case the number is negative*/

  if (*string == '\0') {
    *num = 0;
    return (flag | INVALID);
  }/*if the string is empty it is invalid, no need to check for anything else*/

  for (i = 0, *num = 0, first_comma = 0; string[i] != '\0'; i++) {
    if (!is_acceptable(string[i])) {/*if a character is not acceptable*/
      *num = 0;/*clear the number*/
      return (flag | INVALID);/*and return INVALID*/
    }
    if (string[i] == ',') {/*if the character is a comma*/
      if (i == 0)/*if it is the first character of the string*/
        return (flag | INVALID);/*the string is surely not numeric*/
      
      if (first_comma == 0) {/*otherwise, if still no comma has been met,*/
        if ( i > 3 || (coefficient == -1 && i > 4)) {/*and too many characters have already passed*/
          *num = 0;
          return (flag | INVALID);/*the string is not numeric*/
        }
        first_comma = i;/*otherwise, accept the comma in first_comma position*/
      }
      else { /*if a comma has already been found,*/
        if ((i - first_comma) % 4 != 0) {/*if it is in an invalid position*/
        *num = 0;/*clear the number*/
        return INVALID;/*and return INVALID*/
      }
      }
    }
    else if (string[i] == '-') { /*if a hyphen is met*/
      if (i != 0) {/*if it is not the first character, the string is not numeric*/
        *num = 0;
        return INVALID;
      }
       coefficient *= -1; /*otherwise, at the end change the sign of the number*/
       string++;
       i--;
       /*start the check again as if the hyphen has never been met*/
    }
    else { /*if the character is acceptable, isn't a comma and isn't a hyphen*/
      if (almost_max) {
        if ((INT_MAX - (*num * 10) - char_to_int(string[i])) >= 0) {
          /*if the number with another digit is still in range*/
          *num *= 10;
          *num += char_to_int(string[i]);
          *num *= coefficient;
          if (string[i+1] == '\0') /*if the last one is the last character of the string*/
            return (flag | VALID);
          else if (is_number(string[i+1])) { /*if the next character is a number*/
            *num = 0;
            return (flag | INVALID | OOR);
          }
          else { /*if the next character is not a valid character*/
            *num = 0;
            return (flag | INVALID);
          }
        }
        else {/*if the number would be out of range with another digit*/
          *num = 0;
          return (flag | INVALID | OOR);
        }
      }
      *num *= 10;
      *num += char_to_int(string[i]);

      if (number_of_digits(INT_MAX) - 1 == number_of_digits(*num))
        almost_max = 1;
      
    }
  }

  *num *= coefficient;

  return VALID;

}
      

int get_number_stream(int *num, FILE *stream) {

  char *string;
  int i;
  int c;
  int flag = 0;

  i = 0;
  string = malloc(sizeof(char) * CHUNK);

  while ((c = getc(stream)) != EOF && is_acceptable(c)) {
    if (i >= (CHUNK - 1)) {
      *num = 0;
      flag = flag | INVALID | OOR;
      if (c == EOF)
        flag = flag | FILE_END;
      else if (c == '\n')
        flag = flag | EOL;
      return flag;
    }
    string[i] = c;
    i++;
  }

  string[i] = '\0';
  
  flag = flag | get_number_string(num, string); /*sets the valid/invalid bit*/
  free(string);

  if (c == EOF)
    flag = flag | FILE_END; /*sets the end of file bit*/
  else if (c == '\n')
    flag = flag | EOL; /*sets the end of line bit*/
  else
    flag = flag | EON; /*sets the end of number bit*/

  return flag;

}


void print_number(int number) {
  
  if (number == 0)
    printf("Zero"); /*in the recursive function, 0 is never printed*/
  else {
    if (number < 0) {
      printf("Minus ");
      number *= -1;
    }
    print_number_rec(number);
  }

  putchar('\n');
  return;

}

void print_number_rec(int number) {

  switch (number) {
    case 0:
      break;
    case 1:
      printf("One");
      number = 0;
      break;
    case 2:
      printf("Two");
      number = 0;
      break;
    case 3:
      printf("Three");
      number = 0;
      break;
    case 4:
      printf("Four");
      number = 0;
      break;
    case 5:
      printf("Five");
      number = 0;
      break;
    case 6:
      printf("Six");
      number = 0;
      break;
    case 7:
      printf("Seven");
      number = 0;
      break;
    case 8:
      printf("Eight");
      number = 0;
      break;
    case 9:
      printf("Nine");
      number = 0;
      break;
    case 10:
      printf("Ten");
      number = 0;
      break;
    case 11:
      printf("Eleven");
      number = 0;
      break;
    case 12:
      printf("Twelve");
      number = 0;
      break;
    case 13:
      printf("Thirteen");
      number = 0;
      break;
    case 14:
      printf("Fourteen");
      number = 0;
      break;
    case 15:
      printf("Fifteen");
      number = 0;
      break;
    case 16:
      printf("Sixteen");
      number = 0;
      break;
    case 17:
      printf("Seventeen");
      number = 0;
      break;
    case 18:
      printf("Eighteen");
      number = 0;
      break;
    case 19:
      printf("Nineteen");
      number = 0;
      break;
    case 20:
      printf("Twenty");
      number = 0;
      break;
    case 30:
      printf("Thirty");
      number = 0;
      break;
    case 40:
      printf("Forty");
      number = 0;
      break;
    case 50:
      printf("Fifty");
      number = 0;
      break;
    case 60:
      printf("Sixty");
      number = 0;
      break;
    case 70:
      printf("Seventy");
      number = 0;
      break;
    case 80:
      printf("Eighty");
      number = 0;
      break;
    case 90:
      printf("Ninety");
      number = 0;
      break;
    default:
      break;
  }

  if (number == 0)
    return; /*if number is 0 everything has been taken care of*/
  
  if (number < 100) { /*take care of the tens*/
    print_number_rec(number / 10 * 10);
    putchar('-');
    print_number_rec(number % 10);
    return;
  }

  if (number < 1000) { /*take care of the hundreds*/
    print_number_rec(number / 100);
    printf(" Hundred");
    if (number % 100 != 0) {
      printf(" and ");
      print_number_rec(number % 100);
    }
    return;
  }

  if (number < 1000000) { /*take care of the thousands*/
    print_number_rec(number / 1000);
    printf(" Thousand");
    if (number % 1000 != 0) {
      printf(", ");
      print_number_rec(number % 1000);
    }
    return;
  }
  
  if (number < 1000000000) {
    print_number_rec(number / 1000000); /*take care of the millions*/
    printf(" Million");
    if (number % 1000000 != 0) {
      printf(", ");
      print_number_rec(number % 1000000);
    }
    return;
  }

  print_number_rec(number / 1000000000);
  printf(" Billion");
  if (number % 1000000000 != 0) {
    printf(", ");
    print_number_rec(number % 1000000000);
  }

  return;

}
[/php]

EDIT: Some spelling mistakes corrected.

---

### Post by papibe on 2012-06-04
Here it is.

It uses the "[Long scales large-number naming system]("http://en.wikipedia.org/wiki/Long_and_short_scales")", and it handles input numbers in the range [ -(10^24 - 1), 10^24 - 1]

Regards.

```
#!/usr/bin/env python

# Beginners programming challenge #26: Name numbers using English words.
# Proposed by Bodsda at ubuntuforums.org
# link: http://ubuntuforums.org/showthread.php?t=1988462
#
# Author: papibe
# Mon Jun  4 13:14:08 CDT 2012

# Important note: this program uses the long scale naming system.
# Read about it here: http://en.wikipedia.org/wiki/Long_and_short_scales

# Known Issues: separators are handled on input, but there's no syntax check.
# Example:
#   1,000   -> 1000
#   1,00    -> 100 (separators are just removed)
#   ,10     -> 10 (ugly, I know)

import os, sys

# Numbers between 1 and 19 that are represented by one word.
# Zero is not on the list because is manage as an exception.
digits = {  '0':"", '1':"one", '2':"two", '3':"three", '4':"four",
            '5':"five", '6':"six", '7':"seven", '8':"eight", '9':"nine",
            '10':"ten", '11':"eleven", '12':"twelve", '13':"thirteen",
            '14':"fourteen", '15':"fifteen", '16':"sixteen",
            '17':"seventeen", '18':"eighteen", '19':"nineteen" }

# Tenths from 20 to 90.
# The number 10 is manage by the previous variable (digits).
tenths = {  '0':"", '1':"", '2':"twenty", '3':"thirty", '4':"forty",
            '5':"fifty", '6':"sixty", '7':"seventy", '8':"eighty",
            '9':"ninety" }

# Name for groups of 10^6
position = [ "", "million", "billion", "trillion" ]


# Add the word add to a list representing the name of a number.
# Input example: ['one','hundred','five']
# Output: ['one','hundred', 'and', 'five']
def add_and( words ):

    # Words that are not numbers.
    notvalues = [ "hundred", "thousand", "million", "billion", "trillion" ]

    index = len(words) -1
    prevdigit = False

    # Look for the first place between a number and one that is not/
    while index >= 0:

        # previous word was a number and actual word is not.
        if words[index] in notvalues and prevdigit:
            words.insert( index + 1, "and")
            break

        # Remember previous state of word.
        if not words[index] in notvalues:
            prevdigit = True
        else:
            prevdigit = False

        index -= 1

# Remove null strings from a list representing the name of a number.
def remove_nulls( nlist):

    while '' in nlist:
        nlist.remove('')

# Every group of 3 digits can be named in the same way.
# This function receives 3-digit number string and returns a list representing
# its name.
# Input example: "123"
# Output: ['one', 'hundred', 'twenty', 'three']
def basic_block( snum ):

    word = []

    # Naming the 2 less significant digits.

    # If second digit stars with 1, it means the 2 less significant digits can
    # be represented using one word (contain in the dictionary called digits).
    # That is, from 10 to 19
    if snum[1] == '1':
        word.insert( 0, digits[ snum[1:] ] )
    else:
        # To name the less 2 significant numbers, we need 2 words: one from
        # 'digits' and one from 'tenths'
        word.insert( 0, digits[ snum[2] ] )
        word.insert( 0, tenths[ snum[1] ] )

    # Naming the most significant digits

    # Omit naming the hundreds if the value is zero.
    if snum[0] != '0':
        word.insert( 0, "hundred" )
        word.insert( 0, digits[ snum[0] ] )

    remove_nulls( word )

    return word

# Divide the number in blocks of 6 digits.
# Each block would be divided in two words representing the thousands (w1), and
# the hundreds (w2).
# Example: block=123456 -> w1=123 and w2=456
def count( snum ):

    words = []

    # Number of blocks (6 digits number)
    nblocks = len(snum) / 6

    block = 0
    while block < nblocks:

        index = (block * 6)

        # w1: list containing the name of the 3 most significant numbers.
        w1 = basic_block( snum[index:index+3] )

        # w2: list containing the name of the 3 less significant numbers.
        w2 = basic_block( snum[index+3:index+6] )

        # Append both list to the final word list.
        if w1 != []:
            words.extend( w1 )
            words.append( "thousand" )
        if w2 != []:
            words.extend( w2 )

        # Append the name related to the block (groups of 10^6):
        # Example: million, billion, etc.
        if w1 != [] or w2 != []:
            index = nblocks - block - 1
            if index < len( position ):
                words.append( position[nblocks - block - 1] )
            else:
                return "is too big."

        block += 1

    remove_nulls( words )

    # Add the word 'and' where it correspond.
    add_and( words )

    # Return a string formed by the list strings.
    return (" ".join( words )).strip()

# This is the function called from the main program, but is not the one doing
# the heavy work. It just remove separators (','), handle the special case
# of 'zero', and if it is negative number.
#
# For the rest it fills with leading zeros to form a number which length is
# multiplier of 6.
def num_in_words( s ):
    # Remove separators (',').
    s = s.replace(',','')

    # Number is negative
    if s[0] == '-':
        s = s.replace('-','',1)     # remove sign.
        negative = "negative "
    else:
        negative = ""

    # Remove leading zeros.
    while len(s) > 1 and s[0] == '0':
        s = s.replace('0','',1)

    # Fill with leading zeros to form a number with length = n*6
    diff =  6 - (len(s) % 6)
    if diff != 6:
        s = s.zfill( len(s) + diff )

    # Handle special case: number is zero/
    if s == "000000":
        return "zero"
    else:
        # function count will do the main work.
        return negative + count( s )

# Test if a string is a valid number.
# Although there's a method called isdigit(), it doesn't handle signs and
# separators.
def is_number( string ):
    # Remove separators (',').
    snumber = string.replace(',','')
    try:
        test = int( snumber )
        return True
    except ValueError:
        return False

# It names all arguments into English.
# If no arguments are given, it reads one number per line from the standard
# input, until an empty line.
# Example:
#   $ ./name_numbers.py 123 -45 1,403,789 0
#   $ ./name_numbers.py < test.txt
#   $ ./name_numbers.py
#   Enter one number per line: (end with empty line)
#   123
#   -90,432
#   $ 
def main( argvs ):

    # No arguments. Read from the standard input.
    if len(argvs) == 1:
        print "Enter one number per line: (end with empty line)"

        number = raw_input('')
        while number != "":

            if is_number( number ) :
                print number, "\t", num_in_words( number )
            else:
                print number, "\tis not an integer."

            number = raw_input('')

    else:
        # Name all arguments.
        argvs.pop(0)            # remove program name itself.
        for number in argvs:

            if is_number( number ) :
                print number, "\t", num_in_words( number )
            else:
                print number, "\tis not an integer."

    sys.exit( 0 )


if __name__ == "__main__":

    main(sys.argv)
```

---

### Post by Bodsda on 2012-06-04
> **kingtaurus said:**
> Couple of quick questions:
(1) Should we also handle separators that correspond to different localizations (i.e. comma separators (en_CA.utf8), period separators (de_DE.utf8 for example), ... is there anymore?)?
(2) Should we assume simple newline (or tab) separation between entries in the file?

Cheers,

Only a comma ('**,**' ) will be classed as a separator for the purposes of this exercise (There will be no float's in my test file).
The file will be delimited by newlines (unless you provide your test case input file. Then I'm happy for it to be delimited with anything you like.)

Bodsda

---

### Post by cgroza on 2012-06-05
I have written this one in Haskell and implemented the first 3 cookie points.
Command examples:
```

# reads numbers from a newline separated file
program -f test.txt
``````

# reads numbers interactively
program -i
``````

# reads number from command line
program -n1337

```It can take any number of arguments and in any combination. For example:
```

program -f test.txt -i -n1337

```In this case, it will read and print all the numbers in test.txt, stop and ask for input for a number and print it, and then print the integer supplied via -n.

The code:
```

-- Short program explanation:
-- This program works by dividing the number in blocks of 3 digits by using the 
-- "digits" and "slice" functions.
-- Then, the function "toLetters" converts every triplet into words and the 
-- appropriate magnitude (thousand, million, billion, etc.) is added after the 
-- result by the "numToLetters" function which results in the final number 
-- converted into words.
-- The rest of the functions are helper functions that interpret the input and
-- format the output that have little relevance to the problem.

module Main where
import Control.Monad
import System.Console.GetOpt
import System.Environment
-- digits from 1 to 19
units = ["", "one ", "two ", "three ", "four ", "five ", "six ", "seven ", 
         "eight ", "nine ", "ten ", "eleven ", "twelve ", "thirteen ",
         "fourteen ", "fifteen ", "sixteen ", "seventeen ", "eighteen ", 
         "nineteen "]

-- tens from 20 to 90
-- first 2 elements are just offsets for the indexes
tens = ["", "", "twenty ", "thirty ", "fourty ", "fifty ", "sixty ", "seventy ",
        "eighty ", "ninety "]

-- these are added after each triplet by numToLetters
magnitudes = ["", "thousand ", "million ", "billion ", "trillion ", 
              "quadrillion ", "quintillion ", "sextillion ", "septillion ", 
              "octillion ", "nonillion ", "decillion "]

-- returns number as list of integers
digits :: Integer -> [Int]
digits = reverse . map (fromIntegral . (`mod` 10)) . takeWhile (> 0) . iterate
         (`div` 10) . abs

-- takesn a integer list and divides it at every three numbers starting from 
-- the end
slice :: [Int] -> [[Int]]
slice ints = f ints []
  where f [] xs = xs
        f is xs = f (take (length is - 3) is) ([(drop (length is - 3) is)]++xs)
        
-- takes a list of digits and concatenates them into an integer
joinDigits = foldl1 (\x y -> 10 * x + y)

-- applies toLetters to every triplet and adds the necessary magnitude
numToLetters :: [[Int]] -> String -> String
numToLetters [] ss = ss                
numToLetters (x:xs) ss = numToLetters xs (ss ++ toLetters x ""
                                          ++ (magnitudes !! length xs))

-- takes numbers between 0 - 999 and converts them into words
-- we have to take care of the special case 0
toLetters :: [Int] -> String -> String
toLetters [0, 0, y3] hs = toLetters [y3] ""
toLetters [0, y2, y3] hs = toLetters [y2, y3] ""
toLetters [y1, y2, y3] hs = units !! y1 ++ "hundred " 
                            ++ toLetters [y2, y3] ""
toLetters [y1, 0] hs = units !! y1
toLetters [y1, y2] hs = if y1 == 1 then units !! (joinDigits [y1, y2])
                        else tens !! y1 ++ toLetters [y2] ""
toLetters [y1] hs = units !! y1

-- prefixes the string with "negative " if the number is negative and passes
-- the processed absolute value of the integer to numToLetters
translateNum :: Integer -> String
translateNum i = (if i < 0 then "negative " else "")
                    ++ numToLetters (slice (digits (abs i))) ""
  
-- simply pretty prints the numbers to the terminal
printNumbers :: [Integer] -> IO ()
printNumbers = mapM_ (\n -> putStr (show n ++ "-") >> putStrLn (translateNum n))

-- reads all the integers separated by newlines in a file
readIntsFile :: FilePath -> IO [Integer]
readIntsFile = (return . map read . lines . filter (/= ',') =<<) . readFile

-- reads all the integers separated by newlines from stdin
getInts :: IO [Integer]
getInts = (return . map read . words . filter (/= ',')) =<<  getLine

-- for command line arguments interpretation
data Flag = Interactive | FromArg String | FromFile FilePath

options :: [OptDescr Flag]
options  = [Option "i" ["interactive"] (NoArg Interactive) 
            "ask numbers interactively",
            Option "n" ["number"] (ReqArg FromArg "NUMBER") 
            "provide numbers at command line",
            Option "f" ["file"] (ReqArg FromFile "FILE") 
            "read numbers from file"]

-- calls the appropriate functions to take input according to the flag
processArg :: Flag -> IO ()
processArg arg =
  case arg of
    Interactive -> printNumbers =<< getInts
    (FromArg n) -> printNumbers [read n]
    (FromFile f) -> printNumbers =<< readIntsFile f

main :: IO ()
main = do argv <- getArgs
          let (ss, _, _) = getOpt Permute options argv in mapM_ processArg ss


```Compile with:
```

ghc filename.hs

```Good luck to all participants. :D

---

### Post by Bodsda on 2012-06-07
Challenge will be judged in about a weeks time. Good work to everyone so far. Keep the code coming!

Bodsda

---

### Post by mildisaster on 2012-06-08
I've been wanting to get into programming and this looks like a great thing to be doing, so thank you! Is there a quick way to look at your backlog of these? (I'm assuming there is a backlog, seeing as this is #26)

---

### Post by Odexios on 2012-06-08
> **mildisaster said:**
> I've been wanting to get into programming and this looks like a great thing to be doing, so thank you! Is there a quick way to look at your backlog of these? (I'm assuming there is a backlog, seeing as this is #26)

Here you are:

[http://ubuntuforums.org/showthread.php?t=1714324](http://ubuntuforums.org/showthread.php?t=1714324)

---

### Post by mildisaster on 2012-06-09
> **Odexios said:**
> Here you are:

[http://ubuntuforums.org/showthread.php?t=1714324](http://ubuntuforums.org/showthread.php?t=1714324)

Ah yes, thank you. :KS

---

### Post by VCoolio on 2012-06-12
My contribution in bash. Use as "script <int(s)>", or "script file(s)", or just "script" to enter number interactively. Accepts multiple files or numbers, but only either files or numbers, not both together. Output in short-scale mode. Also I think it should be e.g. "forty-two" instead of "forty two". Can do up to 27 digits (and even more, sort of). Nasty challenge, a lot to deal with. But fun. I hope I did it sufficiently right.

```
#!/bin/bash

units=("" one two three four five six seven eight nine ten eleven twelve thirteen fourteen fifteen sixteen seventeen eighteen nineteen)
tens=(zero ten twenty thirty forty fifty sixty seventy eighty ninety)
min="" ### variable used if number is negative
and="" ### variable used if "and" is needed grammatically

# function to translate two-digit numbers
write_two() {
	first=${1%?}  			# get first digit
	second=${1#?} 			# get second digit
	if [ $1 -lt 20 ]; then 		# if less than 20, use array units
		echo "${units[$1]}"
	elif [ $second = 0 ]; then 	# if last digit is zero, use array tens
		echo "${tens[$first]}"
	else 				# else combine them
		echo "${tens[$first]}-${units[$second]}"
	fi
}

# function to translate three-digit numbers
write_three() {
	first=${1%??}
	lasttwo=${1#?}
	if [ ${#1} -lt 3 ]; then 	# if argument is one or two digits, use write_two
		echo $(write_two $1)
	elif [ "$first" = "0" ]; then 	# check if first digit is zero, to insert "and"
		[ "$1" = "$lastthreeofint" ] && and="and " # but only if it's the last digits of the number
		echo "$and$(write_two $lasttwo)"	   # and use write_two to translate
		unset and
	else				# if it's really three digits
		out1="${units[$first]} hundred" # count hundreds
		if [ $lasttwo = "00" ]; then	# if rest is zero, we're done
			echo $out1
		else
			out2=$(write_two $lasttwo) # else translate rest
			echo "$out1 and $out2"
		fi
	fi
}

default(){
	last="${1#"$firstfew"}" # get last digits
	out1="$(write_three $firstfew) $magnitude" # translate first digits (to count current magnitude)
	out2="$($previous $last)"	# translate rest
	if [ -e $(echo ${last//0}) ]; then	# check if rest is zeroes, then we're done
		echo $out1
	elif [ $firstfew -eq 0 ]; then
		echo $out2 # if current magnitude count is zero, translate only the rest
	else
		echo $out1 $out2 # else translate all
	fi
}

# to translate up to six digits
write_six() {
	firstfew="${1%???}" # count thousands
	magnitude="thousand" # provide string
	previous="write_three" # tell what function to use to count the rest
	default $1
}

# to translate up to nine digits
write_nine(){
	firstfew="${1%??????}"
	magnitude="million"
	previous="write_six"
	default $1
}

# up to twelve digits
write_twelve(){
	firstfew="${1%?????????}"
	magnitude="billion"
	previous="write_nine"
	default $1
}

# and trillions
write_fifteen(){
	firstfew="${1%????????????}"
	magnitude="trillion"
	previous="write_twelve"
	default $1
}

# and quadrillions
write_eighteen(){
	firstfew="${1%???????????????}"
	magnitude="quadrillion"
	previous="write_fifteen"
	default $1
}

write_twentyone(){
	firstfew="${1%??????????????????}"
	magnitude="quintillion"
	previous="write_eighteen"
	default $1
}

write_twentyfour(){
	firstfew="${1%?????????????????????}"
	magnitude="sextillion"
	previous="write_twentyone"
	default $1
}

write_twentyseven(){
	firstfew="${1%????????????????????????}"
	magnitude="septillion"
	previous="write_twentyfour"
	default $1
}

nonumber() {
	echo Error: $1 is not a valid number
	exit 1
}

# main function to check input and count digits to use right function
write_int() {
	int="$1"
	if [[ $int == *[:alpha:]* ]]; then # if there are alphabetic chars, it's no number
		nonumber $1
	fi
	#check if min
	if [ "${int%${int#?}}" = '-' ]; then
		min="minus " # if first char is '-', then number is negative, set var to read later
		int="${int#-}"
	fi
	#check commas and check for non-numerical chars
	if [[ $int == *,* ]]; then # if there are commas, check if they're used right
		fromcomma=${int#${int%%,*}}
		[ -e ${fromcomma//,[0-9][0-9][0-9]} ] || nonumber $int # if not 3 digits behind each comma, it's no number
		int=${int//,} # strip commas from number
	fi
	[ -e ${int//[0-9]} ] || nonumber $int
	#strip leading zeros
	while [[ $int == 0* ]]; do int=${int#0}; done
	chars=${#int}    ### count characters and use function to translate accordingly
	allbutlastthree=${int%???}
	lastthreeofint=${int#"$allbutlastthree"}
	case $chars in
		0) min="" # minus zero is just zero
		out=zero;;
		1) out="${units[$int]}";;
		2) out=$(write_two $int);;
		3) out=$(write_three $int);;
		[4-6]) out=$(write_six $int);;
		[7-9]) out=$(write_nine $int);;
		10|11|12) out=$(write_twelve $int);;
		1[3-5]) out=$(write_fifteen $int);;
		1[6-8]) out=$(write_eighteen $int);;
		19|20|21) out=$(write_twentyone $int);;
		2[2-4]) out=$(write_twentyfour $int);;
		2[5-7]) out=$(write_twentyseven $int);;
		*) out="a shitload (this script accepts up to 27 digits)";;
	esac
	echo ${min}$out
	unset min
}

if [ $1 ]; then
    if [ -f $1 ]; then         ### if input is a file
	    for f in $*; do
	        while read line; do    ### read it line by line
        	    for i in $line; do write_int $i; done # and translate all numbers on that line
		done < $f
	done
    else
        for i in $*; do write_int $i; done           ### else take arguments as input
    fi
else
    printf "You didn't provide one or more files or numbers.\nEnter number: "    ### if no input, ask for it
    read int
    write_int $int
fi

```

Edit 23-06-2012: new version, bash only. Bye sed. Another bug fixed. Not easy to do this right :).

---

### Post by Bodsda on 2012-06-28
And the winner is...............

........
........
........
........
........
........
........
........
........

CGROZA!!

Congratulations. Your code was beautifully written and well commented.

Well done to everyone who entered. I look forward to the next challenge!

Happy Coding,
Bodsda,
Ubuntu Beginners Team

---

### Post by cgroza on 2012-06-28
I want to thank Bosda and all the users involved in creating Beginners Programming Challenge. Also, good work to all participants and thank you for competing.
I will try to elaborate the 27th challenge as quickly as possible, and hopefully, it will be worthy of you :D.

Haskell was a great language to do this in.

Thank you and participate to the next one too ;).

---

### Post by Brandonlayton on 2012-11-03
Threw this together in python. Probably could look nicer but it works up into the billions
```

#Variable stuff
number = raw_input("What number?")              #Get Input
num_in_string = str(number)                     #Turn to string for easier manipulation and looping through characters
num_in_string = num_in_string.replace(',','');  #get rid of commas
english = ""                                    #Create place string to add into for output

###################################################################################################################
#Functions

def getWord(n):
    if n == '1' :
        return 'one'
    elif n == '2':
        return 'two'
    elif n == '3':
        return 'three'
    elif n == '4':
        return 'four'
    elif n == '5':
        return 'five'
    elif n == '6':
        return 'six'
    elif n == '7':
        return 'seven'
    elif n == '8':
        return 'eight'
    elif n == '9':
        return 'nine'
def getTens(n):
    if n == 'two':
        return 'twenty'
    elif n == 'three':
        return 'thirty'
    elif n == 'four':
        return 'forty'
    elif n == 'five':
        return 'fifty'
    elif n == 'six':
        return 'sixty'
    elif n == 'seven':
        return 'seventy'
    elif n == 'eight':
        return 'eighty'
    elif n == 'nine':
        return 'ninety'
def getTensOne(n):
    if n == '1' :
        return 'eleven'
    elif n == '2':
        return 'twelve'
    elif n == '3':
        return 'thirteen'
    elif n == '4':
        return 'fourteen'
    elif n == '5':
        return 'fifteen'
    elif n == '6':
        return 'sixteen'
    elif n == '7':
        return 'seventeen'
    elif n == '8':
        return 'eighteen'
    elif n == '9':
        return 'nineteen'
def getSize(s):
    if s == 3: return "thousand"
    elif s == 6: return "million"
    elif s == 9: return "billion"
    else: return ""
###################################################################################################################
#actual program now
                                            #check to see if it is zero,
if(num_in_string == '0'): english = 'zero'; #because there is no other case where we say anything for zero
else:
    nums = num_in_string[::-1]
    print nums
    l = len(nums)
    for n in range(l):
        if(nums[n] == '0'):
            english = english               #Had to get rid of syntax error
        elif((n+1)%3 == 0):
            english = getWord(nums[n]) + " hundred and " + english
        elif((n+1)%3 == 1):
                english = getWord(nums[n]) + " " + getSize(n) + " " + english
        elif((n+1)%3 == 2):
            english = getTens(getWord(nums[n])) + " " + english

print english

```

:guitar:

---

### Post by Tony Flury on 2012-11-03
> **Brandonlayton said:**
> Threw this together in python. Probably could look nicer but it works up into the billions


I hope you don't mind, but he beauty of these challenges is that you can learn.  Your code would be much nice if your 3 functions were defined like this - replacing the long chain of if/elif with table lookups : 

```

###################################################################################################################
#Functions

def getWord(n):
    print n
    word = ["", "one","two","three","four","five","six","seven","eight","nine"]
    return word[int(n)]

def getTens(n):
    word = {"0":"", 1:"","two":"twenty","three":"thirty","four":"forty","five":"fifty","six":"sixty","seven":"seventy","eight":"eighty","nine":"ninety"}
    return word[n]

def getTensOne(n):
    word = ["", "eleven","twelve","thirteen","fourteen","fifteen","sixteen","seventeen","eighteen","nineteen"]
    return word[int(n)]

```
Also what happens if the input is from 10 to 19 - your code generates an error i think.

---

### Post by Brandonlayton on 2012-11-04
Wow. That is definitely a nicer way of doing it. 
Thanks for your comments :)
I think I fixed everything and made it better:
```



def getWord(n):
    word = ["", "one","two","three","four","five","six","seven","eight","nine"]
    return word[int(n)]
def getTens(n):
    word = {"0":"", "one":"","two":"twenty","three":"thirty","four":"forty","five":"fifty","six":"sixty","seven":"seventy","eight":"eighty","nine":"ninety"}
    return word[n]
def getTensOne(n):
    word = ["ten", "eleven","twelve","thirteen","fourteen","fifteen","sixteen","seventeen","eighteen","nineteen"]
    return word[int(n)]
def getSize(s):
    if s == 4: return "thousand"
    elif s == 7: return "million"
    elif s == 10: return "billion"
    else: return ""
###################################################################################################################
#actual program now
def numToEnglish(number):
    num_in_string = str(number)                     #Turn to string for easier manipulation and looping through characters
    num_in_string = num_in_string.replace(',','');  #get rid of commas
    english = ""
    prevEnglish = ""
                                                #Create place string to add into for output
                                                #check to see if it is zero,
    if(num_in_string == '0'): english = 'zero'; #because there is no other case where we say anything for zero
    else:
        nums = num_in_string[::-1]
        l = len(nums)
        for n in range(l):
            if(nums[n] == '0'):
                english = english               #Had to get rid of syntax error
            elif((n+1)%3 == 0):
                if(english == ""):              #For the weird case where 100 = "one hundred and" and 200 and what not does the same
                    english = getWord(nums[n]) + " hundred " + english
                else:
                    english = getWord(nums[n]) + " hundred and " + english
            elif((n+1)%3 == 1):
                    prevEnglish = english
                    english = getWord(nums[n]) + " " + getSize(n+1) + " " + english
            elif((n+1)%3 == 2):
                #print nums[n]
                #print getWord(nums[n]);
                if(nums[n] == '1'):
                    english = getTensOne(nums[n-1]) + " " + prevEnglish
                else:
                    english = getTens(getWord(nums[n])) + " " + english

    print english
    
number = raw_input("What number?")              #Get Input
numToEnglish(number)

```

---

### Post by Vaphell on 2012-11-04
```
            if(nums[n] == '0'):
                english = english               #Had to get rid of syntax error

```
lol, what syntax error would that be?
if you wanted to put do-nothing line you could use *pass* or not check that condition altogether

---

### Post by Brandonlayton on 2012-11-05
I had to check it because I didn't want it to do anything if it was equal to '0'. I didn't know about "pass" because this is the first script I did in python. Thanks though :)

---

