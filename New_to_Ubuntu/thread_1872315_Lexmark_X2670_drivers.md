---
title: "Lexmark X2670 drivers"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by Drowz0r on 2011-10-30
Hello all

One of my ubuntu 11.10 machines has a Lexmark X2670 but no drivers it seems. I've tried to find the drivers or use generic drivers through ubuntu's own features but had no positive results. I went to the Lexmark website and downloaded the Linux drivers but they won't install. Any ideas?

Thanks

---

### Post by Sef on 2011-10-30
Did you follow the directions for the [Debian Based Package Manager]("http://support.lexmark.com/index?locale=en&page=product&productCode=LEXMARK_X2670&segment=SUPPORT&userlocale=EN_US&frompage=null#1")?

---

### Post by Drowz0r on 2011-10-30
> **Sef said:**
> Did you follow the directions for the [Debian Based Package Manager]("http://support.lexmark.com/index?locale=en&page=product&productCode=LEXMARK_X2670&segment=SUPPORT&userlocale=EN_US&frompage=null#1")?

Yeah that's where I got the Linux drivers from. I went to earlier but when following the instructions I get a prompt for the admin/root password but it doesn't accept the valid password and won't install the driver.

I took the Ubuntu drivers. Should I try a different one?

---

### Post by wojox on 2011-10-30
My lexmark had the same problem. Run the package as sudo from the terminal and it will ask for your password up front and then it will install.

---

### Post by Drowz0r on 2011-10-30
> **wojox said:**
> My lexmark had the same problem. Run the package as sudo from the terminal and it will ask for your password up front and then it will install.

Hey there

I tried doing:

**B. RUNNING THE GUI INSTALLER SCRIPT **
[LIST=1]
[*] Do not attach the printer via USB to the Linux machine.
[*]Extract the zip file.
lexmark-inkjet-[xx]-driver-[x.x.x].i386.deb.sh
[*]  Run the installer script file by double-clicking on the file icon and  then click the "Run in Terminal" button or run the script file via  command-line.
[*] Follow the instructions in the installer screen.
[/LIST]
But it didn't work. So I just tried the terminal way:

**A. RUNNING THE GUI INSTALLER SCRIPT IN THE TERMINAL**

[LIST=1]
[*] Open up your favorite terminal (xterm, konsole, gnome-terminal, etc)
[*] Extract the zip file
[*] Use the following command to install the driver 
   #./lexmark-inkjet-[xx]-driver-[x.x.x]..i386.deb.sh
[*] Follow the instruction in the installation screen.
[/LIST]
...but this didn't work either.

What is the sudo way? The file I have is named:

lexmark-inkjet-08-driver-1.0-1.i386.deb.sh

Is it something like sudo install lexmark-inkjet-08-driver-1.0-1.i386.deb.sh ?

---

### Post by wojox on 2011-10-30
It would be 

```
sudo lexmark-inkjet-08-driver-1.0-1.i386.deb.sh 
```

---

### Post by Drowz0r on 2011-10-31
> **wojox said:**
> It would be 

```
sudo lexmark-inkjet-08-driver-1.0-1.i386.deb.sh 
```

Hmm ok, does the driver need to be placed into any specific location before I try the sudo way?

I'll give it a go tonight and let you know how I get on.

---

### Post by Drowz0r on 2011-10-31
> **wojox said:**
> It would be 

```
sudo lexmark-inkjet-08-driver-1.0-1.i386.deb.sh 
```

Tried that and got:

```
sudo: lexmark-inkjet-08-driver-1.0-1.i386.deb.sh: command not found
```

---

### Post by Drowz0r on 2011-10-31
Anyone know if I'm missing something here?

---

### Post by wojox on 2011-11-01
You need to cd to the directory it's in. :P

---

### Post by Drowz0r on 2011-11-01
> **wojox said:**
> You need to cd to the directory it's in. :P

Yeah it's in my default directory. I typed "ls" and can see the driver, but I still get the command not found error.

---

### Post by wojox on 2011-11-01
It should be executable try:

```
sudo ./*sh
```

---

### Post by Drowz0r on 2011-11-04
> **wojox said:**
> It should be executable try:

```
sudo ./*sh
```

Ok it seemed to install the driver, but the term showed a load of errors when installing. It seemed to install fine regardless. It asked me to connect the printer via usb, which I did, and it detected the printer and everything however the installer wouldn't finish.

So I killed the installer and it seemed to be working. I attempted to print something and it went into the print queue but will not print.

I'm using the ubuntu drivers. Are there better ones? Or is there a different command to try?

---

### Post by Drowz0r on 2011-11-08
I think I'm about ready to explode D:

Are the ubuntu drivers the ones I should use or should I perhaps use a debian linux driver?

---

### Post by JacksRevenge on 2011-11-09
I am having the same problems, i get a bunch of errors while installing and then I get failed to install....any help would be great so that I do not have to keep jumping to windows to print

---

### Post by DFNBunny on 2011-11-09
Hello,
Real frustrated, real beginner.  I am barely knowledgeable on Linux machines.  I can get to terminal and that's about it.

Upgraded to Ubuntu 11.10 and now the Lexmark printer fails.

The error I get after the automatic install is "cups-insecure-filter"
I deleted it and tried installing the  [Debian Based Package Manager]("http://support.lexmark.com/index?locale=en&page=product&productCode=LEXMARK_X2670&segment=SUPPORT&userlocale=EN_US&frompage=null#1") using the terminal AND just running it.  It installs until it asks for me to "plug in the printer".  I plug in the printer and the (bad?) driver automatically installs itself ALSO when I click on OK to keep running the terminal based install, nothing happens.  I keep clicking and the install keeps asking for me to plug in the printer.

The printer works fine when I plug it into a Windows based system.

Real noob:confused: here so please be gentle and thorough with steps to fix this.

---

### Post by Drowz0r on 2011-11-11
I had the similar issues during installation. I'm guessing it's an 11.10 bug then with the volume of people having the same issue?

Can't seem to find any suggestions or acknowledgement of this bug though.

---

### Post by Drowz0r on 2011-11-14
It'd be great to know if someone knows if the debian, ubuntu or other driver was needed or what the differences are between them. It'd sure be a good starting point for me anyway.

---

### Post by Drowz0r on 2011-11-18
Are there any generic drivers that may work for Lexmark or anything? Just want basic printing functionality, nothing fancy.

Maybe something I can run through wine with the windows drivers or something?

---

### Post by Drowz0r on 2011-12-19
Ok, so printing on Linux seems fruitless. Even with a very common printer :/

Are there any known to work printers on Linux? Although I dislike it I may just have to buy a new printer.

---

### Post by Drowz0r on 2012-01-02
Re-did the steps. It showed exactly what printer it was when I connected the printer. It said it was ready for printing and all sorts.. but won't get past this step:

[http://img833.imageshack.us/img833/6447/screenshotat20120102192.png](http://img833.imageshack.us/img833/6447/screenshotat20120102192.png)

So I ignored it and tried to print something anyway but I get these errors:

[http://img714.imageshack.us/img714/6447/screenshotat20120102192.png](http://img714.imageshack.us/img714/6447/screenshotat20120102192.png)

To be honest, I'd be happy just buying a new printer and scanner combo machine that works at this rate though :/

---

