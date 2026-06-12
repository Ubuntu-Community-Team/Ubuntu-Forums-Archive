---
title: "C++ Kubuntu Integration"
date: 2008-04-22
forum: Programming Talk
---

### Post by yao_man on 2008-04-22
I am currently using Kubuntu 8.04. Although I do not know any bash, I altered the bash shell (via internet guides) to append history instead of truncating the history file. After editing the shell, the default way to clear the history (history -c) only clears the interactive history and not the actual history file (since it is no longer truncated upon closing the shell). I then wrote a c++ script to clear the contents of the history file (or an alternative file if one is presented as an argument). It works when I try to access the $HOME environmental variable using getenv("HOME"), but I receive a segmentation fault when I try to use getenv("HISTFILE"). I also wanted to clear the interactive history at the same time. I tried system("history -c") but I received an error as "history" could not be found. I was wondering if there is a way to directly access the environment variable $HISTFILE and also call the shell command history -c. Here is my current c++ script ```
#include <string>
#include <iostream>
#include <fstream>
#include <stdlib.h>
#include "/mydocuments/Documents/c++/headers/stringcaps.h"
using namespace std;




int main (int argc, char * argv[])
{
	string file, input = getenv("HOME");		 //input is set to $HOME variable for use with file
	if (argc == 1)				 //I would prefer to use $HISTFILE if possible
		file = input + "/.bash_history"; 	 //set file to default $HOME/.bash_history
	else
		file = argv[1]; //file becomes offered argument
	ifstream file_check;			 //open file to check
	file_check.open(file.c_str());		 //if it exists
	if (file_check.fail())			 //if not, abort
		cout << file << " does not exist\nNothing was cleared" << endl;
	else					 //if file exists, continue
	{
		file_check.close();		 //close test file before continuing
		cout << "The contents of " << file 
		<< " will be cleared" << endl;
		cout << "Action cannot be reversed\nContinue? [y/n] -> ";
		getline(cin, input);
		if (input == "")
			input = "y";
		lowercase(input);		 //function that changes a string to all lowercase letters found in stringcaps.h
		if (input[0] == 'y')
		{
			ofstream hist_file;
			hist_file.open(file.c_str(), ios::trunc); //open file and erase contents
			hist_file.close();
			/* Next line is currently removed until the problem is solved
			system("history -c");*/
			cout << file << " has been cleared" << endl;
		}
		else
			cout << file << " not cleared" << endl;
	}
	return 0;
}
```

I would appreciate any help you can offer me or any advice on optimizing or improving the code.

A semi-related question, if an argument is surrounded by quotes, is it still separated by whitespace or will it accept the entire quote as a single argument?

Thanks again for any help.

---

### Post by yao_man on 2008-04-22
I found how to include $HISTFILE. In the alias I use to run the c++ script and clear the history file, I included an extra line at the beginning. export HISTFILE. After exporting, I successfully acquired $HISTFILE from within the c++ script. Now then, if anyone knows how to run the shell command "history -c" from within the c++ script or check for y/n answer within the script from the bash shell, please help me out. I appreciate any help.

---

### Post by dwhitney67 on 2008-04-22
Here's my take on your C++ program... sorry, I couldn't help but clean it up a bit.
[PHP]#include <string>
#include <fstream>
#include <iostream>
#include <ctype.h>

using namespace std;

int main( int argc, char **argv )
{
  const char *env = getenv("HOME");
  if ( env == NULL )
  {
    cout << "environment variable HOME is not defined" << endl;
    return 1;
  }
  string file  = (argc > 1 ? argv[1] : (string(env) + "/.bash_history"));

  fstream hist_file( file.c_str(), ios::in );

  if (!hist_file)
  {
    cout << file << " does not exist!" << endl;
    return 2;
  }
  hist_file.close();

  cout << "The contents of " << file << " will be cleared" << endl;
  cout << "Action cannot be reversed\nContinue? [y/n] -> ";

  string input;
  getline(cin, input);

  if (tolower(input[0]) == 'y' || input == "" )
  {
    fstream hist_file( file.c_str(), ios::out | ios::trunc ); //open file and erase contents

    /* Next line is currently removed until the problem is solved
       system("history -c");
     */

    cout << file << " has been cleared" << endl;
    hist_file.close();
  }
  else
  {
    cout << file << " not cleared" << endl;
  }

  return 0;
}[/PHP]

---

### Post by dwhitney67 on 2008-04-23
> **yao_man said:**
> I found how to include $HISTFILE. In the alias I use to run the c++ script and clear the history file, I included an extra line at the beginning. export HISTFILE. After exporting, I successfully acquired $HISTFILE from within the c++ script. Now then, if anyone knows how to run the shell command "history -c" from within the c++ script or check for y/n answer within the script from the bash shell, please help me out. I appreciate any help.
To run a shell command from a C/C++ program, use the system() library function.  For example:

[PHP]int main()
{
  ...
  system( "history -c" );
  ...
  return 0;
}[/PHP]

For the bash-shell question,

```
#!/bin/bash

echo -n "Do you want to continue? [y/n] "
read ans

case $ans in
    [nN]*)   echo "apparently continuing is not an option;
             exit 0;;
    *)       echo "Fine, let's continue";;
esac
#... complete rest of the script...

```

---

### Post by yao_man on 2008-04-23
Thank you very much for your input. I took your advice and modified the program, but there were modifications after what you last saw. Here is what I have come up with after modification. If you don't mind, please look over it again and look for any more improvements.[PHP]#include <string>
#include <iostream>
#include <fstream>
#include <stdlib.h>
using namespace std;




