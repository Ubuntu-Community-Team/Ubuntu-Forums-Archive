---
title: "Can't Find Icon for starting program"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Ragweed on 2008-05-31
I'm relatively new to Ubuntu.  I've used it about a month or so now so I'm STILL trying to get used to it.

I've installed GeneWeb and checked and double checked that it's really there and I find various and sundry folders for it.  Also, my Synaptic Packager also says it's installed.

However, when I search through the menus, I find no Geneweb.

Please help....

Joseph

---

### Post by drs305 on 2008-05-31
Go to post #4

Using the following command will show where the apps files are distributed:
```
whereis appname
```
Note spelling and case are important

You can also run this if you know the start command to find the location of the app:
```
which appname
```

It looks like the launch command will be 'geneweb'. 

If you can't find it in the menus, you can make a launcher by right clicking on the desktop or panel. Name it what you want and (probably) put ' geneweb ' in the command window.

---

### Post by enderwig on 2008-05-31
Right click on your menu button and choose edit menus.  See if your app is in there and just is not checked.  If so, check the box next to it, and it will show in your menu.

---

### Post by drs305 on 2008-05-31
Using the 'whereis' command above after I installed the app, I found the documentation in /usr/share/lib/geneweb. I could not find any menu listings. According to the README file, here is how you run it:


If you are under Unix or Mac
   Launch your Web navigator.
   If you installed GeneWeb, for example in
        /home/smith/geneweb
   open the location:
        file:/home/smith/geneweb/gw/doc/index.htm
   and follow the instructions.


I had to search around a while before finding the file they referenced. If you installed it in the default location, it ended up in usr/share/doc/geneweb/index.htm  
That really isn't where an app's files should be, so you might look in your home folder, perhaps for .geneweb

In your browser address window, type:
```

file:///usr/share/doc/geneweb/index.htm

```

I could not find any files in my user folders after the default synaptic install. If this is your case, if the program allows, you may be directed to make a folder in your home directory to allow you to save any data files that are created. You will not be able to save files in the /usr/shre/doc/geneweb folder by default. You would have to use the 'sudo chown' command to do so. Come back if you need help. 

Hopefully this company has an on-line data system. Go to their site and look for instructions.

---

### Post by Ragweed on 2008-05-31
Enderwing, I checked the menu and there was no icon there.

Drs503, I used the whereis command and got the following:

ragweed@ragweed-den:~$ whereis geneweb
geneweb: /etc/geneweb /usr/lib/geneweb /usr/share/geneweb
ragweed@ragweed-den:~$ cd /usr/lib/geneweb
ragweed@ragweed-den:/usr/lib/geneweb$ dir
gwd.wrapper  gwsetup.wrapper
ragweed@ragweed-den:~$

I'd discovered the gwsetup but was not sure how to get it working.  Remember, I'm very green in this.

---

### Post by Ragweed on 2008-05-31
I used the directions [I think] which you'd given.  The results are as follows:

ragweed@ragweed-den:/usr/lib/geneweb$ cd /home/ragweed/user/lib/geneweb/gw/doc/index.htm
bash: cd: /home/ragweed/user/lib/geneweb/gw/doc/index.htm: No such file or directory
ragweed@ragweed-den:/usr/lib/geneweb$ 

I suppose I got bashed on that one.

---

### Post by drs305 on 2008-05-31
I just finished expanding my previous post. Check post #4. If you still have questions let us know.

Good luck.

---

### Post by enderwig on 2008-05-31
In firefox, go to File, Open File and navigate to /home/ragweed/user/lib/geneweb/gw/doc/index.htm

That should open the htm file in firefox

---

### Post by Ragweed on 2008-05-31
I went to the folder and found only two files:

     gwd.wrapper
     gwsetup.wrapper

That's it.  Nothing more.  Where do I look now?

Should I attempt a reinstalation?

---

### Post by mmb1 on 2008-05-31
Try running it through the terminal by typing "geneweb" just to see if it actually **is** installed.

---

### Post by enderwig on 2008-05-31
> **Ragweed said:**
> I used the directions [I think] which you'd given.  The results are as follows:

ragweed@ragweed-den:/usr/lib/geneweb$ cd /home/ragweed/user/lib/geneweb/gw/doc/index.htm
bash: cd: /home/ragweed/user/lib/geneweb/gw/doc/index.htm: No such file or directory
ragweed@ragweed-den:/usr/lib/geneweb$ 

I suppose I got bashed on that one.

I think there may be an error in the path above.  Are you sure that it is /home/ragweed/user/lib/geneweb/gw/doc/index.htm

or should it be just /usr/lib/geneweb/gw/doc/index.htm
??

---

### Post by drs305 on 2008-05-31
> **Ragweed said:**
> I went to the folder and found only two files:

     gwd.wrapper
     gwsetup.wrapper

