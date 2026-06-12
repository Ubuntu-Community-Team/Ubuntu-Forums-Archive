---
title: "HOWTO: Install Cups-PDF"
date: 2006-06-04
forum: Outdated Tutorials &amp; Tips
---

### Post by LoKi128 on 2006-06-04
[color="red"]THIS TUTORIAL IS OUTDATED[/color]

Thanks to everyone from [this thread]("http://www.ubuntuforums.org/showthread.php?t=187516") for all their guidance. The sticking point in this whole process is that you need to be root to edit the permissions on the executable.

[LIST=1]
[*]Install the cups-pdf package (I used version 2.2.0-1)
[*]Go to System -> Administration -> Printing
[*]Doubleclick "New Pinter"
[*]Notice that there is no mention of a CUPS PDF printer
[*]Open a terminal and tpe "sudo nautilus" and then your password
[*]Go to Filesystem -> usr -> lib -> cups -> backend
[*]Rightclick "cups-pdf" and select Properties
[*]Go to the Permissions tab and click the "Set user ID" special flag
[*]Again try to add a new printer
[*]There is now a "PDF Printer" detected, select it
[*]Select the Generic, Postscript Color Printer (Rev 3b)
[*]Give it a name, like PDF Printer
[*]Right click on the newly created printer, and select Properties
[*]Click "Print a Test Page"
[*]The file should be in your Home folder, under the PDF folder
[/LIST]

---

### Post by jbaloul on 2006-06-05
Dude thanks, just at the right time....

but you know, how are we supposed to ask grandma to do something like that...
stuff like this should be as simple as possible.

---

### Post by simplyw00x on 2006-06-05
Once it's set up then it's easy to use. Would you really expect 'grandma' to install _any_ kind of printer, or a PDF printer on windows? Or know what a PDF is? Or know what a printer is?

On a related note, thanks for the HOWTO.

---

### Post by KillerBOB on 2006-06-06
Thanks for this, it's really useful. I hope this gets enabled by default in future Ubuntu releases.

---

### Post by Canguçu on 2006-06-06
[QUOTE=KillerBOB]I hope this gets enabled by default in future Ubuntu releases.[/QUOTE]

Well, KillerBOB, I'm waiting for that since Warty... :(

---

### Post by sailorxyz on 2006-06-07
Hi,
I am running a clean install of Dapper. There is no cups-pdf in my usr/lib/cups/backend. What now? :-(

Regards,

Paul

---

### Post by jbaloul on 2006-06-07
[QUOTE=sailorxyz]
I am running a clean install of Dapper. There is no cups-pdf in my usr/lib/cups/backend. What now? :-(
[/QUOTE]

try this...
```

sudo updatedb
locate cups-pdf

```

if you still don't see it then...
```

sudo apt-get install cups-pdf

```

like i said before, I wish for nuB user's sake, that this kinda stuff is to be enabled by default or "grandma" intuitive.

---

### Post by seuaniu on 2006-06-08
Good howto - and easy as pie to do.  This is an easy feature, that should be enabled by default though.  I think Apple has it in OSX, so in order to compete on a feature to feature basis, we should have it too :D

---

### Post by simplyw00x on 2006-06-08
seuaniu:
Look at any desktop OS. Is installing a PDF printer 'grandma intuitive'? No. If grandma can't follow a set of simple typed commands then grandma doesn't get PDF printing either way. Do you think 'grandma' even knows what a PDF _is_?

---

### Post by shuttleworthwannabe on 2006-06-08
Thanks worked like a charm! Poor Granny..leave her alone... ;-)

---

### Post by meng on 2006-06-08
I'm sure some grandmas could do this. It's just a matter of how much they need to do it, and to what degree of "inconvenience" they'll tolerate in order to obtain the functionality.
Old != stupid

---

### Post by jimcooncat on 2006-06-08
Guess we know who will be cooking the next holiday dinner!

Won't be granny, she'll be recompiling your kernel with funroll-loops.

---

### Post by jbaloul on 2006-06-08
[QUOTE=jimcooncat]Guess we know who will be cooking the next holiday dinner!

Won't be granny, she'll be recompiling your kernel with funroll-loops.[/QUOTE]

LOL !!!!!!!!!!!!!!!

grandma-ubuntu-pdf-guru-hacker :p

---

### Post by henriquemaia on 2006-06-12
Thanks for this guide.

---

### Post by elpresidente on 2006-06-15
I am attempting to follow the guide. When I get to Step 2 of 2:Printer Driver, nothing shows up. Nothing in the dropdown for manufacturer or driver. I had previously installed a network printer through samba (brother mfc-8300),

Anyone have an idea how to get the default drivers to show?

---

### Post by mudra on 2006-06-16
Thank you worked like a dream on a fresh install of dapper.

Mudra

---

### Post by Franko30 on 2006-06-19
[QUOTE=elpresidente]When I get to Step 2 of 2:Printer Driver, nothing shows up. Nothing in the dropdown for manufacturer or driver.
Anyone have an idea how to get the default drivers to show?[/QUOTE]

In the dropdown menu go to **Generic** and there you'll find the postscript etc rev3 printer.

**@LoKi128:**

Many thanks for this HOWTO!

I tried installing and changing file permissions according to the CUPS-PDF website [http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/documentation.shtml](http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/documentation.shtml) but it didn't work...

Great to have a PDF-printer again in Dapper. :-) 

Cheers

Franko30

---

### Post by unique on 2006-06-19
Very cool! Thanks for this. 
Grandma will be a happy camper once I do this for her!

---

### Post by maka on 2006-06-19
Thanks for this guide!!! Great howto

---

### Post by Horizon on 2006-06-19
Nice one, but it's a bit messy. Maybe you should use the code tags and give the precise commands (like apt-get install) to make it simpler. You could also use "sudo chmod +s /usr/lib/cups/backend/cups-pdf" instead of using nautilus as suggested in the other post.

---

### Post by Franko30 on 2006-06-20
[QUOTE=Horizon]You could also use "sudo chmod +s /usr/lib/cups/backend/cups-pdf" instead of using nautilus[/QUOTE]

Unfortunately I have to contradict that.

HOWTOs are mostly for people not that familiar with the Terminal and commandline stuff. So I think it's nice to see where in Nautilus you can do this sort of changes.

Maybe both (the chmod and nautilus versions) would be nice. ;-)

Cheers

Franko30

---

### Post by Horizon on 2006-06-20
[QUOTE=Franko30]Unfortunately I have to contradict that.

HOWTOs are mostly for people not that familiar with the Terminal and commandline stuff. So I think it's nice to see where in Nautilus you can do this sort of changes.

Maybe both (the chmod and nautilus versions) would be nice. ;-)
[/QUOTE]
Well I'm sorry but there have been discussions about this before and it's pretty obvious copy and pasting one line into the command line is much easier and beats going through 10+ steps to get the same outcome. There's literally nothing that could go wrong. Ingoring the fact that explaining how to navigate through a gui can only be so precise, the less steps the better because there's less for them to screw up. What's the chance of them leaning on their keyboard by accident and deleting something important in nautilus compared to them screwing up a single copy and paste?

Also if you're using linux and aren't familiar with the command line well then now's the time to get familiar, not to mention people usually get familiar with the command line from following guides like those avaiilable on this forum. Now If you don't want or care for getting familiar with the command line then you better switch OS and stop wasting our time trying to help people who won't (read unwilling) even help themselves.

Sorry if I kind of sound a little annoyed. I think it's ok to try to avoid the command line, I just don't condone encouraging people to avoid it.

---

### Post by ubuntuuser on 2006-06-21
[quote=Horizon]Well I'm sorry but there have been discussions about this before and it's pretty obvious copy and pasting one line into the command line is much easier and beats going through 10+ steps to get the same outcome. There's literally nothing that could go wrong. Ingoring the fact that explaining how to navigate through a gui can only be so precise, the less steps the better because there's less for them to screw up. What's the chance of them leaning on their keyboard by accident and deleting something important in nautilus compared to them screwing up a single copy and paste?

Also if you're using linux and aren't familiar with the command line well then now's the time to get familiar, not to mention people usually get familiar with the command line from following guides like those avaiilable on this forum. Now If you don't want or care for getting familiar with the command line then you better switch OS and stop wasting our time trying to help people who won't (read unwilling) even help themselves.

Sorry if I kind of sound a little annoyed. I think it's ok to try to avoid the command line, I just don't condone encouraging people to avoid it.[/quote]
I absolutely second what you say. I believe that it's pretty dangerous to tell a new user who is not used to linux in general and permissions in particular to open a nautilus window with root privileges. Just imagine what happens if he leaves it open for a while, then maybe forgets about this and starts to meddle with his system while trying to follow the latest tutorial. If the person is able to open a terminal and type sudo nautilus, then he is also able to copy/paste the chmod-line.
I am not saying that the average linux beginner will start to randomly delete directories in the / dir :-), but as always, safety first. Ever thought about a harmless exploit in nautilus that becomes severe once nautilus is run as root? Or maybe I'm just being paranoid :-) Just my 2 ct.

