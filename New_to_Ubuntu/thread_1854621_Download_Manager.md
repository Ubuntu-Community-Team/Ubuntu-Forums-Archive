---
title: "Download Manager"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by amirfoad on 2011-10-04
Hi.
I've searched a lot for a good and fast download manager and download accelerator for Ubuntu, but nothing found!
A program with options such as resume, speed limit, separating download parts (for acceleration), auto pop-up by clicking download link and so...!
Something like IDM (Internet Download Manager) in Windows!

Do u have any idea?

---

### Post by ajgreeny on 2011-10-04
If you really feel you need something try the firefox add-on **downthemall**.  I don't think it is an accelerator, (not sure there are any for linux, nor even how effective they are in Windows), nor have I ever tried it or seen a reason to, but it is available easily enough.

---

### Post by fantab on 2011-10-05
> **amirfoad said:**
> Hi.
I've searched a lot for a good and fast download manager and download accelerator for Ubuntu, but nothing found!
A program with options such as resume, speed limit, separating download parts (for acceleration), auto pop-up by clicking download link and so...!
Something like IDM (Internet Download Manager) in Windows!

Do u have any idea?

I use [**jdownloader**]("http://jdownloader.org/download/index"), its is a bit bloated by does most of the things I need and might just cater to your needs.

There is also **uGet** which is available from 'Software Center' you can try this as well...

---

### Post by amirfoad on 2011-10-05
Yes, I have this add-on in my Firefox and use it. Not bad but no acceleration in!
[In some servers which they modify speed limit for downloading, it's very effective and fast!]

---

### Post by amirfoad on 2011-10-05
> **fantab said:**
> I use [**jdownloader**]("http://jdownloader.org/download/index"), its is a bit bloated by does most of the things I need and might just cater to your needs.

There is also **uGet** which is available from 'Software Center' you can try this as well...

OK, I'll try them.
Thank you.

---

### Post by dniMretsaM on 2011-10-05
> **ajgreeny said:**
> If you really feel you need something try the firefox add-on **downthemall**.  I don't think it is an accelerator, (not sure there are any for linux, nor even how effective they are in Windows), nor have I ever tried it or seen a reason to, but it is available easily enough.

It claims to be an accelerator:
[QUOTE=DownThemAll]The first and only download manager/accelerator built inside Firefox![/QUOTE]

---

### Post by ubuntu27 on 2011-10-05
I use [uGet]("http://urlget.sourceforge.net/") (Available in Ubuntu repository), and [FlashGot]("http://flashgot.net/") Add-on for Firefox.

---

### Post by Lisiano on 2011-10-05
I use a CLI program called **axel**, very neat, let's me specify how many connections to use. Combined with DownThemAll (You can set it there) or with Chromes extension Download Assistant, you can easily download files. I usually find that using 8 connections is enough for any server but you can easily use 256 if you wished to, be careful, the server admins might not like it though.
It also resumes downloads by default, if the server let's it, if the server is evil and doesn't let you use multiple connections, axel drops into a single connection mode AFAIK.

---

### Post by amirfoad on 2011-10-05
Yes, Thank you...
I've installed AXEL before and tested it and it was working good. It's a nice program!
In this thread, I just wanna to know if there are some other programs which I don't know them!

---

### Post by ubupirate on 2011-10-05
There is Gwget too, which is what I use to throttle my download speeds when doing direct HTTP downloads.

---

### Post by Krytarik on 2011-10-05
> **amirfoad said:**
> Yes, I have this add-on in my Firefox and use it. Not bad but no acceleration in!
Really? Guess you need to be even more specific then, as DownThemAll really does this ;-) :
> **amirfoad said:**
> separating download parts (for acceleration)

---

### Post by swamyuefa on 2012-05-23
> **amirfoad said:**
> Yes, Thank you...
I've installed AXEL before and tested it and it was working good. It's a nice program!
In this thread, I just wanna to know if there are some other programs which I don't know them!
i have installed axel , but how to use it for downloading, help me:confused:

---

