---
title: "Installing open office"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by jerryheavyarms on 2008-05-29
Hello!

Good day to everyone!:)

Im new to this forum and new to using LINUX so please bear with me.

A couple of days ago, I was able to install Ubuntu Studio 8.04 on an old machine - Pentium3 550Mhz, 3x128MB of RAM, and 8Gig of HD. I want to use this as a workstation, however I didnt't find Open office installed. I recently downloaded Open Office and from there I dont know how to install it?
Please help!

Thanks in advance! God bless to all:)

---

### Post by billgoldberg on 2008-05-29
I don't know ubuntu studio, it might be installed, but hidden.

Anyway, you don't need to go to a website and download an installer in ubuntu.

You just go to "add/remove" or "synaptic package manager" and search for openoffice.

After you selected the application and press "apply", openoffice will be downloaded and installed automatically.

But if you prefer, I can give you a terminal code that will do all of that.

```
sudo apt-get install openoffice.org
```

---

However on an what older machine, you could use some more light weight apps like abiword, gnumeric, ...

---

### Post by quelx on 2008-05-29
**System** > **Administration** > **Synaptic Package Manager**

enter your password and search for **openoffice.org-calc** (for the spreadsheets), **openoffice.org-writer** for the word processor, **openoffice.org-impress** for presentations.  Click the check box next to each and then **Apply**

---

### Post by jerryheavyarms on 2008-05-29
> **quelx said:**
> **System** > **Administration** > **Synaptic Package Manager**

enter your password and search for **openoffice.org-calc** (for the spreadsheets), **openoffice.org-writer** for the word processor, **openoffice.org-impress** for presentations.  Click the check box next to each and then **Apply**

Thank you all for the replies..
Ive tried doing the Synaptic Package Manager but after a few seconds, it terminates by itself.. Doesn't open..:(

But, again, thank you all..

---

### Post by jerryheavyarms on 2008-05-29
> **billgoldberg said:**
> I don't know ubuntu studio, it might be installed, but hidden.

But if you prefer, I can give you a terminal code that will do all of that.

```
sudo apt-get install openoffice.org
```

---

However on an what older machine, you could use some more light weight apps like abiword, gnumeric, ...


Hi Bill!

Ive tried the code but it says:

sudo: unable to resolve host ubuntustudio

What does this means?
Sorry for the inconvenience

---

### Post by quelx on 2008-05-29
> **jerryheavyarms said:**
> Thank you all for the replies..
Ive tried doing the Synaptic Package Manager but after a few seconds, it terminates by itself.. Doesn't open..:(

But, again, thank you all..

**billgoldberg**'s suggestion for the terminal should work then **Applications** > **Accessories** > **Terminal** then paste his code and (Enter)

---

### Post by FuturePilot on 2008-05-29
> **jerryheavyarms said:**
> Hi Bill!

Ive tried the code but it says:

sudo: unable to resolve host ubuntustudio

What does this means?
Sorry for the inconvenience

See this thread for the sudo error
[http://ubuntuforums.org/showthread.php?t=723361]("http://ubuntuforums.org/showthread.php?t=723361")

---

### Post by jerryheavyarms on 2008-05-29
Hi Futurepilot!

The thread you gave was helpful.
Sudo issues resolved.
But what if Im going to join this machine to a network.
Will the problem arise again? Thanks!:)

---

### Post by FuturePilot on 2008-05-29
No, it shouldn't.
and you're welcome! :)

---

### Post by jerryheavyarms on 2008-05-30
Thnak you again..

Hi Bill!
YOu mentioned lightweight apps, is there an app for spreadsheet other than calc?

Thanks!

---

### Post by jerryheavyarms on 2008-05-30
Still need help.. I still cannot install open office..

I downloaded it, save it in my desktop and extracted it there also..

I tried:

sudo apt-get install openoffice.org
sudo apt-get install <the whole package>
sudo apt-get install <the extracted file>

but still, it says:

E:   couldnt find package ....

help! 

Thank you very much..

---

### Post by Sef on 2008-05-30
> YOu mentioned lightweight apps, is there an app for spreadsheet other than calc?

Gnumeric, download it from Add/Remove. 

Applications > Add/Remove > Show: Change to 'All Available Applications' > search gnumeric. 

In Add/Remove, type in Open Office and see if it is marked.  

Idea: System > Prefences > Main Menu > Office > check to see that Open Office is checked.

---

### Post by jerryheavyarms on 2008-05-30
Ive seen gnumeric but our network uses a proxy sa evry time the pc would update it always post an error because it requires authentication.. How will i do it to connect to internet using my account in the proxy?

BTW thanks for the reply Mr.Sef:)

---

### Post by quelx on 2008-05-30
at a terminal window

```
export http_proxy=http://username:password@proxy:port
```

to make this system wide and survive reboots add it to the bottom (above **exit 0**) of **/etc/rc.local**

---

### Post by jerryheavyarms on 2008-05-31
Thank you all for the replies!:)

---

### Post by jerryheavyarms on 2008-06-09
Hello! Recently I reinstalled my Ubuntu Studio and got problems with regards to installing openoffice (again... sorry).
Ive followed this:
> **quelx said:**
> at a terminal window

```
export http_proxy=http://username:password@proxy:port
```

to make this system wide and survive reboots add it to the bottom (above **exit 0**) of **/etc/rc.local**

However, still got error message. This time its says:
Proxy authentication required..

How will i fix this..

Thanks again in advance!
And also thank you for your consideration..



Hello!


This is how I did it:

jerry@ubuntustudio:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
export http_proxy=http://jerry:********@XXX.X.XXX.X:3128
exit 0
jerry@ubuntustudio:~$ 

Do you find any errors?

---

