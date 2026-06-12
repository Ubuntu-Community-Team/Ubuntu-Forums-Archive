---
title: "Error problem with readdir"
date: 2010-06-10
forum: Programming Talk
---

### Post by Magnificence on 2010-06-10
Hello,

I read this from the opengroup site's documentation:
> Upon successful completion, readdir() returns a pointer to an object of type struct dirent. When an error is encountered, a null pointer is returned and errno is set to indicate the error. When the end of the directory is encountered, a null pointer is returned and errno is not changed.
Now, if I'm right, readdir should return a null pointer and errno should return zero if the end of the directory is reached. But in my program, it returns 11 the first time it reached the end and 7 for any other time. I checked what errors the are, and they seem to be EAGAIN and E2BIG.

I don't know why I get these errors when the end of the directory is reached, or maybe the errors actually occur, but then I still don't know why. I've currently build a work-around, but I would really appreciate some help.

Thanks.

---

### Post by trent.josephsen on 2010-06-10
Can't help unless you show us the code...

---

### Post by Magnificence on 2010-06-10
Ok, this is the function where I use readdir in:
```
vector<string> Directory::GetSubDirectories()
	{
		vector<string> dirs;
		DIR* directory = opendir(path.c_str());
		if (directory == 0)
		{
			int errorCode = errno;
			if (errorCode == EACCES)
				throw AccessDeniedFileSystemError();
			else if (errorCode == ELOOP)
				throw LoopFoundInPathFileSystemError();
			else if (errorCode == ENAMETOOLONG)
				throw PathTooLongFileSystemError();
			else if (errorCode == ENOENT || errorCode == ENOTDIR)
				throw PathNotFoundFileSystemError();
			else if (errorCode == ENFILE)
				throw OutOfOtherResourcesError();
			else
				throw UnknownError(errorCode);
		}
		
		dirent* directoryEntry = 0;
		while (true)
		{
		  
			directoryEntry = readdir(directory);
			if (directoryEntry == 0)
			{
				int errorCode = errno;
				cout << "Directory::GetSubDirectories() errorCode:\t" << errorCode << '\n';
				//Stop if end of directory list is reached
				if (errorCode == 0 || errorCode == EAGAIN || errorCode == E2BIG/*It seems that errors 11 and 7 are given when the end of the list is reached.*/)
					break;
				
				//If it is an error, then first close the directory stream
				if (closedir(directory) != 0)
					throw UnknownError(errorCode);
			  
				//	and then throw the error
				throw UnknownError(errorCode);
			}
			
			//Retrieve information about the entry
			struct stat statistics;
			if (stat((path + '/' + directoryEntry->d_name).c_str(), &statistics) != 0)
			{
				int errorCode = errno;
				
				if (errorCode == ENOENT || errorCode == ENOTDIR)
					return dirs;
				else if (errorCode == EACCES)
					throw AccessDeniedFileSystemError();
				else if (errorCode == EIO)
					throw PhysicalIoFileSystemError();
				else if (errorCode == ELOOP)
					throw LoopFoundInPathFileSystemError();
				else if (errorCode == ENAMETOOLONG)
					throw PathTooLongFileSystemError();
				else
					throw UnknownError(errorCode);
			}

			//	and if it is an directory and not the . and .. directories, add it to the list.
			if (S_ISDIR(statistics.st_mode) && string(directoryEntry->d_name) != string(".") && string(directoryEntry->d_name) != string(".."))
			{
				dirs.insert(dirs.end(), directoryEntry->d_name);
			}
		}

		return dirs;
	}
```

---

