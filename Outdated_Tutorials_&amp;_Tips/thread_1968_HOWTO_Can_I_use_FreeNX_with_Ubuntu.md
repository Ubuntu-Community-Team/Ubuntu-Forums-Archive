---
title: "HOWTO: Can I use FreeNX with Ubuntu?"
date: 2004-10-24
forum: Outdated Tutorials &amp; Tips
---

### Post by jdong on 2004-10-24
Q:How can I use FreeNX with Ubuntu?

A:
**EDIT**: For those who don't know what FreeNX is, freeNX is a remote desktop protocol, like VNC. Unlike VNC, FreeNX compresses at the X protocol level, giving it a much better experience over low-bandwidth (and high bandwidth) line. To give you an idea of FreeNX's power, I can use Smooth Scrolling in Firefox over a dial-up line without excessive jerking. Over cable/dsl lines, you can barely notice that you're not actually at the system.

 It's not in Ubuntu's repositories, but is available for Debian. Add the following line to your /etc/apt/sources.list

```
deb http://kanotix.com/files/debian/ ./
```

The repository is for Kanotix, a Debian/SID Knoppix derivative.

Run **apt-get install freenx**.

Then, run **nxsetup**. If you want a nomachine key (RECOMMENDED FOR SIMPLICITY), run **nxsetup --setup-nomachine-key** instead. Please google the command and read the security implications of doing so! (Basically if FreeNX is flawed, there's a possibility of gaining SSH access as the NX user remotely!)

Make sure that SSH is running for FreeNX to work properly.


**Newer (like these) versions of FreeNX no longer need a nxserver --adduser command. Any user that can log into the system via PAM can log in remotely with NX. Running the nxserver --adduser commands is harmless though.

There are also nxclient deb's in the repository, so browse it and enjoy!
**Important Note!**
The repository also contains up-to-date reiser4progs (a good thing if you want to try reiser4, and doesn't affect you if you don't use reiser4 at all)
It also has a newer java-package that supersedes Ubuntu's. The Kanotix java-package works perfectly on Ubuntu, so not really a problem either. Just a heads-up in case you wanted to stay as purely Ubuntu as possible!

**UPDATE**: As someone pointed out, Kanotix FreeNX now depend on libpng being newer or equal to 1.2.7. Warty has version 1.2.5.

You can always grab the Hoary version of libpng. [http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng3](http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng3) and friends are in Ubuntu's repository.

---

### Post by Rancoras on 2004-10-29
Ok, it looks like ssh is working fine.  I can ssh into the box from here at work with putty on windows XP.  

I installed the NX client for windows XP from nomachine.  I think I set everything up ok, but it seems that authentication for user nx is failing.  I see that the user nx is set up.  Here's the output from the nxclient on windows.

```
NX> 203 NXSSH running with pid: 684
NX> 200 Connected to address: XXX.XXX.XXX.XXX on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

```

Any ideas?

---

### Post by fulvioo on 2004-10-29
I get the same error code

---

### Post by jdong on 2004-10-29
did you use the **--setup-nomachine-key** option?

---

### Post by Rancoras on 2004-10-29
[QUOTE=jdong]did you use the **--setup-nomachine-key** option?[/QUOTE]

No, because I like secure.  I guess there's a key I need to copy to the client?

---

### Post by jdong on 2004-10-29
yeah, the SSH host key.

---

### Post by Rancoras on 2004-10-29
Ok, I've gotten a little further.  I got the appropriate key copied to the client.  Now, I'm getting this output:

```
Info: Proxy running in client mode with pid '752'.
Info: Connecting to remote host '192.168.1.110:5001' on SSH port 'localhost:1749'.
Info: Connection to remote proxy '192.168.1.110:5001' established.
Warning: Connected to remote NXPROXY version 1.4.0 with local version 1.3.2.
Warning: Consider checking http://www.nomachine.com/ for updates.
Info: Handshaking with remote proxy '192.168.1.110:5001' completed.
Info: Synchronizing local and remote caches.
Info: Not using NX delta compression.
Info: Using lan link parameters 16384/80/16/8192.
Info: Using pack method '16m-jpeg-9' with session 'unix-gnome'.
Info: Not using ZLIB stream compression.
Info: Not using remote ZLIB stream compression.
Info: Not using persistent cache.
Info: Using remote server '192.168.1.110:5001'.
Info: Starting X protocol compression.
Info: Established X server connection.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.

```

I can't find anything about that error on google other than someone else asking for help.

---

### Post by jdong on 2004-10-30
Make sure that you selected **use SSH to encrypt data**

---

### Post by Rancoras on 2004-10-30
You mean "Enable SSL encryption of all traffic" ?  Yup, it's been checked since the start.  As a test, I configured a profile to connect to nomachine's testdrive server.  All the settings were the same in the client except for the host address.  It worked like a charm.  That leads me to believe that it's a setting on my host that is the problem.

On a side note, I'm very impressed with the speed that I saw during the testdrive.  Much better than VNC.

---

### Post by jdong on 2004-10-30
[QUOTE=Rancoras]You mean "Enable SSL encryption of all traffic" ?  Yup, it's been checked since the start.  As a test, I configured a profile to connect to nomachine's testdrive server.  All the settings were the same in the client except for the host address.  It worked like a charm.  That leads me to believe that it's a setting on my host that is the problem.

On a side note, I'm very impressed with the speed that I saw during the testdrive.  Much better than VNC.[/QUOTE]
 speed: amazing, shocking, those are understatements!

If anyone wants to challenge my dial-up claim, go ahead!

---

### Post by fulvioo on 2004-10-30
Who will be the first to post a how to, configuring freenx on ubuntu and a windows client?

---

### Post by jdong on 2004-10-30
I assumed that the Windows client would be the easy part! Unless, of course, you don't use a Nomachine key... Then, you're on your own to google for how to install keys & such.

---

### Post by fulvioo on 2004-10-30
hmn

after a
chmod 700 /home/.nx
chmod 700 /home/.nx/.ssh
chmod 700 /home/.nx/.ssh/*

everything worked

---

### Post by erson on 2004-11-14
[QUOTE=jdong]Q:How can I use FreeNX with Ubuntu?

A:
**EDIT**: For those who don't know what FreeNX is, freeNX is a remote desktop protocol, like VNC. Unlike VNC, FreeNX compresses at the X protocol level, giving it a much better experience over low-bandwidth (and high bandwidth) line. To give you an idea of FreeNX's power, I can use Smooth Scrolling in Firefox over a dial-up line without excessive jerking. Over cable/dsl lines, you can barely notice that you're not actually at the system.

 It's not in Ubuntu's repositories, but is available for Debian. Add the following line to your /etc/apt/sources.list

```
deb http://kanotix.com/files/debian/ ./
```

The repository is for Kanotix, a Debian/SID Knoppix derivative.

Run **apt-get install freenx**.

Then, run **nxsetup**. If you want a nomachine key (RECOMMENDED FOR SIMPLICITY), run **nxsetup --setup-nomachine-key** instead. Please google the command and read the security implications of doing so! (Basically if FreeNX is flawed, there's a possibility of gaining SSH access as the NX user remotely!)

Make sure that SSH is running for FreeNX to work properly.


**Newer (like these) versions of FreeNX no longer need a nxserver --adduser command. Any user that can log into the system via PAM can log in remotely with NX. Running the nxserver --adduser commands is harmless though.

There are also nxclient deb's in the repository, so browse it and enjoy!
**Important Note!**
The repository also contains up-to-date reiser4progs (a good thing if you want to try reiser4, and doesn't affect you if you don't use reiser4 at all)
It also has a newer java-package that supersedes Ubuntu's. The Kanotix java-package works perfectly on Ubuntu, so not really a problem either. Just a heads-up in case you wanted to stay as purely Ubuntu as possible![/QUOTE]
 It should be noted that the packages on kanotix.com has been upgraded and FreeNX can't be installed according to the guide because the libnxcomp0 and libnxcompext0 packages on kanotix depends on libpng being >= 1.2.7 and Warty has only 1.2.5. So using the libpng in Hoary should solve this problem. You might want to update your guide with suitable changes so that more people can start using FreeNX.

---

### Post by shoelessmike on 2004-11-19
Tried to install freenx from aforementioned repos, and got error
> freenx:
 Depends: nxagent but it is not going to be installed
 Depends: nxproxy but it is not going to be installed
Anyone know where I can get these?

---

### Post by puzzledm on 2004-11-23
[QUOTE=jdong]Q:How can I use FreeNX with Ubuntu?

A:
**EDIT**: For those who don't know what FreeNX is, freeNX is a remote desktop protocol, like VNC. Unlike VNC, FreeNX compresses at the X protocol level, giving it a much better experience over low-bandwidth (and high bandwidth) line. To give you an idea of FreeNX's power, I can use Smooth Scrolling in Firefox over a dial-up line without excessive jerking. Over cable/dsl lines, you can barely notice that you're not actually at the system.

 It's not in Ubuntu's repositories, but is available for Debian. Add the following line to your /etc/apt/sources.list

```
deb http://kanotix.com/files/debian/ ./
```

The repository is for Kanotix, a Debian/SID Knoppix derivative.

Run **apt-get install freenx**.

Then, run **nxsetup**. If you want a nomachine key (RECOMMENDED FOR SIMPLICITY), run **nxsetup --setup-nomachine-key** instead. Please google the command and read the security implications of doing so! (Basically if FreeNX is flawed, there's a possibility of gaining SSH access as the NX user remotely!)

Make sure that SSH is running for FreeNX to work properly.


**Newer (like these) versions of FreeNX no longer need a nxserver --adduser command. Any user that can log into the system via PAM can log in remotely with NX. Running the nxserver --adduser commands is harmless though.

There are also nxclient deb's in the repository, so browse it and enjoy!
**Important Note!**
The repository also contains up-to-date reiser4progs (a good thing if you want to try reiser4, and doesn't affect you if you don't use reiser4 at all)
It also has a newer java-package that supersedes Ubuntu's. The Kanotix java-package works perfectly on Ubuntu, so not really a problem either. Just a heads-up in case you wanted to stay as purely Ubuntu as possible!

**UPDATE**: As someone pointed out, Kanotix FreeNX now depend on libpng being newer or equal to 1.2.7. Warty has version 1.2.5.

You can always grab the Hoary version of libpng. [http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng3](http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng3) and friends are in Ubuntu's repository.[/QUOTE]
 hi there I have read this review and am somewhat confused!  

I need to access and control a windows xp computer (my dad's) and need to be able to give really simple instructions over the phone of how to set up the xp machine as the client.

Then I need simpler instructions - after installing nx how do I get it to work and connect to the xp machine.

The two computers both are on broadband.

Thanks for your help so far!

---

### Post by mr_ed on 2004-11-26
puzzledm, in that case you'll need to use VNC.
The FreeNX server will only work on computers using the X protocol, like Linux and Solaris.

There's client software for Windows, but not server software.
On Linux, there's both client and server software.

---

### Post by AllTom on 2004-12-18
[QUOTE=shoelessmike]Tried to install freenx from aforementioned repos, and got error

Anyone know where I can get these?[/QUOTE]
I get the same error.

---

### Post by jdong on 2004-12-20
I've packaged working freeNX in my warty-extras repository (see the Backports forum).


It's currently undergoing beta-testing in the -staging tree, I'll have it out of there by Jan 10th.

---

### Post by snipes420 on 2004-12-22
If you get a "Parse error in remote options string" type error message it could be because you have a space in the name of the session. I found this info in the mailing list linked. I could not connect the client to the server until I removed the space in the session name.

[http://mail.kde.org/pipermail/freenx-knx/2004-December/000529.html](http://mail.kde.org/pipermail/freenx-knx/2004-December/000529.html)

Edit: I find this to be faster and more flexible compared to VNC. TightVNC anyway, thats all I have used. but I'm wondering how i could use freenx instead of vnc for what I use it for. can you have a session start automaticly with a program running in it when the computer boots/reboots? so you can connect to it whenever you need it and its right there?

---

### Post by Geekboy on 2004-12-22
> I've packaged working freeNX in my warty-extras repository (see the Backports forum).


It's currently undergoing beta-testing in the -staging tree, I'll have it out of there by Jan 10th.
Thanks! :)  That backport worked great.  I installed it last night and installed the windows client for my 2000 box at home.  I was able to connect on my Lan no problem.  I can't believe how fast this is.  Much better than VNC.  I just have a couple questions.

1.  How secure is this?  I know that this needs SSH running but I'm confused about security.  When I create the Windows client session there is an option to use SSL for all traffic.  I am able to connect with SSL on and off.  Is this connection secure?  And what about leaving this open to I can connect from work.  Is that safe?

2.  How do I get this to start at bootup?

Thanks for your help.

---

### Post by zoarre on 2004-12-25
[QUOTE=jdong]I've packaged working freeNX in my warty-extras repository (see the Backports forum).[/QUOTE]

freenx depends upon a version of libstdc++ that I don't have, so I was unable to install it. Anything I can do to remedy this until the 10th? Thx.

---

### Post by PeteG on 2005-01-01
Hi i was wondering if someone could give me some help. I've installed freenx on my linux box which is networked to all the computers in my house via a hub. I can use VNC to remote admin the linux box from my Windows XP computer however i wished to give freenx a try. Everything is installed right, i've setup a nomachine key etc via the original post. I'm using the nx windows client v1.4.0-92 to try get into the linux box. I've setup a user via nxserver adduser [name] and everything. I've got the nx client on the windows box set to Unix>GNOME cause i figured that's what the linux box is running, it's on ubuntu. I tried changing it to VNC and setting it up that way but i got the same error as below. I've also got SSL encryption enabled, i've also tried disabling it. I get this error:

NX> 203 NXSSH running with pid: 3492
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 169.254.125.206 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

Thanks for the help.
Pete.

---

### Post by jdong on 2005-01-01
[QUOTE=Geekboy]Thanks! :)  That backport worked great.  I installed it last night and installed the windows client for my 2000 box at home.  I was able to connect on my Lan no problem.  I can't believe how fast this is.  Much better than VNC.  I just have a couple questions.

1.  How secure is this?  I know that this needs SSH running but I'm confused about security.  When I create the Windows client session there is an option to use SSL for all traffic.  I am able to connect with SSL on and off.  Is this connection secure?  And what about leaving this open to I can connect from work.  Is that safe?

2.  How do I get this to start at bootup?

Thanks for your help.[/QUOTE]
Good, good.

FreeNX goes through ssh security, so it's very secure. I always leave that checkbox checked -- else I get random connection errors. Again, all data through a FreeNX session is SSH encrypted.

2. FreeNX is nothing but SSH with a new user account (nx) with a special shell that talks the NX protocol. So, as long as SSH is started, NX will be started.


Person with libc errors: Post exact errors.

---

### Post by jdong on 2005-01-01
[QUOTE=PeteG]Hi i was wondering if someone could give me some help. I've installed freenx on my linux box which is networked to all the computers in my house via a hub. I can use VNC to remote admin the linux box from my Windows XP computer however i wished to give freenx a try. Everything is installed right, i've setup a nomachine key etc via the original post. I'm using the nx windows client v1.4.0-92 to try get into the linux box. I've setup a user via nxserver adduser [name] and everything. I've got the nx client on the windows box set to Unix>GNOME cause i figured that's what the linux box is running, it's on ubuntu. I tried changing it to VNC and setting it up that way but i got the same error as below. I've also got SSL encryption enabled, i've also tried disabling it. I get this error:

NX> 203 NXSSH running with pid: 3492
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 169.254.125.206 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

Thanks for the help.
Pete.[/QUOTE]
Make sure you used **--setup-nomachine-key** when running nxsetup. Otherwise, you need to carry around the new pubkey to every NX client. We talked about this earlier in the thread.

---

### Post by PeteG on 2005-01-02
[QUOTE=jdong]Make sure you used **--setup-nomachine-key** when running nxsetup. Otherwise, you need to carry around the new pubkey to every NX client. We talked about this earlier in the thread.[/QUOTE]

As stated in my original post i've already done this.

Pete.

---

### Post by limaunion on 2005-01-06
Hello All,

How can I install again freenx ? I made an error and deleted /home/.nx and now when I uninstall/reinstall freenx this directory is not created so when I run nxsetup I get some errors when 'nxsetup' tries to copy the ssh-keys. 


++++++
Searching for nxserver binary...done
Setting up /etc/nxserver/ ...done
Setting up /var/lib/nxserver/ ...done
Setting up known_hosts and .ssh/authorized_keys2 ...open /home/.nx//.ssh/local.id_dsa failed: No such file or directory.
Saving the key failed: /home/.nx//.ssh/local.id_dsa.
mv: cannot stat `/home/.nx//.ssh/local.id_dsa': No such file or directory
mv: cannot stat `/home/.nx//.ssh/local.id_dsa.pub': No such file or directory
chmod: failed to get attributes of `/home/.nx//.ssh/client.id_dsa.key': No such file or directory
chown: failed to get attributes of `/home/.nx//.ssh/client.id_dsa.key': No such file or directory
chmod: failed to get attributes of `/home/.nx//.ssh/server.id_dsa.pub.key': No such file or directory
chown: failed to get attributes of `/home/.nx//.ssh/server.id_dsa.pub.key': No such file or directory
cp: cannot stat `/home/.nx//.ssh/server.id_dsa.pub.key': No such file or directory
+++++++

I want to run again all the installation scripts but uninstalling/installing isn't working (I've tried with 'apt-get --purge remove freenx etc etc)

Thanks for your help!
LU

---

### Post by jdong on 2005-01-06
use mkdir to creat /home/.nx/.ssh

---

### Post by limaunion on 2005-01-06
I'll do that but I'd have preferred to run again the initial scripts as to avoid any kind of mistake, like setting permissions..., it seems that apt can't do this (?)

Thanks for your answer.

---

### Post by jdong on 2005-01-06
I haven't really dissected the debian package to see what it really does. This was the version developed by LinuxTag+Knoppix/Kanotix.

---

### Post by viniosity on 2005-01-10
[QUOTE=jdong]I've packaged working freeNX in my warty-extras repository (see the Backports forum).


It's currently undergoing beta-testing in the -staging tree, I'll have it out of there by Jan 10th.[/QUOTE]

Do you still think this will get into the stable warty-extras today?

---

### Post by jdong on 2005-01-10
It went in already, with issue 4 of Ubuntu Weekly last Friday-ish.

---

### Post by AllTom on 2005-01-17
Which newer version of libpng do I want from the site linked to in the first post? I tried blindly the ones sufficiently new, but not only did they not make the freenx package work, but they also caused KDE to want to uninstall. Are there more detailed instructions on making FreeNX work with Warty?

jdong: Is your FreeNX package supposed to work in warty? I still get the libpng error with it.

---

### Post by jdong on 2005-01-17
AllTom, use Warty Extras (part of Warty Backports). I repackaged FreeNX specifically for Warty.

---

### Post by AllTom on 2005-01-19
[QUOTE=jdong]AllTom, use Warty Extras (part of Warty Backports). I repackaged FreeNX specifically for Warty.[/QUOTE]
Ah, I thought I was using that version before, but apparently Kanotix's version was overriding it, which is why I couldn't resolve the libpng error.

Now I have the same problem as PeteG, even after using "nxsetup --setup-nomachine-key".

Edit: I can log in if I set "PasswordAuthentication yes" in the SSHD config file, which leads me to believe I'm using the wrong key... Doesn't nxclient default to sending its own key?

---

### Post by tomk on 2005-01-21
I'm trying to use FreeNX to conect to a VNC session. I have FreeNX installed and working on my warty box at home, and I'm connecting from my office using the NoMachine Windoze client. I can connect successfully to warty, and it comes up beautifully. Within that NX session, I can open a VNC session to my laptop, which is on the same LAN. 

 I have entered the laptop's details in the client's VNC settings section using the NX Connection Wizard. When I try to connect, I get this error:

```
Parse error in remote options string 'NX>'
```

There are no white spaces in the laptop's host name, by the way.

Any ideas anyone?

---

### Post by oldweasel on 2005-01-27
I am also getting the errors

Depends: nxagent but it is not going to be installed
Depends: nxproxy but it is not going to be installed

Where can these items be found?

---

### Post by limaunion on 2005-01-31
[QUOTE=oldweasel]I am also getting the errors

Depends: nxagent but it is not going to be installed
Depends: nxproxy but it is not going to be installed

Where can these items be found?[/QUOTE]


Same error here, when is it going to be fixed ?   :sad:

---

### Post by Tichondrius on 2005-02-05
I installed FreeNX on my Ubuntu box, and I'm able to connect from a remote windows machine as well as from a VMware windows client. I'm using the NX client from nomachine.com. This is all great, and very fast compared to VNC, but I can't seem to be able to suspend and resume sessions. If I exit the (gnome) session by logging out, then everything is fine, and all the nx processes exit correctly. But if I choose to suspend the session when exiting from the client, then I'm not able to reconnect and resume the session (it fails). Also, sometimes the processes left on the server, especially nxagent, seem to be left in a bad state, and consume 100% of the cpu. The only way to reconnect, is to kill all these processes by hand (and lose the session of course).

So while I like the fact that it's faster then VNC, it cannot serve as a replacement unless the suspend resume (stateless client) feature works reliably.

---

### Post by kdavison007 on 2005-02-06
how did you get past the errors mentioned above?  Same thing I'm getting.

---

### Post by Tichondrius on 2005-02-06
[QUOTE=kdavison007]how did you get past the errors mentioned above?  Same thing I'm getting.[/QUOTE]

you can manually kill all the processes and then it should work. But without suspend/resume like VNC, this is not very useful....

---

### Post by dare2dreamer on 2005-02-07
I've now tried both the ubuntu-backports and kanotix versions of freenx. While both work smashingly, I've run into one visual glitch on several machines running the server that no one seems to be able to provide any insight on fixing.

Once I log into my remote session, several of the icons are missing (and thus show up as a "broken" icon) on my ubuntu desktop. Most notably, everything in the computer menu, the desktop applet icon and the trashcan-applet icon. 

Also, the human theme seems to not render properly, while several other themes work fine. I end up with blue title bars and such when I log in.

As all of these are ubuntu-specific pieces of the desktop, I'm hoping it's something that just requires a bit of tweaking to overcome.

Anyone else experiencing this? Anyone got a fix?

---

### Post by hndrcks on 2005-02-12
First off, many thanks to Jdong for his most excellent backporting work.

Forgive me, as my experience with ssh is primarily text based (OpenBSD firewalls everywhere!)

I have successfully setup sshd to run on an alternate port, say 8822; no problems with manipulating /etc/ssh/sshd_config to make that happen. However, when I run sshd on any port except 22, FreeNX fails, generally with an error that 'smells' like I don't have the proper public key. Any ideas?

It may be obvious that I am working on getting FreeNX through a firewall. There is an alternative way to do this (on the nomachine website) which involves using the ssh client forwarding capability - I recognize this is there but I'd rather have an alternate port solution if at all possible, as the nomachine method requires an account with ssh privilege on the firewall.

Thanks for any and all suggestions! I'll continue to RTFM and will post if I find an answer to my own question.

---

### Post by dare2dreamer on 2005-02-12
hndrcks, I am currently typing this on an NXsession that is running on an ssh session tunnelled through a firewall. The firewall is set up to forward port 22 to my gateway machine (a debian server). When I log in from there, I port forward my desktop's port 22 to localhost:2222 and then tell NX to connect through that.

Works like a charm:

```
ssh -L 2222:desktop:22 server
nxclient (to localhost, port 2222)
```

Hope this helps, saved my butt when I had to "leave town but keep working" recently.

---

### Post by hndrcks on 2005-02-12
Thanks for the prompt reply! You are correct, that works great.

Alas, this is the suggested method on the NoMachine website. I really would like to just run the whole business on a non-standard port. Will keep looking...

---

### Post by dare2dreamer on 2005-02-12
Well, I think I may have a solution to that as well...

A friend of mine currently has his desktop at my place, and he is more or less doing exactly what you are describing. To pull it off, we forwarded some port to his machine from my firewall (I think we ironically forwarded 3389 because it used to be a windows XP machine before we booted it in favor of Ubuntu.)

From there, we told sshd to listen on an alternate port:

from /etc/ssh/sshd_config:

```
# What ports, IPs and protocols we listen for
Port 22
Port 3389
```

In your case, you could remove the port 22 line, thereby disallowing logins completely on the standard port, but to be honest your firewall will stop it anyway if it comes from outside the lan so I wouldn't bother.

If you need a specific port, simply change 3389 to a different port. You might want to make sure it isn't in use by another common service though.

Once you make the change, you'll need to restart sshd in order for it to actually start listening to your new directives:

```
sudo /etc/init.d/ssh restart
```

After that, you should be good to go. Just follow my previous directions, substituting 3389 (or whatever you end up using) for port 22 in the connections.

Now, all he has to do is log in with freenx/ssh to my.external.ip:3389 and he can log in. The only potential problem comes if you try to log in and forget to specify the port...you'll end up hitting wrong machine/no machine at all and make a bit of a mess of your known_hosts file. :-)

Hope this helps.

---

### Post by hndrcks on 2005-02-13
Thanks for the suggestion. *Adding* the extra port to sshd_config, rather than replacing port 22, allowed it to work. When I put only one port in there that wasn't 22, then I got the failure. Go figure...

Anyway, thanks for the suggestion! Mission accomplished!

---

### Post by dare2dreamer on 2005-02-13
As I said, your firewall should stop port 22 (unless you configure it) anyway, so that isn't really a problem. Plus, you can always hit the machine on port 22 within the network.

Glad you got it working!

Now, if we can only figure out the problem with ubuntu icons and freenx

---

### Post by jdong on 2005-02-13
It could be GNOME version specific. I'll package FreeNX for Hoary soon, and we can play with that.

---

### Post by jdong on 2005-02-15
FreeNX for Hoary packaged.

There's no icon bug in Hoary, just in Warty's GNOME.

---

### Post by paul cooke on 2005-02-15
[QUOTE=jdong]FreeNX for Hoary packaged.

There's no icon bug in Hoary, just in Warty's GNOME.[/QUOTE]
 hmm goody, so we can expect to see it in universe shortly? which will be good as the kanotix repository can't be reached currently.

---

### Post by jdong on 2005-02-15
No, I'm not affiliated with Canonical.

It's in Hoary Extras: [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

### Post by dare2dreamer on 2005-02-15
While it won't matter once people start upgrading to hoary, is there any way to fix the bug on existing warty installations?

---

### Post by jdong on 2005-02-15
Hmm, well, I'm stumped. It's apparently a GNOME bug. It doesn't happen with KDE or XFCE (gtk based, even!) on Warty, it doesn't happen in GNOME in Hoary. That means it's something about Warty's GNOME.

---

### Post by dare2dreamer on 2005-02-15
Considering that the problem appears in the custom computer menu, the ubuntu-specific applets like the trash can and in the human theme's colors, I had more or less surmised the same thing.

At a guess, it seems like freenx doesn't know where to look to grab the icon/theming information for these human/ubuntu specific pieces.

Perhaps a symlink in the right place would solve the problem?

I looked around, and couldn't see anything obvious, but then my fu is certainly not as mighty as yours. ;-)

---

### Post by Tichondrius on 2005-02-16
Are  you people able to suspend and resume freenx sessions ?

---

### Post by Tichondrius on 2005-02-16
[QUOTE=jdong]No, I'm not affiliated with Canonical.

It's in Hoary Extras: [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)[/QUOTE]
 can't find it with hoary-amd64

---

### Post by dare2dreamer on 2005-02-16
I can suspend and resume with no issues.

---

### Post by jdong on 2005-02-16
[QUOTE=Tichondrius]can't find it with hoary-amd64[/QUOTE]

No AMD64 or PPC packages --  need devs for these two archs.

---

### Post by marko on 2005-02-23
[QUOTE=jdong]

It's in Hoary Extras: [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)[/QUOTE]

I am trying my best here and feeling pretty helpless..  I added backports.ubuntuforums.org extras to my sources.list, and after apt-get update, still see no sign of freenx.  What am I doing wrong?

---

### Post by dare2dreamer on 2005-02-23
post a copy of your /etc/apt/sources.list

---

### Post by marko on 2005-02-23
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

Then I apt-get update and look for the Freenx package and I see no such thing in synaptic..  I thought this would be pretty straight forward..  Do I need the other line as well?

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted

Thanks for any tips.

---

### Post by dare2dreamer on 2005-02-23
Try adding a forward slash to the end of the url:

```
deb http://backports.ubuntuforums.org/backports/ hoary-extras main universe multiverse restricted
```

Should do the trick.

---

### Post by marko on 2005-02-24
Did it.  No workie..

Strange, here is the output from apt-get update.  The thing that jumps out is the IGN..  What does that stand for, ignored or something?

Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras Release.gpg
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras Release
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages
Fetched 82B in 1s (49B/s)
Reading Package Lists...

---

### Post by hndrcks on 2005-02-24
You have warty-backports specified in the repository, and you are on hoary, hence apt ignores the repository.

(I did that once too!)

Edit: Actually, upon reflection, maybe you didn't do that. I need more sleep!

---

### Post by dare2dreamer on 2005-02-24
Remind me to stop answering help questions in the middle of the night, I completely missed the warty/hoary thing.

:-p

---

### Post by marko on 2005-02-24
So what am I doing wrong then?  Any clues..  Thanks much for the analysis.

---

### Post by Leif on 2005-02-25
I'm getting the exact same error as marko - hoary-extras ignored. Will go back to a rep that I know works (deb [http://debian.tu-bs.de/knoppix/nx/slh-debian/](http://debian.tu-bs.de/knoppix/nx/slh-debian/) ./), but I'd rather use a build that's ubuntu-supported. Plus, this one has problems with suspend/resume, I'm hoping the hoary-extras one doesn't.

---

### Post by jdong on 2005-02-25
FreeNX for Hoary is in the hoary-extras-**staging** distribution. I don't know whether or not libpng's ABI's gonna change before Hoary's release, so I'm not marking it stable!

---

### Post by Rottweiler on 2005-02-25
[QUOTE=jdong]FreeNX for Hoary is in the hoary-extras-**staging** distribution.[/QUOTE]I took the sources.list directly from here: [http://backports.ubuntuforums.org/]("http://backports.ubuntuforums.org/") (bottom of the page). It still doesn't work. Changed it to say hoary-extras-staging, still ignores them. Something is broke somewhere.

Here's my sources.list line:```
deb http://backports.ubuntuforums.org/backports hoary-extras-staging main universe multiverse restricted
```Any help appreciated.

---

### Post by hndrcks on 2005-02-26
Just flush and reload the package data:

```
sudo dselect --expert update quit
```

Then they should update fine.

---

### Post by adun040 on 2005-02-27
OK, getting FreeNX to run was a breeze. Everything is functional, and very quick.

I've noticed a problem with Gnome theme and icons - the Human theme didn't load correctly, and some of the icons were missing - like the Show Desktop, and Trash. I googled for it, and found that others in this thread are having this problem. I think I've found a workaround.

I'm running Hoary, but this should work with Warty too. The workaround is to disable GDM on the server - which means you won't have nice graphical login prompt, but everything will run smoother remotely.

Try this - inside your NX session open a terminal. Then run

sudo /etc/init.d/gdm stop

Your theme should instantly fix itself as GDM shuts down. To make this permanent, remove /etc/rc2.d/gdm and upon next reboot you will have a console login prompt (of course you can login that way and run startx) and NX will work with the correct theme. 

Although, interestingly enough, more than one session with the same login into the system will again show corrupted theme; simultaneous logins from different accounts do not have this problem. I hope this has been helpful; it's not a full fix however. I'm interested to find out why this problem occurs and if anyone has found an actual solution to the problem.

If you are still having problems, try this walkthrough, it might also help. 

[http://women.alioth.debian.org/wiki/index.php/English/BuildingTutorial](http://women.alioth.debian.org/wiki/index.php/English/BuildingTutorial)

---

### Post by ryharv on 2005-02-28
Hello everyone,

After reading this guide, I'm trying to install FreeNX on Warty.  My sources.list looks like this:

> 
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-extras main universe multiverse restricted


But when I run **apt-get update**, and then **apt-get install freenx**, I get the following error message:

> 
sudo apt-get install freenx
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  freenx: Depends: nxclient (>= 1.4.0-75.2) but it is not going to be installed
E: Broken packages

I saw a couple other people post the same error message, but I couldn't decipher any solutions.  Ideas?  Many thanks.

---

### Post by lm05 on 2005-03-01
Has anyone got the inbuilt sound forwarding support working with FreeNX?

I am using a WinXP client, and the only way I have got it to work is by doing manual Esound forwarding using the method at this site:
[Esound Forwarding](http://www.liquid-reality.de/main/projects/esound) 

Works well, but I'd like to get the inbuilt support working.

LM

---

### Post by Golovko on 2005-03-03
I have seen a few posts  detailing problems with trying to install freenx from backports. Some of these seem to be associated with the person running warty and freenx is currently hoary-extras-staging? I myself am running pure hoary right now.

Could someone share where exactly I should point my sources to get freenx?

Gol

---

### Post by ryharv on 2005-03-03
it's in warty-extras and hoary-extras.  you need to setup your sources.list to include:

> deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-extras main universe multiverse restricted 

and uncomment the lines 

> # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe 

Obviously, replace "warty" with "hoary" if you use hoary.

---

### Post by nevc64 on 2005-03-06
[QUOTE=Rancoras]Ok, I've gotten a little further.  I got the appropriate key copied to the client.  Now, I'm getting this output:

--snip--
Info: Established X server connection.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.
[/code]

I can't find anything about that error on google other than someone else asking for help.[/QUOTE]

 ](*,) 

I've researched this about as best as I can. Still have the problem of the sessions starting, screen appears with the !M logo, then the client says the connection has failed with same details as Rancoras above, namely  
"Info: End of session requested by remote proxy. etc"

In this forum I have found references to the chmod issues that affect SSH and have modified the appropriate directory and file permisions to 700.

I am using freenx on Warty and have been testing using the Windows NXClient on Windows 98. In setting up I used the"nxsetup --setup-nomachine-key" as advised in the first post to this thread.

I have had some success with the connection being maintained but this is when I have changed the NXClient configuration to KDE. The result is that the connection seems to be made and is not reset but the screen remains blank (as expected I guess as KDE is not install on the server).

Any other suggestions. Perhaps turning on additional logging for SSH. How do I do that? Where do I find the log? What about trying to find more info about what "nxproxy" is doing? Is there a way to do that?

Any tips appreciated.

Thanks
Neville

---

### Post by joplass on 2005-03-07
Since there is no guide to do this I guess I will ask an "ignorant" question.  Everything looks good according to this now how do I go by to communicate from a windows box?  How does one start freenx?
Thanks

job@ubuntu:~ $ sudo nxsetup --setup-nomachine-key
Searching for nxserver binary...done
Setting up /etc/nxserver/ ...done
Setting up /var/lib/nxserver/ ...done
Setting up known_hosts and .ssh/authorized_keys2 ...done
Setting up permissions ...done
Ok, nxserver is ready.

PAM authentication enabled:
  All users will be able to login with their
  normal passwords.

You can change this behaviour in the nxserver script.
Have Fun!
job@ubuntu:~ $

---

### Post by incubus on 2005-03-07
hey there jo,

After the nxsetup script, you need to run:
```
sudo nxserver --adduser <username>
``` 
to allow your <username> to login. 
Try "sudo nxserver --help" for other options.

You said you want to play around with a windows box. So, drop by [nomachine](http://www.nomachine.com/) and get the latest nxclient for windows. You'll need administrator privileges to install that one.

You should have no problem with connecting if you've set up your nxserver and your ssh correctly. However, if you want to use a non-standard port for SSH (i.e. not 22), you'll need to edit manually the /etc/ssh/sshd_config AND the /usr/bin/nxserver files (strange isn't it). 

Troubleshooting:
If something goes wrong, as it usually does, you should test your connection in the first place. Try to connect to your Ubuntu from Windows with [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)  . Also try to connect from your own machine to localhost (127.0.0.1), using different desktop environments (select gnome, kde, or custom in the nxclient settings). Oh and remember to double-check port, proxy, and firewall before going into despair.

Hope everything works out there.

Cheers,
incubus

---

### Post by joplass on 2005-03-08
I will get to it today.  One thing tho, what IP do I put in Putty since I have a router going.  Is the one from my ISP or the one for the router?  Anyway I will try both.  I don't see how it will not work.  I can still rely on this thread. 
Thank you,

---

### Post by incubus on 2005-03-08
Hi joplass, 

That depends on whether you want to connect to your Ubuntu machine from inside or outside your LAN, so let's get to the answer in two parts. The numbers I'll use are merely illustrative.

1. Inside: Suppose your Windows box is sharing the internet with your Ubuntu. If this is the case, you need to find out the IP your router has set to the boxes. As you may know, the router has an internal IP (usually 10.0.0.138 ) and your boxes receive different ones (e.g. 10.0.0.139, 10.0.0.140, etc).

2. Outside: If you're willing to connect to your Ubuntu from the box at your work, like me, you need two things. Firstly, as you said, you'll need the IP of your connection at home. You can use [checkip.dyndns.org](http://checkip.dyndns.org) to get that. Secondly, you need to set up your router to redirect your SSH request to the Ubuntu box (through the NAT service). If you don't know how to do that, google for instructions for your router model. But just for details, you need to create a port 22 redirection from outside your network (0.0.0.0) to your specific box (10.0.0.139, for example).

If everything fails, you can always count on the Ubuntu community.

Good luck,
incubus

PS: You don't need PuTTY for your NX connection, I just mentioned it for testing, ok? At your windows, it's just the NXClient you need, unless you use a proxy service for internet. Well, that's enough for one post.

---

### Post by joplass on 2005-03-09
Sorry about this reply I rushed to ask the question.  Someone posted about it on this same thread.

---

### Post by joplass on 2005-03-09
NX> 203 NXSSH running with pid: 1848
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: xxx.xx.xxx.xxx on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
**NX> 204 Authentication failed.**
I also did this already as mentioned in a post somewhere in here.
“Make sure you used --setup-nomachine-key when running nxsetup. Otherwise, you need to carry around the new pubkey to every NX client. We talked about this earlier in the thread.”

Thanks for the help!

---

### Post by incubus on 2005-03-09
Hey joplass:

It seems you tried to connect from outside your network, right? I recommend you to EDIT your former post and hide/fake your real IP (well, perhaps you've already done that).

Well, now you can try what I said before: use PuTTY to connect to your computer, just to see where the problem is (i.e. if it connects, the problem should be with nx). You should also try in your own ubuntu computer to connect to itself (localhost). This will tell us if the problem was with the remote computer or with the nxserver configuration.

By the way, have you added your login with the nxserver (--adduser) and typed this same username to connect? 

incubus

---

### Post by joplass on 2005-03-09
Yes added the user with the nxserver and I am trying to login from work.

PuTTy returned this (I typed the whole thing couldn't copy/paste):

loging as: <myusername>
Password: 
Linux Ubuntu 2.6.8.1-5-383 #1 Sat Feb 12 00:19:31 UTC 2005 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
The exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABOLUTELY NO WARRANTY, to the extent permitted by applicable law.
You have mail.

Last login: Wed Mar  9 10:33:35 2005 from revlookup.maintech1.com
job@ubuntu: ~ $

---

### Post by incubus on 2005-03-09
Good, so your connection and the SSH are working alright. Through Putty/SSH you can control your box already, but without the X environment.

Find a folder ".ssh" in your "\Documents and Settings\<username>" and delete it (it just holds a copy of the authentication key, nx will download a new one). Open your Windows NXclient, click Configure and in the "Advanced" tab, check "Enable SSL encryption" if it's not already checked. In the "General" tab, make sure that you typed in the same IP and Port numbers you used in the PuTTy. And login with the same username too (the one you wrote in nxserver --adduser).

Tell me if you still get the same error.
By the way, connect PuTTy again and do a "sudo nxserver --listuser" and see that your username is there.

Best,
incubus

---

### Post by joplass on 2005-03-09
Sincere thanks for your valuable help. 

When I clicked login on NX and it was login in I got this message also included in the script below:

 The authenticity of host 'xxx.xx.xxx.xxx (xxx.xx.xxx.xxx)' can't be established.
RSA key fingerprint is fd:12:06:30:9e:79:91:6d:17:ad:8a:31:b7:18:9a:5a.
Are you sure you want to continue connecting
 “yes” or “no”  

NX gave me this:

NX> 203 NXSSH running with pid: 4984
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: xxx.xx.xxx.xxx on port: 22
NX> 205 The authenticity of host 'xxx.xx.xxx.xxx (xxx.xx.xxx.xxx)' can't be established.
RSA key fingerprint is fd:12:06:30:9e:79:91:6d:17:ad:8a:31:b7:18:9a:5a.
Are you sure you want to continue connecting (yes/no)? 
Warning: Permanently added 'xxx.xx.xxx.xxx' (RSA) to the list of known hosts.
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

PuTTY gave me this after “sudo nxserver –-listuser”:

job@ubuntu:~ $ sudo nxserver –-listuser
NX> 100 NXSERVER – Version 1.4.0-02 OS_(GPL)
NX> 146 NX users list

Username
---------------------
job

NX> 999 Bye
job@ubuntu:~ $

---

### Post by incubus on 2005-03-09
Hmmm. I think we're getting close to it, pal.

I had that problem too, and I googled a lot to find out how to fix that. I can't recall what I did, but it had to do with the keys. The problem was that I installed freenx without the "--setup-nomachine-key", and it persisted even though I corrected that.

When you first installed freenx, did you run the setup with "--setup-nomachine-key"?
If not, maybe we should delete the files it created in the process.

Take a look at this [interesting discussion](https://listman.redhat.com/archives/k12osn/2005-February/msg00087.html) 
Note that this is a discussion on RedHat, I think it will be a little different on ubuntu.

See if you have:
/usr/NX/share/client.id_dsa.key

Try:```

cd <directory where the key is located>
sudo mv client.id_dsa.key client.id_dsa.key.bak
sudo nxsetup --setup-nomachine-key
```
Fire the nxclient again.

Now, if you had used the "--setup-nomachine-key" in the first place, I would uninstall the freenx (sudo apt-get remove --purge freenx nxclient nxserver nxproxy nxagent) and clean-install it again.

Just a tip: try to copy a significant part of the error message into google and see what you find. That's what I usually do.
Anyway, tell us what you got there.

Best,
incubus

---

### Post by joplass on 2005-03-10
Incubus,
I want to thank you for your assistance.  Individuals of your kindness and dedication make the Linux community in general and the Ubuntu community in particular very appealing.  Although I follow your guidance to the best of my knowledge, I could not make Freenx work for me.  I will leave it until this weekend hopefully the wife will give me some room because I really want to access my Ubuntu box from work. 

Be well my friend!
joplass

---

### Post by marko on 2005-03-13
I am in the same boat as you.  I really don't understand why some people seem to breeze through this install and some (like us struggle mightily..

I finally managed to install freenx (with the right deb source) and setup with nxsetup, not reading carefully enough about the need for the nomachine-key..  Have tried to rename the config.key, have agt-get remove and re-installed..  All to no avail.  Still same error as you.

Looking forward to any more tips..

Yuk!

---

### Post by jdong on 2005-03-13
Reinstalling after messing up the --setup-nomachine-key is extremely tricky. Usually, you need to remove /home/.nx, remove (purge), then reinstall.

---

### Post by joplass on 2005-03-13
[QUOTE=jdong]Reinstalling after messing up the --setup-nomachine-key is extremely tricky. Usually, you need to remove /home/.nx, remove (purge), then reinstall.[/QUOTE]

Youd do this manually or at the command line.

---

### Post by joplass on 2005-03-13
[QUOTE=marko]I am in the same boat as you.  I really don't understand why some people seem to breeze through this install and some (like us struggle mightily..

I finally managed to install freenx (with the right deb source) and setup with nxsetup, not reading carefully enough about the need for the nomachine-key..  Have tried to rename the config.key, have agt-get remove and re-installed..  All to no avail.  Still same error as you.

Looking forward to any more tips..

Yuk![/QUOTE]

I just hope someone can post their own steps here so we can try them as well.

---

### Post by marko on 2005-03-14
To summarize, I think I have done everything wrong possible and now have a working NX server on Ubuntu!  =)  This is for a LAN environment though.  Review this thread for WAN installs.

To avoid my pitfalls running FreeNX on Hoary, start by adding this line to your /etc/apt/sources.list

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras-staging main universe multiverse restricted

Run apt-get install freenx.

Make sure SSH is running for FreeNX to work properly (ps -ef|grep ssh).

To get a working install of nxserver, you will want a nomachine key (RECOMMENDED FOR SIMPLICITY) by running nxsetup --setup-nomachine-key. Please google the command and read the security implications of doing so! (Basically if FreeNX is flawed, there's a possibility of gaining SSH access as the NX user remotely!)

To verify that all is well with nxserver, run the following:

nxserver --status

If nxserver is not running, you may need to check and see if the directory /home/.nx/.ssh was created correctly.  If not, you may need to manually create it (mkdir /home/.nx && mkdir /home/.nx/.ssh) and re-run nxsetup --setup-nomachine-key.

Check status again.  If nxserver is running, see what users are defined for usage (nxserver --userlist).  Likely, this will be empty on your first attempt.  If so, run nxserver --adduser, then assign a passwd.

----------------------------

If you, like me, managed somehow to run nxsetup (without --setup-nomachine-key), you may need to clean up after yourself.  To do this:

remove /home/.nx (rm -r /home/.nx)
recreate the directory structure (mkdir /home/.nx && mkdir /home/.nx/.ssh)

Remove freenx (sudo apt-get remove --purge freenx nxclient nxserver nxproxy nxagent) and clean-install it again.  And make sure to run nxsetup --setup-nomachine-key this time..

---

### Post by A-star on 2005-03-16
Any Idea,  how I connect with the NX client from nomachine.com through a proxy server (our company has one for all outgoing connections), or can someone tell me all the ports the NXclient is using?

---

### Post by jdong on 2005-03-16
FreeNX operates through port 22, ssh.

---

### Post by incubus on 2005-03-19
A-star,

I had the same issue when trying to access my Ubuntu box from my work (using Windows), where there is a proxy server too. The problem is that the NXClient has no options for proxy connection (at least none that I know of). 

I proceeded in the following way:
1. I set a connection to my home Ubuntu through PuTTy, which has the option for proxy server. 

2. I created two port-forwards in the PuTTy session: one for port 22, another one for port 5000 (if this one fails, it will try the subsequent ones, 5001, 5002, etc). The NXClient will use this port for the X (I guess this is what you asked). 

3. In the NXClient I disabled "SSL encryption for all traffic", since I was already connecting through secure shell. Then I set it to connect to localhost at the port 22 redirected by PuTTy. Bingo: FreeNX through proxy.

Tell us if you have any problem.
I sincerely hope someone comes with a better solution than mine.

Cheers,
incubus

---

### Post by A-star on 2005-03-21
Thanks for the info, will try it this evening.
> 
1. I set a connection to my home Ubuntu through PuTTy, which has the option for proxy server.

What did you use to accomplish this?

I know how to setup up FreeNX ( at least I hope so). but what I don't know is how to make a connection with putty to my pc at home (which software to use).

---

### Post by incubus on 2005-03-21
A-star:

PuTTy is itself a program for Windows to get you a Secure Shell (SSH) terminal. As you may know, FreeNX uses SSH to connect and transfer all data, so it is encrypted, safer, and more reliable -- at least in theory.

You can download PuTTy here:
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) 
Make sure you read the FAQ and Docs on that page.

These are the steps I used to connect through the proxy server. I hope I can make myself clear.

PuTTy
1. Run PuTTy in your windows box.
2. Fill in your IP and the port (usually 22). Be sure to check the SSH option.
3. In the category tree (left panel), click "Proxy", which is under "Connection". Fill in the fields required by your Proxy Server. (usually Proxy Type, Host, Port, and user/pass)
4. Click the "Tunnel" category. Now you're gonna create two tunnels. I'm assuming you use the default ports. 
4.1. In the "Source Port" field, write "22", and in the "Destination", "localhost:22". Click Add.
4.2. Do the same for port "5000" and destination "localhost:5000".
5. You may want to save these settings if you don't want to do everything again for every connection. In the "Session" category, write down a name and click "Save". 
6. Click Open to connect.

NXClient
1. Run the Windows NXClient and click "Configure".
2. Now you're gonna connect to the tunnel you've just created. The host is "localhost" and the port is "22". When you connect to this, PuTTy will tunnel the data to your home machine.
4. In the "Advanced" tab, I un-check "Enable SSL Encryption".
5. Try to connect now.

Good luck!
incubus

---

### Post by A-star on 2005-03-22
I tried it exactly like you said but now I get this error message:
```
NX> 203 NXSSH running with pid: 3832
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 127.0.0.1 on port: 22
ssh_exchange_identification: Connection closed by remote host
```

I can ssh to my server (with plain password not with the public/private key).
And my ssh server is answering on port 8022 (all ports under 1024 are blocked by my provider).

Kind regards
A-star

---

### Post by santo on 2005-03-22
How can i use FreeNX to connect to my current session/desktop, so I can
continue the work I already started (i.e. like VNC/Krfb does) ?

---

### Post by incubus on 2005-03-22
Hey A-star:

There's a strange problem with former versions of NXserver. Even though you set the SSH server to a port, such as 8022, the nxserver is still listening port 22. 

One solution is to manually edit the /usr/bin/nxserver file:
sudo cp /usr/bin/nxserver ~/nxserver.bak      #backup first
sudo nano /usr/bin/nxserver

Find an entry which reads:
SSHD_AUTH_PORT = "22" 
And change it to the port you want.
Remember to "sudo nxserver --restart".

Another workaround if you're behind a router is to leave settings on default, and create a NAT service redirecting all outside requests from a port, like 8022, to your box at port 22.
0.0.0.0:8022   to   <your ip>:22

Best,
incubus

---

### Post by A-star on 2005-03-22
[QUOTE=incubus]
Find an entry which reads:
SSHD_AUTH_PORT = "22" 
And change it to the port you want.
Remember to "sudo nxserver --restart".
[/QUOTE]

I'll try that this evening.
thanks for all the help so far.

Kind regards
A-star

---

### Post by Lord C on 2005-03-22
I have installed FreeNX, Using Synaptic in Hoary.

It all seems to be running, but I can't connect to my PC from a remote location.
**Connection Timeout** is all I see.
I have fowarded port 22.

sshd seems to be running.

When I type nxagent it says display 0 is in use.
I try nxagent :1 and some black window opens.

I'm not sure what im supposed to do to run this program, it isnt as simple as vnc heh.

```
~$ sudo nxserver --status
NX> 100 NXSERVER - Version 1.4.0-03 OS (GPL)
NX> 110 NX Server is running
NX> 999 Bye

``` 

Any help is appreciated, thanks.

---

### Post by incubus on 2005-03-22
Lord C:

Tell me, have you tried to:
1. Connect to your box through straight SSH?
("ssh <your ip>", for example. If you're under windows, use PuTTY.)

2. Connect through NXClient at your own box?
(run "nxclient" and try to connect to localhost at 22)

With your feedback (and other details you think important) we can probably find a solution.

Best regards,
incubus

---

### Post by Lord C on 2005-03-23
[QUOTE=incubus]Lord C:

Tell me, have you tried to:
1. Connect to your box through straight SSH?
("ssh <your ip>", for example. If you're under windows, use PuTTY.)

2. Connect through NXClient at your own box?
(run "nxclient" and try to connect to localhost at 22)

With your feedback (and other details you think important) we can probably find a solution.

Best regards,
incubus[/QUOTE]
 I connected to my localhost - ew, i paniced when i didnt know how to get out of it, lol.
Logging out did the trick.

I shall try ssh in a moment.

---

### Post by A-star on 2005-03-23
a new day a new error message:
I have almost succeeded in my effort.
Now I get this error message:
```

NX> 203 NXSSH running with pid: 676
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 127.0.0.1 on port: 8022
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.

```

Any clues?

---

### Post by incubus on 2005-03-23
A-star:

Yes, you're close. A new error message is good news.

Now tell me one thing, how was your installation of FreeNX? Do you want it to use a public key? If you do, have you set it up with "nxsetup --setup-nomachine-key" in the first attempt? If you haven't, try to move/rename the files inside "/home/.nx/.ssh/", and run that command again. 

Also make sure you're on the list of "nxserver --listuser". You can try to remove and add your user to the list again. You can also see if there's something wrong with your "authorized keys" and "known hosts" in your "~/.ssh/" directory. Try to move/rename them.

If you want to make sure the FreeNX is working, create yourself another user and try that new one. Just remember to delete it afterwards.

Good luck, my friend.
incubus

---

### Post by A-star on 2005-03-23
[QUOTE=incubus]Now tell me one thing, how was your installation of FreeNX? Do you want it to use a public key? If you do, have you set it up with "nxsetup --setup-nomachine-key" in the first attempt?[/quote] Yes I set it up with the  "nxsetup --setup-nomachine-key" command (with sudo because else it wouldn't let me do it).
> If you haven't, try to move/rename the files inside "/home/.nx/.ssh/", and run that command again. I'll try that this evening if it doesn't work
> Also make sure you're on the list of "nxserver --listuser". You can try to remove and add your user to the list again. You can also see if there's something wrong with your "authorized keys" and "known hosts" in your "~/.ssh/" directory. Try to move/rename them.will also try that this evening.
> If you want to make sure the FreeNX is working, create yourself another user and try that new one. Just remember to delete it afterwards.
Good suggestion, I'll also try this (begins to sound boring ;) )
I will keep you posted as I go along.
and thanks for the help so far.

Kind regards
A-star

---

### Post by incubus on 2005-03-23
Lord C -

Good! So your freenx is set up correctly.
I think the problem should be with your keys or with SSH itself. What do you get when you connect to your home box from outside with ssh or putty?

Check out a few conversations, like those of Joplass and A-star (and others), see that you've followed what the guys have already troubleshooted.

Tell us the results!
Best,
incubus

---

### Post by A-star on 2005-03-23
Okay, here some more info about what I tried.

I deleted everything in the /home/.nx/.ssh folder and ran the nxsetup --setup-nomachine-key again -> same error message as before.

I deleted everything in ~/.ssh -> same error message.

I created another user and tried with that. -> same error message.

In the beginning I tampered a little bit with the config file of ssh, so I think the problem is there.
I will deinstall, delete every config file and reinstall ssh en freenx this evening and see what that gives. -> unless someone can post their unmodified config-files here so I can copy them over.

Thanks

Kind regards
A-star

---

### Post by incubus on 2005-03-23
A-star:

Clean installing is a good idea, but before doing that, what do you get if you try to connect your nxclient at home (localhost:8022)? The same message?

If you will proceed, pay attention to the following things: 
1. Which repository are you using? You're under Hoary, right? Are you using the backports' debs?

2. Purge every single file:
"sudo apt-get remove --purge freenx nxserver nxclient nxagent libnxcomp0 libnxcompext0 nxlibs"

These are the files I remember freenx uses. Make sure you manually delete the /home/.nx/.ssh files too. And the keys under your "~/.ssh".

And don't give up!

Regards,
incubus

---

### Post by A-star on 2005-03-23
[QUOTE=incubus]A-star:

Clean installing is a good idea, but before doing that, what do you get if you try to connect your nxclient at home (localhost:8022)? The same message?[/quote
I get this message:
```

NX> 203 NXSSH running with pid: 676
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 127.0.0.1 on port: 8022
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.
```

> If you will proceed, pay attention to the following things: 
1. Which repository are you using? You're under Hoary, right? Are you using the backports' debs?
I'm using warty at this moment with the backports enabled


> 2. Purge every single file:
"sudo apt-get remove --purge freenx nxserver nxclient nxagent libnxcomp0 libnxcompext0 nxlibs"
These are the files I remember freenx uses. Make sure you manually delete the /home/.nx/.ssh files too. And the keys under your "~/.ssh".
I'll try that this evening, since I have no physical access to the machine this evening.

> And don't give up!
I won't  :)

kind regards
Filip

---

### Post by incubus on 2005-03-23
Hey A-star,

By reading your log it seems to me that there's still something wrong with the keys freenx uses to authenticate in your SSH. 

I'm not a computer scientist -- actually I'm a political scientist --, so this is a guess. Try to check if you have similar (not identical) "known_hosts" and "authorized_keys" in: 
/var/lib/nxserver/home/.ssh/
/home/.nx/.ssh/

If things don't work out, maybe you'd better reinstall it. 
But you're very close to using freenx.    :-)

incubus

---

### Post by A-star on 2005-03-23
Yes,

After I deleted the old config files and reinstalled everything it began working.
Thanks everyone for the help,
I'm just a happy ubuntu-user now.

Kind regards
A-star

---

### Post by incubus on 2005-03-23
Great, A-star!
I'm happy you did it, congratulations.
I think freenx is really good, though it does need a few improvements.

See ya 'round!
incubus

---

### Post by Gman on 2005-03-28
I setup freenx yesterday and it's working perfectly. However, I want the monitor connected to the host to show what i'm doing on the client. Is that at all possible with freenx? If so, what should I do to get it working the way I want to?

---

### Post by garyng on 2005-03-28
[QUOTE=Gman]I setup freenx yesterday and it's working perfectly. However, I want the monitor connected to the host to show what i'm doing on the client. Is that at all possible with freenx? If so, what should I do to get it working the way I want to?[/QUOTE]

No. I believe you can use VNC to do this.  VNC is more mature than freenx. freenx is more for simpler(safer) remote desktop usage, as RDP in Winow world, and speed over very slow link.

---

### Post by Leif on 2005-04-03
[QUOTE=garyng]No. I believe you can use VNC to do this.  VNC is more mature than freenx. freenx is more for simpler(safer) remote desktop usage, as RDP in Winow world, and speed over very slow link.[/QUOTE]

That's like saying Evolution is more mature than Firefox because it handles emails better. VNC and freenx are meant to do quite diffferent things: VNC gives you control of a remote desktop, freenx gives you a session in a remote machine. Personally, I've been using freenx regularly for the last 4 months or so and it's been quite excellent.

---

### Post by fire59 on 2005-04-14
Does anyone have a repository for ppc arch?  I'm running ubuntu on my g4 and want to get freenx running on it.

---

### Post by btdown on 2005-04-14
Could someone please tell the right way to get FreeNX on 5.04? I've seen the instructions at the beginning of this thread but have been hesitant to use it because I dont want to screw anything up using something that wasnt specifically meant for 5.04.  I tried a regular apt-get install for freenx using the repositories in suggested on ubuntuguide.org but none of them had the package. I'd like it to work, but dont want to screw anything up. Any ideas?

Thanks,
BT

---

### Post by Daz on 2005-04-26
Hi there btdown,

I've put together a short [guide](http://oakley.bioinformaticsonline.co.uk/?q=node/18) on my web-site for setting up FreeNX on Hoary. 

That should sort you out, if you get any troubles, let me know.  :-) 

Daz.

---

### Post by btdown on 2005-04-26
Thank you! Am checking it out right now...
BT
 
UPDATE: Didnt work at first, but after I removed and purged all the files, as well as all the .nx and .ssh files and reinstalled, it did work fine. I chose to use the default nomachine keys.
 
I do get a gnome error after I've successfully logged in... a "Error activating XKB configuration". I just close the error and I dont think it affects anything, but its annoying. Anyone else run into this or know how to correct?

---

### Post by Daz on 2005-04-27
I also get those errors - but only when I am using a laptop to log-in to my PC.

Are you using a laptop to remote log-in as well?

From what I can work out this is just because the X server on the laptop (client) has a different keyboard layout/config to the one that Gnome expects from normal use.  It doesn't do any harm, it's just annoying.  Basically, just close the errors down.

I think once in a while you may get a 'do not show me this error again' option, but other than that i've not found a way to stop them coming up.

Sorry.

---

### Post by t3rror on 2005-05-02
***EDIT***

Nevermind guys, I was able to get SSH tunneling of VNC working properly, and this is all I need.  Thanks.

***EDIT***

I have followed the instructions on Daz's website, and everything goes fine.  When I try to connect, the client connects fine and authorizes fine, and even brings up the indow it will eventually put the session in, but then it craps out and gives me the followinf details.  Can anyone help?  I am running the client on WinXP SP2 and the server on Ubuntu Hoary 5.04.  TIA.

NXPROXY - Version 1.4.0

Copyright (C) 2001, 2004 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '1756'.
Info: Waiting for connection from any host on port '3574'.
Info: Accepted connection from '127.0.0.1' on port '3654'.
Info: Connection with remote proxy established.
Info: Handshaking with remote proxy ':5000' completed.
Info: Synchronizing local and remote caches.
Info: Not using NX delta compression.
Info: Using lan link parameters 16384/80/16/8192.
Info: Using pack method '16m-jpeg-9' with session 'unix-gnome'.
Info: Not using ZLIB stream compression.
Info: Not using remote ZLIB stream compression.
Info: Not using persistent cache.
Info: Using remote server connected on port '3574'.
Info: Starting X protocol compression.
Info: Established X server connection.
Warning: Not using shared memory support in X server.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.

---

### Post by Daz on 2005-05-03
Hi t3rror,

I have seen this error before too, :mad: but i've only ever got it once...

I had no idea what was causing it, but found a slightly annoying solution (well, it worked in my case).

It seemed that something in my user settings on the Ubuntu box had went slightly iffy.  All I did was make another user account, and I was able to happily log-in on that!

Then, just to make matters even more confusing - I set NX up on another Windows XP box - tried to log-in on my original account and it all started to work!  ](*,) 

I think the first thing you need to do is to try the second user account approach, and fingers crossed this should work for you.  Then to make life more managable on the new account just add it to the sudoers list all will be fine (i.e. you'll have full admin rights on the new account and can remove the old account if needs be).

If you have another PC about, it might be worth trying another install of the NX client on there - I have absoloutley no idea why it suddenly fixed it, but everything seemed to work after that for me!

Hope this helps, let us know how it goes.

---

### Post by waster on 2005-05-04
One great use of NX seems to me to be the ability to run an application on its own without the desktop. E.g. use Firefox (with all my extensions and bookmarks, etc.) from work on a Windows PC, but running the application on my computer at home.

It doesn't quite work. I can get firefox running (a bit slowly), but the user is not me, so I don't get any of my settings. How do I run an NX session as myself, so it would get firefox prefs from my home directory?

Jack

---

### Post by MemoryDump on 2005-05-09
[QUOTE=santo]How can i use FreeNX to connect to my current session/desktop, so I can
continue the work I already started (i.e. like VNC/Krfb does) ?[/QUOTE]

does anybody know how to set this up? I would rather resume/connect to a currently logged in session rather than starting a new one.

Thanks
-MD

---

### Post by sebwills on 2005-05-14
I too was getting the same error as t3rror (and someone else earlier in this topic): nxclient would connect, open up the window (showing the big !m logo) but then the window would close a moment later.

I think in my case it was caused by a locking problem with my .Xauthority file. On the machine you are connecting to, check for files called ".Xauthority-l"  and ".Xauthority-c" in your home dir. Delete them if they exist. This seems to have solved the problem for me.

---

### Post by Lawen on 2005-05-14
[QUOTE=Daz]
I've put together a short [guide](http://oakley.bioinformaticsonline.co.uk/?q=node/18) on my web-site for setting up FreeNX on Hoary. 
[/QUOTE]

Great guide Daz, you had me up and working in about three minutes flat. Thanks.

---

### Post by Drain on 2005-05-17
I was all excited when I read through Daz's guide - I've had FreeNX up and running on my Mandrake box for a while, and was looking forward to running it on Ubuntu 5.04. 

One small problem though - my Ubuntu install is on an AMD64 box, and I saw earlier in the thread that there aren't packages for AMD64. I figured that was a month or so ago, perhaps they're in there now? 

```
$ apt-cache search freenx
freenx - The FreeNX application/thin-client server based on NX technology
nxserver - The FreeNX application/thin-client server based on NX technology
```

Cool ! 
```
$apt-get install freenx
The following packages have unmet dependencies:
freenx: Depends: nxagent (>= 1.4.0-m2-1) but it is not installable
            Depends: nxproxy (>= 1.4.0-m2-1) but it is not installable
```

D'oh! *apt-cache search* doesn't turn up any results for nxagent, nxproxy, nxssh, etc. There is a package called nxsetup-kanotix, but I'm not sure if that would be useful. 

Any suggestions?

---

### Post by Syirrus on 2005-05-17
Can someone post a link with the nxclient nomachines site is down and there is no other place where I can get it :(

Syirrus

---

### Post by aerials on 2005-05-23
Did anyone get XFCE to work via freenx and can describe how you did it?
I only read from people using it, but never how it was done.

aerials


EDIT: OK, I'm an idiot... custom desktop with startxfce4 as command did it.

---

### Post by Daz on 2005-05-31
[QUOTE=Drain]I was all excited when I read through Daz's guide - I've had FreeNX up and running on my Mandrake box for a while, and was looking forward to running it on Ubuntu 5.04. 

One small problem though - my Ubuntu install is on an AMD64 box, and I saw earlier in the thread that there aren't packages for AMD64. I figured that was a month or so ago, perhaps they're in there now? 

```
$ apt-cache search freenx
freenx - The FreeNX application/thin-client server based on NX technology
nxserver - The FreeNX application/thin-client server based on NX technology
```

Cool ! 
```
$apt-get install freenx
The following packages have unmet dependencies:
freenx: Depends: nxagent (>= 1.4.0-m2-1) but it is not installable
            Depends: nxproxy (>= 1.4.0-m2-1) but it is not installable
```

D'oh! *apt-cache search* doesn't turn up any results for nxagent, nxproxy, nxssh, etc. There is a package called nxsetup-kanotix, but I'm not sure if that would be useful. 

Any suggestions?[/QUOTE]

Sorry Drain,

I forgot to mention that the guide was primarily for x86...

I'm on an AMD64 box too, but I found that there just aren't enough packages ready for x86-64 yet, so i'm running i386 hoary on my box.  (It's a work machine, so I don't have the time to sort it out and start building packages myself at the mo - boss would kill me!  :wink: )

Maybe when Breezy comes out I may start to try x86-64 ubuntu again...

---

### Post by Daz on 2005-05-31
[QUOTE=santo]How can i use FreeNX to connect to my current session/desktop, so I can continue the work I already started (i.e. like VNC/Krfb does) ?[/QUOTE] 

[QUOTE=MemoryDump]does anybody know how to set this up? I would rather resume/connect to a currently logged in session rather than starting a new one.

Thanks
-MD[/QUOTE]

Hi Santo / MemoryDump,

Unfortunately, I don't think this is possible via NX - at least i've not been able to find out anything positive about this...  :| 

I think NX was more thought of for the idea of thin clients and the like (similar idea to Citrix) - allow a basic (cheap) PC to log-in to a much more powerful (expensive) server and have full functionallity for more users, and hence reduce hardware costs and admin time...  I don't think it is in it's remit to move into things like connecting to current sessions etc.

Anyone found any info to the contrary?!?

---

### Post by lm05 on 2005-06-06
I am going a little insane at the moment.

I used to have FreeNX running, then I upgraded from Warty to Hoary.

I have uninstalled FreeNX server and re-installed it.

When ever I log in, I get the !M and then it just sits on a blank screen.

So far I have ascertained that:
- FreeNX client has connected to FreeNX server but failed to initialise Gnome.
- I can start a program in the Remote Window by typing "xterm -display localhost:1000"
- I can start Gnome by typing "gnome-session" within the xterm window.

Has anyone got any ideas where to go next?

I've tried the two suggestions of:
- Create a new user
- Delete the .Xauthority files

Thanks,

LM

---

### Post by Golovko on 2005-06-07
I have never been able to get the suspend function working. I am using the backports packages, since attemping to use the Kanotix packages give dependency errors (the ones listed above by some people).

This would be extremely helpful to get suspend working. Any tips or ideas? Where could I start poking through log files, etc. The nomachine client on windows fails silently. Right after it says "starting X server", it pops up a brief screen of black with the nomachine logo in red on it.

Gol

---

### Post by rcunha on 2005-06-12
[QUOTE=lm05]I am going a little insane at the moment.

I used to have FreeNX running, then I upgraded from Warty to Hoary.

I have uninstalled FreeNX server and re-installed it.

When ever I log in, I get the !M and then it just sits on a blank screen.

So far I have ascertained that:
- FreeNX client has connected to FreeNX server but failed to initialise Gnome.
- I can start a program in the Remote Window by typing "xterm -display localhost:1000"
- I can start Gnome by typing "gnome-session" within the xterm window.

Has anyone got any ideas where to go next?

I've tried the two suggestions of:
- Create a new user
- Delete the .Xauthority files

Thanks,

LM[/QUOTE]
 I'm having the same problem as Im05 since my last  dist-upgrade. Before that, it was working ok. From what i can see, gnome-session is started, the process is running but, just black. anything else just runs, like, for example xterm. Then if i start gnome-session once more in xterm it's shows up ok.

---

### Post by lm05 on 2005-06-12
[QUOTE=rcunha]I'm having the same problem as Im05 since my last  dist-upgrade. Before that, it was working ok. From what i can see, gnome-session is started, the process is running but, just black. anything else just runs, like, for example xterm. Then if i start gnome-session once more in xterm it's shows up ok.[/QUOTE]

Good to know that some-one else in the same boat.

I had done exactly the same process, a DIST-UPGRADE.

I really don't want to have to do a wipe and load. Perhaps - when FreeNX installs it overwrites a config file (for gnome-session perhaps) that the DIST-UPGRADE did not overwrite when it upgraded the packages.

Any thoughts anyone?

---

### Post by alw on 2005-06-12
I have the same problem, the !M window stays blank when using gnome-session.  If I switch to xfce4-session, it works well.  From the Windows version of the !M client, gnome-session works fine.

The backports are handy, but where are the sources?  I can't find them on any of the mirrors.  I need to rebuild nxclient for PPC, but if backports isn't going to support sources, I might as well start from scratch.

---

### Post by lm05 on 2005-06-12
[QUOTE=alw]I have the same problem, the !M window stays blank when using gnome-session.  If I switch to xfce4-session, it works well.  From the Windows version of the !M client, gnome-session works fine.
[/QUOTE]

Interesting - Either client (Windows or Linux) has the same hang on Gnome-session. Perhaps its client version related ??? Are they the same client version on your linux and windows boxes?

---

### Post by sb73542 on 2005-06-14
I just installed this from backports today.  Stinking amazing over my dirt slow dialup connection!!!

Anyone had luck getting sound to be automatically forwarded?  From what I've read, when connecting with the Linux !M client, the FreeNX server will only use artsd to forward sound.  Can anyone confirm that?  What if you're running pure Ubuntu?  Artsd does not get along with esd.  Thanks!

---

### Post by Daz on 2005-06-14
I too am having problems loading up Gnome over NX, it seems to hang (following a recent update).  I think this issue may be server based as I also have the same issue on Mac OS X and using another Ubuntu box - KDE works okay, but Gnome stalls and fails to load...

Also, if anyone out there uses custom server keys (client.id_dsa.key) - the latest upgrade will also affect those as support for custom keys is no longer in the Debian builds of FreeNX - so it's back to the public NX key for all of your clients!

As such I have also done a quick update of my [install guide](http://oakley.bioinformaticsonline.co.uk/?q=node/18) to reflect all of the changes with this latest release.

---

### Post by mlmurray on 2005-06-14
I had to DOWNGRADE back to the previous version of the freenx server (there are 4 or 5 packages).  Once I did this, Gnome started working remotely and I was able to terminate/suspend when closing the client with the client's window managers "close" button.

---

### Post by sb73542 on 2005-06-14
[QUOTE=mlmurray]I had to DOWNGRADE back to the previous version of the freenx server (there are 4 or 5 packages).  Once I did this, Gnome started working remotely and I was able to terminate/suspend when closing the client with the client's window managers "close" button.[/QUOTE]
 I see two different versions.  You are using 0.3.1-2_5.04ubp1 ?   Thanks!

---

### Post by Ozitraveller on 2005-07-09
Ok, I've installed using nxsetup --setup-nomachine-key, and everything works fine. Now I want to add the security, is there any easy way to reconfigure this, or do I have to re-install? I want to be able to access my ubuntu from work, and I don't what any gremlins getting in.

I've noticed that the desktop and trash icons are replaced by red X when the destop is rendered on the windows client, and probably some of the other menu icons as well. Is this normal?

Can I transfer files with freeNX or do I have to use ftp?

---

### Post by Deusiah on 2005-07-12
Hi,

I was able to get FreeNX working fine. However I have now changed SSH daemon config so that it no longer uses PAM. Needless to say FreeNX has stopped working.

I'm a bit confused as to how to go about remedying this as I don't want to reable the use of PAM for the SSH daemon. Do I have to use FreeNX with SSH or just add another key to ~/.ssh/authorized_keys so that user NX can login?

Thanks.

---

### Post by mberry on 2005-07-16
OK, I'm getting jolly frustrated with this whole freenx on ubuntu thing now.
Had things working fine on my SuSE 9.1 box, now trying to get it up and running with ubuntu (Hoary). Have the packages from backports, which are installed and running with the no-machine key, got the nx client on my windows 98 laptop.
SSH works fine via putty, absolutely no problems.
NX authenticates ok, and then *almost invariably* gives up just after displaying the big !M logo, the log files run something like this:
[INDENT]```
NXPROXY - Version 1.4.0

Copyright (C) 2001, 2004 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '1660803'.
Info: Waiting for connection from any host on port '3239'.
Info: Accepted connection from '127.0.0.1' on port '3322'.
Info: Connection with remote proxy established.
Info: Handshaking with remote proxy ':5000' completed.
Info: Synchronizing local and remote caches.
Info: Using cache parameters 4/262144/8192KB/8192KB.
Info: Using image cache parameters 1/1/32768KB.
Info: Using adsl link parameters 8192/80/16/4096.
Info: Using pack method '16m-jpeg-7' with session 'unix-gnome'.
Info: Using ZLIB data compression level 3.
Info: Using ZLIB data threshold set to 32.
Info: Using ZLIB stream compression level 6.
Info: Using remote ZLIB data compression level 3.
Info: Using remote ZLIB stream compression level 6.
Info: No suitable cache file found.
Info: Using remote server connected on port '3239'.
Info: Starting X protocol compression.
Info: Established X server connection.
Warning: Not using shared memory support in X server.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting
```.[/INDENT]
I know others have had similar problems here, but I can't find any replies telling me how to fix this! I have SSL eanbled for all trafic.
I say almost invariably because I have had it running on two and a half occasions! As far as I can see the only thing that changes is the port to the remoter server attenpts to connect to, (3239 above). My most recent (semi) successful attempt, which logged in to gnome OK but then seized up, was to port 1250, FWIW. I wonder if it's a case of X only allowing connections from a certain range of ports - is there a way to test this idea?
--LATER--
 :) 
OK I did ```
apt-get remove --pruge freenx nxserver nxproxy nxagent
apt-get install freenx
```
This is where the problem had been: there's now a helpful menu in the setup script to select what sort of keys you want installing; obviously I chose the no machine key, but then also tried to do [FONT=Courier New]nxsetup --install --setup-nomachine-key[/FONT], 
which evidently messed up all the key settings. So, for the benefit of those who come after, you don't need to use nxsetup at all now, the install script does it all for you.
--LATER STILL--
:(
Despite my optimism above, the same problem is recurring. Reinstalling on client and server sometimes sorts things out, but not always, and there seems no consistency here. Who defined insanity as repeatedly doing the same thing and expecting a different outcome? I still have suspicions that it's an X thing rather than freenx per se. Any ideas where the access settings are for X?
As things stand at present, there's no way I'm going to be using this to provide home access to the school desktops for my pupils.

---

### Post by sep on 2005-07-29
If anyone could help pointing me in the right direction that would be awesome
I've got freenx all installed and looks normal.
I go to connect using windows client and I get the error
\
"error unknown"

I can vnc remote in but it's way to slow, and I can also use putty for ssh.

but I can't figure out this error unknown error

anyone seen this before?

---

### Post by paulrd on 2005-07-31
Hi! I'm pretty new to Ubuntu and I've read here and searched through google and I can't find much help with this problem:

I have installed freenx without much problem (thanks to backports). I am using the nomachine mac os x client. I get the following error when trying to connect to the gnome desktop:

NXPROXY - Version 1.5.0

Copyright (C) 2001, 2005 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '1066'.
Warning: Connected to remote NXPROXY version 1.4.0 with local version 1.5.0.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Remote proxy doesn't support fake authentication.
Info: Forwarding the real X authorization cookie.
Info: Using cache parameters 4/262144/8192KB/8192KB.
Info: Using image cache parameters 1/1/32768KB.
Info: Using adsl link parameters 8192/8/1/5.
Info: Using pack method '16m-jpeg-7' with session 'unix-gnome'.
Info: Using ZLIB data compression level 3.
Info: Using ZLIB data threshold set to 32.
Info: Using ZLIB stream compression level 6.
Info: Using remote ZLIB data compression level 3.
Info: Using remote ZLIB stream compression level 6.
Info: No suitable cache file found.
Info: Starting X protocol compression.
Warning: X connection failed with error 'Invalid MIT-MAGIC-COOKIE-1 key'.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.

Any clues would be greatly appreciated!

Paul

---

### Post by Drain on 2005-08-04
So a little while ago I posted in here about wanting to run FreeNX on my AMD64 Hoary installation, but not having the packages (nxagent and nxproxy) to do so. I think there were one or two people who had the same problem or interest. 

Long story short, here is the how-to thread about getting those packages built from source: [http://ubuntuforums.org/showthread.php?t=54417](http://ubuntuforums.org/showthread.php?t=54417)

And for those of you who just want a more simple "apt-get install", Tamir will soon (hopefully) be putting the necessary files up on his repository. See that thread here: [http://ubuntuforums.org/showthread.php?t=48905](http://ubuntuforums.org/showthread.php?t=48905)

---

### Post by metallikop on 2005-08-08
Has anyone had success running FreeNX on Breezy?  I know this might not be the best place to post this, but i'm getting the same problem as posted by paulrd:

```
Info: Using remote ZLIB data compression level 3.
Info: Using remote ZLIB stream compression level 6.
**Info: No suitable cache file found.**
Info: Starting X protocol compression.
Warning: X connection failed with error 'Invalid MIT-MAGIC-COOKIE-1 key'.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.
```

I tried rebuilding this from source but I'm getting a number of C++ issues.  I tried moving back to gcc-3.3 and still had problems building.  Anyone have any ideas?

---

### Post by JohnMaes on 2005-08-09
I just added the repository and opened up my terminal window, typed sudo apt-get install freenx and it spewed out some message about broken links to nxagent and nxproxy.

Is NoMachine messing things up?
Any help would be appreciated.
Take care!

---

### Post by Jurassic on 2005-08-10
How did you guys manage to DOWNGRADE ](*,) All packages I've found have the same version of NXSERVER - 1.4.0-03.
I got XFCE to work but it behaves really strange. To open a terminal window (gnome-terminal) takes about 1 minute. Same happens to almost all applications.
Meanwhile GNOME refuses to display anything on the screen.

---

### Post by Dec on 2005-08-21
I just installed FreeNX on Breeze and while launching the client application from a windows terminal outside my home network, i get this error:

----------------------------------------------------------------------------
NXPROXY - Version 1.5.0

Copyright (C) 2001, 2005 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '2748'.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using cache parameters 4/262144/32768KB/32768KB.
Info: Using image cache parameters 1/1/131072KB.
Info: Using adsl link parameters 8192/8/10/50.
Info: Using pack method '16m-jpeg-7' with session 'unix-gnome'.
Info: Using ZLIB data compression level 3.
Info: Using ZLIB data threshold set to 32.
Info: Using ZLIB stream compression level 6.
Info: Using remote ZLIB data compression level 3.
Info: Using remote ZLIB stream compression level 6.
Info: No suitable cache file found.
Info: Starting X protocol compression.
Warning: Protocol mismatch in the authentication data.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.
-------------------------------------------------------------------------------

Never had this problem with Hoary..  Any ideas?

---

### Post by appleman77 on 2005-09-01
Has anyone had any luck in getting the Windows NX Client to work over putty?  I'm at a client that has an http proxy so I create a SOCKS proxy using putty to tunnel through the http proxy, but when putty is running, I get the following error from the NX client....


```
ddxProcessArgument - Initializing default screens
winInitializeDefaultScreens - w 1024 h 768
winInitializeDefaultScreens - Returning
ddxProcessArgument - screen - Found ``W D'' arg
_XSERVTransSocketCreateListener: listen() failed
_XSERVTransSocketINETCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: failed to create listener for tcp
_XSERVTransmkdir: Owner of /tmp/.X11-unix should be set to root
_XSERVTransSocketCreateListener: listen() failed
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: failed to create listener for local

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

```

I've tried running the Windows NX client within SocksCap32 to isolate the NX client from even realizing that a SOCKS proxy is running, but then I get the following error:

```
ddxProcessArgument - Initializing default screens
winInitializeDefaultScreens - w 1024 h 768
winInitializeDefaultScreens - Returning
ddxProcessArgument - screen - Found ``W D'' arg
_XSERVTransmkdir: Owner of /tmp/.X11-unix should be set to root
(EE) Unable to locate/open config file
InitOutput - Error reading config file
winDetectSupportedEngines - Windows NT/2000/XP
winDetectSupportedEngines - DirectDraw installed
winDetectSupportedEngines - Allowing PrimaryDD
winDetectSupportedEngines - DirectDraw4 installed
winDetectSupportedEngines - Returning, supported engines 0000001f
InitOutput - g_iNumScreens: 1 iMaxConsecutiveScreen: 1
winSetEngine - Using Shadow DirectDraw NonLocking
winAdjustVideoModeShadowDDNL - Using Windows display depth of 16 bits per pixel
winCreateBoundingWindowWindowed - User w: 1024 h: 708
winCreateBoundingWindowWindowed - Current w: 1024 h: 708
winAdjustForAutoHide - Original WorkArea: 0 0 708 1024
winAdjustForAutoHide - Adjusted WorkArea: 0 0 708 1024
winCreateBoundingWindowWindowed - WindowClient w 1018 h 676 r 1018 l 0 b 676 t 0
winCreateBoundingWindowWindowed -  Returning
winCreatePrimarySurfaceShadowDDNL - Creating primary surface
winCreatePrimarySurfaceShadowDDNL - Created primary surface
winCreatePrimarySurfaceShadowDDNL - Attached clipper to primary surface
winAllocateFBShadowDDNL - lPitch: 2036
winAllocateFBShadowDDNL - Created shadow pitch: 2036
winAllocateFBShadowDDNL - Created shadow stride: 1018
winFinishScreenInitFB - Masks: 0000f800 000007e0 0000001f
winInitVisualsShadowDDNL - Masks 0000f800 000007e0 0000001f BPRGB 6 d 16 bpp 16
winCreateDefColormap - Deferring to fbCreateDefColormap ()
winFinishScreenInitFB starting winInitWM
winFinishScreenInitFB After winInitWM
color offset: b 5 0
winFinishScreenInitFB - returning
winScreenInit - returning
InitOutput - Returning.
error opening security policy file /usr/X11R6/lib/X11/xserver/SecurityPolicy
(EE) No primary keyboard configured
(==) Using compiletime defaults for keyboard
names.keymap=(null)Rules = "xfree86" Model = "pc101" Layout = "us" Variant = "(null)" Options = "(null)"
Couldn't load XKB keymap, falling back to pre-XKB keymap
Could not init font path element /cygdrive/C/Program Files/NX Client for Windows/usr/X11R6/lib/X11/fonts/Speedo, removing from list!
Could not init font path element /cygdrive/C/Program Files/NX Client for Windows/usr/X11R6/lib/X11/fonts/Type1, removing from list!
Could not init font path element /cygdrive/C/Program Files/NX Client for Windows/usr/X11R6/lib/X11/fonts/75dpi, removing from list!
Could not init font path element /cygdrive/C/Program Files/NX Client for Windows/usr/X11R6/lib/X11/fonts/100dpi, removing from list!
winBlockHandler - Releasing pmServerStarted
winBlockHandler - pthread_mutex_unlock () returned
```

These logs come from the NXWin.log file...

I am able to run the Windows NX client successfully from my LAN at home with no issues.  It's only when I try and run it over putty + OpenSSH at work.   I understand that NX using SSH but I need to get through a HTTP proxy so I am using OpenSSH + putty to do that.

Any help would be appreciated.

---

### Post by thoreauputic on 2005-09-10
[QUOTE=Dec]I just installed FreeNX on Breeze and while launching the client application from a windows terminal outside my home network, i get this error:

----------------------------------------------------------------------------
NXPROXY - Version 1.5.0

Copyright (C) 2001, 2005 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '2748'.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using cache parameters 4/262144/32768KB/32768KB.
Info: Using image cache parameters 1/1/131072KB.
Info: Using adsl link parameters 8192/8/10/50.
Info: Using pack method '16m-jpeg-7' with session 'unix-gnome'.
Info: Using ZLIB data compression level 3.
Info: Using ZLIB data threshold set to 32.
Info: Using ZLIB stream compression level 6.
Info: Using remote ZLIB data compression level 3.
Info: Using remote ZLIB stream compression level 6.
Info: No suitable cache file found.
Info: Starting X protocol compression.
Warning: Protocol mismatch in the authentication data.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.
-------------------------------------------------------------------------------

Never had this problem with Hoary..  Any ideas?[/QUOTE]

Deleted my "quick reply" and added it to following post. (thoreauputic)

---

### Post by thoreauputic on 2005-09-10
Note that Seveas (Dennis Kaarsemaker - [https://wiki.ubuntu.com/DennisKaarsemaker](https://wiki.ubuntu.com/DennisKaarsemaker) ) has made packages for freenx both for Hoary and Breezy. Full instructions (very straightforward) at:

[https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX)

Take a look! Thank you, Dennis...

---

### Post by ubuntonista on 2005-09-12
The guide at the wiki has been updated recently to show how to change the sshd port, and also to cover installation of the client on Ubuntu systems:
[https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX)

Thanks, everyone.

---

### Post by Montgomery on 2005-09-27
i'm thinking about using freenx, but i got a traffic limit for my dsl-connection, can anyone tell me how much traffic freeNX causes (in let's say 1 hour)?

thx

---

### Post by BluBoy on 2005-10-01
[QUOTE=Dec]I just installed FreeNX on Breeze[/QUOTE]

How did you get that far?  Every Deb respoitory I've been able to find gives me dependency errors.
Does anyone know the right one to use?  I'm using breezy and want to try this before I resort to a standard VNC.

Cheers!

---

### Post by spikkle on 2005-10-02
I was able to make it work by taking the following steps:

Install all FreeNX packages from here from the deb packages you are allowed to download:
[http://blackbird.kaarsemaker.net/](http://blackbird.kaarsemaker.net/)

Install the nxclient deb package from:
[http://www.nomachine.com/download_client_linux.php](http://www.nomachine.com/download_client_linux.php)

If you get a message to the effect of "Unable to create X authority" or something like that, then for me the problem was that it was looking in an (outdated) incorrect location for the 'xauth' program.  Run these commands:

cd /usr/X11R6/bin
sudo ln -sf /usr/bin/xauth

This will make a link to the xauth program in the location it expects it to be in.  At this point the client worked fine for me.

Good luck.

---

### Post by edge3281 on 2005-10-04
I have followed the instructions to get freenx setup.  But I am having a problem connection from another machine.  I ran "nxsetup --setup-nomachine-key".  The following is the response that I get from this.
```
Setting up /etc/nxserver ...done
Setting up /var/lib/nxserver/db ...done
Setting up /var/log/nxserver.log ...done
Setting up known_hosts and authorized_keys2 ...done
Setting up permissions ...done
----> Testing your nxserver configuration ...
Warning: Invalid value "COMMAND_START_KDE=startkde"
Users will not be able to request a KDE session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
Users will not be able to request a CDE session.
Warning: Invalid value "COMMAND_SMBMOUNT=smbmount". You'll not be able to use SAMBA. 
Warning: Invalid value "COMMAND_SMBUMOUNT=smbumount". You'll not be able to use SAMBA.
Warnings occured during config check.
To enable these features please correct the configuration file.
<---- done
----> Testing your nxserver connection ...
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 quit
Quit
<--- done
Ok, nxserver is ready.
PAM authentication enabled:
All users will be able to login with their normal passwords.
PAM authentication will be done through SSH.
Please ensure that SSHD on localhost accepts password authentication.
You can change this behaviour in the /etc/nxserver/node.conf file.
Have Fun!
```
I don't think those warnings should cause a problem.  I am trying to connect from a windows machine with the nomachine client and I have set it to use a secure connection and to run gnome as my wm.  Everything seems to connect fine.  It gets to the Establish X server connection and then the screen dissapears.  After about 30 seconds a box pops up that says "No response recieved from the remote server.  Do you want to terminate the connection."
I don't under stand what might be happening.  I can log into ssh just fine.  I have search for this on the ubuntu forums as well as the nomachine kb and I haven't came up with anything.  Any ideas would be greatly appriciated.
Thanks,
edge3281

---

### Post by PeteJ on 2005-10-05
Installing freenx on ubuntu hoary 5.04 following this howto [https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX) worked for me, with a couple of tweaks.  Let's see if I can remember them...

Trying to do a thin-client thing, I'm using Knoppix 3.9 live cd from an old "POC" Pentium II 400 MHz 64MB RAM as the freenx client.  I upgraded the old 1MB video card to an old S3 Treo64+ (something like that) that was laying around.  My "server" is an old HP Brio Celeron 466 MHz 256 MB RAM with ubuntu hoary 5.04.

I followed the instructions on [https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX) to install the freenx server on the brio. They worked by far the easiest, fastest, and best of my several attempts at installing freenx on many machines.  However, I had a couple of problems that a few hours of headbanging fixed...

On the server, I ran:
sudo apt-get install freenx expectk nxdesktop nxviewer  libarts1
in a feeble attempt to install the additional recommended packages. The other recommended packages couldn't be found in my sources.list

I then had to:
sudo cp /var/lib/nxserver/home/.ssh/authorized_keys2 /var/lib/nxserver/home/.ssh/authorized_keys
because my:
/etc/ssh/sshd_config
said:
AuthorizedKeysFile      %h/.ssh/authorized_keys
not:
AuthorizedKeysFile      %h/.ssh/authorized_keys2

You can see where the nx home is by:
grep nx /etc/passwd
nx:x:106:65534::/var/lib/nxserver/home:/usr/lib/nx/nxserver

I also had to: 
sudo chmod 644  /var/lib/nxserver/home/.ssh/authorized_keys
because I was getting nx connection permissions errors.

Is the 644 there insecure?  I think it is, but I'm not sure.

I don't think you should do these commands as stated in the ubuntu freenx wiki:
nxserver --adduser <Username>
nxserver --passwd <Username>
because they cause an odd Permissions Error after what seemed like it was going to be a good freenx connection.  I used:
sudo vim  /etc/nxserver/passwords
to delete the user that I think those steps added into that file.
(By the way, I think I had to do:
sudo nxserver --adduser petjal
sudo nxserver --passwd petjal
to get that to work anyway.
I also ran:
sudo nxsetup --install --setup-nomachine-key
but I don't think I had to, because it prompted me for that during the apt-get install; I don't think it hurt.)

Make sure you:
sudo vim /etc/ssh/sshd_config
and set, I think both:
PubkeyAuthentication yes
PasswordAuthentication yes
And then:
sudo /etc/init.d/ssh restart
And:
man sshd_config
is useful.

Somewhere in google, it said to:
sudo passwd -S nx
sudo passwd -u nx
I did that, but I'm not sure I had to.

On the knoppix client side, because the machine is such an old POC, I had to boot knoppix with 
boot:  knoppix display=800x600 depth=16 desktop=twm
(That might have been:
boot:  knoppix display=640x480 depth=16 desktop=twm )
 
I think that's it.  

It'd be nice to figure out a way to automate the knoppix freenx client setup so that normal humans could reboot the thin client if they had to.  And I'll have to test that the session resume works... Someday...

Enjoy,
Pete

---

### Post by edge3281 on 2005-10-05
I have tried all of that and it doesn't seem to help.  I figured out how to turn the logging on.  Here is what is displayed in my log.  There is more above this so if I need to post more I can but there are no errors or warnings in that part.

```
NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: colts-1000-4F716C88E54F682ED604472A54E99874
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: c047eb449f50cb157e4be26e755c0d6c
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: c047eb449f50cb157e4be26e755c0d6c
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 bye
Bye
NX> 999 Bye
NX> 1009 Session status: terminating
NX> 1006 Session status: closed
NX> 1001 Bye.
```

Looks like it just dies for now reason.  Is there some kind of configuration that I need to do differently?  I would think it would throw and error or warning but it doesn't seem to.  I have even changed the logging level to be just errors and just warnings and neither puts anything in the log file.

---

### Post by Tpot on 2005-10-07
I have spent a day trying to get freeNX running and it appears all is well until I try to connect. When I connect from the localhost or another PC everything authenticates ok, but I get this error...

Error: Lost connection to peer proxy on FD#5.
Error: Connection with remote peer broken.
Error: Please check state of your network connection and retry.

ARRRRGH!!! What is the deal?? Please tell me it is something simple. I can't even figure out what 'FD' stands for.

Thanks

---

### Post by Alexandre on 2005-10-13
[QUOTE=edge3281]Looks like it just dies for now reason.  Is there some kind of configuration that I need to do differently?  I would think it would throw and error or warning but it doesn't seem to.  I have even changed the logging level to be just errors and just warnings and neither puts anything in the log file.[/QUOTE]

Take a look on [http://wiki.ubuntu.com/BackportsFreeNX]("http://wiki.ubuntu.com/BackportsFreeNX")

I have successfully ran freenx (nxserver) on Ubuntu Breezy after some research and changes on the confs ... I have updated the wiki page so that any other Breezy user can enjoy the wonders of NX protocol ... It works great on Breezy with 1.5.0 clients from NoMachine (!M).

I have found that there is a little glitch on the icon cache on gnome using FreeNX from Backports (the only packages that I managed to run on my system): Some icons appear as a simple paper sheet ... Maybe someone can help with this little issue ...

---

### Post by julakali on 2005-10-15
> Looks like it just dies for now reason. Is there some kind of configuration that I need to do differently? I would think it would throw and error or warning but it doesn't seem to. I have even changed the logging level to be just errors and just warnings and neither puts anything in the log file.


exactly the same error here.
I'm using ubuntu breezy and installed freenx from the hoary-extras (and expect from hoary main or something) and getting the same error
> NX> 707 SSL tunneling: 1
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 bye
Bye
NX> 999 Bye


Tried every hint mentioned in this thread...

---

### Post by edge3281 on 2005-10-15
Thanks Alexandre,

You are my hero.  I made the changes to the node.conf that are in the wiki now and now my freenx works.

Thanks again,

Edge3281

---

### Post by khomotso on 2005-10-17
[QUOTE=spikkle]

If you get a message to the effect of "Unable to create X authority" or something like that, then for me the problem was that it was looking in an (outdated) incorrect location for the 'xauth' program.  Run these commands:

cd /usr/X11R6/bin
sudo ln -sf /usr/bin/xauth

This will make a link to the xauth program in the location it expects it to be in.  At this point the client worked fine for me.

Good luck.[/QUOTE]

I'm assuming you mean "Unable to create the X authorization cookie" dialog, which I'm seeing now.  Creating that link sounded promising ... but it didn't help.

I'm trying to connect from a Breezy desktop to a RHEL AS4 server.  I had this working with the 1.5 client on Hoary, but I decided to go with the 1.4 nxclient available through the repositories this time.  I may just have to try uninstalling and installing 1.5 instead.

---

### Post by khomotso on 2005-10-17
[QUOTE=spikkle]

If you get a message to the effect of "Unable to create X authority" or something like that, then for me the problem was that it was looking in an (outdated) incorrect location for the 'xauth' program.  Run these commands:

cd /usr/X11R6/bin
sudo ln -sf /usr/bin/xauth

This will make a link to the xauth program in the location it expects it to be in.  At this point the client worked fine for me.

Good luck.[/QUOTE]

I'm assuming you mean "Unable to create the X authorization cookie" dialog, which I'm seeing now.  Creating that link sounded promising ... and it worked.  But now I'm having other problems.

I'm trying to connect from a Breezy desktop to a RHEL AS4 server.  I had this working with the 1.5 client on Hoary, but I decided to go with the 1.4 nxclient available through the repositories this time.  I may just have to try uninstalling and installing 1.5 instead.

I tried doing exactly that, but it's not working.  I'm still getting an error of the form:
[Mon Oct 17 14:29:05 2005]: Error is [Server not installed or NX access disabled]
[Mon Oct 17 14:29:05 2005]: printFatalError [Server not installed or NX access disabled]

It's working from my Windows client, however.

---

### Post by Marcos.Rufino on 2005-10-17
[QUOTE=spikkle]I was able to make it work by taking the following steps:

Install all FreeNX packages from here from the deb packages you are allowed to download:
[http://blackbird.kaarsemaker.net/](http://blackbird.kaarsemaker.net/)

Install the nxclient deb package from:
[http://www.nomachine.com/download_client_linux.php](http://www.nomachine.com/download_client_linux.php)

If you get a message to the effect of "Unable to create X authority" or something like that, then for me the problem was that it was looking in an (outdated) incorrect location for the 'xauth' program.  Run these commands:

cd /usr/X11R6/bin
sudo ln -sf /usr/bin/xauth

This will make a link to the xauth program in the location it expects it to be in.  At this point the client worked fine for me.

Good luck.[/QUOTE]


Thank you man!! You solved my problem!!

---

### Post by Evincar on 2005-10-19
I'm trying to connect to my freenx server at home from a university pc. But unfortunatly, i do not have admin privileges, so i can't install the windows xp client from nomachine.
Does anybody have a client that works by only unzipping and moving files but no executable instalation? Ore even better a webbased client that works with internet explorer.
This seems very logical to me, since it is the way to bypass all the "safety" measurements they take over here which seriously degrades the ussability of the pc's. (I.E.: no right mouse button, no task manager, no firefox)

---

### Post by tlepes on 2005-10-21
Anyone here got nxclient working on Breezy?  I used Seveas's guide on the WIKI [https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX) but get this error when runnin nxclient on the client machine:

```
/usr/NX/bin/nxclient: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```

Searching Synaptic I only find up to C/C++ 6.0 (methinks).  Am I doing something wrong?  Do I need to try compiling nxclient from source?

I noticed that in synaptic the nxclient does not show anything listed for "dependencies".  Maybe this is a problem with the deb in Seveas' repository?

I dunno.  But I would really like to get this to work.  My friend is a Linux n00b and I have set him up with Ubuntu.  He will be connecting strictly through dial-up (as he lives in the country, no DSL or Cablenet).  It will make life much easier for me to support him if I can do a reasonable remote desktop and/or remote GUI login.

And yes, I understand, you can nxserver or nxdesktop to route a vnc or rdp server connection thru NX, benefitting from it's compression and round-trip reduction.  That is my ultimate aim.

Thanks in advance!

---

### Post by tlepes on 2005-10-22
In my original question I asked:

[QUOTE=tlepes]Anyone here got nxclient working on Breezy?  I used Seveas's guide on the WIKI [https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX) but get this error when runnin nxclient on the client machine:

```
/usr/NX/bin/nxclient: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```

Searching Synaptic I only find up to C/C++ 6.0 (methinks).  Am I doing something wrong?  Do I need to try compiling nxclient from source?[/QUOTE]

I got a fast response from "bob2" in the #ubuntu channel on freenode IRC.  He pointed me to a web page with search results for the missing library file "libstdc++-libc6.2-2.so.3" that showed what packages it was.  Issuing the following command solved my problems getting nxclient to run:

```
sudo apt-get install libstdc++2.10-dbg libstdc++2.10-glibc2.2
```

On further reflection, I suppose I could have gotten the missing library file by just installing **one** or the **other**, as opposed to installing both **libstdc++2.10-dbg** and **libstdc++2.10-glibc2.2** packages.

That package search was very cool.  I poked around a bit on the website and figured that bob2 must have used the "Search the contents of packages" section of this page: [http://packages.ubuntu.com/#search_contents]("http://packages.ubuntu.com/#search_contents")

I also made this comment earlier, which I still believe may be a source of trouble for people later on:

[QUOTE=tlepes]I noticed that in synaptic the nxclient does not show anything listed for "dependencies".  Maybe this is a problem with the deb in Seveas' repository?
[/QUOTE]

Now lets see if we can get this mutha humming...  :)

---

### Post by titaniumone on 2005-10-24
i have a clean install of Breezy. i installed freenx using Seveas' repository.

i set it up using nomachine keys.

i added a user and set their password.

now when i log in:

"Server not installed or NX access disabled".

when i click details:
NX> 203 NXSSH running with pid: 512
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 192.168.0.12 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.


i get this regardless of what password i fill in. it's like it isn't even attempting to login. i've been trying to get it working for 3 hours, please help :(

---

### Post by samjam on 2005-10-25
[QUOTE=Alexandre]Take a look on [http://wiki.ubuntu.com/BackportsFreeNX]("http://wiki.ubuntu.com/BackportsFreeNX")

I have successfully ran freenx (nxserver) on Ubuntu Breezy after some research and changes on the confs ... I have updated the wiki page so that any other Breezy user can enjoy the wonders of NX protocol ... It works great on Breezy with 1.5.0 clients from NoMachine (!M).
[/QUOTE]

Good tips. It troubles me that backports do not make the debian sources available.
Last time I asked I was informed that backports sources was breezy development but as breezy doesn't have NX this is not the case.

Ubuntu (not you) seems bad at obfuscating the origins of the binaries.

Here is how I got my NX stuff:

Add to sources.list:
```

deb-src http://kanotix.com/files/debian/ ./

```

Note that this is a deb-src.

Then;
```

apt-get update
apt-get -s build-dep nxserver
apt-get -b source nxserver
apt-get -b source freenx
dpkg -i *deb

```

And that got me freshly built nx server debs.

Then
```

apt-get -b build-dep nxclient
apt-get -b source nxclient
dpkg -i *client*deb
apt-get install libstdc++2.10-glibc2.2

```

I can't find any source packages for nxtunnel-server et al as mentioned on [wiki]("https://wiki.ubuntu.com/BackportsFreeNX")

I fix the standard "Unable to create the X authorization cookie" problem with:
```

cd /usr/X11R6/bin/
ln -sf /usr/bin/xauth

```

and now I'm on

I also make the changes to /etc/nxserver/node.conf as the wiki directs, but I still need the xauth symlink locally.

I can connect locally but not to my home, which also runs breezy with the same packages. Weird.
```

NXPROXY - Version 1.5.0

Copyright (C) 2001, 2005 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '15488'.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using cache parameters 4/262144/32768KB/32768KB.
Info: Using image cache parameters 1/1/131072KB.
Info: Using adsl link parameters 8192/8/10/50.
Info: Using pack method '16m-jpeg-7' with session 'unix-gnome'.
Info: Using ZLIB data compression level 3.
Info: Using ZLIB data threshold set to 32.
Info: Using ZLIB stream compression level 6.
Info: Using remote ZLIB data compression level 3.
Info: Using remote ZLIB stream compression level 6.
Info: No suitable cache file found.
Info: Starting X protocol compression.
Warning: Protocol mismatch in the authentication data.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.

```

Hmm, when I add the xauth symlink to my home machine, I get as far as:
"Established X Server Connection" but then it seems to hang.

---

### Post by fourbeer on 2005-10-25
I have installed per the instructions on the forums.  I even am authenticated when I log in.  However, I only get a big black screen.  After many, many minutes, I eventually see my gnome desktop, but no menu bars.  After many, many more minutes, I see the menu bars.

Anyone seeing these problems?  I am connecting from XP to ubuntu 5.10.  The PC's are right next to each other and are connected via a 100mb/s switch.

Thanks.

---

### Post by awaite on 2005-11-02
fourbeer,

I have experienced the same thing. Interestingly I believe this to be an issue with Freenx and Gnome (i.e. not just Ubuntu) as I tried Suse 10 with Freenx and it works fine with a KDE session but exact same behavior for a GNOME session as you described. I haven't tried this with Kubuntu, I speculate that it would work fine.

My server log doesn't show anything different when doing a GNOME vs. KDE session so I suspect it's more of an issue with GNOME (more speculating).

Curiously, has anyone tried the server from Nomachine.com? I wonder if they have the same issue.

---

### Post by coaxx on 2005-11-12
1.I installed FreeNX like described in
[https://wiki.ubuntu.com/BackportsFreeNX](https://wiki.ubuntu.com/BackportsFreeNX)

But for installing FreeNX Client it needs libstdc++2.10-glibc2.2. Any hints? I tried searching it in synaptic without any luck.:( 

2.I read somewhere here that ist is not neccessary anymore to add a user via the nxserver --adduser /--passwd command. Is that correct, or do I need to add the user who will connect to the server?

3. My FreeNX server is behind a NAT Router Firewall. Do I have to forward any ports (besides port 22 for ssh) to be able to connect to the FreeNX server?

---

### Post by beelzebub1987 on 2005-11-13
beelzebub1987@ray-ubuntu-desktop:~$ sudo apt-get install freenx
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  freenx: Depends: nxagent (>= 1.4.92+1.5.0) but it is not going to be installedE: Broken packages
beelzebub1987@ray-ubuntu-desktop:~$ sudo apt-get install nxagent
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nxagent: Depends: libxcomp1 but it is not going to be installed
           Depends: libxcompext1 but it is not going to be installed
           Depends: nxlibs but it is not going to be installed
E: Broken packages
beelzebub1987@ray-ubuntu-desktop:~$ sudo apt-get install nxlibs
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nxlibs: Depends: libxcomp1 but it is not going to be installed
          Depends: libxcompext1 but it is not going to be installed
E: Broken packages
beelzebub1987@ray-ubuntu-desktop:~$ sudo apt-get install libxcomp1
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxcomp1: Depends: libstdc++6 (>= 4.0.2) but 4.0.1-4ubuntu9 is to be installed
E: Broken packages
beelzebub1987@ray-ubuntu-desktop:~$ sudo apt-get install libstdc++6
Reading package lists... Done
Building dependency tree... Done
libstdc++6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
beelzebub1987@ray-ubuntu-desktop:~$ sudo apt-get install libxcompext1
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxcompext1: Depends: libstdc++6 (>= 4.0.2) but 4.0.1-4ubuntu9 is to be installed
                Depends: libxcomp1 but it is not going to be installed
E: Broken packages
beelzebub1987@ray-ubuntu-desktop:~$ sudo apt-get install libxcomp
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libxcomp
beelzebub1987@ray-ubuntu-desktop:~$ sudo apt-get install libxcomp1
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxcomp1: Depends: libstdc++6 (>= 4.0.2) but 4.0.1-4ubuntu9 is to be installed
E: Broken packages

I need help =(

---

### Post by thoreauputic on 2005-11-13
Your /etc/apt/sources.list is almost certainly broken. 

I suggest you wipe your sources list and use one from 

[http://paste.ubuntulinux.nl/969](http://paste.ubuntulinux.nl/969)

or make your own at

[http://ubuntulinux.nl/source-o-matic](http://ubuntulinux.nl/source-o-matic)

Then add these lines at the bottom

# FreeNX stuff
#
deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas freenx
deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas freenx

Then of course update - reload in synaptic, or  run

sudo apt-get update

---

### Post by beelzebub1987 on 2005-11-14
Thanks for the help. I'll try it out when I get home. :p ;)

---

### Post by thoreauputic on 2005-11-14
just  a quick follow-up.

I suggest all those who want to try FreeNX read

[https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX)

Dennis Kaarsemaker has made all this very easy - he's the guy who supplies the repository I referenced. His repositories are reliable - you can even add a gpg key for them. See

[http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/)

for more information.

---

### Post by beelzebub1987 on 2005-11-16
> beelzebub1987@ray-ubuntu:~$ sudo nxsetup --setup-nomachine-key
------> You did select no action.
        FreeNX guesses that you want to _install_ the server.
        Type "y" to abort the installation at this point in time.
        "N" is the default and continues installation.
        Use "/usr/sbin/nxsetup --help" to get more detailed help hints.

 Do you want to abort now? [y/N] n

Setting up /etc/nxserver ...done
Setting up /var/lib/nxserver/db ...done
Setting up /var/log/nxserver.log ...done
Setting up known_hosts and authorized_keys2 ...done
Setting up permissions ...done

----> Testing your nxserver configuration ...
Warning: Could not find nxdesktop in /usr/lib/nx. RDP sessions won't work.
Warning: Could not find nxviewer in /usr/lib/nx. VNC sessions won't work.
Warning: Invalid value "DEFAULT_X_SESSION=/etc/X11/xdm/Xsession"
         Users might not be able to request a default X session.
Warning: Invalid value "COMMAND_START_KDE=startkde"
         Users will not be able to request a KDE session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
         Users will not be able to request a CDE session.

  Warnings occured during config check.
  To enable these features please correct the configuration file.

<---- done

----> Testing your nxserver connection ...
The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.
RSA key fingerprint is 5f:8c:91:1c:db:66:d1:d6:18:e4:18:94:bc:df:a5:61.
Are you sure you want to continue connecting (yes/no)? Fatal error: Could not connect to NX Server.

Please check your ssh setup:

        - Make sure "nx" is one of the AllowUsers in sshd_config.
        - Make sure your sshd allows public key authentication.
        - Make sure your sshd is really running on port 22.
        - Make sure your sshd_config AuthorizedKeysFile in sshd_config is set to authorized_keys2.

I looked in sshd_config and there is no "AllowUsers"
> # Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	%h/.ssh/authorized_keys2

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes


# To change Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#AFSTokenPassing no
#KerberosTicketCleanup no

# Kerberos TGT Passing does only work with the AFS kaserver
#KerberosTgtPassing yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
KeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

---

### Post by thoreauputic on 2005-11-16
I think you are making this altogether more complicated than you need to.

Did you read the wiki howto I posted a link to above?

You really shouldn't need to go through all those setup steps. If you just choose the No Machine key option on install, the server should work fine.

I would guess running

sudo dpkg-reconfigure freenx

would ask you the relevant questions again, and possibly fix things, but since I didn't run into the problems you are having I can't be sure.  Is ssh properly configured on your machine? Are you using the "authorized_keys2" file as suggested in the output above?

---

### Post by beelzebub1987 on 2005-11-16
> AuthorizedKeysFile %h/.ssh/authorized_keys2

my second quote is my sshd_config file
and thanks

---

### Post by edistar on 2005-12-06
Hey!
I have a question. Does freenx autostart with every user by standard?
Thanks for the answer...

Greetings from Germany

---

### Post by coaxx on 2005-12-06
[QUOTE=jdong]Q:How can I use FreeNX with Ubuntu?


```
deb http://kanotix.com/files/debian/ ./
```

The repository is for Kanotix, a Debian/SID Knoppix derivative.

Run **apt-get install freenx**.
[/QUOTE]


I have 404 Not found error with "deb [http://kanotix.com/files/debian/](http://kanotix.com/files/debian/) ./" in sources.list when doing a "apt-get update"?! Whats wrong here?

---

### Post by halvdansk on 2005-12-06
I get the same error as **[SIZE="3"]beelzebub1987[/SIZE]**
(i have purged and reinstalled it **with** nxsetup --setup-nomachine-key)

blah
blah
Please check your ssh setup:

- Make sure "nx" is one of the AllowUsers in sshd_config.
- Make sure your sshd allows public key authentication.
- Make sure your sshd is really running on port 22.
- Make sure your sshd_config AuthorizedKeysFile in sshd_config is set to authorized_keys2.

any ideeas? thx
(running breezy btw)

---

### Post by ShiftyPowers on 2005-12-08
this thing is the bomb, better than VNC, easier to use I guess.  Question is though, can you enter and exit a connection and still have the same session on the remote system?

---

### Post by primitive on 2005-12-09
[QUOTE=ShiftyPowers]this thing is the bomb, better than VNC, easier to use I guess.  Question is though, can you enter and exit a connection and still have the same session on the remote system?[/QUOTE]

Yes.  Instead of logging out of the remote session to end your session, click the "Close" box of the NX window.  A window should pop up inside the session giving you the choice of either suspending or terminating the session.  When you suspend, it should automatically resume it when you log in next time.

---

### Post by dodek on 2005-12-12
i'm using kubuntu breezy. i've installed the freenx from debian packages. it seems to works until i try to connect to server. error is: 
```

NXPROXY - Version 1.5.0

Copyright (C) 2001, 2005 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '11403'.
Info: Connecting to remote host 'dodek.hopto.org:5000'.
Info: Connection to remote proxy 'dodek.hopto.org:5000' established.
Warning: Connected to remote NXPROXY version 1.4.0 with local version 1.5.0.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Remote proxy doesn't support fake authentication.
Info: Forwarding the real X authorization cookie.
Info: Using cache parameters 4/262144/8192KB/8192KB.
Info: Using image cache parameters 1/1/32768KB.
Info: Using adsl link parameters 8192/8/1/5.
Info: Using pack method '16m-jpeg-7' with session 'unix-kde'.
Info: Using ZLIB data compression level 3.
Info: Using ZLIB data threshold set to 32.
Info: Using ZLIB stream compression level 6.
Info: Using remote ZLIB data compression level 3.
Info: Using remote ZLIB stream compression level 6.
Info: No suitable cache file found.
Info: Using remote server 'dodek.hopto.org:5000'.
Info: Starting X protocol compression.
Warning: X connection failed with error 'No protocol specified'.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.


```

When i'm trying to connect by nxtunnel i'm getting error:
```

Fatal server error:
NXAGENT: Unable to open display "nx/nx,link=,stream=9,pack=16m-png-jpeg-1,nodelay=1,root=/home/dodek/.nx,log=session,stat=stats:80".

```
what i'm doing wrong?

---

### Post by benplaut on 2005-12-13
i tried using the wiki article in breezy, and when trying to connect to myself, as a test, it times out. Any other way to test it? the log doesn't report anything, just

NX> 203 NXSSH running with pid: 8209
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files

---

### Post by oldman on 2005-12-18
Hi!

Well I had all sorts of failure before I came to the last , A proxy was closing down the connection on startup. I found this page as one in this thread pointed on : [https://wiki.ubuntu.com/BackportsFreeNX](https://wiki.ubuntu.com/BackportsFreeNX) .The following lines in /etc/nxserver/node.conf did the trick:

COMMAND_XAUTH=/usr/bin/xauth
COMMAND_XSET=/usr/bin/xset
COMMAND_XMODMAP=/usr/bin/xmodmap
COMMAND_XKBCOMP=/usr/bin/xkbcomp
AGENT_EXTRA_OPTIONS_X="-fp /usr/share/X11/fonts/misc/,/usr/share/X11/fonts/100dpi/,/usr/share/X11/fonts/75dpi/,/usr/share/X11/fonts/Type1/"

Thank you all for this forum!

---

### Post by JShadow on 2005-12-19
[QUOTE=oldman]Hi!

Well I had all sorts of failure before I came to the last , A proxy was closing down the connection on startup. I found this page as one in this thread pointed on : [https://wiki.ubuntu.com/BackportsFreeNX](https://wiki.ubuntu.com/BackportsFreeNX) .The following lines in /etc/nxserver/node.conf did the trick:

COMMAND_XAUTH=/usr/bin/xauth
COMMAND_XSET=/usr/bin/xset
COMMAND_XMODMAP=/usr/bin/xmodmap
COMMAND_XKBCOMP=/usr/bin/xkbcomp
AGENT_EXTRA_OPTIONS_X="-fp /usr/share/X11/fonts/misc/,/usr/share/X11/fonts/100dpi/,/usr/share/X11/fonts/75dpi/,/usr/share/X11/fonts/Type1/"

Thank you all for this forum![/QUOTE]

This finally got my NX working! Thanks for the tip!

---

### Post by sjv on 2006-01-25
Well this seems to be the official FreeNX problem thread, so here it goes...

I am running FreeNX v 1.4.0-45-SVN OS (GPL) package on my Ubuntu machine, and trying to connect via a Win32 !m client. I have any number of errors, from the X cookie problem, to unable to reconnect to existing session errors. Sometimes though it does connect, but all I get is a black screen with a !m logo in the middle, and that's it. 

I have tried the suggested fix of running Custom and running the script at the server instead of GNOME, but the same thing happens. Any ideas where I can start guys? Has anyone experienced the black screen issue?

--update--
I was just able to have someone test it out, and they were able to connect successfully from their Fedora machine. So this appears to be a problem with the win32 client. Obviously this isn't a windows forum, but if anyone has any experience with getting this to work it would be appreciated.

Thanks,
Steve

---

### Post by logichype on 2006-02-08
OK as the previous user posted, this is the best thread I've found on the internet dedicated to freeNX, and it's also pretty close to matching my config/problem.  Several other users have had my exact problem and I'm not sure if they solved it or not.  I tried what has been suggested to no avail.  So here is more on the subject.

I started trying to set up freeNX yesterday.  I just found out about it actually.  I was having trouble setting up vncserver (I've done it before but this time it wouldn't take) so I decided to try freeNX.  At this point, I'm pretty interested in investigating NX because after what I've read I think it should work better than vnc for home-work connetions.

I'm not on Ubuntu, please forgive me, I actually started with Knoppix 4.0 and upgraded to more of a Debian Sarge.  But although there are differences, I think I've troubleshot to the point where it makes no difference.  But just be aware.  Some files are probably in different places or whatnot.

The problem with vncserver was with loading fonts.  It says it can't load the fixed font.  It also won't init the font patch for misc, which is where the fixed font is.  However, outside of nx/vnc, X is working fine for me, and has been all along.  I'm using xorg not XF86 and I'm using it right now.  KDE works fine.  I'm on this page in firefox under X.  But I think the vncserver package may use it's own internal X server....

So I moved on to try NX and I got past all the ssh/port/security stuff.  I got to the point where from the client (no matter linux or windows) it comes up and has an X window, with a big X cursor that even works for a second.  The background is a red and black (and white?) !M logo.  It stays for a second and then it dies.  Looking in the client logs it shows nothing much amiss.  It says it connected to X but then a disconnect was requested from the remote proxy.

Info: Established X server connection.
Info: Using shared memory support in X server.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.

I increased the log level and found in the log under var/log on the server not much more info.  I could tell that something was going wrong either starting X or just after.  So I finally figured out there is an option in node.conf to NOT delete temporary log files for each session.  So then under ~/.nx I had some subdirs (long names) and inside is a session log.  so under ~/.nx/C-...../session I found some more info (exerpt):

Info: Using alpha channel in render extension.
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/latex-ttf-fonts, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/defoma/CID, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/defoma/TrueType, removing from list!

Fatal server error:
could not open default font 'fixed'
Info: End of session requested by agent termination.

Ah-HAH!!  The same culprit.  I gave up on vncserver because I figure it's built against a different X Server and there was an incompatibility.  But I don't see why freeNX should do that -- I thought it should work with my already-installed X Server and just talk to it.

To support this theory, I read an article about freeNX hosted on Linux Journal ([http://www.linuxjournal.com/article/8489](http://www.linuxjournal.com/article/8489)) and it has some protocol diagrams.  It looks to me like NXAgent talks to your local X Server, sort of impersonating an X client.  So in other words, it should use your local X server not it's own or any other.

So during this whole charade, I've tried everything I can think of to get the fonts configured.  Obviously for some reason when NX tries to launch X, X can't load the fixed font, which it considers a base requirement, and it bails.  It's my belief after much research that the fixed font should reside in the misc folder.  On my system, that is under /usr/X11R6/lib/X11/fonts/misc.  I have tried many things to resolve this, including reacquiring the xfonts-base packages, unzipping the contents of misc (gunzip *.gz), rebuilding the font directory using mkfondir and also update-fonts-alias, update-fonts-scaled, and update-fonts-dir (the last I believe is the same as mkfontdir but I tried both).  I also tried to alter the node.conf with the extra agent config option -fp and made sure all the paths given are correct.  They are all fine.  I also checked in the fonts.alias file (before and after rebuild with update-fonts-alias) and it does contain an alias line for fixed.

What I can't figure out is that when freeNX tries to lauch X it says it can't init the path for the misc fonts.  but when I launch it myself either manually or just by rebooting, it inits the path fine, finds the fixed font and everything is cool.  But when NX tries, it can't do it.

I would suspect that freeNX might also have it's own embedded X server, based perhaps on XF86, and it may not be compatible with my fonts directory -- but the diagrams shown on the url I supplied contradict that.

I gave a lot of info both to help others and to help any potential helpers help me.  If anyone has any ideas that would be great, I'm about out of ideas.

I would like to either 1) resolve my font problem by some configuration magic in node.conf or xorg.conf using my current misc fonts directory (must work for both my natural X session (KDE) I use at my desktop when home and for the freeNX session that will be started if I log in remotely).  or 2) I could create a misc2 fonts directory and add it to the fonts path in node.conf if that would work, and if I could figure out how to get such a fonts directory that would match the one X wants when launched via nxserver.  Or 3) you tell me what I'm missing :)

Thanks

---

### Post by ihristov on 2006-02-11
I added the backports repository, but I can't find the freenx package
I am running Hoary (5.04)

```

$ sudo su
$ echo "deb http://archive.ubuntu.com/ubuntu/ hoary-backports main restricted universe multiverse" >> /etc/apt/sources.list
$ apt-get update
 ... No errors ...
$ apt-get install freenx
Reading package lists... Done
Building dependency tree... Done
Package freenx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package freenx has no installation candidate

```

---

### Post by cosmolee on 2006-03-06
Anybody???

I'm having the same problem with Breezy - I added the same line, except for "breezy-backports".  Apt-get can't find the package...:confused:

---

### Post by malaprohibita on 2006-03-06
I'm having the same problem as Steve with my win32 client.  Anyone know which direction to turn?  I really appreciate it!

[QUOTE=sjv]Well this seems to be the official FreeNX problem thread, so here it goes...

I am running FreeNX v 1.4.0-45-SVN OS (GPL) package on my Ubuntu machine, and trying to connect via a Win32 !m client. I have any number of errors, from the X cookie problem, to unable to reconnect to existing session errors. Sometimes though it does connect, but all I get is a black screen with a !m logo in the middle, and that's it. 

I have tried the suggested fix of running Custom and running the script at the server instead of GNOME, but the same thing happens. Any ideas where I can start guys? Has anyone experienced the black screen issue?

--update--
I was just able to have someone test it out, and they were able to connect successfully from their Fedora machine. So this appears to be a problem with the win32 client. Obviously this isn't a windows forum, but if anyone has any experience with getting this to work it would be appreciated.

Thanks,
Steve[/QUOTE]

---

### Post by cosmolee on 2006-03-06
In answer to my own question - here's the link to the Wiki page for FreeNX on Ubuntu, it seems to have updated info:

[https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX)

HTH...

---

### Post by malaprohibita on 2006-03-08
I ended up fixing the problem, but it wasn't an ideal solution.  I reinstalled Breezy, reinstalled the FreeNX server, and... voila!  No more problem on the Win32 client end.  Thankfully it was a test machine and I didn't have to worry about wiping out crucial data, but I know not everyone will have that option.

---

### Post by pacele on 2006-03-18
[QUOTE=halvdansk]I get the same error as **[SIZE="3"]beelzebub1987[/SIZE]**
(i have purged and reinstalled it **with** nxsetup --setup-nomachine-key)

blah
blah
Please check your ssh setup:

- Make sure "nx" is one of the AllowUsers in sshd_config.
- Make sure your sshd allows public key authentication.
- Make sure your sshd is really running on port 22.
- Make sure your sshd_config AuthorizedKeysFile in sshd_config is set to authorized_keys2.

any ideeas? thx
(running breezy btw)[/QUOTE]


... got the same problems ... comeon give us a hint ;-)

---

### Post by ... on 2006-05-03
I am having trouble getting this working...
I folowed the tutorial and used the nomachine key, set up the windows client to connect to port 22 with the setting under desktop as os type-unix gnome. But when I try to connect it immediatly gives me 'cannot start the local X server' It looks like it might have flashed up one other message, but I coudn't read it...

I can ssh into the box with putty just fine, and vnc works (but loading my 60mb desktop is slow even with a 10mbs lan connection), but I can't make freenx do anything...

Does the fact that I am running a twinview (2 monitors, one has the desktop on it and the other is just free space to put windows) setup be messing with it? 

Where do I find the logs to see what is hapening?

Thanks!

btw, if you are having trouble getting the files, use deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) breezy-seveas freenx
works great

---

### Post by eas on 2006-05-13
**Update:**  I did some of the troubleshooting in [this post]("http://www.ubuntuforums.org/showpost.php?p=894293&postcount=60"), specifically deleting the ~/.Xauthority* and it seems to work.  Now if only I could get it to run at 1600x1200.

---------------------------------------------------------------------------------
**Original post**:

So, I can't get this working either.  When I initiate the connection from windows I use the Gnome desktop setting.  It seems to be getting pretty far, it starts to instantiate a display on my windows machine, but then the NoMachine client fails:

```
Info: Proxy running in client mode with pid '5024'.
Info: Connecting to remote host '192.168.1.135:5000'.
Info: Connection to remote proxy '192.168.1.135:5000' established.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Not using NX delta compression.
Info: Using lan link parameters 16384/8/0/0.
Info: Using pack method '16m-jpeg-9' with session 'unix-gnome'.
Info: Not using ZLIB stream compression.
Info: Not using remote ZLIB stream compression.
Info: Not using persistent cache.
Info: Using remote server '192.168.1.135:5000'.
Info: Starting X protocol compression.
Info: Established X server connection.
Info: Using shared memory support in X server.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.
```

When I check the session log on my ubuntu box, I get this towards the end of the log:
```
Info: No window manager has been detected.
nxagentOpenScreen: No window manager is running, forcing fullscreen mode.
Info: Using local device configuration changes.
Info: Using alpha channel in render extension.
Info: Adding the X connection 3 to the device set.
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Error:            Can't find file "en_US" for symbols include
>                   Exiting
>                   Abandoning symbols file "default"
Errors from xkbcomp are not fatal to the X server
Info: Session started, state is [SESSION_UP].
Info: Entering dispatch loop with exception 0x0.
AUDIT: Sat May 13 10:19:21 2006: 24522 nxagent: client 1 rejected from local host
Xlib: connection to "unix:1000.0" refused by server
Xlib: No protocol specified


(gnome-session:24534): Gtk-WARNING **: cannot open display:
Info: Exiting dispatch loop with exception 0x2.
Info: End of session requested by agent termination.

```

Any ideas?  I'd really love to get this working.

---

### Post by kaveraj on 2006-05-16
I also found this page [https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX) which says

> Note: Some people will tell you to add kanotix or backports as a source. Do not do this. It is deprecated

My recommendation will be to follow the wiki. Nice detailed howto though.

---

### Post by ... on 2006-06-10
Has anyone managed to get by the problem with the windows client that when you try to resume a suspended session your desktop turns into the remote one, you get a little window that is supposed to the remote desktop, and you can't close the connection?

Quite a frustrating problem >_<

---

### Post by peroxyd on 2006-07-03
My problem is quite similar. I am trying to connect from my Windows XP machine to my Ubuntu Dapper Drake system. I have installed NXServer viea the seveas repository and it does seem like everything works quite well. The Client can connect, is authenticated but in the end the x server connection just doesnt come up. I can actually see in the NX session administrator that the session is then still alive. Just the x server connection cant be established as it seems. I did see once or twice a black screen with the nomachine logo as well (this only happened when I requested a full screen connection). 

The session log looks like this:

Info: Display running with pid '11768' and handler '0x360ab2'.
NXPROXY - Version 2.0.0

Copyright (C) 2001, 2006 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '8604'.
Session: Starting session at 'Mon Jul  3 08:46:52 2006'.
Info: Connecting to remote host '10.104.1.190:5000'.
Info: Connection to remote proxy '10.104.1.190:5000' established.
Warning: Connected to remote NXPROXY version 1.5.0 with local version 2.0.0.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Warning: Font server connections not supported by the remote proxy.
Info: Using lan link parameters 1536/24/1/0.
Info: Using image streaming parameters 50/128/1024KB/6144/768.
Info: Using pack method '16m-jpeg-9' with session 'unix-gnome'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using persistent cache.
Info: Using remote server '10.104.1.190:5000'.
Info: Forwarding SMB connections to port '139'.
Info: Forwarding multimedia connections to port '6000'.
Session: Session started at 'Mon Jul  3 08:46:52 2006'.
Warning: Cookie mismatch in the authentication data.
Session: Terminating session at 'Mon Jul  3 08:55:52 2006'.
Info: End of NX transport requested by remote.
Info: Your session was closed before reaching a usable state.
Info: This can be due to the local X server refusing access to the client.
Info: Please check authorization provided by the remote X application.
Info: Shutting down the NX transport.
Session: Session terminated at 'Mon Jul  3 08:55:52 2006'.

The Ubuntu laptop is in my office and I try to connect from home to it via a VPN connection. However this also doesnt work when im actually in the office with the windows laptop.

I really really love to get this working...

Chris

---

### Post by s_h_a_d_o_w_s on 2006-07-04
I can't get it to find package freenx.

---

### Post by ordou on 2006-07-09
> **eas said:**
> **Update:**  I did some of the troubleshooting in [this post]("http://www.ubuntuforums.org/showpost.php?p=894293&postcount=60"), specifically deleting the ~/.Xauthority* and it seems to work.  Now if only I could get it to run at 1600x1200.

---------------------------------------------------------------------------------
**Original post**:

So, I can't get this working either.  When I initiate the connection from windows I use the Gnome desktop setting.  It seems to be getting pretty far, it starts to instantiate a display on my windows machine, but then the NoMachine client fails:

(...)

Any ideas?  I'd really love to get this working.

I had this problem (and these error messages) myself, and I can confirm that deleting the .Xauthority* files in my home directory solved the problem.

---

### Post by matcram on 2006-07-13
> **peroxyd said:**
> My problem is quite similar. I am trying to connect from my Windows XP machine to my Ubuntu Dapper Drake system. I have installed NXServer viea the seveas repository and it does seem like everything works quite well. The Client can connect, is authenticated but in the end the x server connection just doesnt come up. I can actually see in the NX session administrator that the session is then still alive. Just the x server connection cant be established as it seems. I did see once or twice a black screen with the nomachine logo as well (this only happened when I requested a full screen connection). 

The session log looks like this:

Info: Display running with pid '11768' and handler '0x360ab2'.
NXPROXY - Version 2.0.0

Copyright (C) 2001, 2006 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '8604'.
Session: Starting session at 'Mon Jul  3 08:46:52 2006'.
Info: Connecting to remote host '10.104.1.190:5000'.
Info: Connection to remote proxy '10.104.1.190:5000' established.
Warning: Connected to remote NXPROXY version 1.5.0 with local version 2.0.0.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Warning: Font server connections not supported by the remote proxy.
Info: Using lan link parameters 1536/24/1/0.
Info: Using image streaming parameters 50/128/1024KB/6144/768.
Info: Using pack method '16m-jpeg-9' with session 'unix-gnome'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using persistent cache.
Info: Using remote server '10.104.1.190:5000'.
Info: Forwarding SMB connections to port '139'.
Info: Forwarding multimedia connections to port '6000'.
Session: Session started at 'Mon Jul  3 08:46:52 2006'.
Warning: Cookie mismatch in the authentication data.
Session: Terminating session at 'Mon Jul  3 08:55:52 2006'.
Info: End of NX transport requested by remote.
Info: Your session was closed before reaching a usable state.
Info: This can be due to the local X server refusing access to the client.
Info: Please check authorization provided by the remote X application.
Info: Shutting down the NX transport.
Session: Session terminated at 'Mon Jul  3 08:55:52 2006'.

The Ubuntu laptop is in my office and I try to connect from home to it via a VPN connection. However this also doesnt work when im actually in the office with the windows laptop.

I really really love to get this working...

Chris

You seem to have 1.5 version on your server and you are trying to connect with the V2.0
Installing the 1.5 version of the client solved the problem for me.

You can grab it here : [http://64.34.161.181/download/1.5.0/client/nxclient-1.5.0-138.exe](http://64.34.161.181/download/1.5.0/client/nxclient-1.5.0-138.exe)

---

### Post by peroxyd on 2006-07-13
Thanks so much. This was indeed the issue. Its pretty stupid that nomachine does not mention this incompatibility anywhere...

This works really awesome now...
So much faster the VNC

---

### Post by botcolon on 2006-07-15
help! newb

getting this error:

NXPROXY - Version 1.5.0

Copyright (C) 2001, 2005 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '2144'.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Not using NX delta compression.
Info: Using lan link parameters 16384/8/0/0.
Info: Using pack method '16m-jpeg-9' with session 'unix-gnome'.
Info: Not using ZLIB stream compression.
Info: Not using remote ZLIB stream compression.
Info: Not using persistent cache.
Info: Starting X protocol compression.
Warning: Protocol mismatch in the authentication data.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.

---

### Post by gumbald on 2006-07-18
What is the client V2 designed for? Is there a new server to be released?

---

### Post by scifan on 2006-07-24
it seems like the version 2.0 client has been engineered so that it doesn't work with the Freenx version of the server.

---

### Post by Predseda3D on 2006-08-03
> **scifan said:**
> it seems like the version 2.0 client has been engineered so that it doesn't work with the Freenx version of the server.

Hi,

If somebody have problem with NX Clients versions 2.0.0 and FreeNX 0.4.x or 0.5.0, you can read wiki about this problem and solution here: 
[http://openfacts.berlios.de/index-en.phtml?title=FreeNX_FAQ/Problem_Solving]("http://openfacts.berlios.de/index-en.phtml?title=FreeNX_FAQ/Problem_Solving")
or here:
[http://wiki.debian.org/freenx]("http://wiki.debian.org/freenx")
or here:
[http://gentoo-wiki.com/Talk:HOWTO_FreeNX_Server#Solutions_for_NX_Clients_versions_2.0.0_and_FreeNX_0.4.x_and_0.5.0]("http://gentoo-wiki.com/Talk:HOWTO_FreeNX_Server#Solutions_for_NX_Clients_versions_2.0.0_and_FreeNX_0.4.x_and_0.5.0")

Hope that will help. 

Predseda

---

### Post by rick_1010 on 2006-09-13
> **scifan said:**
> it seems like the version 2.0 client has been engineered so that it doesn't work with the Freenx version of the server.

I have been successfully using the 2.0 client with the latest version of FreeNX on a Fedora system for a while, so I don't believe this can be true, unless it is only related to the Debian version of FreeNX

---

### Post by rick_1010 on 2006-09-13
"Please check your ssh setup:

- Make sure "nx" is one of the AllowUsers in sshd_config.
- Make sure your sshd allows public key authentication.
- Make sure your sshd is really running on port 22.
- Make sure your sshd_config AuthorizedKeysFile in sshd_config is set to authorized_keys2."



-- I'm still stuck on this error after trying for a long time to get this to work (weeks), I have edited the ssh_config file exactly as it says, re-started ssh and still I am not able to connect (I get the long error message that ends, "killed by signal 15")

Does anyone have any idea what else could be stopping this from working, when I connect from the NXClient it is able to connect and authenticate but then dies before opening the window to view the desktop.

---

### Post by mibikerguy on 2006-10-25
I am currently running the most recient versions of the FreeNX server; node; and client on my Ubuntu server machine. All appears "well" on the server in that I have a LAMP functions running and am using WordPress successfully. My desktop machine is Windoze XP upon which I have installed PuTTY and the Windows client for FreeNX. I am able to connect to my Ubuntu server via PuTTY and have control as expected. When connecting with the NoMachine Windows client (2.1.0-6), I am able to authenticate on the server and the NoMachine logo appears on my Windows monitor. However, soon after the NoMachine logo appears, I am disconnected, and the following message appears on the Windows box:

"The connection with the remote server was shut down. Please check the state of your network connection"

I immediately connect with PuTTY and am able to establish a connection, so I dont believe the network is causing this error. There are no significant messages in the server logs that would indicate any specific problems, so I am at a loss!

Anyone have any ideas? Please?!

---

### Post by ihristov on 2006-10-25
> **mibikerguy said:**
> When connecting with the NoMachine Windows client (2.1.0-6),

What is the version of the server?

On my system the server is 1.5. The client I use to sucesfully connect is 1.5.0-114

---

### Post by mibikerguy on 2006-10-25
Thanks for the prompt reply to my situation.

I am currently using Server Ver. 2.1.0-9; Node Ver. 2.1.0-7; NX Client (on the Ubuntu box for test purposes) Ver. 2.1.0-6; and on the Windoze box Ver. 2.1.0-6

From the windows client, I see the "Connected"; and "Authentication"; messages followed by the red logo with the two letters, and after a couple of seconds, the connection is droped. As stated above, the error message is:"The connection with the remote server was shutdown; Please check the state of your network connection."
The curious thing, is that I cannot determine if the server (host) is dropping the connection, or if the windows box is dropping the connection. 

Suggestions ?

Tom

---

### Post by citizenkahn on 2006-11-01
I have edgy-eft and tried many ways to install freenx (nxserver) and I found a combination of several other methods worked for me.  Here's what worked for me...

FYI, I did the following as root (because I'm a bad man), but you could use sudo.

1. Add kanotix to my source list (nano /etc/apt/sources.list)
deb [http://debian.tu-bs.de/project/kanotix/unstable/dists/unstable/nx/binary-i386/](http://debian.tu-bs.de/project/kanotix/unstable/dists/unstable/nx/binary-i386/) ./

2. update my sources (apt-get update)

3. install the client (apt-get install nxclient)
  it will fail and recommend running apt-get with -f to
  get the dependencies

4. get the dependencies (apt-get -f install)
  stdc++ libs will come down and then the client will come down

5. apt-get nxnode
6. apt-get nxserver
7. setup my sshd to use the default key for the server
 nano /etc/ssh/sshd_config
add this line:
  
8. restart sshd
 /etc/init.d/ssh restart

9. check my server
 /usr/NX/bin/nxserver --status

Hope this helps...
 
Then I was all set
4. See if fail and recommend the -f for dependencies
5. get the dependencies (su

---

### Post by marx2k on 2006-11-13
can you re-post this howto for edgy as it is missing some parts... also, when I try to apt get update, i get:

Failed to fetch [http://debian.tu-bs.de/project/kanot...x/binary-i386/./Packages.gz](http://debian.tu-bs.de/project/kanot...x/binary-i386/./Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by marx2k on 2006-11-13
I got this working by matching a client version for XP with the server version (1.5) running on edgy.

However, your instructions are broken:


Failed to fetch [http://debian.tu-bs.de/project/kanot...x/binary-i386/./Packages.gz](http://debian.tu-bs.de/project/kanot...x/binary-i386/./Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by mbailey on 2006-11-18
I have the classic issue with incompatible versions of freenx client and server and would like to get a windows version 1.5 client. I can't find it on the Nomachines site  - any ideas where I can get it?

---

### Post by StratosL on 2006-11-19
I have found this guide at debianadmin.com, in case it helps anyone:

[http://tinyurl.com/yhry4m](http://tinyurl.com/yhry4m)

StratosL

---

### Post by StratosL on 2006-11-19
Just found out that FreeNX development has stopped, apart from the company NoMachine's free-as-in-free-beer version. 

In the same thread, 2x.com's open source version of NX was suggested.

[http://tinyurl.com/ygzaha](http://tinyurl.com/ygzaha)

---

### Post by robert@debian on 2006-11-28
Folks I've just found a possibilty to suspend and resume my X session.
Just press the key combo **strg+alt+t**.
I don't know if i just works in newer Versions, I'm using 2.1.0 from nomachine.com and it works great :KS

---

### Post by marx2k on 2006-11-29
Does anyone know how to get FreeNX server to initiate ZLib streaming compression? 

The server still seems kind of slow to me. :(

---

### Post by cosmolee on 2006-12-07
Is there no freenx for Edgy?  Synaptic comes up empty for a source for freenx even after an update.  All the instructions I can find are for Dapper and previous versions.  

Any help?

TIA

---

### Post by behemot on 2006-12-13
Some people successfully use debs for dapper or the ones from  NoMachine in edgy.  It works if you connect windows client to nxserver.  I was unable to get it to work under edgy, but I am connecting from other edgy workstations.

Setup was OK, but when I connect I get only a black screen with working mouse, but session never completes loading.

So far there is no debs for edgy.  We have to wait.

---

### Post by cosmolee on 2006-12-16
I've noticed that NXAGENT is available for Edgy.  Can this be used in lieu of FreeNX?  I have no experience with XNest, but nxagent is said to be a NX substitute for xnest.  

While it doesn't look like nxagent could display one's primary X server display, one could run a nested X server and access that remotely.  Could this be the answer to our woes?

Anyone have experience with this?  I couldn't find anything searching "nxagent" nor "xnest" in these forums...

Cosmo

---

### Post by peterLinux on 2006-12-29
This may be it for Edgy users

[http://free.linux.hp.com/~brett/seveas/freenx/dists/edgy-seveas/](http://free.linux.hp.com/~brett/seveas/freenx/dists/edgy-seveas/)

---

### Post by f1re on 2006-12-29
> **peterLinux said:**
> This may be it for Edgy users

[http://free.linux.hp.com/~brett/seveas/freenx/dists/edgy-seveas/](http://free.linux.hp.com/~brett/seveas/freenx/dists/edgy-seveas/)

empty :(

no amd64 still?

---

### Post by Tribe on 2007-01-10
Hi there,

I was having the same prob accessing from a 2.x windows client to a 1.x server. What i am now looking for is a link to download the 1.5 client, anyone got it?

Thanks :)

Edit: found it here: [ftp://turing.une.edu.au/pub/comp131/nxclient/nxclient_windows](ftp://turing.une.edu.au/pub/comp131/nxclient/nxclient_windows) and it works :D

---

### Post by katsumi on 2007-01-23
Hola,

Did you every find a solution to running NX server in edgy??

Thanks,

katsu

---

### Post by cmoz on 2007-01-24
anyone able to get the new incarnation of freenx (2X) working?

---

### Post by hscottyh on 2007-01-24
> **katsumi said:**
> Hola,

Did you every find a solution to running NX server in edgy??

Thanks,

katsu

works great, just use the seveas dapper repository to install it. I haven't had any issues using the 1.x client.

---

### Post by weeksben1 on 2007-01-31
I"ve got FreeNX (2.x) loaded on my edgy box, but when I try to start a session, I can  connect and get to the point where it tries to start the x session and then it fails.  I'm including the log file from my Windows XP machine.  I can SSH and VNC in directly w/o any problems.

Thanks,

Ben

NX> 203 NXSSH running with pid: 4008
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 75.46.243.133 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.4.0
NX> 134 Accepted protocol: 1.4.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: bweeks
NX> 102 Password: 
NX> 103 Welcome to: TESTSRV02 user: bweeks
NX> 105 listsession --user="bweeks" --status="suspended,running" --geometry="1024x768x32+render" --type="unix-kde"
NX> 127 Sessions list of user 'bweeks' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: bweeks
NX> 105 startsession  --link="adsl" --backingstore="1" --nodelay="1" --encryption="1" --cache="8M" --images="32M" --media="0" --session="TESTSRV02" --type="unix-kde" --cookie="******" --geometry="fullscreen" --kbtype="pc102/en_US" --screeninfo="800x600x32+render" 

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: TESTSRV02-1000-14FA61D300920D20C06686438DEA676A
NX> 705 Session display: 1000
NX> 703 Session type: unix-kde
NX> 701 Proxy cookie: 1d41fde1d5b98e405b0e8e316777021d
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: ec0d04706993118df8b99d4dc95187c9
NX> 704 Session cache: unix-kde
NX> 707 SSL tunneling: 1
NX> 504 Session startup failed.
Killed by signal 15.

---

### Post by Ashex on 2007-02-08
To run freenx server in edgy, you can install the dapper packages from the seveas repositories.

There's an article in the ubuntu wiki that you can read [Here](https://help.ubuntu.com/community/FreeNX) about setting it up.

I recommend using the following repository for installing the packages:

```
deb http://seveas.imbrandon.com dapper-seveas freenx 
deb-src http://seveas.imbrandon.com dapper-seveas freenx
```

Add that to /etc/apt/sources.list

and then run the following commands:

```

wget http://seveas.imbrandon.com/1135D466.gpg -O- | sudo apt-key add - 
sudo apt-get update && sudo apt-get install freenx

```


With the packages in the repository, these are 1.5, not 2.0.
So if you want to connect from a windows machine, grab the V1.5 nxclient [Here](http://www.industrial-statistics.com/info/nxclients?IndStats=bbf349f90a518f5a54f290e887d9c768).

---

### Post by SubTerRaiN on 2007-02-09
have a question:

how can i re-enter an existing session, say display 1000 ?

because i open several programs there, i suspend my session, and when i try to enter that session - a new one, say 1001, is created, and i cannot access my apps from 1000...

any ideas ?

thanks.

---

### Post by tannedin on 2007-02-12
> **Ashex said:**
> To run freenx server in edgy, you can install the dapper packages from the seveas repositories.

There's an article in the ubuntu wiki that you can read [Here](https://help.ubuntu.com/community/FreeNX) about setting it up.

I recommend using the following repository for installing the packages:

```
deb http://seveas.imbrandon.com dapper-seveas freenx 
deb-src http://seveas.imbrandon.com dapper-seveas freenx
```

Add that to /etc/apt/sources.list

and then run the following commands:

```

wget http://seveas.imbrandon.com/1135D466.gpg -O- | sudo apt-key add - 
sudo apt-get update && sudo apt-get install freenx

```


With the packages in the repository, these are 1.5, not 2.0.
So if you want to connect from a windows machine, grab the V1.5 nxclient [Here](http://www.industrial-statistics.com/info/nxclients?IndStats=bbf349f90a518f5a54f290e887d9c768).

tried this, now getting a "Server not installed or NX access disabled"
```
NX> 203 NXSSH running with pid: 13801
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 68.54.239.81 on port: 3838
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.
```

---

### Post by oldweasel on 2007-02-23
I get that message also, anyone know how to get around this final issue?

---

### Post by Nu_ on 2007-03-08
Please check your ssh setup:

        - Make sure "nx" is one of the AllowUsers in sshd_config.
        - Make sure your sshd allows public key authentication.
        - Make sure your sshd is really running on port 22.
        - Make sure your sshd_config AuthorizedKeysFile in sshd_config is set to authorized_keys2.

when i run nxsetup i get this, does anyone know how to add a user to sshd?

---

### Post by gambit32 on 2007-06-01
[B]DISREGARD: FIXED

I was able to fix this by changing
127.0.0.1 localhost
in /etc/hosts to
127.0.0.1 localhost unix[/B]

For some reason today, Im no longer able to login to freenx.  I get a black window, and its not able to load a window manager.  

I tried uninstall freenx entirely, and reinstalling from scratch, to no avail.  I get this from 3 different client machines, of none of whose settings have changed


```

gambit32@ubuntu:~/.nx/C-ubuntu-1000-811529A990DCF8731709D52C8710D456$ cat session

NXAGENT - Version 2.1.0

Copyright (C) 2001, 2006 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Agent running with pid '7570'.
Session: Starting session at 'Fri Jun  1 12:32:36 2007'.
Info: Proxy running in server mode with pid '7570'.
Info: Waiting for connection from '192.168.1.146' on port '5000'.
Info: Accepted connection from '192.168.1.146' with port '3829'.
Info: Connection with remote proxy established.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using wan link parameters 768/24/1/0.
Info: Using agent parameters 5000/50/0/0.
Info: Using cache parameters 4/4194304/8192KB/8192KB.
Info: Using image streaming parameters 50/128/1024KB/3072/384.
Info: Using image cache parameters 1/1/32768KB.
Info: Using pack method '16m-jpeg-9' with session 'unix-gnome'.
Info: Using ZLIB data compression 1/1/32.
Info: Not using ZLIB stream compression.
Info: No suitable cache file found.
Info: Established X client connection.
Info: Using shared memory parameters 1/1/1/2048K.
Info: No window manager has been detected.
nxagentOpenScreen: Forcing fullscreen mode with no window manager running,
Info: Using local device configuration changes.
Info: Using alpha channel in render extension.
Session: Session started at 'Fri Jun  1 12:32:37 2007'.
SESSION_MANAGER=local/ubuntu:/tmp/.ICE-unix/7582

```

---

### Post by joker535 on 2007-11-08
I have my server end setup and working fine on 7.04. I have the windows client running on my laptop and I can successfully connect to my ubuntu box from the lan. 

I went into the router and forwarded port 22 tcp to the static ip of my server. I have a static IP on the wan side and when I put it in the client, I can not connect tot he server.

What am I doing wrong?

Thanks

Bob

---

### Post by daflame on 2007-11-18
If anyone is interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If anyone needs other dist packages, please let me know and I'll start a VM to build one.

---

### Post by c-m on 2007-11-22
[http://kanotix.com/files/debian/](http://kanotix.com/files/debian/) ./ 

does not exist

---

### Post by qpieus on 2007-11-22
> **daflame said:**
> If anyone is interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If anyone needs other dist packages, please let me know and I'll start a VM to build one.

yes, I'm interested. Where can i get it (gutsy i386)?

---

### Post by c-m on 2007-11-25
this guide seems to be out of date. Where can I get freenx for gusty?

---

### Post by daflame on 2007-11-27
> **c-m said:**
> this guide seems to be out of date. Where can I get freenx for gusty?

I have created a new forum and posted packages for Gutsy there.  I imagine that the equivalent Debian version to Gutsy will also work, but it is untested.  Get the packages here:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---

