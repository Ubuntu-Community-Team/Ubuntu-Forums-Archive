---
title: "HOWTO: Server Side VNC Client"
date: 2005-12-23
forum: Outdated Tutorials &amp; Tips
---

### Post by dragonfyre13 on 2005-12-23
After 19 grueling hours trying to set up a VNC Client that resides on my VNC Server, here it is.

I was looking for a Java Based VNC Client, that someone could simply connect to through my existing apache web server, and enter the password. Then, they could browse the machine just like a normal VNC connection.

I thought all I had to do was apt-get the tightvnc-java package. Nope. Wouldn't give me a web interface. Besides, I wanted it integrated.

Here's how I did it.

Make sure that you have the universe repository enabled. [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Also make sure that you have the correct plugins for your browser, if you are going to be testing it on the same machine. (that means you need the java plugin for Firefox, for most of you.)

**1. INSTALL APACHE (If not already done)**

If you don't already have Apache installed, install it now.

*apt-get apache2*

That's easy, it comes all nice and configured, ready to go. Let's check the setup with the web browser. Just point it to 127.0.0.1 (Yep, "localhost" does just fine too) It should pop up with a screen that says  "apache2-default/" with a little folder in front of it. If it doesn't, try logging out, and then back in.

YAY! That worked! (If not, there is a nice tutorial on how to install apache at [http://www.ubuntuguide.org/#apachehttpserver](http://www.ubuntuguide.org/#apachehttpserver) that I used)

Now for our purposes, all we need is apache. We don't have to worry about any other parts other than the base installation. (IE. php, mysql, etc.)

**2. ACTIVATE REMOTE DESKTOP**

This is actually a VNC server that comes shipped with Ubuntu, and since I am tailoring this to be simple, I thought I would use this instead of X11VNC. Intangible wrote a nice peice on installing and configuring X11VNC if you want to check it out.

To activate this, go to System -> Preferences -> Remote Desktop. Allow other Users to view and control your desktop, and MAKE SURE TO PUT IN PASSWORD PROTECTION!! Also, turn off asking for confirmation.

**3. DOWNLOAD AND INSTALL THE JAVA VNC VIEWER**

This is actually pretty simple too. I didn't use the repository, because I needed all the files in one place, ready for deployment.

Download this file to your home directory: 
[http://prdownloads.sourceforge.net/vnc-tight/tightvnc-1.2.9_javabin.tar.gz?download](http://prdownloads.sourceforge.net/vnc-tight/tightvnc-1.2.9_javabin.tar.gz?download)

(From [http://www.tightvnc.com](http://www.tightvnc.com) it's in the downloads section, under "Java
(viewer only)" and the package you want is the tar.gz of the binary format downloads)

*sudo file-roller /home/user/tightvnc-1.2.9_javabin.tar.gz*
(replace "user" with your user name)

extract everything to /var/www

*sudo gedit /var/www/index.html*

Delete all of the file, and replace it with this slightly modified version.

```

<HTML>
<TITLE>
TightVNC desktop
</TITLE>
<APPLET CODE=VncViewer.class CODEBASE=classes/ WIDTH=800 HEIGHT=632>
<param name=PORT value=5900>
<param name="Open New Window" value="yes">
</APPLET>
<BR>
<A href="http://www.tightvnc.com/">TightVNC site</A>
</HTML>

```

Save it.

**4. TRY IT OUT!**

go to a browser, and go through the same steps as you did to check the apache server. It should pop up with a java window this time! That's your client! Feel free to type in your password, and give it a go, from another machine. (Bad things happen when you connect to the local computer, and share the same screen.)

To connect from a remote computer, get your IP address, ( [http://www.whatsmyip.com/](http://www.whatsmyip.com/) ) and go type it into another computer's browser.  If that computer is on your network, you need your "Private IP" which you can get from typing *ifconfig* into the browser.

Have Fun!

---

### Post by chenel on 2006-01-03
One piece of wisdom I stumbled across -- the TightVNC Java client doesn't necessarily automatically open a new window for the display; sometimes it stays embedded in the web page.  To force it to open a new window every time, add the following line to the **index.html** file (step 3):
```

<APPLET CODE=VncViewer.class CODEBASE=classes/ WIDTH=800 HEIGHT=632>
<param name=PORT value=5900>
[COLOR="Red"]<param name="Open New Window" value="yes">[/COLOR]
</APPLET>

```

-Jeremy

---

### Post by Granduke on 2006-01-03
[QUOTE=dragonfyre13] Before using this example, make sure the
     value of the PORT parameter is set correctly (normally, the port number
     is 5900 + display number).
[/QUOTE]

What is this display number you are speaking of?

thanks.

---

### Post by dragonfyre13 on 2006-01-04
That's just an example script. I'm editing it right now to reflect a few changes to make it even easier, and so you don't even have to worry about that.

---

### Post by dragonfyre13 on 2006-01-04
Thanks Chenel. I added it to the page's HTML.

---

### Post by chenel on 2006-01-04
Dragonfyre-

Do you have any idea if there are any VNC servers on Linux that have an embedded Java viewer like the Windows ones usually do?  I've hunted around a lot, and I haven't been able to find anything useful.  I'd rather do that than Apache (even though I'm using Apache for now) since I don't really need the extra overhead of running Apache exclusively for the VNC client download...

---

### Post by Granduke on 2006-01-04
Dragonfyre,

                  Thanks for the HOWTO.  Works great.

---

### Post by dragonfyre13 on 2006-01-04
[QUOTE=chenel]Dragonfyre-

Do you have any idea if there are any VNC servers on Linux that have an embedded Java viewer like the Windows ones usually do?  I've hunted around a lot, and I haven't been able to find anything useful.  I'd rather do that than Apache (even though I'm using Apache for now) since I don't really need the extra overhead of running Apache exclusively for the VNC client download...[/QUOTE]

I'll check around. i would assume there is, and it seems that there should be an easier way, but I haven't found it. Some of them boast that there is, but I can't get any of them to work.

---

### Post by chenel on 2006-01-04
[QUOTE=dragonfyre13]I'll check around. i would assume there is, and it seems that there should be an easier way, but I haven't found it. Some of them boast that there is, but I can't get any of them to work.[/QUOTE]

Let me know which ones make that claim--I'm willing to do some tinkering to see if I can get them to work!

Thanks.

---

### Post by dragonfyre13 on 2006-01-05
[QUOTE=chenel]Let me know which ones make that claim--I'm willing to do some tinkering to see if I can get them to work!

Thanks.[/QUOTE]

Well, tight VNC is one of them, I believe. I know hidden in the documentation X11VNC says something about it. If it helps, they seem to all say that if your VNC port is 5901, 5801 should be the port you dial into with a browser to get the VNC Java interface. I always get an "RPC 003:003" message when I dial in on 5901, and on 5801 I get nothing.

---

### Post by chenel on 2006-01-05
Thanks for the tip.  I discovered that it's actually really easy to do with x11vnc: you just put the Java .class and other associated files (including an "index.vnc" that's got the same content as your "index.html") in /usr/local/share/x11vnc/classes, then run x11vnc with the -http option.  So I know it works, and it works nicely.

By the way, while it's a bit easier to use the built-in VNC server (vino), x11vnc uses up a lot less processor time on my machine (~10-20%, vs. ~40-50% or more for vino).  It might be worth adding x11vnc to the howto in case people want to use it instead...

---

### Post by dragonfyre13 on 2006-01-05
[QUOTE=chenel]Thanks for the tip.  I discovered that it's actually really easy to do with x11vnc: you just put the Java .class and other associated files (including an "index.vnc" that's got the same content as your "index.html") in /usr/local/share/x11vnc/classes, then run x11vnc with the -http option.  So I know it works, and it works nicely.

By the way, while it's a bit easier to use the built-in VNC server (vino), x11vnc uses up a lot less processor time on my machine (~10-20%, vs. ~40-50% or more for vino).  It might be worth adding x11vnc to the howto in case people want to use it instead...[/QUOTE]


Good to know, and thanks for the tip about X11vnc. What port do you connect to for the client? I've got apache running, and tomcat, and ssh, and http-tunnel, and webmin, and a whole host of others. Right now I'm worried about whether I have a decent port open...

---

### Post by chenel on 2006-01-05
[QUOTE=dragonfyre13]What port do you connect to for the client? [/QUOTE]

By default it binds to 5800 + display number (so 5800 for me).  In reading another howto ([here]("http://ubuntuforums.org/showthread.php?t=45565")) I found a good way to set up x11vnc to start when a user logs into GDM, and this particular script stores the port that vnc is using to ~/.vnc/port.txt -- you might check it out.  Anyways, you might be able to set the port number, but I couldn't find any indication of that in a quick search.  However you said that you get nothing when you try port 5800 so hopefully it should be open.

**EDIT:** use "netstat" to see what ports are in use.

---

### Post by dragonfyre13 on 2006-01-05
[QUOTE=chenel]By default it binds to 5800 + display number (so 5800 for me).  In reading another howto ([here]("http://ubuntuforums.org/showthread.php?t=45565")) I found a good way to set up x11vnc to start when a user logs into GDM, and this particular script stores the port that vnc is using to ~/.vnc/port.txt -- you might check it out.  Anyways, you might be able to set the port number, but I couldn't find any indication of that in a quick search.  However you said that you get nothing when you try port 5800 so hopefully it should be open.

**EDIT:** use "netstat" to see what ports are in use.[/QUOTE]


Yeah, I tried netstat, and tried the tutorial that you pointed to. I've actually got x11vnc running right now, because I followed that tutorial. Problem is, I didn't know to copy the files over, and so I got nothing when I dialed in to port 5800. Oh, and you can set the VNC port with one of the command line commands. I had it at 443 for a while. I can dig the command up if you want it.

---

### Post by chenel on 2006-01-05
I think you can also leave the files wherever you want them, and use x11vnc -http-dir=[directory you specify], if that's more convenient.

Does it work now?

---

### Post by sciurus on 2006-01-05
> I was looking for a Java Based VNC Client, that someone could simply connect to through my existing apache web server

Please note that if you don't have this requirement it is much easier install vncserver and vnc-java. You can connect to the vncserver at [http://*your-ip](http://*your-ip)*:580*x*, where x is the display number. You can have multiple vnc displays simultaneously if you so desire.

---

### Post by dragonfyre13 on 2006-01-06
[QUOTE=sciurus]Please note that if you don't have this requirement it is much easier install vncserver and vnc-java. You can connect to the vncserver at [http://*your-ip](http://*your-ip)*:580*x*, where x is the display number. You can have multiple vnc displays simultaneously if you so desire.[/QUOTE]


Yes, but I was looking for a way to embed it in the already existing website. Actually, if you read the recent discussion, this is what we have been commenting on. The problem comes when you only have port 5900 enabled, or something similar.

---

### Post by dragonfyre13 on 2006-01-06
[QUOTE=chenel]I think you can also leave the files wherever you want them, and use x11vnc -http-dir=[directory you specify], if that's more convenient.

Does it work now?[/QUOTE]

Flawlessly :cool: 

Thanks. I'll have to file this away in Tomboy.

---

### Post by chenel on 2006-01-06
Sweet.  Glad it worked out for you.

---

### Post by hen3rz on 2006-01-16
This tutorial is amazing! thank you very much. I have been struggling to work out how to do this for so long.

You have saved me many painful hours!

---

### Post by dragonfyre13 on 2006-01-16
No problem. I had the same issue. That's why I put up the HowTo. ^_^

---

### Post by phyzome on 2006-02-10
[QUOTE=sciurus]Please note that if you don't have this requirement it is much easier install vncserver and vnc-java. You can connect to the vncserver at [http://*your-ip](http://*your-ip)*:580*x*, where x is the display number. You can have multiple vnc displays simultaneously if you so desire.[/QUOTE]

You know, I tried that and it didn't work.  Browser just stares at me blankly and goes, "What? I don't know what you're talking about."

---

### Post by dragonfyre13 on 2006-04-06
[QUOTE=phyzome]You know, I tried that and it didn't work.  Browser just stares at me blankly and goes, "What? I don't know what you're talking about."[/QUOTE]

I kow exactly what you are talking about. that is one of the reasons that I made this thread.

---

### Post by aaarg on 2006-04-09
first off thx for the how-to, worked great!

forgive me if this sounds silly, still new...is there a way to run this over ssh or some way to run this securely. i would like to be able to access my ubuntu machine from work without allowing my ISP (at home) to see that i am running a server (they suck and dont allow servers, but alas i am in the country with no other options.) 

i was thinking maybe i could run ssh over port 443 (just thinking, dont know if it will work or if they will be able to tell i am running a server.) any help/ideas/suggestions would be greatly appreciated!

---

### Post by dragonfyre13 on 2006-04-11
Well, if they don't allow servers, an SSH server is incredibly common, so it probably will flag that as well. You may want to look into FreeNX. Check out cosmopod.com for a free implementation, or you could just search the forums for the howto. FreeNX is actually much more secure, and doesn't get flagged as a server as often from what I hear.

Otherwise, there really isn't a way to do the java applet over ssh, so far as I know. There is a java ssh client that I have, however, that does the trick for me.

I grabbed it here. It's a free download, for personal use. It's also a java applet.

[http://www.appgate.com/products/80_MindTerm/](http://www.appgate.com/products/80_MindTerm/)

---

### Post by aaarg on 2006-04-15
thx for the tip dragonfyre....you are right about them flagging ssh...

that is why i am thinking if i run it on port 443....look like a https session with my gmail or some such...

what you think?

---

### Post by Greeface on 2006-04-15
Haha, awesome, thanks for the howto!  This also works in Mac OSX, by the way.

---

### Post by Wenakko on 2006-04-16
Thanks great HOWTO

But, I can only use it, if the server is running GNOME, I want to connect to it, when it's running Fluxbox. How that can be done :confused: If I connect to it when fluxbox is running, it just says something that connection refused or something, should I start the vino on fluxbox? How?


Thanks

---

### Post by dragonfyre13 on 2006-04-19
[QUOTE=aaarg]thx for the tip dragonfyre....you are right about them flagging ssh...

that is why i am thinking if i run it on port 443....look like a https session with my gmail or some such...

what you think?[/QUOTE]


It depends. If you have a transparent proxy at work, it should work pretty well. If you have a proxy server that requires you use proxy settings, it takes a bit more work. I havn't figured out how to do that yet.

I ran it on 443, and it worked well, but then they put something else in, and it died. Otherwise, I find it works fine.

---

### Post by Harold P on 2006-05-14
I know this a very old topic, but I absolutely love the tutorial, and the application! 

Thanks. :)

---

### Post by dragonfyre13 on 2006-05-26
No problem!

---

### Post by phsyk on 2006-10-23
i go to it... and it asks for password.  i type in the one i set at preferences... and it doesnt work.  Is there a diff password i have to use?

---

### Post by .t. on 2006-12-10
Bringing up an old thread with some healthy info. Remember, ignore my quotation marks (').
1. Make sure you have vnc-java installed.
2. In /etc/vnc.conf, uncomment the line beginning '# $vncClasses = ' by removing the hash.
3. Then change its value so it looks like '$vncClasses = "/usr/share/vnc-java";'
4. Restart vncserver
5. Point your browser to <server>:<port> where <port> is 5801 + display number (usually 1 or 0).

No more need for apache!

---

### Post by steampunk on 2007-02-26
So uhm, I realize that the VNC server actually works without having to touch the Remote Desktop settings (and also apparently without using Apache2). However, there is no way to change the password for me in either scenario. I've tried using vncpasswd to no avail. Some other threads have attempted to answer this question, but I've yet to see any solid fix.

How does one change the password for VNC from the command line in both of these scenarios?

Thanks for any help. :popcorn:

EDIT: Sorry, I should also say that vncpasswd appears to have successfully changed the password, but after restarting the vnc server, my login attempts fail.

---

### Post by steampunk on 2007-02-27
Heh, nevermind. They blocked 5900 here at work. I totally misread the error.  :lolflag:

---

### Post by Prometheus7 on 2007-07-30
Is there a way that I can setup vncserver up on port 8080? The computer I am on has an http proxy and only accepts connections on port 8080. If this would be possible then I could simply change the index.html to point to 8080 instead of 5900 and everything would work, right?

---

### Post by berre on 2007-12-13
Does there anybody know if it's possible to sign the jar (applet) provided with the vnc-java package and make a VNC connection to an IP on the same LAN of the web server?

---

### Post by berre on 2007-12-13
no sweat, found out how, passing host as parameter

---

### Post by jorwex on 2008-04-09
I'm trying to put this on my school's webspace, so it's not an apache server that I can control, but I feel like there should be a way to get this to work. 

However whenever I go to the page, it says  something like, 

"unable to connect to server: www.XXXXXXX.edu:5900"

where XXXXX is my school's student webspace website. Is there a way to get it to prompt you where you want it to connect to? I'd like to put my ip in there without it assuming i want to connect to the site that I have it hosted on :)

Thanks

---

### Post by chadlewis on 2008-04-13
Quick question. I've had this setup running on my server for a few months now. I'm looking to clean up some space, but I can't tell if I need java on the host, or if it's just needed on the client. Is it safe to uninstall java on the host without killing this setup?

Love the tutorial btw. It's been working great!

---

### Post by chadlewis on 2008-04-13
Anyone?

---

### Post by baerwin on 2008-07-03
I have followed all the steps to set this up and it works, however, it only works to connect from another computer on the same network that my vncserver is running.

When I try to connect from a machine that is outside of the network, the java applet pops up, i enter my password, I wait about 20-30 seconds, and then i get the error: Network error: could not connect to server: se.tricity.wsu.edu:5900

Does this have something to do with port forwarding maybe?  Thanks in advance.

---

### Post by djbon2112 on 2008-10-01
I'm wondering how to configure this for the particular situation I'm in.

I use ProxMox, which has a built-in host-based VNC to all its running clients. I find them at <proxmoxPC IP>:900x, where x is the machine number. Now, I have my management website set up on one of the virtual servers. How do I have it point to the proxmoxPC IP and its port, and not to the machine housing the webserver itself? I tried adding this line:

<param name=HOST value=[proxmoxPC IP]>

But I get this error whenever I connect:


Error: access denied (java.net.SocketPermission <proxmoxPC IP> connect,resolve

...even when I put in the correct password (to test it says the same thing if I put in a blatantly wrong password).

---

### Post by JT9161 on 2008-10-30
> **baerwin said:**
> I have followed all the steps to set this up and it works, however, it only works to connect from another computer on the same network that my vncserver is running.

When I try to connect from a machine that is outside of the network, the java applet pops up, i enter my password, I wait about 20-30 seconds, and then i get the error: Network error: could not connect to server: se.tricity.wsu.edu:5900

Does this have something to do with port forwarding maybe?  Thanks in advance.

I'm having the same issue, Have you had any luck with a normal client ?

---

### Post by mmetan on 2008-11-13
> **JT9161 said:**
> I'm having the same issue, Have you had any luck with a normal client ?

First of all thanx for this amazing guide... highly appreciated.

donno if its the same problem but im having trouble here too.

Im using Kubuntu 8.04... ive asked this in kubuntuforums by gicing this guide's link but noone replied, and followed this pretty guide... Only difference here is that the remote desktop application. There is another thing in kubuntu, i dont remember the name right now... 

The problem here is that the browser keeps me asking username and password. I ve even tried my root username and pasword but i cannot login... any ideas? 

any helps are highly appreciated guys... thanx.

---

### Post by SlickRick on 2008-11-14
Hey, I'm trying to connect to my computer via my psp using a portable vnc client. I've followed your guide but am not able to connect. It is possible because there are videos on youtube of people demonstrating that it works but no tutorials on how to set it up on Linux. Any help appreciated.

I managed to get it working easily on windows so I think it's on my computer is where I'm going wrong

---

