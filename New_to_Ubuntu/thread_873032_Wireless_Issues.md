---
title: "Wireless Issues"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by shrewsbury on 2008-07-28
So I'm really new to Ubuntu. I have the operating system installed already and I'm dual booting with Windows at the moment.

The problem is that I can not get my wireless card to work.

I'm using a Marvell TopDog 802.11n (CB82) wireless adapter. I've read some things here but I'm finding it fairly difficult to understand. Also, all of the guides require the use of the internet through a wire to get things up and running.

I was wondering if anyone knows how to get this up and running without use of ethernet? And a fairly noob-proof explanation would be great.

Thanks in advance if anyone can help. :):)

---

### Post by ibuclaw on 2008-07-28
if it requires drivers, rather difficultly...

What is the output of this command in the terminal?

```
iwconfig
```
If your wireless card has been detected and the modules loaded, this will tell you.

Regards
Iain

---

### Post by bobnutfield on 2008-07-28
According to several posts in other forums, there is no native driver for Linux for this chipset.  So, if that is the case, you will need to use Ndiswrapper, which, according to same posts, WILL work with this wireless chipset.  Marvell is generally poorly supported natively in Linux.  

If that is what you have to do to get it working, it should not be too difficult for us to get you through it.

Bob

---

### Post by shrewsbury on 2008-07-28
Okay cool. that iwconfig command returns

```
lo	no wireless extensions
eth0	no wireless extensions
```

Also, is there any wireless cards that work pretty much out of the box with Ubuntu? Because of it's going to be a huge hassle, maybe just buying a new card is the way to go?

---

### Post by ibuclaw on 2008-07-28
It might not be a huge hassle, but mileage may vary depending on knowledge.

It appears that you will most definitely require a hard-link connection first though, as you'll have to get ndiswrapper, the windows drivers for ndiswrapper to use, etc...

If you are in the mindscape of getting a new wireless, [this site]("http://linux-wless.passys.nl/") may help you choose wisely. But it depends on what you have...

