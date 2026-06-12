---
title: "3000 miles to Ubuntu"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by scrivnerl on 2008-05-16
Ok.  Really not sure where to start so lets start with my history.

I have tried to use Fedora Core 4 and 5 before but found that as a new user this is not the place to start.  Went into Knoppix to build a MythBox but dropped it after finding that a tivo was much easier. I am not a complete newb when it comes to Linux, but the command line is not my strong point so lets just go ahead and say that I am a newb.


Here is the problem.  I am currently working in Iraq, and have decided to build a web server back home in the states, on an old laptop that is just sitting in a closet, so that I can keep in touch with everyone back home.  I want to do a fresh install on the laptop, currently running WinXP.  My wife is at home and will be doing most of the grunt work(plugging in cables and such), but she has no experience with Linux at all.  She can check her email surf the web and burn music cds. 

I want to do a fresh install of Ubuntu prefferably server.  But will have no way to remote during install or even track the progress until the server is built and either install VNC or putty.

The only solution that I have come up with is a VMWARE or a flavor of.  But would like to wipe the hard drive. I have not checked with VMWARE but I was thinking that there was a way to move a Vitual machine to a Physical machine, yes I know i should check there first.  I was hoping that someone could help me out here.

If anybody has any ideas please let me know.

I really dont want my wife to ship the laptop out here, then configure it and ship it back.  The laptop is not in the best of shape physically.

---

### Post by fazavon on 2008-05-16
dude why run it on a laptop. all you have to do is pay for the domain name (9.99$ a year) 

and then look at google apps 

