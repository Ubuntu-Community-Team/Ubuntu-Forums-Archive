---
title: "Howto: Change the hostname of a system SAFELY"
date: 2008-04-29
forum: Outdated Tutorials &amp; Tips
---

### Post by sammydee on 2008-04-29
This is a short and sweet howto that is nonetheless very important. It is based on my experiences when changing the hostname of a system. The hostname is effectively just the name of the system. You do not usually need to change it, but if you do have to for whatever reason, it isn't very difficult at all.

Whilst changing the hostname is not a difficult task in itself, it can be dangerous because if the system cannot resolve it's own hostname, it is impossible to sudo. Thus, if done improperly, changing a hostname can **lock you out of your own system**. Firstly, and most importantly, we make backups. Go to accessories/terminal and paste this command in, then press enter:

```
sudo cp /etc/hosts /etc/hosts.bak && sudo cp /etc/hostname /etc/hostname.bak
```

You **MUST** make backups, just in case. If you can't boot to a usable system after finishing this howto, or sudo doesn't work, see the instructions at the end of this guide. If you aren't completely familiar with the linux terminal, it might be a good idea to write these down or print them off.

Ok, now we have made backups, we can edit /etc/hosts:

```
sudo nano /etc/hosts
```

You should see what you are looking for fairly quickly, at the top of the file it should look something like:
```

127.0.0.1       localhost
127.0.1.1       old_hostname

```

Change old_hostname to a new hostname of your choice. Now save and exit.

Second file to edit is /etc/hostname. This does what it says on the tin, the file will have one line in it and that line is your hostname. Change it to your new hostname, save and exit.

Now reboot, you should have a perfectly working system in which sudo works. You can test both sudo and your new hostname by doing, simply:

```
sudo hostname
```

*NOTE: This command does not usually need to be run sudo, we are just testing both the changed hostname AND sudo at the same time.*

If it doesn't work, see below. You DID take backups, didn't you?

[LIST]
[*]Get into the grub menu by pressing esc on bootup, or allowing it to display automatically if you have set it up like this
[*] Choose recovery mode
[*] If prompted, select "drop to single user mode" or similar (note: this applies only on hardy I think)
[*] When you are at a root shell, type the following command:
```
cp /etc/hosts.bak /etc/hosts && cp /etc/hostname.bak /etc/hostname
```
[*] Then press ctrl-alt-del and you should reboot back to a perfectly working system.
[/LIST]

That's it! If anybody has problems, post here and I'll try to help.

Sam

---

### Post by wersdaluv on 2008-12-24
Very nice. I wonder why no one replied to this yet

---

### Post by Muttonhead on 2008-12-25
I just wanted to say that this helped me out a lot today.  It worked without a hitch.

Thank you for sharing this.

---

### Post by warpasylum on 2009-06-20
Thanks man.

---

### Post by darwinj on 2009-07-03
Just what I was looking for. Thanks!

---

### Post by mxgeldar on 2009-07-09
perfect instructions  -  thanks!

---

### Post by kellyhardinguk on 2009-07-09
You do need to consider updating certificates (stuff like webmin, ssh) too, otherwise you'll get security certificate mismatches (especially if you install IMAPS on your system for instance).

Not entirely sure how to do that myself, but its a consideration to extend this howto.

---

### Post by jaebe2 on 2009-12-05
Works perfectly,

Thanks

---

### Post by arsradu on 2010-01-14
Worked like a charm!

Thank you a lot!

---

### Post by seemu on 2010-02-11
Cool, thanks for that! I just had a very curious bug when I tried to change the hostname. My first action was just to change the /etc/hostname file, when I was not aware that one must also change the /etc/hosts file. After rebooting the Ubuntu (2.6.31-20-PAE) refused to boot due to a kernal panic of unknown reason. 

Many attempts concluded that the kernel panic was caused by inconsistent hostnames in the /etc/hostname and /etc/hosts files - my box boots now without any problem. 

Therefore take care guys when you want to change the hostname from the command line, and be aware of what to do if a strange kernel panic appears!

---

### Post by Francewhoa on 2010-03-12
Thanks sammydee. But there is an** easier, safer and faster **way to do this.

Using Ubuntu 8.04 LTS (Desktop edition).

Steps
    * Navigate to System > Administration > Network
    * Select the General tab. 
    * You might have to click on Unlock button.
    * Enter the new name of your computer in the Host name field.
    * Click Close button.
    * Close all open applications and reboot.

This will automatically change all settings related to hostname (computer name). Including /etc/hosts and /etc/hostname

---

### Post by dbch on 2010-05-15
Hi.

How would you do that in Ubuntu 9.4.  There's isn't 'Network' there's 'Network Tools' and there's no 'General' tab under that.

Under Ubuntu Help & Support on the computer it has it under 'Network Settings' but that isn't there either.

I've got - Network:  Tools;  Connections;  Proxy, and none of them have a 'General' tab.

I really want to change my computer's name from the one that it is now - the place I bought it - came like that.

Thanks.:grin:

---

### Post by sammydee on 2010-05-17
> **dbch said:**
> Hi.

How would you do that in Ubuntu 9.4.  There's isn't 'Network' there's 'Network Tools' and there's no 'General' tab under that.

