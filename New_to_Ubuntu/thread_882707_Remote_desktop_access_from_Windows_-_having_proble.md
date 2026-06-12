---
title: "Remote desktop access from Windows - having problems"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by anewguy on 2008-08-07
I followed a couple of links that had me install lamp, then install tightvnc.  The end result is that I was supposed to be able to have a Windows PC access and control my PC using a web browser on the Windows PC.

I have remote desktop enabled, and I copied the folder of unzipped tightvnc stuff to the /var/www folder as directed in one of the links.  This includes an index.html file that contains the following:

<!-- 
     index.html - an example HTML page for TightVNC Java viewer applet, to be
     used with a standalone Web server running on the same machine where the
     TightVNC server is running. Before using this example, please MAKE SURE
     to check the following:

     * the value of the PORT parameter should be set correctly (normally, the
       port number is 5900 + display number);

     * the CODE and ARCHIVE attributes of the <APPLET> tag should point to
       the correct directory (this example assumes that this page is in the
       same directory with .jar and .class files);

     * the WIDTH and HEIGHT attributes of the <APPLET> tag correspond to the
       actual desktop size on the server (height should be increased to leave
       enough space for the button panel).
-->

<HTML>
<TITLE>
TightVNC desktop
</TITLE>
<APPLET CODE="VncViewer.class" ARCHIVE="VncViewer.jar"
        WIDTH="800" HEIGHT="632">
<PARAM NAME="PORT" VALUE="5901">
</APPLET>
<BR>
<A href="http://www.tightvnc.com/">TightVNC site</A>
</HTML>

Since the class and jar files are in a subfolder, and the port I supposedly need to use is 5900, the file now looks like this:

<!-- 
     index.html - an example HTML page for TightVNC Java viewer applet, to be
     used with a standalone Web server running on the same machine where the
     TightVNC server is running. Before using this example, please MAKE SURE
     to check the following:

     * the value of the PORT parameter should be set correctly (normally, the
       port number is 5900 + display number);

     * the CODE and ARCHIVE attributes of the <APPLET> tag should point to
       the correct directory (this example assumes that this page is in the
       same directory with .jar and .class files);

     * the WIDTH and HEIGHT attributes of the <APPLET> tag correspond to the
       actual desktop size on the server (height should be increased to leave
       enough space for the button panel).
-->

<HTML>
<TITLE>
TightVNC desktop
</TITLE>
<APPLET CODE="/var/www/remotedesktop/classes/VncViewer.class" ARCHIVE="/var/www/remotedesktop/classes/VncViewer.jar"
        WIDTH="600" HEIGHT="500">
<PARAM NAME="PORT" VALUE="5900">
</APPLET>
<BR>
<A href="http://www.tightvnc.com/">TightVNC site</A>
</HTML>


When I do [http://192.168.1.2/remotedesktop](http://192.168.1.2/remotedesktop), it opens a window that says tightvnc, has a grey area followed by a link to [www.tightvnc.com](www.tightvnc.com).  It then says it is starting applet, then stops saying the applet was not initialized.  I end up with just the grey screen and the link - no copy of my desktop.

Can someone help me to get this working, and then tell me how someone from the internet needs to put in an address in order to get to my PC?  I am wireless and have set the router for port forwarding on port 5900 as directed for tightvnc, and port forwarding on port 80 as mentioned for lamp.  I have a password assigned, yet it never asks for the password and on the Linux side it never asks for permission to allow the user in.

When I just run applications/internet/remote desktop viewer I get the password box and also am asked to ok the user on the Linux side, but I get a messed up screen.

I have java installed and the plugin in firefox.  I have tried using ie4linux, but it asks to download java, does the download but never installs it, and I appear not to have java.  So I downloaded java separately and installed it using wine.  Java still does not show in ie4linux so I can't access from there.

Any help would be GREATLY appreciated!  This is all new to me so I have no idea if I've done everything correctly.  I really need this working before noon central time U.S. as a perspective employer wants to be sure they can get to my PC from Windows and run desktop applications if needed.

Thank you in advance!!  :)

---

