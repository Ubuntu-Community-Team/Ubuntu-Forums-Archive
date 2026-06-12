---
title: "[SOLVED] Synaptic manager wont load"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by naggis on 2008-05-11
Hi
When I attempt to open the Synaptic manager a notification opens at the bottom of the page saying "Starting administration", the wheel turns for about 15 - 20 seconds and then - nothing. The same happens when trying to open the Update manager.
Recently I have been trying to allow file sharing across a network with a windows pc. This got me into a bit of a pickle but I seemed to resolve it ok - but now Synaptic problems.
I have only been using Ubuntu for a few weeks and upgraded to Hardy 2 weeks ago.
Any help would be very welcome
Thanks

---

### Post by naggis on 2008-05-11
Is the answer to reinstall Hardy. If so, which is the easiest way to do this. I am concerned that if I just boot from the cd, the installation process may create more partitions and generally mess up the hard disk. Can I do a repair from the boot cd? What about an upgrade? I guess that upgrading is not on as the installation is fully up to date anyway.
As you can see, I need help

---

### Post by Taboo Mirage on 2008-05-11
Open a terminal and type this:
```
gksudo synaptic
```
Paste any error messages that appear in the terminal back here.

---

### Post by Cifra on 2008-05-11
Open a terminal and type 'sudo synaptic' andtry to open it. Show us the output of teh terminal

---

### Post by alienexplorers on 2008-05-11
If you renistall Hardy and have a /home directory setup just run the install CD and when you get to the section about setting up partitions just format the root partition and leave the /home partition unformatted.  This will hold all your settings.

---

### Post by naggis on 2008-05-11
Typing "gksudo synaptic" into a terminal results in the black cursor flashing and no result. Its still flashing after 2-3 mins. Can you understand anything from this?
Typing "sudo synaptic" give the following output - 
sudo: unable to resolve host roger-laptop

Thanks for the help so far.

---

### Post by Biggy on 2008-05-11
sudo aptitude update

sudo aptitude safe-upgrade

---

### Post by naggis on 2008-05-11
Both of these two commands result in the same message as before - that the host could not be resolved.

---

### Post by naggis on 2008-05-11
Maybe I should just bite the bullet and reinstall Hardy which hopefully will resolve the matter.

---

### Post by Joeb454 on 2008-05-11
By the looks of it you aren't in the sudoers group.

The *easiest* option, is to reinstall. Just check your partitions before you do if you're worried about it :)

---

### Post by Cifra on 2008-05-11
Here's a solution to your problem which will probably work, naggis:

add the hostname in /etc/hosts beacuse it may be missing.

1. Go to the terminal and type
```
sudo gedit /etc/hosts
``` 

In the hosts file find the line:

```
127.0.1.1 hostname:DOMAIN hostname:DOMAIN
```

change it so that it reads:

```
127.0.1.1 hostname:DOMAIN hostname:DOMAIN hostname
```
where "hostname" is your computer's name(roger-laptop in your case, I think) and "DOMAIN" the Windows domain name of the LAN where you are.

Then save the file, logout/login or even better reboot the computer and now synaptic should work.



**To all the others: Reinstalling is so Windows-like. You won't learn anything in the process and this will benefit no-one. Never give up!**

---

### Post by naggis on 2008-05-11
Problem solved by reinstalling. This gave me a few other problems which are in the process of being sorted.
So, thanks everyone for their contribution

---

### Post by Ken Jannot on 2008-05-12
Alright, Cifra, I'd like to take you up on your offer of a learning opportunity.

I have the same problem, in that when I click "Install Updates" in Update manager, the wheel keeps turning, but nothing happens--never gets to the password verification for the installation. I have tried all of the suggestions above for terminal commands, and I just get the flashing cursor on the next line--nothing else happens. This includes with your most recent suggestion, Cifra, so I can't try to edit the host name. 

I may be crazy here, but this SEEMS to happen only when the red arrow shows up in the update notification spot, not when the orange splash appears. Right now I have the red arrow.

I really don't want to reinstall, since I went to a lot of trouble to get Hardy working properly.

---

