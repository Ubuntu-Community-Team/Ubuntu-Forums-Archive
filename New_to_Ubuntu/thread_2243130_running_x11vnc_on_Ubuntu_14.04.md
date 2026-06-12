---
title: "running x11vnc on Ubuntu 14.04"
date: 2014-09-06
forum: New to Ubuntu
---

### Post by brian_gillette on 2014-09-06
New to ubunto. running version 14.04. I have been tearing my hair out trying to get a remote desktop or vnc system setup for use only on my local network. I am trying to run Ubunto 14.04 on a spare small server with no keyboard and monitor, so i want to setup a remote desktop or vnc server on it so i can remote into it on my local network. I have tried the built in remote desktop vino with no luck. everywhere i have read says x11vnc is the thing to use ..i have installed that ok,and have my ubuntu server to automatically log me in when it boots, and have x11vncserver setup in the autostart area. x11vnc is loading correctly when the server boots up and logs me in, and it displays a window indicating its running on port 5900.
HOWEVER, i cannot connect anything to it at all. I've tried Ultravnc and VNCViewer. I keep getting a host refused connection. Anyone have this up and running ok. I don't care about encryption/ssl or any password security as i am running this on my own local /internal network for "play" purposes to get familiar with Ubuntu and Linux. so i don't need or have any security setup or passwords for the vnc server or connections. I've tried to eliminate anything that might be causing an issue, but just can't figure it out!
I am thinking that it is one of the many configuration settings in x11vnc that i just don't have set correctly. However, i have gone through all the settings and played with different variations for about 2 days solid. can't get it.!
anyone else have this running ok? if so, could you tell me your configuration.

---

### Post by cariboo on 2014-09-08
It would be helpful if you gave us the error message you are getting, when trying to connect to the server. As an aside, I use ssh/sftp to administer my server. File management can be down through your regular file manager, and any configuration file changes can be made using a simple text editor.

---

### Post by henk7 on 2014-09-18
I am too having a problem using the viewer.  I used to get the same error message using krdc, it said the server closed the connection.  Later after starting both pc's that message changed to server not found and using port number 5901 I get "Disconnected: read (-1334841388: &#65533;&#65533;)".  I have tested both pc's on a loopback connection using 127.0.0.1 and I have succesfully connected both times.  When using vncviewer it opens up a window asking for the password and regardless whether I enter a password or not when I click OK it just closes the window.

---

