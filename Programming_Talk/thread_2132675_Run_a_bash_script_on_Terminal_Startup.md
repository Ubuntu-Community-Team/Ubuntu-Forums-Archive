---
title: "Run a bash script on Terminal Startup"
date: 2013-04-05
forum: Programming Talk
---

### Post by thecodejunkie on 2013-04-05
I have Ubuntu 12.

I made a simple script to ask for a password before I can get in the terminal, but how do I make it so it runs this script every single time I start Terminal? Here's the script:

```
clear

echo EVTech TermLock v1.0.0
echo #
echo Enter password now:
read password

if [ $password = password ]
    then echo #
    echo Access granted! Press enter to continue.
    read key
    clear
    else echo #
    echo Access denied! Press enter to try again.
    read key
    bash EVTermLock.sh
fi
```

---

### Post by Cheesemill on 2013-04-05
You could call it from your ~/.bashrc file which gets run every time you open a terminal.
Just edit your ~/.bashrc and add the following to the bottom...
```
source /path/to/script.sh
```

You do realise that your script provides no extra security and is trivial to disable don't you ?

---

### Post by thecodejunkie on 2013-04-05
> **Cheesemill said:**
> You could call it from your ~/.bashrc file which gets run every time you open a terminal.
Just edit your ~/.bashrc and add the following to the bottom...
```
source /path/to/script.sh
```

You do realise that your script provides no extra security and is trivial to disable don't you ?

I do know that it's stupid and simple and provides no real protection, but I'm really just doing it to learn.

How do I get to said "~/.bashrc"?

---

### Post by texpat on 2013-04-05
Its in your home directory. The dot '.' before the filename makes it hidden. Try [FONT=Courier New]ls -a[/FONT] to see it in a directory listing.

---

### Post by thecodejunkie on 2013-04-05
I figured it out, had to unhide the files. Thanks! It works now. I'll perfect the script :D

---

### Post by thecodejunkie on 2013-04-05
Now if I wanted to hide the user input with *'s, how would I do that?

Slightly updated script:
```
clear

echo EVTech TermLock Protocol v1.0.1
echo #
echo Enter password now:
read password

if [ $password = password ]
    then echo #
    echo Access granted! Press enter to continue.
    read key
    clear
    else echo #
    echo Access denied! Press enter to try again.
    read key
    bash ~/Documents/Scripts/Bash/EVTermLock.sh
fi
```

---

### Post by savi3000 on 2013-04-05
read -s key

---

### Post by thecodejunkie on 2013-04-05
> **savi3000 said:**
> read -s key

Keep in mind that this is in fact the Absolute Beginners Section, I have no idea how to use that in the proper context.

---

### Post by DrGroove on 2013-04-06
Just replace your original line:
> read key
with
> read -s key

Output when entering the password will be empty.

---

