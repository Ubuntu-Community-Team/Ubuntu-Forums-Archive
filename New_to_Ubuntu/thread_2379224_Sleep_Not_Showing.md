---
title: "Sleep Not Showing"
date: 2017-12-02
forum: New to Ubuntu
---

### Post by sparks79 on 2017-12-02
I am Using Ubuntu 17.10 x64 with Gnome Desktop.
I would like to know Why SLEEP does Not Show in The Power Off .
It only Shows Cancel , Power Off and Restart.
Also in Settings/Power There is Nothing there about Sleep.
I am a Windows User for Many Years, and would like to Set my Screen to Sleep After 5 Minutes.
And something else if I am allowed to ad it here, The Annoying Password Reminder.
I am the only user on this pc and this O/S Asks me for a Password to do just about Everything So Annoying, I Don't Need it and Don't Want it.
Even to Wake Up the PC Whilst Asleep.
Any help would be appreciated.
But please go easy on me after all I am only 70 years young.

---

### Post by jasomux on 2017-12-03
First let me say that "Sleep" is called "Suspend" in Ubuntu, if you're having trouble finding some settings. To put your whole computer to sleep (suspend), you click on the system menu in the upper right hand corner, and of course you'll see the Power icon. If you hold down the Alt key, you'll see the icon change to what looks like a "pause" icon. Continue to hold the Alt key and click on the icon and your system will suspend. It's sort of a hidden feature.

As for turning your screen off after 5 minutes, go to **System > Power** and there is a section for "Power Saving." Next to "Blank Screen After" there is a button to click; just pick 5 minutes from the list. Now your screen should turn off automatically after 5 minutes of inactivity.

Now for all the password requests. Ubuntu (as well as most Linux Distributions) is set up with high security in mind. WARNING! I don't normally advise people to turn security settings off, but if you want to make your life a little easier, you can follow along.

To keep your screen from locking when it turns off (no password required when waking the screen up), go to **Settings > Privacy** and click the top box for "Screen Lock" and click the slider for "Automatic Screen Lock" to turn it off.

If you want your computer to boot directly to the desktop without having to stop at the login screen, go to **Settings > Details > Users**. You will need to click the "Unlock" button at the top and enter your password (sorry). Then click the slider for "Automatic Login". Next time you reboot and start your computer it should go right to the desktop without stopping at the login screen.

As for requiring your password when waking the machine up from suspend (sleep), there is no menu setting for that and it requires a terminal command to make the change. I know that intimidates a lot of people. If you wish to proceed, open a terminal by pressing Ctrl+Alt+t or open the applications menu and type terminal in the search box. In the terminal you need to enter the following command followed by the ENTER key:

```
gsettings set org.gnome.desktop.screensaver ubuntu-lock-on-suspend 'false'
```

If you ever want to change this back just re-enter this command and change 'false' to 'true'

With all these changes, the only things you'll encounter on a regular basis that require a password are installing software and updates; Changing this system behavior requires "hacks" and I certainly wouldn't suggest them to anyone. Those you should just live with. I hope this helps.

---

### Post by leunam12 on 2017-12-04
Thank you Jasomux, I didn't know about the ALT trick for suspend, very useful. I was wondering about it.
Now, since I use one of my computer mostly with just a mouse and no keyboard, I installed pm-utils and then modified the sudoers file to enable pm-suspend without password.
Finally I made a .desktop file on the desktop that runs 'sudo pm-suspend' that I can just double-click and it suspends the computer. It is a very useful workaround.

---

