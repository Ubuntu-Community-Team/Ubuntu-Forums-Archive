---
title: "Installing g++ on kubuntu"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by ItecKid on 2008-09-27
I got the g++ C++ compiler off of the Synaptic Package Manager, however when I try to install it, it gives me an error message that says "Dependency is not satisfiable: gcc-4.0-base."

I'm completely new to linux, so I have no idea how to fix this.

Thanks for any help you can provide.

---

### Post by kjohansen on 2008-09-27
you should just 
```

sudo apt-get install g++

```
and this will install all dependencies.

---

### Post by Iowan on 2008-09-27
The usual recommendation for installing compiler is to install **build-essential** - more info [here]("http://ubuntuforums.org/showthread.php?t=931148").

---

### Post by ItecKid on 2008-09-27
So this is another newbie question, but how to run the program after installation?  I tried 
```
./build-essential
```
in terminal, but it said 'no such file or directory'.  Same thing with g++. 

Furthermore, is there a way to update my menus in applications so they will launch the programs?  I tried
```
sudo update-menus
``` 
but the terminal said it was an invalid command.  Or rather, it said, command not found.

Thank you for any help you can provide.

---

### Post by Xiong Chiamiov on 2008-09-27
Build-essential is a package, not a program, so you can't run it directly.  If you tell us what you're trying to do, we can help you with that, rather than an issue that you may not even need to be dealing with.

And you need to install the "menu" package for update-menus to work.

---

### Post by ItecKid on 2008-09-28
Basically, all I'm trying to do is get a working C++ compiler on the system.

I also attempted to use kDevelop, though that seems to have some problems with both C and C++.

My C++ program is as follows:
```
#include <iostream>
using namespace std;
int main ()
{
cout << "Hello, World!" << endl;
return 0;
}
```
When attempted to compile using the command
```
cc helloworld.cpp
```
The compiler prints unfriendly messages.  I have also tried using void main () with no return value; this also does not work.

The C program compiles correctly, though the compiler seems to dislike the \n (newline) command.  What's up with that?

By the way, both of these programs were compiled using vi (not emacs).

---

### Post by andrescostelo on 2009-04-23
Hello to all. In regard to the matter of installing c++ compilers on Kubuntu I have a problem and I hope you can help me. Here's what happening, whenever I try to type:

1: sudo apt-get install g++
2: sudo apt-get install build-essential
3: sudo apt-get install python

In all cases I get the following message:

E: No se pudo bloquear /var/lib/dpkg/lock - open (11 Recurso temporalmente no disponible)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

When I look for the "lock" file on the specified location I see that it is impossible to open the file using the editor. This files is a 0 Bytes file... Any idea what's going on???

P.S.: I'm completely new to Linux...

---

### Post by Dougie187 on 2009-04-23
Do you have synaptic open when you are doing this?

---

### Post by adamitj on 2009-04-23
apt-get, aptitude, Synaptic and Update Manager all uses package administration and can run only one at once.

Tip: just installing build-essential installs g++.

---

### Post by jowilkin on 2009-04-23
Try closing all programs except the terminal and then using the command "sudo aptitude install build-essential".

---

### Post by vkotian on 2009-05-04
> **kjohansen said:**
> you should just 
```

sudo apt-get install g++

```
and this will install all dependencies.

This did work for me. thanks. I tried to compile gcc with g++. But that got stopped because of the following error. 
'checking for i686-pc-linux-gnu-gcc...cannot create object files.'. These are not exact words. 
I checked this directory which had just configure.status, configure.cache files. Any clues.
But...I did not have to compile form scratch.
as su, apt-get install g++ worked. I did have to get it from installation cd. 'apt-get add cdrom' i guess,I used for adding cdrom path. http universal locations are not working for me.'Error http... not found ip...'. Any clues on this?

---

