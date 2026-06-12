---
title: "removing unnecessary programs and files..."
date: 2012-10-07
forum: New to Ubuntu
---

### Post by Florio on 2012-10-07
About a year ago I posted on this forum; I had just installed Ubuntu 11.04 on my wife's Acer Aspire One which,  as you may know, is a netbook with not a lot of HD space and limited  memory. Ubuntu managed to fit on there, but as my wife said she would probably never use most of the accessories/applications included in the  install, I thought I'd remove various programs, for example those  for editing videos and burning CDs  (especially since there is no CD drive on the  AAO). Basically she wanted only a media player, access to internet, and an email account.

Well, quite a bit of time has passed since then, and I never actually got around to removing stuff from my wife's netbook. In the meantime she's been using it without problems, and the extra space I was thinking of freeing up has never been an issue. Until today. Now she wants me to install Skype.

I should probably first upgrade to Ubuntu 12.04. But once I've done that, and before I install Skype, what programmes do you think I could safely remove, and how do I remove them?

Some who replied to my original post suggested deleting LibreOffice. There must be heaps of other programs and applications that are probably superfluous, at least as far as my wife is concerned.

I realise now that I could have chosen  to install the 'basic' version of Ubuntu, but seeing as I've already installed the standard version, I have to remove things.

All suggestions welcome!

Florio

---

### Post by jerrrys on 2012-10-07
When you upgrade to 12o4, all programs that you remove now will be reinstalled :(

---

### Post by cottfcfan on 2012-10-07
Before removing programs, why don't you try cleaning your system?
Ubuntu Tweak has a good janitor, & Bleachbit works well.

---

### Post by oldos2er on 2012-10-07
If your main issue is freeing up hard disk space, see [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

I use Synaptic or 'apt-get purge foo' to uninstall unwanted programs; either of these methods will allow you to review the list of packages to be removed, so you can check that nothing vital is about to go down the drain so to speak.

---

### Post by DuckHook on 2012-10-07
You sound like a perfect candidate for Lubuntu, the lightweight variant of the Ubuntu distro. Perfect for notebooks without a lot of disk, low powered processor/video, etc. However, if you wish to just upgrade to Ubuntu 12.04, then you should do so first, and then remove all unwanted programs later. There are all sorts of lightweight alternatives to most of the main programs that come with Ubuntu. Discovering them is part of the fun. Software Center is excellent for doing this because it consolidates descriptions and reviews in one easy-to-use, easy-to-read spot. Then just remove/purge old programs as per oldos2er's instructions and you are good to go.

---

### Post by Mark Phelps on 2012-10-07
Advise against using Computer Janitor.  It's too easy to remove stuff accidentally that other apps depend upon.  

If you're that short on space that you need to remove apps, the suggestion of using a more lightweight distro is the better way to go.

---

### Post by Florio on 2012-10-07
Thanks a lot for all your input, guys.:-) 

I really like the idea of a lighter version of Ubuntu, so Lubuntu sounds like the best move. I wasn't even aware it existed.

I'm just wondering about saving the email that my wife currently has on her netbook. Is this possible, given that (from what I've just read), Lubuntu 12.4 has a completely different email client. What format do email messages have in Ubuntu, and where are they stored?
Forgive the lame questions, but I'm a Windows user and know very little about Linux (it's a wonder I managed to install it on the netbook!):lolflag:

---

### Post by will1982 on 2012-10-07
If you hate lubuntu, try xubuntu. It's not lightweight, but not heavy like normal Ubuntu.
 The medium tasting, I would put it.

---

### Post by DuckHook on 2012-10-07
> What format do email messages have in Ubuntu, and where are they stored?

Ubuntu doesn't store e-mail in any specific format. This is the job of the e-mail client, so your storage format will depend on what your client is. I believe the default client was still *Evolution* in 11.04 but I may be wrong. In any case, it is now *Thunderbird* for 12.04 and they use two different formats. I had to change from *Evolution* to *Thunderbird* when I upgraded and it is, unfortunately, a pain--a long and convoluted process that it would be very unwise for average users to try. For people not yet familiar with Linux and who are wary of the command line, I would recommend that both e-mail clients remain installed. You can ask her to use the new client for all new e-mail and fire up *Evolution* (if that is the legacy one) only when the need for accessing old e-mails comes up. Note: Lubuntu may use yet a different e-mail client than either *Evolution* or *Thunderbird*.

E-mail is generally stored in every user's **home** directory. *Make sure* this directory is backed up to some outside storage before nuking her HD and installing another OS.

BTW, *will1982* mentioned Xubuntu, which is another very viable alternative. I have it installed on two older laptops and love it. Had to download different driver modules for my Broadcom wireless card, but after doing so, it has worked like a charm, with the usual Linux robustness.

