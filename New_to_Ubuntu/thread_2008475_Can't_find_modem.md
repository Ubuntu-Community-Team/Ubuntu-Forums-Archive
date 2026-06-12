---
title: "Can't find modem"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by peterjm on 2012-06-22
I'm trying to get Ubuntu onto the internet. I have dial-up. Computer is an IBM laptop with 2000 operating system.
I carefully followed the instructions [both in the imbedded help menu and the book] and got the reply: No Modem Detected. I tried to determine what my modem is [again following the instructions] and got all kinds of resistance. I have the things on my desktop [I got that far] but it can't find them? 
The book warned that Ubuntu support for dial-up is sketchy. Dial-up is $10 or $12 /month. The faster systems are more than twice that and I am cheap!
So the question is: How do I get Ubuntu onto the internet?

---

### Post by jmore9 on 2012-06-22
What kind of modem ?  win modem or serial ?  need to know that first.  If it is a serial modem may not need any drivers at all.

---

### Post by lkraemer on 2012-06-22
peterjm,
Sometimes being cheap isn't the most cost effective way to go.
For instance, a Serial modem can run as high as $80.00, and after you spend 3-5 days trying to make it work,
you end up with a screen update time of around two minutes when you are surfing.  Updates will most likely
take all night, and you're likely to get disconnected several times before a complete update gets done.
But Dialup is semi-functional  if you have the time and patience.

If you have a Win Modem, I wouldn't waste my time trying to make it work. The driver will likely cost you
just as much as a Serial Modem.

Another option is to purchase a used Serial Modem from Ebay and try that.

There are several good tutorials on this forum.  If you search for SM56 you'll likely run across one I conjured up.

[http://ubuntuforums.org/showthread.php?t=1100310&highlight=SM56](http://ubuntuforums.org/showthread.php?t=1100310&highlight=SM56)

Good Luck.
 
lk

---

### Post by peterjm on 2012-06-24
I don't know what kind of modem it is. It is in an IBM think pad about 10 years old.
I daily visit sites such as  Strategy Page but lately it has been giving me problems such as hanging up my computer. The Atlantic website advises me to update my browser. So I went to the labrary and got an update [Windows Explorer 7} on my thumbdrive. But when I tried to install it, it wouldn't [complaint that encryption device controller or something was missing].
So I found a book on Ubuntu at the libary. What could be better than a new, modern?, and FREE new operating system. I managed to install it. But now it can't connect to the internet. Why is this so difficult? Ubuntu is supposed to be easy to use and all this advice is to buy a serial modem when I already have one on this machine.
You guys are supposed to be geniuses yet you can't solve this simple problem of designing something to connect to the internet.
~Peter

---

### Post by wildmanne39 on 2012-06-24
Hi, we are just people like you that volunteer to help, and I work with wireless issues but I do not know anything about dial up.

---

### Post by peterjm on 2012-06-24
Dial-up is used by maybe 10% of computer users. Maybe not so much in the States but perhaps in less sophisticated regions. It is the duty of Ubuntu to make it available to all.
~Peter

---

### Post by wildmanne39 on 2012-06-24
Hi, here is a link that I found that should help.
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer/](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer/)
Thanks

---

### Post by DingusFett on 2012-06-24
On the cost, I initially changed to ADSL simply because by the time you factor in the cost of calls to make the dialup connection, and the time that you are holding up the line so the phone cannot be used, you're not really saving much and ending up with a terrible connection that will frequently drop out and have no speed (most ADSL plans that impliment shaping still shape you at 64kb, far faster than you could hope to achieve over a dialup connection).

---

### Post by Cheesemill on 2012-06-24
Can you open a terminal and post the result of the command
```
lspci
```
This should let us know what sort of modem you have.

---

### Post by lkraemer on 2012-06-25
peterjm,
What you are failing to understand is those guys are geniuses!  They have
provided you a FREE OS, that works with Dialup, Wired, Wifi, at ZERO
Cost to you.  You do have to be able to read and type on a keyboard to get
your specific hardware functional.  And, to top it off those same guys are
willing to help you on this forum.  Yet you seem to think it's their
responsibility to get your computer's modem functional.  Well, they will do that too!

