---
title: "Have to ssh-add after each reboot"
date: 2014-01-04
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2014-01-04
Hi Guys,

I'm on Ubuntu 12.04 32bit

This is weird.
I was going along enjoying life using a script to upload files to my website when all of a sudden (I think after an Ubuntu update) I couldn't login to my server via the script.
The script uses lftp and I've saved my key in the ~/.ssh directory.
Well I thought it was about time to make a new key anyway, seeing as it is now 2014, so I did.

I still couldn't login.  I get the error ```
permission denied (publickey). 
```
I don't understand what this means.

So I went to my hosting company's site and did some reading.  I noticed that in order to ssh into their server from linux I should run
ssh-add and point to my key.

I did that and could indeed login.
What's more my script started working again...kind of.

The really strange thing is if I call the script by clicking on the quick list I put in Ubuntu's dock like thing, the terminal opens up and I see the message that this script is for uploading files etc. Press enter to run.  I press enter and get permission denied (publickey). 
 
If I open a terminal and type the name of the script, (which is Phoca_upload) into the terminal then hit enter I see the same message that this script is for uploading files and to press enter to actually upload the files.  I do and everything works as it should.

Now here is another odd thing.  I noticed that after rebooting the machine I could not get the script to work no matter what.  So I ran ssh-add again and things began working.
After doing this five or six times, I'm convinced that my system is not saving my key when I shut down.

Does anyone know why this might be?
My two questions are:

1. Why would a script run if I type the name of the script in the terminal, but not if I call the script from a quicklist (that is for sure launching the exact same script)?
2. How I can get my system to save my key so I do not have to ssh-add each time I start the machine?

---

### Post by GrouchyGaijin on 2014-01-05
[COLOR=#ff0000][B]UPDATE


[/B][/COLOR]I solved the problem.
I vaguely remember having to do this last time I wanted to set up keys for the lftp script, but had forgotten.

Basically, I use [SiteGround]("http://www.siteground.com/index.htm?afbannercode=2b701e544e0bd8261f4c0b0197f023a1") for my hosting company and they are pretty good considering how inexpensive they are.
They really stress that you generate ssh keys using the tool in their control panel on their site.

That seems to have been the problem.

The minute I generated my own key and uploaded my public key to their server, everything began working again.
In case you don't know the command to generate a key (in the format that SiteGround wants) is:
```
***ssh-keygen -t dsa***
```

They do actually provide instructions on how to do this, but everything else on their site steers you toward using the control panel to generate a key.
Following the instructions on the control panel, did result in a key that worked with Filezilla.  LFTP, however, kept getting the publickey error.  It wasn't until I made my own key and uploaded the public key to their server that I was able to get things to work.

[http://kb.siteground.com/generate_ssh_key_in_linux/](http://kb.siteground.com/generate_ssh_key_in_linux/)

---

