---
title: "HOWTO: Install Mental Ray satellite rendering for Autodesk Maya"
date: 2009-03-31
forum: Outdated Tutorials &amp; Tips
---

### Post by acy76 on 2009-03-31
This has been completed successfully on two Ubuntu 8.10 x64 desktop installations; I have also successfully tested it under Xubuntu x64. I assume it would also work for 32-bit varieties but have not tested it.

*[COLOR="DarkOrange"]** As always, be careful when installing software from outside Ubuntu's repositories. It's only advisable to do so from sources you trust, or you may compromise your system.[/COLOR]*
[B]
1) Obtain Mental Ray Satellite software from Autodesk:[/B]

[http://usa.autodesk.com/adsk/servlet/ps/dl/index?siteID=123112&id=2334435&linkID=9242259#section2]("http://usa.autodesk.com/adsk/servlet/ps/dl/index?siteID=123112&id=2334435&linkID=9242259#section2")

Select the version of Maya you own and there should be the latest update to Mental Ray Satellite listed on its page.

Update your Maya installation at this time if you have not already done so - it seems that the satellite and Maya need to have the same version of the rendering engine installed or Maya will complain and not render over the network.

Choose the appropriate version for your OS (i.e. 32- or 64-bit).
Note that the number of satellite rendering machines you may use is dependent on your Maya license (2 for Complete, 8 for Unltd.)

**2) Decompress archive: **

Mental Ray Satellite comes as a .tgz compressed file -- double-click it to open it in the archive manager and drag the .rpm file into your home folder (or another convenient location).

**3) Open terminal:**

Assuming you've got the file in your home folder, open the terminal (Applications -> Accessories -> Terminal); you will be in your home folder by default.

**4) Install xinetd to manage the satellite renderer:**

```
sudo apt-get install xinetd
```

**4.1) Install the csh shell:**

```
sudo apt-get install csh
```

[COLOR="Red"]** EDIT: If you followed the first version of the guide, the host maya installation would report that it could not receive a welcome message from the satellite. This seems to fix the issue, after much trial and error. **[/COLOR]

**5) Install rpm:**

Mental Ray is an .rpm file, which is not natively supported by Debian/Ubuntu. Install rpm to overcome this (alternatively, you can use alien to convert to a .deb first; although this is more work, it will install successfully):

```
sudo apt-get install rpm
```

**  Also, if you make a mistake and try to install the .rpm prior to altering the shell in step 6, the install will fail and subsequent attempts will result in a message that the software is already installed (which it is not). In this case, be sure to change the shell first (obviously) and then use alien to convert the .rpm to a .deb and dpkg to install the .deb

**6) Change default shell:**

This is the big hang-up: the install script expects a bash shell, and Debian/Ubuntu uses dash by default. You will need to change the symbolic link 'sh' from 'dash' to 'bash' in order for the package to install (don't worry, we will change it back afterward):

```
sudo ln -s /bin/bash /bin/sh --force
```

**7) Install the Mental Ray .rpm:**

Note that the filename used here is current for Maya 2008 at the time of writing; modify as necessary.

```
sudo rpm -ivh --nodeps mentalraySatellite3.6.51_Maya2008_linux64.rpm
```

**8.) Change the symlink to get the old shell back:**

```
sudo ln -s /bin/dash /bin/sh --force
```

**9) Verification:**

At this point, Mental Ray should be working. We can verify the installation to be sure -- first check to see whether it is listed in /etc/services as listening on the correct port:

```
cat /etc/services
```

The last entry in the list should appear as follows, under "Local services":

```
mi-raysat3651    7108/tcp    # mental ray for Maya network rendering
```

If you need to change the default port, use the nano editor:

```
sudo nano /etc/services
```

Search (CTRL+W) for string "mi-" to find it quickly (edit only if necessary, defaults should work unless your Maya installation expects a different port due to changes made to deal with firewalls etc.).

**10) Install chkconfig to monitor/query xinetd:**

This allows us to check the status of the rendering daemon.

```
sudo apt-get install chkconfig
```

**11) Check the status of the daemon:**

```
chkconfig --list mi-raysat3651
```

It should be listed as follows:

```
xinetd based services:
        mi-raysat3651:      on
```

**12) Configure Maya:**

Configure your Maya installation to use the new machines as satellites. This varies by OS -- check this old guide for some hints if you are unsure how to proceed:

[http://www.lamrug.org/presentations/oct2004/mental_ray_for_maya_render_farm_.htm]("http://www.lamrug.org/presentations/oct2004/mental_ray_for_maya_render_farm_.htm")

[COLOR="RoyalBlue"]And that's it. Once a render is started by the master, the process should launch automatically on the satellite machines. You can use the 'top' command in the terminal to watch the 'raysat' process start and climb to max CPU use. It often takes a couple of minutes to get the satellites up to full speed, so be a little patient - the process should appear immediately and ramp up to full CPU usage, but will not always remain at 100%.

I should also add that there is a very helpful 'readme' included with the installation of Mental Ray. It is located here (change directory name as necessary to agree with installed version):

```
/usr/autodesk/mentalraysat3651-x64/readme_mr_sat.txt
```

It is also worth noting that during troubleshooting, if your host Maya installation cannot connect to the satellites, it will give up and not try again until Maya is restarted. So, if you're tweaking things on the satellite side, be sure to restart Maya each time.

Happy rendering.[/COLOR]

---

### Post by tempo500 on 2009-04-18
thanks allot for this!!!! its finally up and running! hurray! after 2 years.... thanks phil

---

### Post by bambanx on 2010-03-29
my installation of satellite is good i have on two pc with ubuntu , but cant config this, pls send me a tutorial or link .
thx

---

### Post by acy76 on 2010-04-01
You'll have to be more specific as to the problems you're having. 

Everything I learned installing the satellites under Ubuntu is included in the guide, so be sure you're following it carefully.

---

