---
title: "Cannot login with correct password"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by agentfortyseven on 2011-10-28
Hello everyone,
I had a great time using Ubuntu 10.04 for about an year now. But today I "completely" uninstalled Evolution mail, and when I tried rebooting i could no longer login. The same login screen would popup again and again even after entering correct login info. I dual boot with XP and Ubuntu 10.04.  Please help me out folks.

---

### Post by hakermania on 2011-10-28
Hey, did you messed up with nautilus? I had the exact same problem when I'd unistalled nautilus hehe.

Well, while being on the prompt for the password, where it doesn't let you login, press Crl+Alt+F1 and enter your login name, press enter, enter your passwd, press enter and see if it lets you login, just to make sure you know the correct passwd and that's not the case.

---

### Post by agentfortyseven on 2011-10-28
yes it would let me log in from the console using Alt+Ctrl+F1

---

### Post by agentfortyseven on 2011-10-28
thanks for the quick reply. I also tried sudo apt-get install gnome-applet. But it would give me an error:
                                  **E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?**

---

### Post by agentfortyseven on 2011-10-28
I'm more than sure uninstalling Evolution and its indicator applet is the reason.

---

### Post by agentfortyseven on 2011-10-28
> **hakermania said:**
> Hey, did you messed up with nautilus? I had the exact same problem when I'd unistalled nautilus hehe.


I didn't uninstall nautilus. I don't remember doing anything else other than uninstalling Evolution and its components "completely"

---

### Post by hakermania on 2011-10-28
I don't think that you'll have internet connection to the terminal via the Ctrl+Alt+F1 unless you have a wired connection.
If google replys:
```

ping google.com

```
then you have internet connection. When you're sure you have an internet connection, try to reinstall the packages you *completely* uninstalled.

---

### Post by agentfortyseven on 2011-10-28
> **hakermania said:**
> I don't think that you'll have internet connection to the terminal via the Ctrl+Alt+F1 unless you have a wired connection.
If google replys:
```

ping google.com

```then you have internet connection. When you're sure you have an internet connection, try to reinstall the packages you *completely* uninstalled.

And how do I reinstall Evolution from the console screen?

EDIT: I mean what should be the command at the console screen.

---

### Post by lordievader on 2011-10-28
To install Evolution via the CLI, simply enter:
```
sudo apt-get install evolution
```

---

### Post by agentfortyseven on 2011-10-28
> **lordievader said:**
> To install Evolution via the CLI, simply enter:
```
sudo apt-get install evolution
```

Hey buddy. Thanks. Do you think that would fix my login issue?

---

### Post by lordievader on 2011-10-28
Well it might, I just checked on my 11.04 install. Evolution itself doesn't have very important dependencies, but the package "evolution-data-server-common" does have a few dependencies vital to the gnome (2) desktop. Things like gnome-panel and gnome-session, etc. You could see if the package "ubuntu-desktop" is installed. If not install it, perhaps it will solve your problem.

---

### Post by agentfortyseven on 2011-10-28
I'll get back to you as soon as its done. Thanks.

---

### Post by agentfortyseven on 2011-10-28
> **lordievader said:**
> Well it might, I just checked on my 11.04 install. Evolution itself doesn't have very important dependencies, but the package "evolution-data-server-common" does have a few dependencies vital to the gnome (2) desktop. Things like gnome-panel and gnome-session, etc. You could see if the package "ubuntu-desktop" is installed. If not install it, perhaps it will solve your problem.

Thanks but it didn't help. I got the following error when i tried installing Evolution.
[B]E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

[/B]EDIT: you know what I tried sudo apt-get install gnome-applet too and it gave me the same error as above.

---

### Post by lordievader on 2011-10-28
Odd, did you try what he says? Running "sudo apt-get update" before installing? (It is always a good idea to do that before installing.) And if that doesn't work try the second suggestion "sudo apt-get --fix-missing"

---

### Post by agentfortyseven on 2011-10-28
i tried both of them none of them actually worked

EDIT: sorry about the late reply. I might have to start a new thread on how to know when someone replies to your post.

---

### Post by lordievader on 2011-10-28
Very strange, I hope someone else here has some good idea's, to be honest I am running out of ideas.

Have you tried to install the ubuntu-desktop package? (sudo apt-get install ubuntu-desktop)

