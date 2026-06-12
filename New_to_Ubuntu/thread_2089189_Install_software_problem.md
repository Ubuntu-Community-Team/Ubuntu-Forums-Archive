---
title: "Install software problem"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by littlewenwen on 2012-11-28
Dear All

I am trying to install a software from source code; however, after I unpack the the tar file, I did not see the usual Readme or INSTALL file. Here is what I got after unpacking:

```

anyconnect.desktop         license.txt   vpnagentd_init
AnyConnectLocalPolicy.xsd  manifesttool  vpndownloader
AnyConnectProfile.tmpl     pixmaps       vpn_install.sh
AnyConnectProfile.xsd      update.txt    VPNManifestClient.xml
libcrypto.so.0.9.8         vpn           vpnui
libssl.so.0.9.8            vpnagentd     vpn_uninstall.sh
```

How should I continue the installation? Thanks (by the way, the software is Cisco VPN provided by our school)

---

### Post by dannyboy79 on 2012-11-28
I would say you should run the file called vpn_install.sh

---

### Post by littlewenwen on 2012-11-28
Thanks.
I tried as you suggested, however I got a message saying that "Command not found"

---

### Post by audiomick on 2012-11-28
Hi. 
Got this
>  Installing the AnyConnect Client on a PC Running Linux

To install the AnyConnect client on a PC Running Linux, follow these steps:

Step 1 For Linux, the client files are contained in a tar/gz file. Unpack the archive with a tar command. For example:

tar xvzf AnyConnect-Linux-Release-2.0.0xxx.tar.gz


The files necessary for installation are placed in the folder ciscovpn.

Step 2 Change to the ciscovpn folder. As a root user, run the script named vpn_install.sh. For example:

[root@linuxhost]# cd ciscovpn

[root@linuxhost]# ./vpn_install.sh


The client installs in the directory /opt/cisco/vpn. This script also installs the daemon vpnagentd and sets it up as a service that is automatically started when the system boots.

After installing the client, you can start the client manually from the user interface with the Linux command /opt/cisco/vpn/bin/vpnui or with the client CLI command /opt/cisco/vpn/bin/vpn. 

