---
title: "c++ question"
date: 2007-12-05
forum: Programming Talk
---

### Post by limac on 2007-12-05
Hi,

I tried running this command using g++ thru terminal:

#include <iostream>
using namespace std;

int main(void)
{
	system("TITLE Calculator");
	system("COLOR 3");

	cout<<9+3<<endl;

	return 0;
}

but this error always pops up:

limac@limac-ubuntu:~$ cd ~/Desktop
limac@limac-ubuntu:~/Desktop$ g++ -o co co.cpp
limac@limac-ubuntu:~/Desktop$ ./co
sh: TITLE: not found
sh: COLOR: not found
12
limac@limac-ubuntu:~/Desktop$ 

What can i do about this?

Thnx

---

### Post by zadig on 2007-12-06
AFAI understand you are trying to change the title of your terminal. I dont think you can just type TITLE to do this. gnome-terminal --title=Calculator should do the trick.

---

### Post by LaRoza on 2007-12-06
Are you getting this code from somewhere else? They are Windows commands, and won't work in Linux.

---

### Post by samjh on 2007-12-06
Not sure what you're trying to accomplish.

The int system(const char *command) function is used for system commands.  This means that any command you pass into that function must be executable on your system's default command interpreter.  If you can't run those commands on terminal - in this case you can't - then they won't work.

---

### Post by Kadrus on 2007-12-06
> **limac said:**
> Hi,

I tried running this command using g++ thru terminal:

#include <iostream>
using namespace std;

int main(void)
{
	system("TITLE Calculator");
	system("COLOR 3");

	cout<<9+3<<endl;

	return 0;
}

but this error always pops up:

limac@limac-ubuntu:~$ cd ~/Desktop
limac@limac-ubuntu:~/Desktop$ g++ -o co co.cpp
limac@limac-ubuntu:~/Desktop$ ./co
sh: TITLE: not found
sh: COLOR: not found
12
limac@limac-ubuntu:~/Desktop$ 

What can i do about this?

Thnx
I think this changes the color of terminal if i am not mistaken...and it's a wrong code...

---

### Post by CptPicard on 2007-12-06
No it doesn't, at least not on any Linux I know. Perhaps on some other OS :)

---

### Post by LaRoza on 2007-12-06
> **CptPicard said:**
> No it doesn't, at least not on any Linux I know. Perhaps on some other OS :)

It is for Windows.

---

### Post by tyoc on 2007-12-06
second time second strike?

--------------------

OK, for dont be 1 line not contributing more than pointing the second strike...

Try the commands of the programm you are trying to compile in the terminal (sh, gnome-terminal and related), you will see the same "fail" results instead of what you are triying to do.
> $ TITLE Calculator
$ COLOR 3If you ask what is that "$" is normally used short of "prompt" of sh (or shell)

in the man I dont remember the page, but for change color codes in console it is something about the escape character then a secuence that "has a meaning" and finally the close indicator.

Here are some results from google for: linux sh console color code

[http://www.funtoo.org/en/articles/linux/tips/prompt/](http://www.funtoo.org/en/articles/linux/tips/prompt/)
[http://www.newlinuxuser.com/linux-console-codes/](http://www.newlinuxuser.com/linux-console-codes/)

Aside: Searching for the man page, have found this, seem usefull for have nice display? hehehe
[http://www.console-colors.de/index.php?n=ColorizerTools.ColorGCC](http://www.console-colors.de/index.php?n=ColorizerTools.ColorGCC)

---

