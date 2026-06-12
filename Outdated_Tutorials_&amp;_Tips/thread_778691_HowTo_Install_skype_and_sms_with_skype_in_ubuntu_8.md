---
title: "HowTo: Install skype and sms with skype in ubuntu 8.04"
date: 2008-05-02
forum: Outdated Tutorials &amp; Tips
---

### Post by grobar on 2008-05-02
**1. Skype installation**
a. Get skype (choose Ubuntu 7.04+)
[http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)
Now you have file skype-debian_2.0.0.68-1_i386.deb on your desktop(default location to save your file with firefox)
b. Right click on the file and chose open with "GDebi Package Installer".
c. Skype is installed now, check in the top left corner under applications---internet---skype

2. **Send SMS(text messages) with skype: Download Skype4py**

a.Go to [http://sourceforge.net/project/showfiles.php?group_id=202148](http://sourceforge.net/project/showfiles.php?group_id=202148) and download only Skype4Py-1.0.29.0.tar.gz file
b. right click on the file and chose extract here
c. go to this directory where you just extracted files and type "sudo python setup.py install" (without "") in the terminal (applications--accessories---terminal)

3. a.Download [http://www.kolmann.at/philipp/linux/skysentials/skysentials-1.0.1.tar.gz](http://www.kolmann.at/philipp/linux/skysentials/skysentials-1.0.1.tar.gz) 
b. right click on the file and chose extract here
c. open skype 
d. go to this directory where you just extracted files in 3.b and run program with ./skysentials.py in the terminal(or sudo python skysentials.py)

Enjoy!:guitar:

---

### Post by mick.ng on 2008-05-03
Thanks. Got skype installed and working great. A dumb question- Do we have to pay to send txt (internationally) using Skype4Py?

---

### Post by mjoksa on 2008-05-05
Ok, this is my problem: 
I am new with Ubuntu (or any other Linux) and I try to migrate to it. I am thrilled with it possibilities but my problem is Skype. I followed instructions on how to install Skype on Ubuntu 8.04 but it failed because my Ubuntu is x64. Can anyone tell me how to enable 32b programs on Ubuntu 8.04 x64 and how to install Skype?
10x

---

### Post by Steve.G on 2008-05-05
Ok, I got through all of the steps, and Skype comes up and asks for permission for a program to connect to it. So far so good, it launches, but then:

When I type in a phone number for it to check (regardless of the number) It just hangs..

```
Traceback (most recent call last):
  File "/tmp/skype/skysentials-1.0.1/SendSMS.py", line 121, in check_number
    self.mysms = self.skype.CreateSms('OUTGOING', number)
  File "/usr/lib/python2.5/site-packages/Skype4Py/skype.py", line 630, in CreateSms
    return ISmsMessage(chop(self._DoCommand('CREATE SMS %s %s' % (MessageType, ', '.join(TargetNumbers))), 2)[1], self)
  File "/usr/lib/python2.5/site-packages/Skype4Py/skype.py", line 360, in _DoCommand
    raise ISkypeError(int(errnum), errstr)
Skype4Py.errors.ISkypeError: [Errno 583] SMS: CREATE SMS takes a list of phone numbers
```

---

### Post by grobar on 2008-05-10
I always enter a country code e.g. 00 44 + phone number (to send a SMS to UK) or 00 1 + phone number (for US) even if you live in of the countries that I mentioned above... Did you try that?

> **Steve.G said:**
> Ok, I got through all of the steps, and Skype comes up and asks for permission for a program to connect to it. So far so good, it launches, but then:

When I type in a phone number for it to check (regardless of the number) It just hangs..

```
Traceback (most recent call last):
  File "/tmp/skype/skysentials-1.0.1/SendSMS.py", line 121, in check_number
    self.mysms = self.skype.CreateSms('OUTGOING', number)
  File "/usr/lib/python2.5/site-packages/Skype4Py/skype.py", line 630, in CreateSms
    return ISmsMessage(chop(self._DoCommand('CREATE SMS %s %s' % (MessageType, ', '.join(TargetNumbers))), 2)[1], self)
  File "/usr/lib/python2.5/site-packages/Skype4Py/skype.py", line 360, in _DoCommand
    raise ISkypeError(int(errnum), errstr)
Skype4Py.errors.ISkypeError: [Errno 583] SMS: CREATE SMS takes a list of phone numbers
```

---

### Post by grobar on 2008-05-10
> **mick.ng said:**
> Thanks. Got skype installed and working great. A dumb question- Do we have to pay to send txt (internationally) using Skype4Py?


Yes, before you send a SMS you'll see the price for 1 text message=160 characters!

But it's still cheaper than your own phone provider ! ;)

---

### Post by havilandw on 2008-05-19
Thanks!  Very much appreciated.:popcorn:

---

### Post by Timbothecat on 2008-06-01
Hi Guys.

Just wanted to know if anyone else has had the problem of skype closing when you try to run the webcam.

I'm going to "Options" to set things up and when I go to test the video it just shuts down (as per usual giving no explanation). If anyone else has had this and/or knows how to fix it I'd love to hear from you.

All the best.

Tim.

---

### Post by PA_Dummy on 2008-06-02
dum de dum dum !!

I downloaded the above Skype file:

I got the following message from the skype installer:

          Error:  Wrong architecture i386

I guess my AMD 64 needs a different version.

](*,)

---

### Post by Timbothecat on 2008-06-02
> **PA_Dummy said:**
> dum de dum dum !!

I downloaded the above Skype file:

I got the following message from the skype installer:

          Error:  Wrong architecture i386

I guess my AMD 64 needs a different version.

](*,)

I'm pretty sure there isn't a 64Bit version of Skype as yet. Although, apparently some people on here have had success with getting it to run.

Try this: [http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295) . I haven't done it cause I don't have 64 bit architecture but apparently it works.

---

### Post by the sailor on 2008-06-08
hi...
my installation went smoothly...
but when am trying to send an sms it gives me the error message; cannot connect to server

can someone plz help.
thx

---

### Post by poccino on 2008-06-09
I upgraded to Ubuntu hardy. I am presently using kernel # 2.6.24.18 (I got rid of the newest since my PC didn't boot).
I can hear others' voice but they don't hear mine.
I regularly fail my test-call.
Any help, please?

---

### Post by sophie27 on 2008-07-07
I have **UBUNTU 8.04** and a **64bit** system: i've just sent my first sms, it works!
Thank you!!!!!!!!:)

---

### Post by Rafal07BC on 2008-07-09
I have installed skype and program is working but I have problem with microphone.
Microphone in system is working. I can hear myself in the speakers. But when I use skype it is not transmitting input from microphone (nobody can hear me).

Any ideas how to fix this?

---

### Post by jagannath on 2008-07-10
Hi guys,

I'm getting the following error message while installing skype:

sudo python /home/jagannath/Desktop/skysentials-1.0.1/skysentials.py
skysentials.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

Anyone knows the fix??

Thanks,