---

### Post by Mishal on 2006-06-25
Thanks for the howto :)

Is there anyway I can make the pdf printer to ask me where I want to save the file rather than doing it in the home folder directly?

---

### Post by waterzebra on 2006-06-26
Thanks for the guide. As a new ubuntu linux user, it's nice to be able to find how-to's for the important things !

---

### Post by ka1axy on 2006-06-27
Well done.  Answers my question as to why the "PDF Printer" isn't detected by default.

Works exactly as described on my system which was upgraded from 5.10 to 6.06.

Thanks!
Peter

---

### Post by makoto149 on 2006-06-28
Great how-to.  Works like a charm.

---

### Post by ounas on 2006-06-29
Thanks, this very helpfull.


Ounas

---

### Post by kleeman on 2006-06-29
Did not work for me (nothing appears in the PDF subdirectory). I get the following message in
/var/log/cups/cups-pdf_log

[ERROR] failed to set file mode for PDF file (non fatal) (/home/richard/PDF/_howto__General_6_06_-_HOWTO__Install_Cups-PDF_-_Page_3_-_Ubuntu_Support_Forums.pdf)

Looks like some kind of wierd permissions issue

ls -al /usr/lib/cups/backend/cups-pdf   reveals

-rwsr-xr-x 1 root root 23120 2006-05-17 21:49 /usr/lib/cups/backend/cups-pdf

Any ideas?

---

### Post by rdd on 2006-07-02
The permissions look the same on my system. Not sure what that is. Bumping it for you hereby. 

Anyway, I have put this in the wiki, because I didn't find anything to make this work in dapper anywhere in it before. 

[https://help.ubuntu.com/community/forum/software/cups-pdf]("https://help.ubuntu.com/community/forum/software/cups-pdf")

---

### Post by klytu on 2006-07-03
Great HOWTO! 

I just posted a correction for the O'Reilly book "Ubuntu Hacks" Hack #26, "Make Your Own PDFs" citing this thread.

---

### Post by sabitha on 2006-07-03
nice HOWTO........ btw how to make this work on network like my HPLaserjet-1010 do

---

### Post by skirkpatrick on 2006-07-03
You can probably share your PDF printer like any other.

---

### Post by sabitha on 2006-07-03
i already do that, i know because i can see that printer (PDF printer & Laserjet-1010) on another computer but just PDF printer didnt do the job. PDF printer only can print from server not client.

---

### Post by william_nbg on 2006-07-06
I'm having a strange problem here.

I had the cups-pdf running on Breezy and now wanted to set it up on Dapper.

I installed the cups-pdf and and can find it in the 'backend' directory, change the permissions as required, but it still doesn't show up as a detected printer???

Anyone have an idea or similar experience??

---

### Post by william_nbg on 2006-07-07
OK, I found the problem. I'm having a conflict with my network printer. The printer hangs on my wife's computer (which is also Ubuntu) and I print over the cups network. If I turn that off, the pdf printer pops on. I have a vague idea how to correct this and I'll give it a shot this weekend.

---

### Post by lorris on 2006-07-09
excellent howto! I used the pdf printer i installed to print a pdf of the howto for later use during installs :)

Ciao!

Lorris

---

### Post by mourad on 2006-07-09
> **LoKi128 said:**
> Thanks to everyone from [this thread]("http://www.ubuntuforums.org/showthread.php?t=187516") for all their guidance. The sticking point in this whole process is that you need to be root to edit the permissions on the executable.

[LIST=1]
[*]Install the cups-pdf package (I used version 2.2.0-1)
[*]Go to System -> Administration -> Printing
[*]Doubleclick "New Pinter"
[*]Notice that there is no mention of a CUPS PDF printer
[*]Open a terminal and tpe "sudo nautilus" and then your password
[*]Go to Filesystem -> usr -> lib -> cups -> backend
[*]Rightclick "cups-pdf" and select Properties
[*]Go to the Permissions tab and click the "Set user ID" special flag
[*]Again try to add a new printer
[*]There is now a "PDF Printer" detected, select it
[*]Select the Generic, Postscript Color Printer (Rev 3b)
[*]Give it a name, like PDF Printer
[*]Right click on the newly created printer, and select Properties
[*]Click "Print a Test Page"
[*]The file should be in your Home folder, under the PDF folder
[/LIST]

Yeah very simple and easy way .... However, I have a unique problem, I did not find "Printing" in the system "Administration" ... I don't have it ... Anypne can help telling me how to "Printing" in the system administration ...
Thanks....

---

### Post by luxaeternam on 2006-07-11
Works like a dream - thank you very much :KS

---

### Post by froggay on 2006-07-13
ok, nice, the virual pdf printer work fine from local and remote.

But there's no /etc/cups-pdf.conf 

how do i change the default pdf output location ?

---

### Post by kleeman on 2006-07-13
> **froggay said:**
> ok, nice, the virual pdf printer work fine from local and remote.

But there's no /etc/cups-pdf.conf 

how do i change the default pdf output location ?
For future reference use synaptic to find where this file really is:
 /etc/cups/cups-pdf.conf

---

### Post by froggay on 2006-07-13
sorry i made a mistake in the path.

i tried to copy a template cups-pdf.conf (from cups-pdf website)
to /etc/cups/cups-pdf.conf

and changed the "Out"
restart the daemon with /etc/init.d/cupsys restart

but it seems that the /etc/cups/cups-pdf.conf is not parsed !
my pdf still going to /home/$USER

what's the problem ?

---

### Post by Hexx on 2006-07-17
Can anyone tell me how to get CUPS-PDF working under Xubuntu?

---

### Post by Cephus on 2006-07-20
> **LoKi128 said:**
> Thanks to everyone from [this thread]("http://www.ubuntuforums.org/showthread.php?t=187516") for all their guidance. The sticking point in this whole process is that you need to be root to edit the permissions on the executable.

[LIST=1]
[*]Install the cups-pdf package (I used version 2.2.0-1)
[*]Go to System -> Administration -> Printing
[*]Doubleclick "New Pinter"
[*]Notice that there is no mention of a CUPS PDF printer
[*]Open a terminal and tpe "sudo nautilus" and then your password
[*]Go to Filesystem -> usr -> lib -> cups -> backend
[*]Rightclick "cups-pdf" and select Properties
[*]Go to the Permissions tab and click the "Set user ID" special flag
[*]Again try to add a new printer
[*]There is now a "PDF Printer" detected, select it
[*]Select the Generic, Postscript Color Printer (Rev 3b)
[*]Give it a name, like PDF Printer
[*]Right click on the newly created printer, and select Properties
[*]Click "Print a Test Page"
[*]The file should be in your Home folder, under the PDF folder
[/LIST]

First off, thanks so much for the how-to!  This works beautifully!  I have a couple additional questions, however.  As a Windows convert to Linux, the previous PDF driver (not Adobe) I used allowed appending to the beginning or end of the created document, altering its quality and therefore file size, etc.  Do such options exist with this listed setup?

Thanks!

Cephus

---

### Post by oskvaz on 2006-07-21
Thank you Loki, good howto!

;)

---

### Post by leohart on 2006-07-27
Thanks for How-to. Was wondering around how to do that this morning. 

A quick question is : why does cups-pdf need SetUID? Doesn't that mean whenever cups-pdf is run, it will run under root priviledges?

Why does it need root priviledge? It is putting the file in my $HOME so if I run it, it should be able to write to my $HOME right?

---

### Post by TuxCrafter on 2006-07-29
I use xubuntu and i dont have the gnome printer dialog i use the cups webinterface : [http://localhost:631/](http://localhost:631/)

Can somebody post these files with a working pdf-printer
/etc/cups/cupsd.conf
/etc/cups/printers.conf

thx

---

### Post by Jose Catre-Vandis on 2006-08-06
I have used Cups PDF printer from the beginning :-) Can anyone advise, however, why the output is not machine readable? I'll explain. Open up one of your created pdfs in Adobe reader and then using the Select tool, grab some text, copy and past it into your text editor. You should see a row of little boxes with numbers and letters inside, and not the text you copied. This doesn't happen with "proper" pdfs? Any clues?

---

### Post by TuxCrafter on 2006-08-06
I believe cups-pdf uses postscript to genarate pdf, however i am not sure. I have also problems with evence and printing if i generate a pdf with tranparent images (alpha layer) evence cant print them correctly) acrobat can.

So there are diffrences between the engines that are used.

---

### Post by neohawkeye on 2006-08-11
Excellent thanks for this thread I have now got PDF up and running in no time.

---

### Post by TuxCrafter on 2006-08-11
Can someone rewrite this howto to work with te cups web interface?
I use xubuntu and it is some what diffrent than the gnone print tool.

---

### Post by louaym on 2006-08-25
Thanks for this, it's really useful.

---

