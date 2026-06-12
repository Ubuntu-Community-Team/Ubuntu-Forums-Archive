---
title: "Howto Easily run an Xserver under Windows"
date: 2006-07-30
forum: Outdated Tutorials &amp; Tips
---

### Post by topgi on 2006-07-30
Sometimes, you need to connect from Windows to a Unix or Linux system just to run a specific software. For example, if you want to run some Linux open source program under windows and you have a Linux machine in your network or accessible from the Internet, there is an easy way to do it: Xming.

Xming is a open source X server that runs under windows, easy to install and use. Just go to the homepage: [http://freedesktop.org/wiki/Xming](http://freedesktop.org/wiki/Xming).

The installation is pretty forward. Once installed, the easiest way to use is to run it straight away. You have an X icon on your windows desktop, run it.

Then you need a remote terminal connection software, the best open source is Putty.
It is an executable, just download it and lunch it. Depending from the remote terminal service that is running on your server, configure Putty to use it. I suggest OpenSSH. You have also to configure the X11 Forwarding setting in Putty to forward the X session to your windows machine IP address. Done.

You will get a console, login in on your Linux server and lunch the application you want. Magically, it will appear on your windows desktop. I use this method to run application like Kivio (no need to buy Visio ) or other good open source that I will mention in other articles, on my office notebook when I am at home. The server is my Linux machine.

I repeat the instruction:

1) Install under Windows Xming and Putty

2) Have a terminal server running under Linux, like OpenSSH

3) Execute Xming under windows: double click the X icon

4) Execute Putty: configure it to connect your server Ip and to forward the X11 to your Windows machine IP.

5) Login and run the Linux application.

Here the website where you can find this and other usefull article: [http://ubuntufriends.wordpress.com/]("http://ubuntufriends.wordpress.com/")

---

### Post by lazyart on 2006-11-11
I'm going to append to this as I had a few issues and headaches before finding a solution that worked for me.

Get Putty [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) and
Xming [http://prdownloads.sourceforge.net/xming/Xming-6-9-0-21-setup.exe?download](http://prdownloads.sourceforge.net/xming/Xming-6-9-0-21-setup.exe?download)

Note, both of these applications are "portable" and can be copied to a thumbdrive and run on any machine you may have access to.

Launch Xming and select the style you wish to display the X server output.  Hint: Select Multiple Windows and your X applications will look like they were launched from Windows.  Leave Display number set to 0
Click Next.  Select Start No Client and click Next.
On Server Options, check the box title Disable Server Control.  Leaving the box unchecked can give you an "unspecified protocol error" later down the road.
Click Next and save your configuration.  This will create a quick way to launch Xming later.

Once you see the X in the systray you can launch Putty.
Enter the address of the machine you are trying to connect to.  Be sure to select SSH as the protocol.

Now connect.  With luck you will be asked to log in.  Enter your credentials.
Now to actually forward the ports. There is an option in Putty for this but it never seems to work for me.. so I type:

DISPLAY=your.windows.ip.address:0.0
export DISPLAY

Subsitute the IP address of the windows machine you are running Putty on.  DISPLAY must be typed in uppercase!  If everything is going correctly your Ubuntu box will say nothing back when you enter these commands.

Now, the test. Type

xclock &

and an analog clock should appear.  Try

mozilla-firefox &

and your web browser should appear.  Looking for your email? Try

evolution &

or

mozilla-thunderbird &

Be sure to use the amperstand after each command so that you can launch multiple apps. Otherwise, the terminal "hold" the commands until the application is closed.

When you're done, type exit in Putty and it all goes away!

Neat thing is that the clipboard works and you can copy and paste from system to another.

You won't be able to see your desktop, so you'll have to know the names of the apps you want to run.  To see the desktop requires XDMCP, which is easy to set up but is NOT secure.

---

### Post by pichalsi on 2006-12-16
Wow cool i just tried this out of boredom and it works like a charm thanks both :)

---

### Post by stalefries on 2007-01-11
Bump for coolness.

---

### Post by newlinux on 2007-01-11
Yes, this has worked very nicely and easily on my home and work XP machines.

---

### Post by alibobar on 2007-01-24
I'm having trouble getting this to work.

I have X11forwarding enabled on my dapper install. But when I try the connection (ie xclock &) after a couple of minutes I get an error that there is no connection to the computer running xming.

---

### Post by totalnub on 2007-05-11
ok, i got this to work on my local network. but i really want to be able to access my machine from anywhere. i really need help with my router and configuring that pos. any help is greatly appreciated. :)

---

### Post by lazyart on 2007-05-16
SSH is port 22 and you might have to forward that from your router to the Ubuntu box.

You need a way to know you external IP address.  Create an accout at dyndns.org, install a dynamic dns client on a machine (windows or linux box, it doesnt matter, but only pick one) and you can find your machine by a name instead of a changing IP.

---

### Post by Gruelius on 2007-07-06
Never mind i figured it out!!

Anyway if you want to forward the X11 through putty (no need for typing Display) you first need to install xauth ( sudo apt-get install xauth ) then reconnect and it should work!

---