### Post by swamyuefa on 2012-05-23
> **Lisiano said:**
> I use a CLI program called **axel**, very neat, let's me specify how many connections to use. Combined with DownThemAll (You can set it there) or with Chromes extension Download Assistant, you can easily download files. I usually find that using 8 connections is enough for any server but you can easily use 256 if you wished to, be careful, the server admins might not like it though.
It also resumes downloads by default, if the server let's it, if the server is evil and doesn't let you use multiple connections, axel drops into a single connection mode AFAIK.
hi Lisiano,
i have installed axel via ubuntu software centre, but how to use it. help me guys, as i am new to ubuntu.:confused:

---

### Post by mustafi05 on 2012-05-23
you can use " prozgui" its a download accelerator with a downloadhelper tinge

---

### Post by jtarin on 2012-05-23
> **swamyuefa said:**
> hi Lisiano,
i have installed axel via ubuntu software centre, but how to use it. help me guys, as i am new to ubuntu.:confused:

[http://www.linuxjournal.com/content/speed-your-downloads-axel](http://www.linuxjournal.com/content/speed-your-downloads-axel)

Look for the front-end gui......"axel-kapt". You can fine it in Synaptic or the Software Center.

I will say though...jdownloader is the best. While not an accelerator, I've never lost a download with it.

---

### Post by thomsebastin on 2012-05-23
None mentioned fatrat:) so i'll take that risk..try it buddy.

---

### Post by thomsebastin on 2012-05-23
Oh yeah,downloading flashgot for firefox would b a good idea as you can select from different options during download time frm firefox.

---

### Post by swamyuefa on 2012-05-24
> **jtarin said:**
> [http://www.linuxjournal.com/content/speed-your-downloads-axel](http://www.linuxjournal.com/content/speed-your-downloads-axel)

Look for the front-end gui......"axel-kapt". You can fine it in Synaptic or the Software Center.

I will say though...jdownloader is the best. While not an accelerator, I've never lost a download with it.

hi jtarin,
thanks buddy for your reply. i am willing to try axel.

---

### Post by ubuntu27 on 2012-05-24
> **jtarin said:**
> [...]

I will say though...jdownloader is the best. While not an accelerator, I've never lost a download with it.

I second that motion. [Jdownloader ]("http://www.jdownloader.org/")in my opinion is the best GUI based download manager available for Linux. I recently discovered 2 months ago, and now I am a believer!


They have PPA for Ubuntu too.

[http://www.jdownloader.org/](http://www.jdownloader.org/)

[https://launchpad.net/~jd-team/+archive/jdownloader](https://launchpad.net/~jd-team/+archive/jdownloader)

---

### Post by FulciLives on 2012-09-14
Could someone explain how to use axel-kapt (that's the GUI for Axel).

I mean it seems simple enough but even though I clicked the VERBOSE option all that happened was a terminal window opened and then nothing. Just a flashing (well I think it was flashing) cursor.

The file did download and it was fast (but a huge file so it took a while) but there was no indication of what was happening. I could tell my internet was being used to the max due to an applet I use that shows internet speeds but that's it. It was like an "invisible" process but I don't like that ... I want to see some sort of progress etc.

Does Axel even do that or what?

---

### Post by jtarin on 2012-09-14
> **FulciLives said:**
> Could someone explain how to use axel-kapt (that's the GUI for Axel).

I mean it seems simple enough but even though I clicked the VERBOSE option all that happened was a terminal window opened and then nothing. Just a flashing (well I think it was flashing) cursor.

The file did download and it was fast (but a huge file so it took a while) but there was no indication of what was happening. I could tell my internet was being used to the max due to an applet I use that shows internet speeds but that's it. It was like an "invisible" process but I don't like that ... I want to see some sort of progress etc.

Does Axel even do that or what?[A little direction on using.]("http://linuxers.org/article/axel-console-based-download-accelerator-linux")

---

### Post by cyb3r_sn4k3 on 2012-09-14
+1 for firefox with downthemall

---

### Post by FulciLives on 2012-09-15
> **jtarin said:**
> [A little direction on using.]("http://linuxers.org/article/axel-console-based-download-accelerator-linux")
Thank you for that info but in the end I got the uGet plug-in for Axel to work and so I'm now getting accelerated downloads that way. The uGet GUI is nice (not perfect but more than good enough) so I'm a happy camper.

---

