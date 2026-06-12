---
title: "password request when shutdown"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by vibaviattigala on 2012-11-13
is there a way to ask a password like when installing a new apps to shutdown reboot suspend etc?

---

### Post by Wim Sturkenboom on 2012-11-13
Using the command line, you need to use sudo so you will be prompted.

Not sure how to achieve it using the graphical environment.

---

### Post by offgridguy on 2012-11-13
> **vibaviattigala said:**
> is there a way to ask a password like when installing a new apps to shutdown reboot suspend etc?

To install new apps. you will be asked for password verification by default.

---

### Post by dannyboy79 on 2012-11-13
> **offgridguy said:**
> To install new apps. you will be asked for password verification by default.
he already knows that, he's asking if there is a way for the system to ask for a password when a user wants to shutdown, suspend, etc etc.

What process are you using to shutdown? Are you using the drop down menu in the upper right corner? There may be a way to have it prompt for a password BUT what is the real goal, meaning why is it you want it to ask you for a password when you press shudown?

---

### Post by vibaviattigala on 2012-11-13
becasue sometimes my sister trys to shut down the pc

---

### Post by philinux on 2012-11-13
> **vibaviattigala said:**
> is there a way to ask a password like when installing a new apps to shutdown reboot suspend etc?

You might try reversing what's going on here. [http://ubuntuforums.org/showthread.php?t=1713686](http://ubuntuforums.org/showthread.php?t=1713686)

Just be very careful editing that file.

Similar stuff [http://askubuntu.com/questions/1190/how-can-i-make-shutdown-not-require-admin-password](http://askubuntu.com/questions/1190/how-can-i-make-shutdown-not-require-admin-password)

---

### Post by deadflowr on 2012-11-13
If your not on the pc, and your sister has access, lock the screen.
Unfortunately, turning off a pc is easy, as all you have to do is unplug it.

---

### Post by CharlesA on 2012-11-13
> **deadflowr said:**
> If your not on the pc, and your sister has access, lock the screen.
Unfortunately, turning off a pc is easy, as all you have to do is unplug it.
This x 9000.

If you step away from your PC, lock the screen. Physical access = root access.

---

### Post by dannyboy79 on 2012-11-13
> **vibaviattigala said:**
> becasue sometimes my sister trys to shut down the pc
in that case I would suggest just locking the screen within your screensaver settings. set it to decent amount of time and check the box that says "lock screen" upon screensaver. something like that.

I know there is a way to edit the commands within the graphical pull down menus such that you could add a password prompt to it but I can't find the right file to edit....

---

### Post by Cheesemill on 2012-11-13
I've not done this myself but try editing /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy and change the section:
```
  <action id="org.freedesktop.consolekit.system.stop">
    <description>Stop the system</description>
    <message>System policy prevents stopping the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

```to read
 ```
  <action id="org.freedesktop.consolekit.system.stop">
    <description>Stop the system</description>
    <message>System policy prevents stopping the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
[COLOR=Red]      <allow_active>auth_admin_keep</allow_active>[/COLOR]
    </defaults>
  </action>

```

You can also change the reboot section as well.

However, as others have said, this will only be of any use if the system is physically secure as well.

---

### Post by dannyboy79 on 2012-11-13
> **Cheesemill said:**
> I've not done this myself but try editing /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy and change the section:
```
  <action id="org.freedesktop.consolekit.system.stop">
    <description>Stop the system</description>
    <message>System policy prevents stopping the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

```to read
 ```
  <action id="org.freedesktop.consolekit.system.stop">
    <description>Stop the system</description>
    <message>System policy prevents stopping the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
[COLOR=Red]      <allow_active>auth_admin_keep</allow_active>[/COLOR]
    </defaults>
  </action>

```

You can also change the reboot section as well.

However, as others have said, this will only be of any use if the system is physically secure as well.how did you find out about this, that's what I was trying to figure out. Where are files for editing what commands do within the drop down applications menu? I used to love the "Main menu" editor that used to be within System Settings, Administrative back in 10.04.  thanks

---

### Post by newb85 on 2012-11-13
> **dannyboy79 said:**
> in that case I would suggest just locking the screen within your screensaver settings. set it to decent amount of time and check the box that says "lock screen" upon screensaver. something like that.

I believe 10.04 is the last supported release that ships with screensavers.  On the newer releases, automatic screen locking can be set in the Brightness and Lock settings.

---

