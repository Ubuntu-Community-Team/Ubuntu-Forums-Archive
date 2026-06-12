---
title: "add lines to init file"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by skoziel on 2012-05-01
Hi, this isn't going to sound like a beginner question but it is.
I am installing a program through the command line interface using a very good set of instructions and it seems to have worked but the last instruction is
"add lines to init file"

and it gives me the lines to add, or alternately gives me code to add lines to .bashrc

but I can't edit and save to .bashrc can't even seem to change the permissions

and I can't seem to find an init file.

Can someone please help.

The line I'm adding is simply something to allow me to run the program from the command line.
If anyone can help by describing either where to find the file or tell me how to change the .bashrc file permissions so I can add the line

or explain to me how to write a sudo line that adds a line of code to the .bashrc file it would help a lot.

Thanks

(Just an update to let folks know that the answers below solved the problem - Thanks again everyone)

---

### Post by billyseth on 2012-05-01
You shouldn't need to sudo to edit your .bashrc file.

is it located in /home/(username)/.bashrc?

---

### Post by Enigmapond on 2012-05-01
The easy way to change the permission, if that's the problem is right-click/properties/permissions and make is writeable. Then just open it in gedit and edit the line. No need to sudo anything as it sits in your home...

---

### Post by skoziel on 2012-05-01
Okay I'm looking in home/*username*
and can't find anything that looks like a .bashrc file.

Now one quirk might be is that this is a Windows7 dual boot system that was set up with the new file out that allows a person to add ubuntu turning the system into a dual boot...
and I'm not sure if that has something to do with it.

I just set the ubuntu system with the defaults that the windows installer put into it.

So I have a feeling that where the files are might be odd. This is my home computer and no one else uses it and I'm listed as an administrator... but there are a lot of files I seem unable to access because I not listed as the owner (so I'm not sure how that works).

The only bashrc file I can find is where it says file system etc and there is a bash.bashrc file that I can't modify anything on it at all.

The home/username/ folder only seems to have folders in it.

---

### Post by Hadaka on 2012-05-01
hi

try this..in terminal mode

cd /home/your-user-name
ls -al | grep -i .bashrc

*if it is there..then enter*

ls -l .bashrc

*this again verifies the file .bashrc is in YOUR home directory*
*important...mke a note of the exsisting r-r-rw-r permissions *
* to make it writeable*

sudo chmod og=rw .bashrc

ls -l .bashrc          *you should see the chage in the percmiisions*

*then you should be able to edit .bashrc

hope this helps.

---

### Post by Enigmapond on 2012-05-01
The file is hidden in your home directory. CTRL +h reveals it. The '.' before the .bashrc indicates it's a hidden file.

---

### Post by skoziel on 2012-05-01
Thank you Hadaka that was excellent and solved all the problems. I  figured it was hidden but for the life of me I couldn't remember how to find the hidden files. 

Thanks everyone everything is fixed and I'm now running my program.

---

### Post by Hadaka on 2012-05-01
welcome, glad i was able to help. after i posted and re-read what you wrote..i was a bit
concerned that perhaps you misread the instructions..and were making the script file 
you are working on gobal... and lines were to be added to it...not .bashrc. Glad it all
worked out for you. on a secondary note..my .bashrc file is not hidden in my home directory
Ubuntu 11.10     maybe its version thing.

---

### Post by skoziel on 2012-05-01
I suspect the hidden files are a default thing maybe due to the windows dual boot or something, I used Enigmapond's suggestion and unhid everything in my home directory.
 
...and yeah - if it was a script file I would have been better off... the instructions were pretty clear though... add alias to .bashrc by adding x line.
 
Because I couldn't find the bashrc file or how to reveal the hidden files it was getting really frustrating. I even looked at changing the etc/bash.bashrc since there were instructions for that too and this is my computer... but couldn't change those permissions until I figured the whole sudo thing out (the last time I did any linux stuff was years and years ago and I can't remember half of it... and don't ever recall having to add sudo at the begining of the lines). 
 
I clearly fall into the camp of a little knowledge is a dangerous thing... enough to seem to know what I'm doing but missing small little things that would make everything go faster.

---

### Post by billyseth on 2012-05-02
Everything starting with a period (.bashrc) should be hidden be default, helps keep the clutter of all the config files and folders that are in your home folder from bothering you.

---

### Post by skoziel on 2012-05-02
Thanks.
I'm used to working in a windows environment where I unhide everything (and I really do mean everything) and I get snakey when I can't figure out how to unhide files and find myself searching for some file that someone figured they'd hide to keep things tidy.
 
The clutter doesn't bother me - wasting a few hours trying to figure out where a file is does - since even searching for the file in the dash on C:/ didn't come up with it because it was hidden, and then not knowing the command to unhide things. Very frustrating. (Which probably makes no sense that I'd be missing that bit of info when I have no issues with other unix commands... like I said my experience with linux is spotty - I used it at school... but all the computers were set up so we could program on them... and then I haven't had the chance to use it again; since my work, until recently, was a windows only place - :-? )
 
But you guys all helped a ton, and the quick helpful responses are a lovely change from some of the other help forums I've been on for these sorts of things. :) Now I feel much better about choosing to install ubuntu. I like the feeling that someone has my back and doesn't make me feel like an idiot for asking a question that I perhaps should know... I won't mention the names of any other OS help forum communities - it would be unkind.

---

