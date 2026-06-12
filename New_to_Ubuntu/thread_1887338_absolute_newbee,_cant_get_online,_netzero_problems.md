---
title: "absolute newbee, cant get online, netzero problems in 11.10"
date: 2011-11-26
forum: New to Ubuntu
---

### Post by monsterbronc on 2011-11-26
I finally decided I was tired of Mr. Gates and all the BS, so I got Ubuntu and Xubuntu 11.10 on cd from ubuntu and installed Ubuntu into a test desktop, it boots, it loads, it seems to work, except I haven't a clue how to work it. If I can figure it out and I like it, Xubuntu is going on my toughbook.

I got the PDF guide with it, but it appears to be written for the seasoned geek, its Greek to me. I have figured out a few things by surfing the net on my windows box, but haven't been able to do much.

My problem is I have determined that to get any of the programs for ubuntu I NEED to be online, but I am on netzero dialup and it wont work without programs available online (Wine). see my problem, (I cant get online because the program I need to get online is online) I got a couple downloads of wine from the library's internet on a flashdrive, but I cant figure out how to install them. one is a tarball, and the others a deb file of wine1.3.33, the tarball will extract, but what do I do with it after that? and all I get from the deb file is an error, bad command.

please help, Im tired of being stuck with all the anti this and anti that involved with Megalosoft, I cant even update my legit copy because they say its not, even though its the original copy that came with the store bought HP.

Steve

---

### Post by jjex22 on 2011-11-26
Hi there! welcome to the forums!

Gotta be honest I was a little thrown by the dial up, I'm assuming this isn't 56k? 

but to the packages! bit weird Gdebi couldn't open it, but not to bother! you get to learn compiling from source - seems much scarier than it actually is! 

first thing to do, make life easiest for yourself - copy the tarball to your Downloads folder - home->username->Downloads.

Now we know where it is, it's time to open the terminal - just type terminal in the launcher and it'll pop up underneath - click to launch - you should now have a console screen looking like this

username@computername ~ $

If you don't mind, I'll assume you've not used it before.

First thing to do is navigate to your Downloads directory, by using the command cd -change directory, type

cd Downloads

note that Downloads has a capital D. your terminal should now look like this

username@computername ~/Downloads $

next we need the name of the tar ball, so we list the contents of the directory with ls (lower case L), so just type 

ls

and it will display everything in Downloads - as the internet doesn't work yet I'm guessing it'll be just the wine package, something like

wine-version-number.tar.gz

how the file ends is the most important part now - does it end in .tar.gz, or .tar.bz2 ? we need to unpack the files - but the type of compression dictates how. If you've got a .tar.gz (most common) type the following command

tar xvzf package-name.tar.gz

If you have a .tar.bz2 it goes like this

tar xvjf package-name.tar.bz2

phew! right now it's decompressed, we can get to work - use ls again to show the contents of /Downloads it'll look something like this:

username@computername ~/Downloads $ ls
wine-version-number.tar.gz
wine-version-number

now we change into the new directory with cd:

cd wine-version-number

Almost there - type the following

./configure

Now if we're really lucky it won't chuck out any errors, and tell you to 'do make to compile wine' - if this is the case,move on to next step. likely outcome is error - must install flex, or error - must install bison (if you get the flex error, you'll probably get the bison error, once you install flex.) if you need them - you can get the sources from here - [FLEX]("https://launchpad.net/ubuntu/oneiric/+source/flex/2.5.35-10ubuntu1") and  [BISON]("https://launchpad.net/ubuntu/+source/bison") to install these packages - follow this guide exsaclty as I'm listing for wine - but do it first, before continuing with the wine and then cd back into the /Downloads/wine directory and run ./configure again - read on to see what you do once you've run ./configure and ended up with the message 'do make to install'.

Type

make depend

Wait for it to finish, then type

make

again wait... then finally

sudo make install

It'll ask for your password and then - off and running, once it finishes, you're done! Don't worry, this is not how we install packages day to day! once you've got your internet up and running it's all very easy!

Any questions,just post!

---

### Post by anewguy on 2011-11-26
Is your modem internal, external USB, or external serial?  Unless it is either an internal hardware modem (very rare now) or an external hardware modem (usually serial), it may take some work to hopefully get your modem working as well.  So, after you've done everything to unpack and install wine and then your netzero programs (I assume that must be what they are), try it and see if it works.  It probably won't find the modem or have problems trying to use it.  Post back when you reach that point.

Dave ;)

