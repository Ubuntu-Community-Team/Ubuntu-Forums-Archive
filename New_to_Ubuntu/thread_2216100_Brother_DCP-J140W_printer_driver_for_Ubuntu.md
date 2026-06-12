---
title: "Brother DCP-J140W printer driver for Ubuntu"
date: 2014-04-10
forum: New to Ubuntu
---

### Post by kiwikid1948 on 2014-04-10
I have managed to install a Brother HL-2270DW printer with no real problems (once I figured out how to do it!), but the DCP-J140W printer - with scanner - is proving way more difficult.

I have been to System Settings, selected Printing, found DCP-J140W on the list, clicked forward, but no driver found.  

I have tried using the disc which came with the printer and Wine - again no success.

I have tried using Terminal but only get as far as /home/valerie/ - how do I locate the file in Downloads from the Brother Solutions NZ site for Linux deb users.

I have been repeating these operations for about 4-5 days, off and on, with increasing frustration.

If someone could help me install this printer (preferrably with blow-by-blow instructions) I would be most grateful.

Many thanks -

Valerie

---

### Post by Double.J on 2014-04-10
Hi there! 

Gotta say I'm very impressed with the documentation for linux support! Time was there wasn't even any point looking on the manufacturers site. 

If you downloaded it will most likely have been saved at /home/valarie/Downloads/ 
notice how Downloads has a capital? This is important.

Important commands:
```
cd
ls
```

cd is change directory, so 
```
cd /home
```
takes you to home, and 
```
cd /home/valarie/Downloads
```
will take you to Downloads.

