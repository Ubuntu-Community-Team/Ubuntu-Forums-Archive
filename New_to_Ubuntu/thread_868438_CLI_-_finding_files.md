---
title: "CLI - finding files"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-23
I don't know where anything is.  most specifically downloads, and anything specific.  I can use cd proficientlly and ls.  But What I want is to be able to find anything fast and easy.  For example, I downloaded gnaural the otherday.  But where 'd it go?  I'm not really even sure to begin.  I just want to know I can find something when I want to.

---

### Post by iaculallad on 2008-07-23
> **adamogardner said:**
> I don't know where anything is.  most specifically downloads, and anything specific.  I can use cd proficientlly and ls.  But What I want is to be able to find anything fast and easy.  For example, I downloaded gnaural the otherday.  But where 'd it go?  I'm not really even sure to begin.  I just want to know I can find something when I want to.

To search for filesname:

```
locate file_name
```

To search for a specific command:

```
which command_name
```

---

### Post by ApOgEEs on 2008-07-23
The command line to find files is:

```
locate <your-file-name>
```

for example if you wanna find gnaural, just type in:

```
locate gnaural
```


However, if it is not found, maybe you should update your locate database by doing:

```
sudo updatedb
```

then try again:

```
locate gnaural
```

---

### Post by Dr Small on 2008-07-23
Try:
```
find / -name searchterm
```

---

### Post by unutbu on 2008-07-23
Suggestion for firefox: Click Edit>Preferences. Click Main tab. Enable "Always ask me where to save files".

---

### Post by adamogardner on 2008-07-24
Apogees,  I followed your directions and nothing really happened as you can see:  

adamogardner@CRONUS:~$ locate gnaural
adamogardner@CRONUS:~$ sudo updatedb
sudo: unable to resolve host CRONUS
[sudo] password for adamogardner: 
adamogardner@CRONUS:~$ locate gnaural
adamogardner@CRONUS:~$

unutbu, thanks for that. never new it was there.  now I customized my webpages!

dr.small,  your wording is confusing. " find / " i understand, but " -name " and "searchterm" i don't understand.

---

### Post by Joeb454 on 2008-07-24
do you have gnaural installed?

---

### Post by Vivaldi Gloria on 2008-07-24
```
sudo: unable to resolve host CRONUS
```

adamogardner, you're getting an error there. Do you have

```
127.0.0.1	localhost
127.0.1.1	CRONUS
```

lines in your /etc/hosts file?

---

### Post by adamogardner on 2008-07-24
it always says that about host not found.  here's what it says:

127.0.0.1       localhost
127.0.1.1       CRONOS

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Vivaldi Gloria on 2008-07-24
> **adamogardner said:**
> it always says that about host not found.  here's what it says:

127.0.0.1       localhost
127.0.1.1       CRONOS

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

That looks fine to me. Weird. Don't know why you get that error. 

Other than getting that error does everything work OK?

---

### Post by adamogardner on 2008-07-24
no everything is in ruins.  and I need a job.  I can almost remember when this started, and that something happened preceeding it, but I can't remember what.  I was so overwhelmed at the time and since everything worked fine regarding that error, I let it go.  I would like now to know how to look into this more deeply if you have any ideas.

and to stay the course, I did install gnaural.  how can I check?  It's not in synaptic.

---

### Post by Vivaldi Gloria on 2008-07-24
Also let me recap the two ways of searching in the cli. find and locate.

locate uses a prebuild database of files to search. So it is a lot more faster. To build and update the db use the command

```
sudo updatedb
```

It's easy to use:

```
locate file
```

On the other hand, the command "find" does a live search. 

```
find <where_to_search> -name <what_to_search>
```

Note that find automatically searches the subfolders. Some examples:

```
find ~ -name "*.pdf"
sudo find / -name "menu.lst"
find . -name "v*"
```

The first one finds pdf files in your home folder and its subfolders.

The second finds menu.lst in the whole system (/ and subfolders). I used sudo because you need root rights to look into system folders.

The third example finds the files starting with v in the current folder (which is .) and its subfolders.

You can use find and then execute commands on the results found. For example

```
find ~ -name "*.backup" -exec rm -f {} \;
```

find all the files ending with "backup" and deletes them. Here the results found are subtitued in {} and \; just ends the command.

---

### Post by ApOgEEs on 2008-07-24
> **adamogardner said:**
> Apogees,  I followed your directions and nothing really happened as you can see:  

adamogardner@CRONUS:~$ locate gnaural
adamogardner@CRONUS:~$ sudo updatedb
sudo: unable to resolve host CRONUS
[sudo] password for adamogardner: 
adamogardner@CRONUS:~$ locate gnaural
adamogardner@CRONUS:~$



So, if your locate program is woking fine, it possibly means that you don't have any file or directory named as gnaural. You may verify this by trying to search for file that you're pretty sure is exists in your computer. for example, by searching for files or directory named as "updatedb" itself:

```
apogee@apogee-ubuntu:~$ locate updatedb
/usr/share/man/man1/updatedb.notslocate.1.gz
/usr/share/man/man1/updatedb.1.gz
/usr/bin/updatedb.notslocate
/usr/bin/updatedb
/etc/updatedb.conf
apogee@apogee-ubuntu:~$ 

```

or else, you may have another issue on your system.

---

### Post by Vivaldi Gloria on 2008-07-24
> **adamogardner said:**
> no everything is in ruins.

Sorry to hear that mate. Hope things get better.

> **adamogardner said:**
>  I would like now to know how to look into this more deeply if you have any ideas.

Not really. How about starting a new thread for it.

> **adamogardner said:**
>  and to stay the course, I did install gnaural.  how can I check?  It's not in synaptic.

Our posts crossed above. I posted without reading your post.

I searched "gnaural" in

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

It's available in feisty & gutsy repos but it is not in hardy repos. You can try downloading from its web page. May be the gutsy version can work also on hardy:

[http://packages.ubuntu.com/gutsy/gnaural](http://packages.ubuntu.com/gutsy/gnaural)

In general, to search for a package in the repos use the command

```
apt-cache search -n <package_name>
```

And to see if it's installed use

```
dpkg --status <package_name>
```

---

