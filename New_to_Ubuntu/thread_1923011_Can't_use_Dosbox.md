---
title: "Can't use Dosbox"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by Ketman on 2012-02-09
I followed the instructions in the documentation. 

> 
In a regular terminal, (NOT DOSBox), you can execute 
 $ mkdir ~/dos/c  
which will create the  /dos/c  directory in your home directory.  To have DOSBox use this as its  C:\  drive, execute the following command in DOSBox: 

mount c /home/wikiuser/dos/c 
Doing that, I get:

ketman@ketman-laptop:~$  mkdir ~/dos/c
mkdir: cannot create directory `/home/ketman/dos/c': No such file or directory
ketman@ketman-laptop:~$ mkdir ~/dos/c

Help?

---

### Post by dcsoldschool53 on 2012-02-09
> **Ketman said:**
> I followed the instructions in the documentation. 


Doing that, I get:

ketman@ketman-laptop:~$  mkdir ~/dos/c
mkdir: cannot create directory `/home/ketman/dos/c': No such file or directory
ketman@ketman-laptop:~$ mkdir ~/dos/c

Help?
If you are doing this from a terminal prompt in Ubuntu, the command would be```
mkdir -p ~/dos/c
```This will create two folder at the same time, one inside the other, C folder will be created inside of the folder called dos.

---

### Post by Ketman on 2012-02-09
Thanks. That did the trick. I have found the dos folder with c: inside it. So I know it exists. But DOSbox doesn't agree. This is what I got at the prompt:

Z:\> cd c:
To change to different drive type C:

Z:\> C:
Drive C does not exist!
You must mount it first. Type intro or intro mount for more information.

Z:\> cd /home/ketman/dos
You are still on drive Z:, change to a mounted drive with C:

Z:\> C:
Drive C does not exist!
You must mount it first. Type intro or intro mount for more information.

Z:\>


Ha! Some sadistic variation of Catch-22. 

Any ideas?

---

### Post by dcsoldschool53 on 2012-02-09
When you created the directory did you use the small c or the capital C. If it was the small c delete it and redo the command with```
mkdir -p /dos/C
```or```
cd dos
```then```
mkdir C
```directory.

---

### Post by oldos2er on 2012-02-09
> **Ketman said:**
> Thanks. That did the trick. I have found the dos folder with c: inside it. So I know it exists. But DOSbox doesn't agree. This is what I got at the prompt:

Z:\> cd c:
To change to different drive type C:

Z:\> C:
Drive C does not exist!
You must mount it first. Type intro or intro mount for more information.

Z:\> cd /home/ketman/dos
You are still on drive Z:, change to a mounted drive with C:

Z:\> C:
Drive C does not exist!
You must mount it first. Type intro or intro mount for more information.

Z:\>


Ha! Some sadistic variation of Catch-22. 

Any ideas?

```
mount c: /home/ketman/dos/c
``` Then retry ```
c:
```

