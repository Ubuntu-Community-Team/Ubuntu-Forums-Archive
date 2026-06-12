---
title: "how to untar to a specific directory???"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by locum on 2008-07-22
Hi all, 
I am completely new to Linux and Ubuntu and installed it because of my interest in Joomla, so I am trying to install Xampp but clearly I am doing something wrong, even though I'm following the "how to" instructions.
This is the results I get when I open a terminal and sudo the Xampp tar

tar: xampp-linux-1.5.3a.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I am trying to unzip it to C/ opt

The Xampp tar is on my desktop as is the terminal when I open it. I feel a bit stupid because it's such a simple task and I must be doing something fundamentaly wrong, I have serched for the last few hours for the answer many of which tell you what to do but not precicley how.

Many Thanks. Martin

---

### Post by Tim Sharitt on 2008-07-22
Change into the directory you wish to unpack the file and pass the full path of the archive to tar.
```
cd /directory you wanto unpack to
tar -xzf /full path to archive/archive.tar.gz
```

If you are trying to unpact to /opt you will have to run as sudo.

---

### Post by Troll_the_Great on 2008-07-22
The easiest way is to just right click on the .tar file and choose "Extract here".After that you can move it anywhere you want.If you want to install it, it's a bit more complicated.Have a look at this links and post back any question you have (and there will be :) ). 
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Cheers

---

### Post by freak42 on 2008-07-22
tar cannot find the file you want to untar.

either the file must be in the same directory as you are when you issue the tar filename command or you have to specify the whole path to the file for tar to find it.

Also note there is no C/ opt folder.
The root folder in any linux file system is simply /
However there is a /opt/ folder, but usually only root is allowed to write there. (so you would need to use sudo tar ... if you want to write to a folder where you can't write with your normal user rights.

---

### Post by locum on 2008-07-22
Thanks for the replies guys but I'm afraid I still don't get it. This is what I want to do:  sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt

If I cant get this right then I haven't got a hope in hell of following the remainder of the instructions to install Xammp.

I wonder if anyone knows of a linux guide that holds your hand?

Thanks again. Martin

---

### Post by Tim Sharitt on 2008-07-22
Are you in the directory which contains the archive? If not, chance to that directory, or give the full directory to tar.

---

### Post by jerome1232 on 2008-07-22
When you open the terminal it's actually in /home your desktop is in /home/Desktop

so you would want to do
```
sudo tar xvzf Desktop/xampp-linux-1.5.3a.tar.gz -C /opt
```
or you can do this one from anywhere

```
sudo tar xvzf ~/Desktop/xampp-linux-1.5.3a.tar.gz -C /opt
```

---

### Post by billgoldberg on 2008-07-22
> **locum said:**
> Thanks for the replies guys but I'm afraid I still don't get it. This is what I want to do:  sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt

If I cant get this right then I haven't got a hope in hell of following the remainder of the instructions to install Xammp.

I wonder if anyone knows of a linux guide that holds your hand?

Thanks again. Martin

Like the poster above me said, you'll always need to specify the path to the file if you aren't in the directory (using the cd commqnd).

So let's say your .tar file is on the desktop and locum is your username, the command would be

```
sudo tar xvfz /home/locum/Desktop/xampp-linux-1.5.3a.tar.gz -C /opt
```

You can use a curly (don't know the name) instead of /home/locum/ but I don't have it on my azerty keyboard, so I never use that.

note: commands are case sensitive (aka desktop isn't the same as Desktop)

--

Edit: beaten by jerome1232, but he misspelled desktop in the command making it useless, so I win :p

---

### Post by freak42 on 2008-07-22
Hi again,

this is somewhat offtopic. But if you want to install apache, php and mysql there are easier ways.

These programs (as well as many others) come in so called packages which are preconfigured installations for ubuntu.

Here is a tutorial how one can install apache php and mysql (and I am sure perl is not harder):
[http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100]("http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100")

It is probably much easier to follow this tutorial than to do a custom install.

I hope this helps, otherwise apologies.

---

### Post by locum on 2008-07-22
Hello again, this is driving me nuts, but thanks to all your help I now understand what I have to do to unzip a file, however I have tried all the permutations suggested and all I get is: "No such file or directory".

I wondered if C/ perhaps is somehow called something else or is it always the default drive? and how can I find out?

Hi freak42 I did previously think about the options that you have suggested but thought Xampp would be easier as I have used it before with no trouble, obviously not on Linux though. Anyway whatever happens I need to get sorted out with the tar archive problems I'm having first.

Appriciated, Martin

---

### Post by CatKiller on 2008-07-22
> **locum said:**
> I wondered if C/ perhaps is somehow called something else or is it always the default drive? and how can I find out?

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by ace007 on 2008-07-22
the "-C' is a flag for the tar command.  There should be a space between it and whatever the next argument is.

For instance

```

sudo tar xvfz /home/locum/Desktop/xampp-linux-1.5.3a.tar.gz -C /opt

```

has the "-C" flag which means to create an archive.  You're telling tar to create an archive.  I think you are mistaken.

I think "/opt" is the destination of where you want the compressed package untarred.

So, try this:
```

cd /opt
sudo tar xvfz /home/locum/Desktop/xampp-linux-1.5.3a.tar.gz

```

You have entered the directory "/opt" and are untarring the package where you are.

Hope it helps

---

### Post by jerome1232 on 2008-07-22
Linux doesn't use drive letters to distinguish partitions (c:/ e:/ etc)
it uses mount points.  The root of the drive is just / refered to as root.

Some people make a second partition and mount it as /home

in the command where i have -C /opt doesn't mean drive c, it's a flag for tar to tell it to change to /opt and decrompress the archive there

---

### Post by locum on 2008-07-23
Thanks to all you guys for trying to help me with this, I have tried and tried all the suggestions and am getting nowhere. I am now wondering if there is possibly a glitch in the terminal and I need to reinstall.

Before I do that though I wonder is someone might help me by downloading the file to their desktop and let me know how they get on. I hope I'm not pushing my luck here as you have helped me a lot already.

Here is the link to the download     [http://prdownloads.sourceforge.net/x...ar.gz?download](http://prdownloads.sourceforge.net/x...ar.gz?download)

Here is the link to the instructions I am trying to follow   [http://ubuntuforums.org/showthread.php?t=223410&highlight=install+xampp](http://ubuntuforums.org/showthread.php?t=223410&highlight=install+xampp)

Much appriciated.  Martin

---

### Post by locum on 2008-07-23
Well thank goodness I've finally sorted it out, I moved the tar file to Documents, cd to Documents and pasted in the remainder of the original instructions and bingo the tar was unzipped to opt.
So it seems that I can't untar directly from my desktop or home, well at least I know now where I can untar from.
Big thanks to everyone for their help and support, and also for the help links which I have bookmarked, I am going to buy Linux for Dummies before I go any further with the terminal and other applications.
Regards, Martin.

---

