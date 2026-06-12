---
title: "Accessing Ubuntu machine from iMac"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by Penfold1971 on 2012-06-30
I have been directed to this page: [http://narnia.cs.ttu.edu/drupal/node/132](http://narnia.cs.ttu.edu/drupal/node/132)

I'd like to take things step-by-step with this, since I don't think I'm even at 'beginner' yet.

Firstly, if I only want to look at my Ubuntu machine from my iMac (not wanting to do it the other way around as well), is the iMac the 'client', and does the Ubuntu machine contain the SSH Server? Or is the U-machine itself the Server?

---

### Post by mapes12 on 2012-06-30
On the Ubu machine right click the folder you want the iMac to be able to access and enable "Sharing". You may need to reboot. Your iMac should then be able to see and access the shared folder in Finder>Go>Network

I have an Ubu laptop and a Macbook and it works for me this way.

I think in this configuration the Ubu is server and Mac the client.

---

### Post by sudodus on 2012-06-30
> **Penfold1971 said:**
> I have been directed to this page: [http://narnia.cs.ttu.edu/drupal/node/132](http://narnia.cs.ttu.edu/drupal/node/132)

I'd like to take things step-by-step with this, since I don't think I'm even at 'beginner' yet.

Firstly, if I only want to look at my Ubuntu machine from my iMac (not wanting to do it the other way around as well), is the iMac the 'client', and does the Ubuntu machine contain the SSH Server? Or is the U-machine itself the Server?

A simple method is described by *mapes12*.

Yes, you can install the SSH server into Ubuntu. See this link
[[COLOR="Red"]_https://help.ubuntu.com/10.04/serverguide/openssh-server.html_[/COLOR]]("https://help.ubuntu.com/10.04/serverguide/openssh-server.html")

Then you need winscp (or some similar software) in Windows and an ssh or sftp software in MacOS in order to log in and run programs or transfer files.

---

### Post by Penfold1971 on 2012-07-01
Thanks, *mapes12*. I'm not sure it's just  folder I'll be wanting to access. I want to control the Folding@home client on the Ubuntu machine.

---

### Post by Penfold1971 on 2012-07-01
> **sudodus said:**
> Yes, you can install the SSH server into Ubuntu. See this link
[[COLOR="Red"]_https://help.ubuntu.com/10.04/serverguide/openssh-server.html_[/COLOR]]("https://help.ubuntu.com/10.04/serverguide/openssh-server.html")

Then you need winscp (or some similar software) in Windows and an ssh or sftp software in MacOS in order to log in and run programs or transfer files.

Thanks. I should explain more.
I am going to use the Ubuntu machine exclusively for Folding@home. Eventually I want to disconnect the monitor, keyboard and mouse and take a look at progress with the F@H work units (being processed on the Ubuntu machine), from time to time, from my Intel iMac.

My understanding is that I use a Utility called X11 on the iMac, but it's the setting up of things on the Ubuntu machine that I have to get straight first.

Installing the ssh server looks straightforward. I can do that, but could you explain 'configuration' to me please?

---

### Post by mapes12 on 2012-07-01
Could you give a bit more detail what Folding@Home is please? I've got my Mac and Ubu machines on so I can replicate what you're after.

EDIT: > but could you explain 'configuration' to me please? I think I've just realised what you need to do. I've read the guide you're following and you need to make some changes to system files owned by root. For the first one you need to call up the file in a text editor with sudo permission. Go Applications>Terminal and cut n paste this: > gksu gedit /etc/ssh/ssh_configIt willask for your password. Make the changes then save the file and close it. The next one like this: > gksu gedit /etc/ssh/sshd_configmake the changes then save the file and close it. It then says to restart ssh. I don't know a command but simply restarting the Ubu machine should do the job.

Then go to the iMac and call up the X11 utility. Insert the commands into the xterm Terminal replacing with your real user name and the address of your Ubu box. If you want to use the Ubu box IP address to identify it in the command then right click your network adapter icon>Connection information and you will see the IP address. For example mine is 192.168.1.X where "X" is the final number for the machine in your local network.

The guide looks like a very efficient way to access an Ubu box via a Mac, with low network overhead.

---

### Post by Penfold1971 on 2012-07-01
Here's the concise description of Folding@home (fah):

"Folding@home is a distributed computing project for simulation of protein folding, computational drug design, and other molecular dynamics for disease research."

I have a fah client on my Ubuntu machine that crunches work units (WUs) sent from the Pande lab at Stanford University. Upon completion, results are sent back to Pande lab. Another WU is then sent to my machine, etc. The whole process is automatic, requiring no further action on my part. I can, however, view progress of the WU, pause it, or even stop it altogether should I wish. That is what I'd like to be able to do from my iMac, once my Ubuntu machine is headless (correct terminology?).

I might have taken a step too far already - see my next post.

---

### Post by Penfold1971 on 2012-07-01
So I opened a Terminal on my Ubuntu machine and used the command;

sudo apt-get install openssh-server

The result was:

[I]Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
    ssh-import-id
Suggested packages:
    rssh molly-guard openssh-blacklist-extra monkeysphere
The following NEW packages will be installed
    openssh-server ssh-import-id
0 upgraded, 2 newly installed, 0 to remove and 5 not upgraded
Need to get 345 kB of archives
After this operation, 881kB of additional disk space will be used.
Do you want to continue [Y/n]?[/I]

At this point I chose 'Y', after which I got the following:

[I]WARNING: The following packages cannot be authenticated!
    openssh-server  ssh-import-id
Install these packages without verification [y/N]?[/I]

I have left it like that at the moment. Cause for concern?

---

### Post by mapes12 on 2012-07-01
Thanks for the F@H clarification. Yep, you need something more than file sharing.

I think that by default the ssh client is part of the main Ubu distro. The way I installed ssh-server package is by installing the meta package like this: ```
sudo apt-get install ssh
```I didn't get the warning message you have. Another way to install it is by searching for **ssh** in Software Centre. You want the one that says (**metapackage)**. It then installs everything you need to follow the guide.

---

### Post by Penfold1971 on 2012-07-01
Yes, I read that the ssh client is already part of the Ubuntu installation.

Already things have got uncomfortably complicated (for me) - :confused:

What is the difference between these commands:

'sudo apt-get install openssh-server'

and

'sudo apt-get install ssh'   ?

---

### Post by mapes12 on 2012-07-01
I'll defer to others to fully answer that one but as far as I know the latter install is a metapackage. This checks your system to make sure you have the openssh-client and the openssh-server installed then adds the packages you don't currently have plus any dependency packages.

I installed > sudo apt-get install sshon another Ubu machine today so that I could connect to it via SSH from my main machine. The install went perfectly with no warning message.

---

### Post by Penfold1971 on 2012-07-01
OK, I've gone ahead and although I got the warning message again, I did the install. (I think.)

Can you tell me how to proceed from here?

---

### Post by mapes12 on 2012-07-01
Go back to post 6 and edit those files.

Not sure if it fits into your plans but this may be worth looking at: [http://www.teamviewer.com](http://www.teamviewer.com)

---

### Post by Penfold1971 on 2012-07-01
I don't know where to find the file /etc/ssh/ssh_config

I'm trying to go by the instructions here, by the way (which are probably easier to follow than I'm making them) :

[http://narnia.cs.ttu.edu/drupal/node/132](http://narnia.cs.ttu.edu/drupal/node/132)

I have to insert lines as indicated in the blue boxes, then do a Restart, as I understand it.

---

### Post by Penfold1971 on 2012-07-01
> **mapes12 said:**
> Go back to post 6 and edit those files.

Got it - thanks. I didn't see your reply! :oops:

---

### Post by Penfold1971 on 2012-07-01
I hope you're not getting too fed up with me and all this! It's very good of you to reply so often.

Where the chap says, "Make these lines be in that file", does he mean that I have to type them in as additional lines at the end?

---

### Post by mapes12 on 2012-07-01
> Where the chap says, "Make these lines be in that file", does he mean that I have to type them in as additional lines at the end?I'm not on my Ubu box right now but I did check earlier. What you need to look for is those lines already in the file and where the annotation is "no". Simply change it to "yes" for the respective lines. Save and close. I think you will find them at the top of the text but just look through all the text to locate them.

Make sure you type yes at exactly the same point in the file where no is i.e. start the "Y" for yes in the same space as where the "N" is for no.

His English isn't that good but I got the jist of what he means.

---

### Post by Penfold1971 on 2012-07-01
I think I did all that properly.

A couple of Restarts seemed to be needed to get the Desktop back again (low graphics mode on the first Restart).

Opened X11 on my iMac, then tried a couple of times to reproduce a version his command:

*ssh -X [email]user_name@the_server_IP_or_hostname.domain[/email]ame*

that would work.

It's the 'server IP' I couldn't get properly, I think. It could be that my setup is a bit awkward. I have three macs hooked up wirelessly to an AirPort Extreme Base Station (which is wired to the modem in the hall cupboard). The Ubu box is connected directly via Ethernet cable to the AEBS.

When I go into 'Network' on the Ubu box, it has a hardware address, an IP address, Subnet mask, Default route (presumably the AEBS) andDNS.

I did actually get the pinky/purple Ubu Desktop with the two files that are on it, on my iMAC'S Screen!

But the list of errors, warnings, fatals, and so on that appeared on the X11 terminal window were huge. At one point there is the message: *gnome-session[2355]: CRITICAL: We failed, but the fail whale is dead. Sorry....*

I'm assuming that the Ubu Desktop is GNOME?

I have saved the contents of that window, but it's probably best to call it a day for today - I'm beat. I'll return to it again tomorrow - or later if you or any other kind soul is still about.

Thanks for all your help this afternoon/evening.

---

### Post by Penfold1971 on 2012-07-01
I tried once more, late on, but same result. Got the Ubuntu 12.04 default Desktop along with the icons for two URLs that were already on the Desktop.

This is the content of the X11 window I had tried to use to connect from my iMac to the Ubu box:

[FONT="Courier New"][SIZE="2"]bash-3.2$ ssh -X xxx@xx.x.x.x
xxx@xx.x.x.x's password: 
Warning: untrusted X11 forwarding setup failed: xauth key data not generated
Warning: No xauth data; using fake authentication data for X11 forwarding.
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-26-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

Last login: Sun Jul  1 19:32:49 2012 from xxx-xxxxxs-imac.local
xxx@xxx-Z68MA-D2H-B3:~$ gnome-session
GNOME_KEYRING_CONTROL=/tmp/keyring-E12EjD
SSH_AUTH_SOCK=/tmp/keyring-E12EjD/ssh
GNOME_KEYRING_PID=3689
GNOME_KEYRING_CONTROL=/tmp/keyring-E12EjD
SSH_AUTH_SOCK=/tmp/keyring-E12EjD/ssh
GPG_AGENT_INFO=/tmp/keyring-E12EjD/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-E12EjD
SSH_AUTH_SOCK=/tmp/keyring-E12EjD/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-E12EjD
SSH_AUTH_SOCK=/tmp/keyring-E12EjD/ssh
GPG_AGENT_INFO=/tmp/keyring-E12EjD/gpg:0:1

(gnome-settings-daemon:3688): power-plugin-WARNING **: Unable to start power manager: RandR extension is not present

(gnome-settings-daemon:3688): color-plugin-WARNING **: Unable to start color manager: RandR extension is not present

(gnome-settings-daemon:3688): xrandr-plugin-WARNING **: Unable to start xrandr manager: RandR extension is not present
[1341179818,000,xklavier.c:xkl_engine_start_listen/]    The backend does not require manual layout management - but it is provided by the application

(gnome-settings-daemon:3688): keyboard-plugin-WARNING **: Failed to set the keyboard layouts: GDBus.Error:org.freedesktop.Accounts.Error.PermissionDenied: Not authorized

(gnome-settings-daemon:3688): clipboard-plugin-WARNING **: Clipboard manager is already running.
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
compiz (core) - Fatal: No composite extension
compiz (composite) - Error: initScreen failed
compiz (core) - Error: Couldn't activate plugin 'composite'
compiz (core) - Error: Plugin 'composite' not loaded.

compiz (core) - Error: InitPlugin 'opengl' failed
compiz (core) - Error: Couldn't activate plugin 'opengl'
compiz (core) - Error: Plugin 'composite' not loaded.

compiz (core) - Fatal: No composite extension
compiz (core) - Fatal: No composite extension
Initializing nautilus-gdu extension
gnome-session[3676]: WARNING: Child process 3706 was already dead.
gnome-session[3676]: WARNING: Application 'compiz.desktop' killed by signal
gnome-session[3676]: WARNING: App 'compiz.desktop' respawning too quickly
gnome-session[3676]: CRITICAL: We failed, but the fail whale is dead. Sorry..
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
compiz (core) - Fatal: No composite extension
compiz (composite) - Error: initScreen failed
compiz (core) - Error: Couldn't activate plugin 'composite'
compiz (core) - Error: Plugin 'composite' not loaded.

compiz (core) - Error: InitPlugin 'opengl' failed
compiz (core) - Error: Couldn't activate plugin 'opengl'
compiz (core) - Error: Plugin 'composite' not loaded.

compiz (core) - Fatal: No composite extension
compiz (core) - Fatal: No composite extension
gnome-session[3676]: WARNING: App 'compiz.desktop' respawning too quickly
gnome-session[3676]: WARNING: Application 'compiz.desktop' killed by signal
gnome-session[3676]: WARNING: App 'compiz.desktop' respawning too quickly
Failure: Module initalisation failed
^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[B^[[A^[[A[/SIZE][/FONT]

---

### Post by Penfold1971 on 2012-07-02
Just giving this thread a bump.

Looking at my last post, above, can anyone shed light on what I might have done wrong, or might need to do to get things right?

I seemed to be so close since I got the Ubuntu Desktop, but only that, on my iMac's screen.

What I want to be able to do is look into fahcontrol, the app/window that contains the details about (and which enables me to pause, stop etc.)  the current work unit from Folding@home.

_Edit:_ In the page I was using to guide me through this, ([http://narnia.cs.ttu.edu/drupal/node/132](http://narnia.cs.ttu.edu/drupal/node/132)) the author says "If your desktop is GNOME, then just type [in X11 window on my imac]: gnome-session '

Is my desktop GNOME? How will I know for sure?

---

### Post by sudodus on 2012-07-02
Do you need a graphics user interface via ssh for Folding@home?

If it is OK with a command line interface, it will be much easier to get it running. I suggest that you try that (not starting Nautilus or some GUI file manager but running bash commands and a text interface of Folding@home).

---

### Post by Penfold1971 on 2012-07-02
I personally really *would* need a GUI, yes. Much more preferable, less chance of me really messing things up than with cli.

It seemed from Forrest Sheng Bao's notes, and especially from his screenshot at the end, that I could simply get the window for fahcontrol that I normally use on the Ubu desktop.

I wonder if I made a slip putting the details in

ssh -X user_name@[COLOR="Red"]the server_IP_or_hostname.domainame[/COLOR]

---

### Post by sudodus on 2012-07-02
> **Penfold1971 said:**
> I personally really *would* need a GUI, yes. Much more preferable, less chance of me really messing things up than with cli.

It seemed from Forrest Sheng Bao's notes, and especially from his screenshot at the end, that I could simply get the window for fahcontrol that I normally use on the Ubu desktop.

I wonder if I made a slip putting the details in

ssh -X user_name@[COLOR="Red"]the server_IP_or_hostname.domainame[/COLOR]

To get a text ssh connection to a typical IP address in a home network behind a simple router try something like the following commands. Change the ip address to fit your server.

```
ssh penfold@192.168.0.2
``` and to add X graphics capability
```
ssh -X penfold@192.168.0.2
```

Please test if your basic text connection works, for example try some simple commands. 
```
ls -l
top
who
```
and then some simple graphics commands
```
xlogo
gnome-system-monitor
```

Do you get any response from any of those commands?

---

### Post by Penfold1971 on 2012-07-02
It was the second of those suggestions,

ssh -X [email]penfold@xxx.xxx[/email].x.x

that I was attempting. I don't really know what to put in after the @ symbol, I suspect. Where would I look to get the xxx.xxx.x.x details?

---

### Post by sudodus on 2012-07-02
If you have a router, log into it via your local area network (using a web browser) and look at its menus, or

from the computer that is now an SSH server, run the terminal command ```
ifconfig | grep "inet addr"
``` Probably it is an address starting with 192... (not 127... but it might be something else)

---

### Post by Penfold1971 on 2012-07-02
I ran that command on the Ubu machine, and got two lines back.

inet addr: 10.x.x.x  Bcast: 10.x.x.xxx  Mask: 255.xxx.xxx.x
inet addr: 127.x.x.x  Mask: 255.x.x.x

I tried:

ssh -X penfold@127.x.x.x

and got the message:

ssh: connect to host 127.x.x.x port 22: Connection refused

---

### Post by sudodus on 2012-07-02
> **Penfold1971 said:**
> I ran that command on the Ubu machine, and got two lines back.

inet addr: [COLOR="red"]10.x.x.x[/COLOR]  Bcast: 10.x.x.xxx  Mask: 255.xxx.xxx.x
inet addr: 127.x.x.x  Mask: 255.x.x.x

I tried:

ssh -X penfold@127.x.x.x

and got the message:

ssh: connect to host 127.x.x.x port 22: Connection refused
Try [COLOR="Red"]10.x.x.x[/COLOR]

---

### Post by Penfold1971 on 2012-07-02
Tried that and got:
[I]Warning: untrusted X11 forwarding setup failed: xauth key data not generated
Warning: No xauth data; using fake authentication data for X11 forwarding.
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-26-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

0 packages can be updated.
0 updates are security updates.

Last login: Sun Jul  1 22:51:28 2012 from penfolds-imac.local
penfold@penfold-XXXXX-XXX-XX[/I]

---

### Post by Penfold1971 on 2012-07-02
Is there anything inherently obstructing things with my network set up here?

As I mentioned, my iMac (along with a G4 fp iMac from 2002, and a G4 PowerBook) are connected wirelessly, to each other and the internet via an AirPort Extreme Base Station. The AEBS is connected directly to our modem.  The new Ubu machine is connected directly to the AEBS with an ethernet cable.

---

### Post by sudodus on 2012-07-02
> **Penfold1971 said:**
> Tried that and got:
[I]Warning: untrusted X11 forwarding setup failed: xauth key data not generated
Warning: No xauth data; using fake authentication data for X11 forwarding.
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-26-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

0 packages can be updated.
0 updates are security updates.

Last login: Sun Jul  1 22:51:28 2012 from penfolds-imac.local
penfold@penfold-XXXXX-XXX-XX[/I]

So you are logged in now and should be able to run some commands, for example those I suggested to try (in post # 23)
:KS

---

### Post by sudodus on 2012-07-02
> **Penfold1971 said:**
> Is there anything inherently obstructing things with my network set up here?

As I mentioned, my iMac (along with a G4 fp iMac from 2002, and a G4 PowerBook) are connected wirelessly, to each other and the internet via an AirPort Extreme Base Station. The AEBS is connected directly to our modem.  The new Ubu machine is connected directly to the AEBS with an ethernet cable.
If you want to raise the security level, read this link
[[COLOR="Red"]_https://help.ubuntu.com/community/SSH/OpenSSH/Configuring_[/COLOR]]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")

---

### Post by Penfold1971 on 2012-07-02
gnome-system-monitor brought up a window with tabs and info about the system on the Ubu machine. Great!

The X11 window returned:

[I]bash-3.2$ ssh -X penfold@10.x.x.x
penfold@10.x.x.x's password: 
Warning: untrusted X11 forwarding setup failed: xauth key data not generated
Warning: No xauth data; using fake authentication data for X11 forwarding.
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-26-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

0 packages can be updated.
0 updates are security updates.

Last login: Mon Jul  2 19:12:37 2012 from penfolds-imac.local
penfold@penfold-Z68MA-D2H-B3:~$ gnome-system-monitor

** (gnome-system-monitor:7362): WARNING **: SELinux was found but is not enabled.
[/I]

---

### Post by sudodus on 2012-07-02
> **Penfold1971 said:**
> gnome-system-monitor brought up a window with tabs and info about the system on the Ubu machine. Great!
...
Yes, now you have X graphics via SSH :-)

---

### Post by Penfold1971 on 2012-07-02
At present, then, I can get a window from my Ubu machine as long as I know what to ask for?

I have tried the command 'gnome-session', as described here: [http://narnia.cs.ttu.edu/drupal/node/132](http://narnia.cs.ttu.edu/drupal/node/132)

where he says "If your desktop is GNOME, then just type [FONT="Courier New"]gnome-session[/FONT]" and I should get the equivalent of the screenshot at the bottom of his page.

However that is when I get the huge readout as I pasted in post 19, indicating, among other things that 'the whale is dead'. :confused:

So far, I can get (a) the plain desktop along with the two icons I have put there, and (b) the system monitor window, as per your instruction.

This means, I suppose that I need to know how to get the Desktop with FAHControl open on it. Does the FAHControl window even have to be open?

I'm stabbing in the dark here.

---

### Post by sudodus on 2012-07-02
> **Penfold1971 said:**
> At present, then, I can get a window from my Ubu machine as long as I know what to ask for?

I have tried the command 'gnome-session', as described here: [http://narnia.cs.ttu.edu/drupal/node/132](http://narnia.cs.ttu.edu/drupal/node/132)

where he says "If your desktop is GNOME, then just type [FONT="Courier New"]gnome-session[/FONT]" and I should get the equivalent of the screenshot at the bottom of his page.

However that is when I get the huge readout as I pasted in post 19, indicating, among other things that 'the whale is dead'. :confused:

So far, I can get (a) the plain desktop along with the two icons I have put there, and (b) the system monitor window, as per your instruction.

This means, I suppose that I need to know how to get the Desktop with FAHControl open on it. Does the FAHControl window even have to be open?

I'm stabbing in the dark here.

Don't try to squeeze a whole desktop environment through SSH! Learn the commands instead, or get a menu list!

We can start with the most important ones:

- What do you really need to run via SSH?
- How do you run it now?

If I cannot help, I'm sure someone else will help us find those commands.

---

### Post by Penfold1971 on 2012-07-02
> **sudodus said:**
> Don't try to squeeze a whole desktop environment through SSH! Learn the commands instead, or get a menu list!

We can start with the most important ones:

- What do you really need to run via SSH?
- How do you run it now?

If I cannot help, I'm sure someone else will help us find those commands.

My priority is to be able to control the running of Folding@home, which runs currently on my Ubu machine, remotely from my iMac.

On the Ubu machine is a process (app?) called FAHControl. I can use that to pause or stop the FAHClient, which crunches the work units sent to the Ubu machine from the Folding@home servers at Stanford University.

I don't know whether I'm explaining this correctly. I'll check with the Folding@home people.

---

### Post by sudodus on 2012-07-02
> **Penfold1971 said:**
> My priority is to be able to control the running of Folding@home, which runs currently on my Ubu machine, remotely from my iMac.

On the Ubu machine is a process (app?) called FAHControl. I can use that to pause or stop the FAHClient, which crunches the work units sent to the Ubu machine from the Folding@home servers at Stanford University.

I don't know whether I'm explaining this correctly. I'll check with the Folding@home people.
My guess is that you can type ```
fahcontrol
``` or ```
fah-control
``` from the terminal (internally in your Ubu machine, or via SSH from another one). Otherwise check behind the launcher or menu entry, what command it is, or ask the people at Stanford!

---

### Post by Penfold1971 on 2012-07-03
How do I check "behind the launcher or menu entry'?

Am I right in guessing here that the system might know FAHControl by another name?

I've started asking questions on the Folding forum to do with things linux/Ubuntu, but nothing yet.

---

### Post by sudodus on 2012-07-03
> **Penfold1971 said:**
> How do I check "behind the launcher or menu entry'?

A launcher looks like a Windows shortcut icon on the Desktop. Right-click on it, and I think you will be able to edit it. Otherwise you can select it via for example ```
gedit launcher-name.desktop
``` if you have changed directory to where the launcher is.

I don't use Unity, so I don't know how to access the menu items in that environment (it's not like the old menu systems). In gnome you right-click on the menu system icon on the panel at the top of the screen, select edit menu and when you find the menu item, look at properties.

> 
Am I right in guessing here that the system might know FAHControl by another name?

Yes, sometimes the same, sometimes slightly different, sometimes totally different.
> 
I've started asking questions on the Folding forum to do with things linux/Ubuntu, but nothing yet.

---

### Post by mapes12 on 2012-07-04
> As I mentioned, my iMac (along with a G4 fp iMac from 2002, and a G4 PowerBook) are connected wirelessly, to each other and the internet via an AirPort Extreme Base Station. The AEBS is connected directly to our modem. The new Ubu machine is connected directly to the AEBS with an ethernet cable.I haven't got an AEBS but Googled **airport extreme ssh** and a range of HowTo's came back. So, it might be worth having a read of some of them and compare the settings you have in your Airport Admin Utility to double check that your AEBS is set up correctly for ssh.

---

### Post by Penfold1971 on 2012-07-04
I've got a lead on the FAH forums. I'll leave this thread for now, but try and get a summary posted when and if I get resolution - then I'll mark the thread 'Solved'.

---

### Post by sudodus on 2012-07-06
Have a look at the following thread [[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1939132_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1939132")

maybe the name is ***FahMon*** (the monitoring program for Folding@Home)

You should try also ```
fahmon
``` (lower case letters)

Otherwise, maybe you can post in his/her thread or try to send an Ubuntu Private Message to *Lifeboat*. Maybe you can start helping each other.

---

### Post by Penfold1971 on 2012-07-06
Thanks, sudodus.

I should have posted a summary of the resolution of all this stuff to do with F@H. I spent a few hours back-and-forthing with a couple of very clued-in guys on the F@H forums. I finally, in the wee small hours of Wednesday morning got a result.

The upshot is that I can monitor and control the F@H client on my Ubu machine from my iMac. It's a sweet setup.

In which Support Category or Community Discussion do you think I should post my summary? I'm probably not the only person who has tried to get this sort of F@H setup between an iMac and a Ubu machine.

---

### Post by sudodus on 2012-07-06
> **Penfold1971 said:**
> Thanks, sudodus.

I should have posted a summary of the resolution of all this stuff to do with F@H. I spent a few hours back-and-forthing with a couple of very clued-in guys on the F@H forums. I finally, in the wee small hours of Wednesday morning got a result.

The upshot is that I can monitor and control the F@H client on my Ubu machine from my iMac. It's a sweet setup.

In which Support Category or Community Discussion do you think I should post my summary? I'm probably not the only person who has tried to get this sort of F@H setup between an iMac and a Ubu machine.

Great, post it here in a final post :KS

and then click **Thread Tools** at the top of this page to mark this thread as SOLVED

If you want to, you can make a small **[COLOR="Red"]Ubuntu Wiki page[/COLOR]**. In that case of course post a link from here to that wiki page.

The Ubuntu Forums want wiki pages now instead of how-to threads. The advantage is that several people can contribute and it will be easier to edit to make it 'reader-friendly'.

---

### Post by Penfold1971 on 2012-07-06
To show how groggy I've got over the past days getting to grips with all of this, I honestly believed I'd marked this thread as solved ... until you suggested I should!  :lol:

I can certainly post a summary. I just looked at some of the Ubuntu wiki stuff - another whole new venture! I'd like to be able to contribute, for sure.

Summary to follow.

---

### Post by Penfold1971 on 2012-07-06
_Summary:_

Although the title of this thread is 'Accessing Ubuntu machine from iMac', my main aim was a lot narrower, namely to be able to monitor and control Folding@home running on the Ubuntu machine (the 'Umac') remotely from my Intel iMac.

The Umac ( OS: Ubuntu 12.04, 64-bit ) is a self-build dedicated to running F@H continuously. It has an Intel Core i7 2600k 3.4 GHz CPU, 4GB memory and a 60 GB SSD. This machine is connected directly via ethernet cable to an Apple AirPort Extreme Base Station, which is in turn connected by cable to our broadband modem. Both FAHClient v7.1.52 and FAHControl v7.1.52 are installed and running. They can be downloaded from [[COLOR="Red"]this page[/COLOR]]("https://fah-web.stanford.edu/projects/FAHClient/wiki/BetaRelease").

The iMac ( Mac OS X - 10.6.8 ) is a Core 2 Duo 2.4 GHz, 4 GB memory. It is connected wirelessly to the AEBS.

**[COLOR="Red"]A[/COLOR]** On the Umac, use FAHControl to configure FAHClient to allow remote control :

-  change the popup on the upper right to "Advanced"
-  select the client named "local" and click the "Configure" button
-  select the tab, "Remote Access". (All of the following are to be applied under this "Remote Access" tab.)
-  if required, set a simple password (**or leave blank - preferred**)
-  in "IP Address Restriction" set the "Allow" field to "127.0.0.1 10.0.0.0/8". (**Note**: there is a space between "127.0.0.1" and "10.0.0.0/8")
-  further down the page, in "Passwordless IP Address Restriction" make sure that the entries in the "Allow" and "Deny" fields are the same as those in the corresponding fields in "IP Address Restriction".
-  click the "Save" button
-  reboot the Umac machine

**[COLOR="Red"]B[/COLOR]** On the iMac download fah-installer_7.1.52_i386.mpkg.zip from [[COLOR="Red"]this page[/COLOR]]("https://fah-web.stanford.edu/projects/FAHClient/wiki/BetaRelease").

-  install only FAHControl. Deselect options to install FAHClient and FAHViewer.
-  in FAHControl, click the "Add" button near lower left
-  put the Umac&#8217;s hostname in "Name" field
-  put the hostname.local name in "Hostname or IP"
-  put whatever password was selected in **[COLOR="Red"]A[/COLOR]**, in "Password", (**or leave blank - preferred**)
-  click the "Save" button

FAHControl on the iMac is now set up to monitor and control FAHClient running on the Umac.

My heartfelt thanks go out to the kindly folk on the Folding@home forum who helped me with all of the above.

EDIT : I must also thank those of you who took the time to post replies here. My apologies for not including my thanks to you earlier!

---