---

### Post by monsterbronc on 2011-11-29
Yeah, I know, Dialups pretty low tech, but Im rural, with no cable service, and I havent got TV, so anything other than dialups really expensive for me.But I am looking into arczip, they claim to support linux, and is priced the same as netzero, although they claim to be almost as fast as broadband (Ill believe it when I see it) I havent been too happy with netzero and their spotty service lately, its impossible to download anything over 2 megs, the server kicks me off after a certian amount of time (if youve ever downloaded with dialup, you know all about "time")

I tried installing bison and flex, and both threw out an error, I need GNU M4 1.4. and wine did in fact ask for flex, so Ill try to find this gnu in the same place you directed me to flex and bison, anything else I might be missing? Im gonna try and download it from work, where I have a much faster/reliable internet connection.

as for modems, can the silly winmodems be adapted to work, or am I gonna have to buy a modem? (can you still buy modems?)

---

### Post by anewguy on 2011-11-30
Winmodems can be a big problem.  It all depends if someone has written a driver for it (that's why most recommend a true hardware modem for Ubuntu - not to mention no matter what the OS it takes all the signal processing that's CPU hungry otherwise).

So, I know there is what is by now an outdated list on how much some Winmodems are supported.  If you post back your Winmodem specs (lspci or lsusb would be great) we might be able to see if it's supported.

Dave ;)

---

### Post by monsterbronc on 2011-11-30
Im assuming the info I need for the modem would be on it somewhere? A sticker, or writing on the circit board maybee?
 
I searched for gnu m4 11.10, and got a bz2 file called m4_1.4.19.orig.tar.bz2
is that what Im looking for?
 
truthfully this all crazy to me after being so used to windows, but its kinda fun. I love how open source almost everything is, and its great to have a forum like this to ask questions and get support (although Im currently still running online in windows)
 
just out of curiosity, is there a list somwhere of all the terminal commands and what they do?

---

### Post by monsterbronc on 2011-11-30
I think Flex installed, I think gnu installed, bison throws an error2, and wine does not say "do make for compile wine", it runs through a bunch of script then when it quits, it doesnt have an error like befor, then I type make etc. and it says for "make" and "make install" no rule found, or something similar. after GNU and flex appeared to work, I didnt notice any changes, are there icons or something somewhere?
 
How do I cd back in terminal?
 
As for modems, this is what Ive got...
one of the loose modems I have is a Conexant D850 56k v.9x DFVc, Ive got another somewhere, Ill look for it
my ubuntu desktop has a Medion V.9X HAM 56K 1394V
Rev: CTX900_V3, P/N: 80.0000.13.002.0007
my windows box has a Agere Systems D11561#/A1A
and the future Xubuntu laptop has a Agere Systems AC'97

---

### Post by monsterbronc on 2011-12-01
I surfed around launchpad, and apperently wine for 11.10 isnt quite right, not published or something and its not stable, so Im gonna try the previous verson for Natty, asnd Ill see what happens. Im sure if I down a few homebrews and tinker Ill get somewhere (but I might not remember how):D

---

### Post by monsterbronc on 2011-12-06
I am currently looking for a serial modem, there seem to be alot of those us robotics 56k's around, I might land one fro 15$
 
I got almost everything to work exept now wine is telling me it cannot find X for Xlib/Xfree86, whats that?

---

### Post by Bartender on 2011-12-06
OK, first off, netzero won't work.  I was on Juno for years.  Netzero and Juno use proprietary software to connect.  Windows based proprietary software.

So the first thing you gotta do is dump NZ and sign up with copper.net or fry's or just about any dial-up internet ISP that doesn't use proprietary software.

