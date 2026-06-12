---
title: "Perhaps a sticky?"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by anewguy on 2012-09-12
I have a suggestion for a sticky that might be worth while.

In debugging network problems, be they wireless or whatever else, there has always been a given set of commands we ask the user to post the results back of.  A while back I created a script for Wild Man (wildmanne39) for this, then he had some of the pros enhance it.  What exists now is a script the provides a lot of information.

I thought it might be worth while to create a sticky something like "Before you report a network or wireless request".  It could include the instructions (for Linux it's quite simple) for Linux and also instructions on how to download the script portion in Windows to bring to a Linux box that has no net connection do to problems, be they missing drivers, locks, etc..

Here is how to get the script and have it set everything up and execute in Linux.  All the user need do is copy/paste to command line and execute, the post with the resulting file netinfo.txt attached.

wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script

Again, I would think there would need to be 2 sections to this - one for the user that has network access directly from Linux, and one for the user that must download the script via Windows or some other OS, load it to their Linux box, then make it executable and execute it.

I could even try to volunteer for this, but I would need to know how to do the equivalent of the wget in Windows without requiring the user to install wget for Windows. You know - use the existing tools if possible.

Just an idea.

---

### Post by hypnot0ad on 2012-09-12
If absolutely any user could do it this is an awesome idea, and should be done.
Great idea.

---

### Post by overdrank on 2012-09-12
Hi and no one reads the stickies :)
But how about this [_one_]("http://ubuntuforums.org/showthread.php?t=370108").

---

### Post by NikTh on 2012-09-12
Hi ,

Good Idea @anewguy , but I must agree with @overdrank too :P 

I have another idea for this script , but need some skills that I don't have. 

What about create a program (python maybe?) that any user could install and this program will do two things. 

1. Execute the script 

2. Upload the results in pastebin and give the link to user , 
or attach the file here in forums (if this is possible). 

and if someone has not internet at all (in linux) he/she can download the program straight from the link (eg: sourceforge) and transfer the program to linux and install it there. 

again: I don't have any coding skills , or packaging skills (.deb etc) . Only the idea :)

Thanks

---

### Post by anewguy on 2012-09-12
> **overdrank said:**
> Hi and no one reads the stickies :)
But how about this [_one_]("http://ubuntuforums.org/showthread.php?t=370108").

I think everything it requires being done manually is covered in the script, so perhaps I should contact someone about that thread and offer it there.  Thanks!

---

### Post by anewguy on 2012-09-12
> **NikTh said:**
> Hi ,

Good Idea @anewguy , but I must agree with @overdrank too :P 

I have another idea for this script , but need some skills that I don't have. 

What about create a program (python maybe?) that any user could install and this program will do two things. 

1. Execute the script 

2. Upload the results in pastebin and give the link to user , 
or attach the file here in forums (if this is possible). 

and if someone has not internet at all (in linux) he/she can download the program straight from the link (eg: sourceforge) and transfer the program to linux and install it there. 

again: I don't have any coding skills , or packaging skills (.deb etc) . Only the idea :)

Thanks
Except for the transfer, it pretty much does that if you just copy and paste the line.  However, I also have thought about finding ways to automate this.  If some of you want to toss around ideas, I would be happy to do some of the work.  Right now I'm not sure how to do the upload programmatically, but if worse came to worse it could be done from the command line inside the script itself.  Any thoughts on details?  I could write the program in C with GTK so it has a GUI'd interface.  I also know squat about what is required to make an app "packable" and what must be done to make a package.

The only draw back I have ever seen to the whole idea, even from the start when I did the initial scripting for wildmanne39, is that if you are having issues so there is a need to use the script, chances are that for the vast majority it would mean needing to use another computer to download and another computer to upload the results.  I like the idea of a package because it would be something they could download from anywhere.  That package need only contain a readme and the script and it would help.  Getting the output back up is another matter - again for the vast majority it would mean copying the file to a removable media and taking to another computer that has internet access. There is a realistic limit to what can actually be automated.  I do like the package idea, and if other things can be thought of to add to it, I can add it to the script or write a program.

Thanks for the input, and if you guys have more detail to pass along, or even just add to it yourselves, I could try to maintain more of it from here.  I'm just trying to avoid getting too much in to it personally due to some bad experiences this summer with what I have to assume were school kids out for the summer wanting to argue with me.  That's why I dropped out my Ubuntu Member status, and also why I have tried to stay WAY in the back ground.  I've done a little more replying lately because wild man told me he has other committments right now that are distracting from how much time he can put into things right now.  In no way could I take his place, but maybe help just a little until someone else comes to those threads.

Thanks, friends!
Dave ;)

---

### Post by sandyd on 2012-09-12
I like the idea of creating the file locally.

After all, if a user does not have something to transfer files to the computer in question, how do they install firmware, files/patches .etc .etc onto that computer?

Anyways, I have a perliminary GUI that I originally used for the Adobe Flash Tools.

Its really easy to modify and is already setup to run commands from scripts.

If you want, I can fish it back out of [s]whereever I put it[/s] I know where I put it, and you can use it.

Here it is.... (I was lazy, and didn't increase the size of the button - sorry)

Install dev libs
```

sudo apt-get install gtk+-2.0-dev
```

test.c
```
http://pastebin.com/DDPLHKSX
``` - UF kept on messing with the formatting - gave up on that.

Compile with
```

gcc ./test.c -W -Wall -ansi -pedantic -g `pkg-config --cflags --libs gtk+-2.0` -o test.bin
```

---

### Post by anewguy on 2012-09-13
Thanks Sandyd!  I'l let one of the other people handle this.  I've just been back a couple of days and again in some of the threads where I've I've been trying help the OP wants to argue again.  That's why I dropped my Ubuntu Member status and went into the woodwork to begin with.  So, with this starting again, I'm going back to the woodwork again.  If you or anyone else wants to contact me I'll still be watching my PM's.

Thanks again!  I really hope someone picks up on this.

Dave ;)

BTW - I notice you're in LA.  Back in the 80's I worked in Infomation Systems at Todd Pacific Shipyards.  I remember we had a Sandy there who had a consulting business and some people working there from her group as well.  Any chance it was you?

---

### Post by varunendra on 2012-09-13
Awsome script there anewguy !

One suggestion though- How about adding an 'echo' in the beginning to inform the user that a "netinfo.txt" file is about to be created that will hold all the info required for troubleshooting?
Something like:
```
clear
echo -e "\n\n The following file is about to be created (in your currect directory) :\n\n\t`pwd`/netinfo.txt \n\n Attach this file or copy-paste its contents in forums if you seek help there.\n"(+blah-blah-blah... if it helps.. ;))
```

I've seen new users getting confused if they don't get any output on screen after they've entered a command. Not to mention when you have to tell them they won't see 'stars' or 'dots' or anything while entering their password at sudo prompt ;)

---

### Post by anewguy on 2012-09-13
Would be a good idea - pass this along to someone to work on.  I'm not actually going to be involved anymore.

---

