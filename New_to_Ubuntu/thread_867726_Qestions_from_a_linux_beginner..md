---
title: "Qestions from a linux beginner."
date: 2008-07-23
forum: New to Ubuntu
---

### Post by IloveTux on 2008-07-23
Hello, i need some help regarding two problems. Please excuse me if this questions are stupid but i`m a beginner. I have just installed ubuntu 8.04 and i`m very happy because i did that all by myself. The drivers are working fine except for the video card. When i installed it( i have a nvidia fx5200 and an old horizon 17" monitor) it asks me for a restart. I restart the system and when it loads to the password screen it goes black and display`s the message"OUT OF RANGE-Horizon"). I don`t know if others had the same problem but i don`t know what to do. Can you give me some advices? :)
The second problem is that i want to learn the c language. I know the basic of it but i need a compiler for ubuntu. Can someone tell me what and where to get one?

Thanks very much! MY machine runs very nice now with ubuntu. Thank you so much, and many thanks to the developers. I wish you all the best!:)

---

### Post by Buffalo Soldier on 2008-07-23
Welcome to Ubuntu and the GNU/Linux world :)

I'm afraid I cannot help much on the first part. Maybe others who have experience with NVIDIA card will give you a hand.

The second part, what you need is the build-essential metapackage. It's basically a collection of all the most used compilers. If you're comfortable with the command line, here's how to install it.

```
sudo apt-get install build-essential
```

More information on [compilers in Ubuntu]("https://help.ubuntu.com/community/InstallingCompilers")

---

### Post by Bachstelze on 2008-07-23
> **IloveTux said:**
> When i installed it( i have a nvidia fx5200 and an old horizon 17" monitor) it asks me for a restart. I restart the system and when it loads to the password screen it goes black and display`s the message"OUT OF RANGE-Horizon"). I don`t know if others had the same problem but i don`t know what to do. Can you give me some advices? :)

You can press Ctrl+Alt+F2 to go to a terminal. Then you can login, and run the following command to revert to a default Xorg configuration :

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

> **Buffalo Soldier said:**
> 
The second part, what you need is the build-essential metapackage. It's basically a collection of all the most used compilers.


To be precise, it is two compilers (gcc for C and g++ for C++), plus all the other tools usually required to compile software (preprocessor, standard libraries, make, etc.). So in short, yess, this is what you need if you want to do C/C++ in Ubuntu.

---

### Post by IloveTux on 2008-07-23
Thanks Buffalo Soldier. I will try, i managed to install vlc and amarok. Hurrayyyyyyyyyyy! But i`m a bit rusty in the terminal. I don`t know a lot of things. I must read on the forum and search for tutorials. :)
That`s ok, maybe others can help. Thanks anyway! :KS

---

### Post by IloveTux on 2008-07-23
I installed build essentials, now how can i make a source file and compile it? Again, i`m very sorry if this questions have been asked before. Please don`t me mad at me.
Next time i will search before posting but i need to fix the problem with my video card and compiler very fast! :)

---

### Post by Bachstelze on 2008-07-23
> **IloveTux said:**
> I installed build essentials, now how can i make a source file and compile it? Again, i`m very sorry if this questions have been asked before. Please don`t me mad at me.
Next time i will search before posting but i need to fix the problem with my video card and compiler very fast! :)

You can make a source file in whichever text editor you like, it should look like this:

```

#include <stdio.h>

int main(void)
{
    printf("Hello, world!\n");
    return 0;
}

```

you save it as e.g. helloworld.c, and compile it with

```
gcc helloworld.c -o helloworld
```

An executable called helloworld will be created in the current directory, and you can run it with

```
./helloworld
```



That's basically how it works. Of course, a complete C training is well outside the scope of this thread, there are plenty of online resources for that.

---

### Post by Troll_the_Great on 2008-07-23
I think the problem with your monitor is age.The monitor doesn't support the resolution or the refresh rate of the video adapter and this is why you get the "Out of range" message.
To install the Nvidia drivers try EnvyNG, is a program that search for drivers and installs them.Open a terminal and type:
```
sudo apt-get install envyng-gtk
```
After you installed it you can find it under Applications-System Tools-EnvyNG.
This program installs the nvidia-settings too, you can find those under System-Administration-NVIDIA X Server Settings, and can configure your Nvidia adapter from there.
Welcome to the linux world!
Cheers!

PS:You said you were a virgin to linux.Here you don't need condoms, there are no viruses...:lolflag:

---

### Post by IloveTux on 2008-07-23
Thanks very much people! :) Thanks for the help!

---

### Post by IloveTux on 2008-07-23
I typed that code in the terminal and :
sudo apt-get install envyng-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  envyng-gtk: Depends: envyng-core (>= 1.1.0) but it is not going to be installed
  skype: Depends: libqt4-core (>= 4.2.1) but it is not going to be installed
         Depends: libqt4-gui (>= 4.2.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by Troll_the_Great on 2008-07-23
Try with 
```
sudo aptitude install envyng-gtk
```

---

### Post by IloveTux on 2008-07-23
Thanks

---

### Post by realdude19 on 2010-07-01
I am going Crazy trying to use EnvyNG... How do you install it in Ubuntu 10.04

And Am I going to get in trouble for rezzing a dead thread? lol

Here is what I am getting:

```

luke@BlueShift:~$ sudo aptitude install envyng-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  envyng-core envyng-gtk 
0 packages upgraded, 2 newly installed, 0 to remove and 64 not upgraded.
Need to get 236kB of archives. After unpacking 1,303kB will be used.
The following packages have unmet dependencies:
  envyng-core: Depends: python (< 2.6) but 2.6.5-0ubuntu1 is installed.
  envyng-gtk: Depends: python (< 2.6) but 2.6.5-0ubuntu1 is installed.
Unable to resolve dependencies!  Giving up...
The following packages are BROKEN:
  envyng-core envyng-gtk 
0 packages upgraded, 2 newly installed, 0 to remove and 64 not upgraded.
Need to get 236kB of archives. After unpacking 1,303kB will be used.
aptitude failed to find a solution to these dependencies.  You can solve them yourself by hand or type 'n' to quit.
The following packages have unmet dependencies:
  envyng-core: Depends: python (< 2.6) but 2.6.5-0ubuntu1 is installed.
  envyng-gtk: Depends: python (< 2.6) but 2.6.5-0ubuntu1 is installed.
Resolve these dependencies by hand? [N/+/-/_/:/?]

```

Is there no way to get this for 10.04?


[COLOR="Red"]EDIT! I Just found this! "Envy is no longer supported starting from Ubuntu 10.04. Please use Jockey instead."[/COLOR]

---

### Post by afrodeity on 2010-07-21
I have a similar problem trying to install unknown-horizons game

```

install unknown-horizons
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages are BROKEN:
  python-fife 
The following NEW packages will be installed:
  libguichan-0.8.1-1{a} libguichan-opengl-0.8.1-1{a} 
  libguichan-sdl-0.8.1-1{a} unknown-horizons 
0 packages upgraded, 5 newly installed, 0 to remove and 93 not upgraded.
Need to get 34.1MB of archives. After unpacking 50.1MB will be used.
The following packages have unmet dependencies:
  python-fife: Depends: python (< 2.6) but 2.6.5-0ubuntu1 is installed.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
python-fife [Not Installed]
unknown-horizons [Not Installed]

Score is -9868

```

---

