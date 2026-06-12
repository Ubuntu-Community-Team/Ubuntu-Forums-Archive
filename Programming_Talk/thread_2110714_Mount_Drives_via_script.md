---
title: "Mount Drives via script"
date: 2013-01-30
forum: Programming Talk
---

### Post by n8af on 2013-01-30
Hi all,

For my own reasons, i want to create a script to mount some network drives.  I was using fstab; however, for some reason my wireless is intermittent with ubuntu 12.04 and it causes hangups while booting and shutting down.  In the meantime, i'm trying to write a simple script that will do this for me once i'm logged in at the desktop.

Here is what i have so far:

```
#!/bin/bash
clear
echo "Network Drive Mount"
echo "-----------------------------------"
echo "What to do?"
echo "1: Mount Documents"
echo "2: Mount Music"
echo "3: Mount Pictures"
echo "4: Mount Server Drive F"
echo "5: Mount ALL OF THE ABOVE"
read userselect

if [ "$userselect" = 1 ]; then
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/storage/skydrive/documents/nate/ /home/nate/Documents
fi

if [ "$userselect" = 2]; then
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/music /home/nate/Music
fi

if [ "$userselect" = 3]; then
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/storage/skydrive/pictures /home/nate/Pictures
fi

if [ "$userselect" = 4]; then
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/ /home/nate/mounts
fi

if [ "$userselect" = 5]; then
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/storage/skydrive/documents/nate/ /home/nate/Documents
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/music /home/nate/Music
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/storage/skydrive/pictures /home/nate/Pictures
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/ /home/nate/mounts
fi
```

Right now the only option that works is number 1.  All the other options just exit the script without entering the if statements.  I'm not sure what i'm doing wrong. First time writing a bash script;)

---

### Post by Bucky Ball on 2013-01-30
*Thread moved to **Programming Talk***

---

### Post by r-senior on 2013-01-31
When checking that two things are equal, use '=='. A single '=' is used for assigning a value to something.

```
if [ "$userselect" [COLOR="Red"]==[/COLOR] 1 ]; then
```

---

### Post by furything on 2013-01-31
Use elif to combine statements

so ```
#!/bin/bash clear 
echo "Network Drive Mount" 
echo "-----------------------------------" 
echo "What to do?" 
echo "1: Mount Documents" 
echo "2: Mount Music" 
echo "3: Mount Pictures" 
echo "4: Mount Server Drive F" 
echo "5: Mount ALL OF THE ABOVE" 
read userselect  

if [ "$userselect" = 1 ]; then 
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/storage/skydrive/documents/nate/ /home/nate/Documents  

elif [ "$userselect" = 2]; then 
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/music /home/nate/Music  

elif [ "$userselect" = 3]; then
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/storage/skydrive/pictures /home/nate/Pictures  

elif [ "$userselect" = 4]; then
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/ /home/nate/mounts 

elif [ "$userselect" = 5]; then 
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/storage/skydrive/documents/nate/ /home/nate/Documents 
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/music /home/nate/Music 
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/storage/skydrive/pictures /home/nate/Pictures 
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/ /home/nate/mounts
fi

```Note last elif test for =5 could be default so just 'else' that is key 1-4 do as asked anything else just do all
> When checking that two things are equal, use '=='. A single '=' is used for assigning a value to something.This is true for c,c++,c# and a number of other programming but not here in bash

---

### Post by rnerwein on 2013-01-31
hi
just as a hint:
#!/bin/bash
echo "1: Mount Documents"
echo "2: Mount Music"
echo "3: Mount Pictures"
echo "4: Mount Server Drive F"
echo "5: Mount ALL OF THE ABOVE"
echo -n "your selection: "
read userselect

case $userselect in
    1) sudo mount ..... ;;
    2) sudo mount ..... ;;
    3) sudo mount ..... ;;
    4) sudo mount ..... ;;
    5) sudo mount ..... ;;
    *) echo "wrong input"
        exit 1
esac

# and you can apend your /etc/sudoers with: your_name ALL=NOPASSWD: /bin/bash, /bin/mount
# to avoid the password question.

have fun with bash
cheers

---

### Post by n8af on 2013-01-31
> **r-senior said:**
> When checking that two things are equal, use '=='. A single '=' is used for assigning a value to something.

