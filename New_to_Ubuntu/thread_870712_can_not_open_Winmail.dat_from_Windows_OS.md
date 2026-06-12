---
title: "can not open Winmail.dat from Windows OS"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by prifer on 2008-07-26
Hello, I am new to Linux.

In my office, only me using linux. like usual I send and receive emails from others, but I often receive attachemnt Winmail.dat whereas the sender send me the excel attchments so I could not open it. But some attachments with excel format can be oppened. I have tried to rename it by using extension xls so that I can open it using openoffice or abiword, but still can not.
so now I just resend it to my gmail account and I can open the excel/word attachemnt in gmail. anyone can help me?

Thanks
prifer

---

### Post by prifer on 2008-07-26
additional:
this text that the attachments appears
        "TNEF message attachment (winmail.dat)"

---

### Post by Paddy Landau on 2008-07-26
Good ole Windows, ensuring that they are as unportable as possible.

Do you use Thunderbird? If so, install the Lookout extension:
[https://addons.mozilla.org/en-US/thunderbird/addon/4433](https://addons.mozilla.org/en-US/thunderbird/addon/4433)

If not, then let us know what email client you're using.

---

### Post by adieb on 2008-07-26
you can always try to open things that don´t have the right ending by right-clicking them and choosing "open with".

after that, try open-office. but i really wonder, why an excel sheet is called winmail.dat. 

Looking that up in google, it appears to be encrypted or coded by outlook. so  you can take a lookat this site:
[http://tud.at/php/tnef/](http://tud.at/php/tnef/)

good luck

---

### Post by prifer on 2008-07-28
I've installed Thunderbird and LookOut successfully, and what next? I make a trial, resend the messeage with 'winmail.dat' but it still appears and can not be opened:confused:
why dyou mean by client?

---

### Post by prifer on 2008-07-28
Sry, I mean my email client is POP3

---

### Post by hailang on 2008-07-28
Microsoft Outlook Express users have this problem too! It is happen when Microsoft Outlook (without Express) users send mail to you and you do not use Microsoft Outlook program to check mail. Please check what is your email program (Evolution, Thunderbird or something like that) and search for solution on internet. With Thunderbird you can follow above link of Paddy Landau to get plug in.

---

### Post by hyper_ch on 2008-07-28
tell the others to set their email client correctly and not to use tnef anymore.

---

### Post by hailang on 2008-07-28
> **hyper_ch said:**
> tell the others to set their email client correctly and not to use tnef anymore.

You can't!!! I my self try many setting to users' Microsoft Outlook (change message format from Rich Text to HTML to Plain Text) but sometime Microsoft Outlook Express users still have winmail.dat instead of attach files.

---

### Post by hyper_ch on 2008-07-28
[http://kb.mozillazine.org/Winmail.dat_attachments](http://kb.mozillazine.org/Winmail.dat_attachments)

---

### Post by coastdweller on 2008-07-28
Had this same problem, found this. Allows you to view it like an attachment.

[http://www.ipute.com/winmail_opener.exe](http://www.ipute.com/winmail_opener.exe)

It's safe, I'm using it to read some web design notes from a client and no errors (VIrus etc).

---

### Post by hyper_ch on 2008-07-28
and how would you run that from linux?

---

### Post by coastdweller on 2008-07-28
[http://tud.at/php/tnef/](http://tud.at/php/tnef/)

[http://linux-sxs.org/internet_browsing/winmail_dat-linux.html](http://linux-sxs.org/internet_browsing/winmail_dat-linux.html)

---

### Post by Paddy Landau on 2008-07-28
> **prifer said:**
> I've installed Thunderbird and LookOut successfully, and what next? I make a trial, resend the messeage with 'winmail.dat' but it still appears and can not be opened:confused:
As I understand, it's no good resending the email. You need to receive it fresh in Thunderbird with Lookout already installed.

Ask the sender to send the email again.

> **prifer said:**
> why dyou mean by client?
You email client is the program that you use to receive emails. For example Outlook, Outlook Express, Thunderbird, Evolution, ...

---

### Post by Paddy Landau on 2008-07-28
> **hyper_ch said:**
> tell the others to set their email client correctly and not to use tnef anymore.
Most Outlook users wouldn't have the faintest idea of what that means, much less how to change it. MS doesn't make it easy.

BTW, this is from MS's site:

> In all versions of Outlook, you can disable TNEF completely:  
[LIST=1]
[*]On the "Tools" menu, click "Options", and then click the "Mail Format" tab.
[*]In the "Send in this message format" list, click "Plain Text" or "HTML", and then click "OK".
[/LIST]


---

### Post by hyper_ch on 2008-07-28
> **Paddy Landau said:**
> Most Outlook users wouldn't have the faintest idea of what that means, much less how to change it. MS doesn't make it easy.

A simple procmail rule that will auto-reply with instructions could do wonders ;)

---

### Post by prifer on 2008-07-28
I have installed LookOut, and resend the message, but it still appears as winmail.dat.
it is imposible to ask all ppl to deactivate their TNEF, since a lot of ppl and different departments here](*,)

---

### Post by prifer on 2008-07-28
It works!:popcorn:
I am using Winmail.dat reader. simply download it using Wine, then launch.
find the winmail.dat, but cant use 'open' tab, so i saved it with xls extension and reopen the file with xls extension.

thanks guys, i like this forum and wondering if i have enough time to explore ubuntu and know more

---

### Post by barratt_sab on 2008-07-30
For another solution (particularly for evolution users):

install package "ytnef" using synaptic package manager

This package can unpack the winmail.dat files into their constituent parts.

It can be run in a terminal as:

ytnef -f <target directory> <winmail.dat file>

or you can make a short script to run it:

1. open terminal
2. [FONT="Courier New"]cd /usr/local/bin[/FONT]
     (just somewhere to keep the script)
3. [FONT="Courier New"]sudo gedit ytnef.decode[/FONT]
     (or whatever you want to call your script file)
4. type your sudo password, to start gedit and edit the script
5. type in the following script (explanation below):

[FONT="Courier New"]#!/bin/sh
# wrapper script to unpackage winmail.dat attachments 
YTNEF=`which ytnef`
FILE=$1

$YTNEF -f ~/Desktop $FILE[/FONT]

6. explanation:
    first line tells [linux] how to interpret the script
    second line is a descriptive comment
    third line finds where synaptic installed ytnef
      using the "which" command and sets YTNEF to this location
    forth line sets FILE equal to the parameter passed when the script
      is called (see below)
    last line calls the YTNEF command, with -f for "unpack" into
      ~/Desktop (the current users desktop) on the required FILE

7. this is a very simple script, derived from the one shown at:
    [http://linux-sxs.org/internet_browsing/winmail_dat-linux.html]("http://linux-sxs.org/internet_browsing/winmail_dat-linux.html")

8. once you have finished the script, save the changed script and exit gedit

9. now change the script to be executable by typing
[FONT="Courier New"]
sudo chmod +x ytnef.decode[/FONT]

10. now close the terminal

11. find an email with a winmail.dat attachment and save the attachment onto the desktop

12. right click and <open with other application>

13. expand the <use custom command> box

14. in the box, type [FONT="Courier New"]/usr/local/bin/ytnef.decode[/FONT] (or you can browse to find the file, if you prefer)

15. hit open - this should unpack the attachments onto your desktop

now, whenever you get a winmail.dat attachment, you can simply save it to your desktop and double click it.  This will call your script with the winmail.dat file name (and location) as a parameter and the contents will be unpacked onto the desktop.

Note that ytnef will overwrite files, so if the _contents_ of the winmail.dat file are the same as files already on the desktop, the existing files will be replaced with the files unpacked from the winmail.dat file (WITHOUT PROMPTING!)

---

### Post by el02 on 2008-12-22
Thank you!! It solved my problem.

---