once there you can use ls (LS) to see what's in there:
[CODE]ls[/[CODE]

so long as you see BRSCAN4-0.... In the list, the instructions from the brother web page will work.

one little hint - if you type BRS (caps again) then hit tab it will probably auto complete the rest (so long as noting else in the Downloads starts with BRS) it's a great way to double check there's no typo!

Jj

---

### Post by kiwikid1948 on 2014-04-10
OK - I got as far as the ls command but BRSCAN4-0... was not on the list although linux-brprinter-installer-2.0.0-1.gz was - but permission was denied!

This is further than I have been before using Terminal!

Valerie

---

### Post by pdc on 2014-04-10
Hi Valerie; so you would like to get both the printing and scanning functions of the DCP-J140W going .........

from the Brother website I get this [http://support.brother.com/g/b/downloadlist.aspx?c=nz&lang=en&prod=dcpj140w_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=nz&lang=en&prod=dcpj140w_all&os=128)

so you have got the package [COLOR="#008000"]linux-brprinter-installer-2.0.0-1.gz[/COLOR] in your Downloads directory?

.........if you start with just the desktop (ie what the computer looks like when you have turned it on and is the desktop screen) and now open a terminal and I suggest these commands should install the printer driver for you

> [COLOR="#FF0000"]cd Downloads[/COLOR]  .....hit the enter key each time

> [COLOR="#FF0000"]gunzip linux-brprinter-installer-2.0.0-1.gz[/COLOR]

> [COLOR="#FF0000"]sudo bash linux-brprinter-installer-2.0.0-1 DCP-J140W[/COLOR]

Your printer is connected by a usb cable?

If so, during the run of the install, you will get a question

> When you see the message "Will you specify the DeviceURI ?",

 For USB Users: Choose N(No)             so you press the N key and you should have the printer driver installed; try printing something

_________________________________________________--

Scanner: if you can paste this > [COLOR="#FF0000"]uname -a[/COLOR] into the terminal later when all is done; can you paste back what  you get so we can get the correct scanning package installed for you please

---

### Post by kiwikid1948 on 2014-04-10
Do I need to close Firefox before I open Terminal?

cd Downloads indisates no such file or Directory

If there something I am missing?  Should it really be this difficult?

---

### Post by pdc on 2014-04-10
sorry: I understood you to have the Brother installer script: if we use that, to help you; so let's download a fresh copy as it is a tiny file 

(and you are welcome to leave Firefox open whilst using the terminal)

so go here [http://support.brother.com/g/b/downloadend.aspx?c=nz&lang=en&prod=dcpj140w_all&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=nz&lang=en&prod=dcpj140w_all&os=128&dlid=dlf006893_000&flang=4&type3=625) with the intention of downloading Brother's install script

and hopefully you will see a prompt (I enclose a screenshot); click on the download button and elect to SAVE if asked what you want to do ........so that should be saved to your Downloads directory

if you now open a terminal and paste in 

> [COLOR="#FF0000"]cd Downloads[/COLOR] and hit the enter key and if you now type [COLOR="#FF0000"]ls[/COLOR] and hit the enter key, the ls asks the system to list what is in that directory; you should see [COLOR="#008000"]gunzip linux-brprinter-installer-2.0.0-1.gz[/COLOR]     Is it there ok?

then > [COLOR="#FF0000"]gunzip linux-brprinter-installer-2.0.0-1.gz[/COLOR] to unpack the compressed file you downloaded

now to run the printer driver install

> [COLOR="#FF0000"]sudo bash linux-brprinter-installer-2.0.0-1 DCP-J140W[/COLOR]

.........oh and there will be the prompt > When you see the message "Will you specify the DeviceURI ?",

For USB Users: Choose N(No)  so hit the N key if you are USB ............

and that should install a printer driver; does the printer print for you now?

We can tackle the scanner side later

---

### Post by Ubi_one_2014 on 2014-04-10
otherwise

go to:
[http://support.brother.com/g/b/downloadlist.aspx?c=nz&lang=en&prod=dcpj140w_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=nz&lang=en&prod=dcpj140w_all&os=128)

download bot .deb files ( deb packages) for printer driver and scanner driver
pls note that there are 32bits and 64 bits, depending on your system, you need to choose between these deb packages

open terminal
cd /home/[usernamen]/Downloads
ls[enter]
if  the packages are there:
sudo su -[enter]
fill in password for current user
cd /home/[username]/downloads
dpkg -i *.deb [enter]

procede to configure your scanner by either repeat what you did to configure the scanner:

[COLOR=#000000]I have been to System Settings, selected Printing, found DCP-J140W on the list, clicked forward, but no driver found[/COLOR]

---

### Post by kiwikid1948 on 2014-04-11
I regret that I follow all the instructions as laid down but get no printer installed.

Now I cannot enter my password in Terminal.

I am sorry - is there an easier way or am I missing something - some words or whatever I need to put into Terminal to get it to do what I want it to do?  Are the commands being suggested enough on their own?

---

### Post by kiwikid1948 on 2014-04-11
*linux-brprinter-installer-2.0.0-1.gz* comes up in red in Terminal - does that mean anything?

---

### Post by kiwikid1948 on 2014-04-11
It is a multi-function - fax-scan-print thingy ...

---

### Post by kiwikid1948 on 2014-04-11
Should I be using Term, UTerm or UXTerm?

What is the difference between these three?  Perhaps I am starting in the wrong place - I have been using TERM ...

Many thanks -

Valerie

---

### Post by kiwikid1948 on 2014-04-11
Apparently no difference between the three - they all come up with the same result - no such file or directory, when I enter gunzip linux-brprinter-installer-2.0.0-1.gz

---

### Post by pdc on 2014-04-11
Valerie: I don't know what you mean by TERM

........were you able to follow the instructions in the post earlier; to click on the Brother installer script; and download it into your computer: ............do you think that happened?

---

### Post by kiwikid1948 on 2014-04-11
No - it did not happen.

I don't know what I am doing wrong ...

Nothing I have tried - following all the instructions provided - has worked, so far!

Valerie

P.S. On the applications thing, it uses the terms TERM, UTERM and UXTERM for varieties of Terminal.

---

### Post by kiwikid1948 on 2014-04-11
Using terminal - once I get to where I need to enter a password for valerie, it refuses to go any further.

That is, after I have entered sudo - the cursor stops and will not let me write anything in there.

At least I have now managed to get to the sudo command before the bash command!  Does this mean progress is being made :D

Valerie

---

### Post by westie457 on 2014-04-11
When typing in your password in a terminal nothing shows on the screen. Just type in the password and hit 'Enter'.

Nothing shows so that if someone is looking at your screen they do not get an idea of how many characters are in your password.

---

### Post by kiwikid1948 on 2014-04-11
Thanks Westie.

How do I check what my password is - the two most likely I tried did not accomplish anything.

Or is there somewhere I can go to change my password?

---

### Post by westie457 on 2014-04-11
The password for sudo is the same as the one set up for the user at installation of the OS.

If that one is forgotten it can be changed. See here for a 'How-to' [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Edit: The sudo password is usually the same as the used to log in to the system at start up (Log in Screen).

---

### Post by kiwikid1948 on 2014-04-11
Thank you.  Presumably this is also the one I have used to authenticate installations using Wine?  If this is the case, terminal won't accept it for some reason.

---

### Post by pdc on 2014-04-11
>  If this is the case, terminal won't accept it for some reason. 

...................do you mean it says ........................wrong password ...........................................

---

### Post by kiwikid1948 on 2014-04-11
Yes ...

---

### Post by Ubi_one_2014 on 2014-04-11
kiwikid1948

did you install the debian packages?

if yes, go to: 127.0.0.1:631
login as root

so userame = root
pass = root pass

Can you login? if NO please install cups
if YES , report back and i will guide you

---

### Post by JeQhdMD on 2014-04-11
She has disabled sudo because of a reply by Ubi.  So now, she needs to know how to reenable it and start from start.

Also, installing the two debs from Brother site will not install the drivers!   She needs to install the base script (installer) and has been following conflicting advice.

---

### Post by gifford on 2014-04-11
So now that we as a group have borked her system, maybe it is time we start paying attention to the level of the user and respond in an appropriate manner. Since Ubuntu is set up to not have the user log in or use as root, why would we ever advise a new comer to Ubuntu to do so?

Clearly, kiwikid1948 was asking for specific advice and needed something straight forward and easy to do. I would hope that this experience will not prejudice her views of Ubuntu or the forum users.

---

### Post by kiwikid1948 on 2014-04-11
Many thanks for all your assistance and patience with me as I have struggled with this process of installing my Brother multifunction DCP-J140W on Unbuntu.

It was installed on both Windows XP and Windows 7 before I moved to Ubuntu a couple of weeks ago - at which time I also had access to an HP mini netbook as part of my home network.  However, I managed to damage the tip on the charger for the HP mini and have now ordered a replacement from HP but it will take a "few weeks" to get here.  When I am able to connect to the netbook again, I am hoping the DCP-J140W will still be connected to it, at which time I will be able to use the scanner function without any trouble - and I can always re-install it if it is no longer part of the old network.

So, I have decided not to continue with trying to install this multifunction on to Ubuntu - it has taken up enough of my time already, and continues to be a no-goer, so there seems little point in continuing with the effort.  I have managed to install a Brother HL-2270DW to Ubuntu, so I do still have a printer I can use - but sooner or later I am going to need to be able to use a scanner ...

Again, many thanks to all for your continued persistence and patience with me during this process -

Valerie

---

### Post by pdc on 2014-04-11
I hear in NZ you have a wonderful site called trademe 

here you are Valerie;

[http://www.trademe.co.nz/computers/peripherals/scanners/auction-716385777.htm](http://www.trademe.co.nz/computers/peripherals/scanners/auction-716385777.htm)

flatbed scanner; plug it in; it is completely supported by sane; [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) currently going for $1NZ; no software needed

it will work out-of-the-box for you

---

### Post by tbsoft2001 on 2014-04-14
NOt sure if this thread is still live; wanted to tell the Kiwikid that I feel her pain . . . I have a DCP-J140W as well ... networked wirelessly... thought my problem was the wireless connection but now I have it running - at least on the printer side.

If you still care, Was able to do this by downloading the linuxbr-printer-installer from here: [http://support.brother.com/g/b/downloadlist.aspx?c=nz&lang=en&prod=dcpj140w_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=nz&lang=en&prod=dcpj140w_all&os=128)

For someone not familiar or comfortable with the command line, this might be problematic as CLI is the only way to install. It was a relatively simple process - unzip the downloaded file, make it executable and then run it - a rather long set up procedure then takes place with lots of additional package downloads, licenses and set up. However, at the end, it worked. It is rather complicated so if you choose to go this way you might try a "trial" run-through to familiarize yourself with the steps . . and the information you will need to input - not much, but some details are helpful.

I have not been able to get the scanner to function; one of the downloads is (supposedly) software enabling one-touch scanning with the "Scan" button on the J140W - I'm still working on this.

If you'd like added information and a step-by-step of what I actually did, I'm happy to supply it. Just don't want to go into all that when there's no interest.

Good luck!

---

### Post by bozzchem on 2014-04-14
> **kiwikid1948 said:**
> I have managed to install a Brother HL-2270DW printer with no real problems (once I figured out how to do it!)

I am a 100% noob/dumb as a box of rocks when it comes to all things Linux.  I have tried Ubuntu in the past but my lack of patience always made me go back to Windoze.

I just torched an old laptop to remove Vista (hideous OS) and it is now running Lubuntu.  I am a bit shocked at how quickly Lubuntu boots and is ready to roll.

The HL-2270DW is precisely the printer I am attempting to install and operate via my home network.  I do not use USB with this printer.  It is only used as a wireless printer.  

Is there a site or video that can guide me through this installation on a Lubuntu machine?

I'm not giving up this time.  I'm not putting Windoze back on that machine.  I will learn the process or the laptop will keep papers from moving on my desk.

Much thanks/gratitude to all who are willing to help!

bozzchem

---

### Post by pdc on 2014-04-14
well; I had a go in post #4 so the instructions are there: Brother used to guide you on their website to the specific drivers you needed; 

.....now they have standardised on an installer: a bit like having a kindly friend stand by and do the work for you: so if I paste here what you need to do; and I will enter [COLOR="#0000FF"]HL-2270DW[/COLOR]  as  you say that is your printer; we put lubuntu on an old asus we had; it works well;

so get the installer from here [http://support.brother.com/g/b/downloadhowto.aspx?c=au&lang=en&prod=hl2270dw_all&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadhowto.aspx?c=au&lang=en&prod=hl2270dw_all&os=128&dlid=dlf006893_000&flang=4&type3=625) and save it to your Downloads folder (that will be the default folder)

it comes down as [COLOR="#008000"]linux-brprinter-installer-2.0.0-1.gz[/COLOR] and I suggest you paste the commands in using your mouse and the top line of the terminal: ie Menu and along to Edit and down to Paste ........

Commands are in red:

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]gunzip linux-brprinter-installer-2.0.0-1.gz[/COLOR]

> [COLOR="#FF0000"]sudo bash linux-brprinter-installer-2.0.0-1 HL-2270DW[/COLOR]

then as you have a network printer you will have to complete section 5b here [http://support.brother.com/g/s/id/linux/en/instruction_prn1a.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_prn1a.html?c=us_ot&lang=en&redirect=on)

......so have a read at this a couple of times **before you start the install** and feel more familiar with it before it comes to you from the terminal install

_________________

so ready to have a go? Enjoy

---

### Post by kiwikid1948 on 2014-04-19
Please note:  I have now given up trying to install Brother DCP-J140W printer, and will no longer be checking this thread.

I have followed all instructions suggested, all to no avail.

I shall probably return to Windows as soon as I can aford to buy a box ...

Thank you -

Valerie

---

### Post by stevelamb-x on 2014-04-19
This URL may be helpful, if your interested kiwikid1948

UK

[http://support.brother.com/g/b/downloadlist.aspx?c=gb&lang=en&prod=dcpj140w_all&os=128]("http://support.brother.com/g/b/downloadlist.aspx?c=gb&lang=en&prod=dcpj315w_eu_as&os=128")

NZ

[http://support.brother.com/g/b/downloadlist.aspx?c=nz&lang=en&prod=dcpj140w_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=nz&lang=en&prod=dcpj140w_all&os=128)

---

### Post by kurt18947 on 2014-04-19
I don't know if Valerie will check back but I think there was some bad advice given.  The Brother install script or any other install commands must be run from an account having SUDO privileges.  I did not see that mentioned until the install was already a mess.  The installer works well for the printer but there is some additional work required to get the scanner functional.

---

### Post by pdc on 2014-04-19
thanks Kurt; I believe you have highlighted an important issue;

> The Brother install script or any other install commands must be run from an account having SUDO privileges. I did not see that mentioned

can you detail which posts you saw these errors committed in please?

---

### Post by stevelamb-x on 2014-04-20
I had to download a .deb file, .lpr file and cupswrapper if I remember correctly. I started off on Ubuntu 9 and did every update until I got to 13.10. Ubuntu seems quite good at detecting hardware, almost PnP. Total newbie to Ubuntu having just moved from Vista. Would leave Windows altogether except for one problem I have.

---

### Post by MrSteve on 2014-04-20
if you right click the downloaded .deb file(s) you will be able to install the file(s) using the ubuntu software centre which will be on the right click menu
i do hope that a lesson has been learned here, there should be LIMITED CLI advice in the beginners forum (only at the last resort should CLI advice be given) ...

edit by me
to correct an absolute 'no'

---

### Post by kurt18947 on 2014-04-21
> **MrSteve said:**
> if you right click the downloaded .deb file(s) you will be able to install the file(s) using the ubuntu software centre which will be on the right click menu
i do hope that a lesson has been learned here, there should be no CLI advice in the beginners forum (only at the last resort should CLI advice be given) ...

Part of the problem is that Brother's install process is set up to use the command line.  The .deb installers didn't work on 64 bit distros at one time, all printer packages were/are 32 bit and they required a --force-all 'switch'. I don't know if they do now or not.  The installer scripts take care of that without user intervention but still must be run from the command line.

---

### Post by pdc on 2014-04-21
I suspect from reading the installer script that Brother have taken account of 32bit and 64bit systems

eg some selections

> dellist=''
cpscanlibmodules(){
  for file in $1
  do
    lib64mod=/usr/lib64/$file
    libmod=/usr/lib/$file

    if [ -f $lib64mod ];then
      if [ -d /usr/lib ];then
        if [ ! -f $libmod ];then
           cp $lib64mod  $libmod 2> /dev/null
           if [ -f $libmod ];then
             dellist2=$(echo $dellist $libmod)
             dellist=$dellist2

> LIB64FLT=/usr/lib64/cups/filter
LIB32FLT=/usr/lib32/cups/filter
LIBFLT=/usr/lib/cups/filter

> arch=$(uname -m | grep "amd64")
if [ "$arch" = '' ];then
  arch=$(uname -m | grep "x86_64")

---

### Post by kurt18947 on 2014-04-22
Yes, the script does indeed account for 32 & 64 bit.  I don't know a way to run it except from the command line though.  My thought regarding the inexperienced user and CLI is to give "From an account with SUDO privileges, copy and paste these lines, one at a time" type instructions.  Also most of the 'pre-required procedures' appear to be not required with recent Ubuntu releases.

---

