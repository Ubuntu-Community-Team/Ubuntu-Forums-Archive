---
title: "[C++] Is this a charset encoding problem?"
date: 2010-02-08
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2010-02-08
I am developing a small helper program that will read a text file line by line. Almost every line contains a number. I try to convert the std::string to a float but I can't. Is this a charset encoding problem? If yes, what do you suggest to do to workaround it?

Here is the code:
[php]
#include <iostream>
#include <string>
#include <sstream>
#include <fstream>


int main(int argc, char *argv[])
{
  float num=0;
  std::string line;
  std::istringstream buf;
  std::ifstream input_file;
  std::ofstream output_file;


  input_file.open(argv[1]);

  if (input_file.is_open())
    {
      while (!input_file.eof())
        {
          getline (input_file,line);
          buf.str(line);
          buf >> num;          
          std::cout << "Line: " << line << std::endl;
          std::cout << "Number: " << num << std::endl;
        }
      input_file.close();
    }
  else std::cout << "Couldn't open the file" << std::endl;

  return 0;
}[/php]

When I run this program num is always 0.

I attach the original txt file. Usage "./progname path-to-text-file"

---

### Post by dwhitney67 on 2010-02-08
Consider the following approach, which is very similar to yours.  With it, I had no trouble parsing your data file, even though the data file appears to be a dos-formatted one.
```

#include <fstream>
#include <string>
#include <sstream>
#include <iostream>

int main(int argc, char** argv)
{
   using namespace std;

   fstream file(argv[1], ios::in);

   if (file)
   {
      string       line;
      unsigned int lineNum = 0;

      while (getline(file, line))
      {
         ++lineNum;

         stringstream iss(line);
         float        val;

         iss >> val;

         if (iss.good())
         {
            cout << "val = " << val << endl;
         }
         else
         {
            cerr << "error reading float from file " << argv[1] << " at line " << lineNum << endl;
         }
      }
   }
   else
   {
      cerr << "error opening file " << argv[1] << endl;
      return -1;
   }
}

```

---

### Post by SledgeHammer_999 on 2010-02-08
Thank you. Essentially the difference between for code and mine is the way you give the string object to stringstream. You passed it on the constructor. I passed later using .str(). When I made the change to my code it worked. So I opened and read the .str() docs-->[link](http://www.cplusplus.com/reference/iostream/istringstream/str/). All I needed to do is put a .clear() before .str().

Now my code looks:
[php]#include <iostream>
#include <string>
#include <sstream>
#include <fstream>


int main(int argc, char *argv[])
{
  float num=0;
  std::string line;
  std::istringstream buf;
  std::ifstream input_file;
  std::ofstream output_file;


  input_file.open(argv[1]);

  if (input_file.is_open())
    {
      while (!input_file.eof())
        {
          getline (input_file,line);
          buf.clear();
          buf.str(line);
          buf >> num;          
          std::cout << "Line: " << line << std::endl;
          std::cout << "Number: " << num << std::endl;
        }
      input_file.close();
    }
  else std::cout << "Couldn't open the file" << std::endl;

  return 0;
}[/php]

And it works. Thanks.

(just to nitpick, you forgot "return 0;" when no error occurs :P)

---

### Post by dwhitney67 on 2010-02-08
> **SledgeHammer_999 said:**
> 
(just to nitpick, you forgot "return 0;" when no error occurs :P)
No I didn't; C++ apps return 0 by default.  Only in C must one be specific.

---

