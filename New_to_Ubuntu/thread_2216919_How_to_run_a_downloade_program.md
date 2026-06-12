---
title: "|How to run a downloade program?"
date: 2014-04-14
forum: New to Ubuntu
---

### Post by thevenerable2 on 2014-04-14
[http://rootzwiki.com/topic/38786-tpdebrick-v004/](http://rootzwiki.com/topic/38786-tpdebrick-v004/)

I downloaded the two programe from there, but when i type the commands it tells me to type in the terminal, i get errors
im running lubuntu

i just want to unzip or run these two programs

please tell me how,  as usual, linux makes it sop hard just to run a program

thanks

---

### Post by thevenerable2 on 2014-04-14
please can someone just give me step by step instructions how to unzip and run there??

i just cant understand the googled tips i tried to look for, they are madly complicated.

''
The first thing you need to do is extracting it in a folder, let's  make it your desktop. You can extract an archive right clicking on it  and choosing the appropriate entry. It should create a new folder with a similar name, e.g. *program-1.2.3*. Now you need to open your terminal and then go to that directory:
  cd /home/yourusername/Desktop/program-1.2.3
  Make sure you first read a file called *INSTALL* or *INSTALL.txt* or *README*. Check if there is any of these files with the *ls* command, and then display the right one with:
  xdg-open INSTALL
  The file will contain the right indications to go on with the compiling process. Usually the three "classical" steps are:
  ./configure
make
sudo make install
''

all that and more just to install a downloaded file??

please give me a solution, i cannot work with this system

---

### Post by sandyd on 2014-04-14
> **thevenerable2 said:**
> [http://rootzwiki.com/topic/38786-tpdebrick-v004/](http://rootzwiki.com/topic/38786-tpdebrick-v004/)

I downloaded the two programe from there, but when i type the commands it tells me to type in the terminal, i get errors
im running lubuntu

i just want to unzip or run these two programs

please tell me how,  as usual, linux makes it sop hard just to run a program

thanks

Hi, what errors do you get - and what commands produce errors?

---

### Post by thevenerable2 on 2014-04-14
Hi

i am told by tjhe guide to type this:
 Run "cd Downloads"
Run "unzip tpdebrick-v004"
Run "cd tpdebrick-v004"

each one produces this result:
'Run: command not found'

maybe im typing them in wrong
i am copying and pasting them
please tell me how to open these dowloaded files properly or i will uninstall ;linux

this is the first time ive tried to actually do something productive on it and i am stuck already, i cant even run a downloaded file for gods sake.
i have really had enough

Dear linux, please learn how to use mouse clicks to unzip and install software. its really great & will bring you into at least the 1990's

---

### Post by Elfy on 2014-04-14
>  Dear linux, please learn how to use mouse clicks to unzip and install software. its really great & will bring you into at least the 1990's works like that for me - what do you get if you right click?

 'Run: command not found'

Run isn't a command

try 

```
cd Downloads
```

---

### Post by monkeybrain20122 on 2014-04-14
Well you can just unzip it by right clicking and choose 'extract here', this will create a folder tpdebrick-v004 in Downloads.
Then open a terminal and type
```
cd Downloads/tpdebrick-v004
```
cd means change directory. Now you are in the directory ~/Downloads/tpdebrick-v004
"~/" means /home/username, since you start the terminal in your home all that can be omitted and you entered only "Downloads/tpdebrick-v004" in the terminal.

After getting into the tpdebrick-v004 directory you will have to do other things, maybe to run a install script, or to build from source, or maybe just as simple as running a precompiled binary. It depends on the software.

---

### Post by thevenerable2 on 2014-04-14
When i right click on th edownload files i get options ' open containing foler etc'
i have no idea whereto unzip them too, or how to run it even if i could unzip it.

I managed to run the script or whatever its called, i didnt know i didnt have to type 'run'

anyway, it didnt work.. and now im trying it again its giving me an error:
cd downloads
bash: cd: downloads: No such file or directory

---

### Post by bapoumba on 2014-04-14
> **thevenerable2 said:**
> When i right click on th edownload files i get options ' open containing foler etc'
i have no idea whereto unzip them too, or how to run it even if i could unzip it.

I managed to run the script or whatever its called, i didnt know i didnt have to type 'run'

anyway, it didnt work.. and now im trying it again its giving me an error:
cd downloads
bash: cd: downloads: No such file or directory

```
cd Downloads
```
with a capital D, we are case sensitive.

---

### Post by Elfy on 2014-04-14
linux is case sensitive

cd Downloads

---

### Post by thevenerable2 on 2014-04-14
i think i got past the stage
but then get this error:

dfu-util not installed
fastboot not installed


If any of you looked at the link i sent regarding the tutorial to debrick my hp touchpad, you will see ive got as far as running thos command, plus the:
22. Run "script" (this will capture the output of the tpdebrick process)
23. Run "sudo ./tpdebrick XX" (where XX is the size of the TP: 16, 32 or 64)

but then i get those errors above

how do i install those missing prgrams please?
I've looked on google but yet again as itas linux and cant do anything the easy way, its more confusing than helpful.

---

### Post by bapoumba on 2014-04-14
> **thevenerable2 said:**
> i think i got past the stage
but then get this error:

dfu-util not installed
fastboot not installed


If any of you looked at the link i sent regarding the tutorial to debrick my hp touchpad, you will see ive got as far as running thos command, plus the:
22. Run "script" (this will capture the output of the tpdebrick process)
23. Run "sudo ./tpdebrick XX" (where XX is the size of the TP: 16, 32 or 64)

but then i get those errors above

how do i install those missing prgrams please?
I've looked on google but yet again as itas linux and cant do anything the easy way, its more confusing than helpful.
[http://rootzwiki.com/topic/36658-tpdebrick-v01/page-48](http://rootzwiki.com/topic/36658-tpdebrick-v01/page-48)

---

### Post by thevenerable2 on 2014-04-14
''I had this issue as well. Open software manager or what ever it is and  go edit and then software sources. The second check box that ends in  "universe" needs to be checked. Then run "sudo apt-get update" and then  "apt-get install dfu-util" and try step 5 again. Also you'll want to  make sure your using a 64 bit version of Ubuntu for a later step.''

how do i open software manager?

and i cant even do this on a 32 bit machien then?

---

### Post by bapoumba on 2014-04-14
> **thevenerable2 said:**
> ''I had this issue as well. Open software manager or what ever it is and  go edit and then software sources. The second check box that ends in  "universe" needs to be checked. Then run "sudo apt-get update" and then  "apt-get install dfu-util" and try step 5 again. Also you'll want to  make sure your using a 64 bit version of Ubuntu for a later step.''

how do i open software manager?

and i cant even do this on a 32 bit machien then?

[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Repositories_in_Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Repositories_in_Ubuntu)

---

### Post by thevenerable2 on 2014-04-14
i told you im on lubuntu

and i dont know where to start with those links you sent me

i am supposed to read an encyclopedia now just to get this done ??
those links are massive. I have to learn all that ??  

links are no good when i cant understand them

please advise me instead.

Anyone ?

---

### Post by thevenerable2 on 2014-04-14
''apt-get install dfu-util
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?''

I CANT do anything else unless you advise me.
I dont understand what part of those links i am even supposed to look at
you cant expect a common person to read through all that lunacy jusy to install something

if you do really expect me to study all that , please re confirm and i will stop even asking for help here
its far to complicerted even with help if thats the case

---

### Post by monkeybrain20122 on 2014-04-14
you need to run apt-get install with root privilege
```
sudo apt-get install dfu-util
```

---

### Post by lisati on 2014-04-14
> **thevenerable2 said:**
> ''apt-get install dfu-util
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?''

Are you running this from the terminal? If so, you might have better results if you use:
```
sudo apt-get install dfu-util
```
You are likely to get asked for your password. Don't worry if your password doesn't show when you type it, this is a normal security precaution.

---

### Post by Elfy on 2014-04-14
I've closed the thread.

You've done little but complain in your threads.

Linux is not windows. 

Everyone here is a volunteer - everyone - there are people wanting help who do not constantly whine about it being easier on windows, if windows is easier for you then use that.

---