### Post by tvor on 2006-08-31
This was the most helpfull clear and straight forward help I got ever! Thank you worked straight and really well. (but really why isn't this enabled by default?) :-P

---

### Post by vgeneral on 2006-08-31
Thanks for the great How-To.

---

### Post by pwk on 2006-09-01
For Xubuntu, install cups-pdf then use

sudo chmod +s /usr/lib/cups/backend/cups-pdf

A virtual printer should appear in the printer manager (see the Desktop Guide documentation link on the default browser page for accessing the printer manager).

Step through the set-up as for a normal printer. I used a generic PS/Foomatic printer option that seems to work OK.

Set additional printer options in the printer tab. For web page options like background printing, use the browser page set-up dialogue.

---

### Post by TuxCrafter on 2006-09-02
> **pwk said:**
> 
sudo chmod +s /usr/lib/cups/backend/cups-pdf


Thx this was helpfull

---

### Post by Anduu on 2006-09-02
Good stuff :KS

---

### Post by yopnono on 2006-09-02
Or you can use this latest version of cups-pdf and if will fix everything.

Just install it. And stay happy....

---

### Post by Anduu on 2006-09-02
> **yopnono said:**
> Or you can use this latest version of cups-pdf and if will fix everything.

Just install it. And stay happy....

I can't speak for the others but I like to keep my system as "stock" as possible.I don't mind using third party software and apps of course;however for core system stuff I won't go outside the repos.

---

### Post by yopnono on 2006-09-03
> **Anduu said:**
> I can't speak for the others but I like to keep my system as "stock" as possible.I don't mind using third party software and apps of course;however for core system stuff I won't go outside the repos.

I agree with you about this. Anyhow you can always check the deb before installing it. This deb include the latest cups-pdf. 

And also it have the permission fixed. (it set the permission to "user id" during install.

---

### Post by techstop on 2006-09-12
Just found this HOWTO, works great, cheers!

---

### Post by NewbieLearnLinux on 2006-09-12
Sorry to ask but why do we need to install this Cups-PDF ?

---

### Post by froggay on 2006-09-12
cups-pdf is only necessary if you want to print to a pdf file

in my case i have sun an hp boxes ( cad station ) and i don't want to install a pdf printer on each box.

So i have installed a pdf printer on the linux box with cups and cups-lpd so that i can directly send task to this spooler from all the cad workstation.

it was working fine with ubuntu 4.1, and now i'm trying to migrate to 6.06 on a sparc machine (without gnome)

---

### Post by yopnono on 2006-09-12
> **NewbieLearnLinux said:**
> Sorry to ask but why do we need to install this Cups-PDF ?

The deb I provided is for people that just like to install the cups-pdf and have it working directly without having to sett permission and stuff. 

It does the same as installing from synaptic and setting the permission yourself

---

### Post by techstop on 2006-09-12
A more general response is that cups-pdf lets you print from an application to a pdf file rather than a physical printer.

---

### Post by mssever on 2006-09-12
Thanks for the HOWTO. I have a couple of questions, though:

First, why on earth does this backend have to be setuid root? None of the other backends are, so it must be poorly-designed software--especially as most *nix programs go out of their way to avoid setuid root.

How come the deb doesn't set the proper permissions? The whole point of a package is to set everything up automatically. I shouldn't have to read a HOWTO.

---

### Post by yopnono on 2006-09-12
> **mssever said:**
> Thanks for the HOWTO. I have a couple of questions, though:

First, why on earth does this backend have to be setuid root? None of the other backends are, so it must be poorly-designed software--especially as most *nix programs go out of their way to avoid setuid root.

How come the deb doesn't set the proper permissions? The whole point of a package is to set everything up automatically. I shouldn't have to read a HOWTO.

I think it's on ubuntu you need to set user id.
If you read the makers website you don't need to do that, but on ubuntu yes... don't know why.  You don't need to do that on Fedora 5

[http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/](http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/)

---

### Post by NewbieLearnLinux on 2006-09-14
> **techstop said:**
> A more general response is that cups-pdf lets you print from an application to a pdf file rather than a physical printer.

Thanks for answering. I thought OpenOffice.org could export doccuments to PDF files ...

---

### Post by techstop on 2006-09-14
> **NewbieLearnLinux said:**
> Thanks for answering. I thought OpenOffice.org could export doccuments to PDF files ...

It sure does, but other applications don't have that feature, therefore the need for cups-pdf.

---

### Post by NewbieLearnLinux on 2006-09-14
I had used PDFCreator on Windoze but I rarely used it after I installed OOo-win. Nevertheless this HowTo is a nice one ...

---

### Post by factor on 2006-09-14
Hi, i'm using 64 bits ubuntu and i have downloaded the cups-pdf package v2.4.1-1 from the debian.org repository, i have followed your instructions but the printer doesn't appear as detected, do you have any idea on how to get it to work?

Regards.

---

### Post by Danny Boy on 2006-09-14
Excellent How-To Thanks :)

---

### Post by froggay on 2006-09-15
> **factor said:**
> Hi, i'm using 64 bits ubuntu and i have downloaded the cups-pdf package v2.4.1-1 from the debian.org repository, i have followed your instructions but the printer doesn't appear as detected


i have the same problem on a sun sparc server, i've used apt-get install cups-pdf and the printer pdf:/ does not appear.

So if you find a way, can you post a message here please

---

### Post by mkw87 on 2006-09-20
I managed to get cups-pdf to work in Edgy.  Instead of root-nautilus'ing and changing properties, simply open a gnome terminal and execute the following:
```
“sudo chmod +s /usr/lib/cups/backend/cups-pdf”
```

---

### Post by EddyMac on 2006-09-24
> **LoKi128 said:**
> Thanks to everyone from [this thread]("http://www.ubuntuforums.org/showthread.php?t=187516") for all their guidance. The sticking point in this whole process is that you need to be root to edit the permissions on the executable.

[LIST=1]
[*]Install the cups-pdf package (I used version 2.2.0-1)
[*]Go to System -> Administration -> Printing
[*]Doubleclick "New Pinter"
[*]Notice that there is no mention of a CUPS PDF printer
[*]Open a terminal and tpe "sudo nautilus" and then your password
[*]Go to Filesystem -> usr -> lib -> cups -> backend
[*]Rightclick "cups-pdf" and select Properties
[*]Go to the Permissions tab and click the "Set user ID" special flag
[*]Again try to add a new printer
[*]There is now a "PDF Printer" detected, select it
[*]Select the Generic, Postscript Color Printer (Rev 3b)
[*]Give it a name, like PDF Printer
[*]Right click on the newly created printer, and select Properties
[*]Click "Print a Test Page"
[*]The file should be in your Home folder, under the PDF folder
[/LIST]

Thanks for this, it worked perfectly and allowed me to print off a rather important job application form. That's another small step towards getting everything working just the way I want it. Aren't these forums wonderful?

---

### Post by makadam on 2006-10-09
Thanks for this HOWTO.  It helps me always to redo the CUPS-PDF installation.

---

### Post by A. J. Rimmer on 2006-10-10
Thanks for the help.  Now I can save all the great things I find on the Ubuntu Forum (such as this how-to) as PDF documents rather than HTML files (which entails keeping track of both the page and the associated folder of images, etc.), and am seldom connected to a printer with this laptop anyway, (since I tend to use it mostly at away-from-home WiFi spots).

Thanks again!

---

### Post by cemptor on 2006-11-07
Thanks. It works in Edgy, without setting the setuid bit.

However, can anyone help me with the following (open to other packages)

1. Change the filename and location of the printed PDF file, instead of a fixed one. It picks up the title of the page as filename and puts in in $HOME/PDF. I want to choose the location everytime

2. If I try "Print to File", it lets me choose the name and location, but prints the file as a postscriptfile, and not pdf. What am I doing wrong?

Thanks

I have Edgy 386 standard installation

---

### Post by yopnono on 2006-11-07
You will find the settings in the cups config file

/etc/cups/cups-pdf.conf

---

### Post by cemptor on 2006-11-07
> **yopnono said:**
> You will find the settings in the cups config file

/etc/cups/cups-pdf.conf

I did look, but couldn't find any options to let me set the path to be variable. I can change the path to another fixed one, but I want it to be prompted everytime I print (just as in ghostscript on windows)

I changed the TitlePref key to 1, but it still doesn't ask for a filename. What other value could I give it?

---

### Post by kkarim on 2006-12-09
Thanks a lot dude! worked great! :)

---

### Post by shakyone on 2006-12-20
Just an update to this page.  With Edgy Eft, step 8 is the "Emblems" tab.  Check the icon labeled "Special" then continue with the procedure.

---

### Post by kpictjl on 2006-12-27
When I add PDF-Printer to my windows xp machine to print to pdf across my network it sort of works.  It prints a pdf file to /var/spool/cups-pdf/ANONYMOUS/ instead of a home directory.  Plus, it cuts off about 1/2 inch off the side of the each page.  

I'm guessing there is a setting that would allow the output of an anonymous pdf print job to go somewhere else.  Where do I find that setting?

Also, I'm guessing I'm not using the correct print driver.  WinXP doesn't have the rev3b (or whatever) printer.  I tried several of the "Generic" XP drivers but none of them call themselves postcript.  I currently use "MS Publisher Color Printer", but that doesn't work right.

