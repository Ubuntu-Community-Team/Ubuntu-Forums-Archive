---
title: "Printer Woes networked MFC-7440N"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by jfbooth on 2012-01-16
This is Xubuntu 11.10.  Everything used to work just fine.  Discovered printer and scanner no longer works.  Twiddled around and got the scanner to work .. but not the printer.

I can ping the printer
All of the following has been done:

```
sudo apt-get install tcsh
sudo dpkg -i --force-all brmfc7440nlpr-2.0.2-1.i386.deb
sudo dpkg -i --force-all cupswrapperMFC7440N-2.0.2-1.i386.deb
```

Click System/Printing and window opens titled 'Printing - localhost' which says 'There are no printers configured yet.'  Click ADD button.

Window opens, Select option NETWORK PRINTER.  Select Brother MFC-7440N (BRN0080770794D4) under Network Printers (the printer I am trying to fix).  To the right it says Host: BRN0080770794D4 and a button to PROBE.  Below that is says BINARY_P1

Click FORWARD button.  Small window opens, says 'Searching for drivers' . and after several seconds it closes.  That is as far as I can get.

Switch to Firefox and go to [http://localhost:631](http://localhost:631)  .. the CUPS HOME PAGE.

Click PRINTERS tab ... "No printers",  Click Administration tab.  Click 'Add Printer'.  

Bullet 'Discovered Network Printers: Brother MFC-7440N (Brother MFC-7440N)'  Click 'Continue'.

Three boxes:

Name:  Brother_MFC-7440N  (filled in)
Description: Brother MFC-7440N (filled in)
Location: Back room (I fill this in)

Under those 3 boxes is:

Connection: 	lpd://BRN0080770794D4/BINARY_P1  (filled in)
Sharing: 	Share This Printer (UNCHECKED)

Click Continue button.  New window:

> Add Printer Brother_MFC-7440N Error

Unable to get list of printer drivers:

    Unknown

Add Printer Brother_MFC-7440N Error

Unable to get list of printer drivers:

    Unknown

Yes .. this is listed twice.

Been working on this for about 12 hours and am at end of rope.  I have tried everything I can find on this support site .. tutorial, other posts.  Googled the problem and gone to other websites.  No love found.

By the way .. AFTER twiddling like I have done ... I found out the orig problem is that my printer's IP had changed.   but at this point, there seems to be some other problem I cannot resolve.

old IP 192.168.1.9
new IP 192.168.1.5

Sure would like some help.  Thank you in advance.

---

### Post by migs73 on 2012-01-17
Have you tried setting the IP address back to the original?
I had a similar problem with my wireless Brother printer and had to manually give it a fixed IP address to stop it getting assigned a different one sometimes when it was switched on.

---

### Post by jfbooth on 2012-01-17
> **migs73 said:**
> Have you tried setting the IP address back to the original?
I had a similar problem with my wireless Brother printer and had to manually give it a fixed IP address to stop it getting assigned a different one sometimes when it was switched on.

Thank you for the reply.  I actually do not know how to set the IP.  I just know how to find out what it is ... and right now, it is 192.168.1.5,

You are right though .. once I get it working, I need to do whatever I need to do so this doesn't happen again.

Since posting, now the scanner doesn't work.  I have since uninstalled all pertinent packages .. even tcsh and started over from scratch.  I have used the very popular 'tutorial' here ... been through that about a dozen times now .. I have it memorized ... and the step by step procedures from the Brother website.  No go .. no love.  I even connected USB (since I could never get it to be 'network'' .. and nothing works either way .. USB or NETWORKED.  I'm completely stumped.  It has worked great in the past.  Wondering if it has something to do with Xubuntu 11.10.  Dunno.  Can't find much help.  Thank you .. for your attention.

---

### Post by kurt18947 on 2012-01-17
> **jfbooth said:**
> Thank you for the reply.  I actually do not know how to set the IP.  I just know how to find out what it is ... and right now, it is 192.168.1.5,
<snip>


What I have done with pretty good success is to use "socket".  In the device URi window (in printer properties) I put the following:  "socket://xxx.xxx.xxx.xxx:9100"  where xxx=I.P. address.  For this to work reliably you do need to set the I.P. address to be static, DHCP won't work. There should be a way to set network address to static on the printer's control panel.

---

### Post by jfbooth on 2012-01-17
> **kurt18947 said:**
> What I have done with pretty good success is to use "socket".  In the device URi window (in printer properties) I put the following:  "socket://xxx.xxx.xxx.xxx:9100"  where xxx=I.P. address.  For this to work reliably you do need to set the I.P. address to be static, DHCP won't work. There should be a way to set network address to static on the printer's control panel.

Thank you so much, Kurt.  I need ANY kind of help here.  To be honest, I have tried that .. possibly 1/2 dozen times .. but using the KNOWN IP address 192.168.1.5 which I admit .. is dynamic.  I will try it again AFTER I set it to static .. as you have described .. assuming I can figure out how.

I have tried practically everything (except the right thing . obviously).  It will NOT change from local USB to networked.  Keeps saying can't find driver files.  I have gone through everything I can find .. the driver is installed, cups is installed, tcsh is installed.

Thanks again .. I will try to set it to STATIC 192.168.1.5

Edit:  PRINTER control panel!!  I thought you meant printer 'control panel' in Xubuntu!!  God, I'm losing it.  I am fairly certain I now have it static at 192.168.1.5.  The Network guide (printed) went on to talk about MAC address etc .. but I left all that alone.  [COLOR="Red"]**Unfortunately, none of it seems to have made any difference.**[/COLOR]

---

### Post by kurt18947 on 2012-01-18
I'm sorry to hear your machine is still being recalcitrant.  When I install the MFC-6490CW it installs with usb:/................. in the device URI window even when there's no USB cable installed.  For me changing the device URI enabled network printing.  There are instructions on Brother's Linux drivers page that talk about editing the file etc/printcap.  I've never had to do this but it might it be worth a try?
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html#printcap2](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html#printcap2).  Step 5
[B]
For Network Connection[/B]
replace ":lp" line to the following 2 lines:

rm=(ip address of your printer)\
:rp=lp\

[Example]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html#printcap2")

Here is my /etc/printcap which was generated automatically.  Do you have something similar?
```
# This file was automatically generated by cupsd(8) from the
# /etc/cups/printers.conf file.  All changes to this file
# will be lost.
MFC6490CW|MFC6490CW:rm=Thinkpad-r61:rp=MFC6490CW:
7820N|7820N:rm=Thinkpad-r61:rp=7820N:
```

I did use Brother's email support for a scanner issue in 12.04.  I got a response back within 24 hours so trying the email link on their support page might be worthwhile.

---

### Post by jfbooth on 2012-01-18
> **kurt18947 said:**
> I'm sorry to hear your machine is still being recalcitrant.

Me too, .. driving me nutz.  I sure appreciate your help though.

> When I install the MFC-6490CW it installs with usb:/................. in the device URI window even when there's no USB cable installed.

So does mine.  If I try to change it to any of the NETWORKING selections, it ends up with **Unable to get list of printer drivers:**.

> For me changing the device URI enabled network printing.

Changing the device URI results in **Unable to get list of printer drivers:**.  I have GOOGLED that phrase with a CUPS qualifier .. but don't find anything on it.

> There are instructions on Brother's Linux drivers page that talk about editing the file etc/printcap.  I've never had to do this but it might it be worth a try?

I will try just about anything.  I have that file.  It (now) says:

```
# This file was automatically generated by cupsd(8) from the
# /etc/cups/printers.conf file.  All changes to this file
# will be lost.
```

That's all it says .. BUT, know that I have completely removed all Brother packages (in order to start over AGAIN).  When I get it all 'back up', I will check this file for content.  Thank you for this.

> [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html#printcap2](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html#printcap2).  Step 5
[B]
For Network Connection[/B]
replace ":lp" line to the following 2 lines:

rm=(ip address of your printer)\
:rp=lp\

[Example]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html#printcap2")

Here is my /etc/printcap which was generated automatically.  Do you have something similar?
```
# This file was automatically generated by cupsd(8) from the
# /etc/cups/printers.conf file.  All changes to this file
# will be lost.
MFC6490CW|MFC6490CW:rm=Thinkpad-r61:rp=MFC6490CW:
7820N|7820N:rm=Thinkpad-r61:rp=7820N:
```

I did use Brother's email support for a scanner issue in 12.04.  I got a response back within 24 hours so trying the email link on their support page might be worthwhile.

I will get everything reinstalled and take your tips into account.  Thanks again for the help.

EDIT: I CLOSELY followed the installation from the Brother Website.  Made sure I did all the pwewekwizits.  As usual, it installed USB:

[B]Description:	MFC7440N
Location:	
Driver:	Brother MFC7440N for CUPS (grayscale, 2-sided printing)
Connection:	usb://Brother/MFC-7440N?serial=000A8N117986
Defaults:	job-sheets=none, none media=iso_a4_210x297mm sides=one-sided[/B]

I cannot even set the location.  Modify CURRENT connection and fill in LOCATION with Back Room results in **Modify Printer MFC7440N Error Unable to get list of printer drivers:**.

Same thing if I try to modify to a NETWORKED printer.

One thing though, .. /etc/printcap looked like:

[B]# This file was automatically generated by cupsd(8) from the
# /etc/cups/printers.conf file.  All changes to this file
# will be lost.
MFC7440N:\
        :mx=0:\
        :sd=/var/spool/lpd/MFC7440N:\
        :sh:\
        :lp=/dev/usb/lp0:\
        :if=/usr/local/Brother/lpd/filterMFC7440N:[/B]

so I edited it to this:

[B]# This file was automatically generated by cupsd(8) from the
# /etc/cups/printers.conf file.  All changes to this file
# will be lost.
MFC7440N:\
        :mx=0:\
        :sd=/var/spool/lpd/MFC7440N:\
        :sh:\
        :rm=192.168.1.5\
	:rp=#lp\
        :if=/usr/local/Brother/lpd/filterMFC7440N:[/B]

per your suggestion.  No love .. same thing with the freekin Unable to get list of printer drivers: .  Maybe I have to reboot .. will try that but I have my doubts.

---

### Post by migs73 on 2012-01-18
When you say it used to work do you mean in 11.04 or in 11.10?
Assuming you meant 11.04, was it 64bit (I am again assuming your 11.10 install is 64bit as you use the --force-all)or 32bit? I know that the forcing of the architecture has caused many problems for others.

---

### Post by jfbooth on 2012-01-18
Rebooting did not help matters, . at all.

> **migs73 said:**
> When you say it used to work do you mean in 11.04 or in 11.10?
Assuming you meant 11.04, was it 64bit (I am again assuming your 11.10 install is 64bit as you use the --force-all)or 32bit? I know that the forcing of the architecture has caused many problems for others.

Truthful answer.. it worked perfectly with 11.04 Xubuntu.  I did an in place upgrade to 11.10 .. and I do not THINK I even tested with 11.10 so cannot say for certain it ever worked in 11.10.  It might have .. can't remember.

Both 11.04 and 11.10 was/is 32-bit.  I used the commands recommended by Brother.

> Step 4. Install the driver
    4-1. Turn on the printer and connect the usb, network or parallel cable.
    4-2. Go to the directory where the driver is.
    4-3. Install LPR driver. The install process may take some time. Please wait until it is complete.

        Command (for dpkg)  :  dpkg  -i  --force-all  (lpr-drivername)

> 4-4. Install cupswrapper driver.The install process may take some time. Please wait until it is complete.

    Command (for dpkg)  :  dpkg  -i  --force-all  (cupswrapper-drivername)

Should I install these with different commands?  If so .. what would be the suggested command?

Thank you too for the help.

---

### Post by migs73 on 2012-01-18
type;
```
uname -a
```

into a terminal and post the output here. That'll let us know for sure if it is 64 or 32 Bit Xubuntu you have.

---

### Post by migs73 on 2012-01-18
> Should I install these with different commands? If so .. what would be the suggested command?

I am sure the last time I installed the drivers, I just downloaded them to my desktop, double clicked on them and let the Software centre take care of the install.

---

### Post by jfbooth on 2012-01-18
> type;
Code:

uname -a

into a terminal and post the output here. That'll let us know for sure if it is 64 or 32 Bit Xubuntu you have.


```
jb@Compaq:~$ uname -a
Linux Compaq 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
```

---

### Post by migs73 on 2012-01-18
> **jfbooth said:**
> jb@Compaq:~$ uname -a
Linux Compaq 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux

Well 32bit it is then, I am beginning to run out of ideas now. The only other thing I've seen that could be an issue is that you did an upgrade rather than a re-install. I know this can be problematic, but would require a fresh install to clear up (if it was the problem). Very much a last resort, so I would hang in there and see if any others have any ideas.

Sorry I can't be of more help.


Mike   :confused:

---

### Post by jfbooth on 2012-01-18
> **migs73 said:**
> I am sure the last time I installed the drivers, I just downloaded them to my desktop, double clicked on them and let the Software centre take care of the install.

I have been using this printer/scanner going back to Xubuntu 8 or 9.  Never had this kind of problem until 11.10.  It was never as easy for me as you claim but ... I have got it working SEVERAL times .. and am pretty familiar with what it took in the past .. but nothing is now working the way it has in the past.

I would be amazed if Brother support would help me .. printer is a couple of years out of warranty.

---

### Post by jfbooth on 2012-01-18
> **migs73 said:**
> Well 32bit it is then, I am beginning to run out of ideas now. The only other thing I've seen that could be an issue is that you did an upgrade rather than a re-install. I know this can be problematic, but would require a fresh install to clear up (if it was the problem). Very much a last resort, so I would hang in there and see if any others have any ideas.

Sorry I can't be of more help.

You are quite a gentleman and I really appreciate your effort and time.  Hopefully someone else will help me out.  Thank you again.

EDIT:  FWIW, I just called Brother.  "Do you support Brother printers that are out of warranty?"  "We sure do, .. how can I help you?"  I about dropped the phone.  Then I told her and when I mentioned LINUX, she practically hung up on me. Very nice young lady, but apologized that support is not available for Linux .. of any kind .. not phone or email.  Sad, ain't it?  She told me to contact 'Linux support'.

---

### Post by kurt18947 on 2012-01-18
Phone support is not available.  Email support **IS** available.  Here are a couple email addresses to try:

[EMAIL="faxsupp@brother.com"]faxsupp@brother.com[/EMAIL]  This was the return address on the email I received.

This was at the end of the email.
Fax/MFC Software Support Customer Service Brother International Corporation, USA [swsup@brother.com]("https://lavabit.com/apps/webmail/src/compose.php?send_to=swsup%40brother.com") 

I'm a little skeptical about the second address.  I thought Linux support was based 
in Japan, not the U.S. I didn't know you were using 32 bit Xubuntu.  Usually 32 bit is easier to use, it doesn't require the --force-all switch for starters.  When I installed on 32 bit I just used Gdebi, no command line required.

---

### Post by jfbooth on 2012-01-18
> **kurt18947 said:**
> Phone support is not available.  Email support **IS** available.

Hmmm .. I specifically asked her about email support.  She said neither was available for Linux.


> Here are a couple email addresses to try:

[EMAIL="faxsupp@brother.com"]faxsupp@brother.com[/EMAIL]  This was the return address on the email I received.

This was at the end of the email.
Fax/MFC Software Support Customer Service Brother International Corporation, USA [swsup@brother.com]("https://lavabit.com/apps/webmail/src/compose.php?send_to=swsup%40brother.com") 

I'm a little skeptical about the second address.  I thought Linux support was based 
in Japan, not the U.S.

I will look into this.  Thank you very much.

> I didn't know you were using 32 bit Xubuntu.  Usually 32 bit is easier to use, it doesn't require the --force-all switch for starters.  When I installed on 32 bit I just used Gdebi, no command line required.

Interesting.  --force-all is called for in that tutorial here and at the Brother website.  So . never heard of Gdebi .. so what command should I try?  Would this be correct?:

dpkg -i (lpr-drivername)

---

### Post by kurt18947 on 2012-01-20
> **jfbooth said:**
> Hmmm .. I specifically asked her about email support.  She said neither was available for Linux.




I will look into this.  Thank you very much.



Interesting.  --force-all is called for in that tutorial here and at the Brother website.  So . never heard of Gdebi .. so what command should I try?  Would this be correct?:

dpkg -i (lpr-drivername)

I'm a CLI neophyte.  I'd think sudo dpkg -i should work but I won't guarantee it.  Gdebi is a .deb package installer.  It's found in the repositories.  The Ubuntu software center should work, gdebi seems a little faster.

---

### Post by jfbooth on 2012-01-20
> **kurt18947 said:**
> I'm a CLI neophyte.  I'd think sudo dpkg -i should work but I won't guarantee it.  Gdebi is a .deb package installer.  It's found in the repositories.  The Ubuntu software center should work, gdebi seems a little faster.

Yeah .. I tried Software Center for a few things .. very slow on this old Windows ME machine.  CLI is 'fast enough' .. and though a neophyte (actually dummy) myself, am inclined to stick to that.  I will give dpkg -i a try .. but I really doubt it will make any difference to the ultimate problem.

Thanks again for your replies.

---

