---
title: "Problem writing to /home/&lt;user&gt; in c/c++"
date: 2009-11-18
forum: Programming Talk
---

### Post by SenojLuap on 2009-11-18
Hello posters, and thanks in advance for any help you can provide.
I'm working on a small project in C++ using gtkmm, although I think my question is non-specific to the language/packages I'm using.
As I understand it, the convention is to save user-specific configuration files to the /home/<user>/.program folder. The problem I'm running into is that my program keeps complaining about not having the access required to create those files/directory.
I originally tried by creating and writing to a std::ofstream initialized to "/home/paul/.numberstudy (my program's called numberstudy FYI). When that didn't work, I tried creating a FILE * and writing to it with fprintf(). After getting the same result twice with two different methods I figured that there was some fundemental problem I wasn't addressing, so here I am. Any thoughts?

---

### Post by dwhitney67 on 2009-11-18
What is it that you are trying to create?... a file or a directory?  If the latter, then use mkdir().

For files use std::ostream; do not use fopen().

---

### Post by SouthOfHell on 2009-11-18
> **dwhitney67 said:**
> What is it that you are trying to create?... a file or a directory?  If the latter, then use mkdir().

For files use std::ostream; do not use fopen().

Why std::fstream over fopen?

---

### Post by A_Fiachra on 2009-11-19
> **SouthOfHell said:**
> Why std::fstream over fopen?


Because C++ has the ability to deal with typesafe file stream objects.  Using fopen is mixing your metaphors, adding potential bugs to your code and throwing out the flexibility of iostreams with no particular upside.

---

### Post by Arndt on 2009-11-19
> **SenojLuap said:**
> Hello posters, and thanks in advance for any help you can provide.
I'm working on a small project in C++ using gtkmm, although I think my question is non-specific to the language/packages I'm using.
As I understand it, the convention is to save user-specific configuration files to the /home/<user>/.program folder. The problem I'm running into is that my program keeps complaining about not having the access required to create those files/directory.
I originally tried by creating and writing to a std::ofstream initialized to "/home/paul/.numberstudy (my program's called numberstudy FYI). When that didn't work, I tried creating a FILE * and writing to it with fprintf(). After getting the same result twice with two different methods I figured that there was some fundemental problem I wasn't addressing, so here I am. Any thoughts?

Does the folder .program already exist?

---

### Post by lisati on 2009-11-19
> **SenojLuap said:**
>  When that didn't work, I tried creating a FILE * and writing to it with fprintf().

I'm guessing that the "*" is a pointer reference, not a file name. If you're using "*" in the filename that you want to write to, it probably won't work, because "*" has a special meaning in file names supplied to some OSes (including Linux, Windows, & MS-DOS)

Code snippet perhaps, so the gurus who are better versed in C/C++ than myself might be able to help?

---

### Post by SouthOfHell on 2009-11-19
> **A_Fiachra said:**
> Because C++ has the ability to deal with typesafe file stream objects.  Using fopen is mixing your metaphors, adding potential bugs to your code and throwing out the flexibility of iostreams with no particular upside.

So say someone wanted to do this purely in C, would there really be no way of doing it without fopen?

---

### Post by dwhitney67 on 2009-11-19
> **SouthOfHell said:**
> So say someone wanted to do this purely in C, would there really be no way of doing it without fopen?

Yes, use open().

Btw, earlier I was only stating that fopen() should be frowned upon for C++ programs.  It is fine for C programs.

---

### Post by SenojLuap on 2009-11-25
Maybe this will help explain:
```
	std::ofstream out(fileName, std::ios::out | std::ios::binary | std::ios::trunc);
	
	if(!out)		// Check to make sure the file opened
	{
		std::string path;
		std::cerr << "Error when opening file: " << fileName << std::endl;
		path = Glib::get_home_dir();
		path = path + "/.numberstudy";
		if(mkdir(path.c_str(), 755))
		{
			std::cerr << "Could not create configuration directory" << std::endl;
			return false;
		}
		out.open(fileName, std::ios::out | std::ios::binary | std::ios::trunc);
		if(!out)
		{
			std::cerr << "Could not create configuration file" << std::endl;
			return false;
		}
	}

```
And to answer a previous question: no, /.numberstudy does not exist to begin with.
The above code is my closest solution so far, but the current problem I'm having is that after the directory is created, it doesn't have the appropriate permissions. It has view-only permission. Am I using mkdir() incorrectly?

---

### Post by froggyswamp on 2009-11-25
> **SenojLuap said:**
> 
As I understand it, the convention is to save user-specific configuration files to the /home/<user>/.program folder.
It's an old and deprecated convention. New apps _should_ follow the freedesktop.org specifications.
For example:
[http://standards.freedesktop.org/basedir-spec/basedir-spec-0.6.html](http://standards.freedesktop.org/basedir-spec/basedir-spec-0.6.html)

---

### Post by dwhitney67 on 2009-11-25
> **SenojLuap said:**
> ...Am I using mkdir() incorrectly?

You will need to preface the 755 with a zero (0), because it represents an octal number.  Thus, try:
```

if(mkdir(path.c_str(), 0755))

```

---

### Post by dwhitney67 on 2009-11-25
By the way, this is how I would do it; there's probably another/better way.
```

#include <sys/stat.h>
#include <string>
#include <cstdlib>

int createDir(const char* dirpath)
{
   struct stat buf;
   int         status = stat(dirpath, &buf);

   if (status == 0 && !S_ISDIR(buf.st_mode))
   {
      // path exists, but it is not a directory!
      status = -1;
   }
   else if (status != 0)
   {
      // no entry exists; create it
      status = mkdir(dirpath, 0755);
   }

   return status;
}

int main(int argc, char** argv)
{
   const char* home = getenv("HOME");

   if (home)
   {
      std::string dirpath = std::string(home) + "/.numberstudy";

      if (createDir(dirpath.c_str()) != 0)
      {
         return -1;
      }
   }
   else
   {
      return -1;
   }

   // ...
}

```
Basically, determine first if it is necessary to create the '.numberstudy' directory; maybe it already exists.  If the '.numberstudy' already exists, ensure that it is a directory; otherwise you have an error.  If it does not exist, then create the directory.

---

### Post by SenojLuap on 2009-11-25
I'm gonna give that a shot. If it works I'll add the [solved] tag and throw in a few extra "thank you"'s :)
In the meantime, I'm interested to hear how other feel about froggyswamp's posting above. I really want to have my program perform in the standardized fashion. However, the frequency of /home/user/.program style configurations far outnumber the XDG standard mentioned. I'm curious to hear how others handle the storage of user-specific configurations.

---

### Post by dwhitney67 on 2009-11-25
> **SenojLuap said:**
> ...
In the meantime, I'm interested to hear how other feel about froggyswamp's posting above...

The XDG Base Directory Specification appears to be (and probably is) a proposal.  I personally do not have an environment variable set that is called XDG_DATA_HOME.  Thus that specification would not work on my system (at this time).

If it is good enough for Firefox (Mozilla) to place a hidden directory in my home folder, I'm sure it will be good enough for your app.

P.S.  I missed this in the spec...
```

If $XDG_DATA_HOME is either not set or empty, a default equal to $HOME/.local/share should be used.

```
So, I suppose your app could create a folder there; but as indicated wrt Firefox, it doesn't.

---

### Post by SenojLuap on 2009-11-25
Aight, used mkdir(fileName, 0755) and it worked perfectly. Thank you to all who contributed. :)

---