### Post by Lars Noodén on 2013-04-06
read is built into bash.  If you want to know more about the other options for it and the other built-in commands, then the place to look is [the manual page for bash](http://manpages.ubuntu.com/manpages/precise/en/man1/bash.1.html).  It will give you more than you want to know, but it's an invaluable reference and well worth learning to navigate.

---

### Post by thecodejunkie on 2013-04-06
> **DrGroove said:**
> Just replace your original line:

with


Output when entering the password will be empty.

Well yeah but I asked how to hide input with *

---

### Post by schragge on 2013-04-06
> **thecodejunkie said:**
> Well yeah but I asked how to hide input with *
```

exec 3>&1
passwd=`whiptail --passwordbox 'Enter password:' 7 21 2>&1 1>&3`
exec 3>&-
echo $passwd

```
Alternatively, you could use [dialog](http://manpages.ubuntu.com/manpages/precise/en/man1/dialog.1.html) or [zenity](http://manpages.ubuntu.com/manpages/precise/en/man1/zenity.1.html) instead of [whiptail](http://manpages.ubuntu.com/manpages/precise/en/man1/whiptail.1.html).

---

### Post by thecodejunkie on 2013-04-06
> **schragge said:**
> ```

exec 3>&1
passwd=`whiptail --passwordbox 'Enter password:' 7 21 2>&1 1>&3`
exec 3>&-
echo $passwd

```
Alternatively, you could use [dialog]("http://manpages.ubuntu.com/manpages/precise/en/man1/dialog.1.html") or [zenity]("http://manpages.ubuntu.com/manpages/precise/en/man1/zenity.1.html") instead of [whiptail]("http://manpages.ubuntu.com/manpages/precise/en/man1/whiptail.1.html").

I had originally posted this in the absolute beginners section, so telling me that doesn't really tell me anything.

---

### Post by r-senior on 2013-04-06
Whiptail displays various types of controls inside a terminal window. Things like information boxes, error boxes, text entry boxes, etc.

```
whiptail --msgbox "This is what Whiptail looks like" 10 30
```

Zenity and Dialog do a similar job, but they display a separate window, rather than using the existing terminal. The window will match the desktop environment being used, so on default Ubuntu it will have an orange close button, etc.

```
zenity --info --text="This is what Zenity looks like"
```

Screenshots of Whiptail and Zenity attached.

For a password box with '*':

```
zenity --entry --text="Password" --hide-text
```

---

### Post by schragge on 2013-04-06
The whole script done with whiptail:
```

#!/bin/bash -e

get_password() {
  exec 3>&1
  REPLY=`whiptail --ok-button 'Unlock' --nocancel --passwordbox 'Enter password:' 7 21 2>&1 1>&3`
  exec 3>&-
  return 0
}

while
  get_password
  [[ $REPLY != 'password' ]]
do
  whiptail --ok-button 'Try again' --msgbox 'Access denied!' 7 19
done

whiptail --ok-button 'Continue' --msgbox 'Access granted!' 7 19

```

---

### Post by thecodejunkie on 2013-04-08
> **schragge said:**
> The whole script done with whiptail:
```

#!/bin/bash -e

get_password() {
  exec 3>&1
  REPLY=`whiptail --ok-button 'Unlock' --nocancel --passwordbox 'Enter password:' 7 21 2>&1 1>&3`
  exec 3>&-
  return 0
}

while
  get_password
  [[ $REPLY != 'password' ]]
do
  whiptail --ok-button 'Try again' --msgbox 'Access denied!' 7 19
done

whiptail --ok-button 'Continue' --msgbox 'Access granted!' 7 19

```

Thanks, but that's still not really what I asked. I asked how to change MY SCRIPT to have stars instead of the password or the -s thing or whatever.

It seems like nobody on this forum has any listening skills.

---

### Post by schragge on 2013-04-08
Well, you can read one character a time with *read -sn1* and output an asterisk for it:
```

#!/bin/bash
password=''
while read -sn1 char; do
[[ -z $c ]] && break;
echo -n \*
password+=$char
done
echo
echo $password

```

---

### Post by thecodejunkie on 2013-04-08
> **schragge said:**
> Well, you can read one character a time with *read -sn1* and output an asterisk for it:
```

#!/bin/bash
password=''
while read -sn1 char; do
[[ $c == '' ]] && break;
echo -n \*
password+=$char
done
echo
echo $password

```

How would I apply this to my script?

---

### Post by Bodsda on 2013-04-08
> **thecodejunkie said:**
> How would I apply this to my script?

Can I suggest that you run some of the code that you have been given, find the one that has the best output for your needs, analyse it and adapt to suit.
What would you be learning if we write it for you?

Bodsda

---

### Post by thecodejunkie on 2013-04-10
> **Bodsda said:**
> Can I suggest that you run some of the code that you have been given, find the one that has the best output for your needs, analyse it and adapt to suit.
What would you be learning if we write it for you?

Bodsda

I would learn how to adapt it to my script.

I could analyze someone else's code and figure out how they did it in a few minutes, or I could spend hours trying to apply it myself and get nowhere.

---