---

### Post by deadflowr on 2012-10-07
> **Florio said:**
> Thanks a lot for all your input, guys.:-) 

I really like the idea of a lighter version of Ubuntu, so Lubuntu sounds like the best move. I wasn't even aware it existed.

I'm just wondering about saving the email that my wife currently has on her netbook. Is this possible, given that (from what I've just read), Lubuntu 12.4 has a completely different email client. What format do email messages have in Ubuntu, and where are they stored?
Forgive the lame questions, but I'm a Windows user and know very little about Linux (it's a wonder I managed to install it on the netbook!):lolflag:

Email downloads depend on the type of protocol you set up and use.
If you use IMAP, then all your email is still sitting on the server, which can be accessed through a web browser. If you use POP then all your mail has been downloaded and fully moved to your system.
I can't remember the default email client for natty, but if it's thunderbird, you could probably just save the thunderbird folder(which is a hidden folder inside your home folder, where your pictures and videos are. Press ctrl+h to show hidden files/folders).
If you can't remember how your email setup is run, I'd suggest going to the email site online through a browser and logging into it to see if the mail is still there or if it has been moved to your computer.

---

### Post by Florio on 2012-10-07
Yes, Evolution is the client on my wife's netbook. As far as I know, Sylpheed is on Lubuntu 12.04. I'll look into this a bit more and see, first of all, is she actually wants to keep any of her old emails!
Thanks again for all your assistance.
:)

---

### Post by Lars Noodén on 2012-10-08
> **Florio said:**
> I'm just wondering about saving the email that my wife currently has on her netbook. Is this possible, given that (from what I've just read), Lubuntu 12.4 has a completely different email client. 

Regardless of which distro you choose, you can always install the mail client you wish to use even if it is not the default for that distro.

---

### Post by puntigamer on 2012-10-08
My solution was to build a "custom" system from the ubuntu-core image. It's really not difficult! Just follow a guide to install your desired DE and after that install everything you/your wife need/needs via apt-get (begin with synaptic or Ubuntu SW Center) ;)
So you won't have anything unnecessary on you system!

---

### Post by newb85 on 2012-10-08
> **DuckHook said:**
> I had to change from *Evolution* to *Thunderbird* when I upgraded and it is, unfortunately, a pain--a long and convoluted process that it would be very unwise for average users to try. For people not yet familiar with Linux and who are wary of the command line, I would recommend that both e-mail clients remain installed. You can ask her to use the new client for all new e-mail and fire up *Evolution* (if that is the legacy one) only when the need for accessing old e-mails comes up. Note: Lubuntu may use yet a different e-mail client than either *Evolution* or *Thunderbird*.

But why switch at all?  If she's used to Evolution and happy with it, let her use Evolution.  It can still be installed on 12.04 (regardless of whether you choose Ubuntu, Lubuntu, Xubuntu, etc.).

Before switching to another flavor of Ubuntu, you should drop it onto a Live USB and have your wife test drive it to make sure she likes the interface.

---

### Post by DuckHook on 2012-10-08
> **newb85 said:**
> But why switch at all?  If she's used to Evolution and happy with it, let her use Evolution.  It can still be installed on 12.04 (regardless of whether you choose Ubuntu, Lubuntu, Xubuntu, etc.).

This is true. In my case, I made the effort to switch because:

1. Evolution is big and unwieldy and often refused to sync with my SP,
2. Evolution would sometimes crash,
3. I wanted the ongoing ease of using Ubuntu's "recommended" client knowing that they would be committed to supporting it for the duration of 12.04's support cycle

However, there is a lot to be said for just sticking with Evolution.

---

### Post by Florio on 2012-10-09
Well, I have installed Lubuntu 12.04, and have made a few small changes, including replacing Chromium with Firefox. For the moment my wife seems very happy with it, also because the user interface is quite similar to that of Windows.
I do, however, have one small problem. I've retained Sylpheed as an email client rather than installing Evolution, but I cannot for some reason send email, only receive it (my wife has a hotmail account). I get the following message:
Error
Can't connect to SMTP server: smtp.live.com:25

I've searched the internet for a solution, and although I've seen that other Sylpheed users have had the same problem, I've yet to find a solution. One website suggested changing the SMTP port from 25 to 587, but this does not work for me.

Can someone offer a fix to this problem?

---

### Post by nothingspecial on 2012-10-09
Hi,

Please make a new thread with a title pertaining to your problem eg

"Can't send emails with hotmail using sylpheed" or something like that.

Right now your thread title has nothing to do with the current problem and as such the person who knows the answer will miss it.

Use the lubuntu prefix also.

---

### Post by Florio on 2012-10-09
Thanks.  Will do!

---

