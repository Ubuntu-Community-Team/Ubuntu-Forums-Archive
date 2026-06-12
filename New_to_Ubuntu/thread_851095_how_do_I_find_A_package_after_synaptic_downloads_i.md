---
title: "how do I find A package after synaptic downloads it?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-06
how do i find a package after synaptic downloads it?  It's not in a menu.  It's not on my Desktop.  It's not in traker search tool.  So why isn't this easy?  I'd have more luck with pen and paper

---

### Post by steveneddy on 2008-07-06
In the terminal type the name of the application

or in terminal type

```
locate name_of_application
```

usually if you can launch the software from terminal, you can build a launcher.

---

### Post by adamogardner on 2008-07-06
found it!  how do I build a launcher?  or better how do I open this and set up my aircard?

---

### Post by nothingspecial on 2008-07-06
Right click on the desktop. Select create launcher. Fill in the boxes and bingo. :)

---

### Post by steveneddy on 2008-07-06
> **adamogardner said:**
> found it!  how do I build a launcher?  or better how do I open this and set up my aircard?

open what?

---

### Post by angry_johnnie on 2008-07-06
Usually (not always) the command that is used to launch an app is the same --or very similar-- to the app's name.

For example, to launch firefox 2, you would have to issue the command **firefox-2**.

If you're not sure, you could try typing the name of the app, or the beginning of the name of the app, and then press the tab key, and the terminal will autocomplete it.

---

### Post by hyper_ch on 2008-07-06
generally only gui applications are added to the menu... CLI commands are not...

---

### Post by Tomatz on 2008-07-06
> **adamogardner said:**
> how do i find a package after synaptic downloads it?  It's not in a menu.  It's not on my Desktop.  It's not in traker search tool.  So why isn't this easy?  I'd have more luck with pen and paper

What app is it?

---

### Post by werries on 2008-07-06
yeah, what package did you download?

---

### Post by issih on 2008-07-06
Ok, you sound like you need to know a few things about how linux operates....apologies if you already know this.

Almost everything that is installed via synaptic is installed into fairly well defined locations (If I remember correctly things usually get dropped into /usr somewhere, and it will depend if its a library file or a an actual binary as to exactly where)

Usually however, it doesn't really matter where it is. Because these things get put somewhere that linux expects to find them, the system is set up so that the PATH variable already contains all the likely locations. Because of this, when you try to run a command from a terminal you can just type the command name from any location within the directory tree and the system will search the defined path for a matching program.

In essence you can launch firefox with the command firefox from anywhere...you don't actually need to know where it is.

Therefore as long as you know, or can guess with the aid of tab completion what the command name is, you can launch the program.

Making a launcher is then easy as you just enter that command name into the command line and away you go.

You rarely actually need to know the actual location where synaptic has installed files, however, if you really want to know, just open synaptic, navigate to the package you are interested in, select it and then click properties. select the installed files tab and you get a list of all the files installed by installing that package.

You have to ignore entries that are just directories, these seem to get listed too, general rule, if you are trying to find the executable name, look for files that have been placed in a bin directory. bin stands for binary and is where linux executables are nearly always kept.

Hope that helps.

---

### Post by adamogardner on 2008-07-06
the app is NDISWAPPER ...but there is already a thread on it I just got slack ffrom for steering this conversation to what I opened that thread for.  so what to do, what to do?

---

