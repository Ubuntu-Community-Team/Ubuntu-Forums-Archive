---
title: "Group Seeting Or Security Issues"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by IcedDante on 2008-05-16
I don't know how all of this started, but I think I'm still dealing with issues that I posted in the thread:

[http://ubuntuforums.org/showthread.php?t=703998](http://ubuntuforums.org/showthread.php?t=703998)

The basic gist of it was that I was having user Groups problems, was unable to see several menu buttons like the Synaptic Package Manager, and I fixed this by running:
*usermod -a -G admin userNameHere*

This solved some of my access problems. I was, however, having a problem with no sound that I reported here:

[http://ubuntuforums.org/showthread.php?t=792090](http://ubuntuforums.org/showthread.php?t=792090) and was advised to add myself to the Sound group under the **User Privileges** tab of the **Users and Group** editor.

When I went to this tab- I found it empty for both myself and root. I don't know why this was, but I clicked on OK to leave this window, and I think that by doing so I inadvertently wiped out the groups that were there originally. After rebooting I get a bunch of ugly terminal output and no Ubuntu login window.

I tried repeating the usermod command and I now get the message:

The GDM group "gdm" does not exist. Please correct GDM configuration and restart GDM.

And I am redirected to the shell. Where should I go from here? If I type in groups for myself, I see only: root.

Thanks!

---

### Post by IcedDante on 2008-05-16
One question that I think might help get me started- is there a way to:

[LIST=1]
[*]See all available groups
[*]See which groups I belong to
[*]Add myself to these groups
[/LIST]

via the command line?

---

### Post by IcedDante on 2008-05-17
I've been researching this problem and came upon this thread:
**[http://ubuntuforums.org/showthread.php?t=462991](http://ubuntuforums.org/showthread.php?t=462991)**
Which seems to be of the same nature. I was somewhat disconcerted to see that they were unable to find a fix for it and that reinstalls were needed. :(

I'll check /etc/groups to see what is in there but any suggestions that people in the expert community could provide would be appreciated.

Holla.

---

### Post by IcedDante on 2008-05-17
More info yet:

I ran: cat /etc/group

and got only this for the output:
```

root :x :0 :
nogroup :x:65534 :

```

Please help, my friends: my machine is unusable!

---

### Post by IcedDante on 2008-05-19
Is it possible to rebuild my groups file? That might be the best way to go. Does someone have a template I can use?

---

### Post by IcedDante on 2008-05-19
> **IcedDante said:**
> 
The basic gist of it was that I was having user Groups problems, was unable to see several menu buttons like the Synaptic Package Manager, and I fixed this by running:
*usermod -a -G admin userNameHere*

This solved some of my access problems. I was, however, having a problem with no sound that I reported here:

[http://ubuntuforums.org/showthread.php?t=792090](http://ubuntuforums.org/showthread.php?t=792090) and was advised to add myself to the Sound group under the **User Privileges** tab of the **Users and Group** editor.

When I went to this tab- I found it empty for both myself and root. I don't know why this was, but I clicked on OK to leave this window, and I think that by doing so I inadvertently wiped out the groups that were there originally. After rebooting I get a bunch of ugly terminal output and no Ubuntu login window.

I tried repeating the usermod command and I now get the message:

The GDM group "gdm" does not exist. Please correct GDM configuration and restart GDM.

And I am redirected to the shell. Where should I go from here? If I type in groups for myself, I see only: root.

Thanks!

> **IcedDante said:**
> One question that I think might help get me started- is there a way to:

[LIST=1]
[*]See all available groups
[*]See which groups I belong to
[*]Add myself to these groups
[/LIST]

via the command line?

> **IcedDante said:**
> 
I ran: cat /etc/group

and got only this for the output:
```

root :x :0 :
nogroup :x:65534 :

```

Please help, my friends: my machine is unusable!

I was on the Ubuntu IRC channel and was informed that these problems might have been started by using sudo to run GUI applications (instead of gksudo) which was a valuable lesson learned. The one who told me about that did not have any information on how to fix my current problem. I am hoping *someone* here does.

I know these forums are a volunteer effort, but I have still received no reply (is my problem that dire or obtuse?) so I demand nothing but I ask that if you can provide any help or at least point me in the right direction that you do so.

Many thanks to y'all!

---

### Post by IcedDante on 2008-05-20
> **IcedDante said:**
> I was on the Ubuntu IRC channel and was informed that these problems might have been started by using sudo to run GUI applications (instead of gksudo) which was a valuable lesson learned. The one who told me about that did not have any information on how to fix my current problem. I am hoping *someone* here does.

Many thanks to y'all!

Someone on the IRC channel helped me out by suggesting I add the groups manually with 
```
sudo usermod -a -G ...
```
I tried this and I got **"unknown group"** for audio, lpadmin, admin, cdrom, etc... basically it looks like all my groups are gone!

When I  boot into recovery mode I also see these errors:
[B]chown: `root:utmp': invalid group
chown: `root:tty': invalid group
[/B]
Does anyone know how this could have happened and how I can fix it?

---

### Post by IcedDante on 2008-05-20
Alright. I'm going to take the hint here and abandon this thread. For any future users that experience this problem, know that I fixed it by getting someone else's group file and typing that into my /etc/group and rebooting.

The problem with this solution is that I have installed quite a few applications and I have no way of knowing if these come with groups that are now missing, nor what problems this may cause. If anyone has opinions on that- please feel free to post them here.

Holla!
iDante

---

