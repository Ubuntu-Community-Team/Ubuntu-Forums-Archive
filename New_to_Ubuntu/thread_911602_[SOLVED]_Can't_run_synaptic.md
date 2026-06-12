---
title: "[SOLVED] Can't run synaptic"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by garyed on 2008-09-05
When I try to use Synaptic I get an error that tells me to manually run in terminal- 
```
 sudo dpkg --configure -a 
```
When I do that I get a screen that pops up about configuring openssh server
with a menu on the top & no error messages. When I close the the window & go back & run synaptic I get the same error again. I've tried rebooting & that didn't work. Any ideas?

---

### Post by drs305 on 2008-09-05
Try checking synaptic, settings, preferences, network and select "Direct connect to the internet" and see if that works.

---

### Post by garyed on 2008-09-05
> **drs305 said:**
> Try checking synaptic, settings, preferences, network and select "Direct connect to the internet" and see if that works.

The problem is I can't get in to synaptic settings because the error message won't let me in. I can see the menu in the background but I can't do anything
until I close the error message out & then it closes synaptic automatically.

---

### Post by rocknrolf77 on 2008-09-05
Try in the terminal

```
sudo aptitude install -f

```

---

### Post by garyed on 2008-09-05
> **rocknrolf77 said:**
> Try in the terminal

```
sudo aptitude install -f

```

I tried that & it gave me the same error & said that I needed to run 
```
 dpkg --configue -a 
``` to correct the problem.
This time when i ran the command & got to the setting up openssh-server window, I tried reset from the menu. It brought me back to the terminal & this is what it shows.

gary@dell-desktop:~$ sudo dpkg --configure -a
Setting up openssh-server (4.3p2-8ubuntu1.4) ...
 

It seems like its just hanging on the server & can't get any further.
I there a way to temporarily disable the ssh-server?
Maybe that would do the trick.

---

### Post by garyed on 2008-09-05
Now when I try to run synaptic it won't open at all & I get an error telling me that apt-get or aptitude is still running. 
How do I close aptitude?

---

### Post by Sef on 2008-09-05
> Now when I try to run synaptic it won't open at all & I get an error telling me that apt-get or aptitude is still running.
How do I close aptitude?


Check [Psychocats fix sudo]("http://www.psychocats.net/ubuntu/fixsudo").

---

### Post by garyed on 2008-09-05
I don't have a problem running sudo.
I can log in as root if I want.

---

### Post by garyed on 2008-09-05
I went ahead & rebooted & now I'm back to my original problem.
I run synaptic & get the error to run dpkg --configure -a
I run the command & get the openssh-server window thing.
It's just a loop going from one to the other.
If I could close the ssh-server that might help.

---

### Post by knix on 2008-09-05
it wants to configure the package. you may have to interact with it to do so. I would dpkg -r openssh-server, then reinstall if needed.

I believe you can disable ssh in system>administration>services. (I'm not sure, i'm not in gnome right now.

Even with it disable, you'll still have an unconfigured package.

Edit: it should show up in the gnome system monitor if you want to kill it.

---

### Post by wolfen69 on 2008-09-05
try uninstalling and reinstalling synaptic:
```
sudo apt-get purge synaptic
``` then ```
sudo apt-get clean
```then ```
sudo apt-get autoremove
```then ```
sudo apt-get install synaptic
```

---

### Post by garyed on 2008-09-05
Thanks to all, I think I finally got it.
I used this:
```
 sudo /etc/init.d/ssh stop 
```

Then I could open synaptic without the errors.
I was trying to update wine which didn't go so good, I got errors in Samba but that's for another thread.
Anyways I went back & issued the following command: 
```
 sudo /etc/init.d/ssh start 
```
and synaptic opened again O.K.
Evidently there's something in open-ssh thats causing the problem.
It may have something to with permissiions, but it's working now.

---

### Post by rocknrolf77 on 2008-09-06
Good to see you fixed it. Someone should really do something about that problem in apt. Give a more precise error message.

---

