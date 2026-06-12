---
title: "[ C++ ] Is there a way to simulate BACKSPACE ?"
date: 2009-09-30
forum: Programming Talk
---

### Post by credobyte on 2009-09-30
```
ID: 1 <ENTER>

```

When I enter 1, it'll launch an application and watch for it ( running or not ). Now, when I close it, I need a way to automatically remove my previously entered number, so I would see the same ID:, waiting for my input.

Note: Standard library only ( don't want to use ncurses ).

Any ideas ?

---

### Post by dribeas on 2009-09-30
The standard does not have operations for that. You can either use libraries (ncurses) or implement the same functionality by sending escape sequences to the terminal, but that will be highly non-portable: depending on the specific terminal you have the escape sequences can differ.

The easiest standard way of doing it is by prompting the user again:

```

ID: 1<Enter>
ID: _

```

This will also allow the runned applications to output information to the user.

---

### Post by credobyte on 2009-09-30
> **dribeas said:**
> The standard does not have operations for that. You can either use libraries (ncurses) or implement the same functionality by sending escape sequences to the terminal, but that will be highly non-portable: depending on the specific terminal you have the escape sequences can differ.

The easiest standard way of doing it is by prompting the user again:

```

ID: 1<Enter>
ID: _

```This will also allow the runned applications to output information to the user.

I simply can't make another prompt, just because of the fact that my program looks like this:
```
1. BBC One            5. Euronews
2. BCC News           6. ...
3. Flaunt
4. Clubland TV
-------------------------------------
Play (ID):
```The list is a little bit longer ( ~ 60 entries ), so if I'll make a new prompt, I'll need to scroll up/down to see the list ( which is uncomfortable ).

---

### Post by A_Fiachra on 2009-09-30
What if you check for 0x08??

---

### Post by credobyte on 2009-09-30
> **A_Fiachra said:**
> What if you check for 0x08??


[LIST=1]
[*]What does it mean ?
[*]How do I {check for it} ?
[/LIST]

---

### Post by Arndt on 2009-09-30
> **dribeas said:**
> The standard does not have operations for that. You can either use libraries (ncurses) or implement the same functionality by sending escape sequences to the terminal, but that will be highly non-portable: depending on the specific terminal you have the escape sequences can differ.

The easiest standard way of doing it is by prompting the user again:

```

ID: 1<Enter>
ID: _

```

This will also allow the runned applications to output information to the user.

Escape sequences are nonportable, but one of the more portable control characters is "clear screen", which is ^L. Clear the screen and print everything again. Instead of outputting ^L yourself, you can call the little program 'clear' - then it's even portable.

---

### Post by dwhitney67 on 2009-09-30
> **credobyte said:**
> I simply can't make another prompt, just because of the fact that my program looks like this:
```
1. BBC One            5. Euronews
2. BCC News           6. ...
3. Flaunt
4. Clubland TV
-------------------------------------
Play (ID):
```The list is a little bit longer ( ~ 60 entries ), so if I'll make a new prompt, I'll need to scroll up/down to see the list ( which is uncomfortable ).

Here's a small app that handles the basics of terminal I/O, without the usage of ncurses.

Compile it and give it a shot; later, augment it with your 60 entries.  Although with that many entries, I would recommend that you employ the use of more columns in your menu.  The app below only supports two columns.

```

#include <iostream>
#include <cstdio>
#include <cstring>
#include <cassert>
#include <termios.h>


void displayMenu(const char* prompt, const char* menuItems[], const size_t numItems);
int  getInput();


int main()
{
   const char*  menu[] = { "BBC One", "BBC News", "Flaunt", "Clubland TV", "Euronews", "...", "Quit" };
   const size_t menuSz = sizeof(menu) / sizeof(char*);
   const char*  prompt = "Play (ID): ";

   displayMenu(prompt, menu, menuSz);

   unsigned int choice = getInput();

   while (choice != menuSz)
   {
      if (choice >= 1 && choice <= menuSz)
      {
         std::cout << "\r                              ";  // clear previous entry
         std::cout << "\r" << prompt << choice;

         // handle input
      }
      else
      {
         std::cout << "\r" << prompt << choice << " <--- Bad Input!!!";
      }

      choice = getInput();
   }
   std::cout << "\r" << prompt << choice << "                  ";
   std::cout << "\nAll done.\n" << std::endl;
}

void displayMenu(const char* prompt, const char* menuItems[], const size_t numItems)
{
   const size_t COL = 2;

   size_t rows = (numItems / COL) + (numItems % COL > 0 ? 1 : 0);

   for (size_t i = 0; i < rows; ++i)
   {
      const int num = i + 1;

      std::cout << num << ". " << menuItems[i] << "\t\t";

      if (i + rows < numItems)
      {
         std::cout << (num + rows)<< ". " << menuItems[i + rows];
      }
      std::cout << std::endl;
   }
   std::cout << "--------------------------------------------\n" << prompt;
}

int getInput()
{
  int            ch;
  struct termios old;
  struct termios tmp;

  if (tcgetattr(STDIN_FILENO, &old))
  {
    return -1;
  }

  memcpy(&tmp, &old, sizeof(old));

  tmp.c_lflag &= ~ICANON & ~ECHO;

  if (tcsetattr(STDIN_FILENO, TCSANOW, (const struct termios*) &tmp))
  {
    return -1;
  }

  ch = getchar();

  tcsetattr(STDIN_FILENO, TCSANOW, (const struct termios*) &old);

  return ch - '0';
}

```

---

### Post by A_Fiachra on 2009-09-30
> **credobyte said:**
> 
[LIST=1]
[*]What does it mean ?
[*]How do I {check for it} ?
[/LIST]

  

Come to think of it, I'm remembering old school conio.h from DOS days.  I think the other suggestions have you covered.

---

