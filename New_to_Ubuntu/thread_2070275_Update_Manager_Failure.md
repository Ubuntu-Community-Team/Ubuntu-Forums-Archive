---
title: "Update Manager Failure"
date: 2012-10-12
forum: New to Ubuntu
---

### Post by blueschord on 2012-10-12
I've been using the current version of Ubuntu (with great pleasure)for a while now, but this is my first problem (and hence my first post). 

My problem is that Update Manager downloads 84 updates (at last count)  - including new versions of Chrome & Thunderbird.  When I try to install them, it runs for a while and then I get this message:

[I]installArchives() failed: dpkg: error: parsing file '/var/lib/dpkg/available' near line 0: 
 field name `../../../help-langpack/software-center/ca/software-center.xml' must be followed by colon 
Error in function: [/I]

I haven't been able to find this exact problem on the forum and wd be very grateful if someone can help me sort this out.

Many thanks

---

### Post by grahammechanical on 2012-10-12
Hi and welcome to the forum.

Please explain what you mean when you say:

> When I try to install them,

Usually, Update Manager downloads the updates and installs them for us. It is a 3 part process.

1) The package lists are updated to identify which packages need to be downloaded because they have been updated.

2) The updated packages are downloaded.

3) The downloaded packages are installed with the out of date packages being removed.

It seems to me that one of the files in the package lists has not been correctly formatted.

You can open a terminal and run these two commands and then tell us what error messages you see.


```
sudo apt-get update
```

```
sudo apt-get upgrade
```

You will need to put your password in for these commands to run

Regards.

---

### Post by blueschord on 2012-10-12
Thanks for your reply.  By "when I try to install", after download, it tells me how many updates have been downloaded and the size.  There is also a button which says "Install" which I then click.

Anyway, did what you suggested and this is the response:


Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/available' near line 0:
 field name `../../../help-langpack/software-center/ca/software-center.xml' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by mmtrt on 2012-10-12
hi, try these commands.


sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install


if that did'nt helps solving your problem, or try this method,


sudo dpkg --configure -a

and

sudo apt-get install -f

if the problem of a broken package still exist the solution is to edit the dpkg status file manually.

sudo gedit /var/lib/dpkg/status  

Locate the corrupt package, and remove the whole block of information about it and save the file.

---

### Post by blueschord on 2012-10-14
[FONT="Arial"]Thanks again.  I followed your instructions and failed again (I fear I'm not up to the editing task.  I just made things worse, I suspect.)
Update manager is now telling me:

[I]An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'[/FONT][/I]

I'm wondering if I should wait until Quetzal and do a clean install.  I'm dual booting with XP (Ubuntu on its own disk).

Thanks again

---

### Post by Bashing-om on 2012-10-14
blueschord;
 It is a process of learning. To become the complete master of your machine, editing is required.

In This particular circumstance rather than editing, I suggest we move the corrupted database files out of the way and generate new ones thusly:
terminal commands, copy/past -one-at-a-time-:
```

1. mv /var/lib/dpkg/info /var/lib/dpkg/info_old
2. mkdir /var/lib/dpkg/info
3. sudo apt-get update
4. sudo apt-get -f install
5. mv /var/lib/dpkg/info/* /var/lib/dpkg/info_old/
6. rm -f /var/lib/dpkg/info
7. mv -f /var/lib/dpkg/info_old /var/lib/dpkg/info

```never ever do a "rm" command with out fully understanding what results

after the above is completed .....reboot
then in terminal do:
```
sudo apt-get update
sudo apt-get upgrade
```advise if any errors generated at this point, all I expect to be good ! 
[INDENT]just try'n to help <==BDQ

[/INDENT]

---

