---
title: "File searching"
date: 2009-07-10
forum: Programming Talk
---

### Post by swappo1 on 2009-07-10
Hello,

I am writing a program in C++ that searches for files.  If I start with root and open that directory, I get like 10+ directories from that.  Once I start opening those directories I get more directories which ends up being a tree of directories.  I am not sure of the best way to go about accessing a tree of files.  If I store the contents of each directory in a container I will have to keep making a new container for every directory that opens.  I really don't know the best way to handle this.  Can someone point me in the right direction?

---

### Post by smartbei on 2009-07-10
Are you looking to solve a practical problem? If so, then quite a few people have already solved this part of it. Also, are you sure you need to store all of that information? If you are searching for a file, for example, you just need to do some sort of test on a particular path (or on the file at that path), and if it passes print out the output. No need for complex datastructures at all.

Otherwise, How about something like a Directory class that holds a linked list of child directories, and while recursing through the filesystem you add it's children directories to it. You could also have another linked list for files. That way, it is no problem to dynamically add more directories as you are scanning. Take a look at STL lists for example: [http://www.sgi.com/tech/stl/List.html](http://www.sgi.com/tech/stl/List.html).

---

### Post by swappo1 on 2009-07-10
Yes, I am looking to solve a practical problem.  I know this has been done before but I am writing this program as an exercise.  I think this program would be something like the find command in bash.  Any ideas how I could access the files for the find command so I could see how it is written?  I am assuming it is written in C and uses the C library?

---

### Post by soltanis on 2009-07-10
Yeah, you can download the source package for coreutils which I think find is a part of. If you're writing this as a coding exercise to yourself, then I would suggest an recursive-descent strategy, starting at the top directory, examining the contents, reading files first, then repeating the procedure for all subdirectories.

This would effectively search all subdirectories for a file, at the cost of being recursive (possibility of running out of stack space).

EDIT.

Your other option (are you using C++? well you can do this with classes though I describe it with structs) is to first climb down the entire directory tree and construct a representation of it in memory using a B+ tree:

```

struct trnode {
        struct trnode **children;
        int nchildren;
        unsigned char flagged;
        char dirname[MAX_NAMELEN];
};

```

When you enumerate a directory, you would then malloc an array of struct trnode* equivalent to the number of subchildren. Then, set the number of children, set the flag equal to zero, and set the directory name. Do this for every directory level, until no more directories have subdirectories.

Then, descend through the tree, starting at the first child of every node, looking for whatever. When you reach a directory with no subdirectories, climb back up the tree and mark the flags on all the directories until you reach a branching point, descend back down, and repeat the strategy.

This would be a depth first search.

---

### Post by dwhitney67 on 2009-07-10
Just use a combination of opendir() and readdir(), in a recursive function.

You begin by calling the function to open a directory, and if successful, you read the contents.  If one of the contents happens to be another directory, then you recursively call the function again.

As you are delving into the directories and subdirectories, if you find a name match with the item you are looking for, just print out the result to stdout.

Here's a related example:
```

#include <dirent.h>
#include <string>
#include <iostream>


bool listFileAndType( const std::string &dir )
{
  DIR *dirp = opendir( dir.c_str() );

  if ( dirp )
  {
    struct dirent *dp = 0;

    while ( (dp = readdir( dirp )) != 0 )
    {
      std::string file( dp->d_name );

      if ( file == "." || file == ".." )   // skip these
        continue;

      if ( dp->d_type == DT_DIR )
      {
        std::string dirPath = dir + "/" + file;

        std::cout << file << ": Directory." << std::endl;

        listFileAndType( dirPath );
      }
      else
      {
        std::cout << file << ": ";

        switch( dp->d_type )
        {
          case DT_FIFO:
              std::cout << "FIFO.";
              break;
          case DT_CHR:
              std::cout << "Character Special.";
              break;
          case DT_BLK:
              std::cout << "Block File.";
              break;
          case DT_REG:
              std::cout << "Regular File.";
              break;
          case DT_LNK:
              std::cout << "Link.";
              break;
          case DT_SOCK:
              std::cout << "Socket.";
              break;
          case DT_WHT:
              std::cout << "WHT.";
              break;
          case DT_UNKNOWN:
          default:
              std::cout << "Unknown Type.";
              break;
        }

        std::cout << std::endl;
      }
    }

    closedir( dirp );

    return true;
  }
  else
  {
    return false;
  }
}

int main( int argc, char **argv )
{
  const std::string dir = (argc > 1 ? argv[1] : "foo");

  if ( listFileAndType( dir ) == false )
  {
    std::cout << "Error:  Cannot open directory '" << dir << "'" << std::endl;
  }

  return 0;
}

```