### Post by nothingspecial on 2008-07-06
You can install ndisgtk which will give you a gui for ndiswrapper.
It`s in synaptic.

---

### Post by adamogardner on 2008-07-06
nothing happened (like after I bought bold party blend CHEX MIX)  I'll try and restart maybe.

---

### Post by issih on 2008-07-06
installing ndisgtk is a good plan.

That provides a gui front end to ndiswrapper which can be found under:

System->Administration->Windows wireless Drivers

Hope that helps

---

### Post by adamogardner on 2008-07-06
I agree,  that was a good plan.  I found it but am having again some confusion.  a window says select .inf file to install.  so I double clicked the one that ends in .INF   AUTORUN.INF    an error popped up but when I tried it a second time it said the driver was already installed, but it snot displayed in the GUI.

---

### Post by issih on 2008-07-06
I doubt that the autorun.inf file is the one you need to be honest. That will be the file that tells windows what to run when you pop the cd in the drive.

You need a different inf file. chances are its buried inside the .exe fie somewhere, you probably need to look at using cabextract to ocrack open the exe file and see whats inside it.

---

### Post by caljohnsmith on 2008-07-06
> **adamogardner said:**
> I agree,  that was a good plan.  I found it but am having again some confusion.  a window says select .inf file to install.  so I double clicked the one that ends in .INF   AUTORUN.INF    an error popped up but when I tried it a second time it said the driver was already installed, but it snot displayed in the GUI.
I think you might be a little mixed up; you don't want to use "autorun.inf"--you want to use the .inf file for your wireless card. You can get that from the CD that should have come with your wireless card. If you don't have the CD, you can download drivers (the .inf and .sys files) for your wireless card from the manufacturer's website of your card.

---

### Post by adamogardner on 2008-07-06
"You need a different inf file. chances are its buried inside the .exe fie somewhere, you probably need to look at using cabextract to ocrack open the"

ok  how?  I have the .exe file  it doesn't install in its entirety.

---

### Post by Tomatz on 2008-07-06
> **adamogardner said:**
> "You need a different inf file. chances are its buried inside the .exe fie somewhere, you probably need to look at using cabextract to ocrack open the"

ok  how?  I have the .exe file  it doesn't install in its entirety.

Attach the driver to your next post so i can find you the relevent file ;)

---

### Post by adamogardner on 2008-07-06
I don't have any way to cut and paste that I know Of.  and what do you mean attach the driver?  it's a folder with a bunch of stuff in it.  one is .exe  one is .inf  i tried all of them i think.

---

### Post by Tomatz on 2008-07-06
> **adamogardner said:**
> I don't have any way to cut and paste that I know Of.  and what do you mean attach the driver?  it's a folder with a bunch of stuff in it.  one is .exe  one is .inf  i tried all of them i think.

Zip the file up (hilight, r-click, create archive)

Then when you write your next post, at the top of the box you will see a paperclip.

Click it and attach the archive ;)

---

### Post by jualin on 2008-07-06
"Attach" go to "New Reply" and click on the "clip-like" icon and then just select the file. If you have a folder then compress the folder to something like .tar or .zip so it can be one big file and so you can attach it to your next post. Hope this helps!

---

### Post by issih on 2008-07-06
a .exe file is often a bit like a zip file, it actually contains a load of other files bound together and hidden from view. Chances are you need to rip open the .exe to find the .inf file you need. Look into using cabextract or indeed post the .exe here and get some other kind soul to do your donkey work :)

One other way to do it that I've used is to just run the setup.exe under wine, then go exploring in the virtual C drive to find the required files.

---

### Post by jualin on 2008-07-06
> **issih said:**
> donkey work :) :lolflag::)

---

### Post by forger on 2008-07-06
Wouldn't it be easier to tell you the Brand and Model name / number to find the drivers? :)

---

### Post by RequinB4 on 2008-07-06
You can always just go to packages.ubuntu.com for the .deb

---

### Post by adamogardner on 2008-07-06
how do I "zip up" the file, and there is no "attach" after right click.  I only have "show hidden files" as an option.  I see nothing that any of you mention.  I must be on the wrong page.

---

### Post by issih on 2008-07-06
right click on the file and look for the archive option. That will probably create a tar.gz file by default, but thats fine. To attach that to the forum hit new reply, and in the little editor click on the paperclip icon.

Hope you follow that

---

### Post by adamogardner on 2008-07-06
i followed it the first time.  I hit the mouse button on the right while hovering the pointer over various files.  first file is the one all the other ones reside in.  It's found in the left column in the file browser. When I right click that it offers zero of two options (remove rename.)  If I click on say the .exe file in the column on the right it offers one of two options (show hidden files, and add to bookmarks).  Perhaps I am totally misunderstanding you?   This "select .inf file" browser is resultant of my using ndiswrapper.  That probably means nothing though.

---

### Post by issih on 2008-07-06
Ok, that isn't helping. Simply open a file browser seperately. Go to Places->Home

then navigate to the folder containing the files you want to send to the forum. If they are on a cd copy them off there first into a folder on your hard drive.

once you have all the files you want to send contained in a folder on your hard drive, navigate the file browser so you can see that folder in the right hand pane.

Right click on that folder and select archive.

That should create a file named similarly to the folder but with an extension like tar.gz or similar.

upload that to the forums as described before.

---

### Post by adamogardner on 2008-07-06
ok i hit create archive   where is it?   I did It twice now two are missing

---

### Post by adamogardner on 2008-07-06
what dO I keep doing when I upload to this forum and nothing happens?  I browse from the clip,  find the .exe  that I apparently archived twice (though I have know idea where they went.)  And then I hit upload and then once again absolutely nothing happened.

---

### Post by issih on 2008-07-06
In the little attachment screen you will see a list of filetypes.

Your attachment HAS to be one of those types and it has to be less than the specified size for that type of file for the attachment to work.

You'll notice that .exe is not a filetype that is accepted!

You need to get the archiving thing sorted. I assume you are used to zip files in windows. We are basically trying to achieve the same thing here. Archiving a file should create a new file in the same directory as the one you are archiving, which will have an extension like .zip or .tar.gz. What happens when you try to create an archive, what exactly are you doing? you have to achieve that in order to upload something

---

### Post by adamogardner on 2008-07-06
well if I open my .exe file then the application installation begins.  there are no smaller files inside that I know how to get at and do whatever I have to do to get you to see it.  Should I try another component of that folder?

---

### Post by issih on 2008-07-06
The exe file wouldn't do anything at all unless you are either running windows or you have wine installed.

If you want to do as some suggested and upload a file so someone else can extract it for you then you need to archive the exe file, not run it.

In windows send it to a compressed folder.

In ubuntu right click on it and archive it.

If you want to open up the exe file yourself you need to try running tar -xvzf on it in a terminal, or install cabextract and run that on it.

To be honest it doesn't seem like you are likely to be comfortable with the terminal commands necessary to achieve this, but we can try if you like.

stop trying to make the exe file do something as it stands....it won't. its no use to you in its current form.

you have to either:

1. Upload it somewhere where someone can get at it and open it up for you

2. Tell us the make and model of your wireless adapter so we can find the files ourselves

3. install cabextract via synaptic and then use that to extract the exe file.

---

### Post by adamogardner on 2008-07-06
verizon AC595U. sierra makes it   

I am trying but I think I need to learn the basics.  As far as learning windows first...yeah for 2 months.  ubuntu for 2 also.  So I've learned just enough of windows to confuse the hell out of me.  I like Ubuntu though and want to stay, and I appreciate your patience.  I am going to try the other things you suggest still but above is the make model if you want to speed things along I don't blame you.

oh and I do have wine  but I don't intend on trying to run it through this.

---

### Post by adamogardner on 2008-07-06
actually terminal commands are cool and I like the enviornment and wouldn't mind at all taking that route.  I just need to know what to do, right?  I think It would be clearer than trying to describe what the pictures will and won't let me do.

---

### Post by adamogardner on 2008-07-06
here's what i got:  
adamogardner@CRONUS:~$ locate cabextract
adamogardner@CRONUS:~$ cabextract
cabextract: No cabinet files specified.
Try 'cabextract --help' for more information.
adamogardner@CRONUS:~$ cabextract --help
Usage: cabextract [options] [-d dir] <cabinet file(s)>

This will extract all files from a cabinet or executable cabinet.
For multi-part cabinets, only specify the first file in the set.

Options:
  -v   --version     print version / list cabinet
  -h   --help        show this help page
  -l   --list        list contents of cabinet
  -t   --test        test cabinet integrity
  -q   --quiet       only print errors and warnings
  -L   --lowercase   make filenames lowercase
  -f   --fix         fix (some) corrupted cabinets
  -p   --pipe        pipe extracted files to stdout
  -s   --single      restrict search to cabs on the command line
  -F   --filter      extract only files that match the given pattern
  -d   --directory   extract all files to the given directory

Almost there.  this however is confusing.  I know I need to do something with that folder? or .exe adamogardner@CRONUS:~$ locate cabextract
adamogardner@CRONUS:~$ cabextract
cabextract: No cabinet files specified.
Try 'cabextract --help' for more information.
adamogardner@CRONUS:~$ cabextract --help
Usage: cabextract [options] [-d dir] <cabinet file(s)>

This will extract all files from a cabinet or executable cabinet.
For multi-part cabinets, only specify the first file in the set.

Options:
  -v   --version     print version / list cabinet
  -h   --help        show this help page
  -l   --list        list contents of cabinet
  -t   --test        test cabinet integrity
  -q   --quiet       only print errors and warnings
  -L   --lowercase   make filenames lowercase
  -f   --fix         fix (some) corrupted cabinets
  -p   --pipe        pipe extracted files to stdout
  -s   --single      restrict search to cabs on the command line
  -F   --filter      extract only files that match the given pattern
  -d   --directory   extract all files to the given directory



almost there...

---

### Post by issih on 2008-07-06
hmmmn, I seriously doubt ndiswrapper is going to help you out here. Ndiswrapper is meant for wireless networking devices (i.e. 802.11 devices) to connect from computer to a router which has a hard line connection to the internet.

I suspect you have a usb modem device operating over a cellular network, if thats the case I don't think ndiswrapper will do you any good at all, although I may be wrong.

---

### Post by issih on 2008-07-06
[http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601)

That page is your best bet, although I think the module may be included in ubuntu by default, so you may need to just configure your ppp settings.

I have never used such things however

---

### Post by adamogardner on 2008-07-06
back to square one, the snake swallows it's tail, I started at gnomeppp went to kppp, went to wine, and tried bridging a path into my windows partition, finally thinking I got it with ndiswrapper, to be broought back to start.  I'm chagrined.  thanks for your time.  I'm sorry It proved fruitless.

---

### Post by Tomatz on 2008-07-07
> **adamogardner said:**
> back to square one, the snake swallows it's tail, I started at gnomeppp went to kppp, went to wine, and tried bridging a path into my windows partition, finally thinking I got it with ndiswrapper, to be broought back to start.  I'm chagrined.  thanks for your time.  I'm sorry It proved fruitless.

Send me a link to the driver. Then i'll post you a step by step howto.

;)

---

### Post by adamogardner on 2008-07-07
a link to the driver?   I have it on disk.  Do you mean you want a link to a website?  or a link to a program (driver)  I'm not sure what driver you want but try this maybe ...hold on let me find something....
           
             1. Download the sierra.c driver(v.1.0.6) file
                 
              2. Download the pppd scripts file

Is this right?
found this too:

 The latest released kernel driver was tested with kernels 2.6.18 and 2.6.20.

---

### Post by adamogardner on 2008-07-07
I don't know why they are not links.  i copy and paste?  or is this something else I need to spend t months learning?

---

### Post by Tomatz on 2008-07-07
> **adamogardner said:**
> I don't know why they are not links.  i copy and paste?  or is this something else I need to spend t months learning?

Click the paperclip to attach a file to the forums. I have attached a screenshot explaining....

You will need to zip the file up first (r-click on the file, create archive).

;)

---

### Post by lazyart on 2008-07-07
Is this all about getting an aircard to work?  I use one on my laptop and didn't need to go through all of this.

Give some information about your hardware and version of ubuntu.  Maybe start a new thread mentioning the aircard.  It's a great device.  Mine is a u757 but really they all work pretty well in Ubuntu.  But you'll need KPPP not GnomePPP to get it to connect.

---

