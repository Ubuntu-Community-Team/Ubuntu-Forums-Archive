---
title: "[SOLVED] Problem 1. Can't get Flash Player to Install"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by incendiary on 2008-08-22
Hello there. I'm having a few issues, being a novice. This is problem 1...

I'm trying to get Flash Player to install into Firefox on Xubuntu (Compaq Evo N600c). I get as far as running the install package, then it asks for a path, but whatever I enter I am told is invalid.

I downloaded the install_flash_player_7_linux.tar.gz as instructed in a very helpful forum entry here. I then extracted and executed as follows:

cd Desktop
tar zxvf install_flash_player_9_linux.tar.gz

Then I ran the installation:

cd install_flash_player_9_linux
sudo sh flashplayer-installer

When asked to enter the installation path, I tried the following, but was told it is invalid...

-----------------------------------------------------------------
Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): 
------------------------------------------------------------------

I have tried varous paths to Mozilla, Mozilla/extensions, Mozilla/plugins, Firefox, Firefox/extensions, and a number of other obvious ones but all are 'invalid'. I know this is not due to mis spelling as this gives a different error message.

What am I doing wrong?

---

### Post by Sef on 2008-08-22
> I'm trying to get Flash Player to install into Firefox on Xubuntu

Why not download flash from the repositories?

---

### Post by bikeboy on 2008-08-22
You're doing it the hard way, the Windows way.

Open up a terminal (Alt+F2, gnome-terminal)

Type *sudo apt-get install flashplugin-nonfree* followed by your user password. Another option, the heavyweight way that installs lots of other extras is *sudo apt-get install xubuntu-restricted-extras*.

Edit, Xubuntu. How to open a terminal is slightly different, but the command still applies.

---

### Post by LTFC2020 on 2008-08-22
.tar.gz doesn't really work too well with ubuntu
open a terminal and type

sudo apt-get install flashplugin-nonfree flashplayer-nonfree

should work fine

---

### Post by LTFC2020 on 2008-08-22
bike boy beat me to it..:)

---

### Post by Dedoimedo on 2008-08-22
Hello,

The hard way:

1. Download the archive from Adobe site.
2. Extract archive.
3. Run the script (no need to sudo).
4. The script will look for installation path for browsers.
5. Confirm.
6. You should have Flash running.

The easy way:

1. Power up your browser (Firefox ?), got to Youtube. The browser should popup the "additional codecs needed ..."
2. Select either Adobe or Gnash, install, restart browser.
3. You should have Flash running.

Cheers,
Dedoimedo

---

### Post by incendiary on 2008-08-22
> **bikeboy said:**
> You're doing it the hard way, the Windows way.

Open up a terminal (Alt+F2, gnome-terminal)

Type *sudo apt-get install flashplugin-nonfree* followed by your user password. Another option, the heavyweight way that installs lots of other extras is *sudo apt-get install xubuntu-restricted-extras*.

Edit, Xubuntu. How to open a terminal is slightly different, but the command still applies.

Billiant. Thanks bikeboy - and everyone else for the very quick response. I now have all Java / Flash etc working.

On to Problem 2... Look out for the next installment of 'incendiary's problems' in another thread...

---

### Post by snktagarwal on 2008-08-24
cd Desktop
tar zxvf install_flash_player_9_linux.tar.gz

Then I ran the installation:

cd install_flash_player_9_linux
sudo sh flashplayer-installer
-----------------------------------------------------------------------

See first thing u got wrong was the **_sudo_** sh <bla bla>
Basically mozilla has got a home directory ~/.mozilla. So u need not do sudo.... actually when u sudo u may become the root.... in case u have root equivalent permissions..... 

What happens i will tell u, first the right way for a normal user to do it....

1. The defult directory in flash script is ~/.mozilla
2. make sure u have the permissions to write to it.
3. if u dont:
    3.1 $ cd ~
    3.2 $ sudo chmod o+w .mozilla,  that is taking the write permissions 
4. make a folder called plugins if not already present
5. see u hav the right permissions to write to it.... most prob u have them
6. $ sh flashplayer-installer

Now u won't be prompted at all..... 

What if u were the almighty.... ROOT or equivalent... in ur case maybe sudoer

1. u need to add a dir called components under /usr/lib/mozilla
     1.1 $ cd /usr/lib/mozilla 
     1.2 $ sudo mkdir components
     
2. now install by $ sudo sh flashplayer-installer


root may also be there instead of sudo.... hope u do that urself
 
So now the thing u wud be scratching is that why didnt the script do it itself..... well it's a bit clumsy for sure.... the error reporting is worse too..... 
REMEMBER: root only when u need to!!

---

### Post by Bucky Ball on 2008-08-24
Open a terminal and do this (line by line not all at once):

```
cd /tmp
wget [http://download.macromedia.com/pub/l..._070208.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz")
tar -zxvf flashplayer10_install_linux_070208.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer
```

You are on your way ... :)

---

