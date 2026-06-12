---
title: "Installing sh script in Ubuntu 11.04"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by cdo on 2012-04-24
Not new to Ubuntu but new to 11.04 and having trouble opening and running an sh script . Script comes from a trusted Genealogy source that i deal with and previous softwear has installed and worked fine by using Wine apps. Below is a dialogue with customer support regarding this problem .

[Installing indexing on a Computer with a Linux Operating System   ]("https://help.familysearch.org/publishing/231/111415_f.SAL_Public.html")
( Indexing being a genealogy project involving the public with census data , etc. )

 
FamilySearch does not officially support Linux operating systems with  FamilySearch products. ( Assuming they don't mind the id ) . However, the engineers have created .sh File  Shell Script that installs indexing on computers running Linux with  Firefox.
  To install:
  1. Open a Firefox browser on the Linux desktop.
  2. Browse to [http://indexing.familysearch.org]("http://indexing.familysearch.org/").
  3. Click the **Get Started** link.
4. Click the **here** link  ( there was no here link but the download image below )

5. Save the File in the default downloads directory.




( Updated file shows as 3_13_1.sh )


6. Open a command line or a terminal window.
  7. Change the folder to the Downloads folder by typing **cd Downloads** or to the directory where the .sh file was saved.  ( My downloads normally go to desktop though i also sent to download folder as well ) 

  8. Type **bash Indexing_unix_3_7_11.sh** (remember Linux is case sensitive), and then click **Enter** on the keyboard.
  9. Click **Next**.
  10. Click **Finish**, and log in using the FamilySearch Account or LDS Account.


Terminal: 

To run a command as administrator (user "root"), use "sudo <command>".
alan@alan-desktop:~$ "sudo cd Downloads".
alan@alan-desktop:~$ bash Indexing_unix_3_13_1.sh
bash: Indexing_unix_3_13_1.sh: No such file or directory
alan@alan-desktop:~$ "sudo cd Desktop".
alan@alan-desktop:~$ bash Indexing_unix_3_13_1.sh
bash: Indexing_unix_3_13_1.sh: No such file or directory
alan@alan-desktop:~$ To run a command as administrator (user "root"), use "sudo <command>".
bash: syntax error near unexpected token `('   ( Don't know what this refers too )


If anyone can help me sort through this will be greatly appreciated .


Thanks

---

### Post by cdo on 2012-04-24
Forgot to include step 5 image..

---

### Post by cdo on 2012-04-24
For whatever reason step 5 image of download page does not copy and paste..

---

### Post by oldfred on 2012-04-24
With scripts you need to run as root or as it is saying sudo <command>

I find you can use {tab} to complete a line or fill in unique characters when you have several versions.

sudo bash Ind{tab key} 

If file is in directory then tab will complete it. 

I would look at script to see what it does, although many are over my head, but I try to learn as I go.

---

### Post by robgraves on 2012-04-24
umm, I usually avoid using sudo command unless absolutely necessary i.e. you shouldn't have to prefix "cd Downloads" with sudo.  Also I do not see your prompt change when you change directories, my prompt will change when I change directories:
```

robgraves@ubuntu:~$ pwd
/home/robgraves
robgraves@ubuntu:~$ cd Downloads
robgraves@ubuntu:~/Downloads$ pwd
/home/robgraves/Downloads
robgraves@ubuntu:~/Downloads$ 

```

I would verify that you in fact changed to the proper directory

to amend what i said in conjunction with oldfred, i would change directories without sudo and type "ls" to verify you were in the correct directory and that the file was in fact saved there, also to prefix the command "sudo bash Indexing_unix_3_13_1.sh"

---

### Post by ixtok on 2012-04-24
After changing to a directory ```
ls
``` will list the items there so you can make sure you are in the proper place and have the correct file

---

### Post by cdo on 2012-04-24
Is the pwd the prompt you are referring to as i do not get that...

alan@alan-desktop:~$ cd Downloads
alan@alan-desktop:~/Downloads$ 
alan@alan-desktop:~/Downloads$

---

### Post by bogan on 2012-04-24
Hi!, **cdo**,

'pwd' is not part of the prompt, it is a command that returns the path to the folder to which you are 'cd'd: ie. to which current commands are directed.

When you paste commands from text, do not use the enclosing double or single inverted commas, except where a title has spaces in it.

Chao!, **bogan.**

---

### Post by robgraves on 2012-04-24
> **cdo said:**
> Is the pwd the prompt you are referring to as i do not get that...

alan@alan-desktop:~$ cd Downloads
alan@alan-desktop:~/Downloads$ 
alan@alan-desktop:~/Downloads$

pwd stands for print working directory, it should tell you where you are currently in your filesystem, so for example if you downloaded the file to /home/username/Downloads
and you type in pwd and it returns /home/username
you know you haven't changed into your Downloads folder,

whereas if pwd returns /home/username/Downloads
you should, in theory, be where your file was downloaded
and you can confirm this by putting in the ls command which should list every file and folder in the currrent directory.

---

### Post by robgraves on 2012-04-24
> **cdo said:**
> Is the pwd the prompt you are referring to as i do not get that...

alan@alan-desktop:~$ cd Downloads
alan@alan-desktop:~/Downloads$ 
alan@alan-desktop:~/Downloads$

sorry, i missed that, your second and third prompt here reflect you being in the Downloads folder, so assuming your file was downloaded here you should run your command:
```

sudo bash Indexing_unix_3_13_1.sh

```
from this directory, when you are in the Downloads folder.

---

### Post by cdo on 2012-04-24
Thanks a ton Rob as that did the trick and ran the installer . Not crazy about 11.04 but there are people out there like yourself and that make Linux special . Also proves that old farts like myself shouldn't be messing with command stuff ..  :-)

Thanks again guys for your help

---