int main (int argc, char **argv)
{
	const char * def_file = getenv("HISTFILE");
	string input, file = (argc > 1 ? argv[1] : def_file);
	fstream file_check;			 //open file to check
	file_check.open(file.c_str(), ios::in);	 //if it exists
	if (file_check.fail())			 //if not, abort
	{
		cout << file << " does not exist\nNothing was cleared" << endl;
		return 1;
	}
	file_check.close();		 //close test file before continuing
	cout << "The contents of " << file << " will be cleared" << endl;
	cout << "Action cannot be reversed\nContinue? [y/n] -> ";
	getline(cin, input);
	if (tolower(input[0]) == 'y' || input == "")
	{
		fstream hist_file(file.c_str(), ios::out | ios::trunc); //open file and erase contents
		/* Next line is currently removed until the problem is solved
		system("history -c");*/
		cout << file << " has been cleared" << endl;
		hist_file.close();
	}
	else
		cout << file << " not cleared" << endl;	
	return 0;
}[/PHP]
As for the system("history -c") command, I tried that before and it didn't work. That is why it is currently commented out of my program.
Also, for the bash part, how exactly would I incorporate that into my bash shell? I run the clear program from an alias where .clear_history is the compiled object of the above c++ script. ```
alias ch="export HISTFILE;~/.clear_history"
```How would I incorporate the two together?
Thank you for your help.

---

### Post by dwhitney67 on 2008-04-23
Although your program surely works, is hard to read because many of your statements run together without vertical spaces (i.e blank lines).  Perhaps this is not important to you, but it does make it easier for others to read your code if there is separation of logical blocks of code.

The other thing that you should be concerned about is using the char pointer returned by getenv() without first verifying if it is non-null.  In your code, if HISTFILE had been misspelled or not defined, the code would crash when you attempt to open the file with the C-string returned by file.c_str().

Concerning the system() command, upon reflecting more upon the problem, I think I understand why it doesn't work... the "history" call is a built-in bash service call; not a *nix command.

If your C++ executable is named '.clear_history', and you execute the 'ch' command from your shell, the need for the 'export HISTFILE' is not necessary (although it doesn't hurt to have it).

Try setting up your alias like:
```
alias ch='~/.clear_history'
```

Then source your alias file (or .bashrc) where you have defined your alias.  For example:
```
$ source ~/.bashrc
```

You can verify the alias's setting with:
```
$ alias ch
```

---

### Post by yao_man on 2008-04-23
As for the c++ script divisions, that makes sense. I will try to break up my code from now on to increase readability. I will also modify it accordingly to check for NULL.

As for the export HISTFILE command, it is necessary. I tested it out, and I can add it at any point before running the clear script, but the HISTFILE variable must be exported before the c++ script can have access to it. Instead I added that line to the beginning of my addon file for bash and removed it from the aliases.

As for the alias, I already have the alias setup, I was just asking how to incorporate the two. How could I have it run "history -c" if I input y in the c++ script and not run it if you input anything else?

Here is the newest code with null check and separations: [PHP]#include <string>
#include <iostream>
#include <fstream>
#include <stdlib.h>
using namespace std;




int main (int argc, char **argv)
{
	const char * def_file;
	string input, file;
	fstream file_check, hist_file;

	def_file = getenv("HISTFILE");

	
	if (def_file == NULL && argc == 1)
	{
		cout << "HISTFILE could not be acquired and no file was offered" << endl;
		cout << "Clearing cancelled..." << endl;
		return 3;
	}	
	

	file = (argc > 1 ? argv[1] : def_file);
	

	file_check.open(file.c_str(), ios::in);	 //if it exists
	if (file_check.fail())			 //if not, abort
	{
		cout << file << " does not exist\nNothing was cleared" << endl;
		return 2;
	}
	file_check.close();		 //close test file before continuing
	
	
	cout << "The contents of " << file << " will be cleared" << endl;
	cout << "Action cannot be reversed\nContinue? [y/n] -> ";
	getline(cin, input);
	
	
	if (tolower(input[0]) != 'y' && input != "")
	{
		cout << file << " not cleared" << endl;	
		return 1;
	}
	
	else
	{
		hist_file.open(file.c_str(), ios::out | ios::trunc); //open file and erase contents
		
		
		/* Next line is currently removed until the problem is solved
		system("history -c");*/
		
		
		cout << file << " has been cleared" << endl;
		hist_file.close();
		return 0;
	}
}[/PHP]

---

### Post by yao_man on 2008-04-24
Is there a way to catch a c++ scripts main function return value in the bash shell and use it to determine whether or not to run a code?

---

### Post by dwhitney67 on 2008-04-24
Yes!

From within the bash script:
```

#!/bin/bash

# run application
~/my_app

# save return status that is returned by main
app_status=$?
echo "the program exited with status = $status"

...
```

Alternatively, you can do something like:
```
...
if [ $? eq 0 ]
then
    echo "success"
else
    echo "failure"
fi
...
```

The main lesson is that "$?" contains the value you seek.

---

### Post by yao_man on 2008-04-24
Fantastic, thank you very much. I got everything working to perfection. If anyone is wondering or looking for a way to do this, here is the code I used. I replaced the aliases with function calls. ```
clearhistory () {
        if [ $1 ];then
                ~/.clear_history $1
        else
                ~/.clear_history $HISTFILE
        fi
        if [ $? == 0 ];then
                history -c
        fi
}

```
Since my c++ code only returns 0 if it erases the file, this works perfectly.

---

