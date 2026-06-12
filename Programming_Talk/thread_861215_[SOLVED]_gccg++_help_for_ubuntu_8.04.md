---
title: "[SOLVED] gcc/g++ help for ubuntu 8.04"
date: 2008-07-16
forum: Programming Talk
---

### Post by AceDip on 2008-07-16
well i am trying hard to shift to linux completely{dont like microsoft)but this one problem is a big hinderence.
well now, i made a simple cpp file as

```
#include<iostream>
using namespace std;
int main() {
cout<<"hello";
}
```

and when i compile it as
```
gcc <filename>
```
its gives following output```
Bash:Syntax error unexpected token 'newline'
``` 
and on running the file as
```
./a.out
``` it gives this ```
no such file or directory
``` 
and in the package manager i have gcc already installed but g++ is not there but i guess isnt gcc enough?
well anyways kindly help so that i can do cpp again.

---

### Post by era86 on 2008-07-16
First, make sure you return an int.  What is the file named?  What are you typing exactly on the cl?

---

### Post by Bachstelze on 2008-07-16
Install *build-essential*.

---

### Post by elmoosecapitan on 2008-07-16
I also want to emphasize adding the line:

return 0;

right before you end you main function.

Also, it might help (sometimes) to include the file path, i.e. ~/Desktop/filename.cpp or /home/username/Desktop/filename.cpp

---

### Post by AceDip on 2008-07-16
returning this int isnt a trouble,ISO C++ supports it.
My file name is new.cpp
and i'm typing
gcc <new>
then 
./a.out

---

### Post by Tony Flury on 2008-07-16
not returning an Int would not give a bash script error - it might give a compiler warning, but i am not sure that gcc or g++ is that strict.

Make sure you install the build-essentials package

```

sudo apt-get install build-essential

```

As era says though - provide us with all the command lines you enter - and the exact output.

And finally - when you are including code or cli output in posts on this forum - make sure that you use the code tags - it preserves the formatting and makes it easier to read.

---

### Post by Tony Flury on 2008-07-16
> **AceDip said:**
> returning this int isnt a trouble,ISO C++ supports it.
My file name is new.cpp
and i'm typing
gcc <new>
then 
./a.out

Trying the command :
```

g++ new.cpp -o a.out

```
to compile your code, and not what you have (actually -o a.out is superfluous but i think it is a good habit to explicitly name the output executable)

I think the gcc command line is getting confused with you using <new>, as it will look like you are piping input and output ...

---

### Post by sujoy on 2008-07-16
for compiling cpp with gcc you need to add the libstdc lib.

its something like, gcc -o name name.cpp -libstdc

or better use g++

---

### Post by AceDip on 2008-07-16
When i type```
gcc new.cpp
```
its gives following output
```
gcc:error trying to exec 'cclplus': execvp: No such file or directory 
```
and even if i type 
```
gcc new.cpp -o a.out
```
it gives the same above output

---

### Post by Tony Flury on 2008-07-16
did you install build-essentials - and the compiler : 
```

sudo apt-get install build-essential
sudo apt-get install g++

```

one positive thing from all of this  : at least now you are getting some form of compiler error - and not a scripting error - so you have made a step forward.

---

### Post by AceDip on 2008-07-16
ya true step forward is definitely a conclusion.
gcc is already there in my package manager and when i select it, it asks me to either remove it or remove all.
so that seems its already there and one thing more, when i write
```
gcc
```
it gives output
```
no input file
```
and it asks for the package builder when i type g++ instead

---

### Post by appi2012 on 2008-07-16
I don't know why this should make a difference, but I use the extension .C rather than .cpp. Just a thought;)

---

### Post by Tony Flury on 2008-07-16
> **AceDip said:**
> ya true step forward is definitely a conclusion.
gcc is already there in my package manager and when i select it, it asks me to either remove it or remove all.
so that seems its already there and one thing more, when i write
```
gcc
```
it gives output
```
no input file
```
and it asks for the package builder when i type g++ instead