### Post by trent.josephsen on 2010-06-10
I re-considered what you were expecting to happen, and it occurred to me that you are under the mistaken impression that errno should be set to 0 if no error happens.  In fact, no standard function ever sets errno to 0 (someone correct me if I'm wrong).  You must zero it yourself before calling the function if you want to check it against 0 (line 25 of the posted code).

---

### Post by dwhitney67 on 2010-06-10
> **Magnificence said:**
> 
I don't know why I get these errors when the end of the directory is reached, or maybe the errors actually occur, but then I still don't know why. I've currently build a work-around, but I would really appreciate some help.

Thanks.

How are you getting these errors?  Are you removing a file from the directory as the readdir() progresses through its entries?

A simple program would not yield any such errors; for example:
```

#include <dirent.h>
#include <sys/stat.h>
#include <cerrno>
#include <cstring>
#include <iostream>

int main()
{
   const char* dirname = "/tmp";
   DIR* dir = opendir(dirname);

   if (dir)
   {
      dirent* entry = 0;

      while ((entry = readdir(dir)) != 0)
      {
         std::cout << "Found entry: " << entry->d_name << std::endl;
      }

      if (!entry)
      {
         std::cerr << "error = " << strerror(errno) << " [" << errno << "]" << std::endl;
      }

      closedir(dir);
   }
   else
   {
      std::cerr << "Failed to open directory " << dirname << std::endl;
   }
}

```
As for all of the flavours of exception classes, why don't you condense those into one class.  For example:
```

class MyException : public std::exception
{
public:
   MyException(const char* reason, const int errnum) throw() : reason(reason), errnum(errnum) {}

   virtual ~MyException() throw() {}

   virtual const char* what() const throw()
   {
      std::stringstream oss;
      oss << reason << " [" << errnum << "]";
      return oss.str().c_str();
   }

private:
   std::string reason;
   int         errnum;
};

```
To use the above, something like:
```

throw MyException(strerror(errno), errno);

```

---

### Post by Magnificence on 2010-06-11
> **trent.josephsen said:**
> I re-considered what you were expecting to happen, and it occurred to me that you are under the mistaken impression that errno should be set to 0 if no error happens.  In fact, no standard function ever sets errno to 0 (someone correct me if I'm wrong).  You must zero it yourself before calling the function if you want to check it against 0 (line 25 of the posted code).
Ok, then I think I should check if the end of the list is reached in another way.

> **dwithney67]if (!entry)
      {
         std::cerr << "error = " << strerror(errno) << " [" << errno << "]" << std::endl said:**
> 
It seems that you are checking if entry is zero, but isn't that what I'm doing too?

Anyway, this is what the opengroup's documentation says:
[QUOTE]Upon successful completion, readdir() shall return a pointer to an object of type struct dirent. When an error is encountered, **a null pointer shall be returned and errno shall be set to indicate the error**. When the end of the directory is encountered, **a null pointer shall be returned and errno is not changed**.
Now, how do I check if an error is found? In both cases a null pointer is returned, but how do I distinguish (am I saying this correctly? :P) these cases?

---

### Post by trent.josephsen on 2010-06-11
Just like I said -- set errno = 0 before calling readdir.

---

### Post by dwhitney67 on 2010-06-11
> **Magnificence said:**
> 
Now, how do I check if an error is found? In both cases a null pointer is returned, but how do I distinguish (am I saying this correctly? :P) these cases?

This was the issue I found; when readdir() returns null, that indicates it has no more entries cached.  As Trent indicated, if you set errno to zero before each iteration of your while loop, then when readdir() returns null under nominal situations, errno will still be 0.  Otherwise it will be set to something else.

To check for an error:
```

...

dirent* entry = 0;
errno = 0;

while ((entry = readdir(dirp)) != 0)
{
   ...
}

if (errno != 0)
{
   // error with readdir() occurred
}

```
Alternatively:
```

...

while (true)
{
   errno = 0;
   dirent* entry = readdir(dirp);

   if (entry == 0)
   {
      if (errno != 0)
      {
         // error
      }

      break;
   }

   ...
}

```

---

### Post by Magnificence on 2010-06-11
Hmm, ok, that's sounds a good idea. I'll try it out when I have some time again. BTW, isn't errno a macro?

---

### Post by trent.josephsen on 2010-06-11
> **Magnificence said:**
> Hmm, ok, that's sounds a good idea. I'll try it out when I have some time again. BTW, isn't errno a macro?

Yes, but it is also an lvalue (which means it can be assigned to).  [ISO/IEC 9899:1999 7.5p2](www.open-std.org/jtc1/sc22/wg14/www/docs/n1256.pdf)

---

### Post by dwhitney67 on 2010-06-12
> **Magnificence said:**
> ... BTW, isn't errno a macro?
No it is not a macro.  It is a variable of type int.  Look at errno.h

---

### Post by trent.josephsen on 2010-06-12
> **dwhitney67 said:**
> No it is not a macro.  It is a variable of type int.  Look at errno.h

I found:
```

#ifndef errno
extern int errno;
#endif
```

The macro is actually defined in <bits/errno.h> as
```
#   define errno (*__errno_location ())
```

But whether it's a macro or a variable with external linkage is really inconsequential.  (The Standard calls it a macro, but it could just as well be a variable by the "as-if" rule if I'm not mistaken.)  Anyway, what it "really is" doesn't affect how you should use it.

---

### Post by Magnificence on 2010-06-13
Ok, it works! Thank you all guys.

---

