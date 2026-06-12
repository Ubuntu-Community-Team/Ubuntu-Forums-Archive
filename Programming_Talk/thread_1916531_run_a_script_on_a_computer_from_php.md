---
title: "run a script on a computer from php"
date: 2012-01-28
forum: Programming Talk
---

### Post by Paulair on 2012-01-28
Hi guys,

I'm unsuccessfully trying to execute a shell command from php. The goal is to switch on/off my music player of my computer/server via internet (with my phone for example). Here is what I would be able to do :

I have a very simple file "play.sh" :
```

xdotool key XF86AudioPlay;
echo "switched";

```if I run it ./play.sh, that works (music player switches on/off)

then I have an other very simple php file "play.php" :
```

<?php echo shell_exec("./play.sh"); ?>

```These two files are in the main folder of my server which is a partition of my computer. (I'm using lampp)

But when I'm going on localhost/play.php, I can see "switched" that showed me the sh file as been executed, but the sound doesn't turn off .

Does someone have an idea to do that ? Is it a configuration of apache..?

Thanks !


&#1055;&#1086;&#1083; &#1071;.

---

### Post by shymega on 2012-01-28
Hi,

For the PHP code for executing the play script, can you try using the full path of the script and report back?

By the way, VLC has a nice interface for web interface: [http://wiki.videolan.org/Documentation:Modules/http_intf](http://wiki.videolan.org/Documentation:Modules/http_intf)

Hope that helps.

--
sm

---

### Post by Paulair on 2012-01-28
Hi,

Thanks for replying !
You mean with the absolute path (from root folder)? With "/opt/lampp/.../play.sh", the result is the same. I see the string line but that has no effect..
I think that even if I installed the server on my computer, they are working very separately.. I mean the sound on the server seems no to be the same as the sound on my computer.. but how to combine them ? .. Some programs like VNC can do that (access to the system), or we can find several apps able to control your keyboard or mouse through the local network.. but I really don't know how they work.. :/

I'm gonna have a look on your page, but my goal is also to do it by myself if it's possible :p

&#1055;&#1086;&#1083; &#1071;.

---

### Post by SeijiSensei on 2012-01-28
Try using exec() instead of shell_exec().

---

### Post by Paulair on 2012-01-28
Also tried, but same effect.. :|

---

### Post by shymega on 2012-01-29
Hi,

Have you tried using system()? Might be worth a try?

Hope it goes well!

---

### Post by Paulair on 2012-01-29
Hi,

I just tried exec(), shell_exec(), passthru(), system(), .. the result is exactly the same.. :/
But that's weird, I'm not sure, but I think that what I run on my computer side is not the same than what I run on my server side. I mean that it's like the sound was turning on/off on the virtual server but had no link with the sound of my computer. That could be an explanation.. but then, how to execute a script on my computer from internet/my server..?

Thanks again ;)

---

### Post by Paulair on 2012-01-29
I found the problem !!!

This was a problem of www-data permission. To access to Window :0 , I had to authorize it with : 
```
xhost + local:www-data

```

Youpi ! 

Thanks for all your replies !

&#1055;&#1086;&#1083; &#1071;.

---

### Post by shymega on 2012-02-04
Glad to hear you got it sorted. :D

--
sm

---

