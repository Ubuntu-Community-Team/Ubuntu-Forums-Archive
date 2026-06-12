---
title: "Fresh lubuntu install - can't login to GUI"
date: 2013-07-08
forum: New to Ubuntu
---

### Post by edb66083 on 2013-07-08
I just did a fresh install of lubuntu, but when I try to login, the window just flickers and then returns to the login again. I can login using Guest and it works fine, but when I use my username, no luck. I have tried changing my .Xauthority permissions, but still no luck. Anybody got any ideas?

---

### Post by claracc on 2013-07-09
This thread: [http://askubuntu.com/questions/146137/login-screen-loops-unless-you-login-as-guest](http://askubuntu.com/questions/146137/login-screen-loops-unless-you-login-as-guest) describes a similar problem and proposse different ways to solve the situation.

Perhaps some of them can help you

---

### Post by edb66083 on 2013-07-09
I tried all the different ways, and I'm still not having success. I removed .Xauthority. I changed ownership to username:username. Still no luck. Any other ideas?

---

### Post by BreezyBrooke on 2013-07-09
If it's a fresh install, just reinstall Lubuntu. I've had incidents where Ubuntu botched an install, specifically with X. It may have happened to you as well. So a reinstall may give you a working system this time around.

---

### Post by steeldriver on 2013-07-09
I presume you can log in to a virtual terminal (Ctrl-Alt-F1 etc.)? Have you looked at ~/.xsession-errors? or in /var/log/lightdm/lightdm.log (or the equivalent lxdm log, for older versions of lubuntu)?

---

### Post by edb66083 on 2013-07-09
I tried a re-install, and still have the same problem.

.xsession-errors is empty. Here is my /var/log/lightdm/lightdm.log -->

```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.3, UID=0 PID=1834
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for greeter
[+0.00s] DEBUG: Starting local X display
[+0.01s] DEBUG: Using VT 7
[+0.01s] DEBUG: Activating VT 7
[+0.02s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.03s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.03s] DEBUG: Launching X Server
[+0.03s] DEBUG: Launching process 1839: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.03s] DEBUG: Waiting for ready signal from X server :0
[+0.05s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.06s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.32s] DEBUG: Got signal 10 from process 1839
[+0.32s] DEBUG: Got signal from X server :0
[+0.32s] DEBUG: Connecting to XServer :0
[+0.33s] DEBUG: Starting greeter
[+0.33s] DEBUG: Started session 1844 with service 'lightdm', username 'lightdm'
[+0.41s] DEBUG: Session 1844 authentication complete with return value 0: Success
[+0.41s] DEBUG: Greeter authorized
[+0.41s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+0.41s] DEBUG: Session 1844 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+0.62s] DEBUG: Greeter connected version=1.2.3
[+0.62s] DEBUG: Greeter connected, display is ready
[+0.62s] DEBUG: New display ready, switching to it
[+0.62s] DEBUG: Activating VT 7
[+1.38s] DEBUG: Greeter start authentication for username
[+1.38s] DEBUG: Started session 1894 with service 'lightdm', username 'username'
[+1.40s] DEBUG: Session 1894 got 1 message(s) from PAM
[+1.40s] DEBUG: Prompt greeter with 1 message(s)
[+4.91s] DEBUG: Continue authentication
[+5.17s] DEBUG: Session 1894 authentication complete with return value 0: Success
[+5.17s] DEBUG: Authenticate result for user username: Success
[+5.22s] DEBUG: User username authorized
[+5.23s] DEBUG: Greeter requests session Lubuntu
[+5.23s] DEBUG: Using session Lubuntu
[+5.23s] DEBUG: Stopping greeter
[+5.23s] DEBUG: Session 1844: Sending SIGTERM
[+5.32s] DEBUG: Greeter closed communication channel
[+5.32s] DEBUG: Session 1844 exited with return value 0
[+5.32s] DEBUG: Greeter quit
[+5.37s] DEBUG: Dropping privileges to uid 1000
[+5.37s] DEBUG: Restoring privileges
[+5.42s] DEBUG: Dropping privileges to uid 1000
[+5.42s] DEBUG: Writing /home/username/.dmrc
[+5.42s] DEBUG: Restoring privileges
[+5.44s] DEBUG: Starting session Lubuntu as user username
[+5.44s] DEBUG: Session 1894 running command /usr/sbin/lightdm-session /usr/bin/startlubuntu
[+5.49s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+5.55s] DEBUG: Session 1894 exited with return value 1
[+5.55s] DEBUG: User session quit
[+5.55s] DEBUG: Stopping display
[+5.55s] DEBUG: Sending signal 15 to process 1839
[+5.62s] DEBUG: Process 1839 exited with return value 0
[+5.62s] DEBUG: X server stopped
[+5.62s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+5.62s] DEBUG: Releasing VT 7
[+5.62s] DEBUG: Display server stopped
[+5.62s] DEBUG: Display stopped
[+5.62s] DEBUG: Active display stopped, switching to greeter
[+5.62s] DEBUG: Switching to greeter
[+5.62s] DEBUG: Starting new display for greeter
[+5.62s] DEBUG: Starting local X display
[+5.62s] DEBUG: Using VT 7
[+5.62s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+5.62s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+5.62s] DEBUG: Launching X Server
[+5.62s] DEBUG: Launching process 1941: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+5.62s] DEBUG: Waiting for ready signal from X server :0
[+5.91s] DEBUG: Got signal 10 from process 1941
[+5.91s] DEBUG: Got signal from X server :0
[+5.91s] DEBUG: Connecting to XServer :0
[+5.91s] DEBUG: Starting greeter
[+5.91s] DEBUG: Started session 1944 with service 'lightdm', username 'lightdm'
[+6.00s] DEBUG: Session 1944 authentication complete with return value 0: Success
[+6.00s] DEBUG: Greeter authorized
[+6.00s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+6.00s] DEBUG: Session 1944 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+6.20s] DEBUG: Greeter connected version=1.2.3
[+6.20s] DEBUG: Greeter connected, display is ready
[+6.20s] DEBUG: New display ready, switching to it
[+6.20s] DEBUG: Activating VT 7
[+6.20s] DEBUG: Stopping greeter display being switched from
[+6.93s] DEBUG: Greeter start authentication for username
[+6.93s] DEBUG: Started session 1994 with service 'lightdm', username 'username'
[+6.95s] DEBUG: Session 1994 got 1 message(s) from PAM
[+6.95s] DEBUG: Prompt greeter with 1 message(s)
[+329.94s] DEBUG: Greeter start authentication for guest account
[+329.94s] DEBUG: Session 1994: Sending SIGTERM
[+331.85s] DEBUG: Greeter requests session Lubuntu
[+331.85s] DEBUG: Using session Lubuntu
[+331.85s] DEBUG: Stopping greeter
[+331.85s] DEBUG: Session 1944: Sending SIGTERM
[+331.92s] DEBUG: Greeter closed communication channel
[+331.92s] DEBUG: Session 1944 exited with return value 0
[+331.92s] DEBUG: Greeter quit
[+331.92s] DEBUG: Opening guest account with command '/usr/sbin/guest-account add'
[+333.87s] DEBUG: Guest account guest-RaEbUH setup
[+333.87s] DEBUG: Started session 2097 with service 'lightdm-autologin', username 'guest-RaEbUH'
[+333.96s] DEBUG: Session 2097 authentication complete with return value 0: Success
[+333.96s] DEBUG: Autologin user guest-RaEbUH authorized
[+334.06s] DEBUG: Dropping privileges to uid 107
[+334.06s] DEBUG: Restoring privileges
[+334.10s] DEBUG: Dropping privileges to uid 107
[+334.10s] DEBUG: Writing /tmp/guest-RaEbUH/.dmrc
[+334.10s] DEBUG: Restoring privileges
[+334.10s] DEBUG: Running guest session through wrapper: /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper
[+334.10s] DEBUG: Starting session Lubuntu as user guest-RaEbUH
[+334.10s] DEBUG: Session 2097 running command /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper /usr/sbin/lightdm-session /usr/bin/startlubuntu
[+334.15s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session1
[+395.81s] DEBUG: Session 2097 exited with return value 0
[+395.81s] DEBUG: Closing guest account guest-RaEbUH with command '/usr/sbin/guest-account remove guest-RaEbUH'
[+397.10s] DEBUG: User session quit
[+397.10s] DEBUG: Stopping display
[+397.10s] DEBUG: Sending signal 15 to process 1941
[+397.15s] DEBUG: Process 1941 exited with return value 0
[+397.15s] DEBUG: X server stopped
[+397.15s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+397.15s] DEBUG: Releasing VT 7
[+397.15s] DEBUG: Display server stopped
[+397.15s] DEBUG: Display stopped
[+397.15s] DEBUG: Active display stopped, switching to greeter
[+397.15s] DEBUG: Switching to greeter
[+397.15s] DEBUG: Starting new display for greeter
[+397.15s] DEBUG: Starting local X display
[+397.15s] DEBUG: Using VT 7
[+397.15s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+397.15s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+397.15s] DEBUG: Launching X Server
[+397.15s] DEBUG: Launching process 2336: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+397.15s] DEBUG: Waiting for ready signal from X server :0
[+397.43s] DEBUG: Got signal 10 from process 2336
[+397.43s] DEBUG: Got signal from X server :0
[+397.43s] DEBUG: Connecting to XServer :0
[+397.43s] DEBUG: Starting greeter
[+397.43s] DEBUG: Started session 2339 with service 'lightdm', username 'lightdm'
[+397.52s] DEBUG: Session 2339 authentication complete with return value 0: Success
[+397.52s] DEBUG: Greeter authorized
[+397.52s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+397.52s] DEBUG: Session 2339 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+397.71s] DEBUG: Greeter connected version=1.2.3
[+397.71s] DEBUG: Greeter connected, display is ready
[+397.71s] DEBUG: New display ready, switching to it
[+397.71s] DEBUG: Activating VT 7
[+397.71s] DEBUG: Stopping greeter display being switched from
[+398.42s] DEBUG: Greeter start authentication for guest account
[+401.62s] DEBUG: Greeter requests session Lubuntu
[+401.62s] DEBUG: Using session Lubuntu
[+401.62s] DEBUG: Stopping greeter
[+401.62s] DEBUG: Session 2339: Sending SIGTERM
[+401.70s] DEBUG: Greeter closed communication channel
[+401.70s] DEBUG: Session 2339 exited with return value 0
[+401.70s] DEBUG: Greeter quit
[+401.70s] DEBUG: Opening guest account with command '/usr/sbin/guest-account add'
[+402.88s] DEBUG: Guest account guest-ewL1bX setup
[+402.88s] DEBUG: Started session 2450 with service 'lightdm-autologin', username 'guest-ewL1bX'
[+402.97s] DEBUG: Session 2450 authentication complete with return value 0: Success
[+402.97s] DEBUG: Autologin user guest-ewL1bX authorized
[+403.07s] DEBUG: Dropping privileges to uid 107
[+403.07s] DEBUG: Restoring privileges
[+403.11s] DEBUG: Dropping privileges to uid 107
[+403.11s] DEBUG: Writing /tmp/guest-ewL1bX/.dmrc
[+403.11s] DEBUG: Restoring privileges
[+403.11s] DEBUG: Running guest session through wrapper: /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper
[+403.11s] DEBUG: Starting session Lubuntu as user guest-ewL1bX
[+403.11s] DEBUG: Session 2450 running command /usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper /usr/sbin/lightdm-session /usr/bin/startlubuntu
[+403.16s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session2

```

I'm not sure how to interpret some of it. One thing that stands out is the username 'lightdm' at one point. Is this the problem?

---

### Post by steeldriver on 2013-07-09
The 'lightdm' username is normal I think - the owner should switch once the user session starts

I assume you preserved your home dir when you reinstalled? if so it could be something corrupted in a session file somewhere - not sure where that would be in LXDE (~/.cache/openbox/sessions maybe?) - you could try to figure it out or just delete your whole ~/.cache dir

If you *didn't* preserve your home dir then I have NO idea...

---

### Post by edb66083 on 2013-07-10
I did preserve my /home dir when I did the install, but I thought I deleted all the hidden files and directories (anything that started with a period '.'). But perhaps I missed something. I will check later today when I have time and see if the .cache dir is the problem. I'll look around at other session files, but I'm not familiar with where to find them. Thanks for your help. It is very much appreciated.

---

### Post by edb66083 on 2013-07-10
Well, I think I tried everything that I could find, and still nothing worked. I decided to try another distro since my goal was originally to install lubuntu 12.04 and then upgrade through and up to 13.04, expecting that it would keep the non-pae kernel. But from I have read, you need a fake-pae ppa to accomplish this. I'm just going to try to find another distro that supports non-pae on a ten year old thinkpad. Yeah, it's old, but it still works really well. I'm still using lubuntu on my two other machines. Thanks for everyone's help.

---

