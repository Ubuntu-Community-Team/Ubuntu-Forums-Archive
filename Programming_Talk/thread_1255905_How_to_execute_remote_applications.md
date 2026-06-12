---
title: "How to execute remote applications?"
date: 2009-09-02
forum: Programming Talk
---

### Post by ana12 on 2009-09-02
Hi:

I am using Ubuntu9.04. 

In my **network** there are two machine in that one is with **Ubuntu9.04 O.S.** and another is **Windows OS**.

In** windows machine i have installed clipper programming language** and **write some clipper programs**.And now i want to **execute these program from my Ubuntu machine**.

I have installed wine also on my Ubuntu machine.

So, can any body help me to solve this problem?

Thank You.

---

### Post by zarthon on 2009-09-02
To run programs using wine, from the command line precede whatever you would enter into the windows prompt with "wine ".

@progstachen:~/sysimg$ wine --help
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit

Use a thumb drive or network sharing to copy the programs to the other computer. Install clipper on wine by running the setup using wine as descrobed above,  WINE may or many not support your windows clipper.

You might look at the FlagShip ide for Windows and Linux. [http://www.fship.com/](http://www.fship.com/)
It is commercial but they have a trial version.

You could rewrite your programs in python. ( shameless python plug)

---

### Post by ana12 on 2009-09-02
Hi:

I have already installed Clipper in Ubuntu using wine, but how to access the applications on remote
machine using command prompt(terminal)?




Thank You.

---

### Post by aeiah on 2009-09-02
either set up samba and use the samba path as part of your wine command, or access the remote location via ssh, depending on what you actually want to achieve.

---

### Post by zarthon on 2009-09-03
What is the status of your project?

Have you gotten a clipper program to run on wine? 

How would you execute them from another windows machine on the network?

I have written a few ideas out but I don't know if they pertain. Please describe what you want to accomplish in more detail.

To accomplish program execution cross platform you will need to use a standard or at least common network protocol. It is unclear if you want to execute these programs and view the results or if you are doing data processing in Linux and want to integrate this with your clipper programs. Regardless of what protocol you use you will have to properly configure any software firewalls running on the systems.
3 possible options are:

RDP ( Remote desktop protocol)
You can use rdesktop or krdc to use you windows comptuer from your Linux desktop. I use my windows laptop from my Linux workstation by using rdesktop. I like this solution much better than trying to get things working on wine. When i enter the command a window opens that displays my windows desktop from the laptop and i can use it as I please. 
You will need to configure your windows comptuer to allow remote desktop connections.
Due to limitations in non server versions of windows the machine will revert back to the login window while you are using the comptuer over rdesktop. Non-server versions of windows are made to support a single user at a time. 
rdesktop allows more control over the connection like the size of the desktop ( you can use it at any resolution reguardless of the windows system resolution) file sharing a local linux directory to the windows system, and how sound is treated.
Krdc is alot easier to use. You just pick it from the applications start menu in gnome or lauch it with KDE.

ODBC (Open Database Connectivity)
If the database is what must remain on the windows sytem you may be able to configure ODBC on your linux system, and configure an odbc data source on your windows system.

You could then run your clipper programs locally on wine and it would access the database on the windows comptuer. I'd try to get this running between two windows machines first. 

HTTP / CGI
It may be practical to write a cgi application in a scripting language like python, perl or php and use http to communicate over the network.
This link describes how cgi works:
[http://www.jmarshall.com/easy/cgi/](http://www.jmarshall.com/easy/cgi/)
I have not researched if clipper as an api to integrate with scripting languages. If there is one then the the scripting code would just execute the clipper program and return the results. The usual client for a cgi application is a web brower but you can also write scripts to act as clients. The script just imitates a web form post and then parses returned results.

---

