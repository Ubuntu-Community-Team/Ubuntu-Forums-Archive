---
title: "Do you have an older Lexmark or Dell printer that won't work?"
date: 2014-08-22
forum: New to Ubuntu
---

### Post by dave131 on 2014-08-22
First off, I'm a newbie, so no promises can be made here!  I just helped a user get their printer working - a Lexmark 2420 - in 12.xx, and I was able to install the same driver in 14.04 - I just don't have a printer like that to test with.  Please note - this driver is a 1 does all kind of thing - it works for many of Lexmarks' printers and should work with several Dell printers as well.

I know that at least in the past a lot of Dell printers were rebranded Lexmark printers, so this *might* apply to you as well.

I also want to say NONE of this is original by me - this is ALL someone else's work.

Step 1:  if you are running 64-bit Ubuntu, you need to install the i386 support via:

open a terminal window viar ctrl/alt/t

type:

sudo apt-get install multiarch-support <press enter>

========

Step 2:  download the driver file via from [this link]("http://www.mediafire.com/download/w545ftercecb1vu/New-lexmark-08z-series-driver-1.0-1.i386.deb.deb").  This should download the file to your Downloads folder.

========

Step 3:  user ctrl/alt/t to open a terminal window, then type:

cd Downloads <press enter>

sudo dpkg -i New-lexmark-08z-series-driver-1.0-1.i386.deb.deb <press enter>

 =======

This should run and say it installed the driver.

Connect your printer via USB and go through the add printer menu.

If your printer also has wireless and you want to use it wirelessly, you should first assign the printer a "fixed" IP address, then go through the Printers menu again, Add, and select wireless, then select your printer.

PLEASE post back if you try this with the result and the make/model of your printer.

---

### Post by adambond on 2014-08-31
I have a lexmark 9575 
I am attempting this, but have hit a snag on step 3.  I type 'cd downloads' into terminal, and hit enter and simply get this  [COLOR=#0000cd]"bash: cd: downloads: No such file or directory"[/COLOR]
I proceed anyways and enter [COLOR=#0000cd]"sudo dpkg -i New-lexmark-08z-series-driver-1.0-1.i386.deb.deb"[/COLOR]

After entering my password, it returns this [COLOR=#0000cd]"dpkg: error processing New-lexmark-08z-series-driver-1.0-1.i386.deb.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 New-lexmark-08z-series-driver-1.0-1.i386.deb.deb"[/COLOR]

---

### Post by marco-parillo on 2014-08-31
I would make sure that you typed the command as Dave131 specified: cd Downloads
Note that most file systems you will mount in Linux are case-sensitive.
Since this is the New to Ubuntu forum, maybe we should simply say file and directory names are case-sensitive and leave it at that.

---

### Post by adambond on 2014-08-31
Well said sir, I should have known that. Thank you, I will try.

---

### Post by dave131 on 2014-09-01
As Marco-Parillo said, it is case sensitive, so you do need to be sure there is a capital "D", not a lower case "d".  You should be able to just copy and paste the lines you need to run - no need to re-type them.

Please let us know how this goes so we can know if this driver supports your printer.

---

### Post by Vladlenin5000 on 2014-09-02
Please note the instructions telling you to go to the Downloads folder is only valid if your Ubuntu is in standard English. In any other languages the default folders have their names changed to the system language. If so, please replace Download with whatever the default faolder for downloads you have.

---

### Post by marco-parillo on 2014-09-02
> [COLOR=#000000]Please note the instructions telling you to go to the Downloads folder is only valid if your Ubuntu is in standard English.

Not only standard English, it even works with American English ;-)

[/COLOR]mparillo@mparillo-work-KubuntuBeta1RC1:~$ locale
LANG=en_US.UTF-8
LANGUAGE=en_US


[COLOR=#000000]
[/COLOR]

---

### Post by adambond on 2014-09-06
Ok. Going to install the Lexmark Deb file. And I get this. 

[IMG]http://i36.photobucket.com/albums/e44/327amc/Screenshotfrom2014-09-06131445_zpsae21133e.png[/IMG]

---

### Post by dave131 on 2014-09-06
I never ran mine via the software center, so I don't know anything about that error message.

EDIT:  I just tried this again.  Did you click on the .deb file with file manager, or did you use the dpkg statement shown above?  I used dpkg again - it didn't open the software center and it installed in terminal without any error messages.  Try it again using terminal and copy/paste the sudo dpkg statement as shown in my original post.

---

### Post by Enigma12 on 2014-09-07
Since I was having an ongoing problem (detailed below) with my Lexmark Optra E321, I decided to copy and paste, then print the entire first post before I did anything else. Downloaded the file, deleted the printer, disconnected the USB cable, ran the Step 3 commands given in LXTerminal, then reinstalled the printer. As a test, I printed a test page from the final printer installation window. It came out perfect. 

As a further test, I copied the entire Readme-drivers.txt into Abiword and got that file down to 6 pages. Printed pages 1, 3, and 5 perfectly. To save paper, I printed page 2 on the back side of page 1, which came out perfect. When I printer page 4 on the back of page 3, the ongoing problem that I have had resurfaced. Below is an example of what has happened fairly often with this printer working under Lubuntu 14.04.1.

[ATTACH=CONFIG]256234[/ATTACH]

This image is one fairly extreme example only--NOT what I got today, which was ***slightly less*** jumbled. If I only get 1 page out of 6 to give me this garbage, that will be an improvement, but I still have a problem getting things to just print as they should. 

I've NEVER before had this kind of problem with any printer or any Windows version. And I fully accept that I have much to learn to get competent with Linux, which will take time, study, and some experimentation, but I've only been using Lubuntu as my first exposure to Linux for a very few months and only have limited time to incease my knowledge each day. So, if anyone can offer a detailed solution to this paper wasting problem, PLEASE let me know. Thanks in advance.

---

### Post by dave131 on 2014-09-07
Hard to tell - could still be the driver.  Since Lexmark seems to have stopped Linux driver support it is questionable as to whether or not it will work.

---

### Post by adambond on 2014-09-08
I tried the code in terminal. I get this error.   And the way the OP reads, I assume all that terminal input was for 64bit systems anyways. Im 32bit.

---

### Post by dave131 on 2014-09-09
Should work on 32-bit systems fine - it's a 32-bit driver. You just won't need to do the install of the i386 compatibility. The screen image you posted indicates it's not finding the file.  Depending on what version of Ubuntu and what release you are running, it may not have put the downloaded file in Downloads.  If you don't see it in your Downloads folder, check your other folders starting with your home folder.  Where ever you find it, you want to change the cd command to match that folder, then run dpkg.

---