### Post by timcredible on 2007-07-06
agreed.  xming is great, i use it at work quite a bit.  putty is also great.  open source on windows - not something my work likes (can't figure out why they want to spend hundreds of dollars on reflection x when xming works better).

---

### Post by PaulHuffman on 2007-10-05
xming sounds cool, and I'm ready to try it out.  But since I've already paid for Reflection X and have Putty (longtime Solaris user, I can run applications from my Solaris box with that appname & trick) I thought I could get Reflection to work for me on Ubuntu.  But I must be missing a setting on the Ubuntu machine, something that allows remote logins.  I tried a few vnc solutions, like Krdc and Krfb, but couldn't get on.  Putty won't let me on either, just says connection refused.  Reflection X starts up the brown login screen, but says my username or password are the wrong case.    

Sometimes I think Solaris experience isn't much help to me.  I'm always a little disoriented on Ubuntu.

---

### Post by PaulHuffman on 2007-10-05
Incremental progress.   I did a apt-get install ssh on Ubuntu.   Now Ubuntu allows Putty to connect. And got Xming and have it waiting in the XP tray, but after defining DISPLAY and trying xclock &, I get   

[B]paul@paul-ESeries:~$ Xlib: connection to "161.217.20.31:0.0" refused by server
Xlib: No protocol specified

Error: Can't open display: 161.217.20.31:0.0[/B]

Reflection X still doesn't work

---

### Post by king3382 on 2007-10-16
now i am facing the same issue.
how to configure the x server is the key to this.
but i dunt know.
anybody know it?
kindly hope to post answer.
many thanks ahead.


> **PaulHuffman said:**
> Incremental progress.   I did a apt-get install ssh on Ubuntu.   Now Ubuntu allows Putty to connect. And got Xming and have it waiting in the XP tray, but after defining DISPLAY and trying xclock &, I get   

[B]paul@paul-ESeries:~$ Xlib: connection to "161.217.20.31:0.0" refused by server
Xlib: No protocol specified

Error: Can't open display: 161.217.20.31:0.0[/B]

Reflection X still doesn't work

---

### Post by PaulHuffman on 2007-10-16
I think I had to go to System>Preferences>Remote Access and allow other users to view my desktop.  Or maybe that was just for VNC. Xming now works for me to start apps like xclock from a ssh session,  but I haven't been able to view the whole desktop or Xming Launch to connect to Ubuntu with XDMCP or single window.

I think at this stage I also figured out I had to configure Putty to forward X connections to the local host: [http://www.zen6478.zen.co.uk/images/PuTTY4.png]("http://www.zen6478.zen.co.uk/images/PuTTY4.png")

---

### Post by PaulHuffman on 2007-10-17
I'm getting good results now with Xming. I start up Putty, log in to linix, set DISPLAY 161.217.20.21 (my local IP address of the XP machine) then export DISPLAY
gnome-session & 

However when I do this with Reflection X,  I get an X desktop but blank top and bottom bars.  Reflection calls them the "top expanded edge panel" and the "bottom expanded edge panel". What's up with that?  

But when I try an XDMCP connection with Xming or ReflectionX,  all I get is the gdmgreeter, then nothing or a little gray box.  Installing and fiddling with Firestarter to be sure the 6000 tcp ports are open didn't help and may have been a time waster.  Do I need to do something in Ubuntu to start a XDM service?

---

### Post by aleksys on 2008-01-09
This works great.
But I have a problem while trying to forward whole linux desktop to my Windows system.
How I am trying to do this:
1. Starting XLaunch (installed with Xming)
2. Selecting how Xming displays programs (do not select multiple windows, the you will not be able to enter host name which do you want to connect to)
3. Entering display number (by default it should be 10)
4. 'Open session via XDMCP'
5. Entering a hostname or IP addres,
clicking next...

after that a new window appears, with login and passwword prompt (single ubuntu logins screen), when login and passwd are entered, everything i see is default desktop color screen, nothing more.

any ideas?

thanks in advance

P.S. sorry for my english

---

### Post by PaulHuffman on 2008-01-10
I got the same results.  

But I didn't know until today that I couldn't log in remotely if I was already logged in with the same user locally.

---

### Post by opioid on 2008-05-01
Thanks for the screenie PaulHuffman, that did it.

---

### Post by earthmeLon on 2008-07-12
Don't try to run gui'd applications through a screen session :P

---

### Post by aleksys on 2008-08-03
Hi guys, 
It's been a while I posted my post here, and I see nobody posted any working solution here. But I found it. I don't remember where exactly, but turning off sounds worked for me. It should be somewhere in Administration, or something. Just turn it off, and you will see the magic :)

---

### Post by Windsurfer619 on 2008-08-04
Wouldn't it just be easier to install [http://www.andlinux.org/](http://www.andlinux.org/) ?

---

### Post by PaulHuffman on 2008-08-04
> **aleksys said:**
> Hi guys, 
It's been a while I posted my post here, and I see nobody posted any working solution here. But I found it. I don't remember where exactly, but turning off sounds worked for me. It should be somewhere in Administration, or something. Just turn it off, and you will see the magic :)

Turn the sound off on which, the Ubuntu system?

---

### Post by keithclark on 2008-10-01
Thanks for the straight forward instructions.  Works like a charm here.

Keith

---

