---
title: "HELP please"
date: 2010-05-08
forum: Programming Talk
---

### Post by Quashie on 2010-05-08
I created code using vi editor
then try to execute using ./file.cpp i got error message said
./file.cpp: 1: //: Permission denied
./file.cpp: 3: Syntax error: "(" unexpected

someone please help me. I really appreciate
thanks

---

### Post by KdotJ on 2010-05-08
So I'm assuming this is a C++ file you've coded?
Well before you can execute it, you need to compile it. IF you have the g++ compiler installed you can compile the file by navigating to the directory where the file is and typing:

```
g++ file.cpp
```

IF then, it returns with no errors you can execute it. If you used the code as I've written above, you can run it by typing:

```
./a.out
```


However, if you do not have g++ installed (and you will be told if you don't when you run the first of above commands, then you can installed it by typing:

```
sudo apt-get install g++
```

Hope this helps.

---

### Post by Tony Flury on 2010-05-09
Also make sure that you install build-essential too - as that contains a load of essential libraries 
```

sudo apt-get install build-essential

```

---

### Post by Quashie on 2010-05-09
It is still so many error.

I am beginner here. I really need help with this. This is for my class and I using example from my book which is simple script. We are not using it in the class yet. Probably next week. But, I try at my laptop running Ubuntu OS. 

Assuming this is my script :
// My first C++ program
#include <iostream>
int main()
{
 std::cout << "Hi there!" << std::endl";
 std::cout << "This is my first C++ program" << std::endl";
 return(0);
}
$_

When I open terminal, I type sh return.
Then using vi editor to write the script.
After that, I use g++ first.cpp, but it showed so many error there.

I already instaledl which you guys told me.

Any help will be very very appreciate.

---

### Post by MadCow108 on 2010-05-09
you don't have to type sh when opening a terminal, that will only drop you into a less capable shell (dash on ubuntu) from the shell used by default (bash on ubuntu)

the problem with your file are the trailing ":
endl**"**;
remove these

in future please include the error messages and put your code in [code] tags for better formating

---

### Post by Quashie on 2010-05-09
> **MadCow108 said:**
> you don't have to type sh when opening a terminal, that will only drop you into a less capable shell (dash on ubuntu) from the shell used by default (bash on ubuntu)

the problem with your file are the trailing ":
endl**"**;
remove these

in future please include the error messages and put your code in [code] tags for better formating


Those are the screenshot with error message and the script that i wrote.

---

### Post by lisati on 2010-05-09
> **Quashie said:**
> 
// My first C++ program
#include <iostream>
int main()
{
 std::cout << "Hi there!" << std::endl[COLOR="Red"]"[/COLOR];
 std::cout << "This is my first C++ program" << std::endl[COLOR="Red"]"[/COLOR];
 return(0);
}


As has already been pointed out, you have extra quote marks at the end of two of your lines. I've highlighted it in red. Remove them and you should be fine.

---

### Post by Quashie on 2010-05-09
> **lisati said:**
> As has already been pointed out, you have extra quote marks at the end of two of your lines. I've highlighted it in red. Remove them and you should be fine.
I modified it. How to see the result after I execute?
I type g++ first.cpp then it nothing come out. As you can see the screen shot.

Thank you for your help. I am really appreciate.

---

### Post by MadCow108 on 2010-05-09
that means it worked.
by default gcc creates an executable named a.out
execute it with ./a.out (the ./ means current folder)

you can change the name by adding a -o exeutable_name to g++

best is you go over some of the guides listed in the stickies

---

### Post by Quashie on 2010-05-09
yeah that's work.

Thank you for everybody. :)

---

### Post by Quashie on 2010-05-16
I am running bash shell on ubuntu. Is it possible to change it to bourne shell?

1. I know how to display current process by typing ps -e. And how to display specific user to display only those user processes? getting stuck with this.

2. who command to show current users. How to display user Ids only? is that who -q command line? and how to display an alphabetized list of the users currently on the system?

Thanks for reading and helping me.

All answers are very appreciate.

---

### Post by trent.josephsen on 2010-05-16
To run the Bourne shell (well, a very close POSIX-compliant approximation):  Type sh.

1.  man ps

2.  man who

---

