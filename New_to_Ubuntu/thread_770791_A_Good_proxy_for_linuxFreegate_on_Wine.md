---
title: "A Good proxy for linux/Freegate on Wine"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Hoom@n on 2008-04-27
Hello!
I'm in Iran and here government censors the web, all news sites, all about politics, all social networks(like myspace, facebook and ...), all music sites, all video sites and so on! I use Freegate in Windows, but I can't run in on Wine and I get:
[IMG]http://i30.tinypic.com/2pov50y.png[/IMG]
So I used Tor for a while, but:
[LIST=1]
[*]It was too slow and didn't work everytime!
[*]To use it on Firefox I need TorButton which doesn't work in FF3
[/LIST]
So please tell me a good way to bypass the Iran's internet censorship!
Thanks.

---

### Post by Hoom@n on 2008-04-29
No one?!/No way?!/Can't run that on Wine?!

---

### Post by Monicker on 2008-04-29
Take a look at FoxyProxy, I use that when I need to connect to Tor.

---

### Post by Hoom@n on 2008-05-01
Really thanks! It's really good!
But is there any other proxy (not Tor) for any emergency situation in which Tor doesn't work?

---

### Post by Monicker on 2008-05-01
> **Hoom@n said:**
> Really thanks! It's really good!
But is there any other proxy (not Tor) for any emergency situation in which Tor doesn't work?

The only other thing I know of myself is proxychains, which is a command line application.  You still need a list of proxy servers to use with it though.  I only tried it briefly, so I don't recall a lot about how it works.  Its in the Ubuntu repos.

---

### Post by rd1381 on 2009-01-20
> **Hoom@n said:**
> Hello!
I'm in Iran and here government censors the web, all news sites, all about politics, all social networks(like myspace, facebook and ...), all music sites, all video sites and so on! I use Freegate in Windows, but I can't run in on Wine and I get:
[IMG]http://i30.tinypic.com/2pov50y.png[/IMG]
So I used Tor for a while, but:
[LIST=1]
[*]It was too slow and didn't work everytime!
[*]To use it on Firefox I need TorButton which doesn't work in FF3
[/LIST]
So please tell me a good way to bypass the Iran's internet censorship!
Thanks.

you need the correct version of that dll "mfc42.dll" installed in your-home-directory/.wine/drive_c/windows/system32

here is the link to correct version of that dll

[http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc42.dll/6.0.400/download.html](http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc42.dll/6.0.400/download.html)

happy surfing

---

### Post by ShoeYork on 2009-02-03
I have a fully updated Wine
I have the mfc42.dll and am no longer getting the error for it
When I start up Freegate6.79Pro I get this error:

[IMG]http://i43.tinypic.com/1zcpc08.png[/IMG]

No matter which option I choose, and which options I toy with after, I can't get around filters.

Wine Internet Explorer pops up with it but is without an address bar and uselessly sits on WineHQ.

Is it because I'm trying to use firefox?

Anybody?

---

### Post by rd1381 on 2009-02-04
> **ShoeYork said:**
> 

No matter which option I choose, and which options I toy with after, I can't get around filters.

Wine Internet Explorer pops up with it but is without an address bar and uselessly sits on WineHQ.

Is it because I'm trying to use firefox?

Anybody?


set this optiom in tunnel tab of freegate
"classic mode"

and in setting tab check "Do not open browser ....."'

---

### Post by fishfillet on 2010-01-02
> **Hoom@n said:**
> Hello!
I'm in Iran and here government censors the web, all news sites, all about politics, all social networks(like myspace, facebook and ...), all music sites, all video sites and so on! I use Freegate in Windows, but I can't run in on Wine and I get:
[IMG]http://i30.tinypic.com/2pov50y.png[/IMG]
So I used Tor for a while, but:
[LIST=1]
[*]It was too slow and didn't work everytime!
[*]To use it on Firefox I need TorButton which doesn't work in FF3
[/LIST]
So please tell me a good way to bypass the Iran's internet censorship!
Thanks.

What I simply did is to I copied the mfc42.dll file from my Windows XP SP3 installation and copied it to my wine folder.

Right after that, freegate (6.89h) is working well... actually much faster that it was running in Windows.

---

### Post by z0Zor on 2011-06-05
Hi everyone , 
I am a new user , ubuntu 11.04 
Sorry to up this problem , but i got the same, 
Yesterday have installed wine in my computer to be able to use Freegate, the version of my freegate is U21 . When tried to run the program using wine ,  have as reply , this program is not marked as executable .. it may be dangereous to run it , after that , nothing. is an executable program i dont know why dont want to run ,  could you please help me to solve this problem ?
 Thanks in advance and sorry for my bad english .

---

### Post by Elfy on 2011-06-05
Necroclosed.

Please start a new thread.

---