That's it.  Nothing more.  Where do I look now?

Should I attempt a reinstalation?

Did you try to type this in your internet browser. It will take you to their site where it may give you more instructions. The actual web site address is in the lower corner of the page this link opens. The above will actually not take you to the internet but a stored page on your computer.
```
file:///usr/share/doc/geneweb/index.htm
```

If you need more help please send me a PM or come back here.

---

### Post by drs305 on 2008-05-31
> **mmb1 said:**
> Try running it through the terminal by typing "geneweb" just to see if it actually **is** installed.


It doesn't run via terminal. I'm trying to sort this out for him. Files are installed on the computer but it looks like after that more compilation is required. I think I dealt with this program with someone a year or two ago and it was a mess.

If I can figure it out I'll post back. Thanks for the input.

---

### Post by cariboo on 2008-05-31
If you used synaptic to install geneweb then open firefox and then click File|open File navigate to /usr/local/doc/geneweb and double click on index.htm. Thats all there is to it. Once it's running just bookmark it.

Jim

---

### Post by drs305 on 2008-05-31
> **cariboo907 said:**
> If you used synaptic to install geneweb then open firefox and then click File|open File navigate to /usr/local/doc/geneweb and double click on index.htm. Thats all there is to it. Once it's running just bookmark it.

Jim

That's all I can find. I've gone through all the documentation installed via synaptic. The documentation discusses installation with ./gwsetup and other items but none of them were sownloaded to the machine.

So the only option is the link, which hopefully will do what is necessary for Ragweed to run the program.

Jim, if you know any more about the program I hope you will help Ragweed should he have any more quesitons. Thanks to all.

---

### Post by mmb1 on 2008-05-31
> **drs305 said:**
> It doesn't run via terminal. I'm trying to sort this out for him. Files are installed on the computer but it looks like after that more compilation is required. I think I dealt with this program with someone a year or two ago and it was a mess.

If I can figure it out I'll post back. Thanks for the input.


Sorry, my bad guys.  :oops:

---

### Post by Ragweed on 2008-05-31
I'm not sure I did this right, but I did "sudo xterm" and it took me to "root" where I can't seem to do much.

---

### Post by drs305 on 2008-05-31
> **mmb1 said:**
> Sorry, my bad guys.  :oops:


Hey, no problem. The documentation isn't your fault. Hopefully you'll get the thing running online. It may even be an online installation. Best of luck.

---

### Post by Ragweed on 2008-05-31
I found this on the htm page:

"if you installed GeneWeb under Unix or Linux by another method, you can launch gwsetup just by typing "./gwsetup" in an xterm."

Now I'm asking....   what's an xterm?  Boy oh boy, never a dull moment with linux.  But I LOVE the challenge.  It's a lot like old DOS....

Joseph

---

### Post by drs305 on 2008-05-31
> **Ragweed said:**
> I found this on the htm page:

"if you installed GeneWeb under Unix or Linux by another method, you can launch gwsetup just by typing "./gwsetup" in an xterm."

Now I'm asking....   what's an xterm?  Boy oh boy, never a dull moment with linux.  But I LOVE the challenge.  It's a lot like old DOS....

Joseph

They are talking about a terminal.  I've already uninstalled geneweb so I can't look again. I did read that in the doc folders but never found the files to install it. Normally when you compile a program there is a folder you extract that has the installation files. You move into that folder and then you compile it. In this case, there is probably SUPPOSED to be a script or installation file so that when you run gwsetup the program is installed. I couldn't find any such files or folders on the computer. That's when I uninstalled it via synaptic. :(

---

### Post by Unix_Slayer on 2008-05-31
> **Ragweed said:**
> I found this on the htm page:

"if you installed GeneWeb under Unix or Linux by another method, you can launch gwsetup just by typing "./gwsetup" in an xterm."

Now I'm asking....   what's an xterm?  Boy oh boy, never a dull moment with linux.  But I LOVE the challenge.  It's a lot like old DOS....

Joseph

Everyone might not be using the same x11, but it's in _**System**_ on your start menu. You'll see **_Terminal_** **_Program_**.

---

### Post by Ragweed on 2008-05-31
I have only one terminal and that's in "Applications/Accessories"

---

### Post by Unix_Slayer on 2008-05-31
> **Ragweed said:**
> I have only one terminal and that's in "Applications/Accessories"


There ya go. That's what you are looking for.

---

### Post by drs305 on 2008-05-31
This thing is driving me nuts, so I installed it again. It turns out gwsetup is a separate install via synaptic. It wasn't installed with the geneweb app, which is why there were not any files to run. You probably have to install gwsetup to get this thing running on your computer - without it you might be able to use databases stored on the internet (and perhaps other people's computers).

