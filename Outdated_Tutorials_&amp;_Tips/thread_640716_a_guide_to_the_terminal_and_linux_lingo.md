---
title: "a guide to the terminal and linux lingo"
date: 2007-12-14
forum: Outdated Tutorials &amp; Tips
---

### Post by antisocialist on 2007-12-14
ok, i have written a guide to the terminal and common words phrases acronyms etc that new users may not know

If there is a specific command you are looking for, type ctrl+f and type it in. if no results are found, post the command you are looking for and i will try to add it as soon as i can

If you have any questions for me, please ask.
If you feel my guide is missing something, feel free to tell me and I will add it as soon as i can, if after a couple days i still havent added it just email me at [email]1337chillax@gmail.com[/email]

and now for the guide...
**[CENTER]Intro[/CENTER]**
If you are like most new people, then you are scared of the terminal. this is ok, its normal. the reason we have the terminal is because it is much easier to help someone by telling them to copy and paste some text into the terminal than it is to say "ok first you click system, then preferences, then you click the one towards the top of the list that says blahblahblah".

**common terminal commands and what they mean, and underneath a short description**

**rm**= remove
this is a potetially dangerous command, as you have probably seen in many forum members signatures, and if you read the announcement. if you haven't read the announcement I highly suggest you read it, it can be found via the link below
[http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73)
also, please note that this command will delete things WITHOUT confirmation, therefore a small typo could end up deleting vital files, especially if you are root when you run the command  

**sudo**= super user (root) do
while this command is essentially useful, when used with potentially malicious commands it can be very dangerous.  sudo allows commands to be executed as root, root in linux is basically what an administrator in windows is, however root can do ANYTHING, thus making sudo a command that must be used only if you can trust the person who told you the code, or you have used the same or a similar code before.  in most cases where you dont understand a command you should wait for another user to post the same thing verifying that the command is indeed safe.

**gksudo**= graphical super user (root) do
This command is basically the same as sudo, but rather than being meant for text it is meant for graphical user interfaces, or GUI's