Under Ubuntu Help & Support on the computer it has it under 'Network Settings' but that isn't there either.

I've got - Network:  Tools;  Connections;  Proxy, and none of them have a 'General' tab.

I really want to change my computer's name from the one that it is now - the place I bought it - came like that.

Thanks.:grin:

Hey, just follow the instructions in the original post. You don't need to rely on the graphical way for that to work.

---

### Post by s1mmel on 2010-05-20
> **sammydee said:**
> 
```

127.0.0.1       localhost
127.0.1.1       old_hostname

```


FYI, this is mainly for servers or machines with "hardcoded" IP's and according DNS entries, but still might be of interest to some ppl.

```

root@tuvok:/home# cat /etc/hosts
127.0.0.1       localhost
213.239.x.x tuvok q3.xxxxx.de tuvok.xxxxx.de

```

Cheers,
s1mmel

---

### Post by koushik.ms on 2010-05-21
Hey sammydee. Thanks for the simple & clear instructions. Worked like a charm on my laptop running ubuntu 10.04.

And yes, I did make backups ;-).

---

### Post by isaacj87 on 2010-05-26
Great tip man!

Thanks for the help :)

---

### Post by COKEDUDE on 2010-06-11
> **Onopoc said:**
> Thanks sammydee. But there is an** easier, safer and faster **way to do this.

Using Ubuntu 8.04 LTS (Desktop edition).

Steps
    * Navigate to System > Administration > Network
    * Select the General tab. 
    * You might have to click on Unlock button.
    * Enter the new name of your computer in the Host name field.
    * Click Close button.
    * Close all open applications and reboot.

This will automatically change all settings related to hostname (computer name). Including /etc/hosts and /etc/hostname


In case you don't have this you need to install Network tool. So pop open a terminal and type:
```
sudo apt-get install gnome-network-admin
```

You could also use Synaptic if you prefer to use a gui and search for network-admin.

---

### Post by gzarkadas on 2010-06-12
Hi,

Nice and brief, easy to follow howto. And it definitely works as is on a usual Ubuntu installation. But it may break some packages or even the system itself if [COLOR=DimGray]/etc/sudoers[/COLOR] has been configured with more restrictive than the defaults settings, say like the ones in [this howto of the month]("http://ubuntuforums.org/showthread.php?t=1132821"). 

So, I would propose to add the following two steps in the process, in order to extend the domain of successful application of this howto and save the need to restore to our previous settings:

-----------

[B]a. Just after the cp commands:
[/B]
If you are certain that you *never* changed the configuration of sudo, you may skip this step.

Use ```
visudo
``` to inspect the contents of /etc/sudoers. Watch for any lines that _do not_ start with the comment character (#) _and_ contain the old_hostname. 

If you find such line(s), change the hostname in those lines to the new one and save your changes. Else close the editor without saving any changes.
[B]
b. Just before rebooting:
[/B]
Inspect the configuration files in your system for places that your hostname is used. Use the `find' command to grep all files inside /etc for instances of your old_hostname. 

_Explanation of arguments:_
-O2 : a speed optimisation flag
-type f : only look for files
-name '*[!~]' : do not consider backups (that end in ~)
-exec grep : execute the grep command on each file's contents
-Hn -C0 : show filename and line number and do not print context lines (to make the list short)
old_hostname : replace it with your old hostname
'{}' ';' : enter them as is, they mean the found file and the end of find command
| less : pipe the output to less in order to browse it all if it is too long
```

find -O2 /etc -type f -name '*[!~]' -exec grep -Hn -C0 old_hostname '{}' ';' | less

```Note down the files that need editing.

Alternatively, you can slightly modify the above command to also write the output to a file which you will then open with your graphical viewer/editor of choice (replace <filename> with your desired path to the file):

_Explanation of (additional) arguments:_
| tee <filename> : pipe output to `tee' first, to duplicate it in <filename>; the pipe following sends it also to less.
```

find -O2 /etc -type f -name '*[!~]' -exec grep -Hn -C0 old_hostname '{}' ';' | tee <filename> | less

```Now use your favorite editor to open all files that were found to contain references to old_hostname and change all instances of old_hostname to the new_hostname. 

-----------

For example, in my system the following files (apart /etc/hosts and /etc/hostname) would also have needed editing:

/etc/sudoers
/etc/postfix/main.cf
/etc/inetd.conf
/etc/apache2/sites-available/default-ssl
/etc/apache2/sites-available/default
/etc/gtags/htmake.conf
/etc/psad/psad.conf

---

### Post by COKEDUDE on 2010-06-13
Whats sudoers and how does it effect changing your hostname? I can't find a good explanation on what it is.

---

### Post by gzarkadas on 2010-06-13
> **COKEDUDE said:**
> Whats sudoers and how does it effect changing your hostname? I can't find a good explanation on what it is.

It *may* have an effect, if you select to grant permissions based on hostname (to narrow down the potential or a remote attack). This is something that is suggested as part of hardening a system. The link to the sudoers configuration howto in my previous post is quite explanatory; you can also try `man sudo' and `man sudoers' inside a terminal window.

---

### Post by Happibun on 2010-08-28
Thanks for this! I was able to correct my banana fingered mistake when I installed 10.04 on a fresh HD this morning.

Cheers.

---

