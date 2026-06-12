---
title: "changing ownership to create files"
date: 2009-12-21
forum: Programming Talk
---

### Post by kwyto on 2009-12-21
i'm trying to create a text file in a C program, but the system it's not letting me do it. if i create the file, then once the ./a.out is created then the file is fill with the data i wanted it to generated. i know it has to do something with **chown** or **chmod**.  thank you in advance.

---

### Post by doas777 on 2009-12-21
well, what are the permissions/ownership on the folder?
run 
```
ls -al <path>
```to see them. all you should have to do is change the owner on the folder.

```
sudo chown <user>:<usergroup> <path>
```

---

### Post by kwyto on 2009-12-21
i'm compiling the program in the Desktop folder. do you recommend to create a folder just for programming? for security purposes? thank you for the code

---

### Post by Zugzwang on 2009-12-21
Your problem description is a little bit hard to understand. Are you saying that your "a.out" program file is overwritten with the text file? Is it possible that this only happened after you ran the program? In this case, note that the first argument given to the "main" function of your C program is the location of the program itself. Your parameters begin in the second slot of the array given. 

For example, if you have "int main(int argc, char** argv)", then "argv[0]" will point to a string telling your program from "where it was loaded". If you give a file name as parameter, search for it in "argv[1]" and let your program check that there are indeed so many parameters given.

---

### Post by kwyto on 2009-12-21
i'm sorry, but no. i'm writing a simple C program that generates some data in a text file and does some stuff with it. the folder's ownership wouldn't let me create the file, but it would create the ./a.out. now, if i were to open gedit and create a blank text file and save it, then when i were to compile the program the text file would have the data inside. that's why i knew it had to do with chown but I didn't know how to mess with that. i'm kind of new to linux

---

### Post by dwhitney67 on 2009-12-21
Open a terminal, go to the folder where your code is at.  Run this command, and verify that you have write-permissions within the folder:
```

ls -ld

```

Also, post the code that you have written which creates the file.

---

### Post by kwyto on 2009-12-21
> **doas777 said:**
> well, what are the permissions/ownership on the folder?
run 
```
ls -al <path>
```to see them. all you should have to do is change the owner on the folder.

```
sudo chown <user>:<usergroup> <path>
```

i tried this and didn't work. i went and change the permissions of the folder, but the file is not created 

here is the code:
#include <fstream>
#include <iostream>
#include <stdlib.h>

using namespace std;

void GenerateFile(fstream &File)
{
    srand(time(0));
    int number;
    
    for(int i=0; i<5; i++)
    {
        for(int j=0; j<5; j++)
        {
            number=rand()%100+1;
            File << number << "  ";
        }
        File << "\n";
    }
}

int main()
{

    fstream File("Numbers.txt");
     if(!File.is_open()) 
    {
        cout<<"error";
        exit(0);
    }    
     GenerateFile(File);
    File.close();
    
    
    return 0;
}

---

### Post by Arndt on 2009-12-22
> **kwyto said:**
> i tried this and didn't work. i went and change the permissions of the folder, but the file is not created 

here is the code:
#include <fstream>
#include <iostream>
#include <stdlib.h>

using namespace std;

void GenerateFile(fstream &File)
{
    srand(time(0));
    int number;
    
    for(int i=0; i<5; i++)
    {
        for(int j=0; j<5; j++)
        {
            number=rand()%100+1;
            File << number << "  ";
        }
        File << "\n";
    }
}

int main()
{

    fstream File("Numbers.txt");
     if(!File.is_open()) 
    {
        cout<<"error";
        exit(0);
    }    
     GenerateFile(File);
    File.close();
    
    
    return 0;
}

You are opening the file, but the default is to open it for reading. To open it for writing, use this:

fstream File("Numbers.txt", ios_base::out);

I see that the childish forum makes the two colons above into a smiley. Well, it's two colons.

---

### Post by Hellkeepa on 2009-12-22
HELLo!
> **Arndt said:**
> I see that the childish forum makes the two colons above into a smiley. Well, it's two colons.

Fixed it for you:
```
fstream File("Numbers.txt", ios_base::out);
```
That's why I always use code-tags around code. ;-)

Happy codin'!

---

### Post by kwyto on 2009-12-22
thank you guys, help much appreciated

---

