---
title: "corrupted textfile contains binaryblobs, how to remove"
date: 2009-05-27
forum: Programming Talk
---

### Post by monkeyking on 2009-05-27
I got some textfiles,
that got corrupted, and I basicly just want to remove the lines where the error occurs.

[http://rapidshare.com/files/237756041/textVsBin.tar.gz.html](http://rapidshare.com/files/237756041/textVsBin.tar.gz.html)

This should be 3 column and 3 line file.
But it explodes to almost 4 megs.

If I cat the file it works,
if I head/tail the file it works,
but |less doesnt work.

And my c++ programs get stuck on these input files.
The following program will complain,
but I am unable to jump to the next line with getline, and soon as I enter the binary blob.

Does anyone know how to fix this?

[PHP]
#include <iostream>
#include <fstream>
#include <cstring>
#define LENS 10000

int main(int argc, char **argv){
  std::ifstream pFile(argv[1],std::ios::in);

  if(!pFile)
    printf("Error starting program\n");
  char line[LENS];

  const char* strs;
  int numRow=0;

  while(!pFile.eof()) {
    pFile.getline(line,LENS);
    printf("%s\n",line);

    strs = strtok(line," \t");
    strs=strtok(NULL," \t");
    if(strs==NULL){
      printf("error occured at line %d\n",numRow);
      return 0;//changing to continue, will make the program loop inf.
    }
    numRow++;
  }
  return 0;
}
[/PHP]

thanks in advance

---

### Post by dwhitney67 on 2009-05-27
If you do indeed have a corrupted text file, then you cannot assume the last character on a particular line is a newline.  Thus the use of getline() should be avoided.  I would recommended that you read in one character at a time, then use isprint() and other logic (to check for the newline), so you know which characters to ignore and which to output to the other file or stdout.

Below is an example; see if this would work for you (note, I have not tested it):

```

#include <ctype.h>
#include <fstream>
#include <iostream>

int main(int argc, char** argv)
{
  std::fstream file(argv[1], std::ios::in);

  if (file)
  {
    char ch;

    while (file.get(ch))
    {
      if (isprint(ch) || isblank(ch) || (ch == '\n') || (ch == '\r'))
      {
        std::cout << ch;
      }
    }
  }
  else
  {
    std::cerr << "Cannot open file '" << argv[1] << "'" << std::endl;
    return 1;
  }
}

```

---

### Post by monkeyking on 2009-05-27
Thanks dwithney
alway helpfull with a good solution.


Using your framework I found out that every 2-3000 line contained 4 meg's of null chars.

thanks

---

