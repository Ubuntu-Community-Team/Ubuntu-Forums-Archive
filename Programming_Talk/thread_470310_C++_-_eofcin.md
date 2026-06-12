---
title: "C++ - eof/cin"
date: 2007-06-10
forum: Programming Talk
---

### Post by spamalot on 2007-06-10
hi,

1)
how to i tell cin it's eof .e.g 

while(cin>>s) ... 

typing Ctrl-D + Enter does not work within cdt/eclipse.

2) how do i launch an exe made with eclipse from a terminal?

3) is this the right place to post this?

thanks!!

---

### Post by PandaGoat on 2007-06-11
1) I'm assuming you are using istream [input stream].

```

istream cin("somefile.txt");

while(!cin.eof())
{

}


```

2) Figure out where your projects folder is [likely in /home/user].  Find the binary that eclipse made.  Drag it over the terminal and hit enter.

3) I believe so.

---

### Post by spamalot on 2007-06-11
Thanks PandaGoat!

1) in fact, i meant standard input (keyboard), i just can't get the program to stop with Ctrl-D+Enter e.g.

#include <iostream>
#include <string>


int main()
{

    std::string s;
    while (std::cin >> s) //what i type shows in the console, but Ctrl-D+Enter is not recognized as eof 
    ...

}

2) nice! in fact i also found another way: 

$cd relevant directory
$./name

---

### Post by bboozzoo on 2007-06-12
the problem with your input is that only a single string will be extracted, if you input more data separated by spaces, this is likely to extract only the first chunk. more reliable is to use getline
```

#include <iostream>
#include <string>
using namespace std;
int main() {
        string s;
        while (getline(cin, s)) {
                std::cout << "got: " << s << std::endl;
        }
        return 0;
}

```
this way you get both ctrl+d (EOF) and fetch whole line of input, what can easily be parsed later

---

### Post by spamalot on 2007-06-12
thanks bboozzoo!

you're right, getline is probably a better choice.

after a bit of experimentation, the problem i describe, either with cin>s or getline does Not occur if i run the program from the terminal, but it's still there if i run it from the sdk (eclipe)...

---

### Post by samjh on 2007-06-12
> **spamalot said:**
> after a bit of experimentation, the problem i describe, either with cin>s or getline does Not occur if i run the program from the terminal, but it's still there if i run it from the sdk (eclipe)...

That's just the way Eclipse handles console input.  Other terminal emulations display similar behaviour - some keys or key combinations don't work.  Stick to using ordinary terminal.

---