We're finally free of dial-up.  Using satellite now, which kinda sucks but better than nothing.  I have about five old US Robotics serial modems with the cables and power supplies.  Unless mailing would be ridiculous, I'll sell you one for $10.  Take a look at my old [dial-up thread]("http://ubuntuforums.org/showthread.php?t=1377619") for pointers on dial-up and US Robotics modems.  You can run one of those old serial USR's on a USB port with a USB cable like the Sabrent mentioned in that thread.

PM me if you're interested in a known-good USR modem.  I flashed all of them to the latest firmware.

AFAIC those old US Robotics modems are much better than any winmodem.  They're tough, make a faster connection than any hacked winmodem, and there's no fancy terminal commands involved.  Well, you'll probably have to suffer thru getting pppconfig set up, but it's not that bad.  Once you've got it going, they "just work".

I don't know if I'd sign up with a dial-up ISP that claimed to be "almost" as fast as broadband.  There's no such thing.  Watch out for any "accelerator" software they might try to foist on you.  It won't work in Linux.

---

### Post by Bartender on 2011-12-06
I'm gonna send monsterbronc a US Robotics modem no charge.  As far as [arczip]("http://www.arczip.com/") goes, anyone have any input?  I'd say for sure don't pay for the $19.99 "Up to 6X faster" offering.  AFAIK none of these "accelerators" work with Linux.  As I understand it, accelerators just compress files, they don't actually speed anything up.

---

### Post by monsterbronc on 2011-12-07
Ive contacted arczip and await their reply, I intend to use their $14.95 package, but I want to know if they will in fact support Xubuntu or not.
 
And thank you very much for the Modem.

---

### Post by Bartender on 2011-12-07
Don't ask them if they "support" Linux.  The answer will probably be "no".  Ask them if there's any reason why a Linux PC won't connect to their system.

Most dial-up ISP's have a basic offering that doesn't care whether you're using a PC, Mac, or Linux.

I know fry's.com works because we used it for years.  Copper.net also works, and they offer US-based support.  There are many others.

EDIT: If you're going to install Linux to a Toughbook, and if your library or school or whatever offers broadband, take a good read thru the stuff in those old posts about Package Download Scripts.  Using PDS, a Linux laptop, and our library wi-fi was the only method that I found to keep our desktop PC updated.

---

### Post by monsterbronc on 2011-12-10
I have talked with arczip, and they are "compatible" with Linux and Ubuntu, but they do not "support" it. they basically explained to me that if I have trouble logging on or whatnot, they wont be able to help and Ill be on my own, but their system should link up to me just fine as long as everything's  kosher on my end. And I told them I was going to use the USR modem, and they said I should have little to no trouble, so they seem to know something about Linux based computers, just not willing to booger with them.
 
as for the Toughbook, there is a whole plethera of info about them in another forum, [http://forum.notebookreview.com/panasonic/](http://forum.notebookreview.com/panasonic/) and Im not the first, apperently most problems arise with the touchscreen and touchpad, and a few bugs with the Wifi, but these guys seem to have it all sorted out. Im not doing it yet though, I need a few upgrade parts before I go that route. more ram, bigger drive, etc. that And its only got a floppy drive, parts are available, I just dont have the $ or time right now. but the toughbook seems to have a cult following. if youve ever used one you would know why. its made of metal, built to take the rain snow and dust, you can drop em and even stop on em, but they do weigh 10 lbs or more.

---

### Post by colorpurple21859 on 2012-01-10
This tells you how to get netzero working
[http://ubuntuforums.org/showthread.php?t=877345&highlight=netzero](http://ubuntuforums.org/showthread.php?t=877345&highlight=netzero)

---

### Post by mike555 on 2012-01-10
If you get a modem then I would recommend "basicISP" $8.95 a month and just works ..... [http://www.basicisp.net/](http://www.basicisp.net/) (at least it does here in USA)

 btw/  don't get accelerated , it doesn't work ,plus you can just use "adblock" to speed up Internet.

---