Edit: If you want ~/dos/c mounted each time you start dosbox, at that mount to ~/.dosbox/dosbox-0.74.conf (or whichever version of dosbox you're using).

---

### Post by Ketman on 2012-02-09
> **dcsoldschool53 said:**
> When you created the directory did you use the small c or the capital C. If it was the small c delete it and redo the command with```
mkdir -p /dos/C
```or```
cd dos
```then```
mkdir C
```directory.

Thanks, but same old story:

Z:\> cd dos
You are still on drive Z:, change to a mounted drive with C:

---

### Post by oldos2er on 2012-02-09
If you ran the mount command I gave you, all you need to type is "c:"

---

### Post by dcsoldschool53 on 2012-02-09
Try what old said and use your new C file that you created.

---

### Post by Ketman on 2012-02-09
> **dcsoldschool53 said:**
> When you created the directory did you use the small c or the capital C. If it was the small c delete it and redo the command with```
mkdir -p /dos/C
```

I deleted both the c directory and the dos directory and started again with that first command:

Z:\> mkdir -p /dos/C
Illegal switch: /dos/C

---

### Post by Ketman on 2012-02-09
> **oldos2er said:**
> ```
mount c: /home/ketman/dos/c
``` Then retry ```
c:
```

Z:\>mount c: /home/ketman/dos/c
Directory /home/ketman/dos/c doesn't exist

Z:\>

---

### Post by oldos2er on 2012-02-09
You need to run ```
mkdir -p ~/dos/c
``` in gnome-terminal, not dosbox.

---

### Post by Ketman on 2012-02-09
> **oldos2er said:**
> You need to run ```
mkdir -p ~/dos/c
``` in gnome-terminal, not dosbox.

Right that works. The dos and c directories are there.

And then I went back to DOSbox and tried the second of your suggested commands:

Z:\> cd dos
You are still on drive Z:, change to a mounted drive with C:

So I went to terminal again and tried it there.

ketman@ketman-laptop:~$ cd dos
ketman@ketman-laptop:~/dos$ 

Am I there?

---

### Post by oldos2er on 2012-02-09
dosbox doesn't "see" your Linux directories unless you specify them with dosbox's 'mount' command so that it sees them as DOS drives (hope that's clear). Try "c:" again now.

---

### Post by lkraemer on 2012-02-09
Perhaps a sample of using DOSBox would help........
[http://ubuntuforums.org/showthread.php?t=1569510&highlight=trs80](http://ubuntuforums.org/showthread.php?t=1569510&highlight=trs80)

lk

---

### Post by Ketman on 2012-02-09
> **oldos2er said:**
> dosbox doesn't "see" your Linux directories unless you specify them with dosbox's 'mount' command so that it sees them as DOS drives (hope that's clear). Try "c:" again now.

I guess you mean try it in terminal, not DOSbox. I tried it and I get this. 

ketman@ketman-laptop:~/dos$ c:\
> 

I'm not sure what that means, but at least it isn't an error message.

I'm completely bewildered. Why am I writing all these commands in terminal when DOSbox doesn't even see them, and is stubbornly sticking to directory Z:/?

---

### Post by jwbrase on 2012-02-09
The whole process:

In gnome-terminal:

```
mkdir -p ~/dos/c
```

The name of the directory you use doesn't matter. It can be ~/dos/c, ~/dos/C, ~/dosbox/drive_c, ~/abc/xyz, or any directory on your system, just as long as the directory you tell DOSBox to mount is the directory you're dumping your DOS programs into.

In DOSBox:

```
Z:\> mount C ~/dos/c
Z:\> C:
C:\>
```

---

### Post by Ketman on 2012-02-09
Okay, I'm there. I did the mount command in DOSbox, and the prompt is showing "c:\". 

But now I've run into another problem. Using the "dir" command, it tells me there are 0 files and 2 directories in c:\. But as a matter of fact there are 2 files and 0 directories in C:\. I pasted those files into the directory myself. One of them is an exe file, which I tried to run just by typing its name at the prompt. I got "Illegal command".

Edit: I tried the mkdir command and made a directory called "dummy". Then I tried "dir" again. Now it is showing those 2 files, and 3 directories. I tried running the exe again. I didn't get an error message this time. I just got the prompt, as if I'd hit carriage return without typing anything. 

And that's how things stand at the moment. I'm in the right directory, but I can't run anything.

New edit: One of those strange happenings at least is explained. I pasted a second program in the directory and that one runs okay. It looks like the first is a faulty program. But that didn't show up in the directory via "dir" either until after I'd run it. There's obviously some delay before the system updates itself with regard to changes made.

---

### Post by jwbrase on 2012-02-10
> **Ketman said:**
> Okay, I'm there. I did the mount command in DOSbox, and the prompt is showing "c:\". 

But now I've run into another problem. Using the "dir" command, it tells me there are 0 files and 2 directories in c:\. But as a matter of fact there are 2 files and 0 directories in C:\. I pasted those files into the directory myself. One of them is an exe file, which I tried to run just by typing its name at the prompt. I got "Illegal command".

The two directories is because each directory contains a link to itself (".") and to the parent directory (".."). So dir will report an empty directory as containing two directories. 

> There's obviously some delay before the system updates itself with regard to changes made.

I've noticed this myself.

---

### Post by Ketman on 2012-02-10
> **jwbrase said:**
> The two directories is because each directory contains a link to itself (".") and to the parent directory (".."). So dir will report an empty directory as containing two directories. 


Yeah, I forgot about that. It's some years since I've used DOS, except as a DOS box in Windows, where you can just click and run. The only directories you ever look at in that mode are Windows folders. 

I'm not sure DOSbox is going to work out for me. I used one of the .exe files for an hour or so last night, and there are at least 4 essential keys that don't do what the app has designed them to do (and which do work inside Windows). One of them crashes the system and ejects you from DOS altogether.

Thanks for all the contributions. I'll mark the thread as solved, because I am at least up and running.

---

### Post by Damascushead on 2012-02-10
I had more success running Dosbox when installing it using Wine. It might work with the methods that you are talking about, but when I installed it it was looking for the C:\\ directory in ~/.wine.
 
Just a suggestion. Hopefully you can do it without wine. :P

---

### Post by eriktheblu on 2012-02-10
> **Ketman said:**
>  there are at least 4 essential keys that don't do what the app has designed them to do 

Some of the keys (particularly the F keys) are reserved for DOSbox functions such as video recording, screenshots, and as you have discovered, forced quit. You can remap these.

---

### Post by Ketman on 2012-02-10
> **eriktheblu said:**
> Some of the keys (particularly the F keys) are reserved for DOSbox functions such as video recording, screenshots, and as you have discovered, forced quit. You can remap these.

That sounds worth doing. Can you give me some idea how to go about it?

---

### Post by Dennis N on 2012-02-10
Here is a little shortcut for you:

The dosbox command will automount a directory as the C: drive so you don't need to do that manually or even add directions for mounting to the configuration file.

From the terminal:

[B]dosbox /home/user-name/dosgames/
[/B]
will start DOSBox and mount /home/user-name/dosgames/ as the C: drive.

I store all the DOS games within folders inside this directory. Then I can CD into any of them easily.

---

### Post by Ketman on 2012-02-10
> **Dennis N said:**
> Here is a little shortcut for you:

The dosbox command will automount a directory as the C: drive so you don't need to do that manually or even add directions for mounting to the configuration file.

From the terminal:

[B]dosbox /home/user-name/dosgames/
[/B]
will start DOSBox and mount /home/user-name/dosgames/ as the C: drive.

I store all the DOS games within folders inside this directory. Then I can CD into any of them easily.

Brilliant! Thanks a lot for that.

---

### Post by Dennis N on 2012-02-10
If you want make it even simpler, create an alias for that:

add the line below into the file ~/.bash_aliases and you then only need to type 'dosgames' into the terminal to run the command in post #23.

**alias dosgames='dosbox /home/user-name/dosgames/'**

~/.bash_aliases needs to be created as a hidden file. It is just a text file read by the terminal when it starts if it exists. So open gedit, type in the line (substitute your directory of course), and save the file as .bash_aliases in your home folder. You can also add this line to ~/.bashrc but I like to keep all the alias definitions separate.

Note: the quotes around the right side expression are necessary.

---

### Post by eriktheblu on 2012-02-10
> **Ketman said:**
> That sounds worth doing. Can you give me some idea how to go about it?

[http://www.dosbox.com/wiki/KeyMapper]("http://www.dosbox.com/wiki/KeyMapper")

---

### Post by Ketman on 2012-02-10
Thanks, eriktheblu and Dennis N for some really useful info.

---