You need to go to the [http://www.linmodems.org/](http://www.linmodems.org/) site, then download
the ScanModem.tool and execute that script to get the information
on the modem. Then subscribe to the Linmodems discussion list.
Then send Marvin and those fine folks an email (in plain text..ONLY) to
the discussion list. They will analyze your results and get back to you
on what to do to get the correct drivers to get the Modem working.
Don't be surprised if they request payment for their Driver. 

You can also search the archives posted there for your Modem and read
those messages about how others have tried to get theirs working.
Use EDIT then FIND for your Modem and search each month for responses
to keep from pouring over each months' ton of postings.

Once that is done you're 80% done.........or you can use an External USR
Modem with your serial port or USB to serial Adapter and forget the extra
multiple days' hassel of the Winmodem..... 

Now you are at the following place in the previously noted Guide:
> 
Once that decision is made, you will need to set up the pap-secrets and/or chap-secrets
file by running the following in a Terminal Window:

You are going to need your ISP Login, ISP Password, and the ISP Phone Number.  Some Dialup ISP's
don't play well with Linux.  I use Copper.Net.  They are $99.00 per year for their service, and 
pretty well cover the USA.  It might be worth your time to search the forum for other ISP's that
work well with Linux.  Those postings are somewhere on this forum.

So, Input your ISP information...................with:
```

sudo pppconfig

```
Post if you have questions.

So, I'd say you're off to the races with your quest!

Keep us informed of your progress.


lk

---

### Post by peterjm on 2012-06-26
My modem is:
Agere Systems AC97
attached to:
COM 3
Then there's this:
PCI\VEN_8086&DEV_2486&SUBSYS_05/A1014&REV_02
 
~Peter

---

### Post by mbuell on 2012-06-28
Peter - I apologize for not having the time to find links to some of the stuff I have found. Not sure if this will be helpful - but:

1. The ubuntu developers agree with you that modems should work out of the box. However, there are a large number of problems with this that have not been overcome. a) Modems have proprietary drivers, few have open-source drivers. b) Modems are largely dead for most users and obsolete. This reduces the urgency of finding fixes. 
2. My Thinkpad uses a conexant chip for the modem. If it does, see #3. While there are supposedly drivers for this in earlier versions, nothing is available yet for 12.04, and they seem to be version specific. Earlier versions of Ubuntu have "fixes" on one of the links you were given in an earlier response. Also, I think some of the files necessary for making the conexant drivers may no longer be available. See the thread linked in #3. 
3. Scanmodem may not detect your modem. There was a helpful thread using pccardctl to assist in the detection. I will post a link later when I can find the link. See also this thread:  [http://ubuntuforums.org/showthread.php?t=1903439&highlight=laptop+modem]("http://ubuntuforums.org/showthread.php?t=1903439&highlight=laptop+modem")

4. Older external serial modems are reported on various threads to work much more easily. However, your laptop probably does not have a serial port, and you would then need a USB to serial adapter. Such an adapter may need a driver itself, and thus could be another problem to solve to get functionality. I do not know - but may have to find out soon. Current USB modems are available from Trendnet and USR Robotics that claim compatibility with linux. The Trendnet is 25-30 US. The USR is 45-50 US. 

5. Some forum dwellers have posted that Intel modem chips work well - but I have a pcmcia Zonet modem (Intel chip!) that is giving me headaches trying to make it functional. 

IMO, Ubuntu has excellent hardware support, except for modems. While I understand your feeling that there "should" be better support - there is only a limited amount they can do. Of course - if we all paid $100 for our copy, they would have more money to spend on problems, wouldn't they! :D

---

### Post by mbuell on 2012-06-28
Peter - here are some links where I found useful information.

[https://help.ubuntu.com/community/DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto")
Ubuntu's modem how-to. Helpful, relies on Scanmodem to get you started. My Thinkpad T60 uses a Conexant chipset for the modem - and Scanmodem does not detect Conexant chips. If this is your case, Scanmodem's helpfulness may be limited. There used to be a commercial driver for Conexant call Linuxant - but it costs $. And may not be ready for 12.04. Dell had drivers available for the Conexant chips, and various users had devised methods to make those drivers run on Ubuntu - but not on 12.04 yet, and Dell has as of this writing pulled that file. It is not available for download today. 

[http://linmodems.technion.ac.il/]("http://linmodems.technion.ac.il/")Lots of stuff here, including Scanmodem. Getting long in the tooth, because for most people modems are obsolete. 

Because of the difficulty involved in getting the Conexant chip modem operational - I bought a pcmcia modem, a Zonet 56K with Intel chipset. This also gave me difficulty - but towards the end of this thread
[http://forums.fedoraforum.org/showthread.php?t=104377]("http://forums.fedoraforum.org/showthread.php?t=104377") they discuss pccardctl - a very handy utility that allowed me to get things working again. They also have some operational tactical tips that helped. 

And, this page was linked by another Ubuntu forum dweller as useful in understanding how to get the modem functioning with wvdial, once you get it recognized. [https://wiki.archlinux.org/index.php/Wvdial]("https://wiki.archlinux.org/index.php/Wvdial")

---

