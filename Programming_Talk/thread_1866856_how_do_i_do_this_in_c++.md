---
title: "how do i do this in c++"
date: 2011-10-22
forum: Programming Talk
---

### Post by crimscx on 2011-10-22
when i make a program like this..

#include <iostream>
using namespace std;

int main()
{
         cout << "blah blah blah" << endl;
         return 0;
}

and i compile it..it gives me this executable file on the desktop, how do i make it to where when i double click it, my text pops up in the terminal without having to go through in the terminal go to its location and type ./nameofthefile and in the compiled programs properties it IS set to executable soo i don't know why it wont open when i double click it..

---

### Post by lisati on 2011-10-22
There are multiple ways of doing this. One way is to copy the executable file to your Desktop folder.

---

### Post by crimscx on 2011-10-22
real funny im serious, when i double click it wont open it can only be opened via terminal

---

### Post by gsmanners on 2011-10-22
You do realize that that code is something that outputs to stdout, which you can generally only get in terminal, right?

---

### Post by lisati on 2011-10-22
> **crimscx said:**
> real funny im serious, when i double click it wont open it can only be opened via terminal

Real funny. The answer I gave WORKS. Are you really serious, or are you using us as a homework service?

---

### Post by crimscx on 2011-10-22
you do realize if im asking a question like this im obviously new to c++ so can you try to explain a little better please, sorry for being rude but dang. i hate useless comments

---

### Post by lisati on 2011-10-22
It sounds like you want to learn about developing a user interface. Are you new to programming?

---

### Post by gsmanners on 2011-10-22
Sounds to me like more of a desktop management issue than a coding one. You can create a launcher, right?

---

### Post by crimscx on 2011-10-22
user interface to show my text would be very nice and i thought my compiled file was "the launcher"

---

### Post by gsmanners on 2011-10-22
> **crimscx said:**
> user interface to show my text would be very nice and i thought my compiled file was "the launcher"

Interesting. No, there's this separation between applications and their launcher elements in all graphical user interfaces since the advent of window managers.

---

### Post by crimscx on 2011-10-22
k i guess how do i create a launcher?

---

### Post by gsmanners on 2011-10-22
That depends. What type of desktop are you using?

EDIT: In case you're using Xfce or some other standards-compliant desktop, you can simply create a .desktop file for your app and put that into your ~/Desktop folder. Here's an example:

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Blah
Comment=
Exec=/home/gsmanners/bin/blah
Icon=
Path=
Terminal=true
StartupNotify=true
```

The above creates an icon called "Blah" on the desktop to run an app in my bin folder called "blah."

Here's the source for blah:

```
#include <iostream>
#include <string>
using namespace std;

int main()
{
   cout << "Hello, world!\n";
   string s;
   cin >> s;
}
```

If you run this, you get terminal output and you'll need to hit Ctrl-C to exit. :D

See how easy that is?

---

