---
title: "C++: detect if a file is a link"
date: 2008-05-25
forum: Programming Talk
---

### Post by xlinuks on 2008-05-25
Hi,
I would like to know how can I detect (in C++) whether a file is actually a link (be it symbolic or hard link).
Here's an example, Nautilus says the file "/usr/bin/X11" is "Link to folder".
I didn't find a way to detect the file type of that file, all I get is "Unknown" using the POSIX libraries (I'm learning C++):
1) I have "struct dirent *currentFile"
2) Then I check it's type "unsigned char fileType = currentFile->d_type;"
Then go through if/else checks:
```

string sFileType;

if (fileType == DT_REG) {
                sFileType = "File";
        } else if (fileType == DT_DIR) {
                sFileType = "Directory";
                isDirectory = true;
        } else if (fileType == DT_FIFO) {
                sFileType = "FIFO";
        } else if (fileType == DT_SOCK) {
                sFileType = "Local socket";
        } else if (fileType == DT_CHR) {
                sFileType = "Character device";
        } else if (fileType == DT_BLK) {
                sFileType = "Block device";
	} else if( fileType == DT_UNKNOWN ) {
                sFileType = "Unknown file type";
	} else {
		sFileType = "Unknown";
	}

```

And I get "Uknown" for the file I mentioned above! Please help!

PS: the "ISLNK" macro doesn't seem to detect it either:
struct stat fileInfo;
stat((sParentDirPath + "/" + sFileName).c_str(), &fileInfo);

```

if( S_ISLNK( fileInfo.st_mode) != 0 ) {
	sFileType = "Symbolic Link";
}

```

---

### Post by NormR2 on 2008-05-25
What is the value in the variable: fileType?
Compare it manually with the values of the DT_...s to see what it is.

---

### Post by xlinuks on 2008-05-25
Thanks for the tip, the value is 10, I hand-coded it into the class and it kinda works.
I'm still wondering how people (in real life) work around it.
Perhaps I'll try to have a look at Nautilus source code, hopefully I'll find the piece of code I'm interested in.

---

### Post by geirha on 2008-05-25
I believe you need to use lstat() to determine if it is a symbolic link. Hard links are regular files.

---

### Post by dwhitney67 on 2008-05-25
I cannot fathom why you are having issues determining if a file is a symbolic link.  I wrote a short program (see below), and I had no trouble determining the file types.
[PHP]
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

        // recurse into directory
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
[/PHP]

---

### Post by xlinuks on 2008-05-25
Thanks a lot, I didn't know that there's a DT_LNK for I've been using the following page as a reference which doesn't list a "DT_LNK":
[http://www.delorie.com/gnu/docs/glibc/libc_270.html](http://www.delorie.com/gnu/docs/glibc/libc_270.html)

---

### Post by slavik on 2008-05-25
you may also want to look into 'test' since it handles all the various file tests and such.

---

### Post by moma on 2008-05-25
Take a look at the "readlink" command in the coreutils package.
$ [COLOR="Green"]readlink -f /usr/bin/firefox [/COLOR]

Get the source for the coreutils pkg. But first, activate the Ubuntu's deb-src (source code) repository in the Software sources dialog / Synaptic. Then apt-get the source code.
$ [COLOR="Green"]apt-get source coreutils[/COLOR]
$ [COLOR="Green"]cd coreutils-6.10[/COLOR]
$ [COLOR="Green"]grep -R readlink *[/COLOR]

But if you like, here's another example that should work.
Compile and run it 
$ [COLOR="Green"]gcc test.c -o test[/COLOR]
$ [COLOR="Green"]./test afile[/COLOR]

```
#include <stddef.h>
#include <stdio.h>
#include <stdlib.h>

#include <sys/types.h>
#include <sys/stat.h>


int main( int argc, char **argv)
{
   struct stat statinfo;
   char *filename = argv[1];

   if (argc < 1)
   {
      fprintf(stderr, "Usage: %s  filename\n", argv[0]);
      exit(1);
   }

   if( lstat(filename, &statinfo ) < 0) 
   {
        perror( filename );
        exit(1);
    }

   if (!S_ISLNK (statinfo.st_mode) && statinfo.st_nlink > 1)
   {
  	printf("The file %s IS A HARD LINK to another filename (ln file).\n", filename);         
   }
   else if (S_ISLNK (statinfo.st_mode))
      printf("The file %s IS A SYMBOLIC LINK (ln -s file).\n", filename);         
   else {
      printf("The file %s IS NOT A LINK.\n", filename);         
      printf("Check the dp->d_type flag to spesify the filetype (DT_DIR, DT_REG, DT_FIFO, DT_CHR, DT_BLK, DT_SOCK etc...)\n");
   }

}
```

Try with both symbolic (soft) links
$ [COLOR="SeaGreen"]ln -s file symboliclinkname[/COLOR]
And with hard links
$ [COLOR="SeaGreen"]ln file anothername[/COLOR]

[COLOR="Red"]Code::Blocks IDE [on Ubuntu....]("http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html")[/COLOR]

---

### Post by dwhitney67 on 2008-05-25
> **xlinuks said:**
> Thanks a lot, I didn't know that there's a DT_LNK for I've been using the following page as a reference which doesn't list a "DT_LNK":
[http://www.delorie.com/gnu/docs/glibc/libc_270.html](http://www.delorie.com/gnu/docs/glibc/libc_270.html)
To determine the various types of DT_<whatever>, I went straight to the source where that information is defined... the dirent.h header file.  :)

The header file is located at /usr/include/dirent.h

---