[http://www.google.com/a/help/intl/en/users/user_features.html#utm_medium=et&utm_source=gmail-en&utm_campaign=crossnav&token=gmail_footer](http://www.google.com/a/help/intl/en/users/user_features.html#utm_medium=et&utm_source=gmail-en&utm_campaign=crossnav&token=gmail_footer)

You can do email, website, google docs, shared calendar.. and for free ( minus the cost of the domain name) you rally cannot beat that

---

### Post by rlcomstock3 on 2008-05-16
To solve your problem you can do a remote install of Ubuntu, the live cd can run openssh and you can have your wife get your ip address.  The harder part will be to get her to open up port 22 through your firewall (I am guess you have one because that should be your second machine)  It can all be accomplished.  You will need to be patient with your wife, I have talked my wife through such things and it can be a strain on the relationship. I think your wife would have an easier time installing Ubuntu herself (it is very easy) than opening up the necessary ports.  Then you will need to consider if you have a static IP or a dynamic IP.  If it is dynamic you will need to have her look it up so you can log in.  

Whatever you decide to do good luck, web server are fun!  

Remember to have a strong SSH password, it will get tried hundreds of times a day!

---

### Post by scrivnerl on 2008-05-16
Im not sure exactly what you mean.  But this will not just be a way for me to communicate but a way for me(family) to let everyone else know what I am doing.  Since we dont see or hear from them very much. 

I am not sure what you mean by by a domain name and using Google Apps. 


I also want to get back into Linux and I think that this would be a good start.

---

### Post by scrivnerl on 2008-05-16
Im not sure exactly what you mean.  But this will not just be a way for me to communicate but a way for me(family) to let everyone else know what I am doing.  Since we dont see or hear from them very much. 

I am not sure what you mean by by a domain name and using Google Apps. 


I also want to get back into Linux and I think that this would be a good start.

I will eventually be building a DC, DNS and File server. But thats much later on once I am able to get the Web server up and I am really comfortable with the CLI.

---

### Post by Mud.Knee.Havoc on 2008-05-16
> **scrivnerl said:**
> 
Here is the problem.  I am currently working in Iraq, and have decided to build a web server back home in the states, on an old laptop that is just sitting in a closet, so that I can keep in touch with everyone back home.  I want to do a fresh 

Could you be more specific?  How would having a webserver back home help you keep in touch with people?  If you're interested in hosting a blog or something similar, it would be a lot easier to sign up for WordPress or something like that. 

A webserver won't help your wife burn CDs or surf the internet.  You can very easily install a LAMP server on an old machine with Ubuntu, but it lacks a GUI and related desktop applications.  It might be quite a bit easier if you install normal Ubuntu and then, if you're really interested in the webserver side, install apache.

I think that it might be best to forget the VMWare idea... your poor wife might be getting in over her head.

I apologize if I didn't quite understand your problem (I am admittedly falling asleep as I write this), but if you could clarify exactly what you want to accomplish we might have some ideas.

---

### Post by scrivnerl on 2008-05-16
> **rlcomstock3 said:**
> To solve your problem you can do a remote install of Ubuntu, the live cd can run openssh and you can have your wife get your ip address.  The harder part will be to get her to open up port 22 through your firewall (I am guess you have one because that should be your second machine)  It can all be accomplished.  You will need to be patient with your wife, I have talked my wife through such things and it can be a strain on the relationship. I think your wife would have an easier time installing Ubuntu herself (it is very easy) than opening up the necessary ports.  Then you will need to consider if you have a static IP or a dynamic IP.  If it is dynamic you will need to have her look it up so you can log in.  

Whatever you decide to do good luck, web server are fun!  

Remember to have a strong SSH password, it will get tried hundreds of times a day!


The router wont be much of a problem though I dont have one setup.  I am currently using logmein to remote to my wifes computer.  I will be configuring a Cisco 871W remotely and then have her plug it in before I do all of this. 

It will be pretty tuff to get the wife to do this. As I said she can check her email and surf the web thats about it.  But I think I could write up a document and images using the forums here.  I have looked through the forums the last couple of days and found them to be pretty helpful.

Would the VMWARE thing  not work building a virutal machine up to the point of having it ready with a VNC or putty utility and then wipe the computer and install the server that way or is that not possible to do using somthing like a dvd or external hard drive?

---

### Post by rlcomstock3 on 2008-05-16
Alright...  From what it sounds like to me, you might want to just get domain hosting as was suggested before.  What you are trying to do is possible, it will just be difficult.  You and your wife would learn a lot.

   [http://ubuntuforums.org/showthread.php?t=477526](http://ubuntuforums.org/showthread.php?t=477526)

That might help, but it is rather vague.  Good luck.

---

### Post by rlcomstock3 on 2008-05-16
Didn't see your reply with the vmware concept.  I would avoid vmware.  It would be a nightmare to work with if you run into trouble.  

You might want to try a different distro, Slackware might be the best for what you are trying to do.  With a few minimal command you can have access to the box then do the install yourself.  If can setup the firewall to allow port 22 in it shouldn't be a problem.  

You just need to run an SSH server, then get your IP address at home then ssh into that box, and run whatever you want/need.  (the install initially)

---

### Post by rlcomstock3 on 2008-05-16
Perhaps you have a computers savvy friend?

---

### Post by scrivnerl on 2008-05-16
This is pretty much the same problem that I have except I wont be running wireless.

[http://ubuntuforums.org/showthread.php?t=477526](http://ubuntuforums.org/showthread.php?t=477526)

Wont I be running into the same problem with SLACKWARE as I would with UBUNTU?  Or am I missing something.

---

### Post by niteshifter on 2008-05-16
Hi,

Rather than put your wife through configuring a server install and that a regular server install would be overkill for a laptop base you could:

Install Xubuntu - gives her a GUI to work with for some tasks. But mainly it will install nice and easy. It's also a light weight GUI (Ubuntu = GNOME, takes a bit more horsepower) as you say this is an older laptop and I'm thinking low RAM and low CPU speed are possible problems here.

Then install apache, openssh-server, etc on it. "apt-get" on a command line is easy. The hard part is going to be - any way you do this - configuring apache, sshd, sftp and so forth "remotely" (via phone / mail).

---

### Post by scrivnerl on 2008-05-16
I think that once I get Ubuntu up it wont be much of a problem. Like I said i am using logmein to remote to my wifes computer so I wont need to open any holes in the firewall until I have it configured and ready to put on the internet. 

Its just the initials stages that I am worried about.

---

### Post by scrivnerl on 2008-05-16
> **Mud.Knee.Havoc said:**
> Could you be more specific?  How would having a webserver back home help you keep in touch with people?  If you're interested in hosting a blog or something similar, it would be a lot easier to sign up for WordPress or something like that. 

A webserver won't help your wife burn CDs or surf the internet.  You can very easily install a LAMP server on an old machine with Ubuntu, but it lacks a GUI and related desktop applications.  It might be quite a bit easier if you install normal Ubuntu and then, if you're really interested in the webserver side, install apache.

I think that it might be best to forget the VMWare idea... your poor wife might be getting in over her head.

I apologize if I didn't quite understand your problem (I am admittedly falling asleep as I write this), but if you could clarify exactly what you want to accomplish we might have some ideas.



Just a clarification.  It not jsut for me to communicate with the wife or vice versa but both her family and mine.  I will be the one primarily administering the server but also showing her how to creat web pages as well using a WYSIWYG.  Kinda like having 2 web pages one for her back home and one for me here in Iraq.

I have thought about just building an Ubuntu box and then installing the apapche and sql databases and doing it that way which would problably a much better route.

---

### Post by scrivnerl on 2008-05-16
I guess the Slax idea could be possible. I do have a usb drive that boots slax.  I could configure it here to do everything except webstuff (VNC and SSH) ship it home and have the home change the BIOS of the laptop and then wipe the hard drive remotely and use it as storage and run everything from the USB stick.

Or am I out of line doing it this way?

---

### Post by lazyart on 2008-05-16
It sounds fun and all to do this... but seriously, I would just go to wordpress.com, set up a free blog and be done with it.

---

