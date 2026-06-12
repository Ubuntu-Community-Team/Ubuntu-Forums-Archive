---
title: "My Script To Get Install Info &amp; Backup Config Files"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by nicedude on 2008-05-13
Hey everyone I thought I should share this with everyone since it is simple and might really help out someone here.

Basically it is a script to get system information like software installed, user name, linux version, PCI devices, USB devices & more then write it all to text files in a new folder on your desktop. Also it will backup 7 of your important config files and place them in a sub folder of the first one on your desktop.

I only use commands that do not require SUDO privileges and so this should be safe for anyone to use as it doesn't change anything apart from making a couple new directories on your Desktop. 

It should come in handy for people who don't know the proper commands yet and also for those who do when they want a bunch of answers really fast.

Anyway try it out and tell me what you think, If anyone can think of some other important config files I should add to my list then just let me know so I can add them.

Just make sure its set to be executable and then doubleclick and select run or add to your nautilus scripts folder.

---

### Post by Bruce M. on 2008-05-13
Nice, really nice.

Thanks for making and sharing it.

Have a nice day
Bruce

---

### Post by Nythain on 2008-05-13
cant wait to get home and try this... if it works out, you have saved me soooooooooo much time... i like to experiment and play around a little more than i should, and as a result, usually end up re-installing about 2-3 times a month :P

thanks much mate

---

### Post by Bruce M. on 2008-05-13
I changed the ~/Desktop/....  to  ~/.....
and created the folders in my /home directory.

Much cleaner that way.
Brilliant file though.

Bruce

---

### Post by Bruce M. on 2008-05-13
@ nicedude:

> Who is depicted in my avatar? If you know your probably pretty cool

Hmmm, not me too much hair.  :)

---

### Post by corkscrew on 2008-05-13
sounds like just what i need as a complete neub to linux, i have it downloaded on my desktop i right clicked selected properties then under permissions put a tick in the execute box. when i double click the file on my desktop nothing happens
what have i missed?

---

### Post by Nythain on 2008-05-13
you could try opening a terminal, cd'ing to where the file is and
./filename.sh
and see what it says if anything... thats about all i got, i dotn usually run scripts from the desktop environment via double click

---

### Post by corkscrew on 2008-05-13
ok tried that and i get this
cem@cem-acer:~$ cd ~/Desktop
cem@cem-acer:~/Desktop$ System Configuration.sh
bash: System: command not found

oh and yes the file is on my desktop

---

### Post by Nythain on 2008-05-13
./System\ Configuration.sh

---

### Post by corkscrew on 2008-05-13
i presume you mean type this? i tried it and it worked i dont understand though, the file name is System Configuration.sh is'nt it? not just Configuration?
what does typing ./ do?

---

### Post by Nythain on 2008-05-13
./ pretty much means execute this file in this directory
System Configuration, the space needs to be escaped or some jazz... thats what preceding \ means, you could also put the filename in quotes, but i prefer to always \ before spaces and special characters

---

### Post by Vivaldi Gloria on 2008-05-13
> **corkscrew said:**
> i presume you mean type this? i tried it and it worked i dont understand though, the file name is System Configuration.sh is'nt it? not just Configuration?
what does typing ./ do?

Type 

```
echo $PATH
```

The answer gives you the places where the commands in your system are automatically known. If you want to run an executable somewhere else then you need to write its path explicetly, e.g.

/where_the_executable_file_is/its_name

And "." means the current directory. So to run a file in the current directory you type

./command

By the way, ".." means the containing directory. So if u are in /x/y/z and type 

```
cd .. 
```

then u goto /x/y.

---

### Post by Vivaldi Gloria on 2008-05-13
On another point,

The names of the directories in ~/ directory are arbitrary. For example, in some (all?) non-english versions of ubuntu, the desktop is NOT called "Desktop".  So the script does not work as is. In general, it is better to use "~/x" rather than "~/Desktop/x" if you are going to put a script on the web because "~/x" is universal. 

Useful script. Thanks for posting it.

---

### Post by nicedude on 2008-05-13
Sorry Vivaldi you are correct about non-english Ubuntu, I am a silly American and we foolishly assume everyone speaks english as we are culturally retarded. So sorry all should have said "Works for english Ubuntu install" sorry for anyone from another country that this confused.

Though as I said this can't do anything to mess up your install so thats why I posted it.

To the person who it didn't work that got the bash command not found type error maybe you don't have bash installed (but it should be I think) , you could try editing file and changing first line from #!/bin/bash to #!/bin/sh instead as it might make it work for you.

Does anyone have any suggestions for any other standard config files I should include it to backup or any other list commands that don't require sudo privaledges to function? If so please PM me or just post em here and I will revise it.

PS I used ~/Desktop/ instead of ~/ (home) since I ment it for anyone no matter how newbie even if they can't find their home directory :-)

