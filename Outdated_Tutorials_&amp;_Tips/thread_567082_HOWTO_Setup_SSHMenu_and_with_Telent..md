---
title: "HOWTO: Setup SSHMenu and with Telent."
date: 2007-10-04
forum: Outdated Tutorials &amp; Tips
---

### Post by GrammatonCleric on 2007-10-04
HOWTO: Setup SSHMenu and with Telent.

[IMG]http://sshmenu.sourceforge.net/images/sshmenu_screenshot.png[/IMG]

After switching my work laptop over to Linux one of the things that I've been looking for  was a Linux SecureCRT replacement.  Yes there is  PUTTY for Linux and sure I could setup gnome panel menus for every switch, router, and Unix server but what a pain. Lucky I'm a Digg junkie and I saw an article for SSHMENU.  While this did answer my need for SSH I still needed telnet.  So I emailed the maintainer of SSHMenu to see what I would need to do to add Telent functionality.  A few days later I recieved and email from Grant McLean with a simple answer....which wasn't no.

**Step 1:  Installing SSHMenu:**

-----------------------------------------------------------------------

Adding SSH repo's to your apt source list.
```

deb http://sshmenu.sourceforge.net/debian stable contrib

```Import the repo key:

```

gpg --keyserver subkeys.pgp.net --recv-keys 4CC00851

```then

```

gpg --export --armor 4CC00851 | sudo apt-key add -

```Now run and update:

```

sudo apt-get update

```Install SSHMenu:

```

sudo apt-get install sshmenu-gnome

```With SSHMenu installed you should now be able to add it to your gnome panel.  


 - Right click in your Gnome Panel and select Add to Panel.
 - Scroll down to Utilities and you should see "SSH Menu Applet."  If you don't log out and back in to X.



**Step 2: Now adding Telnet functionality:**
-----------------------------------------------------------------------

I've attached the file sshmenutelent.rb download it and put it where you want.  Just make sure that your account has read, write and execute to the file.


Now locate your .sshmenu file in the root of your home directory.  With you favorite editor open the .sshmenu file.

```

nano .sshmenu

```Locate classes: and make it look like...

```

classes: 
  app: SSHTelnetMenu::App
  app.dialog.host: SSHTelnetMenu::HostDialog
  app.model.hostitem: SSHTelnetMenu::HostItem
  require: /home/gcleric/Documents/Scripts/Ruby/sshmenutelnet.rb


```Of could change the require location to the place where you put the sshmenutelnet.rb file.

Now when you add a new host you should see an added check box that you can select to use telent instead of SSH (see image sshmenutelnet.png).




*[COLOR=Red] One final note.  If found that adding more than a few hosts at a time via the GUI casues that app to have stability issues.   I would recommend adding a couple of hosts and then edit the .sshmenu file directly.[/COLOR]*

---

### Post by k.sangeeth on 2009-10-10
Thanks a lot this info.
I looking for something exactly like this.

---

### Post by lucotuslim on 2009-11-17
Hi, I installed sshmenu-gnome and sshmenu, all seems fine except that whenever I run the ssh, it always set the user as current user I am running. 

Can I change to other user ? 
For e.g I am log in as usera but when I run sshmenu, I want it to be userb.

---

### Post by GrammatonCleric on 2009-11-19
In the "Hostname (etc)" field just add the user name you want to ssh into the host as... 

```

change:  

chu.com

TO:

foo@chu.com


```-GC

---

### Post by lucotuslim on 2009-11-25
Thanks,this really save me from a lot of typing.

---

