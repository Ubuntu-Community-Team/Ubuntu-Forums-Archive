---
title: "c++ creating file in spcified path"
date: 2008-12-23
forum: Programming Talk
---

### Post by burakdede on 2008-12-23
does anybody know how to create file in specific directory for example you wanna create file named temp.txt under root the file name would be "/temp.txt" or you wanna create file gogo.txt under "/home/code/" the file name would be "home/code/gogo.txt" and i wanna give initial size to the file while creating.i am not sure we can do with ofstream 
[PHP]ofstream("/home/code/gogo.txt") //doesnt work for me[/PHP]

---

### Post by snova on 2008-12-23
Open in write mode. If the file does not already exist, it will be created.

On the other hand, if it does exist, it will be truncated.

---

### Post by dwhitney67 on 2008-12-23
I do not believe (in fact, I'm almost certain) that you cannot dictate what size a file will have upon creating it.  You would need to write data to it before a size is established.

With respect to opening the file, you need to provide a path (as you have shown in your example), and if necessary, indicate whether you want to append to the file should it exist already.

Personally, I favor using fstream in lieu of ofstream or ifstream when it comes to opening a file.

For example:
[php]
#include <fstream>

int main()
{
  std::fstream file("/tmp/foo.txt", std::ios::out | std::ios::app);

  if (file)
  {
    file << "Some text." << std::endl;
    file.close();
  }

  return 0;
}
[/php]
The ios flags are used to indicate which operation to perform on the fstream for the specified file.  In the case above, the flags indicate to open the file, and if it already exists, set the file pointer to the end so that the file can be appended.

---

### Post by burakdede on 2008-12-23
is it really creating in specified directory? 
for example /home/code/gogo.txt 
what happen if not found given directories and also one more question how to open with initial size like 1000byte or sth.?

---

### Post by burakdede on 2008-12-23
it is easier if you look at original project description 
here [project]("http://cse.yeditepe.edu.tr/~aulak/courses/f2008/cse211/pslab/cse211project.doc")
here [input file]("http://cse.yeditepe.edu.tr/~aulak/courses/f2008/cse211/pslab/sample.txt")
here is [output file]("http://cse.yeditepe.edu.tr/~aulak/courses/f2008/cse211/pslab/trace.txt")

you can look at it maybe i am in wrong way

---

### Post by dwhitney67 on 2008-12-23
If the specified path, minus the filename, does not exist, then the file will not be opened.  Hence the reason to check for success when attempting to open a file.

If you need to check if a directory exists, you can use the stat() library call.  If stat() indicates that the directory does not exist, then you can use the mkdir() library call to create the directory.

Then create your file.

P.S.  If you are willing to delve into the Boost libraries, then you could consider using the FileSystem library.  Go here for info:  [http://www.boost.org/doc/libs/1_35_0/libs/filesystem/doc/index.htm](http://www.boost.org/doc/libs/1_35_0/libs/filesystem/doc/index.htm)

---