I am just learning how to write scripts in bash after years of writing stupid windows batch files so I am learning as well. Hope everyone gets some use from this and feel free to modify it for your situation as you see fit.

---

### Post by nicedude on 2008-05-14
Heres another script to just test out your network setup. It does a ifconfig, iwconfig, lists router table & then pings Google & Yahoo and lists all the results to a text file on your "English Ubuntu" desktop. 

Anyone who's desktop isn't named Desktop will need to change this to what your desktop is called ( I suggest using the replace funtion inside gedit for this as you can just replace ~/Desktop with ~/"whateveryoursiscalled" and click to replace all at once ) 

Here you go :-)

---

### Post by nicedude on 2008-05-14
Here is a version for anyone that wants or needs the information to go to their home folder instead of the desktop, this should fix problems with non english Ubuntu's desktop not being called desktop.


This will do the same thing but place the resulting data into your HOME folder.

---

### Post by HotShotDJ on 2008-05-14
Brilliant!  I would only make one change... rename the script SysConf.sh and place it in /home/USER/bin (this avoids having to escape the space, having to navigate to the proper directory, and having to use the ./ in front of the command)

Of course, if you have to create the /bin directory, you'll have to log out and then back in so that it will be in your PATH.

---

### Post by linuxnovice on 2008-05-14
Hi, great script.

If I may make a suggesstion....I have noticed its kind of difficult to work with folder names which has spaces in Linux esp. on the command line. So maybe you could consider using one word for the folder by perhaps adding and underscore in the middle or something?

Also if it were interactive and asked for making a backup it would nice, since people might be running this script for many times if they have a problem..
Thanks.

---

### Post by cacycleworks on 2008-05-14
> **corkscrew said:**
> i presume you mean type this? i tried it and it worked i dont understand though, the file name is System Configuration.sh is'nt it? not just Configuration?
what does typing ./ do?

./  tells the shell to look in the current directory for the program.

A while back, it became standard practice to remove the current directory, ".", from the path. The premise being a trojan horse could be planted or something... :)

:) Chris

---

### Post by nicedude on 2008-05-15
Just install nautilus scripts and then place this along with other scripts in the nautilus script folder then you can launch anything you want form your right click menu. I currently have Open Nautilus here & same with root - Open selected with gedit & with same with root + lots of program launchers with & without root depending on needed use. Also I wrote one to put my wifi into monitor mode and then launch a kismet server and then client session window for sniffing with one click :-) . So scripts are a wonderful thing I am finding and are allowing me to not have to use the command line and instead live inside GUI's making my Ubuntu work as friendly as any Windows which is a requirement I am trying to achieve so that I can get my friends and family to switch and kick MS off their PC's.

So you can do anything you want with scripts that you can do with a command line. Also if you just plain want to type away to do something and a file has spaces in the name just wrap the filename in "" quotes and it will work for you at the command line and its just two extra charaters to type, which since you want to use the command line anyway should mean two more strokes of joy :-)

Feel free though to just open this up and use gedits replace funtion to replace the destination name with something else and click replace all, then save it and it can send & save the information anywhere you want.

I would like some feedback though on advice for other config files that could be of use to backup with this so I can add them t my script, I think also for in future I might try to make this use a dialog window and give a couple choices on where to send the resulting data ( maybe desktop or home folder ) 

Anyway someone who is super Ubuntu smart please give me ideas for other configuration files that need to be backed up in Ubuntu than the ones I included, I know there have to be others that would be handy to have backed  up.

Heres a script for everyone that is similar to my first, but this one runs ifconfig, iwconfig, lists the current network routing table & then pings Google & Yahoo. It sends all this data to your Desktop into one text file in about 5-10 seconds. once the text is done you can view it to see your current network adapters and route table plus with the ping results you get verification that your internet is working and an idea of the speed at which it is working.

I made 2 versions - Both do the same things only 2nd is for no spaces sent to your home folder. 
First on NeworkTest will name report "My Current Network Setup.txt" & send the report to your desktop.

Second one will make a report called NetInfo ( No Spaces ) and will send it to your home folder instead of the desktop

---

### Post by Camilia on 2008-09-01
> **nicedude said:**
> Hey everyone I thought I should share this with everyone since it is simple and might really help out someone here.

Basically it is a script to get system information like software installed, user name, linux version, PCI devices, USB devices & more then write it all to text files in a new folder on your desktop. Also it will backup 7 of your important config files and place them in a sub folder of the first one on your desktop.

I only use commands that do not require SUDO privileges and so this should be safe for anyone to use as it doesn't change anything apart from making a couple new directories on your Desktop. 

It should come in handy for people who don't know the proper commands yet and also for those who do when they want a bunch of answers really fast.

Anyway try it out and tell me what you think, If anyone can think of some other important config files I should add to my list then just let me know so I can add them.

Just make sure its set to be executable and then doubleclick and select run or add to your nautilus scripts folder.

I double click it saved 1st time, 2nd time click browse. No result either way. Very confused.

---