Any help is appreciated.

---

### Post by kpictjl on 2006-12-28
I've answered my own questions.

Here is the cups-pdf project home page (near as I can tell).
[http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/welcome.shtml](http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/welcome.shtml)

The documentation is here...
[http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/documentation.shtml](http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/documentation.shtml)

> **kpictjl said:**
> I'm guessing there is a setting that would allow the output of an anonymous pdf print job to go somewhere else.  Where do I find that setting?

In the following file
```
/etc/cups/cups-pdf.conf
```
Change the following line from this
```
#AnonDirName /var/spool/cups-pdf/ANONYMOUS
```
to something like this
```
AnonDirName /home/public/PDF
```
Note that I have /home/public shared out to anyone on my home network so that's good place to dump the pdfs.

> **kpictjl said:**
> Also, I'm guessing I'm not using the correct print driver.  WinXP doesn't have the rev3b (or whatever) printer.  I tried several of the "Generic" XP drivers but none of them call themselves postcript.  I currently use "MS Publisher Color Printer", but that doesn't work right. 

Per the documentation...
> From the cups-pdf documentation, "*On the Windows, OS/2 or MacOS system choose a color postscript driver for that network printer (the drivers for Minolta Page Works or HP DesignJet printers do a good job)*."
I selected this printer, "Minolta Color PageWorks/Pro PS", and it works fine.

---

### Post by l951b951 on 2007-01-09
Thank you for this HOWTO.  Less than 5 minutes and I can create PDFs now.  You are my hero!

---

### Post by bodhi.zazen on 2007-01-10
Nice How-to

This thread has been added to the UDSF wiki.

[http://doc.gwos.org/index.php/Print_to_PDF_with_CUPS]()

---

### Post by chrismyers on 2007-01-16
Cheers...

This is an update for Edgy:

   1. Install the cups-pdf package
   2. Go to System -> Administration -> Printing
   3. Doubleclick "New Pinter"
   4. There is now a "PDF Printer" detected, select it
   5. Select the Generic, Postscript Color Printer (Rev 3b)
   6. Give it a name, like PDF Printer
   7. Right click on the newly created printer, and select Properties
   8. Click "Print a Test Page"
   9. The file should be in your Home folder, under the PDF folder

This has less steps than the original because Edgy appears to handle cups-pdf better. :mrgreen:

---

### Post by SpEcIeS on 2007-01-18
Nice and simple Howto. Worked really well. :)

---

### Post by nrayever on 2007-01-20
This is one of the most helpful howto's i have ever read!! and this is because some wine appz have problems printing to wine printer, this solves everything!! :lolflag: :lolflag:

---

### Post by tombott on 2007-01-22
Cheers for this guide, working a treat under Edgy.

---

### Post by Hishgraphics on 2007-01-24
Excellent HOWTO.

I have to say that this is one of the reasons why my post count is so low. Whatever I needs, I searches. And there be the solution!

Great work.

---

### Post by hanexar on 2007-01-24
Wow, with Edgy it worked out of the box. Install the package and add the printer. Done, easier than ever.\\:D/

---

### Post by jaddi27 on 2007-01-24
I have installed CUPS-PDF as per your instructions, but when I print anything the resulting PDF file is blank. Does anyone know what might be causing this?

I am running Ubuntu Edgy.

Joel

---

### Post by jaddi27 on 2007-01-25
Forget about my last post. I found a newer version of CUPS-PDF and installed it and it worked fine.

---

### Post by notasquirrel on 2007-01-30
> **Franko30 said:**
> Unfortunately I have to contradict that.

HOWTOs are mostly for people not that familiar with the Terminal and commandline stuff. So I think it's nice to see where in Nautilus you can do this sort of changes.

Maybe both (the chmod and nautilus versions) would be nice. ;-)

Cheers

Franko30

