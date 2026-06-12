---
title: "[SOLVED] Upgrading to Firefox 3.0 in Feisty"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Udibuntu on 2008-08-04
> **aysiu said:**
> I'd also recommend this method you've linked to (since I wrote it).

Ubuntuzilla is a script that automates the process and does a few other things (checks for localization, checks the integrity of the download, etc.), but it's a little more involved.

The *gksudo firefox* and *Check for Updates* method will not work. I don't know why someone kept suggesting it. First of all, the *Check for Updates* will install updates only within a version (so newer versions of Firefox 2 if you have 2 installed or newer versions of Firefox 3 if you have 3 installed). It will not upgrade you from 2 to 3. Also, it will not work at all if you're using the Ubuntu version of Firefox. It will work on only the Mozilla version of Firefox.

Same issue on Feisty. Done what you suggested, and terminal process went fine. No sign of FF3 on my system. Is this method not also for Feisty?

---

### Post by gjoellee on 2008-08-04
**use synaptic**

---

### Post by Udibuntu on 2008-08-04
> **gjoellee said:**
> **use synaptic**

Nada

---

### Post by aysiu on 2008-08-04
> **Udibuntu said:**
> Same issue on Feisty. Done what you suggested, and terminal process went fine. No sign of FF3 on my system. Is this method not also for Feisty?
That's odd.

Can you paste these commands in the terminal and then paste the output back here? ```
ls -l /usr/bin/firefox
ls /opt
```

---

### Post by Udibuntu on 2008-08-09
> **aysiu said:**
> That's odd.

Can you paste these commands in the terminal and then paste the output back here? ```
ls -l /usr/bin/firefox
ls /opt
```

udi@udi-laptop:~$ ls -l /usr/bin/firefox
lrwxrwxrwx 1 root root 22 2008-07-18 12:31 /usr/bin/firefox -> ../lib/firefox/firefox
udi@udi-laptop:~$ ls /opt
firefox
udi@udi-laptop:~$ 

Cheers aysiu.

Udi

---

### Post by aysiu on 2008-08-09
Well, your /usr/bin/firefox is pointing to the Ubuntu Firefox and not the Mozilla one.

Can you close Firefox, and then type this in the terminal? ```
/opt/firefox/firefox &
``` and see if that launches Firefox 3?

I see a Mozilla Firefox in /opt, but I don't know if it's 2 or 3.

---

### Post by Udibuntu on 2008-08-09
> **aysiu said:**
> Well, your /usr/bin/firefox is pointing to the Ubuntu Firefox and not the Mozilla one.

Can you close Firefox, and then type this in the terminal? ```
/opt/firefox/firefox &
``` and see if that launches Firefox 3?

I see a Mozilla Firefox in /opt, but I don't know if it's 2 or 3.

When launching from terminal, FF3 launches OK.

When exiting the said FF3 and trying to hit the FF icon on the bar, FF2 launches. FF3 does not appear in menu app's->internet-> FF2

I guess I need to redirect everything to FF3. Can you please point me in the right direction?

Also, I'd appreciate getting a little info on what went wrong with my install of FF3.

Thanks again for your efforts,

Udi

---

### Post by aysiu on 2008-08-09
Paste these commands into the terminal, and you should be good: ```
cp -R ~/.mozilla ~/.mozilla.backup
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/firefox/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

---

### Post by Udibuntu on 2008-08-09
OK, it works - icon opens FF3.

Now I need to find anew all the plugins...

Thanks for your help man, and have a great weekend,

Udi

---

### Post by Enternald on 2008-08-09
Remove firefox and install it again (in synaptic). This helped me when firefox didn't upgraded via update manager (I had 3.0 beta5 and upgraded to 3.0.1)

---

### Post by Udibuntu on 2008-08-09
> **Enternald said:**
> Remove firefox and install it again (in synaptic). This helped me when firefox didn't upgraded via update manager (I had 3.0 beta5 and upgraded to 3.0.1)

???

Won't that leave me with FF2 again? 

I don't have FF3 in the repo's so that Synaptic can lock on to it...

---

### Post by Enternald on 2008-08-09
Sorry I didn't know that feisty haven't firefox 3 in repo.

---

### Post by aysiu on 2008-08-10
> **Udibuntu said:**
> OK, it works - icon opens FF3.

Now I need to find anew all the plugins...

Thanks for your help man, and have a great weekend,

Udi
The second and third commands should have taken care of the plugins.

---

### Post by Udibuntu on 2008-08-10
> **aysiu said:**
> The second and third commands should have taken care of the plugins.

Sorry, no dice. I tried running them again - no error message, no Dallas.

Get some sleep man, it should be the middle of the night at your locale...

Udi

---

### Post by Udibuntu on 2008-08-10
Aysiu,

Do you think we got something wrong here? maybe the name of the new FF3 folder is different than the default, maybe the commands we tried work on FF3 betas or something, maybe the commands work only on FF3 from the repo's, and not the Mozilla FF like I'm using...

I'm trying to fix this with the help of Kilz and his mega thread but no luck so far...

Just some thoughts..

Thanks anyways,

Udi

---

### Post by Kilz on 2008-08-14
> **Udibuntu said:**
> 

I'm trying to fix this with the help of Kilz and his mega thread but no luck so far...


Udi

Yes, and we finally found out that FF3 was manually installed in that thread. I have given a command to symlink the flash plugin [in that thread]("http://ubuntuforums.org/showpost.php?p=5587028&postcount=264"). That should fix it for flash. But all plugins will need to be copied to the FF3 folder as it was manually installed.

---

