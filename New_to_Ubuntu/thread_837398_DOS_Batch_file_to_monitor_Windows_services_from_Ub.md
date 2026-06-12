---
title: "DOS Batch file to monitor Windows services from Ubuntu."
date: 2008-06-22
forum: New to Ubuntu
---

### Post by TBev0 on 2008-06-22
Gday all

I'm having problems with a DOS batch file im trying to put together. What i'd like to do is monitor the services on a remote Windows machine and when one of them crashes i am notified on my Ubuntu laptop. 

I have setup SSH between the machines and plan to execute the batch file via SSH. The batch file needs to be executed every 5min or so but will be initiated from the Ubuntu machine. 

The problem is i cant even get the batch file to work locally on the windows machine. I have downloaded and installed the linux 'diff' command onto the windows box as i was unable to achieve the results i was after with the DOS fc command. I plan to compare the results of two files created with the net start command. There will be a 'master' file which
contain a list of all the services running when compared to a second file which will be created every 5min or so.

Here is what i have so far:

net start > C:\services1.txt

cd "C:\Program Files\GNUWin32\bin"

diff -i -b -B -q C:\services.txt C:\services1.txt | %output%

	IF /I [%output%] ==[Files c:\xeonservices.txt and c:\xeonservices1.txt differ] GOTO 
CRASHED

GOTO END

:CRASHED

diff -i -b -B C:\xeonservices.txt C:\xeonservices1.txt > C:\output.txt

:END

Obviously the problem i am having is piping the output of the diff command into a variable to compare to a string. Has anyone got any bright suggestions or ideas, maybe i am going about the entire thing the wrong way?? Any help is appreciated..

---

### Post by Dedoimedo on 2008-06-22
Hello,

How about:

You set a cronjob to run nmap against the windows machine and check the services? If one does not respond, then you know what you need to do.

Something like:

nmap remote-host | grep "smtp"

And if this one is empty, then you up the service using the net command (in BASIC).

Or simply use the "net" command.

Dedoimedo

---

