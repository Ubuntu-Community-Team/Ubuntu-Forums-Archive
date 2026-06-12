---
title: "installing teanviewer"
date: 2012-11-07
forum: New to Ubuntu
---

### Post by sunny12345 on 2012-11-07
hi 
i am totally new to linux, i want to install teamviewer, i have downloaded it and tried to install it by using 

sudo dpkg--install teanviewer_linux_x64.deb

and it gives me an error that

sudo: dpkg--install: comand not found

can anyone help me on that i need to install teamviewer please
Regards

---

### Post by Robocracy on 2012-11-07
Hey sunny12345 (loving the creativity with the name :p),

Have you tried navigating the terminal to the correct folder that the TeamViewer programme is?

This is a good place to learn how to navigate the terminal (that's if you don't know of course :D)
[http://ubuntuforums.org/showthread.php?t=908543](http://ubuntuforums.org/showthread.php?t=908543)

Hope this helps and hope you're enjoying Linux too (:

---

### Post by newb85 on 2012-11-07
Hello, and welcome to Ubuntu and the forums!

For future reference, commands entered at the terminal and results from terminal commands should be surrounded by code tags when you post them, like this:

[noparse]```
Command
or
output
here
```[/noparse]

(An easy way to do this is to highlight the command/output and click the button with # right above the composition frame.)

Also, copying and pasting is usually a much better idea than retyping commands.  A single character mistake throws everything off.  (Keyboard shortcuts for copy and paste in the the terminal are Ctrl+Shift+C and Ctrl+Shift+V.)
 
```
sudo dpkg --install teanviewer_linux_x64.deb
```

---

### Post by sunny12345 on 2012-11-07
thx for your reply Robocracy :)
i have saved it into my Downloads and then using the comand lines which i found on the internet, i am using linux for the first time, could you possibly guide me how to install teamviewer?
Regards

---

### Post by Robocracy on 2012-11-07
Well I'm hoping I'm going to get this right, so here goes:

You head over to the 'Terminal' and you enter

```
cd /home/[insert your username here without the square brackets]/Downloads
```

then you should get the initial command line change from

```
[username]@[computer name]:~$
```

to

```
[username]@[computer name]:~/Downloads$
```

now enter

```
sudo dpkg --install teanviewer_linux_x64.deb
```

Hopefully that'll sort everything out (:

---

### Post by sunny12345 on 2012-11-07
i am doing the same and its giving me an error:

Errors were encounted while processing: 
teamviewer7: i386

---

### Post by NikTh on 2012-11-07
Hi , 

If the error you received is due to missing dependencies , you can try to correct with this command 

```
sudo apt-get install -f
``` 

or else, make sure you downloaded the correct architecture 32bit or 64bit. 

You can see what arch is your system with these commands 
```
lscpu | grep Arch
uname -a
```
x86_64= 64 bit
i686 or X86 = 32bit

The other thing is that teamviewer is available to another form , where you not need to install something. Scroll down the page and you will see 
[B]Other systems (not officially supported)
Download tar.gz v7.0.9377[/B]
 
You can download this package and extract the contents and then run teamviewer with a simple command in terminal.

We assume you downloaded and extracted the contents to Downloads folder, open a terminal and do 
```
cd Downloads 
./teamviewer
``` 
Is running ?

---

### Post by sunny12345 on 2012-11-07
nothing seems to work for me!!:(

---

### Post by raja.genupula on 2012-11-07
open your terminal and do these steps one by one 
```
wget http://www.teamviewer.com/download/teamviewer_linux.deb
sudo dpkg -i teamviewer_linux.deb
```
execute them one by one .

---

### Post by Zill on 2012-11-07
Firstly, *spelling* is important when installing software and this thread refers to both "tea[COLOR="Red"]m[/COLOR]viewer" and "tea[COLOR="red"]n[/COLOR]viewer".

Assuming you actually want to install "teamviewer_linux_x64.deb" then simply download this file to the location of your choice then double-click on the downloaded file to start the gdebi installer.  This *should* request your password and then install the package automatically.

---

### Post by sunny12345 on 2012-11-07
i cant believe all i had to do was double click on the folder n the rest is done by the machine itself!!!!!!!!!!
THANKSSSS ALLLLOOOTTTT :P



> **Zill said:**
> Firstly, *spelling* is important when installing software and this thread refers to both "tea[COLOR=Red]m[/COLOR]viewer" and "tea[COLOR=red]n[/COLOR]viewer".

Assuming you actually want to install "teamviewer_linux_x64.deb" then simply download this file to the location of your choice then double-click on the downloaded file to start the gdebi installer.  This *should* request your password and then install the package automatically.

---

### Post by sunny12345 on 2012-11-07
problem solved !!!! finally 
thanks everyone:P

---

### Post by Zill on 2012-11-07
sunny12345:  I am pleased you got the package installed.

Now would you please mark the thread as "Solved" by using the "Thread Tools" pull-down menu near the top right of this screen.  Only the original-poster can do this!

---