This app looks like a terminal program which doesn't really have a computer-based gui interface. You have the terminal database and the internet interface. I'm not really familiar with these kinds of apps.

---

### Post by Ragweed on 2008-06-01
I'd already tried the "Terminal" but to no avail.  It says to just run "./gwsetup" but it doesn't say where.  Seems they should give that instruction for novices.  It should be in the default folder, but no where have I found where that default folder is.  I HAVE found several folders with packages in which apparently needs unpacked, but no where have I found a "gwsetup" EXCEPT in the "/usr/bin/gwsetup"....    

However, while I can migrate to that one in the file browser, and the gwsetup file is there, When I use the terminal, I get the following:

ragweed@ragweed-den:/usr$ whereis gwsetup
gwsetup: /usr/bin/gwsetup
ragweed@ragweed-den:~$ cd /usr
ragweed@ragweed-den:/usr$ cd/bin
bash: cd/bin: No such file or directory
ragweed@ragweed-den:/usr$ cd usr/bin
bash: cd: usr/bin: No such file or directory
ragweed@ragweed-den:/usr$ ./gwsetup
bash: ./gwsetup: No such file or directory
ragweed@ragweed-den:/usr$

I've tried everything I know of to do....   That's why I'm here.

Joseph

---

### Post by Ragweed on 2008-06-01
Oh yes, drs305, I had already downloaded all four of those files that were there (just in case), and even after doing that and trying all I did above, none of my attempts have worked.  I must be missing something....   but I can't figure out what.

Joseph

---

### Post by drs305 on 2008-06-01
I've done some more looking around and this is what I've found. The geneweb program IS installed (after also installing gwsetup). I did a search and there are several listings in /etc/init.d, which means the app is being started during boot.

So, next refer to the instructions at /usr/share/doc/geneweb/en/start.htm  To open it in a browser, the address should be file:////usr/share/doc/geneweb/en/start.htm or you can browse to it. The instructions on that page serve as a reference for what I've written below. **Bold** items are those that you will need to change.

Open a normal terminal. To open an xterminal, type :
```
xterm
```

_All the following commands are typed in the xterminal._

Create a database directory and file. 
First, make a directory where you want to store the files (example)
```
mkdir **/home/username/my-geneweb**
```

Next, create a database. Type this in the xterm:
```
gwc -o **/home/username/my-geneweb/filename**
```

Start the geneweb daemon, with the path to the database:
```
gwd -bd **/home/username/my-geneweb**
```

Once the daemon starts, you should see several IP addresses, such as [http://127.0.1.1:2317/base](http://127.0.1.1:2317/base)

Open a browser window and type one of the addresses displayed. Replace the word **base** with the name of your database:
```
In the browser window: http://127.0.1.1:2317:**filename**
```

That should open your database in your internet browser and you are good to go.

Note: to kill the daemon, CTRL-C, close the xterminal, or try 'killall gwd'.

If you get GeneWeb working, please mark this thread solved. I won't be able to answers about the specifics of running the databases but I will monitor the thread for a few days if you have any problems with the setup.

---

### Post by gordon3913 on 2009-01-20
A friend of mine installed Geneweb on Suse without any trouble.
Why can't Ubuntu do the same?

The directions for use page:-
file:///usr/share/doc/geneweb/en/diruse.htm

This just confuses people more as they try the different links without any success.

A lot more people would use Ubuntu if there was a user friendly genealogy program available.

---

### Post by flamboyant on 2009-02-10
> **drs305 said:**
> ... The geneweb program IS installed (after also installing gwsetup) ...

Open a normal terminal. To open an xterminal, type :
```
xterm
```

_All the following commands are typed in the xterminal._

Create a database directory and file. 
First, make a directory where you want to store the files (example)
```
mkdir **/home/username/my-geneweb**
```

Next, create a database. Type this in the xterm:
```
gwc -o **/home/username/my-geneweb/filename**
```

Start the geneweb daemon, with the path to the database:
```
gwd -bd **/home/username/my-geneweb**
```

Once the daemon starts, you should see several IP addresses, such as [http://127.0.1.1:2317/base](http://127.0.1.1:2317/base)

Open a browser window and type one of the addresses displayed. Replace the word **base** with the name of your database:
```
In the browser window: http://127.0.1.1:2317:**filename**
```

Note: to kill the daemon, CTRL-C, close the xterminal, or try 'killall gwd'.

If you get GeneWeb working, please mark this thread solved
drs305 :KS
SOLVED
another way to do just the same:
(change *username* with your username, and *database* with the name of your database)
```
mkdir /home/*username*/my-geneweb
cd /home/*username*/my-geneweb
gwc -o *database*
gwd
```
and open the address in a browser: [http://localhost:2317/](http://localhost:2317/)*database*
it just worked for me in Kubuntu

---