```
if [ "$userselect" [COLOR="Red"]==[/COLOR] 1 ]; then
```

Oh yes! it was late last night and i think my brain just shut down! I can't believe i missed this.

Edit: > Note last elif test for =5 could be default so just 'else' that is key 1-4 do as asked anything else just do all
This is true for c,c++,c# and a number of other programming but not here in bash  

Ah! I was wondering after reading through the tutorial again.

Thanks for the additional posts.  You guys more than helped answer my question!  And thanks for the no password method!  You guys rock! :guitar:

---

### Post by n8af on 2013-01-31
> **furything said:**
> Use elif to combine statements

so ```
#!/bin/bash clear 
echo "Network Drive Mount" 
echo "-----------------------------------" 
echo "What to do?" 
echo "1: Mount Documents" 
echo "2: Mount Music" 
echo "3: Mount Pictures" 
echo "4: Mount Server Drive F" 
echo "5: Mount ALL OF THE ABOVE" 
read userselect  

if [ "$userselect" = 1 ]; then 
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/storage/skydrive/documents/nate/ /home/nate/Documents  

elif [ "$userselect" = 2]; then 
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/music /home/nate/Music  

elif [ "$userselect" = 3]; then
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/storage/skydrive/pictures /home/nate/Pictures  

elif [ "$userselect" = 4]; then
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/ /home/nate/mounts 

elif [ "$userselect" = 5]; then 
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/storage/skydrive/documents/nate/ /home/nate/Documents 
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/music /home/nate/Music 
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/storage/skydrive/pictures /home/nate/Pictures 
sudo mount -t cifs -o credentials=/path/secured/.creds //192.168.1.4/f/ /home/nate/mounts
fi

```Note last elif test for =5 could be default so just 'else' that is key 1-4 do as asked anything else just do all
This is true for c,c++,c# and a number of other programming but not here in bash

I tried this method but it did the same thing.  It only mounts the first option and ignores the others.
However, I did try the other format:
```
#!/bin/bash
echo "1: Mount Documents"
echo "2: Mount Music"
echo "3: Mount Pictures"
echo "4: Mount Server Drive F"
echo "5: Mount ALL OF THE ABOVE"
echo -n "your selection: "
read userselect

case $userselect in
1) sudo mount ..... ;;
2) sudo mount ..... ;;
3) sudo mount ..... ;;
4) sudo mount ..... ;;
5) sudo mount ..... ;;
*) echo "wrong input"
exit 1
esac
```

This one works great!

I also tried inserting the no password command into the sudoers file (using visudo command); however, it still asks for the password.  This isn't a very big deal, i can live with it.  Thanks though!

---

### Post by furything on 2013-02-01
You know the example I looked at states just one = for equivalence 
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-6.html#ss6.2](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-6.html#ss6.2)

but it is two
[http://www.thegeekstuff.com/2010/06/bash-conditional-expression/](http://www.thegeekstuff.com/2010/06/bash-conditional-expression/)

or can you do both?
Not experienced with bash as you can see

---

### Post by n8af on 2013-02-01
> **furything said:**
> You know the example I looked at states just one = for equivalence 
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-6.html#ss6.2](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-6.html#ss6.2)

but it is two
[http://www.thegeekstuff.com/2010/06/bash-conditional-expression/](http://www.thegeekstuff.com/2010/06/bash-conditional-expression/)

or can you do both?
Not experienced with bash as you can see

I tried it with both a single '=' and a double '==' with the same result.  I'm not sure as to why it was skipping the other options while using the if/then/else conditions.  

I thought maybe my mount command wasn't written correctly until i tried the other menu option in which i just cut and pasted the mount command and now it works.  :confused:

Nevertheless, thanks for your input!

---

### Post by r-senior on 2013-02-02
I think it is something very trivial and it confused me into writing nonsense. 

I took the script, changed the = to == and it worked ... well it did after I added spaces before the closing square brackets. ;)

```
= 2]; then
```

```
= 2 ]; then
```

I think that was the problem. Both styles of equality test work (once the brackets are fixed). Obviously the case statement takes the brackets out of the game.

---

### Post by furything on 2013-02-04
Thanks r-senior that makes sense. 
I will try to remember this (] with spacing) as sometimes I edit scripts that closely match what I want but not quite.

---