### Post by trikkievic on 2008-05-12
I've been experiencing exactly the same problem, but only AFTER upgrading to 8.04. I never had this problem in 7.10. Somehow, first going to the update manager, checking for updates and then going to the synaptic package manager seemed to work. Other times, I just needed to open the system monitor, and kill the package manager, which was listed as sleeping. Then I could open it again. I think it's a 8.04 bug, I haven't really looked around whether or not it's reported though. I'll try the advise given above as well. See if it helps in my case. I don't really want to reinstall :(

V.

---

### Post by Ken Jannot on 2008-05-12
Now that you mention it--I opened my system monitor and Update Manager and Update Notifier were both listed as "sleeping," even though I'd clicked Update Notfier to start Update Manager, and it was in its stuck mode again. I shut them both down. When I restarted Update Manager, I got the same result. And now the System Manager says it's sleeping again.

---

### Post by trikkievic on 2008-05-12
Adding the localhost and domain in the /etc/hosts file as mentioned above seemed to have solved the issue. At least, when I click synaptic manager, it asks for my password and then the package manager opens. Now that I think of it, when the problem was still there, the package manager opened (if it did at all :P ) without asking for my password! Thanks for the tip!

gr

V

---

### Post by Cifra on 2008-05-12
> **Ken Jannot said:**
> Now that you mention it--I opened my system monitor and Update Manager and Update Notifier were both listed as "sleeping," even though I'd clicked Update Notfier to start Update Manager, and it was in its stuck mode again. I shut them both down. When I restarted Update Manager, I got the same result. And now the System Manager says it's sleeping again.

Try

```
sudo apt-get upgrade
```

I'm not sure if it's the same thing the Update manager does, but if it works, you won't need your update manager, just apt-get upgrade every once in a while :)

---

### Post by Ken Jannot on 2008-05-12
Upgrade, or update? I thought "upgrade" was for jumping up to a new version.

---

### Post by naggis on 2008-05-13
I reinstalled Hardy but met with the same problem again. At the next reinstall, I made sure that the ./ folder was selected for formatting and that has worked so far.
Maybe there was some problem in installing correctly.

---

### Post by Ken Jannot on 2008-05-13
> **Cifra said:**
> Try

```
sudo apt-get upgrade
```

I'm not sure if it's the same thing the Update manager does, but if it works, you won't need your update manager, just apt-get upgrade every once in a while :)

That seemed to work. But I'd rather have Update Manager work properly.

I'm thinking that editing the host, etc. doesn't make sense, because when I call it up (as laid out above), all the line says is, "kathy-desktop"--my companion's login and the computer name. No domain name and localhost distinction seems to be made. Or is that what I need to add?

---

### Post by Cifra on 2008-05-13
Yep, try the computer name as the host it's the name after the username i nthe terminal, for instance user@**host**

---

### Post by Ken Jannot on 2008-05-13
What I don't seem to have is any domain name listed.

---

### Post by rheide on 2008-05-17
For what it's worth, I lost my ability to successfully run Update Manager immediately after I used System|Administration|Network and tried to set my domain to match the MS computer network at home.

Based on the messages I found here, I was able to edit my hosts file and make Update Manager work again. Basically what I found was this:

127.0.1.1 bob-laptop.DOMAIN

By just removing the .DOMAIN, and saving the change, things worked again.

I'm not sure if there is a problem using System|Administration|Network to set the domain or not. That's a different post, but I thought it might help others to consider that they may have made such a change prior to Update Manager no longer working.

---

### Post by Ken Jannot on 2008-05-18
After I used the "sudo apt-get upgrade" process, the next time an update was available (shown by the red arrow in the corner), and I clicked it to open and use Update Manager -- everything worked as it should. I had not done anything with editing the domain name, etc. Perhaps that set of updates fixed this problem?

I'll see if this continues--at the very least, this seems to be a bug that appears sporadically and not an absolute condition.

Edit: It IS, apparently, a bug that appears sporadically. I've used Update Manager twice in the past week: once it hung up, and once it worked fine. When it hung up, upgrading through terminal didn't work either because it never asked for my administrative password. I had to restart in order to be able to upgrade through terminal. 

Is something going on between Update Notifier, Update Manager, and the Administrative Application?

---

### Post by Matt640 on 2008-05-24
Re: Unable to open Synaptic Package Manager
Re: Problem with Synaptic Package Manager
Re: Synaptic Package Manager Problem
Re: Synaptic Problem!
Hey.
I'm sorta having the same problem here only the cause was something different. I'm using the ordinary Desktop Edition of Ubuntu 8.04 not the 64AMD one. So I read from the Forums that by installing Sun Java 6, I can get my FrostWire up and running again. So I use my SPM to find it and download it. In the middle of Download/Installing, it hanged/jammed and my only option was to reboot. After I did, I realize that I can't open my SPM and it ask me to manually run sudo dpkg --configure -a. When I do, this turns up:
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation. You will need to go download one of the
archives:

jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

[http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download. The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

As you can see, I'm in desperate need of HELP! Can anyone encrypt this for me?

---