P.s. You can set the forums up to send you an email if there are replies.

---

### Post by mikechant on 2011-10-28
I'd suggest booting from a live CD/USB and then posting the contents of
/etc/apt/sources.list
from your installation's root partition, which should be listed on the 'places' menu 
(note we don't want the version of /etc/apt/sources.list from the running LiveCD/USB, which would be what you would get by default if you just open the file manager and go to the/etc/apt folder)


You may have some dodgy repositories defined, if so we can probably identify them so you can remove them.

---

### Post by hakermania on 2011-10-28
Hey, wait a moment, do you have internet connection in the terminal?
give
```

ping google.com

```
and if you get an answer like
```

PING google.com (74.125.39.99) 56(84) bytes of data.
64 bytes from www.google.com (74.125.39.99): icmp_req=1 ttl=53 time=73.3 ms
64 bytes from www.google.com (74.125.39.99): icmp_req=2 ttl=53 time=73.5 ms
64 bytes from www.google.com (74.125.39.99): icmp_req=3 ttl=53 time=74.1 ms

```
then you have internet connection. Press Ctrl+C to terminate the 'ping' process.
Post back with the results.

---

### Post by albaqui on 2011-10-28
> **agentfortyseven said:**
> thanks for the quick reply. I also tried sudo apt-get install gnome-applet. But it would give me an error:
                                  **E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?**

Hi
I have been trying since yesterday to fix my password in ubuntu. I pressed ctrl+alt+F1
it allowed me to set my username and password
But finally shows this:username@username-laptop:~$
Now what to do? PLEASE HELP ME.

---

### Post by agentfortyseven on 2011-10-28
> **lordievader said:**
> Very strange, I hope someone else here has some good idea's, to be honest I am running out of ideas.

Have you tried to install the ubuntu-desktop package? (sudo apt-get install ubuntu-desktop)

P.s. You can set the forums up to send you an email if there are replies.

Well I tried that too and it didn't help. Anyway I really appreciate your help so far.
Thanks.

---

### Post by agentfortyseven on 2011-10-28
> **hakermania said:**
> Hey, wait a moment, do you have internet connection in the terminal?
give
```

ping google.com

```and if you get an answer like
```

PING google.com (74.125.39.99) 56(84) bytes of data.
64 bytes from www.google.com (74.125.39.99): icmp_req=1 ttl=53 time=73.3 ms
64 bytes from www.google.com (74.125.39.99): icmp_req=2 ttl=53 time=73.5 ms
64 bytes from www.google.com (74.125.39.99): icmp_req=3 ttl=53 time=74.1 ms

```then you have internet connection. Press Ctrl+C to terminate the 'ping' process.
Post back with the results.

I tried ping google.com and it never gave me the above output

EDIT: But i do have wifi enabled. I will post the results asap.

---

### Post by agentfortyseven on 2011-10-28
> **albaqui said:**
> Hi
I have been trying since yesterday to fix my password in ubuntu. I pressed ctrl+alt+F1
it allowed me to set my username and password
But finally shows this:username@username-laptop:~$
Now what to do? PLEASE HELP ME.

I think you might have to enter your username and press return key followed by a prompt which asks for your password. When you enter the password and press return key it will take you to the console screen of ubuntu. But then again I'm not sure how you can "fix" your password. Maybe the wiser penguins can help you.

---

### Post by agentfortyseven on 2011-10-28
> **mikechant said:**
> I'd suggest booting from a live CD/USB and then posting the contents of
/etc/apt/sources.list
from your installation's root partition, which should be listed on the 'places' menu 
(note we don't want the version of /etc/apt/sources.list from the running LiveCD/USB, which would be what you would get by default if you just open the file manager and go to the/etc/apt folder)


You may have some dodgy repositories defined, if so we can probably identify them so you can remove them.

Can i install ubuntu on a 4 Gb live USB?

---

### Post by agentfortyseven on 2011-10-28
[FONT=Arial]I've told this before and I'm stressing on this again n again.[B]
_The uninstallation of Evolution, its gnome indicator applet and other dependencies_ [/B]is most probably the reason behind this as I've observed from other threads on this forum.[/FONT]

---

### Post by lolpenguin on 2011-10-28
When uninstalling Evolution, were its dependencies uninstalled? Some of these may be critical to the operation of ubuntu. Search through your logs to see if anything required for the OS was uninstalled, and re-install them.
Hope it helps:)

---

### Post by lordievader on 2011-10-29
Hakermania's suggestion is very useful. Without an active internet connection it won't be able to locate all of the packages. So issue a ping command and see if it gets replies.

EDIT: seems I am very slow...

---

### Post by hakermania on 2011-10-29
> **lordievader said:**
> Hackermania's suggestion is very useful. Without an active internet connection it won't be able to locate all of the packages. So issue a ping command and see if it gets replies.

It's h**ake**rmania :P
He already told that he tried pinging and got no reply...

So, this means that even if your wireless is enabled you aren't connected to the internet, so connect to your modem via a LAN cable before booting, and when you've placed the wire then boot your Ubuntu (i've done this before, it will work).
Now you'll have internet connection.
After this, try installing evolution again (this time it will work because you'll have internet connection!) using the commands somebody else have pointed out before (sudo apt-get install evolution)!

I hope I'm clear now :)

---

### Post by agentfortyseven on 2011-10-29
> **lolpenguin said:**
> When uninstalling Evolution, were its dependencies uninstalled? Some of these may be critical to the operation of ubuntu. Search through your logs to see if anything required for the OS was uninstalled, and re-install them.
Hope it helps:)

Indeed the critical dependencies were uninstalled. I had this premonition and saw it coming right when I was uninstalling them. I'm no Linux wizard so I've no idea how to go through the logs :)

EDIT: Thanks.

---

### Post by agentfortyseven on 2011-10-29
> **hakermania said:**
> It's h**ake**rmania :P
He already told that he tried pinging and got no reply...

So, this means that even if your wireless is enabled you aren't connected to the internet, so connect to your modem via a LAN cable before booting, and when you've placed the wire then boot your Ubuntu (i've done this before, it will work).
Now you'll have internet connection.
After this, try installing evolution again (this time it will work because you'll have internet connection!) using the commands somebody else have pointed out before (sudo apt-get install evolution)!

I hope I'm clear now :)

Thanks a lot buddy. I am going to do that soon but I'm currently preoccupied with lots of other work. So it will take a while for me to reply. Really appreciate your help.
Thanks :-)

---

### Post by hakermania on 2011-10-31
waiting for response

---

### Post by agentfortyseven on 2011-11-01
WOOHOO... :D

Nailed it finally, wasn't a big deal though. I'm sorry about the late reply.. was busy with work.
Thanks a LOT Hakermania... you're the man.
So here's what happened.

1) I plugged in a LAN cable and logged into the Alt+Ctrl+F2 mode of Ubuntu.
2) First thing I tried was PING google.com and it gave me a perfect reply exactly like the one in the previous post by Hakermania.
3) Next up I tried sudo apt-get install evolution (It didn't help a bit so don't bother to reinstall evolution if you're in a similiar situation)
4) And finally I ran sudo apt-get install gnome-applets which did the trick for me and now I'm back on my fav OS.

special thanks to Hakermania :) for being really helpful.

---

### Post by agentfortyseven on 2011-11-03
Thank you everyone for replying and helping me out.
Ubuntuforums ROCKS :KS

---

### Post by Garland Fox on 2011-11-03
SOLVED] 			 			[Oneiric 11.10 Password Reset]("http://ubuntuforums.org/showthread.php?t=1874577") 			 		  		  		 			 			 				
Had this problem after upgrading to Oneiric 11.10 and uninstalling Evolution. Nothng worked to reset the password until I Found this on how-to-geek site

---

### Post by hakermania on 2011-11-04
Hey, I was too busy too and I hadn't time to monitor this thread, well, i'm happy to see that everything went fine :)

---

### Post by agentfortyseven on 2011-11-06
thank you once again :-)

---

### Post by agentfortyseven on 2011-11-06
> **Garland Fox said:**
> SOLVED] 			 			[Oneiric 11.10 Password Reset]("http://ubuntuforums.org/showthread.php?t=1874577") 			 		  		  		 			 			 				
Had this problem after upgrading to Oneiric 11.10 and uninstalling Evolution. Nothng worked to reset the password until I Found this on how-to-geek site

I'm not very sure we had the same issue.

---

