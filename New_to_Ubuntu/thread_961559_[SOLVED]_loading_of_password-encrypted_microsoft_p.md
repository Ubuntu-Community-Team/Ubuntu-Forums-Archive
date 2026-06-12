---
title: "[SOLVED] loading of password-encrypted microsoft powerpoint is not supported?"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by LastWho on 2008-10-28
Hi
i tired to open an important pps file with openoffice.org but i couldn't and recieved this error message:

[INDENT]change background page assigment
the loading of password-encrypted microsoft powerpoint
presentations is not supported.[/INDENT]

it said that its password-protected but other windows users confirmed to me that its not.

i need this doc to study and i ve only ubuntu on my pc (and wine of course), plz help 

thanks

ps: i made some searchs with google and i found this scary page:
[http://qa.openoffice.org/issues/show_bug.cgi?id=46307](http://qa.openoffice.org/issues/show_bug.cgi?id=46307)

also i ve tried to install the ppt viewer with wine but it didn't work

---

### Post by dracayr on 2008-10-28
this may help:

[http://icosahedron.wordpress.com/2007/10/05/viewing-powerpoint-on-linux/](http://icosahedron.wordpress.com/2007/10/05/viewing-powerpoint-on-linux/)

dracayr

---

### Post by cariboo on 2008-10-28
This problem has been around for a long time and it doesn't seem like the Open Office devs feel that this is a big problem. Their work around's don't seem to be viable, as they feel it is the fault of the creator for setting it up improperly.

Jim

---

### Post by LastWho on 2008-12-19
to open such files, i m using the ppt viewer 2003; that i installed with winetricks as the following:
```
$ wget www.kegel.com/wine/winetricks
```

then

```
$ sh winetricks msxml3 dotnet20 gdiplus riched20 riched30 vcrun2005sp1
```

thx

---

### Post by mostafakvd on 2009-04-04
Thank u my friend u r really good :p:p;);):popcorn:

---

### Post by hlopezvg on 2009-09-01
Thanks  LastWho, works great for me, I was able to avoid the annoying message "l[B]oading of password-encrypted microsoft powerpoint is not supported?":o

Great
[/B]

---

### Post by RobinAJ on 2009-11-20
> **LastWho said:**
> to open such files, i m using the ppt viewer 2003; that i installed with winetricks as the following:
```
$ wget www.kegel.com/wine/winetricks
```then

```
$ sh winetricks msxml3 dotnet20 gdiplus riched20 riched30 vcrun2005sp1
```thx


How do I do this?

I've installed Wine, downloaded the vieuwer (2007) from the microsoft site, I hava a password coded pps on my desktop but how to proceed from here?
I also typed the code in the terminal but I don't seem to get it to work. Please help me with this problem.

I use Ubuntu 9.04 Netbook Remix on a Asus 900 Eeepc.

---

### Post by fire.for.effect on 2010-07-24
Wow. This is cool. Seems to be loading fine. I have to teach some classes and, go figure, they are all password protected and in everyone's favorite office suite. Ugh! When will the rest of the world get with the program?

---

### Post by PGFracing on 2012-08-25
I just downloaded 12.04 on my laptop and it doesn't have this problem at all, but I have a desktop that I had 10.04 and then upgraded to 12.04 and it has this problem. Obviously it works on the 12.04 without having to download wine there must be another solution. I do have wine but would like to be able to just click and watch. Any more news? thanks

---

### Post by overdrank on 2012-08-25
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

