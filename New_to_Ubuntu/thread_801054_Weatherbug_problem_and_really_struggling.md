---
title: "Weatherbug problem and really struggling"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by drifter2502 on 2008-05-20
I downloaded WeatherBug for Linux I chose to run it and it ended up in Accessories. I tried to run in a terminal but to no avail.
Now I can,t even delete the icon in applications. I found the file in filesystems/etc and tried to run it from Permissions/allow excecuting but nothing happened. Now I have two dead files on the system. This WeatherBug and Realplayer and can,t get rid of either. I don,t want to give up on Ubuntu but things are getting difficult for me. If I search on Add/Remove it does not show up there either. Is there something missing ? Perhaps it needs some kind of support from somewhwere? As you can tell I am a struggling Newbie and need some easy `down to earth`guidance on this one. Any help or suggestion would be enlightening(I hope!) helpful.
I am not concerned about the Realplayer/delete. I through that in as well just to illustrate how frustrated I am at the moment!!
Thanks.I am running Wubi 8.04.

---

### Post by Ansible on 2008-05-20
Did you try searching in the synaptic package manager instead of Add/Remove?  If you downloaded and installed the program outside of the Add/Remove, then it won't show up there.  If you installed from a .deb file though, I think it might be in the package manager.

---

### Post by BDNiner on 2008-05-20
You should be able to remove the program by going to the terminal and using apt-get. Do you know the command that launches the program? that is the name of the program you should use when trying to use apt-get remove.

---

### Post by drifter2502 on 2008-05-20
Thank you #2&3. I managed to locate the file in Package Manager(that&#347; taught me a lot). It is in Status as installed(local or obselite).Think I will rid myself of it for now. Be greatful if you can tell me if this code is correct then...apt get.WeatherBug.   Or something similar ?
Just tried this and got this message...
tc3mc@tc3mc-laptop:~$ apt-get remove WeatherBug
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
tc3mc@tc3mc-laptop:~$ 
What&#347; are you root?

---

### Post by H.Callahan on 2008-05-20
To remove it, it should be:```
sudo apt-get remove WeatherBug
``` from the terminal.

---

### Post by BDNiner on 2008-05-20
Sorry for the imcomplete instructions, after inputting H.Callahn's command you will be asked for your user password and then the command will run. you should look at this link for help on super user.

[https://help.ubuntu.com/8.04/administrative/C/](https://help.ubuntu.com/8.04/administrative/C/)

---

### Post by drifter2502 on 2008-05-20
Done it!!! Marvelous!
P.S, It,s my long service wedding anniversary today so me and my wife will hold a toast for you two tonight!
My kindest regards to you.
I may be an `Old Duffer`but I,am faster than Vista. Thanks again.

---

### Post by Momof9Blessings on 2008-06-01
HI all,

I just put linux on my laptop yesterday....  a long story - is there a place for introductions?  :)

So I am trying to add Weatherbug - it is really hot here today - and I love my Weatherbug!!!  

I installed it - then I read I need to...

Ubuntu (GNOME users):

Add the word

weatherbug

to your sessions tool by Ctrl-F2 then typing gnome-session-properties .

Sooooooo  where do I find "Session tools" ?

Thank you,
Mom

---

### Post by HotShotDJ on 2008-06-01
I can't figure out why you want Weatherbug.  Does it provide something that the weather applet that comes with Ubuntu (part of the Clock panel applet) or the [Clear Weather Screenlet]("http://www.gnome-look.org/content/show.php/Clear+Weather+Screenlet?content=66609")?

---

### Post by HotShotDJ on 2008-06-01
> **Momof9Blessings said:**
> Sooooooo  where do I find "Session tools" ?Well... what I would do is press Ctrl+F2 and then type gnome-session-properties

EDIT:  ACK!!  Both the instructions you listed in your post AND what I typed is WRONG.  Use Alt+F2

---

### Post by Momof9Blessings on 2008-06-01
Thank you - I did not know that there was a weather applet.  I did set it up.  How do you get the callendar to close now?  :)

Will this give weather alerts, forcasts etc?  That is one great feature of weatherbug - and here in our area we have lots of severe weather....

HotShot - when I push ctrl F2 - nothing happens.....

Thank you,
Mom

---

### Post by HotShotDJ on 2008-06-01
> **Momof9Blessings said:**
> HotShot - when I push ctrl F2 - nothing happens.....To close the calendar, just click on the date in your panel again -- it operates like a toggle button.  And I realized my error right after my last post... see the edit. ;)

Mom of 9 Blessings!?!?!?!?  Please tell me your talking about kittens.  :)

---

### Post by Momof9Blessings on 2008-06-01
Thank you,

I actually found it by accidently clicking on it....  there are a lot of "new" things to get used to in linux.  My husband is talking about switching to linux - if he can either get DAZ to work in linux or a good equivalent.

Right now, I am just trying to get my computer back to what I had with windows....  wireless internet, my printers set up, a great graphics program etc.....

Mom

---

### Post by Momof9Blessings on 2008-06-01
No - we have 9 kids - 20y to 8 months - 5 girls and 4 boys....

---

### Post by HotShotDJ on 2008-06-01
> **Momof9Blessings said:**
> if he can either get DAZ to work in linux or a good equivalent.If you mean the 3D graphics software... have him take a look at [Blender]("http://www.blender.org")

---

### Post by odindio on 2009-09-28
I'm not sure what was shown here?  Did you just show someone how to remove weatherbug and they thanked you? I think they wanted to know how to get it to work?  There is no substitute.  That's the program people want.  If you don't know how to do something, just say it!

---

### Post by odindio on 2009-09-28
sorry I quess the one person wanted to know how to remove it.  The second person had not given up.  Obviously you don't use it therefore you don't understand why other weather apps are crap. WE want to use the app weatherbug WE want to use the app weatherbug WE want to use the app weatherbug WE want to use the app weatherbug  AND NOT IN WINDOWS(RIPOFF)

---