Jagannath

---

### Post by Jason.dude on 2008-07-13
> **sophie27 said:**
> I have **UBUNTU 8.04** and a **64bit** system: i've just sent my first sms, it works!
Thank you!!!!!!!!:)


Congratulations!

Could you please share the magic with me?  I'm not a programmer so I get a bit confused when phrases like "type this code into the directory where you opened it (skype)" are used.  I have been trying to get skype installed for a few hours with no luck so far.  Hope you have a life preserver you can throw me!!!  :-)

Thanks!

---

### Post by Ralph Corderoy on 2008-07-14
It would be nice to see Skype team up with Canonical to get Skype into the standard `commercial' repository, in a similar way to VMware IIRC.  I'd rather avoid installing from deb files if possible, as the headache come upgrades of not knowing what's littered around your filesystem isn't worth it in the long run.  GNU stow can help, but best of all would be for Skype to push for `official' status.

---

### Post by lolobu on 2008-07-14
No need to install it from a deb, Skype is under Medibuntu repository.

---

### Post by grobar on 2008-07-21
There's a new version of Skype4py. I edited step 2. just reffering to this new version, the rest remains the same...

---

### Post by jmjohn on 2008-08-04
> **Jason.dude said:**
> Congratulations!

Could you please share the magic with me?  I'm not a programmer so I get a bit confused when phrases like "type this code into the directory where you opened it (skype)" are used.  I have been trying to get skype installed for a few hours with no luck so far.  Hope you have a life preserver you can throw me!!!  :-)

Thanks!
First, have a look at the first post in the thread.  Next.

Skyessentials, the SMS program, is a python program that hooks into the already running Skype program that you have installed from the repositories and are running.  In order to execute python programs, you have to use the "python myfile.py" command.  In this case, the .py file can be found after navigating to the unzipped file.  You would navigate to that directory in the terminal using the cd /where/I/Put/My/.py file then you could "sudo python file.py"

First you have to run the Skype4Py main .py file which allows Skype to execute .py scripts, then you have to run the skyessentials.py file while Sype is running, both executed using the "python" command.

-glass.dimly

---

### Post by mat.elis on 2008-08-06
a. Get skype (choose Ubuntu 7.04+)
[http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)
Now you have file skype-debian_2.0.0.68-1_i386.deb on your desktop(default location to save your file with firefox)
b. Right click on the file and chose open with "GDebi Package Installer".
c. Skype is installed now, check in the top left corner under applications---internet---skype

2. **Send SMS(text messages) with skype: Download Skype4py**

