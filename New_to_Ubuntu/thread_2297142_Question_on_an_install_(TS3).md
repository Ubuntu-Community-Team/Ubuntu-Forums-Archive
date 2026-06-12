---
title: "Question on an install (TS3)"
date: 2015-10-01
forum: New to Ubuntu
---

### Post by eddiefiggie on 2015-10-01
More of an Unbuntu question than a Team Speak 3 (TS3) question.  I'll share the source information then ask the question.

Here's the guide I used to install TS3:  [http://robert.penz.name/296/howto-install-teamspeak-3-server-on-ubuntu-10-04-lucid/](http://robert.penz.name/296/howto-install-teamspeak-3-server-on-ubuntu-10-04-lucid/)

Now here's my question:

I learned in a previous thread that when a tilde "~" is used before a path it means it's referring to the users /home directory.  For example ~/bin would be the bin directory within someones /home/username/bin directory.  Please correct me if I'm wrong but that is how I understood it.  That was quite helpful as there are many /bin directories within the file tree.

Now for my question...

I read this:
> 
We move it to a nice place with


 ```
mv teamspeak3-server_linux-amd64 /opt/ts3


```


Now there is no tilde here "~" so I "ass-u-me" it means this is intended for the /opt (right off the root).  I'm currently confused as to when and why something would be installed out in the root area versus the /home area.  Is this to support multiple users on the machine?  Can someone validate my understanding?

Thanks as always.

---

### Post by howefield on 2015-10-01
> **eddiefiggie said:**
> Now there is no tilde here "~" so I "ass-u-me" it means this is intended for the /opt (right off the root).

Correct.

---

### Post by NathanRodriguez on 2015-10-01
True, you used an absolute path specified from filesystem root.

---

### Post by yancek on 2015-10-01
>  I'm currently confused as to when and why something would be installed out in the root area versus the /home area

Most software is not installed in a user /home directory but under the / of the system.  There are some configuration files in /home/user that are specific to the user but generally it is so the software is available system wide for users.

---

### Post by eddiefiggie on 2015-10-02
> **yancek said:**
> Most software is not installed in a user /home directory but under the / of the system.  There are some configuration files in /home/user that are specific to the user but generally it is so the software is available system wide for users.

With this particular application.  I downloaded a file called:

> TeamSpeak3-Clinet-linux_amd64-3.0.18.run

I believe I ran that file from the GUI through a file manager and it unpacked/installed (not sure of the difference within Linux), the content to my desktop, which is where I ran the file.

Ok, now this directory for TS3 is added to my desktop....  and I can run the *.sh file within the directory to launch the application. 

1) Can I move this directory with files (which include the *.sh file used to launch it all) some place else?  i.e. the /opt directory without breaking anything?

2) Where's my icon? hehe sorry, I'm used to Windows.  Are these files "installed" and shouldn't be moved?  I'd like a launcher icon that activates this application.

I'm so scurd!  =P  Again, this is less about TS3 as an application and more about understanding how Linux treats installed applications.  I'm quite confused by this but I'm sure the information is out there.

Thanks for any insight.

---

### Post by yancek on 2015-10-02
Usually when you download something like that it is extracted to another directory with the same/simlar name.  If the instructions (often a README file) tell you to move it to the /opt directory I expect it would work.  Obviously, you would then need to call it from there or create a launcher/desktop link to it to start.

---

### Post by eddiefiggie on 2015-10-02
> **yancek said:**
> or create a launcher/desktop link to it to start.


Found a link to help me with this.  Thanks so much for clearing that up.

[http://askubuntu.com/questions/64222/how-can-i-create-launchers-on-my-desktop](http://askubuntu.com/questions/64222/how-can-i-create-launchers-on-my-desktop)

---