gcc is a general compiler - it will do a lot more than just c (or c++) so just having the gcc command installed does not mean you have a c or c++ compiler.

did you install the g++ package with the apt-get instruction i gave you ?

---

### Post by AceDip on 2008-07-16
i do not have g++ in the package manager

---

### Post by elmoosecapitan on 2008-07-16
You should be able to download g++ via a terminal using the sudo apt-get command. Typing in 

```
g++
``` 

will give you instructions for installing with a terminal. Then type

```
$ g++ ./new.cpp
$ ./a.out

```


To answer you question, using '.C' does make a slight difference when trying to compile. I generally try to stay with '.cpp'.

cheers

---

### Post by AceDip on 2008-07-16
running the apt-get instruction,gives
```
0 installed 0 removes 0 upgraded
```
in short it cant find g++ package or rather i think its not there.
but gcc is there in the package manager and installed.as i told u asks for its removal when i click on it there and for its installation.

---

### Post by AceDip on 2008-07-16
here another problem arises.My internet is working from windows not ununtu,by phone vendor does support the phone cable which is connected to my    
comp.so i'm on windows now.

---

### Post by Tony Flury on 2008-07-16
which sources do you have enabled (give us the contents of your /etc/apt/source.lst file) - it is very odd that you don't have the g++ package available

does the apt-get say that g++ is not available or does it say it is already installed - on my system : 

```

sudo apt-get install g++

Reading package lists... Done
Building dependency tree       
Reading state information... Done
g++ is already the newest version.
g++ set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

As you can see the last line is similar to yours - but the key line is : 
```

g++ is already the newest version.

```

As has already been mentioned - it is a good idea to copy and paste all the output into any reply - often the last line is a summary - and the error is somewhat earlier

---

### Post by DGortze380 on 2008-07-16
just use g++.
You're problem appears to be a syntax error in typing the command.

for example.
my source file is call: howToCompile.cpp
and is located in /home/user

```

g++ /home/user/howToCompile.cpp -o howToCompile

```

As far as the internet issue, that is the reason apt-get is not working.

---

### Post by AceDip on 2008-07-16
> **Tony Flury said:**
> did you install build-essentials - and the compiler : 
```

sudo apt-get install build-essential
sudo apt-get install g++

```

one positive thing from all of this  : at least now you are getting some form of compiler error - and not a scripting error - so you have made a step forward.

i typed these instructions and following was the output
```
sudo apt-get install build essential

Reading package list...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package build
```

and the next command

```
sudo apt-get install g++

Reading package list...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package g
```

but this one gave some anticipated output,which you can comprehend

```
sudo apt-get install gcc

Reading package list...Done
Building dependency tree
Reading state information...Done
gcc is already the newest version.
0 upgraded,0 newly installed,0 to remove and 0 not upgraded.
```

---

### Post by AceDip on 2008-07-17
> **Tony Flury said:**
> did you install build-essentials - and the compiler : 
```

sudo apt-get install build-essential
sudo apt-get install g++

```

one positive thing from all of this  : at least now you are getting some form of compiler error - and not a scripting error - so you have made a step forward.

i typed these instructions and following was the output
```
sudo apt-get install build essential

Reading package list...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package build
```

and the next command

```
sudo apt-get install g++

Reading package list...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package g
```

but this one gave some anticipated output,which you can comprehend

```
sudo apt-get install gcc

Reading package list...Done
Building dependency tree
Reading state information...Done
gcc is already the newest version.
0 upgraded,0 newly installed,0 to remove and 0 not upgraded.
```

---

### Post by era86 on 2008-07-17
Should be "sudo apt-get install build-essential" with the dash.

---

### Post by Tony Flury on 2008-07-17
> **AceDip said:**
> i typed these instructions and following was the output
```
sudo apt-get install build essential

Reading package list...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package build
```

and the next command

```
sudo apt-get install g++

Reading package list...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package g
```

but this one gave some anticipated output,which you can comprehend

```
sudo apt-get install gcc

