---
title: "Need a replacement for windows.h in C++ (Or help with some functions)"
date: 2012-06-25
forum: Programming Talk
---

### Post by xXNinjaTurtleXx on 2012-06-25
Hi.
I'm trying to do something in C++ that requires "windows.h" library.
I want to do something like this:
```

void setcolor(unsigned short int color)
{
    HANDLE hcon = GetStdHandle(STD_OUTPUT_HANDLE);
    SetConsoleTextAttribute(hcon, color);
}

```
But for that, I'll need windows.h library, which of course isn't available on Linux.
What could I use instead? I just want to color some text on the console.

Thanks :).

---

### Post by |{urse on 2012-06-25
```
std::cout << "                        " << "\033[33;40m" << "I.I.I" << "\033[0m" << endl;
std::cout << "                        "  << "(- O)"  << endl;
std::cout << "____________________" <<  "ooO--(_)--Ooo" << "____________________\n";
std::cout << "\033[5;1m" << "";
std::cout << "   8P     dP" << "\033[0m" << " ::::|+{Avi 2 DVD Toy}.|::::\n";
std::cout << "\033[5;1m" << "   88   .d8'\n";              
std::cout << "   88aaa8P'  dP    dP 88d888b. .d8888b. .d8888b. \n";
std::cout << "   88   `8b. 88    88 88'  `88 Y8ooooo. 88ooood8 \n";
std::cout << "   88     88 88.  .88 88             88 88.  ... \n";
std::cout << "   8P     dP `88888P' dP       `88888P' `88888P' \n" << "\033[0m";
std::cout << "____________________________________________________\n";
std::cout << "\033[32;40m" << "1) Press 1 to convert an avi to DVD" << endl;
std::cout << "2) Press 2 to burn to DVD" << endl << "3) Press 3 for setup info" << endl << "0) Press 0 to exit\n4) OMG MY EYESSS\n" << "\033[0m";
std::cout << "\n\n\n\nChoose " << "\033[5;1m" << "--> " << "\033[0m" ;
std::cin >> f;
```

There's a few examples of how to do that without including a lib.

---

### Post by |{urse on 2012-06-25
Here, you'll need this too.

[http://www.cplusplus.com/forum/unices/36461/](http://www.cplusplus.com/forum/unices/36461/)

---

### Post by Simian Man on 2012-06-25
You can also use the Ncurses library which also allows you to do more things like reuse portions of the screen and have text-based buttons and things.

---

### Post by xXNinjaTurtleXx on 2012-06-26
Thanks guys! I've used the "\033..." method :)

---

### Post by |{urse on 2012-06-26
Make sure and mark this issue solved in the thread tools menu at the top of the page. Happy coding!

---