### Post by anewguy on 2008-08-08
Well, it's so far beyond noon that I obviously don't need this for the particular time, but does anyone have any ideas on how to make this work?  It would appear there is something wrong with the java files included in tightvnc.

thanks

---

### Post by Mister.Vash on 2008-08-08
I think that those might need to be relative paths and not absolute paths
So the the base would be /var/www

So instead of:
<APPLET CODE="/var/www/remotedesktop/classes/VncViewer.class" ARCHIVE="/var/www/remotedesktop/classes/VncViewer.jar" WIDTH="600" HEIGHT="500">

I think it should be:
<APPLET CODE="remotedesktop/classes/VncViewer.class" ARCHIVE="remotedesktop/classes/VncViewer.jar" WIDTH="600" HEIGHT="500">


If that doesn't do it, the apache logs should hopefully provide more information.  If you can find the lines and post those, that would provide more insite as what happens when the server tries to load the files.

---

### Post by anewguy on 2008-08-08
When I first checked, the error log was saying that remotedesktop/remotedesktop/  did not exist.  This said to me it is already at the remotedesktop folder, so I changed it to just classes/ so it would point to the correct subfolder.  Still no change.  I deleted the error.log and error.log.2 files and tried again, but it didn't create a log file.  So, I untar'd one of the archived logs, copied it over as error.log, added a line for where my debugging should start, then restarted apache.  Now I get the following in the log:

[Fri Aug 08 18:04:01 2008] [notice] start my debugging here

[Fri Aug 08 18:12:08 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Fri Aug 08 20:38:39 2008] [error] [client 192.168.1.2] File does not exist: /var/www/favicon.ico
dave@dave-desktop:/var/log/apache2$ 


I've looked, and there is no such file in /var/www or in /var/www/remotedesktop or it's subfolders.  

Any ideas?

Thanks! :)

---

### Post by anewguy on 2008-08-09
I found a favicon.ico for Picasa in my wine folders so I copied it to the /var/www folder.  Got rid of that error message, but still getting applet not initialized.  Is there anything special for ownership, etc., of the folders/files in /var/www that I need to be aware of?

---

### Post by anewguy on 2008-08-09
Okay, I don't know what it wants for paths in the index.html file, so I copied everything from the classes subfolder to the remotedesktop folder.  Now that applet runs, but I get:

network error:  could not connect to server:192.168.1.2 

and a box to login again.

Please note I am NEVER asked to confirm someone wanting to use my desktop remotely either.

I have the index.html file set as follows now:

<!-- 
     index.html - an example HTML page for TightVNC Java viewer applet, to be
     used with a standalone Web server running on the same machine where the
     TightVNC server is running. Before using this example, please MAKE SURE
     to check the following:

     * the value of the PORT parameter should be set correctly (normally, the
       port number is 5900 + display number);

     * the CODE and ARCHIVE attributes of the <APPLET> tag should point to
       the correct directory (this example assumes that this page is in the
       same directory with .jar and .class files);

     * the WIDTH and HEIGHT attributes of the <APPLET> tag correspond to the
       actual desktop size on the server (height should be increased to leave
       enough space for the button panel).
-->

<HTML>
<TITLE>
TightVNC desktop
</TITLE>
<APPLET CODE="VncViewer.class" ARCHIVE="VncViewer.jar"
        WIDTH="600" HEIGHT="432">
<PARAM NAME="PORT" VALUE="5901">
</APPLET>
<BR>
<A href="http://www.tightvnc.com/">TightVNC site</A>
</HTML>


and I have the router port forwarding set for port 80, ports 5900 to 5905.

Can anyone help on this??

---

### Post by anewguy on 2008-08-09
OK, I changed the port to 5900 in the index.html file and now I can connect - asked for password, asked to ok remote access.  

One question, though:

There appears to be multiple copies of my desktop in that window.  I can only access the disconnect, etc., line in the first, but, for example, if I select "Options" I get 3 option boxes on my screen.

I don't know if this has something to do with connecting locally (I [http://192.168.1.2/remotedesktop](http://192.168.1.2/remotedesktop), which I don't image ever goes past the router.

How do I test this by forcing it to go "through the net"?

Thanks

---