Reading package list...Done
Building dependency tree
Reading state information...Done
gcc is already the newest version.
0 upgraded,0 newly installed,0 to remove and 0 not upgraded.
```

As i pointed out gcc is only part of the compiler, you need the g++ module as well. I can only assume that the shell that you use misunderstood the '+' sign on the command line - which is odd : Try this instead : 

```

sudo apt-get install "g++"

```

also as era pointed out - you should be using build-essential - i had included the "-" in my posts (copy and paste is your friend).

---

### Post by AceDip on 2008-07-17
hey Tony and Era.i tried as u guys said and this how it comes
```
sudo apt-get install build-essential

Reading package list...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package build-essential
```

and 

```
sudo apt-get install "g++"

Reading package list...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package g
```

so wat does this mean man...

---

### Post by era86 on 2008-07-17
I would look into your sources.list file for proper repositories.  Just do a gedit on /usr/apt/sources.list and show us the contents of that file.

---

### Post by AceDip on 2008-07-17
hey Tony and Era.i tried as u guys said and this how it comes
```
sudo apt-get install build-essential

Reading package list...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package build-essential
```

and 

```
sudo apt-get install "g++"

Reading package list...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package g
```

so wat does this mean man...

---

### Post by Dougie187 on 2008-07-17
Did you try to type
```
sudo apt-get update
```
before you did the two installs?

Exact Code:
```

sudo apt-get update
sudo apt-get install build-essential

```

---

### Post by AceDip on 2008-07-17
> **era86 said:**
> I would look into your sources.list file for proper repositories.  Just do a gedit on /usr/apt/sources.list and show us the contents of that file.
look i'm not very familiar with wat u are talking about..can u please tell me wat exact code do i have to write there..

---

### Post by DGortze380 on 2008-07-17
> **AceDip said:**
> look i'm not very familiar with wat u are talking about..can u please tell me wat exact code do i have to write there..

Open a terminal (accessories>terminal) and copy and paste the output of:


```

cat /usr/apt/sources.list

```

---

### Post by Tony Flury on 2008-07-17
ok - what shell are you running ? do the following command and post the results : 

```

echo $SHELL

```

The commands i have provided work in the bash shell.

Alternatively - do you not have the Synaptic Package Manager installed on your System ? It normally resides under the System -> Administration menu. the g++ package should be there.

---

### Post by Dougie187 on 2008-07-17
rather then looking for G++ specifically look for build-essential. that should have g++ in it.

---

### Post by AceDip on 2008-07-17
> **Tony Flury said:**
> ok - what shell are you running ? do the following command and post the results : 

```

echo $SHELL

```

The commands i have provided work in the bash shell.

Alternatively - do you not have the Synaptic Package Manager installed on your System ? It normally resides under the System -> Administration menu. the g++ package should be there.
I have checked the Synaptic Package Manager,its showing a list a packages..i guess the package manager is installed??
and g++ is not there while gcc is.

---

### Post by Dougie187 on 2008-07-17
You should try some of the other suggestions in this post.

---

### Post by johnnybravo666 on 2008-07-17
This has already been mentioned but post the results of this command

```
cat /etc/apt/sources.list
```

---

### Post by AceDip on 2008-07-17
> **Tony Flury said:**
> ok - what shell are you running ? do the following command and post the results : 

```

echo $SHELL

```

The commands i have provided work in the bash shell.

Alternatively - do you not have the Synaptic Package Manager installed on your System ? It normally resides under the System -> Administration menu. the g++ package should be there.

```
echo $SHELL


/bin/bash
```

as i have mentioned package manager is showing the list of packages..so i guess the package manager is installed.it is not showing g++.

---

### Post by AceDip on 2008-07-17
> **johnnybravo666 said:**
> This has already been mentioned but post the results of this command

```
cat /etc/apt/sources.list
```

```
/etc/apt/sources.list

bash: /etc/apt/sources.list: Permission denied
```

---

### Post by DGortze380 on 2008-07-17
did you remember the cat command?

try 

```

sudo cat /etc/apt/sources.list