Would like to comment (hoping nobody else said the same thing in the pages I didn't read... :-k )

Edgy does not seem to have the button mentioned in the howto in Nautilus.  No option for the setuid flag.  I'm pretty competent with a command line, but still don't know exactly what that flag does, and it seems Nautilus doesn't have it any more.

So, in my situation, I still need the howto but the GUI directions caused extra confusion until I flipped through several pages of reply posts.  I assume that happened because the howto was written for a different blend of Ubuntu.  (Like they ALL seem to be through Google.)

I appreciate the movement to make things easier to use in linux, but go too far and you have the opposite effect.  Like those printers that only have one button now, so you sit there poking at it trying to figure out how to print a test page because the only options are on/off and page-feed, and turns out you have to hold combinations of buttons down until lights blink or un/reinstall the cartridges, or attach it to a computer and find it in software.  Not easier!

I have the same problem with the screensaver window.  For some reason, between Dapper and Edgy they took out the "screensaver options" button so I'm stuck with default behavior on all of them until I can figure out how to change things.  Less buttons?  yes.  Less options?  yes.  Easier?  No!


Command-line will always work the way it's written so IMO that is MUCH easier.

---

### Post by xurizaemon on 2007-02-03
Hi, this didn't work for me (Edgy Eft; no printer drivers appeared in add printer dialog)

So I did it like this:

[LIST=1]
[*]In Terminal,
```

sudo apt-get -uf install cups-pdf
sudo chmod u+s /usr/lib/cups/backend/cups-pdf

```
*Is the chmod u+s still required?*
[*]In browser, visit [http://localhost:631](http://localhost:631)
[*]In the CUPS web admin interface, complete the next few steps:
[LIST=1]
[*] Click **Add Printer**. You will be asked for a username/password that has admin rights for printers on your Ubuntu machine.
[*] **Add New Printer**: Enter "PDFPrinter" for name, and any values you like for Location and Description
[*] **Device**: Select "Virtual Printer"
[*] **Make/Manufacturer**: Select "Generic"
[*] **Model/Driver**: Select "Generic Postscript Printer Foomatic/Postscript (recommended) en"
[*] Set your preferred PDF options (eg page size, A4 for me)
[/LIST]
[/LIST]

This worked fine for me. Hope it helps someone else too!

I can confirm that in Edgy, the setuid button has vanished. But it didn't matter for me as *sudo chmod u+s filename* is quicker to type than *sudo nautilus* ... *clickety clickety* and has less chance of being f*cked up.

This HOWTO might therefore need an update, although I guess not everyone has the "no printer drivers in Gnome Printer Admin" problem that I have :)

---

### Post by xurizaemon on 2007-02-03
> **TuxCrafter said:**
> Can someone rewrite this howto to work with te cups web interface?

[http://www.ubuntuforums.org/showthread.php?p=2101876#post2101876](http://www.ubuntuforums.org/showthread.php?p=2101876#post2101876) sure thing TuxCrafter :)

---

### Post by bikeman on 2007-02-10
I'm running Edgy and Cups-PDF installed very easily and runs fine, in Linux.  However, when I try to open the saved pdf file on a Windows machine with Adobe Acrobat 5 (full) or Adobe Reader (versions 7 and up), the file will not open and Adobe gives an error that the file is corrupted.  The file still opens just fine in Linux.  Is there a setting I missed?  While I can open the files (at home), I cannot share them or open them at work.  Thanks!

---

### Post by Jose Catre-Vandis on 2007-02-10
On my new Edgy install I followed the howto, but I do not see a PDF Printer avaialble to select ? Similarly if I try the CUPS web interface there is no selection for Virtual printer.

Edgy failed to detect my HP deskjet 720C as well (although it did see it in dmesg, it failed to come up in Cups.

This is what file permissions are like:
```
jose@edgy:/usr/lib/cups/backend$ ls -l
total 216
-rwxr-xr-x 1 root root  7199 2006-09-22 05:39 beh
-rwxr-xr-x 1 root root 10184 2006-10-20 19:03 bluetooth
-rwxr-xr-x 1 root root 10508 2006-09-27 11:41 canon
-rwsrwsrwx 1 jose  root 23824 2006-10-03 13:07 cups-pdf
-rwxr-xr-x 1 root root 10604 2006-09-27 11:41 epson
-rwxr-xr-x 1 root root 20496 2006-10-13 18:36 hp
-rwxr-xr-x 1 root root  9012 2006-10-13 18:36 hpfax
-rwxr-xr-x 3 root root 23452 2006-10-09 17:56 http
-rwxr-xr-x 3 root root 23452 2006-10-09 17:56 ipp
-rwsr-xr-- 2 root lp   16712 2006-10-09 17:56 lpd
-rwxr-xr-x 2 root root 12732 2006-10-09 17:56 parallel
lrwxrwxrwx 1 root root    21 2007-02-07 18:33 smb -> ../../../bin/smbspool
-rwxr-xr-x 2 root root  9868 2006-10-09 17:56 socket
-rwxr-xr-x 2 root root 13996 2006-10-09 17:56 usb
```

Any help on how to get the PDF Printer to show up?

[EDIT]
In the meantime have found a workaround.

install kdeprint
```
 sudo aptitude install kdeprint
```
using firefox:  

File > Print > Select default printer > Properties > type "kdeprint" (in the command line box, no quotes)

Click OK > Tick the print to File box > Print > enter your file name > Save

You will now have a postscript file in your home folder

Next, download the attached script, unzip it, and place it in your nautilus scripts folder
Set as executable
It should now show up in your Right Click on file > Scripts list

Right Click on your recently saved postscript file > Scripts > ps2pdf

A pdf will be created and your postscript file will be deleted

[ATTACH]25152[/ATTACH]

---

### Post by quiller on 2007-02-13
This is clearly a larger issue than just printing to a PDF, but when I try to add a new printer (from System>Admin>Printing), gnome-cups-add hangs every time. I can force-quit the window and try again, but it will always crash. Are there logs somewhere that might help? Can I try to install/upgrade cups to solve a hypothetical already-solved bug?

---

### Post by wgandhi on 2007-02-17
I'm running Edgy and Cups-PDF installed very easily and runs fine, in Linux. However, when I try to open the saved pdf file on a Windows machine with Adobe Acrobat 5 (full) or Adobe Reader (versions 7 and up), the file will not open and Adobe gives an error that the file is corrupted. The file still opens just fine in Linux. Is there a setting I missed? While I can open the files (at home), I cannot share them or open them at work. Thanks!
__________________
------
Daniel 

I have the same problem. Generated PDF does not work with Adobe Acrobat reader

---

### Post by Jose Catre-Vandis on 2007-02-18
> **Jose Catre-Vandis said:**
> On my new Edgy install I followed the howto, but I do not see a PDF Printer avaialble to select ? Similarly if I try the CUPS web interface there is no selection for Virtual printer.

Edgy failed to detect my HP deskjet 720C as well (although it did see it in dmesg, it failed to come up in Cups.

This is what file permissions are like:
```
jose@edgy:/usr/lib/cups/backend$ ls -l
total 216
-rwxr-xr-x 1 root root  7199 2006-09-22 05:39 beh
-rwxr-xr-x 1 root root 10184 2006-10-20 19:03 bluetooth
-rwxr-xr-x 1 root root 10508 2006-09-27 11:41 canon
-rwsrwsrwx 1 jose  root 23824 2006-10-03 13:07 cups-pdf
-rwxr-xr-x 1 root root 10604 2006-09-27 11:41 epson
-rwxr-xr-x 1 root root 20496 2006-10-13 18:36 hp
-rwxr-xr-x 1 root root  9012 2006-10-13 18:36 hpfax
-rwxr-xr-x 3 root root 23452 2006-10-09 17:56 http
-rwxr-xr-x 3 root root 23452 2006-10-09 17:56 ipp
-rwsr-xr-- 2 root lp   16712 2006-10-09 17:56 lpd
-rwxr-xr-x 2 root root 12732 2006-10-09 17:56 parallel
lrwxrwxrwx 1 root root    21 2007-02-07 18:33 smb -> ../../../bin/smbspool
-rwxr-xr-x 2 root root  9868 2006-10-09 17:56 socket
-rwxr-xr-x 2 root root 13996 2006-10-09 17:56 usb
```

Any help on how to get the PDF Printer to show up?

[EDIT]
In the meantime have found a workaround.

install kdeprint
```
 sudo aptitude install kdeprint
```
using firefox:  

File > Print > Select default printer > Properties > type "kdeprint" (in the command line box, no quotes)

Click OK > Tick the print to File box > Print > enter your file name > Save

You will now have a postscript file in your home folder

Next, download the attached script, unzip it, and place it in your nautilus scripts folder
Set as executable
It should now show up in your Right Click on file > Scripts list

Right Click on your recently saved postscript file > Scripts > ps2pdf

A pdf will be created and your postscript file will be deleted

[ATTACH]25152[/ATTACH]

[RESOLVED]
(For Edgy)
Downloaded and installed the experimental cups-pdf package from Debian, and instantly has a pdf printer show up in "New Printers". get it here:
[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fc%2Fcups-pdf%2Fcups-pdf_2.4.3-1_i386.deb&md5sum=758bbec4a0908874cf218e2d32950b9e&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fc%2Fcups-pdf%2Fcups-pdf_2.4.3-1_i386.deb&md5sum=758bbec4a0908874cf218e2d32950b9e&arch=i386&type=main)

or follow links to the experiemental deb from here:
[http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/download.shtml](http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/download.shtml)

And finally:

If you want to change the output directory for your PDFs:

```
sudo nano /etc/cups/cups-pdf.conf
```

Scroll down to where it says:
```
Out ${HOME}/PDF
```

Change this to whatever you want, e.g.
```
Out /mypdfs
```
and save the file. No apparent need to restart the cupsys service.

---

### Post by jharbert on 2007-02-21
> **xurizaemon said:**
> 
This worked fine for me. Hope it helps someone else too!

Worked great!  Thanks!!

---

### Post by fulanodetal316 on 2007-02-24
Gotta say, this was pretty easy for me, I have been running Edgy for about a week or so and am really new to Linux and I had no problem. BTW: I didn't have to set any flags, it just came right up so I guess your wish came true.

---

### Post by fifth on 2007-03-11
Thanks for the how-to, works great for me with a couple of wee exceptions;

1. Had to use the generic postscript driver the other PCL 3,4,5 did not work, they just gave a blank pdf file.

2. I have not been able to print from any Java apps. This gives the same problem as above with an empty pdf file. Took a bit of work to get it that far tho, was originally getting an error message of no print service.

If anyone can shed light on printing from Java I would be very grateful :)

Chris.

ps this might not be a cups-pdf problem, since i don't have any real printers on this pc to check.

---

### Post by sero on 2007-04-27
Thanks for the great tutorial. Although for U7.04 I did not need to do the permission adjustments, the PDF Printer showed up right after I did "sudo apt-get cups-pdf", which I believe does make adding a PDF Printer quite grandma friendly.

---

### Post by mmendez on 2007-05-07
> **cemptor said:**
> Thanks. It works in Edgy, without setting the setuid bit.

However, can anyone help me with the following (open to other packages)

1. Change the filename and location of the printed PDF file, instead of a fixed one. It picks up the title of the page as filename and puts in in $HOME/PDF. I want to choose the location everytime

2. If I try "Print to File", it lets me choose the name and location, but prints the file as a postscriptfile, and not pdf. What am I doing wrong?

Thanks

I have Edgy 386 standard installation

Anybody find the solution to this? This would be the icing on the cake for this howto. I for example have different folders for different things that I regularly print with pdf as I am sure many of you do too. What a pain it is to have to use mv or cp or have to go through and find it then travel through my lan and place it where I want it, when this could be done from the beginning.

thanks

---

### Post by heliopaixao on 2007-07-05
> **wgandhi said:**
> I'm running Edgy and Cups-PDF installed very easily and runs fine, in Linux. However, when I try to open the saved pdf file on a Windows machine with Adobe Acrobat 5 (full) or Adobe Reader (versions 7 and up), the file will not open and Adobe gives an error that the file is corrupted. The file still opens just fine in Linux. Is there a setting I missed? While I can open the files (at home), I cannot share them or open them at work. Thanks!
__________________
------
Daniel 

I have the same problem. Generated PDF does not work with Adobe Acrobat reader

I was generating pdf files using firefox and was selecting "Print to file" box to indicate pathname of generated file - this was causing the problem. I have generated without select this box and the the pdf file was generated on default path (in my case {HOME}/Desktop). This way the pdf file is opened by acrobat reader at windows.

---

### Post by paguilera on 2007-07-10
Thank you very much for this HOWTO.  I followed most every step with the exception of using Nautilus to change the permissions on the file.  I didn't see that option in the permissions tab so I used the command shown in post 20 instead.  Worked like a charm.

Thanks to all who helped with this HOWTO.

---

### Post by perspectoff on 2007-08-19
I using Feisty 7.04. When I go to the Permissions tab for cups-pdf backend, iIdo not see a "Set User ID" tag.

Other ideas?

> **LoKi128 said:**
> Thanks to everyone from [this thread]("http://www.ubuntuforums.org/showthread.php?t=187516") for all their guidance. The sticking point in this whole process is that you need to be root to edit the permissions on the executable.

[LIST=1]
[*]Install the cups-pdf package (I used version 2.2.0-1)
[*]Go to System -> Administration -> Printing
[*]Doubleclick "New Pinter"
[*]Notice that there is no mention of a CUPS PDF printer
[*]Open a terminal and tpe "sudo nautilus" and then your password
[*]Go to Filesystem -> usr -> lib -> cups -> backend
[*]Rightclick "cups-pdf" and select Properties
[*]Go to the Permissions tab and click the "Set user ID" special flag
[*]Again try to add a new printer
[*]There is now a "PDF Printer" detected, select it
[*]Select the Generic, Postscript Color Printer (Rev 3b)
[*]Give it a name, like PDF Printer
[*]Right click on the newly created printer, and select Properties
[*]Click "Print a Test Page"
[*]The file should be in your Home folder, under the PDF folder
[/LIST]

---

### Post by mssever on 2007-08-19
> **perspectoff said:**
> I using Feisty 7.04. When I go to the Permissions tab for cups-pdf backend, iIdo not see a "Set User ID" tag.

That seems to have been changed for some people. I have such an option when I run Nautilus as my normal user, but not when I run it as root. I don't know what's different.

The checkbox "Allow executing file as program" seems to be relevant here, but but I'm not sure what it means. Nautilus clearly is inventing their own terminology rather than using the terminology everybody else uses.

You can make it setuid from the terminal like this: ```
sudo chmod 4755 /usr/lib/cups/backend/cups-pdf
``` Read ```
man chmod
``` for an explanation of what those numbers mean.

---

### Post by Franko30 on 2007-08-20
> **perspectoff said:**
> I using Feisty 7.04. When I go to the Permissions tab for cups-pdf backend, iIdo not see a "Set User ID" tag.
Other ideas?

Hi,

when I installed 7.04 I didn't need to change any permissions - the PDF-printer showed up right after installing CUPS-PDF.

Maybe the 1st post of this thread needs to be updated (again).

Cheers

Franko30

---

### Post by ntlam on 2007-08-31
> **Franko30 said:**
> Hi,

when I installed 7.04 I didn't need to change any permissions - the PDF-printer showed up right after installing CUPS-PDF.

Maybe the 1st post of this thread needs to be updated (again).

Cheers

Franko30

I just installed cups-pdf on feisty. the 1st post was definitely old and did not apply. However I dont see PDF printer either.

---

### Post by mishu on 2007-09-03
HI,

I installed cups-pdf on ubuntu 7.04.
I have an aplication installed with wine.
I can`t print from wine to pdf printer.

Can you help me?

thank you

---

### Post by talkout on 2007-10-09
Thnaks a lot... this works fine...

---

### Post by spesheled1 on 2007-10-26
Thanks for this info.  It works perfectly.

---

### Post by ugm6hr on 2007-11-19
Only Steps 2, 10-15 are necessary for Ubuntu7.10.

EDIT: The following line is incorrect - see entries below.
I did have to manually create the Folder "PDF" in my home directory too.

---

### Post by Franko30 on 2007-11-19
> **ugm6hr said:**
> I did have to manually create the Folder "PDF" in my home directory too.

Hi,

did you do it before you printed your first PDF?

On my system the PDF folder was created the first time I printed with Cups-PDF.

Cheers

Frank

---

### Post by ugm6hr on 2007-11-19
> **Franko30 said:**
> Hi,

did you do it before you printed your first PDF?

On my system the PDF folder was created the first time I printed with Cups-PDF.

Cheers

Frank

I tried printing a "Test" page, which didn't work.  Then I created the folder, and printed a webpage - which worked.  

Given your comment - I've just tried another "Test" page - which didn't work again, so presumably it was the Test page printing function that failed, and not cups-pdf.  Sorry for the confusion.  I will re-edit my previous post.

---

### Post by labinnsw on 2007-11-23
I am using Gutsy Gibbon

After step 5, I get the following in the terminal

labinnsw@labinnsw-desktop:~$ sudo nautilus
[sudo] password for labinnsw:
Initializing gnome-mount extension
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:55: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:56: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:57: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.

and the attached roof file browser window.


If I continue to step 6, I get the attached cups pdf properties window.

Any suggestions.

---

### Post by ugm6hr on 2007-11-24
> **labinnsw said:**
> I am using Gutsy Gibbon

After step 5, I get the following in the terminal

Any suggestions.

Have a look at my post above re: Gutsy:
[http://ubuntuforums.org/showpost.php?p=3799857&postcount=117](http://ubuntuforums.org/showpost.php?p=3799857&postcount=117)

---

### Post by labinnsw on 2007-11-30
After doing step 2 and steps 10-15, the test page does not print. A window pops up which says "Test page submitted as job 170." I click OK and nothing happens.

So I try printing a page from firefox, and a window pops up which says "Progress: preparing..." then closes after a while. In the document print status window, the status of the job is held. I select the job and releases it. The status changes temporarily to processing and then reverts to held. I do this 4 times and after the 4th attempt, it dissapears. 

I go to the PDF directory and no new job is there. The last job was created October 6 (prior to my upgrade to Gutsy).

The cups-pdf_log looks like this (only larger):

Fri Nov 30 11:43:58 2007  [ERROR] failed to open spoolfile (/var/spool/cups-pdf/SPOOL/cups2pdf-7127)
Fri Nov 30 11:44:07 2007  [ERROR] failed to open spoolfile (/var/spool/cups-pdf/SPOOL/cups2pdf-7129)
Fri Nov 30 11:44:56 2007  [ERROR] failed to open spoolfile (/var/spool/cups-pdf/SPOOL/cups2pdf-7163)
Fri Nov 30 11:45:10 2007  [ERROR] failed to open spoolfile (/var/spool/cups-pdf/SPOOL/cups2pdf-7165)

Any suggestions?

---

### Post by labinnsw on 2007-12-01
This problem is still not solved, does anyone have any further ideas?

---

### Post by ashikahamed on 2007-12-01
I installed cups-pdf as per the instructions from this forum.The test page is printed in the roots folder '/root/PDF' instead of my home folder.Any solution for this problem?

---

### Post by mssever on 2007-12-01
> **ashikahamed said:**
> I installed cups-pdf as per the instructions from this forum.The test page is printed in the roots folder '/root/PDF' instead of my home folder.Any solution for this problem?

Probably the process you were printing from was owned by root.

---

### Post by ashikahamed on 2007-12-04
The test page is owned by root and so it was printed in the roots home folder.Its works perfectly for files owned by me.Thankyou

---

### Post by rbil49 on 2007-12-04
I've struggled with this and have been unable to get it working properly in 7.10. I have such a beast working fine in Edgy. So somethings broke and I have yet to figure out what.

What I've resorted to doing is to print to file, so that I get a PS file in my ~/PDF directory. Then I run a Nautilus script I wrote on the PS file and convert it to a PDF. A bit of a hassle.

So when people say it works for them, I'd sure like to know the secret. :-)

Cheers.

---

### Post by mssever on 2007-12-05
> **rbil49 said:**
> So when people say it works for them, I'd sure like to know the secret. :-)

My secret is to install cups-pdf, add the printer, and do nothing special. :) Sorry it doesn't work for you.

---

### Post by rbil49 on 2007-12-05
> **mssever said:**
> My secret is to install cups-pdf, add the printer, and do nothing special. :) Sorry it doesn't work for you.

So am I. Man, I can't believe the number of little gotchas like this I'm finding in Gutsy. Previous versions have all worked so fine. This has become quite disappointing.

Cheers.

---

### Post by tyk on 2007-12-05
ahh.. blessings to you people :)
now i have pdfs from my CAD dwgs, up to A3 size; exactly what i need
manny mannny thanks

---

### Post by labinnsw on 2007-12-06
I have found a solution to my problem. Before I give the solution, I would like to briefly describe what my problem was and how it started.

I had a working Feisty and upgraded to Gutsy. After that I could no longer print to PDF. I read and followed the instructions from various posts and nothing changed until last night. I found a post at [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/152537](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/152537) about an unrelated matter. I tried one of the solutions offered there "sudo aa-complain cupsd" and the problem was immediately fixed.

It may or may not work for you. If it does work I would like to know.

---

### Post by marym on 2007-12-07
"Go to the Permissions tab and click the "Set user ID" special flag"

I cannot find the Set User Id special flag.

Any ideas?  (I am using Feisty)

Many thanks

Mary

---

### Post by mssever on 2007-12-07
> **marym said:**
> "Go to the Permissions tab and click the "Set user ID" special flag"

I cannot find the Set User Id special flag.

Any ideas?  (I am using Feisty)

Many thanks

Mary

I think that step is no longer necessary in Feisty. At any rate, it appears that the setuid option has been removed from Nautilus. You can check the permissions by typing ```
ls -l /usr/lib/cups/backend/cups-pdf
``` and see if there's an *s* in the first field (something like this: -rwsr-xr--) If not, you can set the permissions from the terminal thus: ```
sudo chmod 4755 /usr/lib/cups/backend/cups-pdf
```

---

### Post by disabled_20220313 on 2007-12-08
Hi,

Thanks for helping Marym. She is my mother, and if it wasn't for this forum I'm sure I'd be getting a lot more phonecalls asking for help.

Cheers for keeping me less stressed.

Ciarán

---

### Post by marym on 2007-12-08
Sorted and thank you all.  :popcorn:

And don't believe everything Ciarán says - he loves getting calls from me really.  

MaryM

---

### Post by stoian on 2007-12-30
Thank you very much for the original posting, it made my day!

A note for linux users who would like to use the command line for setting the user id flag in permissions instead of using Nautilus in sudo mode - one can do the same thing by issuing this command:

sudo chmod u+s /usr/lib/cups/backend/cups-pdf

---

### Post by ali80 on 2008-03-08
I've just tested it on PARSIX and it works fine.;)
many thanks to ubuntu community :D>

---

### Post by asaz989 on 2008-03-22
```
I have found a solution to my problem. Before I give the solution, I would like to briefly describe what my problem was and how it started.

I had a working Feisty and upgraded to Gutsy. After that I could no longer print to PDF. I read and followed the instructions from various posts and nothing changed until last night. I found a post at https://bugs.launchpad.net/ubuntu/+s...ys/+bug/152537 about an unrelated matter. I tried one of the solutions offered there "sudo aa-complain cupsd" and the problem was immediately fixed.

It may or may not work for you. If it does work I would like to know.
```

Yeah, that worked for me. Thanks! (Although from what I see on that launchpad bug report, I might have to make this a startup action, as setting aa-complain might not stick after restart

---

### Post by nhomar on 2008-03-24
Thanks to everyone from this thread for all their guidance. The sticking point in this whole process is that you need to be root to edit the permissions on the executable.

   1. Install the cups-pdf package (I used version 2.2.0-1)
   2. Go to System -> Administration -> Printing
   3. Doubleclick "New Pinter"
   4. Notice that there is no mention of a CUPS PDF printer
   5. Open a terminal and tpe "sudo nautilus" and then your password
   6. Go to Filesystem -> usr -> lib -> cups -> backend
   7. Rightclick "cups-pdf" and select Properties
   8. Go to the Permissions tab and click the "Set user ID" special flag
   9. Again try to add a new printer
  10. There is now a "PDF Printer" detected, select it
  11. Select the Generic, Postscript Color Printer (Rev 3b)
  12. Give it a name, like PDF Printer
  13. Right click on the newly created printer, and select Properties
  14. Click "Print a Test Page"
   The file should be in your Home folder, under the PDF folder

Hi.
A can't install a follow this steps but in the 8th step "Set User Id" isn't,  I tried change the permissions to my user and when a go to the 9th step there is no mention of a CUPS PDF printer again.
After i changed the permissions i restart "sudo /etc/init.d/cupsys restart" can you help me please.

---

### Post by Gen2ly on 2008-03-25
Also too a person can use "Print to File" and output to postscript, then use ps2pdf to convert it.  Worked better for me than cups-pdf with a couple images in gimp.

---

### Post by mssever on 2008-03-25
> **nhomar said:**
> A can't install a follow this steps but in the 8th step "Set User Id" isn't,  I tried change the permissions to my user and when a go to the 9th step there is no mention of a CUPS PDF printer again.
After i changed the permissions i restart "sudo /etc/init.d/cupsys restart" can you help me please.

The directions in this thread are very outdated. Dapper (6.06) is the last version they apply to. The permissions that the deb sets are fine; no need to mess with them. On Gutsy, /usr/lib/cups/backend/cups-pdf should be owned by root:root with permissions 0700. In other words, ```
cd /usr/lib/cups/backend
sudo chown root:root cups-pdf
sudo chmod 700 cups-pdf
``` (This is only to undo the changes you made; if you hadn't messed with it, there would be no need to make changes.)

Then, simply add the printer as described in the post.

---

### Post by ACGarland on 2008-04-29
> **labinnsw said:**
> I read and followed the instructions from various posts and nothing changed until last night. I found a post at [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/152537](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/152537) about an unrelated matter. I tried one of the solutions offered there "sudo aa-complain cupsd" and the problem was immediately fixed.

It may or may not work for you. If it does work I would like to know.

Thanks for posting this -- it also allowed my cups-pdf to finally place documents in ~/PDF whereas before they remained 'held' and never generated a file.

---

### Post by judits on 2008-05-16
Hello!

I read all the posts in this thread hoping someone else had the same problem and had solved it, but it seems I'm the only one who has this problem.

I've just upgraded my dist to Hardy, and I've installed the cups-pdf package.

Following the tutorial, I try to add a new printer, but:

1- I choose the Generic printer and then I have to choose the model, but I have no model called postscript or something like that, I just have the "PDF file generator" (Generic PDF file generator [en] (recommended). I suppose this is not a problem at all, and I can solve this by adding the new printer via the CUPS web ([http://localhost:631](http://localhost:631)). Does anyone know if the PDF file generator is OK, or should I choose the postscript one?

2 - I haven't been able to solve this problem though I've tried many things said in this thread. When I get to the last step of adding the printer, I get an error saying "Not permitted: Maybe the password is wrong". The same happens via the CUPS web: "401 Unauthorized: Enter your username and password or the root username and password to access this page. If you are using Kerberos authentication, make sure you have a valid Kerberos ticket."

Can anyone help me, please?

Thank's!

---

### Post by mssever on 2008-05-17
> **judits said:**
> Hello!

I read all the posts in this thread hoping someone else had the same problem and had solved it, but it seems I'm the only one who has this problem.

I've just upgraded my dist to Hardy, and I've installed the cups-pdf package.

Following the tutorial, I try to add a new printer, but:

1- I choose the Generic printer and then I have to choose the model, but I have no model called postscript or something like that, I just have the "PDF file generator" (Generic PDF file generator [en] (recommended). I suppose this is not a problem at all, and I can solve this by adding the new printer via the CUPS web ([http://localhost:631](http://localhost:631)). Does anyone know if the PDF file generator is OK, or should I choose the postscript one?

2 - I haven't been able to solve this problem though I've tried many things said in this thread. When I get to the last step of adding the printer, I get an error saying "Not permitted: Maybe the password is wrong". The same happens via the CUPS web: "401 Unauthorized: Enter your username and password or the root username and password to access this page. If you are using Kerberos authentication, make sure you have a valid Kerberos ticket."

Can anyone help me, please?

Thank's!
Well, I'm running the Hardy Live CD right now and the PDF Printer is installed by default. If you don't already have it, then I'm sure the PDF file generator is what you want. Ubuntu configures the CUPS web interface strangely. You'll have to mess around with creating CUPS passwords if you want to use that interface, I think.

---

### Post by jonsg on 2008-06-23
I can confirm that "sudo aa-complain cupsd" works for me, too. Thanks, folks!

---

### Post by rpalmer2181 on 2008-07-17
> **simplyw00x said:**
> seuaniu:
Look at any desktop OS. Is installing a PDF printer 'grandma intuitive'? No. 

YES it is

---

### Post by pt123 on 2009-01-17
This doesn't work on Intrepid, I see they removed it from the default installation. 
When you install cups-pdf, and try to print it throws of errors like 
[ERROR] failed to create directory (/home/user/PDF)

When you manually create the folder it still throws of these errors.
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/270046](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/270046)

Running
sudo aa-logprof 
or
sudo aa-complain cups
seems to have fixed the problem, but still a mess.

Printing to PDF used to be one of the noticeable advantages for a desktop Ubuntu user over Windows.

---

### Post by mssever on 2009-01-17
> **pt123 said:**
> This doesn't work on Intrepid, I see they removed it from the default installation. 
When you install cups-pdf, and try to print it throws of errors like 
[ERROR] failed to create directory (/home/user/PDF)

When you manually create the folder it still throws of these errors.
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/270046](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/270046)

Running
sudo aa-logprof 
or
sudo aa-complain cups
seems to have fixed the problem, but still a mess.

Printing to PDF used to be one of the noticeable advantages for a desktop Ubuntu user over Windows.
This doesn't work in Intrepid because it doesn't need to work in Intrepid. The ability to generate PDFs is now built in to the standard print dialog and is always available. Just select "Print to file".

(Notice that this HOWTO because obsolete with the release of Edgy in October 2006. Every successive release of Ubuntu further obsoletes this HOWTO. You're best off heeding the red warning at the top of the first post and ignoring this thread.)

---

### Post by pt123 on 2009-01-17
> **mssever said:**
> This doesn't work in Intrepid because it doesn't need to work in Intrepid. The ability to generate PDFs is now built in to the standard print dialog and is always available. Just select "Print to file".

"Print to File" is so cumbersome that it is a joke.

You have to specify the filename it is not smart enough to use the Title of the webpage,. This print to file in Firefox uses "mozilla.pdf" 
While with cups-pdf it would print using the title of the webpage into a PDF folder without any fuss. 
With cups PDF you also had access to settings like DPI.

---

### Post by mssever on 2009-01-17
> **pt123 said:**
> "Print to File" is so cumbersome that it is a joke.

You have to specify the filename it is not smart enough to use the Title of the webpage,. This print to file in Firefox uses "mozilla.pdf" 
While with cups-pdf it would print using the title of the webpage into a PDF folder without any fuss. 
With cups PDF you also had access to settings like DPI.
It's Gnome. What did you expect? :twisted:

Seriously, the concept is good (you shouldn't have to install cups-pdf separately), but you're right that there are major usability issues. That should be reported as a bug, if it hasn't already been.

---

### Post by heatpumpcontrol on 2009-05-06
> **pt123 said:**
> 
sudo aa-complain cups


Printing to PDF used to be one of the noticeable advantages for a desktop Ubuntu user over Windows.

This worked for me with cups 2.5.0-1ubuntu1 on Jaunty 9.04

Great thanks

---

### Post by ldjuda on 2009-06-13
> **pt123 said:**
> 
sudo aa-complain cups
seems to have fixed the problem, but still a mess.

This worked for me, I am on Ubuntu 9.04.
```
sudo apt-get install cups-pdf
```then
```
sudo aa-complain cups
```

---

### Post by zongpog on 2009-06-17
> **ldjuda said:**
> 
```
sudo aa-complain cups
```

Why?  What does this do?


I have tried to get this to work on Ubuntu 9 with no success.  I saw that there is a PDF printer installed but its uri is something bizarre:
 cups-pdf:/

I cannot add a new PDF printer even though I changed /usr/lib/cups/backend/cups-pdf to 4755.

---

### Post by oblong on 2009-06-21
For Jaunty (9.04) I just did this:

Use Synaptic to install cups-pdf (2.5.0-1ubuntu1). That automatically added a printer called PDF. However, using that to print from an application failed with an error ("/usr/lib/cups/backend/cups-pdf failed", I think).

I then created a directory in my home directory called "PDF" (all capitals, no quotes) and it all worked, with the PDF files ending up there.

---

### Post by shields on 2009-06-22
> **oblong said:**
> For Jaunty (9.04) I just did this:

Use Synaptic to install cups-pdf (2.5.0-1ubuntu1). That automatically added a printer called PDF. However, using that to print from an application failed with an error ("/usr/lib/cups/backend/cups-pdf failed", I think).

I then created a directory in my home directory called "PDF" (all capitals, no quotes) and it all worked, with the PDF files ending up there.

That works! Thanks.:D

---

### Post by adamscottmartin on 2009-07-09
> **oblong said:**
> For Jaunty (9.04) I just did this:

Use Synaptic to install cups-pdf (2.5.0-1ubuntu1). That automatically added a printer called PDF. However, using that to print from an application failed with an error ("/usr/lib/cups/backend/cups-pdf failed", I think).

I then created a directory in my home directory called "PDF" (all capitals, no quotes) and it all worked, with the PDF files ending up there.

Worked for me as well!

---

### Post by pt123 on 2009-07-19
to get it to work in Jaunty I had to this
[b]
sudo aa-complain cupsd
[/b]

and not 
sudo aa-complain cups
as  in previous versions

---

### Post by davegk on 2009-08-03
> **adamscottmartin said:**
> Worked for me as well!

Yep, same here (Jaunty 64bit) - glad I found the instruction to create PDF directory, I also did set permissions to others, as mentioned somewhere else.

The problem is - the printer itself is rather primitive, e.g. no way to reduce resulting file size - only resolution down to 150dpi (unlike in Acrobat Pro, where you can print same document as 10MB or a 100KB file), no [obvious] way to change file name and directory, although this is a minor inconvenience. For example: printing fillable form of 730KB resulted in a 2.9MB file, whereas in Acrobat Pro, even without tweaking the "Smalest File Size" option I get 98KB file. Guess which one I would prefer to email each week? :(

Actually, the whole situation with fillable pdf forms - especially creation and editing, is really bad, or to be precise, totally absent from Ubuntu. PDFEdit is a complete rubbish, and I am not aware of any other application that even close to Acrobat Pro in functionality. I have now moved to linux completely and am determined not to use Windows at all. Acrobat Pro and CorelDRAW are the two progs holding me back. Any help greatly appreciated :confused:

---

### Post by chaanakya_chiraag on 2009-08-05
Wait, couldn't you just use the 'Print to File' printer and select pdf as the output type?  That way, you even get to set the name and location of the resulting pdf!

---

### Post by chaanakya_chiraag on 2009-08-05
@pt123: Hmmm... That weird.  I didn't have to either!  I just installed the cups-pdf package and it all worked after that.

---

### Post by davegk on 2009-08-05
> **chaanakya_chiraag said:**
> Wait, couldn't you just use the 'Print to File' printer and select pdf as the output type?  That way, you even get to set the name and location of the resulting pdf!


Yeah, but again - no way to select the resulting properties of pdf file (not that I expect "Print to File" to do that). And the main thing - "Print to File" is not available from certain application, namely Acrobat Reader. Both Cups-PDF and Print to File are okay for very basic "let's grab that page" kind of thing, but no use if you need to create a pdf file with specific qualities.

Incidentally, I have found a program, PDF Studio (not OSS, unfortunatelly) - looks almost as good as Acrobat Pro - basic editing, typewriter, interactive form handling. No way to create or edit interactive fields though, and no printing control comparable to Distiller ...

---

### Post by jdsumsion on 2009-08-12
> **davegk said:**
> Actually, the whole situation with fillable pdf forms - especially creation and editing, is really bad, or to be precise, totally absent from Ubuntu. PDFEdit is a complete rubbish, and I am not aware of any other application that even close to Acrobat Pro in functionality. I have now moved to linux completely and am determined not to use Windows at all. Acrobat Pro and CorelDRAW are the two progs holding me back. Any help greatly appreciated :confused:

You may want to try Scribus.  It's a desktop publishing app.  Still has a few rough edges, but its PDF fillable forms stuff works ok.

The downside is that you have to lay your whole page out by hand.  I couldn't get the pdf import stuff to work.

---

### Post by davegk on 2009-08-12
> **jdsumsion said:**
> You may want to try Scribus.  It's a desktop publishing app.  Still has a few rough edges, but its PDF fillable forms stuff works ok.

The downside is that you have to lay your whole page out by hand.  I couldn't get the pdf import stuff to work.

I did actually try it, although not for pdf handling - I was trying to get it to work with Corel's converted (from cdr to svg) files - it was a total disaster: Scribus couldn't open a sigle file correctly, even most simple ones were horribly messed up...  Perhaps I should try it again for pdf? I've decided to purchase PDF Studio anyway. If only they could make a proper launcher ...

---

### Post by rygle on 2009-08-20
> **davegk said:**
> I did actually try it, although not for pdf handling - I was trying to get it to work with Corel's converted (from cdr to svg) files - it was a total disaster: Scribus couldn't open a sigle file correctly, even most simple ones were horribly messed up...  Perhaps I should try it again for pdf? I've decided to purchase PDF Studio anyway. If only they could make a proper launcher ...

Inkscape should be able to import PDFs and convert them to SVG, plus it will also do the CDR to SVG conversion, as long as you have uniconvertor installed, which I think is a prerequisite of the 0.46 package anyway.

---

### Post by rygle on 2009-08-20
> **rygle said:**
> Inkscape should be able to import PDFs and convert them to SVG, plus it will also do the CDR to SVG conversion, as long as you have uniconvertor installed, which I think is a prerequisite of the 0.46 package anyway.

You can also use OpenOffice to do basic form stuff if you import the PDF (there is a plugin from Sun), then put text boxes in the appropriate spots.

---

### Post by Maddog Battie on 2009-11-03
Just in case somebody is wondering how to print to PDF in 9.10 it is as simple as the following:

sudo apt-get install cups-pdf

You will then have a PDF printer option available with the output going to a PDF directory in your home directory.

---

### Post by pt123 on 2009-11-03
good hopefully no messing around with app armour

---

### Post by HandeH on 2010-02-12
> **pt123 said:**
> good hopefully no messing around with app armour

That's true. In Jaunty I only had to manually make PDF directories to my users' home folders and then correct the folder permissions of the home folders: 
```

cd /home
chmod -v o+x [USER_NAME]
```
(^could also be applied to /home/[USER_NAME]/PDF)

This way you will avoid security risks mentioned in a bug _[report]("https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/295536/comments/65")_

---

### Post by corny on 2010-04-07
ok. i lost cups-pdf upgrading from 8.04 to 9.4 too. installing cups-pdf via synaptic brought it back ready installed as printer. i could print with it, saw the print jobs in the queue but nothing in ~/PDF. i did not want to change access rights on home directories as mentioned elsewhere.

for me [this from launchpad]("https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/295536/comments/30") did the trick:
sudo vim /etc/apparmor.d/usr.sbin.cupsd

and edit the line:
    /usr/lib/cups/backend/cups-pdf {
in order to get:
    /usr/lib/cups/backend/cups-pdf flags=(complain) {

restart AppArmor:
sudo /etc/init.d/apparmor restart

---

### Post by moreback on 2012-02-01
Hi! I was having problems to create my PDFs until finally I commented the line

```
Out ${HOME}/PDF
```

in /etc/cups/cups-pdf.conf. Now my PDF goes to /var/spool/cups-pdf/${USER} but at least gets printed :-)

---

### Post by pt123 on 2012-04-21
after an upgrade from 10.10 to 12.04 the cups was working but this helped
> [B]Just have to remember to go into System --> Administration --> Printing (configure printing), and right-click
 on the PDF printer to ENABLE it after the re-installation.[/B]

[http://ubuntuforums.org/showpost.php?p=10742423&postcount=8](http://ubuntuforums.org/showpost.php?p=10742423&postcount=8)

---

