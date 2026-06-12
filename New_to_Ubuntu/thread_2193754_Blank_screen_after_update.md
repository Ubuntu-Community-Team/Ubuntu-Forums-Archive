---
title: "Blank screen after update"
date: 2013-12-14
forum: New to Ubuntu
---

### Post by johnwill on 2013-12-14
Hello.
I am asking for help again.
I am unable to boot into Ubuntu 12.04 after reconfiguring Locales: sudo dpkg-reconfigure locales.
locales en-GB.UTF-8 reconfigured successfully.
Log out successful-not able to shutdown properly. am now on windows.
System: Lenovo desktop dual boot with windows 7.
Thank you.
John

---

### Post by thatredbird on 2013-12-14
It looks like it has been several hours.  I am sure that you have already tried this option, however just in case you could try holding shift as the computer starts up.  If the main startup intentionally hides the grub loader, sometimes you can still get to it.  Otherwise you may need to use a cd to fix your grub2 package.

---

### Post by johnwill on 2013-12-15
Hello thatredbird
Thank you for your answer-I attemped to start using Shift at boot: into to recovery mode. repaired broken packages;
Tried to boot- message /proc/self/fd9:  3:/etc/default/locale:=en_GB.UTF8:not found.
Screen shows Ubuntu 12.04 but unable to boot.
Is there anything that I can now attempt.
Thank you 
John

---

### Post by asus-user on 2013-12-15
> **johnwill said:**
> -I attemped to start using Shift at boot: into to recovery mode. repaired broken packages;
Tried to boot- message /proc/self/fd9:  3:/etc/default/locale:=en_GB.UTF8:not found.


Try to reset locales by using the following commands while you are in recovery mode:
```
sudo apt-get install language-pack-en-base
sudo dpkg-reconfigure locales
```

If there were some missing files you might need to re-install locales :
```
apt-get install --reinstall locales 
```

For fixing your grub2 refer to:
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Try that and report back.

---

### Post by johnwill on 2013-12-17
hello Asus user.
Thank you for replying: apt-get install: shows error: unknown command 'apt-get'(whilst in recovery mode)
sudo apt-get: Shows error: 'sudo unknown command 'sudo'
You mention Grub2 could you enlighten me on this command.
Thank you. 
John

---

### Post by asus-user on 2013-12-17
> **johnwill said:**
> hello Asus user.
Thank you for replying: apt-get install: shows error: unknown command 'apt-get'(whilst in recovery mode)
sudo apt-get: Shows error: 'sudo unknown command 'sudo'
You mention Grub2 could you enlighten me on this command.
Thank you. 
John

can you please tell exactly what you see on the screen last when you try to boot to ubuntu? something written there might be helpful.

---

### Post by Jonathan Precise on 2013-12-17
Boot into recovery mode (Choose "Ubuntu, with Linux ... (recovery mode)", ehich is the recovery mode kernel). Choose "Drop to root shell prompt" when the menu appears (a text menu).

You should now see:

```
root@***something***:~$
```

Type in:

```
apt-get install -f
apt-get install language-pack-en-base
apt-get install --reinstall locales
dpkg-reconfigure locales
```

Then:

```
reboot
```

This will reboot the system. If the ubuntu logo suddenly gets stuck, press and hold the power button, as the system is already halted, and press the power button to turn it on again, and you'll see the grub menu. If it doesn't get stuck, then the system will reboot, and you will see the grub menu. In both cases, just choose "Ubuntu with linux ..." without "(recovery mode)" Done!

Note: commands posted by asus-user. Just explained it a little more

If anything happens, just tell us. We'll be glad to help!

---

### Post by johnwill on 2013-12-17
Hello Asus User.
Thank you for your patience with my query.
Boot into recovery mode: Blank Screen: flashing curser left of screen; then shows /proc/self/fd/9:  3: /ect default/locale: = en_GB.UTF8: not found no further attempt at boot.

---

### Post by johnwill on 2013-12-17
Hello.
Sorry forgot to mention; after seeing screen in last Pressed  Esc Ubuntu 12.04 shows with the four moving 'dots'but no further attempt at boot.
John

---

### Post by johnwill on 2013-12-20
Hello Jonathan.
Thank you for replying to my cry for help.
I have booted as you suggested, get to Shell Prompt: menu shows: /lib/recovery-mode/options/root:  3:/etc/default/locale:en_GB.UTF8 not found.
                                                                                                       /lib/recovery-mode/options/root:  4:/etc/default/locale:en_GB.UTF8 not found.
                                                                                                       Then : give root password to maintenance(or type Control-D) to continue
Typed Control-D message 'login incorrect' how do I continue now?
Thank you 
John

---

### Post by Jonathan Precise on 2013-12-20
You probably have a root account, and setup a password for it. **_[SIZE=4]THIS IS NOT RECOMMENDED!!!!!![/SIZE]_**. Enter your password, and press enter. Post back any errors.

---

### Post by johnwill on 2014-01-06
Hello.
After many attempts I am no nearer regaining Ubuntu and am now very frustrated, I am back on Windows 7 having had to suffer a Trojan horse attack,and to attempt to download Kb3 for windows and ending up with several unwanted programs.
Where do I go from here?have I lost Linux.
When I attempt to Log on Ubuntu still shows as an OS, so I assume I still have a dual boot system: i have attempted to Log in recovery mode as the wizards on these forums have been kind enough to guide me through,and try to follow their instructions,obviously without success,it must be something I am doing wrong,!!!Oscar Wilde said: It is far more difficult to talk about a thing than to do it.
Doing seems to be my problem.
Please Help.
John

---

