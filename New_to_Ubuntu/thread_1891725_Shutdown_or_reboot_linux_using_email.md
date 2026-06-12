---
title: "Shutdown or reboot linux using email"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by digitography on 2011-12-06
I have done a lot of research on this but to very little avail.
I know this can be done in Windows with outlook, but I want to do it on an ubuntu setup.
simple idea I send the computer an email, using evolution message filter it finds the correct message and runs a command to shut the computer down.
The first bit is easy, evolution filters work and find the specific email, and will run a command. How can I tell it to shutdown? I thought about a bash script, but how do I get that to run.

as always your excellent assistance appreciated.

---

### Post by Lars Noodén on 2011-12-06
You might be able to work out something using [procmail](http://www.procmail.org/).  It can do that kind of thing and a lot else, too.  You'll have to look around for some tutorials because until you are familiar with how to configure it, the manual pages will be a little too abstract.

There are some [procmail example recipes](http://manpages.ubuntu.com/manpages/precise/en/man5/procmailex.5.html) to get started with.

---

### Post by androssofer on 2011-12-06
> **digitography said:**
> I have done a lot of research on this but to very little avail.
I know this can be done in Windoze with outlook, but I want to do it on an ubuntu setup.
simple idea I send the computer an email, using evolution message filter it finds the correct message and runs a command to shut the computer down.
The first bit is easy, evolution filters work and find the specific email, and will run a command. How can I tell it to shutdown? I thought about a bash script, but how do I get that to run.

as always your excellent assistance appreciated.

have you got evolution running commands? if so thts awesome! 

anyway. the main issue here is permissions. any command that evolution runs wont have enough permission to shutdown your computer, as shutdown needs run by root. 

**workaround:**

this is how i would do it:

create a bash script that evolution can run. in this bash script, change the value in a file (have the file in the same folder as the script). the file is called 'canShutDown'.

so when the evolution script runs it changes that value to true.

then create a cron job, that run another script with root permissions that checks that file every, minute, hour, day, whatever you like. if the file is true, it sets it back to false then shutsdown...

so basicly you have a cron job with root permissions always checking a file to see if it can shutdown. 

that file is only set to true by evolution when it gets that email. and evolution doesnt need root permission.

:-)

---

### Post by Lars Noodén on 2011-12-06
> **digitography said:**
> 
The first bit is easy, evolution filters work and find the specific email, and will run a command. How can I tell it to shutdown? I thought about a bash script, but how do I get that to run.

There's two parts to that.  One is a shell script which calls shutdown.  The second is to configure [/etc/sudoers](http://manpages.ubuntu.com/manpages/precise/en/man5/sudoers.5.html) so that user can run that script as root without needing a password.  

So if your mail user is a member of the group 'mailgroup' and the shutdown script is [font=Courier New]mailshutdown[/font]
 in [font=Courier New]/usr/local/sbin[/font], then your entry in [font=Courier New]sudoers[/font] would look something like this:


```

%mailgroup   ALL = (ALL) NOPASSWD: */usr/local/sbin/mailshutdown*

```

---

### Post by SeijiSensei on 2011-12-06
You might be able to avoid the permissions problem by sending the message to root@host.  Procmail would process the message with root's permissions.

Otherwise send the message to an ordinary user and have it set a semaphore; then use a cron script running periodically as root to check for the semaphore and shutdown or reboot as required.

Here's a simple procmail recipe that you can use to start.  Put it in /root/.procmailrc.

```

:0
* ^Subject:.*shutdown
| /usr/local/sbin/mail-controller shutdown

:0
* ^Subject:.*reboot
| /usr/local/sbin/mail-controller reboot


```

/usr/local/sbin/mail-controller would look something like:

```

#!/bin/bash

case "$1" in

   shutdown)
   /sbin/shutdown -h now
   ;;

   reboot)
   /sbin/reboot
   ;;

esac


```

You can improve security by including a test for the sender as well:

```

:0
* ^From:.*you@example.com
* ^Subject:.*shutdown
| /usr/local/sbin/mail-controller shutdown

```

Or include an un-guessable token like a SHA1 hash in the message body:

```

:0
* ^From:.*you@example.com
* ^Subject:.*shutdown
{
   :0B
   cc318f58c3a028d7fea78e039dd0f16cec8d83df
   | /usr/local/sbin/mail-controller shutdown
}

```

---

### Post by digitography on 2011-12-06
I gotta say first and foremost, you guys are awesome, so many responses.

OK firstly I have a confession to make when I said I could get evolution to run a command, well that was a big error, seems like it won't, I think I got fooled. I setup a simple filter that would detect the email, raise the email priority to high, and then run gedit. Well I may have already had a gedit window open and was fooled by that.

OK Firstly I went with Lars Noodens suggestion, partly because I know how to run visudo, and it looked familiar.
I setup the script

#!/bin/sh 

echo "shutdown command received"

shutdown -r now

I ensured that the group mailshutdown was set as the group, and that the execute option was set.
The mailshutdown group has the correct user in it.

The filter definitely detects the incoming mail, and sets it to high priority, but nothing after that.

My suspicion is that evolution does not have the rights to run a command.

I will try [androssofer]("http://ubuntuforums.org/member.php?u=304080") suggestion later today or in the morning, however excuse my stupidity but I have never setup a cron job.

Again thanks for all the amazing input.


I created a

---

### Post by Lars Noodén on 2011-12-06
If you can't get Evolution to work, look at the [procmail recipes](http://manpages.ubuntu.com/manpages/oneiric/en/man5/procmailex.5.html) that  SeijiSensei posted.  They should do the job.

---

### Post by androssofer on 2011-12-08
> **digitography said:**
> I have done a lot of research on this but to very little avail.
I know this can be done in Windoze with outlook, but I want to do it on an ubuntu setup.
simple idea I send the computer an email, using evolution message filter it finds the correct message and runs a command to shut the computer down.
The first bit is easy, evolution filters work and find the specific email, and will run a command. How can I tell it to shutdown? I thought about a bash script, but how do I get that to run.

as always your excellent assistance appreciated.

can i ask for the reason you need this? because as with most things linux, there might be 20 alternatives to achieve the same thing, and there might be an easier one to implement for you...

---

### Post by digitography on 2011-12-08
> **androssofer said:**
> can i ask for the reason you need this? because as with most things linux, there might be 20 alternatives to achieve the same thing, and there might be an easier one to implement for you...

I am working on an amateur radio repeater system. A legal requirement of holding a licence for this, means that I must be able to demonstrate that in an emergency I can shut the system down remotely within 30mins. The email idea I saw somewhere else where the user was using a windoze box.

I have made some progress since my last posting. For test purposes I have simply created a bash that pops up a message "shutdown command received", then open gedit nothing more. If I open a terminal and type mailshutdown the script runs and a message tells me "shutdown command received" and gedit opens.
So from this I deduce that the script is running. I am guessing I have to somehow open an terminal window to run the command, however that option isn't in evolution.

---

### Post by Lars Noodén on 2011-12-08
Why not just log in with SSH and use [sudo](http://manpages.ubuntu.com/manpages/precise/en/man8/sudo.8.html) to shut it down?

You can specify with [sudoers](http://manpages.ubuntu.com/manpages/precise/en/man5/sudoers.5.html) which groups can shut the machine down and whether or not a password is needed.

```

%users ALL=(ALL) NOPASSWD: /sbin/shutdown

```

It's arguably less fun than hacking a mail solution but is a lot simpler.

---

### Post by digitography on 2011-12-08
OK, have to admit to being a bit of a beginner with linux, and I have never used SSH, I think it's secure shell?
Did I mention I need to do this across the internet, ie the computer running the repeater will not be on a network I am attached to. The other reason for going down the email route, is that it is possible to send an email using a mobile phone, so no matter where I am I could in theory effect the shutdown.

---

### Post by Lars Noodén on 2011-12-08
[SSH](http://en.wikibooks.org/wiki/OpenSSH) is the normal way of remotely accessing machines via the Internet.  If you have a smartphone, there should be a SSH client for it available for download.

---

### Post by digitography on 2011-12-08
OK thanks, I have no idea where to start with SSH.

---

### Post by SeijiSensei on 2011-12-08
> **digitography said:**
> OK thanks, I have no idea where to start with SSH.

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by Lars Noodén on 2011-12-08
> **digitography said:**
> OK thanks, I have no idea where to start with SSH.

It's rather easy.  On the machine you want to connect to, install the package OpenSSH-Server.  The only configuration that you might want to do would be to change [font=Courier New]PermitRootLogin yes[/font] to [font=Courier New]PermitRootLogin no[/font] in [/etc/ssh/sshd_config](http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html)

Then find the appropriate SSH client for your smartphone and use that to connect.  Be sure that your account has a long password or else follow SeijiSensei's link above and authenticate using keys.  

Once you're connected using SSH, you have full access to the shell and can do anything remotely that you could have done while sitting physically at the console.  That includes shutting down or restarting the machine.

---

### Post by androssofer on 2011-12-08
> **digitography said:**
> I am working on an amateur radio repeater system. A legal requirement of holding a licence for this, means that I must be able to demonstrate that in an emergency I can shut the system down remotely within 30mins. The email idea I saw somewhere else where the user was using a windoze box.

I have made some progress since my last posting. For test purposes I have simply created a bash that pops up a message "shutdown command received", then open gedit nothing more. If I open a terminal and type mailshutdown the script runs and a message tells me "shutdown command received" and gedit opens.
So from this I deduce that the script is running. I am guessing I have to somehow open an terminal window to run the command, however that option isn't in evolution.


ssh is the way i would go about it. but ssh requires an ssh client. which is fine if you have another linux box or android. but if your on a windows machine, it might be tough. and if your in a hurry it wouldnt be good.

The way i would go about it is:

get apache installed, get it to listen on a random port: 8181 for example. set up ssl and basic authentication (sounds worse than it is). and make a php web page that allows you to click a button that changes a file to false. this would allow you to shut it down from any computer with a semi-modern browser...

cron checks that file every 15 mins, if its false it sets it to true and shuts down.


it sounds quite complex. but it isnt, there are lots of guides on how to do it. and i'd be happy to point you at them / take you through it if you need?

---

### Post by Lars Noodén on 2011-12-08
> **androssofer said:**
> ssh is the way i would go about it. but ssh requires an ssh client. which is fine if you have another linux box or android. but if your on a windows machine, it might be tough. and if your in a hurry it wouldnt be good.

Even a system as poor as Windows has good SSH clients available.  [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) can be found via Google and up and running with only a handful of clicks of the mouse.  The time it takes is about 30 seconds.

---

### Post by Moif_Murphy on 2011-12-08
> **androssofer said:**
> ssh is the way i would go about it. but ssh requires an ssh client. which is fine if you have another linux box or android. but if your on a windows machine, it might be tough
 
Sorry to chime in, but Putty is a fine Windows SSH client. I use it all the time :)

---

### Post by androssofer on 2011-12-08
> **Lars Noodén said:**
> Even a system as poor as Windows has good SSH clients available.  [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) can be found via Google and up and running with only a handful of clicks of the mouse.  The time it takes is about 30 seconds.

i know. No gripes against windows clients. 

My concern is if he is away from his own kit. and an emergency comes up, getting a client onto someone else's windows box etc might not be feasible, thats why i suggested the web page thing. 

But perhaps i'm thinking into it too much... haha

---

### Post by digitography on 2011-12-08
> **androssofer said:**
> 

But perhaps i'm thinking into it too much... haha

No you're not over thinking it.
The apache idea sounds good.
I have no experience of apache, so I'm a lamb to the slaughter.
I would also like to get the SSH idea running too, for no other reason than I have never set this up.
There is one caveat that I would add before we move one. The target computer I would be wanting to shutdown would be sitting behind a broadband router at my home, I could be anywhere. I know it's simple enough to setup port forwarding on the router, but how do I get from wherever I am to the target computer.
These may seem like stupid questions to you guys you probably dream this stuff, to me it's breaking new ground.

---

### Post by Lars Noodén on 2011-12-08
You would SSH to the external address of your router and the router must be set to forward the SSH port (22) to the desired machine. 

How to know the external IP number is the weak point in this, phpMyAdmin, WebMin, the Apache idea, or most any other plan.  You could have the IP address automatically resolved from a domain name at a dynamic ip service like [DynDNS](http://www.dyndns.com/) or many others.

---

### Post by Moif_Murphy on 2011-12-08
Everything you need to know about SSH is right here: [https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html)
 
And here: [http://www.techotopia.com/index.php/Configuring_Ubuntu_11.04_Remote_Access_using_SSH](http://www.techotopia.com/index.php/Configuring_Ubuntu_11.04_Remote_Access_using_SSH)
 
And if you have the firewall enabled then this is a good guide: [http://www.techotopia.com/index.php/Using_gufw_and_ufw_to_Configure_an_Ubuntu_11.04_Firewall](http://www.techotopia.com/index.php/Using_gufw_and_ufw_to_Configure_an_Ubuntu_11.04_Firewall)

---

### Post by androssofer on 2011-12-08
> **digitography said:**
> No you're not over thinking it.
The apache idea sounds good.
I have no experience of apache, so I'm a lamb to the slaughter.
I would also like to get the SSH idea running too, for no other reason than I have never set this up.
There is one caveat that I would add before we move one. The target computer I would be wanting to shutdown would be sitting behind a broadband router at my home, I could be anywhere. I know it's simple enough to setup port forwarding on the router, but how do I get from wherever I am to the target computer.
These may seem like stupid questions to you guys you probably dream this stuff, to me it's breaking new ground.

as already mentioned, get dyndns (or similar service)

info [here]("https://help.ubuntu.com/community/DynamicDNS")

it will set a domain name to your home IP address, so you don't need to worry about what your ip is (if your isp changes it) you just type your dynamic domain name. eg: yourDomain.dyndns.org, and dyndns will convert that to the ip for you. 

then you forward the ports on your router to the computer, so any connection on that port will go to that computer. 

i like using non default ports like 2222 for ssh and 8181 for apache for security (default ports are often scanned by hackers/crackers). but the defaults might be a tad less complicated to set up.. but only a tad.

then open your firewall to allow connections to those services on the chosen ports. then you can access your computer from any computer with internet :-).

---

### Post by digitography on 2011-12-08
Strewth, loads of responses thanks, I think you may be endowing me with more nounce than is appropriate.

OK here's another item to throw into the pot. I have my own website, hosted by an ISP, so my thinking is could I have a page on my website that links back to my router, or is that a stupid idea?

I guess this is why the email option looked so promising, however I just can't get it to execute the script, if I tell it to do something simple like run gedit, it works fine. However there is no way of executing terminal command from evolution, which would have been perfect.

Any looks like I have a lot more to do and to learn than I thought.
The responses have been fantastic, thanks to all of you.

---

### Post by Lars Noodén on 2011-12-08
> **digitography said:**
> OK here's another item to throw into the pot. I have my own website, hosted by an ISP, so my thinking is could I have a page on my website that links back to my router, or is that a stupid idea?

It's a fine idea, but like most of the others it would depend on having a dynamic DNS service because your residential external IP number can change from day to day, at least in theory.  

However, since you have your own externally hosted site, it probably also runs SSH so you could instead of dynamic DNS run a reverse tunnel.  But that is advanced use of SSH.  Give the basic SSH a try first and see how that works.  It's the industry standard method for remote systems management for good reasons.

---

### Post by BC59 on 2011-12-08
Well just to throw an idea, instead of using Evolution you could try with Skype. Answering skype is turning on the video camera, so with the camera you could execute the script.

---

### Post by SeijiSensei on 2011-12-08
1) I gave you a lot of the functionality you'd need to do this by email earlier in the thread.  You seemed wedded to Evolution; I think procmail is a much better approach.

2) Web servers like Apache don't run with root permissions so you cannot write a script in something like PHP that will reboot a machine.  You could have the script create a "semaphore" file in some directory that is checked constantly by a script that runs with root privileges (using cron, for example.)  The script looks to see if the semaphore file exists; if so, it deletes it then reboots.

3) You could try installing [Webmin]("http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb") on your server.  It's a web-based administration tool that runs with root privileges and can be told to [reboot]("http://doxfer.webmin.com/Webmin/BootupAndShutdown") the server.  It does use SSL to protect the password transaction, but you still need to use a very strong password since you're *exposing root control of the server to the Internet*.  Personally I wouldn't take this approach; it's too insecure.  I just use SSH with public-key authentication.

There are ways to run SSH from a browser; here's [one that looks promising]("http://prefetch.net/blog/index.php/2011/03/28/running-an-ssh-client-inside-your-firefox-web-browser/") though I haven't tried it myself.  I saw a number of web sites offering free SSH services which I'd steer far away from.  All you'd need to do to harvest the users' credentials is stick a keystroke logger ahead of the SSH client.

---

### Post by digitography on 2011-12-09
OK I'll take a look at procmail, although at this stage i  don't even know what it is.

The reason I seem wedded to evolution is that it's what I know, I am very new to Linux, and certainly never tried anything this deep before.

However on the evolution front, I have made some progress, evolution doesn't allow you to edit a filter entry directly, ie you can tell it to run a program such as gedit, but you can't give it any parameters (is that the right word?). However the filter is simply an xml file in userid/.evolution/mail/filters.xml.
So here is what I tried:
Firstly I setup a filter so that an email from a specific user, with specific subject and specific words in the body would trigger and pipe to a command (why pipe worked and not run I don't know). So now there is an entry in the filters.xml file that looks like this
```
        <part name="pipe">
          <value name="command" type="command">
            <command>/usr/bin/gnome-terminal</command>
```Then I edited filters.xml so that the gnome terminal now runs my shutdown bash script.

```
        <part name="pipe">
          <value name="command" type="command">
            <command>/usr/bin/gnome-terminal -e /usr/local/sbin/mailshutdown.sh</command>
```And it works, well almost :-(
gnome-terminal does indeed start, and it does indeed execute the script, however because shutdown needs root privileges (I assume) it asks for my password. I tried messing around with sudoers but I don't really understand the syntax, so not really sure what I was doing and well could break the darn thing at any moment.

I really do appreciate all the help that you have freely offered to someone you don't know, and is a fully qualified numpty :-)

---

### Post by digitography on 2011-12-09
> **SeijiSensei said:**
> You might be able to avoid the permissions problem by sending the message to root@host.
[COLOR=Red]snip[/COLOR]
Here's a simple procmail recipe that you can use to start.  Put it in /root/.procmailrc.
[/code]

OK I installed procmail from synaptic
however I do not see the .procmail in the root directory, do I have to create this?

---

### Post by SeijiSensei on 2011-12-09
> **digitography said:**
> OK I installed procmail from synaptic
however I do not see the .procmail in the root directory, do I have to create this?

Yes.  Procmail is the "mail delivery agent" invoked by Postfix to deliver mail to local accounts.  It will scan a user's .procmailrc file for "recipes" to use to handle mail.  You create these files with an editor like gedit.

You might start by reading this:  [https://wiki.ubuntu.com/Procmail](https://wiki.ubuntu.com/Procmail) 

If putting the rebooting recipe in /root/.procmailrc doesn't seem to work, you can try placing it in /etc/procmailrc (note, no leading dot) which procmail reads for every message.  You'll need to add a filter to check the "To" field in this case as well as From, Subject, or others mentioned in the recipe I wrote.

> **digitography said:**
> it works, well almost :-(
gnome-terminal does indeed start, and it does indeed execute the script, however because shutdown needs root privileges (I assume) it asks for my password. I tried messing around with sudoers but I don't really understand the syntax, so not really sure what I was doing and well could break the darn thing at any moment

You could apply the same solution to Evolution running in root's account, but Ubuntu makes it difficult to log in as root and run Evolution from the desktop.  That doesn't mean it's not possible, but I can't tell you how without breaking the Forum Rules.

If you've gotten this far with Evolution, how about trying the two-part solution I and some others mentioned. Have the inbound message invoke a script that creates an empty file in some directory.  Then run a script as root each minute using cron that checks for the presence of the file and runs the reboot command if the file exists.

---

### Post by digitography on 2011-12-12
OK many thanks for all the responses yet again, I can't express my thanks enough.

Well I found a somewhat inelegant solution to the evolution approach, I assigned SUID rights to shutdown, then filtered the email and bang the computer rebooted. Excellent, except for one problem. It would seem Evolution never finishes processing the email, so when the computer reboots and evolution starts up again, it sees the email again and tries to act upon it, ie running the script to shutdown. As there is a time delay I can kill the shutdown, but it's not really an unattended solution.

So I decided to tackle the hybrid approach, having evolution set a file or semaphore (don't really understand that yet) and then have cron job check the status every 2 mins or so. So first problem for me is to understand cron. After some googling I was able to work out that  cron IS installed and is running on the computer. Then put an entry into the crontab file, which I have done, and this is where I need some guidance. I edited /etc/crontab and added the entries

#cron test
*/2 *    * * *    root    /usr/local/sbin/crontest.sh

at this stage crontest.sh is just a bash that opens a terminal window and waits 30 seconds, then exits, however to date nothing happens, so I guess my question, before i lose any more hair is, am I barking up the wrong tree?

---

### Post by Lars Noodén on 2011-12-12
Rather than SUID you can use sudo.  

```

%halters  ALL=(ALL) NOPASSWD: /sbin/shutdown

```

---

### Post by androssofer on 2011-12-12
> **digitography said:**
> OK many thanks for all the responses yet again, I can't express my thanks enough.

Well I found a somewhat inelegant solution to the evolution approach, I assigned SUID rights to shutdown, then filtered the email and bang the computer rebooted. Excellent, except for one problem. It would seem Evolution never finishes processing the email, so when the computer reboots and evolution starts up again, it sees the email again and tries to act upon it, ie running the script to shutdown. As there is a time delay I can kill the shutdown, but it's not really an unattended solution.

So I decided to tackle the hybrid approach, having evolution set a file or semaphore (don't really understand that yet) and then have cron job check the status every 2 mins or so. So first problem for me is to understand cron. After some googling I was able to work out that  cron IS installed and is running on the computer. Then put an entry into the crontab file, which I have done, and this is where I need some guidance. I edited /etc/crontab and added the entries

#cron test
*/2 *    * * *    root    /usr/local/sbin/crontest.sh

at this stage crontest.sh is just a bash that opens a terminal window and waits 30 seconds, then exits, however to date nothing happens, so I guess my question, before i lose any more hair is, am I barking up the wrong tree?

Id say its running. but doesnt work because it doesnt know which screen to open the terminal window on.

(**background** the x window system is made to be network transparent, so you can run programs remotely as if you are at the computer)

so in you bash script add in:

```
export DISPLAY=:0 && **insert you code here***
```

and it should run..


or you could get it it change a file and use that as a test. so the cron job would be:

```
*/2 *    * * *    root    /usr/local/sbin/crontest.sh > /home/username/testfile.txt
```
**replacing username with you username

and crontest.sh would contain:

```
echo "true"
```

then after 2 minutes do;

```
more /home/username/testfile.txt
```

and it should say 'true'

---

### Post by digitography on 2011-12-14
Thanks to everyone yet again for some great input.

OK so I took androssofer's approach.
so now I have:
I can send an email with a specific subject, from a specific user, with specific text in the body.
If the condition is met a script is run that modifies a txt file to say "true" ie shutdown. Cron runs a script every 2 mins, however I am still new to this malarky and I am not sure how to go about testing for the condition of the text file?

I tried this

```
if more /home/usename/testforshutdown.txt = "true"
then shutdown -r 1

exit
```
in my simple mind that makes sense, however what happens is the text inside testforshutdown.txt simply gets cleared.
So I am guessing I don't have the syntax right?

Close but no cigar, yet!

---

### Post by Lars Noodén on 2011-12-14
Instead of messing with cron and going through the trouble of setting a flag in a file, why not use sudo like in post #4 above and call shutdown directly?

---

### Post by digitography on 2011-12-14
> **Lars Noodén said:**
> Instead of messing with cron and going through the trouble of setting a flag in a file, why not use sudo like in post #4 above and call shutdown directly?

I tried calling shutdown directly from evolution by editing the filter file, and indeed it did work, with one problem. When the computer shuts down, evolution is either still processing the email, or has not let it go for some reason, then when the computer reboots and you restart evolution it tries to shutdown again. I even tried forcing evolution to shutdown before the shutdown command was run, same issue. For a situation where I would be coming back to the machine to look at the problem later, it's not an issue, as I can simply kill the shutdown manually, but if I want to simply restart the computer and have programs restarted it is a problem.

I am not dismissing any of the solutions offered, in fact I intend to implement all of them if possible, because the more tools I have at my disposal, the less likely the licencing authorities are to bother me.

---

### Post by Drenriza on 2011-12-14
Why is this so difficult?

Cant you just create a e-mail account & e-mail server, on the machine that needs to get the command, so it can receive and store e-mails.

Then make a cron that delete all e-mails every minut or something. Activated on receiving a new e-mail.
Have another script that read the newest e-mail every 40-50 seconds. Activated on receiving a new e-mail.

in the e-mail have in the subject or w/e something that can be read, like
```
shutdown (option) now
``` and echo it to the system to be executed.

On start-up /boot-up delete all e-mails to avoid accidental reboot / shutdown.

---

### Post by Lars Noodén on 2011-12-14
> **digitography said:**
> When the computer shuts down, evolution is either still processing the email, or has not let it go for some reason, then when the computer reboots and you restart evolution it tries to shutdown again.

You can give it a little lead time, say 1 minute:

```

/sbin/shutdown +1  

```

---

### Post by digitography on 2011-12-14
> **Lars Noodén said:**
> You can give it a little lead time, say 1 minute:

```

/sbin/shutdown +1  

```
even if I give it lead time, evolution still thinks it processing the email.
As I am now so far forward with the evolution/cron approach, I just need to know how to process the text file and if it is true act upon it.

---

### Post by Lars Noodén on 2011-12-14
You can use [grep](http://manpages.ubuntu.com/manpages/oneiric/en/man1/grep.1posix.html).

```

grep true */tmp/y* >/dev/null && /sbin/shutdown 2 &

```

The two minute lead time gives you a chance to cancel it if there was a mistake while you are logged in.

---

### Post by Lars Noodén on 2011-12-14
> **digitography said:**
> even if I give it lead time, evolution still thinks it processing the email.
As I am now so far forward with the evolution/cron approach, I just need to know how to process the text file and if it is true act upon it.

What happens if you invoke shutdown like this instead?

```

sh -c "/sbin/shutdown 2 &"

```

That should allow sh to complete.

---

### Post by androssofer on 2011-12-14
> **digitography said:**
> Thanks to everyone yet again for some great input.

OK so I took androssofer's approach.
so now I have:
I can send an email with a specific subject, from a specific user, with specific text in the body.
If the condition is met a script is run that modifies a txt file to say "true" ie shutdown. Cron runs a script every 2 mins, however I am still new to this malarky and I am not sure how to go about testing for the condition of the text file?

I tried this

```
if more /home/usename/testforshutdown.txt = "true"
then shutdown -r 1

exit
```
in my simple mind that makes sense, however what happens is the text inside testforshutdown.txt simply gets cleared.
So I am guessing I don't have the syntax right?

Close but no cigar, yet!

I'd say do this way for now to get it running, then work on refining it as mentioned above.

try this for your test code:

```

#!/bin/bash

result=`more /home/username/testforshutdown.txt`

if [[ $result =~ "true" ]]
then
echo "false" > /home/username/testforshutdown.txt
`shutdown -r 1 &`
fi

```

---

### Post by Docaltmed on 2011-12-14
It seems to me that you're going through an awful lot of work to put a gaping hole in your security. 

I use SSH to control a remote server. Through SSH, I can not only shut it down, but control any other parameter of the computer as well. I also don't have to worry about creating a security gap by creating root access where none exists (or should exist).

---

### Post by SeijiSensei on 2011-12-14
Just have the script use touch to create a zero-length file in a location to which Apache has write privileges.  Then in the script use:

```

if [ -f /path/to/the/file ] 
then
   rm -f /path/to/the/file
   shutdown -r now
fi

```

The bash manual ("man bash") includes a list of all the available file checking options in the section entitled "CONDITIONAL EXPRESSIONS".

---

### Post by digitography on 2011-12-15
> **Lars Noodén said:**
> What happens if you invoke shutdown like this instead?

```

sh -c "/sbin/shutdown 2 &"

```That should allow sh to complete.

same result evolution never lets go of the transaction, well that's my interpretation of it.

> Just have the script use touch to create a zero-length file in a  location to which Apache has write privileges.  Then in the script use:

Whoosh! that's the sound of something going completely over my head.

```
#!/bin/bash

result=`more /home/username/testforshutdown.txt`

if [[ $result =~ "true" ]]
then
echo "false" > /home/username/testforshutdown.txt
`shutdown -r 1 &`
fi
```

 has the same result as my attempt, it just clears the text from the file.

As always appreciate all the input, so close, but!

---

### Post by Lars Noodén on 2011-12-15
How about this?

```

#!/bin/sh

if grep true /home/username/testforshutdown.txt ; then
  echo false > /home/username/testforshutdown.txt;
  sudo /sbin/shutdown -h 1 ;
fi
```

---

### Post by digitography on 2011-12-15
Lars, I had just googled something similar, when you posted that. I am now at a different computer, and of course I didn't bookmark the link, however I think we are on to something, although the syntax has me reeling. BTW the above didn't work, just wish I could remember the exact words I googled.

---

### Post by digitography on 2011-12-15
Done some googling and a few very basic tests, and this is what I have.
```
#!/bin/sh

if grep - q "true" "/home/username/testforshutdown.txt" ; then
  echo "false" > /home/username/testforshutdown.txt;
  sudo /sbin/shutdown -h 1 ;
fi
```
Can't test it at the moment, but I think that will work, then all I have to do is make it slick, and then work on the SSH option, and all the other stuff folk have posted. If nothing else this has been a huge learning experience for me, and I thank wholeheartedly all those who have contributed in any way. Will post after testing tomorrow.

---

### Post by digitography on 2011-12-16
Well I can't believe this is actually working at last.

So to sum up.
Filter in evolution set to capture an email with specific subject, sender, and content
This kick off a script that changes the content of a file to "true".
Cron job is running every 2 mins that checks the contents of the file, and acts upon it if it is true, ie shutdown, turnoff or reboot.

The real stumbling block has been that I don't really know what I am doing, you may have guessed this, I am not a programmer, just a persistent bodger.
The syntax of the cron job to test the content of the file had the reeling, bash is cryptic, well it is to me.

Here's what finally worked.

```
#!/bin/sh

export DISPLAY=:0 &&

if grep shutdown /home/derek/testforshutdown.txt;
 then
  echo "false" > /home/derek/testforshutdown.txt;
shutdown -r 2 ;
fi

exit
```I made some elementary mistakes along the way. As I was looking for a specific string, I put the string in 
quotes, but that didn't work, despite looking at loads of examples on the web that did have quotes. It was only out of desperation I tried without, and bingo.

This has been a HUGE learning curve for me, but a very positive one, and I have to say thanks to all of you who offered assistance and ideas.

This won't be the last posting on this thread, because once I have this all tidied up I plan on tackling the SSH approach next, and I think I will need loads of help with that.

A good note to end a Friday afternoon on :)

---