To test:
```

g++ FileType.cpp

./a.out .

```

---

### Post by stroyan on 2009-07-10
If you just want results you could use the nftw() library function.
If you seek enlightenment about how to walk directories then get the source code for ntfw.
You could use
apt-get source libc6
and edit glibc-2.9/io/ftw.c

or look at the source code on the web with [http://www.google.com/codesearch/p?hl=en&sa=N&cd=1&ct=rc#bZFm81g2I8w/glibc-2.1.1/io/ftw.c&q=ftw_dir](http://www.google.com/codesearch/p?hl=en&sa=N&cd=1&ct=rc#bZFm81g2I8w/glibc-2.1.1/io/ftw.c&q=ftw_dir)

---

### Post by swappo1 on 2009-07-11
I am having trouble with this member funciton.  Here is the code:
```
void Find::get_dir(const string& path)
{
	DIR *dp = opendir(path.c_str());
	cout << path << "  " << dp << endl;
	struct dirent *ep;
	if(dp == NULL)
		throw domain_error("ERROR - " + path + " is not a valid path.");
	while( (ep = readdir( dp ) ) != 0 )
	{
		string file(ep->d_name);
	
		if(file == "this_test_file.txt")
				cout << file << " is in path: " << path << endl;
			
		if(file == "." || file == "..")
			continue;
	
		if(ep->d_type == DT_DIR)
		{
			string new_path = path + "/" + file;
			get_dir(new_path);
		}
	}
	closedir(dp);
}
```
Here is the output from it:
```
/  0x9804020
//root  0
terminate called after throwing an instance of 'std::domain_error'
  what():  ERROR - //root is not a valid path.
Aborted

```
Yet if I change the code to the following:
```
void Find::get_dir(const string& path)
{
	DIR *dp = opendir(path.c_str());
	if(dp)
	{
		struct dirent *ep;
		while( (ep = readdir( dp ) ) != 0 )
		{
			string file(ep->d_name);
	
			if(file == "this_test_file.txt")
					cout << file << " is in path: " << path << endl;
			
			if(file == "." || file == "..")
				continue;
	
			if(ep->d_type == DT_DIR)
			{
				string new_path = path + "/" + file;
				get_dir(new_path);
			}
		}
	}
	closedir(dp);
}
```
I get the output I am looking for:
```
this_test_file.txt is in path: //home/hopchewer/TEST

```
If the second time through the recursive function, dp = 0, shouldn't if(dp) be skipped since it is not a true statement?  Isn't that why a standard exception is being thrown in the first version of the function?  I'm confused as to why one version works but the other doesn't.

---

### Post by stroyan on 2009-07-11
It seems likely that you got an EACCES error from opendir("//root").
You probably lack permissions.
The first version will give up with the first failed opendir.
The second version will go on to try the rest of the directories it can open.

---

### Post by dwhitney67 on 2009-07-11
The second example is the preferred way, although you really do not need to call closedir() unless you were able to open the directory.  I would recommend placing the call to closedir() within the if-block, not outside of it.

In conclusion, any failure to open a directory is not a failure per se, and thus you should just return from the function.  If you want to mimic the 'find' system utility, then output a statement indicating that you were unable to search a particular path.  The value of 'errno' should provide you the reason for such failure.

---

