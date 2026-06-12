---
title: "using keepass2 won't work anymore because the password is not entered when typing"
date: 2017-03-15
forum: New to Ubuntu
---

### Post by ronjjjg8885 on 2017-03-15
i've a password database

when i try to type the password it is only work for some of the letters (just a few)
so i can't enter the password fully
numbers are fine.

at first it worked fine and the problem started the next day.

the installation was through the ubuntu website direct link

---

### Post by howefield on 2017-03-15
> **ronjjjg8885 said:**
> i've a password database

Cool, a password manager is a great way of keeping track of passwords.

> when i try to type the password it is only work for some of the letters (just a few)
so i can't enter the password fully
numbers are fine.

Are you talking about the password to open the database initially or when you create new entries within the database ? 

> the installation was through the ubuntu website direct link

Can you share the link ?

---

### Post by ronjjjg8885 on 2017-03-15
the link:
[https://apps.ubuntu.com/cat/applications/quantal/keepass2/](https://apps.ubuntu.com/cat/applications/quantal/keepass2/)

i'm talking about opening the database and not talking about entries.

right it's a good passwords manager

---

### Post by ajgreeny on 2017-03-15
That is a very old web-page pointing to a very old version of keepass2 intended for the now unsupported Ubuntu 12.10 so I am surprised you got it to install at all in a supported version of Ubuntu.  Which version of Ubuntu are you using; I hope it's not 12.10?

Try command ```
sudo apt-get remove --autoremove keepass2
sudo apt-get install keepass2
```
to first remove the current unsupported version plus dependencies; the second to install the proper version for your version of Ubuntu.
The first command may not be needed but as that version of keepass2 is out of date and not intended for any currently supported version of Ubuntu it may be best to remove it before getting the correct version.

---

### Post by howefield on 2017-03-15
> **ajgreeny said:**
> That is a very old web-page pointing to a very old version of keepass2 intended for the now unsupported Ubuntu 12.10 so I am surprised you got it to install at all in a supported version of Ubuntu.  Which version of Ubuntu are you using; I hope it's not 12.10?

Try command ```
sudo apt-get remove --autoremove keepass2
sudo apt-get install keepass2
```
to first remove the current unsupported version plus dependencies; the second to install the proper version for your version of Ubuntu.
The first command may not be needed but as that version of keepass2 is out of date and not intended for any currently supported version of Ubuntu it may be best to remove it before getting the correct version.

Before going down that road, might be better to simply check the Keepass2 version that was installed. I'm pretty sure that the link would install the version from your sources.list repositories rather than the older version that one might think it would.

From a terminal..

```
apt-cache policy keepass2
``` 

The various versions are..

```
precise (12.04LTS) (utils): Password manager [universe] : 2.18+dfsg-2: all
trusty (14.04LTS) (utils): Password manager [universe]  :  2.25+dfsg-1: all
trusty-updates (utils): Password manager [universe]      : 2.25+dfsg-1ubuntu0.1: all
xenial (16.04LTS) (utils): Password manager [universe] : 2.32+dfsg-1: all
yakkety (16.10) (utils): Password manager [universe] : 2.34+dfsg-1: all
zesty (utils): Password manager [universe] : 2.35+dfsg-1: all
```

---

### Post by ajgreeny on 2017-03-16
Thanks for that howefield.

I have never installed anything using links of that sort on a web-page possibly because I do not have the ubufox add-on installed in my system and the links do not work. 
I remove that add-on as I like to keep things on a more standard browser basis; in fact I'm not quite sure exactly what it does add to firefox so I am just about to add it to try to find out more and see if it allows me to install that package.

No, even with the ubufox add-on it is not possible to use the link from that web-page as far as I can see, so I am a bit baffled; perhaps it depends on also having the software-centre installed because that is something else that I always remove.

---

### Post by howefield on 2017-03-16
> **ajgreeny said:**
> Thanks for that howefield.

I have never installed anything using links of that sort on a web-page possibly because I do not have the ubufox add-on installed in my system and the links do not work. 
I remove that add-on as I like to keep things on a more standard browser basis; in fact I'm not quite sure exactly what it does add to firefox so I am just about to add it to try to find out more and see if it allows me to install that package.

I did install it last night on a zesty install that was about to be blown away and using the Chromium web browser.

Clicking the link prompted a dialogue box requesting xdg-open be allowed to run, which I believe opens the link in the users preferred application for that type of link, in this case an apt-url.

It installed version 2.35, the current package from the Zesty repositories. 

I think ronjjjg8885 is using Xenial, so probably has Keepass2 version 2.32.

---

### Post by ronjjjg8885 on 2017-03-16
ajgreeny:

i'm using the latest ubuntu

how do i completely remove this old keepass2? does the command is for a complete removal?

i will try to install the way you told me

edit:
ok
i did it but listen
the first time i opened it it worked fine.
but now again after this first time the typing problem returned.

i will read the other replies but it is a bit complicated to me to read english so i hope i will understand

edit:
i'm not sure i understand what to do next

---

### Post by ajgreeny on 2017-03-16
Sorry but I can not personally help you as I have never seen a problem like yours, and I don't use keepass2.

---

### Post by howefield on 2017-03-16
> **ronjjjg8885 said:**
> i'm not sure i understand what to do next

If you are open to using another password manager, I'd recommend Keepassx which is also in the Ubuntu repositories..

Either install with the Software Centre or install via the terminal whichever suits you best..

```
sudo apt install keepassx
```

Keepass2 can be uninstalled with..

```
sudo apt purge keepass2
```

or using the command ajgreeny gave you above.

---

### Post by ronjjjg8885 on 2017-03-16
thank you
i will now use keepassx

after the purge command can i expect it to fully be removed?(keepass2)

what is a good way to synchronize the database between ubuntu and windows? google drive?
i had times where some of my google drive files got corrupted.  this is why i ask

---

### Post by howefield on 2017-03-16
> **ronjjjg8885 said:**
> thank you, i will now use keepassx

You're welcome.

> after the purge command can i expect it to fully be removed?(keepass2)

Yes, using the purge will remove the keepass2 pacakges plus configuration files, although you might want to run

```
sudo apt autoremove
```

to ensure all orphaned dependancies are gone.

> what is a good way to synchronize the database between ubuntu and windows? google drive? i had times where some of my google drive files got corrupted.  this is why i ask

I use an ownCloud setup on a raspberry pi to sync to various devices but yes, google drive will do the job, as will many others such as Spideroak, Dropbox, OneDrive ect ect.

I don't use it but doesn't Google Drive allow for versioned files ? Or just keep a copy or three of the database elsewhere in addition to your file syncing service.

---

### Post by ronjjjg8885 on 2017-03-16
tnx once again
i will try dropbox or google drive

edit:
i've tried to install dropbox with these:
[COLOR=#111111][FONT=Ubuntu]Try to reinstall dropbox.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]First open a terminal and type the following to remove dropbox:[/FONT][/COLOR]
sudo apt-get clean
sudo apt-get update
sudo apt-get --purge remove nautilus-dropbox
sudo apt-get --purge autoremove
[COLOR=#111111][FONT=Ubuntu]Now type the next commands in sequence to install dropbox.[/FONT][/COLOR]
sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
sudo add-apt-repository "deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) $(lsb_release -sc) main"
sudo apt-get update && sudo apt-get install nautilus-dropbox

i did it because the instalation throu the software centre made me a non working dropbox

now i don't have any dropbox and not sure how to undo the comments above

---

### Post by howefield on 2017-03-17
That looks like the correct dropbox repository that you have added so you should be able to install dropbox with the terminal command..

```
sudo apt install dropbox
```

Once installed and launched, dropbox should open and proceed to download the daemon, set itself up and allow you to log in to your account.

If this doesn't work.. give us the output of

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

so that we can advise how to remove the repository that you added and you can go down the more usual method of downloading the deb package from the Dropbox website

[https://www.dropbox.com/install-linux](https://www.dropbox.com/install-linux)

---

### Post by ronjjjg8885 on 2017-03-17
> egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*/etc/apt/sources.list:deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) xenial main restricted
/etc/apt/sources.list:deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
/etc/apt/sources.list:deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) xenial universe
/etc/apt/sources.list:deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) xenial-updates universe
/etc/apt/sources.list:deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) xenial multiverse
/etc/apt/sources.list:deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
/etc/apt/sources.list:deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
/etc/apt/sources.list:deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) xenial main
/etc/apt/sources.list.d/dropbox.list:deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) wily main