```

although I don't think you should need sudo.

---

### Post by Natr0n on 2008-07-17
> **AceDip said:**
> here another problem arises.My internet is working from windows not ununtu,by phone vendor does support the phone cable which is connected to my    
comp.so i'm on windows now.
If you still haven't fixed this you're not going to be able to use apt-get or the package manager to install anything. You need to fix your internet connection first, then do ```
sudo apt-get install build-essential

```

---

### Post by AceDip on 2008-07-17
> **johnnybravo666 said:**
> This has already been mentioned but post the results of this command

```
cat /etc/apt/sources.list
```

here is it

```
cat /etc/apt/sources.list


#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted 
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to 
# newer versions of the distribution. 

deb http://in.archive.ubuntu.com/ubuntu/ hardy main restricted 
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy main restricted 

## Major bug fix updates produced after the final release of the 
## distribution. 
deb http://in.archive.ubuntu.com/ubuntu/ hardy-updates main restricted 
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## universe WILL NOT receive any review or updates from the Ubuntu security 
## team. 
deb http://in.archive.ubuntu.com/ubuntu/ hardy universe 
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy universe 
deb http://in.archive.ubuntu.com/ubuntu/ hardy-updates universe 
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
deb http://in.archive.ubuntu.com/ubuntu/ hardy multiverse 
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy multiverse 
deb http://in.archive.ubuntu.com/ubuntu/ hardy-updates multiverse 
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-updates multiverse 

## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
# deb http://in.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse 
# deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse 

## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu 
## users. 
# deb http://archive.canonical.com/ubuntu hardy partner 
# deb-src http://archive.canonical.com/ubuntu hardy partner 

deb http://security.ubuntu.com/ubuntu hardy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted 
deb http://security.ubuntu.com/ubuntu hardy-security universe 
deb-src http://security.ubuntu.com/ubuntu hardy-security universe 
deb http://security.ubuntu.com/ubuntu hardy-security multiverse 
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse 
ani@WhiteRat:~$ clear 

ani@WhiteRat:~$ cat /etc/apt/sources.list 
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted 
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to 
# newer versions of the distribution. 

deb http://in.archive.ubuntu.com/ubuntu/ hardy main restricted 
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy main restricted 

## Major bug fix updates produced after the final release of the 
## distribution. 
deb http://in.archive.ubuntu.com/ubuntu/ hardy-updates main restricted 
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## universe WILL NOT receive any review or updates from the Ubuntu security 
## team. 
deb http://in.archive.ubuntu.com/ubuntu/ hardy universe 
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy universe 
deb http://in.archive.ubuntu.com/ubuntu/ hardy-updates universe 
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
deb http://in.archive.ubuntu.com/ubuntu/ hardy multiverse 
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy multiverse 
deb http://in.archive.ubuntu.com/ubuntu/ hardy-updates multiverse 
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-updates multiverse 

## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
# deb http://in.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse 
# deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse 

## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu 
## users. 
# deb http://archive.canonical.com/ubuntu hardy partner 
# deb-src http://archive.canonical.com/ubuntu hardy partner 

