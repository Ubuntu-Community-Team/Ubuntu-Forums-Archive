---
title: "Recursion Search Advice"
date: 2008-01-06
forum: Programming Talk
---

### Post by t3hi3x on 2008-01-06
Hokay....ROUND ---(anyone who gets this is awesome)---

anyway...

I am trying to figure out how to count all the files of the same of type in a current directory recursively. I've got one huge step down: seeing if all the files in a single folder are that file type.

I need a way to if it's a directory to go into that folder and search it. I can't figure that out. I keep getting caught up on creating new DIR objects.

Here is the code:

[PHP]#include <dirent.h>
#include <errno.h>
#include <string.h>
#include <stdlib.h>
#include <iostream>
#include <iomanip>

using namespace std;

bool is_dir (const char* dir_char)
{
	struct stat s;
	if(stat(dir_char, &s))
		{cerr << dir_char << " is unreadable, ignoring." << endl;
		return true;}
	else
		{
		if(!S_ISDIR(s.st_mode)){return false;} else{return true;}
		}
}

int wild_test(const char *wild, const char *string) {

  const char *cp = NULL, *mp = NULL;

  while ((*string) && (*wild != '*')) {
    if ((*wild != *string) && (*wild != '?')) {
      return 0;
    }
    wild++;
    string++;
  }

  while (*string) {
    if (*wild == '*') {
      if (!*++wild) {
        return 1;
      }
      mp = wild;
      cp = string+1;
    } else if ((*wild == *string) || (*wild == '?')) {
      wild++;
      string++;
    } else {
      wild = mp;
      string = cp++;
    }
  }

  while (*wild == '*') {
    wild++;
  }
  return !*wild;
}

int main( int argc, char *argv[] ) {
    DIR *pDIR;
    struct dirent *pDirEnt;

    pDIR = opendir(argv[1]);

    pDirEnt = readdir( pDIR );
    while ( pDirEnt != NULL ) {
	const char* char_test_dir = pDirEnt->d_name;

	if (!is_dir(char_test_dir) & wild_test("*.c",char_test_dir)){
       cout << pDirEnt->d_name << endl;
        }
	else if (is_dir(char_test_dir))
		{} //here is where i need to do something. I also think it should be a while loop.
	pDirEnt = readdir( pDIR );
    		}

    closedir( pDIR );

    return 0;
}[/PHP]

I'm reasonably new to c++ (been a few weeks now). I've got some ideas, but none seem to complete themselves in my head lol.

Any advice is greatly appreciated.

---

### Post by dwhitney67 on 2008-01-06
The problem you presented is a little tricky, mainly because wildcard statements can be either simple (e.g. *.c) or complicated (e.g. *.c*pp).

Thus, I came up with a solution to the problem of how to figure out how to match strings within the filenames that meet the wildcard criteria.  This involved collecting the tokens that are within the wildcard statement.  Thus for *.c, there is but one token: ".c".  However for *.c*pp, there are two tokens: ".c" and "pp".

Any file that contains the token(s) is considered a valid match.  Thus if the wildcard is "*c*pp", and the filename is "cannot.pp", then this would be a match.  Obviously a file with a name like "file.cpp" is also a match.  I hope this makes sense.

The rest of the exercise is to traverse from a known/valid location and then find all the files, and when necessary, recurse into subdirectories.

Below is the solution I came up with.  If you have any questions, let me know.

[PHP]
#include <dirent.h>
#include <vector>
#include <string>
#include <iostream>

using namespace std;


typedef vector< string > StrVector;


StrVector getWildCardTokens( const string &wildcard )
{
  StrVector wildCardList;

  char *token = strtok( (char*) wildcard.c_str(), "*" );

  while ( token != NULL )
  {
    wildCardList.push_back( token );
    token = strtok( NULL, "*" );
  }

  return wildCardList;
}


void getAllFiles( StrVector &fileList, const string &dirName, const StrVector &wildCards )
{
  DIR *dirp = opendir( dirName.c_str() );

  if ( dirp )
  {
    struct dirent *dp = NULL;

    while ( (dp = readdir( dirp )) != NULL )
    {
        string file( dp->d_name );

        if ( file == "." || file == ".." )    // skip these
          continue;

        if ( dp->d_type == 4 )
        {
          // found a directory; recurse into it.
          string filePath = dirName + "/" + file;

          getAllFiles( fileList, filePath, wildCards );
        }
        else
        {
          bool matches = true;

          // found a file; check if all of the wildcard tokens exist in its name.
          // search linearly thru the file name (i.e. continue where the last token
          // is found).
          for ( int i = 0, pos = 0; i < wildCards.size(); ++i )
          {
            if ( (pos = file.find( wildCards[i], pos )) == string::npos )
            {
              matches = false;
            }
          }

          if ( matches )
          {
            fileList.push_back( dirName + "/" + file );
          }
        }
    }

    closedir( dirp );
  }
}


int main( int argc, char **argv )
{
  string dir      = argc > 1 ? argv[1] : "foo";
  string wildcard = argc > 2 ? argv[2] : "*.cpp";

  StrVector wildCardTokens = getWildCardTokens( wildcard );

  StrVector fileList;
  getAllFiles( fileList, (argc > 1 ? argv[1] : dir), wildCardTokens );

  cout << "Found " << fileList.size() << " files." << endl;
  for ( int i = 0; i < fileList.size(); ++i )
  {
    cout << "found file " << fileList[i] << endl;
  }

  return 0;
}
[/PHP]

P.S.  When programming in C++, you should avoid using a defined object type (e.g. string) as a variable name.  It is easy to get confused between a variable name and the object type.  Consider using 'str', or some other descriptive name for a string.

---

### Post by t3hi3x on 2008-01-12
Thanks a lot for this code. I honestly didnt expect anyone to completely code it all. I get it all and this really helps me learn several things.

---

### Post by dwhitney67 on 2008-01-12
Your welcome for the help.  Hopefully one thing you learned from this exercise is that when faced with a "big" project, it is very helpful to decompose the project into smaller components.

Thus in the example I provided, there's a section to handle user input, another to break apart the wildcard statement, and lastly a section to find filename matches in the directory of interest.

One little thing I could have done to make it a little more efficient would have been to break out of the for-loop that checks for wildcard token matches should a match not be found.

---

### Post by t3hi3x on 2008-01-12
In this case i had actually gotten that wildcard function as an example online, and it worked well. i could do wild_test(pDirEnt->d_name,"*.cpp") and it would tell me if it fit into that. The biggest problem is I never needed to use recursion in programming. I guess that would be the only way to do it here.

Thanks again.

---

