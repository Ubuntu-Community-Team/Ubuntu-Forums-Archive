---
title: "Input a string like a terminal password"
date: 2009-10-18
forum: Programming Talk
---

### Post by Ratscallion on 2009-10-18
Hello fellow programmers.

I'm using C++ and am making an app in the console/Terminal (I'm not that experienced, but I can interpret quite a bit of code) that has a password in it.
I want to either have it when user inputs their password (which is a string) into the terminal when it asks for user name and password that it shows no input (like if you do a sudo command in Linux, it goes in, but you don't see anything). Or, if that isn't possible (or you don't know how), it could go in in *s. So when user enters a character they see it as a *. 

Thanks.

---

### Post by OpenGuard on 2009-10-18
[URL="http://publib.boulder.ibm.com/infocenter/zos/v1r10/index.jsp?topic=/com.ibm.zos.r10.bpxbd00/rgpass.htm"]getpass()
[/URL]

---

### Post by Ratscallion on 2009-10-19
Thanks! I'll look into that when I get the chance!

---

### Post by dwhitney67 on 2009-10-19
If you want to know the nuts-n-bolts solution, below is one:
```

#include <iostream>
#include <string>
#include <termios.h>

int terminalEcho(bool flag)
{
  struct termios tios;

  if (tcgetattr(STDIN_FILENO, &tios))
  {
     return -1;
  }

  tios.c_lflag &= (flag ? ECHO : ~ECHO);

  if (tcsetattr(STDIN_FILENO, TCSANOW, &tios))
  {
     return -1;
  }

  return 0;
}

std::string getpass()
{
   std::string password;

   terminalEcho(false);

   std::cout << "Password: ";
   std::cin >> password;
   std::cout << std::endl;

   terminalEcho(true);

   return password;
}

int main()
{
   std::string pw = getpass();

   std::cout << "Your password is '" << pw << "'." << std::endl;
}

```

---

### Post by Ratscallion on 2009-10-19
Oooh.. Awesome! That's brilliant! Now, does that work on Windows as well as Linux (and Mac too, but that's the last port of call when I'm debugging)

---

### Post by dwhitney67 on 2009-10-19
I've tested it with Linux and with a Mac -- albeit with one little bug fix (see below). 

In theory it should work with Windows, but since I do not have access such a system, you will have to discover for yourself whether the code works or not.

The bug fix mentioned earlier was within the terminalEcho() function.  The code should be corrected as follows:
```

int terminalEcho(bool flag)
{
  ...

  if (flag)
  {
     tios.c_lflag |= ECHO;
  }
  else
  {
     tios.c_lflag &= ~ECHO;
  }

  ...
}

```

---

### Post by Ratscallion on 2009-10-19
Awesome.. Chers for all your help!

---

### Post by openfly on 2009-10-19
curses also offers a noecho option.

---

