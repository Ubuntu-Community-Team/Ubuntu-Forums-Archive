---
title: "My Apt-Get seriously broken"
date: 2012-11-30
forum: New to Ubuntu
---

### Post by ACagliano on 2012-11-30
I followed the instructions about adding a source to the apt-get repositories. After doing this, apt-get **does not work on a single flipping install**. Is there a way to totally flush out the apt-get repositories, and reinstall them all, without reinstalling Ubuntu?

---

### Post by monkeybrain2012 on 2012-11-30
You can get rid of the ppa as follows:

Open the Software Centre, go to Edit > Software Sources > Other Software where you will find two lines corresponding to your ppa (one for the binaries, one for the source codes), just right click them and choose remove and reload the SC.

Alternatively,

in the terminal 

```
cd /etc/apt/sources.list.d

ls
```

This will list a bunch of files, find those with the name of your ppa  and delete them

```
sudo rm filename
```

then
```
sudo apt-get update
```

---

### Post by ibjsb4 on 2012-12-01
Either remove the new source you added.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab)

Or [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo apt-get update

And please post the output.

---

### Post by Frogs Hair on 2012-12-01
I had serious problems with an icon PPA yesterday and removing the source and updating should work. I had a damaged package because the apt cache didn't set up properly. After finally getting into synaptic with a series of terminal commands I was able get rid of the broken package. I found success with a different source for the same package.

---

### Post by ACagliano on 2012-12-02
```
anthony@anthony-laptop:~$ cd /etc/apt/sources.list.d
[email]anthony@anthony-laptop:/etc/apt/sources.list[/email].d$ ls
[email]anthony@anthony-laptop:/etc/apt/sources.list[/email].d$ ls
[email]anthony@anthony-laptop:/etc/apt/sources.list[/email].d$ ls
[email]anthony@anthony-laptop:/etc/apt/sources.list[/email].d$ sudo apt-get update
[sudo] password for anthony: 
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main InRelease                              
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates InRelease                           
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security InRelease
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main Release.gpg
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates Release.gpg
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security Release.gpg     
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main Release             
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates Release
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security Release
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/multiverse TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/universe TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates/main TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates/multiverse TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates/universe TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security/main TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security/multiverse TranslationIndex
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security/universe TranslationIndex
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/universe Sources    
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/multiverse Sources  
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/universe amd64 Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/multiverse amd64 Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/universe i386 Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/multiverse i386 Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates/main Sources     
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates/universe Sources 
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates/multiverse Sources
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates/main amd64 Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates/universe amd64 Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates/multiverse amd64 Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates/main i386 Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates/universe i386 Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates/multiverse i386 Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security/main Sources    
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security/universe Sources
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security/multiverse Sources
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security/main amd64 Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security/universe amd64 Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security/multiverse amd64 Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security/main i386 Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security/universe i386 Packages
  404  Not Found
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security/multiverse i386 Packages
  404  Not Found
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/multiverse Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/multiverse Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/universe Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) main/universe Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates/main Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates/main Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates/multiverse Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates/multiverse Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates/universe Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) updates/universe Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security/main Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security/main Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security/multiverse Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security/multiverse Translation-en
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security/universe Translation-en_US
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) security/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/main/universe/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/main/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/main/multiverse/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/main/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/main/universe/binary-amd64/Packages](http://old-releases.ubuntu.com/ubuntu/dists/main/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/main/multiverse/binary-amd64/Packages](http://old-releases.ubuntu.com/ubuntu/dists/main/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/main/universe/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/main/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/main/multiverse/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/main/multiverse/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/updates/main/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/updates/main/source/Sources)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/updates/universe/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/updates/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/updates/multiverse/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/updates/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/updates/main/binary-amd64/Packages](http://old-releases.ubuntu.com/ubuntu/dists/updates/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/updates/universe/binary-amd64/Packages](http://old-releases.ubuntu.com/ubuntu/dists/updates/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/updates/multiverse/binary-amd64/Packages](http://old-releases.ubuntu.com/ubuntu/dists/updates/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/updates/main/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/updates/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/updates/universe/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/updates/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/updates/multiverse/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/updates/multiverse/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/security/main/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/security/main/source/Sources)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/security/universe/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/security/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/security/multiverse/source/Sources](http://old-releases.ubuntu.com/ubuntu/dists/security/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/security/main/binary-amd64/Packages](http://old-releases.ubuntu.com/ubuntu/dists/security/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/security/universe/binary-amd64/Packages](http://old-releases.ubuntu.com/ubuntu/dists/security/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/security/multiverse/binary-amd64/Packages](http://old-releases.ubuntu.com/ubuntu/dists/security/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/security/main/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/security/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/security/universe/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/security/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/security/multiverse/binary-i386/Packages](http://old-releases.ubuntu.com/ubuntu/dists/security/multiverse/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
[email]anthony@anthony-laptop:/etc/apt/sources.list[/email].d$
```

---

### Post by monkeybrain2012 on 2012-12-02
So you don't have any ppa (ls in sources.list.d returns nothing), but a lot of "old releases" what is this all about?

How did you install Ubuntu?

---

### Post by mcduck on 2012-12-02
more importantly, which *version* of Ubuntu is it?

old-releases repositories are only used for out-of-support Ubuntu versions...Some lines in the output would indicate that you are running 12.04, which is still a supported release and therefore gets it's packages from normal repositories, not from the old-releases server.

..and on the other hand, if it's *not* 12.04 you are running, you really shouldn't be using 12.04's repositories.

---

### Post by deadflowr on 2012-12-02
> more importantly, which version of Ubuntu is it?

+1.
But I also see that the old-releases seem to be missing the codename(jaunty, hardy, natty, etc,etc).

Here should help:

[http://superuser.com/questions/339537/where-can-i-get-theold-repositories-for-ubuntu-9-04-jaunty]("http://superuser.com/questions/339537/where-can-i-get-theold-repositories-for-ubuntu-9-04-jaunty")

---

### Post by ACagliano on 2012-12-03
I am using 12.04. I changed to the old sources because I was getting frustrated after breaking the reps and then removing the added source and I still didn't work so I was kind of willing to try anything. 

It should be archives.ubuntu.com, correct? And what is my code name?

---

