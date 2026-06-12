---
title: "HOWTO: Install Canon PIXMA ip1500"
date: 2005-08-13
forum: Outdated Tutorials &amp; Tips
---

### Post by rockett15 on 2005-08-13
[SIZE=2]**Do this at your own risk!**[/SIZE]

First you will need to update libc6 to one from the Debian site (why I say at your own risk)

[http://packages.debian.org/testing/base/libc6](http://packages.debian.org/testing/base/libc6)

**sudo dpkg -i libc6_2.3.2.ds1-22_i386.deb**

then goto: [http://linux.cergynux.net/canon/](http://linux.cergynux.net/canon/) 

get: bjfilter-pixmaip1500_2.50-3_i386.deb & bjfilter-common_2.50-3_i386.deb

**sudo dpkg -i bjfilter-common_2.50-3_i386.deb bjfilter-pixmaip1500_2.50-3_i386.deb**

You will then be required to restart cups:

**sudo killall cupsd**
**sudo cupsd**

After we're all done - all we have to do now is set-up the printer!  :smile: 

**System >> Administration >> Printing >> New Printer** 

Select: **Use another printer by specifying port** drop down to: **USB Printer #1 (Canon ip1500)** 

Then select the PIXMA iP1500 ver.2.50 from the list :)

**I have figured a way past the dependancy hell with the above. Install the debian locales package also,**

---

### Post by +Flip on 2005-08-15
At my Ubuntu Machine, your howto doesn't seem to work, i've connected my ip1500 to the usb port, and installed it properly, it does get reconized, but doesn't prints a thing!

What's the problem?

Thanks, anyway

Flip
The Netherlands

---

### Post by andremarcel on 2005-08-16
It works good for me, but the dependencies are so much that i was not able
to install a new programm without removing the whole system. Why is this driver not available for ubuntu?

Is it better to change do Debian if they have better support for my printer?

---

### Post by veelivar on 2005-08-16
Right I'm gonna try this later.  My printer not working was the big killer for not using linux 99% of the time.

hopefully this will sort it out.

Has anyone else got any observations from trying this?

Also does anyone know if ubuntu is likly to support this in the near future with ou having to get the debian libc6 (what with ubuntu being based on debian an everything)

thanks for posting this I'll let you know how I get on.

best regards,
Dan.

---

### Post by veelivar on 2005-08-16
I tried the above steps and at first it seemed to work.

however...

when I tried to print from openoffice it seemed stuck on A5 paper no matter what setting i set it to and printed halfway down the page.  I fiddled with the settings in openoffice a bit and now it won't print at all (dosen't even go to the print queue) I don't know why this is.

Current status:
print preview on the printer is fine no probes here
gimp goes to print queue then nothing
everything else (firefox, openoffice) nothing not even to print queue

I also noticed that it only did up to 600dpi (which if it worked I could probably live with but it would be nice to have higher)