from here
[http://www.cisco.com/en/US/docs/security/vpn_client/anyconnect/anyconnect20/administrative/guide/admin2.html]("http://www.cisco.com/en/US/docs/security/vpn_client/anyconnect/anyconnect20/administrative/guide/admin2.html")

after a spot of looking around on the cisco site. I have not had anything to do with that, but it looks  like the right instructions.

But: 
Those instructions assume you are logged in as root. You will need to use sudo.

In your last post, you reported the error "command not found". That means that you are not in the directory where the install script is, or the script isn't being seen as an executable. I suspect the former, as I can see the script in your list, an I think an .sh is automatically an executable. 

I will have a bit of a think about this and post again, if no-one comes in with better advice in the meantime.

---

### Post by audiomick on 2012-11-28
Ok, this bit
> The files necessary for installation are placed in the folder ciscovpn.

Is that the case? Is that what the folder is called where the files are?

Do you understand this bit?
> Step 2 Change to the ciscovpn folder. As a root user, run the script named vpn_install.sh. For example:

[root@linuxhost]# cd ciscovpn


As I said, those instructions are assuming you are logged in as root, which you wont be on a standard Ubuntu install, because the root account is disabled.

Your cursor will look like this
```
mick@mick-laptop:~$
```

With your computer name instead of "mick-laptop" and your user name instead of "mick".

Anyway, to run the script, you have to be "in" the directory where the files are.

You use the command cd to change where you are.

 The ~ on the end of your cursor indicates your are in your /home/user directory. The $ indicates you are a user without root privileges. The # in the instructions indicates that the user is root.

You can use the command ls to give you a list of what is in the directory that you are currently in. I find that useful for finding my way.

If I were in the ciscovpn directory which was at /home/user/ciscovpn my cursor would look like this
```
mick@mick-laptop:~/ciscovpn$ 
```

To get there, I had to do
```
cd ciscovpn
```

You have to be there, and then you can do
```
./vpn_install.sh
```
which should run the script for you.

---

### Post by littlewenwen on 2012-11-28
Thank you (I should have gone to Cisco web looking for instructions).

I tried following command:

```
littlewenwen@newuser1:/opt/cisco/vpn/bin$ vpnui
```

However I got the error message saying that "vpnui: command not found"

---

### Post by littlewenwen on 2012-11-28
I followed your instructions from Cisco and it did seem to work  (as I can see vpnui in directory /opt/cisco/vpn/bin

---

### Post by raja.genupula on 2012-11-28
> **littlewenwen said:**
> Thank you (I should have gone to Cisco web looking for instructions).

I tried following command:

```
littlewenwen@newuser1:/opt/cisco/vpn/bin$ vpnui
```However I got the error message saying that "vpnui: command not found"


Hi this information not enough for us to solve your issue . provide us the complete log of what you have done .

Thank you .

---

### Post by audiomick on 2012-11-28
> **littlewenwen said:**
> Thank you (I should have gone to Cisco web looking for instructions).

I tried following command:

```
littlewenwen@newuser1:/opt/cisco/vpn/bin$ vpnui
```

However I got the error message saying that "vpnui: command not found"

> **littlewenwen said:**
> I followed your instructions from Cisco and it did seem to work  (as I can see vpnui in directory /opt/cisco/vpn/bin

Ok, so you are moving along. That is good. I am at a bit of a loss as to why that didn't run. As far as I can see, you are in the right place and giving the right command. 

You could perhaps navigate to that file with the file manager, and right click on it to see it's properties. It needs to be marked as an executable. There is a tick box for that on the permissions tab, but you wont be able to change it as a normal user. You need an instance of the file manager with root privileges. You can start that with
```
gksudo nautilus
```

It is possible to check and change permissions with the terminal, of course, but I am not sure of how, so I wont give you any tips that might be wrong. I think you can even see it on the colour of the entry in the terminal if you do ls, but I am unsure of that too.

---

### Post by steeldriver on 2012-11-28
unless the install script adds /opt/cisco/vpn/bin to your PATH, you will need to tell the system where to find the executable (being in the same directory is not enough)

```
[COLOR=Red]**./**[/COLOR]vpnui
```It also needs to be (a) executable and (b) (if it is a binary file) compatible with your architecture (32 vs 64 bit)

... those are the usual gotchas

---

### Post by littlewenwen on 2012-11-28
Thank you for all your help.
 
unfortunately, my cmputer just crashed because of hard drive failure (DST short test failed);could it be because i installed two OS on the same computer (windws and ubuntu)?
 
Hopefully I can get another computer very soon so that I can continue my linux journey...

---

### Post by audiomick on 2012-11-28
> **littlewenwen said:**
> could it be because i installed two OS on the same computer (windws and ubuntu)?.

No, I've got two computers set up like that, and millions of other people have that setup too. Your drive has just had enough. If it is a laptop, maybe it has been knocked around too much.

Hope you get a replacement soon.

---

### Post by littlewenwen on 2012-11-28
(ok, I am now using another ubuntu computer to continue)

Here is the command I just ran:

```
littlewenwen@newuser1:/opt/cisco/vpn/bin$ ./vpnui
```

The program did start running and I saw the interface that asked for hostname, user and password; however, I got the following message:

```
littlewenwen@newuser1:/opt/cisco/vpn/bin$ ./vpnui
/opt/cisco/vpn/bin/vpndownloader: 1: /opt/cisco/vpn/bin/vpndownloader: Syntax error: "(" unexpected

gzip: stdin: unexpected end of file
```


What does this message mean?

---

### Post by littlewenwen on 2012-11-28
In addition, it seems the program continues running, and I could not get back to the shell prompt

---

### Post by audiomick on 2012-11-28
Hmmm, that is well beyond me. If I had to guess, I'd say that there is a corrupted file there somewhere, but I really don't know. You will have to wait for someone with a bit more experience on that. Sorry.

---

### Post by steeldriver on 2012-11-28
It probably means that vpndownloader is a shell script, and there's a command in it that the shell interpreter doesn't understand - without seeing the contents of the script it's hard to be more specific

IMO the most likely reason for that is that the script's author expected the system shell interpreter '/bin/sh' to be a Bourne shell, whereas in current Ubuntu distributions it links to a 'dash' shell

You can probably stop execution by pressing the Ctrl-C key combination

---

### Post by littlewenwen on 2012-11-28
Thank you.

But it seems that it IS working (as I now can connect to a server that has to be through VPN connection)

So, VPN connection is working; now how can I terminate the program and get back to the shell prompt?

What I mean is, currently it looks like:


```
littlewenwen@newuser1:/opt/cisco/vpn/bin$ ./vpnui /opt/cisco/vpn/bin/vpndownloader: 1: /opt/cisco/vpn/bin/vpndownloader: Syntax error: "(" unexpected  gzip: stdin: unexpected end of file
```

I want go back to 

```
littlewenwen@newuser1:/opt/cisco/vpn/bin$
```

---

### Post by littlewenwen on 2012-11-28
the Ctrl-C key combination does work!
Thank you all for great help!

---

