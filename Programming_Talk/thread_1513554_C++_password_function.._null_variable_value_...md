---
title: "C++: password function.. null variable value .."
date: 2010-06-19
forum: Programming Talk
---

### Post by James78 on 2010-06-19
Hi,

I created this function to enter passwords for.. But there's one issue.. The string always has nothing in it by the time the while loop ends, almost like nothing was entered. Any ideas as to why?

Here's a quick example I mopped up showing what happens (or doesn't happen in this case):
[PHP]int getch()
{
    int ch;
    struct termios oldt, newt;

    tcgetattr (STDIN_FILENO, &oldt);
    newt = oldt;
    newt.c_lflag &= ~(ICANON | ECHO);
    tcsetattr (STDIN_FILENO, TCSANOW, &newt);
    ch = getchar();
    tcsetattr (STDIN_FILENO, TCSANOW, &oldt);

    return ch;
}

int main(int argc, char** argv)
{
    string accountPass;

    int i = 0;
    while (true) {
        accountPass[i] = getch();
        if (accountPass[i] == '\n') {
            break;
        }

        // In VT100 (I use Konsole) backspace (delete key) == 0x7f
        if ((accountPass[i] == 0x7f) && (i >= 1)) {
            cout << "\b \b";
            accountPass[i] = '\0';
            i--;
        }
        else if (accountPass[i] != 0x7f) {
            cout << "*";
            i++;
        }
    }

    // accountPass will output NOTHING
    cout << accountPass << endl;
    return 0;
}[/PHP]

---

### Post by dwhitney67 on 2010-06-19
```

        //accountPass[i] = getch();
        accountPass += getch();

```


P.S.  Use the PAM API.

---

### Post by James78 on 2010-06-19
That helped somewhat. But if I enter "as" in there, it only shows "a" and nothing after. Which is pretty strange. Also, wouldn't the first character be in the offset of +1? I didn't really want to handle the first character by creating an if or anything. I guess whatever needs to be done though.

Edit: Does the same on a char[30]. Must be some inherent flaw hmm...

---

### Post by dwhitney67 on 2010-06-20
> **James78 said:**
> That helped somewhat. But if I enter "as" in there, it only shows "a" and nothing after. Which is pretty strange. Also, wouldn't the first character be in the offset of +1? I didn't really want to handle the first character by creating an if or anything. I guess whatever needs to be done though.

Edit: Does the same on a char[30]. Must be some inherent flaw hmm...

I have no idea what issue you are still experiencing.  You're dealing with C++, not C.  Forget arrays and forget adding a character at some index.

When you declare a string, it is automatically set to a null-string (via the constructor).  When you append to said string using the += operator, it takes care of whatever is necessary to accommodate the additional string or character (as in your case) that is added.

Perhaps you should forget about 'i', and use something like the following:
```

    std::string accountPass;

    std::cout << "Enter password: ";

    while (true)
    {
        accountPass += getch();

        const size_t lastCharPos = accountPass.size();

        // use lastCharPos to do whatever you need...
    }

```


P.S.
```

//
// To build:
//
//      gcc pam_password.c -lpam -lpam_misc
//
// To get PAM development library:
//
//      sudo apt-get install libpam-dev
//
//
#include <security/pam_appl.h>
#include <security/pam_misc.h>
#include <stdio.h>

int main(int argc, char** argv)
{
   const char*            user = getenv("USER");
   static struct pam_conv pam_conversation = { misc_conv, NULL };
   pam_handle_t*          pamh;

   int res = pam_start(argv[0], user, &pam_conversation, &pamh);

   if (res == PAM_SUCCESS) {
      res = pam_authenticate(pamh, 0);
   }

   if (res == PAM_SUCCESS) {
      res = pam_acct_mgmt(pamh, 0);
   }

   if (res == PAM_SUCCESS) {
      fprintf(stdout, "Authenticated.\n");
   }
   else {
      fprintf(stdout, "Not Authenticated.\n");
   }

   pam_end(pamh, res);

   return res == PAM_SUCCESS ? 0 : 1;
}

```

---

### Post by James78 on 2010-06-20
It was too much a pain to make it work, so I simply disabled the echo of characters instead using termios. Thanks for the help!

---

### Post by dwhitney67 on 2010-06-20
Here, give this nugget a shot:
```

#include <termios.h>
#include <fcntl.h>
#include <unistd.h>
#include <cstdio>
#include <cstring>
#include <cerrno>
#include <csignal>
#include <string>
#include <iostream>


void sigintHandler(int signo) {}


int enableNoEcho(int fileno, bool enable)
{
   static struct termios old;

   if (enable)
   {
      struct termios tmp;

      if (tcgetattr(fileno, &old))
      {
         return errno;
      }

      memcpy(&tmp, &old, sizeof(old));

      tmp.c_lflag &= ~ICANON & ~ECHO;

      if (tcsetattr(fileno, TCSANOW, (const struct termios*) &tmp))
      {
         return errno;
      }
   }
   else
   {
      tcsetattr(fileno, TCSANOW, (const struct termios*) &old);
   }

   return 0;
}


int enableNonBlocking(int fileno, bool enable)
{
   static int flags = fcntl(fileno, F_GETFL, 0);
   int        rtn   = -1;

   if (enable)
   {
      rtn = fcntl(fileno, F_SETFL, flags | O_NONBLOCK);
   }
   else
   {
      rtn = fcntl(fileno, F_SETFL, flags);
   }

   return rtn;
}


std::string password(const char* prompt)
{
   std::cout << prompt;

   signal(SIGINT, sigintHandler);

   enableNoEcho(fileno(stdin), true);

   std::string pwstring;
   char ch = 0;

   while (true)
   {
      std::cin.get(ch);

      if (ch == 0x1B)   // handle misc keys that generate escape sequences
      {
         enableNonBlocking(fileno(stdin), true);

         while (std::cin.get(ch));

         enableNonBlocking(fileno(stdin), false);

         std::cin.clear();
      }
      else if (ch == '\n')   // we're done when a newline is received
      {
         break;
      }
      else if (ch == 0x7F && pwstring.size() > 0)  // handle delete
      {
         std::cout << "\b \b";
         std::cout.flush();

         pwstring.erase(pwstring.size() - 1);
      }
      else if (isalnum(ch) || ispunct(ch))    // allow alpha-numeric and punctuation chars
      {
         std::cout << "*";
         std::cout.flush();

         pwstring += ch;
      }
   }
   std::cout << std::endl;

   signal(SIGINT, SIG_DFL);
   enableNoEcho(fileno(stdin), false);

   return pwstring;
}


int main()
{
   std::cout << "Your password is: " << password("Enter Password: ") << std::endl;
}

```

---

### Post by James78 on 2010-06-21
Works perfect, thanks. I'm gonna need to go through this one carefully to figure out how it works. :p

---

