---
title: "[SOLVED] e17 install help"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by AnLGP on 2008-06-16
hello,

I've been trying to follow this guide:

[http://wiki.enlightenment.org/index.php/E17_User_Guide/Installing_using_Linux_distribution_packages#Debian_GNU.2FLinux](http://wiki.enlightenment.org/index.php/E17_User_Guide/Installing_using_Linux_distribution_packages#Debian_GNU.2FLinux)

and after I do

```
wget http://xsm.alphagemini.org/files/archive_key.asc
```

it puts out this:

> --2008-06-16 14:29:00--  [http://xsm.alphagemini.org/files/archive_key.asc](http://xsm.alphagemini.org/files/archive_key.asc)
Resolving xsm.alphagemini.org... 85.88.25.135
Connecting to xsm.alphagemini.org|85.88.25.135|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2393 (2.3K) [text/plain]
Saving to: `archive_key.asc'

100%[======================================>] 2,393       --.-K/s   in 0.1s    

2008-06-16 14:29:11 (18.0 KB/s) - `archive_key.asc' saved [2393/2393]

and returns an empty line for the next command.  I try and do this:

```
apt-key add archive_key.asc
```

and it puts out this:

> gpg: can't open `/etc/apt/trusted.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `archive_key.asc': general error
gpg: import from `archive_key.asc' failed: general error

I'd like to try and upgrade to e17 (even tho I know its testing).  Can someone please help?  Thanks!

I'm on Debian Lenny.

---

### Post by Cypher on 2008-06-16
Prefix the "apt-key add" command with "sudo" and proceed with the instructions..

---

### Post by AnLGP on 2008-06-16
ok I did that.  I get to this part:

> Pinning

As EFL packages are entering Debian/experimental and finally Debian/sid it is necessary to override them due to possible API incompatibilities with packages from this repository.

Add the following to /etc/apt/preferences

 Package: *
 Pin: origin debian.alphagemini.org
 Pin-Priority: 600

Supported architectures are i386, amd64 and sparc at the moment.

See [http://xsm.alphagemini.org/E17/repository/](http://xsm.alphagemini.org/E17/repository/) for more details. 

and when I try to edit this file

```
/etc/apt/preferences
```

it says it doesn't exist?

---

### Post by Inxsible on 2008-06-16
Why don't you simply use the OsOz repos. Here's a rundown of what you need to do to get E17 from that repo.

As root
1)```
 nano /etc/apt/sources.list
```2) add this line to it ```
deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) tinwoodman main
```3)```
apt-get update && apt-get upgrade
```4)```
apt-get install e17-cvs
```That will get you the latest e17 on your debian lenny. Is your lenny a minimal install or does it already have some WM/DE ?

If you want you can install a DM like GDM, KDM or SLiM which will start up E17, or if you are like me and hate DMs then you can simply login at the CLI and have a bash profile start up your X for you. The command to start E17 would be ```
startx /opt/e17/bin/enlightenment_start
```

---

### Post by AnLGP on 2008-06-16
there's always an easier way....

I have e16 and JWM as my WMs.  Minimal Install.

I would love to have a bash to start up my X I just don't know how to do it :(

---

### Post by Inxsible on 2008-06-16
> **AnLGP said:**
> there's always an easier way....

I have e16 and JWM as my WMs.  Minimal Install.Good Luck !!

I have never been a fan of the look of JWM though ;-)

If you already have 2 WM's then you would most likely have a DM correct? Then e17 should get added to it or you may have to do it manually.

---

### Post by AnLGP on 2008-06-16
Thanks.

Can you tell me how to do a bash startup file?  :D

---

### Post by Inxsible on 2008-06-16
> **AnLGP said:**
> [snip]

I would love to have a bash to start up my X I just don't know how to do it :(

Once you get your e17 installed. This is what you do.
1)```
leafpad ~/.bash_profile
```You can use whatever editor you are comfortable with. I use Leafpad which is extremely light and good for basic text editing.
2) At the very end add this line```

startx /opt/e17/bin/enlightenment_start
```Btw...if that doesn't work, then you might have to create a xinitrc file.

But you should try this first. Lemme know if that works out for you.

P.S. Note that having a bash profile will not work if you have multiple WM's installed. This is obvious because it will go to the WM that is in the bash profile. If you install a different WM, you will also have to change the command in the bash profile file.

Bottom line: Good if you have only one WM/DE

---

### Post by ubernuber on 2008-06-16
Good stuff Inxsible.

I also am a fan of minimalistic but working environments and will try out the bash profile method to start my X as well for Fluxbox. Would you know the command for Fluxbox, since you also use it?

I also plan to make it a dual boot of E17. :)

---

### Post by Inxsible on 2008-06-16
> **ubernuber said:**
> Good stuff Inxsible.

I also am a fan of minimalistic but working environments and will try out the bash profile method to start my X as well for Fluxbox. Would you know the command for Fluxbox, since you also use it?

I also plan to make it a dual boot of E17. :)Sure. You would probably not need to give the path. E17 requires the path, since the entire source is installed under /opt/e17.

For Fluxbox, simply put this line at the very end of the bash profile file```
startfluxbox
```You don't even need startx before that.

---

### Post by ubernuber on 2008-06-16
Great !!

Bookmarking this thread for trying out later tonight. :D

---

### Post by AnLGP on 2008-06-16
WHOA :cool:\\:D/

that is flashy!  and seems lightweight.

er, is it safe to get rid of e16 or would you keep it around?

---

### Post by Inxsible on 2008-06-16
> **AnLGP said:**
> WHOA :cool:\\:D/

that is flashy!  and seems lightweight.

er, is it safe to get rid of e16 or would you keep it around?I wouldn't keep it around once I was happy with my E17. Make sure you install all the apps that you want.

You can get rid of e16 then.

Did the bash profile suggestion work for you? If so, I would just remove the DM altogether - of course if you plan to keep the other WM's around, you may still need it.

---

### Post by Inxsible on 2008-06-16
You do have to get used to E17 though. You will find a lot of differences in how things are handled in E17 as compared to Gnome/Xfce/KDE etc.

Good for eye candy though and still keeping it lightweight :)

---

### Post by AnLGP on 2008-06-16
I don't use a DE just WMs.  I think I'll keep it around.  Where can I go for themes?

---

### Post by Inxsible on 2008-06-16
> **AnLGP said:**
> I don't use a DE just WMs.  I think I'll keep it around.  Where can I go for themes?
By DM - I meant the display manager like GDM or KDM or SLiM or WDM or XDM (those are all I know:) )


You can get enlightenment themes from

[http://www1.get-e.org/Themes/E17/](http://www1.get-e.org/Themes/E17/)

[E17 Stuff]("http://www.e17-stuff.org")


You can even get animated wallpapers although that uses a lot more resources. My machine just slowed down when I tried that :)

Good thing about Enlightenment is that different desktops can have different wallpapers out of the box.

Bad thing is that configuration is still a major hassle in Enlightenment. That should change over time I guess.
[ ]("http://www.e17-stuff.org")

---

### Post by AnLGP on 2008-06-16
ah yeah I think I'm going to keep slim.  I'm over two gigs on space used now tho and am fretting about it.  I'm gonna mark this solved.  :)

---