Is there anyhting obvious I could have missed? (I don't know linux very well).  As teh printer seems to be installed ok as the test page is fine.

I hope some one can help,
best regards,
Dan.

---

### Post by new2hoary on 2005-08-17
Have a look at turbo print;

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

There is a free version but to get the best from your printer you have to pay for the full version.

It does most new Canon printers as well as hp and some others.

I use it on my Pixma IP5000 and get great results very easy to install. It lets me print to the full capabilites of my printer - including CD printing, paper source selection, and duplex.

I'm in no way connected to the producers of this - just a very happy long term user.

EDIT: I should also say it allows;

Head alignment
Cleaning
Ink levels viewing

---

### Post by rockett15 on 2005-08-17
Yeah,

There appears to be a bit of dependancy hell with this method. You can work through it though.

It would be nice to see these re-packaged for Ubuntu.

---

### Post by alb on 2005-08-22
Yes

I also would like to see the ubuntu packages...

I'm not confident in installing  a different libc6.

alb

---

### Post by Svictor on 2005-08-24
Well, actually, you don't need to reinstall libc6. Ubuntu's version works quite well for the driver. It's just not recognized as appropriate by dpkg. So what you can do is download the rpms instead of the debs, and convert them to debs with alien :
sudo alien <name of the rpm>
The resulting *.deb package doesn't complain anymore about libc6. This worked for me so far and now, I can print. Then, there is this thread : [http://ubuntuforums.org/showthread.php?t=38995]("http://ubuntuforums.org/showthread.php?t=38995"), for fine-tuning (make sure to edit your ppd file !).
What I can't figure though is how to get gimp working. I tried the default : 
lpr -s -d PIXMA-iP1500-Ver.2.50 -oraw
and also :
lpr -P PIXMA-iP1500-Ver.2.50 -oraw
Something happens, the printing job is created and the light on the printer starts blinking, but it never grabs the sheet to write on it.
What printing system does Gimp use ? Why do I get perfect test page, perfect text from openoffice but nothing from gimp ?
Any suggestion  would be appreciated.

**Edit : **

I found out for gimp \\:D/: one should not use the -oraw option, even if gimp itself says you should.

By the way, there was another problem in openoffice, which would only print to a5. The solution is to configure the printer through oopadmin (from command line). I'm not quite sure if one has to do that every time a setting needs to be changed. Anyway, it seems to override the printer settings from openoffice itself (the writer for ex.). 

Good luck to you all ! :D

---

### Post by rockett15 on 2005-08-25
Just to try the above - how would one downgrade libc6 back to the Ubuntu version? Without all the dependancies getting removed?

---

### Post by andremarcel on 2005-08-28
You can remove it with:

sudo dpkg -r libc6

after that you can reinstall libc6 using synaptic or apt.

---

### Post by puppy on 2005-09-10
Sorry threads dont seem to be working properly... didnt mean to post  :???:

---

### Post by puppy on 2005-09-10
"By the way, there was another problem in openoffice, which would only print to a5. The solution is to configure the printer through oopadmin (from command line). I'm not quite sure if one has to do that every time a setting needs to be changed. Anyway, it seems to override the printer settings from openoffice itself (the writer for ex.)."

I've noticed this A5 problem, but running "oopadmin" in a terminal says:

bash: oopadmin: command not found

Where are you running this command from? 

Also in the Gimp even when I miss out -oraw I am getting no output

Please help - I can get a test page from the printer but *no* applications will print anything  :roll:

---

### Post by veelivar on 2005-09-12
[QUOTE=puppy]"By the way, there was another problem in openoffice, which would only print to a5. The solution is to configure the printer through oopadmin (from command line). I'm not quite sure if one has to do that every time a setting needs to be changed. Anyway, it seems to override the printer settings from openoffice itself (the writer for ex.)."

I've noticed this A5 problem, but running "oopadmin" in a terminal says:

bash: oopadmin: command not found

Where are you running this command from? 

Also in the Gimp even when I miss out -oraw I am getting no output

Please help - I can get a test page from the printer but *no* applications will print anything  :roll:[/QUOTE]

I'm still having exactly the same problems.  I was hoping someone who knew about these thing would be able to help.  Hence me checking in now.

Does any one know how to solve these issues?

Cheers,
Dan.

---

### Post by Spokkioso on 2006-08-27
Hi..im an ubuntu user
ive done 

# dpkg -i bjfilter-common_2.50-3_i386.deb ijfilter-pixmaip1500-lprng_2.50-3_i386.deb

whitout errors.(ive done it whit sudo -s for a root shell)
so i went to System >> Administration >> Printing >> New Printer
i select - usb 1 canon pixma 1500 - 
but in the selection of the driver i dont find  PIXMA iP1500 ver.2.50!!
the system first show to me the ImageRunnerss 300 driver,ive used it but when i print i dont get results

any1 know why?tnx

---

### Post by tsayles on 2008-07-18
There is very good HOWTO with cut and paste instrunctions in the Ubuntu Wiki at [https://wiki.ubuntu.com/CanonPixmaIP1500]("https://wiki.ubuntu.com/CanonPixmaIP1500")

---

### Post by jakobtritten on 2008-11-18
QUOTE: "There is a very good HOWTO with cut and paste instructions in the Ubuntu Wiki at https://wiki.ubuntu.com/CanonPixmaIP1500"

I'm trying really hard to be legit by not pirating windows; but why can't i get the Canon PIXMA iP1500 to work with Ubuntu Intrepid?  Every discussion about this has somehow led me to a dead end.  :confused:

I tried the link in the quote above; and when i typed "sudo apt-get install alien libxml1" (near the beginning of the instructions), i got this ...

"Package libxml1 is not available, but is referred to by another package.  This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package libxml1 has no installation candidate" 

Then i got bashed with a "no such file or directory" for the second to last line: "sudo /etc/init.d/cupsys restart".  

:-k

Yes, i am new; but i'm a newb who is diligently trying to learn the Linux way of life and forsake the wayward path that is microsoft (and the rip-off that is mac).  Is someone willing to help me figure out this issue?  Thank you in advance for your kind assistance.

---

### Post by jakobtritten on 2008-11-20
Problem Solved ... 

First of all, make sure your system is up-to-date (e.g., use Synaptic Package Manager under System -> Administration).

Once that's done, the following link is definitely VERY helpful and i would be completely lost without it; but i'm posting a couple of changes to it that worked for my computer.

Link:  [https://wiki.ubuntu.com/CanonPixmaIP1500]("https://wiki.ubuntu.com/CanonPixmaIP1500")

Amendments:

Instruction #3:  If you get an error message about libxml1, try then typing:
sudo apt-get install libxml2

Instruction #8 should be:
sudo /etc/init.d/cups restart

Instruction #9:  After you go to System -> Administration -> Printing, just to be sure, ...
1.  Add the printer if it's icon isn't already there
2.  Right-click on the printer
3.  Select "Properties" from context menu
4.  Click the "Change" button that corresponds to "Make and Model"
5.  Check the radio button beside "Provide PPD file"
6.  Click on the file finder in that section of the window
7.  Locate the directory /usr/share/cups/model
8.  Double-click the PPD file:  "canonpixmaip1500.ppd"
9.  Follow the directions

Thank you, tsayles, for the very helpful link, and thank you to whoever wrote those instructions!

---

### Post by hvqboy on 2009-06-08
Thanks to you all, especially JAKOB!

I am new to UBUNTU... actually new to LINUX... as in this was my first time ever messing around with this.  
I upgraded a four year old laptop to 1G Ram and installed UBUNTU today.
I ran into the same problem with the CANON PIXMA IP1500 and followed the instructions  in this link [https://wiki.ubuntu.com/CanonPixmaIP1500](https://wiki.ubuntu.com/CanonPixmaIP1500) **AS CORRECTED** by Jakob above.  

Brilliant!

My printer works perfectly with UBUNTU now.

Yeay!

:)

---

### Post by jakobtritten on 2009-06-13
Glad i could help, hvqboy!  This is a great forum, is it not?  God bless!

---