I recommend either Atheros PCI cards (such as Netgear 311 range), or Intel Wireless PCI (I'm using a iw4965).
But PCI is the buzzword here. I do much prefer them over shoddy USB sticks...

Regards
Iain

---

### Post by shrewsbury on 2008-07-28
Well if I'm going to have to hook this up through ethernet I'll have to take my computer in to work tomorrow.

As for your suggested cards, will those drivers automatically be installed? And if so, could you link me to a website that has them up for sale?

---

### Post by xnostradamusx on 2008-07-28
actually the purpose of the live cd is to try it first and check if its compatible with all your hardware i encountered also while installing ubuntu on both compaq presario laptop 1 minen and 1 from my cousin my cousins laptop which is compaq v6000 is pretty much compatible with ubuntu,

while mine compaq c745EE just the wireless problem just the same as you,

as they told you to use the ndiswrapper program you need to have the copy of your windows driver inf and thats the file you will need to use for that ndiswrapper.


just point of advice just try and try eventually youll get it working 

if you are really persistent to get youre wireless working

---

### Post by shrewsbury on 2008-07-30
Okay I have my computer hooked up through ethernet right now for the next ~8 hours. If anyone can try and help my get my wireless working before the time is up that'd be awesome :guitar:

[edit] and by help, I mean hopefully guide me step by step.

---

### Post by shrewsbury on 2008-07-30
No one at all?

---

### Post by bobnutfield on 2008-07-30
I will be glad to help you set it up.  As I mentioned in a previous post, I believe you will ndiswrapper with this chipset.  Do you have ndiswrapper installed?

---

### Post by shrewsbury on 2008-07-30
No I don't have ndiswrapper installed. I'm completely new to Ubuntu and don't know how to do that yet

---

### Post by shrewsbury on 2008-07-30
So.. How do I get ndiswrapper installed, anyone?

---

### Post by bobnutfield on 2008-07-30
Ok, that is not hard to get.  You will have to install via the synaptic package manager.  The harder part might be that you also need the Windows drivers for your wireless card.  You stated that it was Marvell TopDog and I had a look for you and the driver seems to be difficult to find, but I did find this link:

[http://listing.driveragent.com/pci/11ab/2a02/*?id=PCI11ab2a02fffefffe&PHPSESSID=i992jvkbfkgtungcj60cdtoc10&PHPSESSID=i992jvkbfkgtungcj60cdtoc10]("http://listing.driveragent.com/pci/11ab/2a02/*?id=PCI11ab2a02fffefffe&PHPSESSID=i992jvkbfkgtungcj60cdtoc10&PHPSESSID=i992jvkbfkgtungcj60cdtoc10")

I can't tell you for 100% that your driver can be found there, but they look the same.  It would be much better if you had the driver cd for your wireless card.  Do you have easy access to the windows drivers if these are not the ones for your card?  You will need the .inf file and the .sys file from the windows driver folder.  If you have the correct windows driver the rest will be fairly simple.

---

### Post by shrewsbury on 2008-07-30
I have ndiswrapper 'common' installed now. I have the topdog drivers for my computer but they come in a .exe just like the ones on that website you supplied me.

What do I do next?

---

### Post by shrewsbury on 2008-07-30
Okay well I installed wine through the Synaptic Package Manager as well and opened the .exe but it self extracts to "C:\cabs" but I have no idea how to navigate there as "C:" isn't a location in Linux (I think)

---

### Post by bobnutfield on 2008-07-30
OK, you need to open the .exe file and to do that you need a program called cabextract.
In a terminal type:

> sudo apt-get install cabextract unshield

Once that is installed, again in a terminal:

```
cabextract <name-of-driver-file.exe
```

This should start listing a load of files and they should be located in your home directory.  The files you are interested in are the ones end in
.inf and .sys.

Try this and post back when complete.

---

### Post by bobnutfield on 2008-07-30
The instructions I am going to walk you through are strictly in linux, nothing to do with wine.  See if you can extract the .exe file with cabextraxt.

---

### Post by shrewsbury on 2008-07-30
every time i try it returns with this

```
wade@wade-desktop:~$ cabextract <driver.exe
bash: driver.exe: No such file or directory
wade@wade-desktop:~$ 

```


Also, sorry if I take a bit to reply. I'm at work right now so sometimes I'm dealing with a customer and just now I was in a meeting.

---

### Post by bobnutfield on 2008-07-30
OK, put the file that contains your driver in your home directory.  The example I gave was just a sample.  You will need to use the actual name of the .exe file.  You do not put < in front of it.  This is just an example, but this is how the command should look:

> cabextract nameofyourdriver.exe

Put the name of your driver file in place of nameofyourdriver.

---

### Post by shrewsbury on 2008-07-30
I did all that an it returns with this

```
wade@wade-desktop:~$ cabextract driver.exe
driver.exe: No such file or directory

All done, errors in processing 1 file(s)
wade@wade-desktop:~$ 

```

I named the .exe as "driver.exe" just for ease of use since it was a much longer file.

Also, the file is on the desktop. I dunno if that's where it should be?

---

### Post by bobnutfield on 2008-07-30
You mean you renamed the file driver.exe?  Why not try using the actual name of the file and make sure it is in the directory you are running the command from, best if it is your home directory, or create a new folder in your home directory.  the cabextract command is not finding the .exe file.

---

### Post by shrewsbury on 2008-07-30
Well I think I'm running the command from the desktop since it says "wade@wade-desktop:-$"

Also, yes the file *is* named 'driver.exe'.

I don't know what you mean by the home directory??? Where is the home directory.

---

### Post by bobnutfield on 2008-07-30
If cabextract doesn't work, just rename the .exe file to .zip, double clikc on it and it should extract for you.

---

### Post by bobnutfield on 2008-07-30
When you opened a terminal, you are in your home directory.  You can see the GUI of your home directory under Place>Home Folder.  This is just the GUI view of what you are seeing from the text in your terminal.  The files are the same. If the driver.exe file is located on your desktop, drag and drop it into your home folder, just like you do in windows.  Change the name to driver.zip, double click on it, and click extract here.  This will open the files so you can get to the .inf and .sys files needed by ndiswrapper.

---

### Post by ElephantGun on 2008-07-30
I see what the problem here is. It's not cabextract, but he might have put the actual file "driver.exe" on the desktop itself instead of in the home directory. There are 2 workarounds to this.

1: use the cd command to navigate terminal to the desktop (not quite sure how to do this, I'm fairly new too)
2: move the driver.exe to /home/wade/ and then run cabextract on it

this is what I can tell just from looking at the thread...

EDIT: bob beat me to it

---

### Post by bobnutfield on 2008-07-30
Thanks for the input, that is what I was trying to get at.  The main thing is that we get to the .inf and .sys files which are inside of the .exe file.  I have many times been successful just renaming the file to .zip and extracting, but it does not always work.  It will work if there any cab files in the .exe file with cabextract.

---

### Post by shrewsbury on 2008-07-30
Okay I renamed the file to .zip and I extracted the files to the desktop.

it comes with:

[LIST]
[*]qInstall.exe
[*]qinstall.ini
[*]read_me.txt
[*]SetupTopDog.exe
[*]TDParam.bat
[*]TDParameters.exe
[/LIST]

What now?

---

### Post by bobnutfield on 2008-07-30
OK, I was afraid of that.  The files we need are inside one of the those files, probably SetupTop.exe.  This is the hardest part, getting to those files.  Try the same thing again with SetupTopDog.exe, rename it and extract.  We still need the ones ending in .inf and .sys.

---

### Post by shrewsbury on 2008-07-30
I tried to rename to a .zip and that didn't work. And when I tried to do cabextract it returned this

```
wade@wade-desktop:~$ cabextract SetupTopDog.exe
SetupTopDog.exe: no valid cabinets found

All done, errors in processing 1 file(s)
wade@wade-desktop:~$ 

```

---

### Post by bobnutfield on 2008-07-30
OK, try changing the name to .zip again and extracting that way.

---

### Post by shrewsbury on 2008-07-30
> **bobnutfield said:**
> OK, try changing the name to .zip again and extracting that way.

I had done that already. No luck.

---

### Post by bobnutfield on 2008-07-30
OK, well I need to do a little research to get at those file.  It will take me just a little while to find the anwser, but I will post back as soon as I have the answer.  As soon as we have the .inf and .sys file, it should not take long to get you up with your wireless.

---

### Post by shrewsbury on 2008-07-30
That'd be awesome. I would love to have my wireless up and running before I go home tonight :D

---

### Post by bobnutfield on 2008-07-30
Well, what has always worked for me does not seem to be working to get at the files we need.  Try to open it with the following:

> unshield l -d SetupTopDog.exe

If it reports back that no cabinet files are found, then I am out of ideas on how to open the file.  I have someone on another forum looking into it for me if this doesn't work, but it will be tomorrow before they can get back to me.

If you recall from your windows days, when you install something, you would usually see something called "InsallShield".  This command simply reverses that and opens the files so that they can be read.

Hopefully, someone else will see this post and chime in to help with this part of it.

As I mentioned, getting at these files from a .exe file would be the hardest part.  If you have someone available to you who may be able to get the windows files from their machine for your card, that might be the solution.

---

### Post by shrewsbury on 2008-07-30
Well I am dual booting but I don't know where I would look on my Windows drive for the files.

The .exe pushes files all over the drive. If you know where I should look, I can try and find them.

Also, the SetupTopDog.exe returns "Missing cabinet file on command line". :(

---

### Post by bobnutfield on 2008-07-30
The driver files are usually in (for XP) Win32\System\inf, but you are right, they could be anywhere in Win32.  I found mine in the past by using the search function and looking for *.inf and .sys.  I believe the driver name you are looking for is Net14wg.inf.  That may not be exactly right, but it will be something close.  Look for something like that.  Normally, driver .exe files are self-extracting files that the unzip command will open, but that is apparently not the case here.

I will get back to you when I have more information.  Once we have those files, we can start working with ndiswrapper.

---

### Post by shrewsbury on 2008-07-31
I figured it out.

It was easier than we made it out to be. I installed the program with WINE and then I went to the 'C:\' drive that WINE emulates (if that's how you want to call it) and I found the drivers in there.

NetMW145.sys and NetMW14x.inf

I think these should be the right files? I booted into Windows after to check what driver my Wireless adapter was currently using and it is using 'NetMW145.sys'.

So does anyone know what I do next?

---

### Post by bobnutfield on 2008-07-31
OK, that's great.  Now that you have the drivers we can proceed.  Put both of those files in your home directory...just drag and drop them.  Then open a terminal and type:

> sudo ndiswrapper -l

This is just to make sure that there are no current drivers.  Just make things simple, do these things and post back.  Then I will guide you through the rest of it.

---

### Post by shrewsbury on 2008-07-31
It returns

"Error no ndiswrapper utils found"

Also, I'm not using an ethernet connection now but two different computers instead, so I won't be able to do a copy and paste quote from the terminal this time.

---

### Post by bobnutfield on 2008-08-01
The app is available in the Synaptic Package Manager, but if you are not online you won't be able to install it that way.  You will need to copy it to a cd and then install it

---

