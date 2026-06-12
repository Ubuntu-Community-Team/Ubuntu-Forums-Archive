---
title: "No password or login field appears !!!"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by mamech on 2011-10-12
Hello
 
I have ubuntu maverick . I tried to log in, but the loading screen stops  and I hear the sound that is supposed to be accompanying the appearance  of login name and passoword window, but no window appears to write the  password in.
 

I got an advice that to press alt+ctrl+F1 then  to enter user name and password, then to write startx, but I got the  following error:

 
Xauth: creating new authority file /home/mostafa/.Xauthority
Fatal server error
Server is already active for display 0
          If this server is no longer running, remove /tmp/.X0-lock and start   
          again
Please consult the X.org Foundation support
    at _[U][http://wiki.x.org/](http://wiki.x.org/)_[/U]
    for help
 
ddxSigGiveUp: closing log
Invalid MIT - MAGIC-COOKIE-1 key giving up
xinit : Resources temporarily unavailable (errno 11): unable to connect to X server
xinit : no such process (errno 3): Server error
What should I do to solve this ?

---

### Post by collisionystm on 2011-10-12
Instead of startx

try 

sudo service gdm start

or

sudo /etc/init.d/gdm start

---

### Post by mamech on 2011-10-12
I tried both commands, and this was what I got:

"sudo service gdm start

start: Job is already running :gdm


sudo /etc/init.d/gdm start

Rather than invoking init script through /etc/init.d, use the service ( 8 ) utility, eg service gdm start since the script you are attempting to invoke has been converted to an Upstart job, you may also use start ( 8 ) utility, eg start gdm"



Any other suggestions?

---

### Post by vajorie on 2011-10-12
> 
I have ubuntu maverick . I tried to log in, but the loading screen stops
  

Is this a new install? If things were okay prior to this, what administrative actions (eg upgrading, updating, installing packages, changing settings etc) did you do prior to this happening? 

Anyway, the command you're looking for is

```
sudo service gdm restart
```

I'm thinking this will not solve your problem. If on every boot the login screen fails to appear, there is a problem with X, possibly poor driver support for your graphics driver. 

Try the above command. 

To try the other person's advice (using startx), see this link: [https://wiki.ubuntu.com/X/Troubleshooting/Other#Problem_may_be_caused_by_gdm.2BAC8-kdm](https://wiki.ubuntu.com/X/Troubleshooting/Other#Problem_may_be_caused_by_gdm.2BAC8-kdm) ("Problem may be caused by gdm/kdm")

If those don't fix the issue and if it's recurrent, you might want to open a new thread using the following: [https://wiki.ubuntuforum](https://wiki.ubuntuforum) .com/X/Troubleshooting/BlankScreen#Problem:__General_Black_Screen_Issue ("Problem: General Black Screen Issue")

---

### Post by mamech on 2011-10-13
> **vajorie said:**
> Is this a new install? If things were okay prior to this, what administrative actions (eg upgrading, updating, installing packages, changing settings etc) did you do prior to this happening? 

Actually this is not a new install. I remember that prior to this , I was trying to solve a problem of Java program , that does not find it dynamic libraries, so I remember that I used some command to modify the variable that points to folder of dyanmic libraries. I used command called export , but I do not remember what I did exactly.

May this have an effect on what is happining now?

> 

```
sudo service gdm restart
```I'm thinking this will not solve your problem. If on every boot the login screen fails to appear, there is a problem with X, possibly poor driver support for your graphics driver. 

Try the above command. 



I tried it, and it made me go to a black screen, with sound of starting up in back ground.

---

### Post by vajorie on 2011-10-14
> **mamech said:**
> Actually this is not a new install. I remember that prior to this , I was trying to solve a problem of Java program , that does not find it dynamic libraries, so I remember that I used some command to modify the variable that points to folder of dyanmic libraries. I used command called export , but I do not remember what I did exactly.


The export command would be reset after a reboot, so even if that broke things (and I don't think it would), a reboot would have fixed it (unless you changed some system files to make the change permanent). 

> 
I tried it, and it made me go to a black screen, with sound of starting up in back ground.

Did that long link in my previous post help at all? 

Also, I'm shooting into the dark but, try

```

sudo dpkg-reconfigure xserver-xorg
```

That reconfigures your desktop thingy (called the X server) and is not risky. But before trying that, take a look at your logs:

```

less /var/log/Xorg.0.log
```

go to the end of the file and look for lines that start with "WW" (means warning) and "EE" (means error), which might give you some hints as to what's going on... 

Also look at your system log for anything that seems out of the ordinary (eg phrases like "missing bla bla" etc)

```
less /var/log/syslog
```

To navigate in there (after issuing the command): 

up arrow scrolls up
down arrow scrolls down
page up, page down do what they are supposed to do
end key takes you to the end of the file
q gets you to exit the file and go back to the termial

if you get stuck in there, simply switch to the second terminal with ctrl+alt+f2.

---