a.Go to [http://sourceforge.net/project/showfiles.php?group_id=202148](http://sourceforge.net/project/showfiles.php?group_id=202148) and download only Skype4Py-1.0.29.0.tar.gz file
b. right click on the file and chose extract here
c. > go to this directory where you just extracted files and type "sudo python setup.py install" (without "") in the terminal (applications--accessories---terminal)

3. a.Download [http://www.kolmann.at/philipp/linux/skysentials/skysentials-1.0.1.tar.gz](http://www.kolmann.at/philipp/linux/skysentials/skysentials-1.0.1.tar.gz) 
b. right click on the file and chose extract here
c. open skype 
d. > go to this directory where you just extracted files in 3.b and run program with ./skysentials.py in the terminal(or sudo python skysentials.py)


**Sorry people, I have problems with the "go to this directory" instruction... how does that work? In the terminal?** :confused:

---

### Post by WenSes on 2008-08-09
The 64bit version of skype is available for download from medibuntu repositories. I've been using in it and no problems (excepting that I'm still not able to use my webcam in it). 

You can go to medibuntu.org to read about how to adding this repository. 

After that, you can use this howto as it goes in the first post. 

C-ya and thxs to the author of this guide!

---

### Post by sir_skiner on 2008-08-11
how to relate skype whith links in the browser?

---

### Post by lapiloeg on 2008-08-22
Hi, I am new in Ubuntu.
I tried to install skype for ubuntu 7.04+ and open it as it is mentioned:
with GDebi package installer.

The error is: Dependency is not satisfiable. libqt4-core.

I appreciate your help

Thanks

---

### Post by spudgunner on 2008-09-07
I got Skype installed, but for some reason the "Sign In" button is not click-able, so I'm kinda stuck... and suggestions?

Nevermind, I had the wrong username and apparently the "Sign In" button doesn't become clickable until that info is right

---

### Post by fizzyric on 2008-09-23
Hi, I have Ubuntu Hardy Heron (recently installed) and am trying to install Skype. I've followed the various tips for obtaining it, but when I download and try to install the file skype-debian_2.0.0.72-1_i386.deb using the package installer, the status appears as: Error:Wrong Architecture 'i386'.

I can also not find Skype in the Synaptic Package Manager.

I'm pretty new to Linux and so wouldnt be surprised if Im missing somethiing obvious - but can anyone help?

Thanks
R

---

### Post by puttingau on 2008-09-29
> try to install the file skype-debian_2.0.0.72-1_i386.deb using the package installer, the status appears as: Error:Wrong Architecture 'i386'.


If you're still trying:
Look at [http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs)
RavanH's post about half way down, regarding installing skype

I started following this, using:
sudo dpkg -i --force-architecture skype*.deb

for my amd64, and it gave me an error message about QT dependencies.
I installed these using Synaptic, then used the above dpkg command again, and Skype was installed. I did not need to use getlibs (the reason for that thread).

---

### Post by ceverett on 2008-10-06
> **Steve.G said:**
> Ok, I got through all of the steps, and Skype comes up and asks for permission for a program to connect to it. So far so good, it launches, but then:

When I type in a phone number for it to check (regardless of the number) It just hangs..

```
Traceback (most recent call last):
  File "/tmp/skype/skysentials-1.0.1/SendSMS.py", line 121, in check_number
    self.mysms = self.skype.CreateSms('OUTGOING', number)
  File "/usr/lib/python2.5/site-packages/Skype4Py/skype.py", line 630, in CreateSms
    return ISmsMessage(chop(self._DoCommand('CREATE SMS %s %s' % (MessageType, ', '.join(TargetNumbers))), 2)[1], self)
  File "/usr/lib/python2.5/site-packages/Skype4Py/skype.py", line 360, in _DoCommand
    raise ISkypeError(int(errnum), errstr)
Skype4Py.errors.ISkypeError: [Errno 583] SMS: CREATE SMS takes a list of phone numbers
```

I am having this same problem: click the "Check Number" button and a few minutes later SkySentials hangs completely. :confused:

**Update: ** Never mind, I figure out that you have to run SkySentials with sudo.  Works a treat.  Now trying to be able to use SUID instead of sudo.  Not working yet.

---

### Post by hey_ram on 2008-10-06
thanx for the tutorial!!!

skype is now up and running on my system...
and without any troubles!!!

---

### Post by ceverett on 2008-10-07
> **grobar said:**
> **1. Skype installation**
a. Get skype (choose Ubuntu 7.04+)
[http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)
Now you have file skype-debian_2.0.0.68-1_i386.deb on your desktop(default location to save your file with firefox)
b. Right click on the file and chose open with "GDebi Package Installer".
c. Skype is installed now, check in the top left corner under applications---internet---skype

2. **Send SMS(text messages) with skype: Download Skype4py**

a.Go to [http://sourceforge.net/project/showfiles.php?group_id=202148](http://sourceforge.net/project/showfiles.php?group_id=202148) and download only Skype4Py-1.0.29.0.tar.gz file
b. right click on the file and chose extract here
c. go to this directory where you just extracted files and type "sudo python setup.py install" (without "") in the terminal (applications--accessories---terminal)

3. a.Download [http://www.kolmann.at/philipp/linux/skysentials/skysentials-1.0.1.tar.gz](http://www.kolmann.at/philipp/linux/skysentials/skysentials-1.0.1.tar.gz) 
b. right click on the file and chose extract here
c. open skype 
d. go to this directory where you just extracted files in 3.b and run program with ./skysentials.py in the terminal(or sudo python skysentials.py)

Enjoy!:guitar:

OK, now to make Skysentials work without having to run sudo:
[LIST=1]
[*]open a terminal


[*]switch to the directory you unarchived skysentials into


[*]create a directory to put the skysential files into and make it globally accessible:
```
sudo mkdir /usr/local/lib/skysentials
sudo chmod 777 /usr/local/lib/skysentials
```
[*]copy all the executables to /usr/local/bin like this:
```
sudo cp *.py* /usr/local/lib/skysentials
```
[*]now we need a short script to run skysentials; open your favorite text editor using sudo and enter this:
```
#!/bin/sh
cd /usr/local/lib/skysentials
python /usr/local/lib/skysentials/skysentials.py
```
and save it to /usr/local/bin/skysentials


[*]Now set the script's suid bit thusly:
```
sudo chmod 4755 /usr/local/bin/skysentials
```
[*]Now we get Skype to fire up skysentials whenever it cranks up:

   a. Open up skype options
   b. click "Notifications" on the left side
   c. select "Skype Login" in the main selection box 
   d. Click the "Advanced View" button on the right
   e. Check the box labeled "Execute the following script"
   f. in the textbox underneath, type in /usr/local/bin/skysentials
   g. click the "Apply" button


[*]Now test by pressing the "Test Event" button, you should see the Skysentials box appear on screen.


[*]Now whenever you log into Skype, Skysentials should appear automatically.
[/LIST]

---

### Post by Toimu on 2008-10-23
> **lapiloeg said:**
> Hi, I am new in Ubuntu.
I tried to install skype for ubuntu 7.04+ and open it as it is mentioned:
with GDebi package installer.

The error is: Dependency is not satisfiable. libqt4-core.

I appreciate your help

Thanks

I have the same problem.  Found some info here:

[http://ubuntuforums.org/showthread.php?t=476053](http://ubuntuforums.org/showthread.php?t=476053)

Haven't read threw it all though.

---

### Post by IainPurdie on 2009-01-19
Just a quick message to thank the original author and the person who provided the instructions to make the SMS facility fire up on Skype loading.

The lack of SMS on Skype was one of the very few reasons I still have XP on my laptop - you've made my life a lot easier as it not means I don't have to reboot into Windows once in a while to send an SMS internationally!

I hope nobody minds, but I'm going to pinch the instructions and pop them on my blog. One more place for people to find them. Of course, a link here will be included as will full credit to the authors.

Now, if someone'll come up with a really good video editor for Ubuntu, I'm sorted...

---

### Post by mdewet on 2009-01-19
I used this to set up skype on my hardy x64

[http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/](http://technical-itch.co.uk/2007/09/18/how-to-install-skype-on-ubuntu/)

---

### Post by anlag on 2009-04-07
> **ceverett said:**
> OK, now to make Skysentials work without having to run sudo:
[LIST=1]
[*]open a terminal


[*]switch to the directory you unarchived skysentials into


[*]create a directory to put the skysential files into and make it globally accessible:
```
sudo mkdir /usr/local/lib/skysentials
sudo chmod 777 /usr/local/lib/skysentials
```
[*]copy all the executables to /usr/local/bin like this:
```
sudo cp *.py* /usr/local/lib/skysentials
```
[*]now we need a short script to run skysentials; open your favorite text editor using sudo and enter this:
```
#!/bin/sh
cd /usr/local/lib/skysentials
python /usr/local/lib/skysentials/skysentials.py
```
and save it to /usr/local/bin/skysentials


[*]Now set the script's suid bit thusly:
```
sudo chmod 4755 /usr/local/bin/skysentials
```
[*]Now we get Skype to fire up skysentials whenever it cranks up:

   a. Open up skype options
   b. click "Notifications" on the left side
   c. select "Skype Login" in the main selection box 
   d. Click the "Advanced View" button on the right
   e. Check the box labeled "Execute the following script"
   f. in the textbox underneath, type in /usr/local/bin/skysentials
   g. click the "Apply" button


[*]Now test by pressing the "Test Event" button, you should see the Skysentials box appear on screen.


[*]Now whenever you log into Skype, Skysentials should appear automatically.
[/LIST]


Unfortunately this doesn't seem to work for me. I tried it first with the .py files in ~/Apps/skysentials-1.0.1 and the shell script in ~/bin, as I prefer to keep these stuff easily portable when I migrate (and bring my ~.) However, realizing that root might have problem seeing the directories that way (despite chown, chgrp, chmod +s) in my home, I followed your howto to the letter - copy/pasting every command. The result with both methods is the same - it crashes with segmentation fault in the same manner as if I try to run skysentials from the default directory without sudo. However, if I prepend the newly made script (yours) with a sudo, it works. So the commands in themselves are apparently in order, but the permissions... perhaps not. Any ideas?

---

### Post by Paddy Landau on 2009-04-10
Thank you so much, grobar, for creating this thread!

Regarding running Skysentials under sudo...

I ran it under sudo the first time, as per the instructions. Thereafter, I've created a menu option (System -> Preferences -> Main Menu):
```
<directory>/skysentials-1.0.1/skysentials.py
```(Obviously, replace <directory> with the name of the directory where you extracted skysentials.) Note that this is without sudo...

It seems to run fine with an occasional hang (as I hardly ever send SMS, that's fine by me).

However, if you want to run it with sudo, use this command instead:
```
gksudo <directory>/skysentials-1.0.1/skysentials.py
```(Note "gksudo" instead of "sudo".)

HTH

---

### Post by xyepblra on 2009-04-13
I followed the HOWTO from the step 2, since I have had Skype installed already, and I followed it precisely, but nothing worked for me. I sent out 4 messages to my own mobile (China Mobile), but none of them were received.

---

### Post by Paddy Landau on 2009-04-14
> **xyepblra said:**
> I followed the HOWTO from the step 2, since I have had Skype installed already, and I followed it precisely, but nothing worked for me. I sent out 4 messages to my own mobile (China Mobile), but none of them were received.
My first test to my own mobile didn't work. After  I'd sent a test to a different mobile, then it all started working for me, although there was a short delay at first.

---

### Post by xyepblra on 2009-04-14
> **Paddy Landau said:**
> My first test to my own mobile didn't work. After  I'd sent a test to a different mobile, then it all started working for me, although there was a short delay at first.I see. The problem is, it's been more than 5 hours since the first test, and no messages have been received neither by me nor by my wife. According to your definition, "one's own mobile" is the one stipulated in one's user details in Skype, right?

---

### Post by Paddy Landau on 2009-04-14
> **xyepblra said:**
> According to your definition, "one's own mobile" is the one stipulated in one's user details in Skype, right?
Right.

Have you tested sending an SMS from a Windows machine with the latest version of Skype? That way you'd know whether it was Skysentials or something else causing the problem.

If that still doesn't resolve the question, then sorry, I don't know how to continue from here. I wonder if the [Skype Community Forums]("http://forum.skype.com/") would have an answer for you?

---

### Post by gregbzh on 2009-04-15
Hi.  I can't get skysentials to start.  My terminal shows the following:

greg@rua:~/Skype/skysentials-1.0.1$ sudo python skysentials.py
Warning! Middle of message received with no beginning!
Warning! Middle of message received with no beginning!
Warning! Middle of message received with no beginning!
Warning! Middle of message received with no beginning!
Warning! Middle of message received with no beginning!
Warning! Middle of message received with no beginning!
Warning! Middle of message received with no beginning!
Warning! Middle of message received with no beginning!
Warning! Middle of message received with no beginning!
Warning! Middle of message received with no beginning!
Warning! Middle of message received with no beginning!
Warning! Middle of message received with no beginning!
Warning! Middle of message received with no beginning!
Warning! Middle of message received with no beginning!


Any ideas?  I'm another person who sends overseas SMS regularly and have to use Windows to do so, so I'd really like to get this working.

Thanks.

---

### Post by xx58 on 2009-04-28
2. **Send SMS(text messages) with skype: Download Skype4py**

a.Go to [http://sourceforge.net/project/showf...roup_id=202148]("http://sourceforge.net/project/showfiles.php?group_id=202148") and download only Skype4Py-1.0.29.0.tar.gz file
b. right click on the file and chose extract here
c. go to this directory where you just extracted files and type "sudo python setup.py install" (without "") in the terminal (applications--accessories---terminal)

I download this package. Then I extract it. Then I had problems: " Where is directory and where in Directory I can write this command? Can somebody give me exact directions. I am new at Linux. Please help me!

---

### Post by IainPurdie on 2009-04-28
Hey xx58 - don't panic! :)

As it happens, I just noticed my copy's not working so I'm re-downloading it. I documented how to do it the last time on my blog. I go into a little more detail than the initial post here, though that's where I got the information from.

[http://www.moshblog.me.uk/2009/01/19/sending-sms-from-ubuntu-skype/](http://www.moshblog.me.uk/2009/01/19/sending-sms-from-ubuntu-skype/)

If that's still not clear enough, drop another post on here and I'll do my best to help.

---

### Post by IainPurdie on 2009-04-28
Grr.

I am now getting the same problem as "anlag" a few posts back. Whereas I had this working perfectly from the off, I am now receiving a segmentation fault if I don't run using sudo.

I've not changed versions, moved folders, changed directory permissions or anything. What I *have* done is upgrade from 8.10 to 9.04 Jaunty. I wonder if thus has affected things somehow?

Going to strip skysentials out then reinstall from scratch following the instructions again. See if that helps.

**Update:** Nope. Makes no difference. Anyone?

---

### Post by xx58 on 2009-04-28
I download and then Extracted and then I open Terminal and writing command    	 	 	 	 	 	  sudo python skysentials.py and then coming message: "No such File or Directory".
I don't know, what do next..., but I am really want have this sms sending tool from Skype

---

### Post by IainPurdie on 2009-04-28
OK, what you need to do is get *into* the folder you extracted.

Where did you download the file to? In Firefox I default to downloading to my desktop. You may download to a Downloads folder, or something. We need to know where that is. Alternatively - this may work - open the folder on the desktop and then right click on the window. Is there an option "Open In Terminal"? If so, click it and a terminal will open with you already in the correct place to enter the "python..." command.

Failing that, as I said, we need to know where the folder is that you're downloading to. When you save the file from Firefox (again, I assume you are using Firefox!) you are given the choice of where to save the file to. The "path" to that folder is displayed above the file list when you "Save As". On mine, it's in the form of little boxes. If the leftmost one is an arrow, click it to display the full path. As an example, mine would be /home/iain/Desktop (note that capitals are important).

Yours may be something else, like /home/xx58/Downloads

Armed with this information, open a terminal. Then enter:

cd /home/xx58/Downloads/skysentials-1.0.1

I think the skysentials name there is right. It's the name of the folder with the files in. Once in there, issue the command you were struggling with.

You'll have to repeat this for the Skype4.... package as well. 

I know it all seems complex at first, but all you're doing is navigating through directories using text instead of pictures. Where you're click "go up a folder" or the up arrow, you would instead type "cd .."

Where you'd double-click on a folder, you'd type "cd <foldername>"

You can string those folders together so instead of:

cd folder1
cd folder2

You could do:

cd folder1/folder2

Note that the folder "/" is the "root" folder. The one at the top of the tree if you like. "cd /" will take you there. And preceding your cd command with a "/" will ensure you start there. Example:

cd /folder1/folder2

will take you from the top of the tree down the given path. Whereas:

cd folder1/folder2

will take you down the path from *your current location*.

I promise it's easy once you get your head around it! The other useful command is:

ls

This lists the contents of a folder and helps you get your bearings or figure out where to go next.

The main trick is to find out your start point i.e. where you've downloaded the files to. And then to connect in your mind navigating by clicking and navigating by text. It's the same thing, but using two different methods :)

I hope this helps! Learning to use the terminal is pretty much an essential part of the Ubuntu experience if you're going to do more than just use the installed utilities. Don't stress about it - there are plenty of people on here who'll help!

---

### Post by xx58 on 2009-04-28
I download it to Desktop

---

### Post by IainPurdie on 2009-04-28
Then the instruction you'll want will be:

cd /home/xx58/Desktop/skysentials-1.0.1

or similar. Again, replace "xx58" with your logon name and check the name of the skysentials folder. I can't recall exactly what name it's given when it's extracted.

---

### Post by xx58 on 2009-04-28
alain@alain-laptop:~$ cd/home/alain/Desktop/Skype4Py-1.0.31.0
bash: cd/home/alain/Desktop/Skype4Py-1.0.31.0: No such file or directory
alain@alain-laptop:~$ 

Nothing going right

---

### Post by IainPurdie on 2009-04-28
You need a space between "cd" and what follows:

cd /home/alain/Desktop/Skype4Py-1.0.31.0

---

### Post by IainPurdie on 2009-04-28
You need a space between "cd" and what follows:

cd /home/alain/Desktop/Skype4Py-1.0.31.0

---

### Post by xx58 on 2009-04-28
Run the 3 following comands.....
I run, but cannot understand where I can find now this code?
How I can save /usr/local/bin/skysentials ?
Don't know anything.....

---

### Post by IainPurdie on 2009-04-28
Check the blog post I referred you to earlier. It details how you can create a shortcut in your Applications menu so you can use the program any time you like.

---

### Post by xx58 on 2009-04-28
I read, but don't understand just. How I can save file as /usr/local bin/skysentials
I open Openoffice writer and write everything to this file  and then I want save as and that not happened.... Cannot understand how to save it as /usr/local bin/skysentials ? 
I am already to half way, little bit more .....

---

### Post by IainPurdie on 2009-04-28
The simplest way is from the command line:

sudo gedit /usr/local/bin/skysentials

This opens an editor on the desktop. Copy and paste or retype the commands listed on the blog post. When done, close the editor and save the changes. That creates the "skysentials" file in the correct place.

Hope this helps! As before, just post if you get stuck again. I know this might seem confusing, but it's the best way to learn :)

---

### Post by navyrunner on 2009-04-28
Thanks for the infro, do you know how to make skype work with the ubuntu 9.4
Thanks for your help

> **grobar said:**
> **1. Skype installation**
a. Get skype (choose Ubuntu 7.04+)
[http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)
Now you have file skype-debian_2.0.0.68-1_i386.deb on your desktop(default location to save your file with firefox)
b. Right click on the file and chose open with "GDebi Package Installer".
c. Skype is installed now, check in the top left corner under applications---internet---skype

2. **Send SMS(text messages) with skype: Download Skype4py**

a.Go to [http://sourceforge.net/project/showfiles.php?group_id=202148](http://sourceforge.net/project/showfiles.php?group_id=202148) and download only Skype4Py-1.0.29.0.tar.gz file
b. right click on the file and chose extract here
c. go to this directory where you just extracted files and type "sudo python setup.py install" (without "") in the terminal (applications--accessories---terminal)

3. a.Download [http://www.kolmann.at/philipp/linux/skysentials/skysentials-1.0.1.tar.gz](http://www.kolmann.at/philipp/linux/skysentials/skysentials-1.0.1.tar.gz) 
b. right click on the file and chose extract here
c. open skype 
d. go to this directory where you just extracted files in 3.b and run program with ./skysentials.py in the terminal(or sudo python skysentials.py)

Enjoy!:guitar:

---

### Post by IainPurdie on 2009-04-28
It should work "out of the box" on 9.04 - it's working fine on mine. I installed under 8.04 or 8.10 (can't recall which) and upgraded as the months went by.

---

### Post by xx58 on 2009-04-28
How I can make shortcut at application menu? Where this application menu locating? I am very end now...

---

### Post by xyepblra on 2009-04-28
> **Paddy Landau said:**
> Have you tested sending an SMS from a Windows machine with the latest version of Skype? That way you'd know whether it was Skysentials or something else causing the problem.You're right, Paddy Landau, from the fact that I haven't received the text I sent from Skype under Windows I see the problem was not in Skysentials. Although money were charged in both cases.

---

### Post by Paddy Landau on 2009-04-29
> **xx58 said:**
> How I can make shortcut at application menu? Where this application menu locating? I am very end now...

[LIST=1]
[*]System -> Preferences -> Main Menu
[*]Click "Internet" on the left side.
[*]Press "New Item"
[*]Fill in as follows.
[LIST]
[*]Type: **Application**
[*]Name: **Skype SMS** (or whatever you want)
[*]Command: **gksudo /home/xx58/skysesntials-1.0/skysentials.py** (change the directory to wherever you saved the program)
[*]Comment: **Send SMS through Skype** (or whatever you want)
[/LIST]
 
[*]Press the logo button (the little springboard to the left of "Type"). Type **/usr/share/icons/skype.png** and press **OK**.
[*]Press **Close**.
[*]Press **Close** again.
[/LIST]
Now you should find it in your menu.

---

### Post by Paddy Landau on 2009-04-29
> **xyepblra said:**
> You're right, Paddy Landau, from the fact that I haven't received the text I sent from Skype under Windows I see the problem was not in Skysentials. Although money were charged in both cases.
Query Skype support about the text that you sent from Windows. Unfortunately, on occasion it can be a little unreliable. The fault may not lie with Skype; it may be your another network after it's left Skype's network.

---

### Post by xx58 on 2009-04-29
I would like to tank everyone who help me to install Skype SMS. Now it working very good. Thank you friends from Linux Ubuntu Forum

---

### Post by xyepblra on 2009-05-04
> **Paddy Landau said:**
> ...it may be your another network after it's left Skype's network.
...which is China Mobile, I guess.
Not the most responsible and user-friendly company in the world...

---

### Post by IainPurdie on 2009-05-04
> **xx58 said:**
> I would like to tank everyone who help me to install Skype SMS. Now it working very good. Thank you friends from Linux Ubuntu Forum

You're welcome! I just noticed you're in Estonia. You should go and visit the Skype offices. They are based in Tallinn - lovely city :)

---

### Post by grobar on 2009-05-05
Thanks to everybody for keeping this topic up to date!

G

---

### Post by mdurham on 2009-05-13
It doesn't appear to work on Karmic. I can't type into the SMS text edit box but I can enter a number into the tel. no. field. Works fine on Jaunty though.
Cheers, Mike

---

### Post by IainPurdie on 2009-05-13
> **mdurham said:**
> It doesn't appear to work on Karmic

Here's hoping that gets fixed by either the app author or the OS coders. Thanks for the heads up. After my crippling of my system performance-wise since shifting to Jaunty I'll definitely be running a test upgrade of Karmic when the final release comes out.

Queensland, eh? Swap you. I miss the sunshine!

---

### Post by mdurham on 2009-05-13
> **IainPurdie said:**
> Here's hoping that gets fixed by either the app author or the OS coders. Thanks for the heads up. After my crippling of my system performance-wise since shifting to Jaunty I'll definitely be running a test upgrade of Karmic when the final release comes out.

Queensland, eh? Swap you. I miss the sunshine!

Ian, shifting to Jaunty hasn't made much difference to me, I don't find it slower at all. I wonder what happened to your system? Oh, and no deal on the swap, sorry about that. You do know it's winter here now don't you? The temp has gone right down to 26 :)
Cheers, Mike

---

### Post by IainPurdie on 2009-05-14
> **mdurham said:**
> Ian, shifting to Jaunty hasn't made much difference to me, I don't find it slower at all. I wonder what happened to your system?

Fairly certain it's memory handling and/or the incredibly dodgy Intel 915 drivers. There are a lot of posts about them as well as fixes involving installing Release Candidate kernels... which don't include drivers for the wifi card I use. I'll wait until a proper release, but it's just shocking to have XP on here that runs more smoothly than Ubuntu.

Anyway, off-topic. I shall shut up. Especially as I'll have a right go at you about the weather is I don't :p (roll on July - back to SE Asia!)

---

### Post by Paddy Landau on 2009-05-14
> **mdurham said:**
> I can't type into the SMS text edit box but I can enter a number into the tel. no. field.
You know that after you enter the number (including the country code), you need to press "Check Number" first? If "Check Number" changes to "Send SMS", then you should be able to enter text; if not, then check your telephone number.

---

### Post by LindaLou on 2009-06-02
I followed the instructions originally posted here (page 1) and when I opened with deb I got this error message - see attached. Suggestions for getting this download installed and up and running would be appreciated.

---

### Post by IainPurdie on 2009-06-02
Looks like you downloaded the 64-bit version when you're running 32-bit or vice-versa. Make sure you've got the correct .deb package version from the package source.

---

### Post by LindaLou on 2009-06-12
Hi IainPurdie, and thanks for the bit of info.  I downloaded Skype from the official webiste ([http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)) selecting the Ubuntu 7.04-8.04 and was not given the option for 32 or 64 bit version.  I am running Ubuntun 64 bit version.

Not sure where to find the correct .deb package, still working on learning all the ins and outs of Linux.  However, I did find this web page, [http://tuxarena.blogspot.com/2008/09/how-to-install-skype-20-in-ubuntu-804.html](http://tuxarena.blogspot.com/2008/09/how-to-install-skype-20-in-ubuntu-804.html), and [http://www.econowics.com/linux/292/how-to-install-skype-on-ubuntu-linux-easy-way/](http://www.econowics.com/linux/292/how-to-install-skype-on-ubuntu-linux-easy-way/), and am wondering if this is the route to take.

Comments and instructions will be gratefully received!! :D

---

### Post by IainPurdie on 2009-06-12
Hey, LindaLou. You might find the following link useful:

[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

It's instructions for installing 64-bit Skype, though the initial post is from 2007 it looks like it's pretty much correct for use now.

The easiest way I found to install Skype is via the second option listed on that post - add Medibuntu as one of your software sources. The bonus with this is that should a newer version be released, it will be updated in the same way as the rest of your Ubuntu install.

---

### Post by LindaLou on 2009-06-12
Well, I think I found it and did it.  Here is a link, with a 64bit version of Skype.  Downloaded it smoothly and seamlessly.
[http://www.ubuntugeek.com/how-to-install-skype-2-on-64-bit-ubuntu.html](http://www.ubuntugeek.com/how-to-install-skype-2-on-64-bit-ubuntu.html)

What you are looking for is this comment from the web page is below, 

 > Abhishek says:
April 30, 2009 at 5:25 pm

Hey guys there is a 64 bit version available by Skype at

[http://www.skype.com/go/getskype-linux-ubuntu-amd64](http://www.skype.com/go/getskype-linux-ubuntu-amd64)

---

### Post by LindaLou on 2009-06-12
Hey IainPurdie,  I have never used the Medibuntu for anything.  But, wish I had the courage because from all the readings I've managed to do with Ubuntu, it seems that Medibuntu is the way to go because of exactly what you said  
> The bonus with this is that should a newer version be released, it will be updated in the same way as the rest of your Ubuntu install.

This holds true for any program/application that one might install on Ubuntu, is that correct?

---

### Post by IainPurdie on 2009-06-12
Yes. Basically, if you install from a repository (of which Medibuntu is one of many) then if an updated version of the program is issued to that repository then your PC will be informed of it.

This is also the case if you install something and then later add a repository which manages that program. For example, if you download the ".deb" package and install Skype that way and then later on add Medibuntu to your software sources, the system will inform you when Medibuntu gets a Skype update.

The default repositories only hold open source software, which is why the likes of Skype are maintained elsewhere. Medibuntu also has versions of Flash, RealPlayer and so forth. It's definitely worth adding to your Software Sources.

---

### Post by LindaLou on 2009-06-12
Well, I guess I had better get going on some google searches and figure out this Medibuntu "stuff"!!
Is is possible to use the Medibuntu for updates on say, Skype, even though I have not used Medibuntu to install Skype?

Thank you so much!

---

### Post by IainPurdie on 2009-06-12
> **LindaLou said:**
> Is is possible to use the Medibuntu for updates on say, Skype, even though I have not used Medibuntu to install Skype?

Yes. At regular times (and when you manually tell it to), the system reached out to all the repositories listed in your "software sources" (from the menu: System / Administration / Software Sources). From each, it downloads a list of the current releases of each file, utility, application and so on. It then compares them against what you have installed regardless of where they were installed *from*.

If a newer version is available, the system will give you a notification and the opportunity to download and update these programs. This is the default behaviour, anyway.

Adding Medibuntu (or any other repository) is simple enough. The following link is very informative:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by IainPurdie on 2009-06-12
> **jamiyoel said:**
> How much will I've to pay for sending text?

That depends on where you're sending a text to. Details here:

[http://www.skype.com/prices/smsrates/](http://www.skype.com/prices/smsrates/)

---

### Post by LindaLou on 2009-06-12
Thank you again, IainPurdie!  Over the week end, I am going to check out the link you provided and any other info I can gather.  Time to for me to get with the program! because I really find it a bit annoying that updates are not always available (Open Office for example).

jamiyoel, here is a link that may answer your question about cost for Text Messages - [http://skype.com/allfeatures/sms/](http://skype.com/allfeatures/sms/)

---

### Post by Captain_tux on 2009-06-14
Hey guys, has anyone gotten this to run under Jaunty? I got it working on the desktop using Hardy, but no luck on my laptop using Jaunty.

I get the following error upon running **./skysentials.py**:

```

benny@laptop:~/skysentials-1.0.1$ ./skysentials.py 
Traceback (most recent call last):
  File "./skysentials.py", line 13, in <module>
    import Skype4Py
ImportError: No module named Skype4Py
```

Appreciate any help I can get... thanks!

---

### Post by mdurham on 2009-06-14
> **Captain_tux said:**
> Hey guys, has anyone gotten this to run under Jaunty? I got it working on the desktop using Hardy, but no luck on my laptop using Jaunty.

I get the following error upon running **./skysentials.py**:

```

benny@laptop:~/skysentials-1.0.1$ ./skysentials.py 
Traceback (most recent call last):
  File "./skysentials.py", line 13, in <module>
    import Skype4Py
ImportError: No module named Skype4Py
```

Appreciate any help I can get... thanks!

Works okay for me in Jaunty

---

### Post by Captain_tux on 2009-06-16
> **Captain_tux said:**
> Hey guys, has anyone gotten this to run under Jaunty? I got it working on the desktop using Hardy, but no luck on my laptop using Jaunty.

I get the following error upon running **./skysentials.py**:

```

benny@laptop:~/skysentials-1.0.1$ ./skysentials.py 
Traceback (most recent call last):
  File "./skysentials.py", line 13, in <module>
    import Skype4Py
ImportError: No module named Skype4Py
```

Appreciate any help I can get... thanks!

Anyone have any ideas?

:(

---

### Post by Paddy Landau on 2009-06-16
> **Captain_tux said:**
> Anyone have any ideas?
I don't know what is causing your problem. The only thing that I can suggest is to uninstall the program, and then reinstall it, following the instructions carefully, precisely and in fine detail.

---

### Post by Captain_tux on 2009-06-16
> **Paddy Landau said:**
> I don't know what is causing your problem. The only thing that I can suggest is to uninstall the program, and then reinstall it, following the instructions carefully, precisely and in fine detail.

Quite sure I did so, but I'll try again... thanks!

:)

---

### Post by LindaLou on 2009-07-07
I followed instructions for adding Medibuntu to Ubuntu 8.04.  Am running 64bit.

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

And the result was this:

ndr@ndr:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

[sudo] password for ndr: 

--10:53:35--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)

           => `/etc/apt/sources.list.d/medibuntu.list'

Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110

Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.

HTTP request sent, awaiting response... 200 OK

Length: 276 [text/plain]



100%[====================================>] 276           --.--K/s             



10:53:36 (27.12 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [276/276]


Next I entered this code in the terminal:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

And the result was this:

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      

Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_CA           

Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_CA     

Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_CA       

Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_CA     

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy Release.gpg                             

Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/main Translation-en_CA                  

Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/restricted Translation-en_CA            

Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/universe Translation-en_CA              

Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/multiverse Translation-en_CA            

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates Release.gpg                     

Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/main Translation-en_CA          

Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/restricted Translation-en_CA    

Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/universe Translation-en_CA      

Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/multiverse Translation-en_CA    

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy Release                                 

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates Release                         

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/main Packages                           

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/restricted Packages                     

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/main Sources                            

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/restricted Sources                      

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/universe Packages                       

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/universe Sources                        

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/multiverse Packages                     

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/multiverse Sources                      

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/main Packages                   

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/restricted Packages             

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/main Sources                    

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/restricted Sources              

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/universe Packages               

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/universe Sources                

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/multiverse Packages             

Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/multiverse Sources              

Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [197B]                   

Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_CA

Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg

Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_CA

Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [11.7kB]

Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_CA

Ign [http://download.skype.com](http://download.skype.com) stable Release

Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release 

Ign [http://download.skype.com](http://download.skype.com) stable/non-free Packages

Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages [6320B]

Err [http://download.skype.com](http://download.skype.com) stable/non-free Packages

  404 Not Found [IP: 212.72.53.130 80]

Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages [7546B]

Fetched 25.8kB in 15s (1649B/s)

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404 Not Found [IP: 212.72.53.130 80]


E: Some index files failed to download, they have been ignored, or old ones used instead.


I did see the failures but without prior knowledge I thought this was OK.

Next was I entered this in the terminal:

ndr@ndr:~$ sudo apt-get install skype

Reading package lists... Done

Building dependency tree       

Reading state information... Done

The following packages were automatically installed and are no longer required:

  libgnomescan-common libgnomescanui-common

Use 'apt-get autoremove' to remove them.

The following extra packages will be installed:

  lib32nss-mdns skype-common

The following NEW packages will be installed:

  lib32nss-mdns skype skype-common

0 upgraded, 3 newly installed, 0 to remove and 5 not upgraded.

Need to get 15.5MB of archives.

After this operation, 20.9MB of additional disk space will be used.

Do you want to continue [Y/n]? y 

WARNING: The following packages cannot be authenticated!

  skype-common skype

Install these packages without verification [y/N]? y

Get:1 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/universe lib32nss-mdns 0.10-3ubuntu2 [17.4kB]

Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free skype-common 2.0.0.72-0medibuntu1.1 [2426kB]

Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free skype 2.0.0.72-0medibuntu1.1 [13.1MB]

Fetched 15.5MB in 33s (460kB/s)                                                

Selecting previously deselected package lib32nss-mdns.

(Reading database ... 193835 files and directories currently installed.)

Unpacking lib32nss-mdns (from .../lib32nss-mdns_0.10-3ubuntu2_amd64.deb) ...

Selecting previously deselected package skype-common.

Unpacking skype-common (from .../skype-common_2.0.0.72-0medibuntu1.1_all.deb) ...

Selecting previously deselected package skype.

Unpacking skype (from .../skype_2.0.0.72-0medibuntu1.1_amd64.deb) ...

Setting up lib32nss-mdns (0.10-3ubuntu2) ...



Setting up skype-common (2.0.0.72-0medibuntu1.1) ...

Setting up skype (2.0.0.72-0medibuntu1.1) ...

Processing triggers for libc6 ...

ldconfig deferred processing now taking place

ndr@ndr:~$ 


Skype is there, in the Applications and when I opened it, there was my old Skype ID and contacts! Strange because prior to this install as noted above, I removed Skype, completely, using Synaptic Package Manager (Mark for Complete Removal).

Then, there is the notification that updates are avaialable. OK, that's good and I click install.  
Here's the list. Also see the first attachment

libavcodec1d (version 3:0.cvs20070307-5ubuntu7.3) will be upgraded to version 3:0.cvs20070307-5ubuntu7.3+medibuntu1

libavformat1d (version 3:0.cvs20070307-5ubuntu7.3) will be upgraded to version 3:0.cvs20070307-5ubuntu7.3+medibuntu1

libavutil1d (version 3:0.cvs20070307-5ubuntu7.3) will be upgraded to version 3:0.cvs20070307-5ubuntu7.3+medibuntu1

libpostproc1d (version 3:0.cvs20070307-5ubuntu7.3) will be upgraded to version 3:0.cvs20070307-5ubuntu7.3+medibuntu1

mplayer (version 2:1.0~rc2-0ubuntu13.1) will be upgraded to version 2:1.0~rc2-0ubuntu13.1+medibuntu1

libamrnb3 (version 7.0.0.1-0.0+medibuntu1) will be installed

libamrwb3 (version 7.0.0.2-0.1+medibuntu1) will be installed

I then saw the warning icon for updates/installs and click on it.  See the second attachment.

Sooooo, not sure what the heck I did wrong, if anything, and am hoping that someone has a resolve to this!;)

Here is the error from the Update Manager when I am asked to update manually: 
GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404 Not Found [IP: 212.72.53.130 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Paddy Landau on 2009-07-07
After adding a repository, you need to tell your computer to trust it.

In your second screenshot, you have NO_PUBKEY 2EBC26B60C5A2...

What you need are the ***last eight characters*** of that string. (I can't see what they are from your screenshot.)

Then, in a terminal, run these two commands:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <key>
sudo apt-get update
```(Replace <key> with the eight characters.)

---

### Post by LindaLou on 2009-07-07
Thanks Paddy Landau.  I followed your instructions and below is the output from Terminal:

ndr@ndr:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0C5A2783
[sudo] password for ndr: 
Sorry, try again.
[sudo] password for ndr: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 0C5A2783
gpg: requesting key 0C5A2783 from hkp server keyserver.ubuntu.com
gpg: key 0C5A2783: public key "Medibuntu Packaging Team <admin@lists.medibuntu.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
ndr@ndr:~$ sudo apt-get update
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy Release.gpg
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/main Translation-en_CA                  
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/restricted Translation-en_CA            
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [197B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_CA                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_CA             
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                               
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/universe Translation-en_CA              
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/multiverse Translation-en_CA            
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/main Translation-en_CA          
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/restricted Translation-en_CA    
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/universe Translation-en_CA      
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/multiverse Translation-en_CA    
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy Release                              
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates Release                         
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/main Packages                           
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/main Sources                            
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/universe Packages                       
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [11.7kB]                     
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/multiverse Packages                  
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/multiverse Sources                   
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/main Packages                   
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/main Sources                    
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/restricted Sources              
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_CA                
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/universe Packages               
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/universe Sources                
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/multiverse Packages             
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/multiverse Sources              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Ign [http://download.skype.com](http://download.skype.com) stable Release                                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                   
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Packages                      
Err [http://download.skype.com](http://download.skype.com) stable/non-free Packages                      
  404 Not Found [IP: 212.72.53.130 80]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Fetched 198B in 4s (41B/s)
W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404 Not Found [IP: 212.72.53.130 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
ndr@ndr:~$ 


Looks like still something may be missing. Not sure but that last 2 lines ( W  and E ) indicates a download  and fetch failure.

What next?

---

### Post by Paddy Landau on 2009-07-07
> **LindaLou said:**
> W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404 Not Found [IP: 212.72.53.130 80]
That last one is about the Skype repository. You've added the repository for Skype for 64-bit (do you have a 64-bit computer and installation?).

I would suggest that you remove that repository from your software sources, simply because I had problems with it.

*System -> Administration -> Software Sources -> Third Party Software*

Instead, use the default Skype that comes with Synaptic Manager.

Other than that, everything looks fine.

---

### Post by LindaLou on 2009-07-10
I am running 64 bit.  
I went ahead and deleted Skype from the repository as you instructed. Let's see how things go.  I checked for updates and everything is fine.  Keeping my fingers crossed.;)

Initially, my first go at Skype was from the website.  I received an error re the i386 and when I opened the download with Deb, it worked.  I still had this funky "out of date " notice from Update Manager, but Skype worked. I would get the out of date notice about every other day.  

Well, I will see how things progress today and Monday.  Thanks for the info. As always, Ubuntu Forum is quality!!  :popcorn:

---

### Post by scrapmetal on 2009-08-14
[SIZE=3]**DESPERATE POSTING:**[/SIZE] :confused:

_**Do I continue with Skype install?**_

Worked fine on an AMD 3200+ (single processor) Running Kubuntu 64 bit. - **"Thanks!"**:)

Now trying the Medibunt Method on a AMD (duel processor) 3200, Running Ubuntu 32 bit.
DO I HAVE PROBLEMS ? :confused:

**Ran in Terminal:**sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list (my password)

**Completed OK.** :)

**Ran in Terminal:** sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

**Received Error below:**
W: GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-proposed Release: The following signatures were invalid: BADSIG **40976EAF437D05B5** Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

**Is the "Ubuntu Archive Automatic Signing Key" a "public key encryption" type system, as I have not set one up on this machine?.**
I ask as there had been one the other (64 it Kubuntu).

[B]Desperetly needing advice on what to do next? :confused:
Do I correct these problems with apt-get update? :confused:
And if so, what do I type in terminal?[/B] :confused:

I have had one previous error report re- library when installing "sound and video" programs, one of which reported bringing its own library. So presumed that was why duel entries had been installed and reported as such. I have ignored this until now as it may be affecting this procedure.

**1st time PROBLEM REPORTED:**
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_hardy_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
_END PROBLEM:_

**2nd time PROBLEM REPORTED:** Wed Aug 12 - 8.58pm EST (Australia)
Update manager: Reported 3 to update. 
Gave this error:
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_hardy_partner_binary-i386_Packages)
**My action:**
Clicked Ok
Update Manager- Then proceded to download 3 files and update.
_END PROBLEM:_

**Oh HELP, am I beyond hope yet?** :confused:

---

### Post by Paddy Landau on 2009-08-14
You have two separate problems. The first that you described involves the signing key (yes, it's public key encryption). The second says that you have the same software source twice.

First, check your software sources.

[LIST=1]
[*]System > Administration > Synaptic Package Manager > Settings > Repositories > Third Party Software
[*]Look through the list. Find any duplicates, and remove them (with the *Remove* button), so that every line is unique.
[*]When you press *Close*, it will probably give you warning about "Repositories changed". If it does, just press *Close*.
[*]Press *Reload*.
[*]If you still get an error, post it here (it may be the same error again).
[*]Otherwise, if you do not get an error, press *Mark All Upgrades*, then, if available, *Apply*.
[/LIST]

---

### Post by scrapmetal on 2009-08-14
Great instructions :) **THANKS!** ):P
**Two duplicates**, highlighted and removed one (with the *Remove* button). :confused: What a dummy I am.
It asked for a re-load. Complied :) (Synaptic)
76 Reloaded OK. :)
[SIZE=2]**Do I have to reload the second command line of Medibuntu again?**[/SIZE]
One very happy and grateful newbie. :P 
[SIZE=2]**Thanks for that save, I could have been stuck there for months.**[/SIZE]

---

### Post by Paddy Landau on 2009-08-14
> **scrapmetal said:**
> [SIZE=2]Do I have to reload the second command line of Medibuntu again?[/SIZE]
I don't know. When you look at the software sources, do you already have Medibuntu listed there? If so, then you already have it.

If you don't have it, you can add it (use the "Add" button). The line reads:
```
deb http://packages.medibuntu.org/ hardy free non-free
```(Change 'hardy' to your distribution, if you have intrepid, jaunty or something other than hardy.) Remember to reload when prompted.

---

### Post by scrapmetal on 2009-08-14
**[SIZE=2]A Big THANKS to all. (solved)[/SIZE]** :guitar:
Up and Running.
Library's OK now.
Keys are to.
Found lots of good stuff to learn, at [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
 -**GREAT PLACE** :)

[SIZE=3]**I live, I learn.**[/SIZE]:popcorn:

---

### Post by MarkieB on 2009-09-14
no longer participating in ubuntuforums.org

---

### Post by Paddy Landau on 2009-09-14
Update!

Skype has released a new version that includes SMS.

You no longer need skysentials.

Simply download the latest version of [Skype for Linux]("http://www.skype.com/intl/en/download/skype/linux/choose/") and install.

It works perfectly for me.

---

### Post by kevinguillorytraining on 2009-10-10
Thanks. I really need skype in my ubuntu machine :)

---