here is the output
the problem persist
when clicking Dropbox nothing happnes

---

### Post by howefield on 2017-03-17
You have set up the dropbox repository with "wily" sources rather than xenial which you are using.

Try this..

```
sudo rm /etc/apt/sources.list.d/dropbox*
```

enter your password if prompted and press enter.

Then.. 

```
sudo apt update
```

We can go to the next step once you successfully complete the removal of this repository.

---

### Post by ronjjjg8885 on 2017-03-17
> [COLOR=#000000]You have set up the dropbox repository with "wily" sources rather than xenial which you are using.[/COLOR]


why?

i think dropbox started to work but i will do what you say, shouldn't i?

what to do now after i've done with the commands?

---

### Post by howefield on 2017-03-17
> **ronjjjg8885 said:**
> why?

I don't know, presumably because you are following an old tutorial ? It is seldom a good idea to mix repositories from different Ubuntu releases, you are using 16.04 Xenial, correct ? So all your repositories should reflect that.

> i think dropbox started to work but i will do what you say, shouldn't i?

Well, if dropbox is working you can ignore the the commands offered and just use it.

> what to do now after i've done with the commands?

As above, use dropbox if it is working.

You could alter the "*/etc/apt/sources.list.d/dropbox.list:deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) wily main*" to reflect xenial instead of wily.

---

### Post by ronjjjg8885 on 2017-03-17
i appreciate the help

---

### Post by howefield on 2017-03-17
> **ronjjjg8885 said:**
> i appreciate the help

after this i should do "sudo apt-get install dropbox"?

You're losing me now, you said earlier that "*i think dropbox started to work*" - then use it ;)

I'd simply advise editing the repository to reflect xenial as mentioned above.

---

### Post by ronjjjg8885 on 2017-03-17
i don't know if at this point it is working with xenial or other version
i want it to be seamless

---

### Post by howefield on 2017-03-17
> **ronjjjg8885 said:**
> i don't know if at this point it is working with xenial or other version
i want it to be seamless

All you have to do to ensure that you are up to date and stay that way is edit the dropbox sources file in /etc/apt/sources.list.d/ and replace the word wily with xenial. Then do a... 

```
sudo apt update && sudo apt upgrade
```

What is the output of 

```
apt-cache policy dropbox
```

If it states "Installed: 2015.10.28" you should be up to date, to stay that way edit the source file as above.

---

### Post by ronjjjg8885 on 2017-03-20
it's
Installed: 2015.10.28
already

and it was xenial in that file
you had a mistake btw with
.list.d
it should be .list

---

### Post by howefield on 2017-03-20
> **ronjjjg8885 said:**
> it's Installed: 2015.10.28 already

Cool, then you are up to date.

> and it was xenial in that file

Again cool, that's what you want.

> you had a mistake btw with .list.d it should be .list

No mistake, ppa information really should be stored in /source.list.d/ but if it was in your sources.list then it's no big problem, it'll work just the same.

Feel free to mark the thread as solved if you feel it is.

---