**chmod +x**= change mode + make executable
this command is used to make files you download from the internet executable, such as .run or .bin files
**aptitude**/**apt-get**=retrieve and use package(s)
a standard aptitude/apt-get command would be
```
sudo aptitude install PROGRAM-NAME
```
in order for an aptitude code to work you must have sudo at the front, because programs are installed in a directory (location) that only root can write in.  aptitude/apt-get is used for mainly for installing and uninstalling programs.

**cd**= change directory
this one is pretty straightforward, the terminal executes commands from /home/USER when opened but can execute from other places using the cd command.
```
cd ~/Desktop
``` would change the terminal working directory to the user desktop with ~ being /home/USER
this command is commonly used for installing programs from the source code

**cp**= copy file or directory
this command can be used to copy files or directories from one place on your computer to another. it will leave the original file or directory where it is and also make a new one somewhere else that is exactly the same
```
cp /home/USER/documents/file1.odt /home/USER/documents/something/file1.odt
```
that would copy the file file1.odt from documents to documents/something

**mv**= move
same as cp (above) but doesn't leave the file where it was originally

**find**= find
this command will search for a file name in directories, sub directories etc of the parent directory you give it
```
find file /
```
would find anything named file in the parent directory / (entire computer)

**df -h**= hd space free&used in human readable format
easy command to remember, tells you in an easy to understand way about your hard drives and storage

**ls**= /home/user directories
tells you the directories of /home/user

**ls -a**= /home/user all directories
shows you your directories in /home/user including hidden folders

**program names**
typing a program name in the terminal, such as firefox, will simply run the program from the terminal, if you close the terminal, you will also close the program.

**killall**= kill all related
this command will stop the program it is addressing, for example the code:
```
killall firefox-bin
```
would kill all open firefox windows, including the downloads window, the addons window, and the web browser itself
~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~

Common Ubuntu and Linux terminology, EXPLAINED

this part of my guide will explain some commonly use acronyms and short forms of words.

cmd= command

tar= tarball archive
a tarball archive is like a zip archive, same files just a less memory consuming version

command line= terminal
it can be found at applications>accessories>terminal
it is the text based version of most other things, from it you can install programs, run programs, uninstall programs, among many, many other thing

window manager
by default this is metacity. basically this controls the top of the window, or the window bar, where the close maximize and minimize buttons are. it also controls the scrollbar, sometimes it will control text entry boxes, and text but sometimes it won't.

compiz
compiz is a special fx program. if you have heard of the cube, this is how it is done. in order to use compiz you are suppose to have a good graphics card like nvidia or ATI but I can run it pretty well with onboard graphics. i have pretty good onboard graphics though. some good videos of compiz in use can be found on youtube.


emerald
another window manager. does the same things metacity does.

gfx
gfx simply is a shorter way to say graphics. im sure you already knew that, but im also sure there are a few people that didn't know.

root/superuser
root, or superuser is basically an administrator, they can do anything on the computer.
~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~*~

if you want anything added post so below, and also you can email me

---

### Post by jenkinbr on 2007-12-14
Just needed to know the difference between sudo and gksudo.  Your post answered my question short and to the point, very helpful, thank you.

Perhaps you could add the following commands:
**cp**: copy file/directory
**mv**: move file/directory

---

### Post by antisocialist on 2007-12-14
yup, ill add them, and im glad I could help you :)

EDIT: done

---

### Post by grim192 on 2007-12-14
how do you search for files ?

grim

---

### Post by Duck2006 on 2007-12-14
Nice post thanks

---

### Post by antisocialist on 2007-12-14
idk a terminal cmd to search for files but if you are using gutsy then on your top panel there will be an icon that looks like a magnifying glass with an orange arrow coming from it. click it and it will let you search for things. if you dont have it on your panel you can add it by right-clicking the panel and selecting add to panel. in the new window that opens up the third icon on the top row from left to right, (it will be called deskbar) is the search thing. click it and it will be added to your panel. once you have it you can click it any time you want to search for something

> **Duck2006 said:**
> Nice post thanks
no problem, my goal with this is to make a wiki-like document so that new people wont have to have as much fun as i did searching google for what commands mean

---

### Post by cyclefiend2000 on 2007-12-14
> **grim192 said:**
> how do you search for files ?

grim

find
[http://www.ss64.com/bash/find.html](http://www.ss64.com/bash/find.html)

edit: or ls
[http://www.ss64.com/bash/ls.html](http://www.ss64.com/bash/ls.html)

---

### Post by antisocialist on 2007-12-14
if you dont know where it is and the search directory has to be / that will takes a long time.

however, it does work, and i will add the cmd find to my list of cmd's

EDIT: i tried find on a file called new file (my guide) in the directory / and it didnt find it
said no files named new or file where found, so it doesnt work with files with spaces in the name

---

### Post by syväpaahto on 2007-12-15
How about in addition posting small tips like:

if you want to copy files
important_file_with_a_long_name_31499
important_file_with_a_long_name_31464
important_file_with_a_long_name_31414
important_file_with_a_long_name_31448
to new location...

instead of writing
cp important_file_with_a_long_name_31499 /new/path/
cp important_file_with_a_long_name_31464 /new/path/
cp important_file_with_a_long_name_31414 /new/path/
cp important_file_with_a_long_name_31448 /new/path/

you can write
cp important_file_with_a_long_name_314{99,64,14,48} /new/path/

Stupidly simple for advanced user, but gold for terminal-noobies, that haven't yet stumbled in to it.

---

### Post by kkkkdddd on 2007-12-15
I have many files in a directory and I want to copy all of them expect one(./unnecessary_file) to another directory.

Is tere any better solution then:
cp * /new/path/
rm /new/path/unnecessary_file
or
cp $(echo *|sed "s/ /\n/g"|grep -v unnecessary_file) /new/path/
?

I would like to write something like  cp * - ./unnecessary_file /new/path/

---

### Post by Neon Lights on 2007-12-15
compiz is the window manager, emerald is just a window decorator for it. ;] Nice guide though.

---

### Post by of_darkness on 2007-12-15
Maybe add kdesudo for all kde users? like 
> gksudo= graphical super user (root) {for gnome users(ubuntu) - kde users(kubuntu) type kdesudo insted} 

---

### Post by of_darkness on 2007-12-15
> ls= /home/user directories
 tells you the directories of /home/user
 
 ls -a= /home/user all directories
 shows you your directories in /home/user including hidden folders
 


Could be a bit confusing..

perhaps change it 2 somthing like this

> ls = lists all non hidden files in the working directory
example -to list the files and folders in your home folder type
[QUOTE]ls 
and it tells you the files and directories of /home/-your username eg /home/peter
 
 ls -a= lists all  files and directorys in the working directory
> ls -a
shows you your files and directories in your home folder including hidden folders and files (those files and folders that bigin whit  a dash eg > .kde
 
[/QUOTE]

and also add before the comand listing
> Working directory = the folder where you are at the moment - you can type [QUOTE]pwdto se where you are > [ blutengel: ~/Desktop ]$ pwd
/home/blutengel/Desktop and in this example im in my Desktop folder and it is my working directory][/QUOTE]

---

### Post by antisocialist on 2007-12-16
> **of_darkness said:**
> Maybe add kdesudo for all kde users? like

while that is a good and valid point, this is the _ubuntu_ forums, not the kubuntu forums

---

### Post by jingo811 on 2007-12-16
anti try to divide your guide in different sections (somehow) to make it easier for newbies to digest and follow.  
Or you could make the commands in alphabetical order but that's boring it has already been done else where.
These kind of guides tend to grow pretty big with time which makes newbies information overload pretty fast.

```
Too much information is like having no information at all.
```

Aside from that little pointer, nice initiative by doing this guide.

---

### Post by antisocialist on 2007-12-16
whats the point of alphabetizing, that would put the most used or most important to know cmds at the bottom (rm, sudo) and put some less important cmds at the top.

im all for rearranging it, but not alphabetically. even if they are a newbie, they should know ctrl+f to find what they want, and i put at the top to type ctrl+f and type the cmd they want if they want a specific one.

also, im not adding every cmd i know, just the most useful and commonly used ones, for this reason i did not add kdesudo to the list, because the majority of users wont need this.

i added less used cmds like df -h because they can be really useful

---

### Post by phelin4 on 2007-12-16
> **antisocialist said:**
> EDIT: i tried find on a file called new file (my guide) in the directory / and it didnt find it
said no files named new or file where found, so it doesnt work with files with spaces in the name

Yes it does. Try something like this:

```
 find / -name "new file"
```

---

### Post by tuproxy on 2007-12-16
Great posting!  I'm in the process of doing something similar, but will be more along the lines of new installation techniques..

Anyway, you might want to add the "tab" function when you are tyoing filenames or directories.  If you don't know what I'm talking about I'll explain.

If you type LS and get  a list of files and directories . Let's say that you have a file called:
 ABC1_New_Linux_Image_That_Has_A_LONG_Filename.ISO
 ABC2_New_Linux_Image_That_Has_A_LONG_Filename.ISO
 ABC3_New_Linux_Image_That_Has_A_LONG_Filename.ISO

Now if you type ABC1 in the CL and then press tab, it will pull up the full filename!  This saves a lot of time when typing..

Also if you want to change dir, like to /home/UbuntuUser/Desktop/New_Videos_Downloaded

That's  alot totpe out, so do this:
/ h (tab) U (tab) D (tab) N (tab)

That should bring up the directory that you want.

If there are other files or folders, like the ABC files above, it will not pull them up.  Try it out and see how it works.

---

### Post by tuproxy on 2007-12-16
If people want to learn most of the commands, check this book out on Google Books. It's the best book i've found for Linux Commands

[Linux PhraseBook on Google]("http://books.google.com/books?id=3w4sjblXbjwC&dq=linux+phrasebook&pg=PP1&ots=F7VHWhIpqT&sig=xUjHkwmMPvsZ76l0T80dbR1WxN4&prev=http://www.google.com/search?q=linux+phrasebook&ie=utf-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&sa=X&oi=print&ct=title&cad=one-book-with-thumbnail&hl=en")

---

### Post by antisocialist on 2007-12-16
if you have a filename that long for a linux disc iso you should rename it to
```
distroname-version
```
for example instead of something like
modified-debian-etch-from-debian-mods.org.iso
they should rename it to
debian-etch-mod.iso
as it would take out most of the stuff in the first one and stil supply most of the info.

i will try your thing with tab though

---

### Post by of_darkness on 2007-12-16
> **antisocialist said:**
> while that is a good and valid point, this is the _ubuntu_ forums, not the kubuntu forums
This is the forum for all *ubuntu flavors.. so it is a varry much valid point..

---

### Post by quanumphaze on 2007-12-18
It would be also good to add that **mv** can also used to rename files.
Also that you have to use '\' (back slash) to put characters with special meanings like whitespace in the terminal.
```
mv file\ with\ a\ really\ long\ name ./smallname
```

---

### Post by Lostincyberspace on 2007-12-18
This is a really good how-to keep up the good work. You might add some thing about ```
..
``` and the rest of the dot structure

---

### Post by PreviousN on 2007-12-19
Is it just me, but I always use locate when trying to find something. Here's the syntax:

locate [options][file]

so, "locate stuff" would find all your stuff. I'm pretty sure this uses a database backend and its really a lot faster than find.

---

### Post by phelin4 on 2007-12-19
> **PreviousN said:**
> Is it just me, but I always use locate when trying to find something. Here's the syntax:

locate [options][file]

so, "locate stuff" would find all your stuff. I'm pretty sure this uses a database backend and its really a lot faster than find.

It is true that locate is quite useful for everyday use. But find is in a different league when scripting or if one just needs to use other attributes than the name of the file. Find can for example be used to search for files that have been modified at a certain time, belong to a certain user etc

Locate is also unable to handle files created too recently:

$ touch test.test
$ locate test.test
$ find . -name test.test
./test.test

---

### Post by phelin4 on 2007-12-19
> **quanumphaze said:**
> It would be also good to add that **mv** can also used to rename files.
Also that you have to use '\' (back slash) to put characters with special meanings like whitespace in the terminal.
```
mv file\ with\ a\ really\ long\ name ./smallname
```

If the file name contains several whitespace characters, it might be easier to put the name in quotes.

---

### Post by antisocialist on 2008-01-01
bump

---

### Post by antisocialist on 2008-01-16
***UPDATED***

now includes chmod +x in the cmd's section

---

### Post by antisocialist on 2008-01-29
> **PreviousN said:**
> Is it just me, but I always use locate when trying to find something. Here's the syntax:

locate [options][file]

so, "locate stuff" would find all your stuff. I'm pretty sure this uses a database backend and its really a lot faster than find.meh, sounds complicated, find is easier

> **phelin4 said:**
> It is true that locate is quite useful for everyday use. But find is in a different league when scripting or if one just needs to use other attributes than the name of the file. Find can for example be used to search for files that have been modified at a certain time, belong to a certain user etc

Locate is also unable to handle files created too recently:

$ touch test.test
$ locate test.test
$ find . -name test.test
./test.test

i use Google desktop, it has completely databased my entire harddrive and now all i have to to do is hit a keystroke and type what i want and it finds it for me, instantly

---

### Post by thyultimate on 2008-03-03
Correct me if I am wrong, but I thought that apt-get and aptitude were different commands....I mean I thought they did things slightly differently

I am pretty sure I read that somewhere.....

---

### Post by SOULRiDER on 2008-03-03
> **of_darkness said:**
> Maybe add kdesudo for all kde users? like

Its kdesu and not kdesudo and I too feel it should be added.

---

### Post by antisocialist on 2008-03-03
> **thyultimate said:**
> Correct me if I am wrong, but I thought that apt-get and aptitude were different commands....I mean I thought they did things slightly differently

I am pretty sure I read that somewhere.....

technically, they are different, apt-get is only for installing and uninstalling packages, where as aptitude can do much more. aptitude can be used in place of all of the following and possibly more (correct me if i am wrong)
apt-get
apt-cache
however, the outcome of
apt-get moo
is different from 
aptitude moo
i believe

---

### Post by antisocialist on 2008-03-03
> **SOULRiDER said:**
> Its kdesu and not kdesudo and I too feel it should be added.

i would add commands for kde, but not only will the bulk of new users (targets of this guide)  not need it, but i do not use kde so i can't be sure of a command, if you would like to get me a citation then i will consider adding it.

---

### Post by myusername on 2008-03-19
ok this is a thread about terminal commands that you will occasionaly see in ubuntu (or any other linux distro for that matter)

here is the format of this thread
command - what it does

cd - cd stands for CHANGE DIRECTORY or go to this folder...e.g. cd /home/username/Desktop

ls - ls is used with something else to list what is connected e.g. lsusb will show all of you usb ports and whats connected

./ - usally to install whats in the directory that you're in e.g. cd /home/user/Desktop/wireless card ./wireless

sudo - stands for SUPER USER DO and it is used for administrato applications or commands

apt-get - to install or remove something with the terminal e.g. sudoi apt-get banshee or sudo apt-get remove banshee

aptitude - same thing as apt-get e.g sudo apttitude install banshee

nano (or kate) - to edit a file with the terminal e.g. sudo nano /etc/hosts

ifconfig - lists all of your network cards e.g. ifconfig

iwconfig - lists all of your wireless cards e.g. iwconfig


i know there are plenty more commands and i will be editing this when i remember them all

feel free to contribute commands that i missed or corrections to commands

sticky anyone?

---

### Post by SOULRiDER on 2008-03-19
Im sure there was somethign like this at the cafe, or maybe the tutorial section. Ill post the link as soon as I find it again.

---

### Post by SOULRiDER on 2008-03-19
Here it is, it was easy to find :) [http://ubuntuforums.org/showthread.php?t=640716](http://ubuntuforums.org/showthread.php?t=640716)

---

### Post by SOULRiDER on 2008-03-19
> **thyultimate said:**
> Correct me if I am wrong, but I thought that apt-get and aptitude were different commands....I mean I thought they did things slightly differently

I am pretty sure I read that somewhere.....

They are, and even if they do the same, aptitude handles dependencies better. Aptitude should be used over apt-get.


gksudo should be fixed, its gksu. Also, ls lists directories AND files, not just directories.

---

### Post by antisocialist on 2008-03-19
> **SOULRiDER said:**
> They are, and even if they do the same, aptitude handles dependencies better. Aptitude should be used over apt-get.
already said that
> 
gksudo should be fixed, its gksu.not in ubuntu it isnt, its gksudo>  Also, ls lists directories AND files, not just directories.

thanks for the correction

---

### Post by bodhi.zazen on 2008-03-19
Threads merged.

gksudo is a link to gksu :

> lrwxrwxrwx  1 root   root        4 2007-11-05 01:19 gksudo -> gksu

---

### Post by Lorry ZA on 2008-05-31
Thanks man, very informative and it really helped me to start getting to know the terminal.

I must say was always scared by the thought linux distros because of the terminal use but been using Hardy for a month now and am starting to get the hang of it i hope.

Thanks again:)

---

### Post by antisocialist on 2008-05-31
> **Lorry ZA said:**
> Thanks man, very informative and it really helped me to start getting to know the terminal.

I must say was always scared by the thought linux distros because of the terminal use but been using Hardy for a month now and am starting to get the hang of it i hope.

Thanks again:)

your welcome, thanks for the positive feedback :)
i tried hardy and it makes my computer run slower then a slug :\

---

### Post by brit0n on 2008-05-31
Thanks for starting this guide. It is a great pity that so many responses include stuff that a newbie won't have a clue about and which the thread itself won't explain. For example, "CL" is mentioned in a post but not explained.

One thing I would like to see is a simple list of commands to allow someone to "browse" to find out what they have connected so that they can "cd" to them. And isn't there a way to change drives so that you can "browse" a different partition?

Case in point, my Ubuntu won't start and I know why, but I am stuck at a command prompt (obviously?)

I need to install a new driver which I have downloaded in another OS and stuck in two places one of which (at least) I ought to be able to "cd" to - a directory on a USB stick and on the root of a non-OS hard drive partition. Note, no need to go into the network or DVD/CD drives. Your guide doesn't include enough commands for me to find out what partitions I can get to, what they are called and how to change to them. It then doesn't tell me how to list the directories in that drive so that I can usefully use "cd" ("ls" says it only lists /home/user directories and I would think that I didn't have access to that in the other OS when I copied the file to those two places).

So could I ask you to try to forget everything you know, imagine you are stuck not being able to boot, know what to do and which commands to type to install the required driver but you simply can't "cd" to where the file is because you don't know the commands to find out what to "cd" to? That would be VERY helpful to a new user and would probably stop us having to ask so many dumb questions on the forums cos we could try to fix problems ourselves more easily!

---

### Post by antisocialist on 2008-05-31
> That would be VERY helpful to a new user and would probably stop us having to ask so many dumb questions on the forums cos we could try to fix problems ourselves more easily!

the problem with that is most new users dont bother searching, they just ask.

also, this guide is aimed at being for the greatest amount of users. most users will not have that problem, and if they do they will find a guide specifically on that. since i want my guide to be as short and to the point as possible i want it to be able to apply completely to every new user, not have some parts specifically for a small group of users.

---

### Post by brit0n on 2008-05-31
OK that works. Thanks anti.

That being the case, might I suggest you put a link to Tuxfiles in your original post? Some new users DO try to find out first (how did I end up here lol) and this would point them to some useful reading which would quickly bring them to a faster speed even though not up to speed.

Example:

[B]This guide is aimed at being the greatest help for the greatest number of users. If you are a new user who needs a more detailed explanation of the command line interface and commands, the following link is a worthwhile starting point without requiring hours of reading:

[INDENT][tuxfiles: An introduction to the Linux command line]("http://www.tuxfiles.org/linuxhelp/cli.html")[/INDENT][/B]

Great thread, anti.

---

### Post by holiday on 2008-05-31
When the hell you ever want to do that, kkk? There's a story there.

I'd like to know how to cp only today's files from one directory to another. That's easy in nautilus, but I want to do it in the terminal.

---

### Post by antisocialist on 2008-05-31
> **holiday said:**
> When the hell you ever want to do that, kkk? There's a story there.

I'd like to know how to cp only today's files from one directory to another. That's easy in nautilus, but I want to do it in the terminal.

but a noob would want to use the GUI whenever possible.

---

### Post by nomnex on 2009-10-07
> **tuproxy said:**
> If people want to learn most of the commands, check this book out on Google Books. It's the best book i've found for Linux Commands

[Linux PhraseBook on Google]("http://books.google.com/books?id=3w4sjblXbjwC&dq=linux+phrasebook&pg=PP1&ots=F7VHWhIpqT&sig=xUjHkwmMPvsZ76l0T80dbR1WxN4&prev=http://www.google.com/search?q=linux+phrasebook&ie=utf-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&sa=X&oi=print&ct=title&cad=one-book-with-thumbnail&hl=en")

Indeed! Thank you for the tip

---

