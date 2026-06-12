---
title: "gcc install"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by dog6 on 2008-07-07
on the gcc.gnu.org website it gives instructions for installing gcc on a linux system as follow

1. get gcc binary package
2. Go into directory under which you want to put GFortran
3. Unpack the package using tar xvfz gcc-trunk-x86_64.tar.gz, which unpacks it into the directory gcc-trunk. 


I saved the binary package to my desktop on my virtual machine which has ubuntu 8.04, how do I go about performing steps 2 and 3.... or should I have gcc already on my OS and I am unaware, how do I check to see if I have it...

I am figuring this all out through trial by error and have never done anything like this...but want to start programming, thanks

---

### Post by iaculallad on 2008-07-07
It's just a single terminal command:

```
sudo apt-get install build-essential
```

and you're ready to go.

---

### Post by dog6 on 2008-07-07
I entered sudo apt-get install build-essential and get the following message.... i tried to type in my ubuntu password and the cursor did not move as i typed...? and then when i hit enter i got the E: ... line ??


[sudo] password for jerome: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
jerome@jerome-laptop:~$

---

### Post by iaculallad on 2008-07-07
If you see "no characters" when typing your password in the terminal, that's just normal:

Enter the command below on your terminal to fix the problem:

```
sudo dpkg --configure -a
```

---

### Post by bodhi.zazen on 2008-07-07
When you enter your password, nothing "prints" on the screen. This is normal.

Just enter your user log in password and hit enter.

To fix your current situation :

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
```

---

### Post by dog6 on 2008-07-07
thanks a lot, it appears to have worked, I guess my next step is trying to compile a simple .f file from my text editor... I might be chattin' you back later if i run into speed bumps...

thanks again

---

### Post by dog6 on 2008-07-08
I saved a file entitled hello_world.f in pico on the Ubuntu terminal,

i would like to compile this file in gcc and then convert to an executable.... 

the way i understand it, is that I need to compile this program into an object file (.o) ?  and then create the executable after that.... any help would be greatly appreciated..

---

### Post by Gamma746 on 2008-07-08
Refer to [http://gcc.gnu.org/wiki/GFortranUsage](http://gcc.gnu.org/wiki/GFortranUsage).

---

### Post by dog6 on 2008-07-08
This is the program I was using in pico and saved as hello_world.f9

 GNU nano 2.0.7            File:hello_world.f9                               

Program Hello_World
        implicit none
        Print *, "Hello, world!"
End Program Hello_World


*** The text below is what happened when I tried to compile... any suggestions..?

jerome@jerome-laptop:~$ gfortran -c hello_world.f
hello_world.f:1.1:

Program Hello_World                                                     
1
Error: Non-numeric character in statement label at (1)
hello_world.f:1.1:

Program Hello_World                                                     
1
Error: Unclassifiable statement at (1)
hello_world.f:4.1:

End Program Hello_World                                                 
1
Error: Non-numeric character in statement label at (1)
hello_world.f:4.1:

End Program Hello_World                                                 
1
Error: Unclassifiable statement at (1)
Error: Unexpected end of file in 'hello_world.f'

---