deb http://security.ubuntu.com/ubuntu hardy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted 
deb http://security.ubuntu.com/ubuntu hardy-security universe 
deb-src http://security.ubuntu.com/ubuntu hardy-security universe 
deb http://security.ubuntu.com/ubuntu hardy-security multiverse 
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse 
```

---

### Post by johnnybravo666 on 2008-07-17
Do you have the DVD or CD version of ubuntu?

---

### Post by AceDip on 2008-07-17
i have the cd.

---

### Post by johnnybravo666 on 2008-07-17
I don't think the CD version comes with the build-essential package. I may be wrong though. Try this.

Run ```
sudo gedit /etc/apt/sources.list
```. This will bring up the sources.list file in the text editor. 

Look for a line that reads ```
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
``` Remove the '#' from the beginning of the line.

Then save and close. Run ```
sudo apt-get update
```

Then ```
sudo apt-get install build-essential
```

This will include the packages on the CD in the package list. They should already be there though. But its worth a try if you don't have a internet connection in linux. Your best bet is to get your internet connection working in linux.

---

### Post by AceDip on 2008-07-17
> **johnnybravo666 said:**
> I don't think the CD version comes with the build-essential package. I may be wrong though. Try this.

Run ```
sudo gedit /etc/apt/sources.list
```. This will bring up the sources.list file in the text editor. 

Look for a line that reads ```
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
``` Remove the '#' from the beginning of the line.

Then save and close. Run ```
sudo apt-get update
```

Then ```
sudo apt-get install build-essential
```

This will include the packages on the CD in the package list. They should already be there though. But its worth a try if you don't have a internet connection in linux. Your best bet is to get your internet connection working in linux.
Thanks a lot man..did as u said and the thing worked..thanks again.i had put in quite a lot of time for this..anyways all is well that ends well..i was begining to get fed-up of ubuntu coz this was important..

and yeah well could you kindly explain to me wat we just did and wat had happen..

---

### Post by AceDip on 2008-07-17
> **era86 said:**
> I would look into your sources.list file for proper repositories.  Just do a gedit on /usr/apt/sources.list and show us the contents of that file.
i must also thank you era for bringing in the idea of ckecking the cources.list file without which i dont think we'd have reached the solution.

---

### Post by Tony Flury on 2008-07-17
> **AceDip said:**
> i must also thank you era for bringing in the idea of ckecking the cources.list file without which i dont think we'd have reached the solution.

Especially as loads of other people suggested it too :-) lol 

Glad you got it sorted though.

---

### Post by johnnybravo666 on 2008-07-17
'/etc/apt/sources.list' is a list of software repositories that apt should check for packages. Basically the line that added the CD as a software repository was commented out. But once you uncommented it, the CD was added as a software repository and you could install software that was located on the CD. The 'sudo apt-get update' tells apt to update its list of packages from the repositories listed in the '/etc/apt/sources.list' file. 

In case you were wondering, apt is the package management system on ubuntu.

If you have any more questions, please ask.

It's a pleasure to help. I've gotten a lot of help from these forums and other linux users in general so I like to help others where I can.

---

### Post by era86 on 2008-07-17
> **AceDip said:**
> i must also thank you era for bringing in the idea of ckecking the cources.list file without which i dont think we'd have reached the solution.

Glad to have helped.  Just doin what this community taught me. ;)

Don't forget to mark your thread as Solved.

---

### Post by AceDip on 2008-07-18
> **Tony Flury said:**
> Especially as loads of other people suggested it too :-) lol 

Glad you got it sorted though.
well dude cant ignore u.you have been there since the begining..thanks a lot man.got my trust and respect back for ubuntu.

---

### Post by AceDip on 2008-07-18
> **johnnybravo666 said:**
> '/etc/apt/sources.list' is a list of software repositories that apt should check for packages. Basically the line that added the CD as a software repository was commented out. But once you uncommented it, the CD was added as a software repository and you could install software that was located on the CD. The 'sudo apt-get update' tells apt to update its list of packages from the repositories listed in the '/etc/apt/sources.list' file. 

In case you were wondering, apt is the package management system on ubuntu.

If you have any more questions, please ask.

It's a pleasure to help. I've gotten a lot of help from these forums and other linux users in general so I like to help others where I can.
well then if this is the case with the cd installation then it certainly sounds quite tough for a newbie.then why does ubuntu have to be so rigid to support even the most common programming languages..they should have been pre-installed and even if not then why so technical.

---

### Post by dribeas on 2008-07-18
> **elmoosecapitan said:**
> I also want to emphasize adding the line:

return 0;

I often find this floating around in discussions. C++ standard clearly states that a function must have a return type or be marked as void. Method/function implementations must return an element of the appropiate type (sadly, g++ does not flag this as an error or even a warning with default options) with the only exception of main that must define int as return value but that **is allowed not to return anything** with the compiler inserting an implicit return 0.

David

---

