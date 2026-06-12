---
title: "Bash Scripting if then functions"
date: 2011-05-04
forum: Programming Talk
---

### Post by datadude3 on 2011-05-04
I'm writing a shell script to install a couple of programs and configure the OS. I'm breaking it up into functions, but whenever I use if then commands from a function, when I run it I get this error:
> /home/andrew/Desktop/Test.sh: line 96: syntax error near unexpected token `}'
/home/andrew/Desktop/Test.sh: line 96: `}'I'm using the function to test if the user wants to manually edit the fstab file, they can, or they can skip it and go to the next function.

This is my script for the 2 functions. Line 96 is the first "}", after "failedmanualFunction;"
> manualFunction(){
echo "Configure fstab file (y/n)?"
read input
if [ $input = y ]
    then fstabFunction
if [ $input = n]
    then continueFunction
fi
failedmanualFunction;
}
failedmanualFunction(){
echo "Invalid response. Please enter either 'y' or 'n'."
manualFunction
}What am I doing wrong? When I run the script outside of the function, it runs fine, I just can't get it to loop if there's an invalid response.

I don't know if it makes much of a difference, but I'm using the latest version Ubuntu 11.04.

---

### Post by crafter on 2011-05-05
You are missing end endif (fi) before your closing bracket.

> if [ $input = y ]
then fstabFunction
if [ $input = n]
then continueFunction
fi
failedmanualFunction;
[COLOR="Red"]fi[/COLOR]

---

### Post by stchman on 2011-05-05
You need a space after the 'n' and the ']'.  Yes it is that sensitive.

```


if [ $input = y ]
          then fstabFunction
if [ $input = n ]
          then continueFunction
fi

```

---

### Post by datadude3 on 2011-05-06
That fixed it, except when you type in anything other then y or n, instead of asking for another input, it keeps going with the rest of the script. It has something to do with where it goes to "failedmanualFunction", I just don't know how to make an if/then statement for "if input is not equal to 'y' or 'n'". Any ideas?

Also, now I added 2 new functions at the beginning to see if you have superuser privileges before it continues with the rest of the installer.

It gives me this error:
> /home/andrew/Desktop/Installer.sh: line 9: syntax error near unexpected token `fi'
/home/andrew/Desktop/Installer.sh: line 9: `fi'This is the script at the beginning, starting at line 0:
> sudoFunction(){
echo "Please enter your password to perform administrative tasks."
sudo echo "---"
user=$(id -u)
if [ $user = 0 ]
          welcomeFunction;
if [ $user > 0 ]
      failedsudoFunction;
fi
}
failedsudoFunction(){
clear
echo "Error: You must be root to continue."
sudoFunction
}If I try to take out the fi on line 9, it gives the same error, but with "}" instead.

---

### Post by tgm4883 on 2011-05-06
> **datadude3 said:**
> That fixed it, except when you type in anything other then y or n, instead of asking for another input, it keeps going with the rest of the script. It has something to do with where it goes to "failedmanualFunction", I just don't know how to make an if/then statement for "if input is not equal to 'y' or 'n'". Any ideas?

Also, now I added 2 new functions at the beginning to see if you have superuser privileges before it continues with the rest of the installer.

It gives me this error:
This is the script at the beginning, starting at line 0:
If I try to take out the fi on line 9, it gives the same error, but with "}" instead.

You probably need to use CASE instead of if/else

---

### Post by datadude3 on 2011-05-06
I figured out how to fix it.
I added "fi" after the first if/then test and added the failedmanualFunction as an else statement to it.

I changed the sudoFunction a little so it's now this:
> sudoFunction(){
echo "Please enter your password to perform administrative tasks."
sudo echo "---"
user=$(id -u)
if [ $user = 0 ]
    then welcomeFunction;
    else failedsudoFunction;
fi
}
failedsudoFunction(){
clear
echo "Error: You must be root to continue."
sudoFunction;
}The only problem is that now when you are sudo, it loops between the two functions infinitely.

---

