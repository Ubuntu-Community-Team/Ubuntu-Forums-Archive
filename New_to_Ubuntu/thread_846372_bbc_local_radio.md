---
title: "bbc local radio"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by irishy on 2008-07-01
Thanks for all the help and advice I have had from you all in the past can anyone help me with this I have now studied what many people have said about listening to bbc radio using hardy heron and what is  needed has anyone easy instruction on what I have to do nothing I have tried so far has worked
thanks in anticipation

---

### Post by brian_p on 2008-07-01
> **irishy said:**
> Thanks for all the help and advice I have had from you all in the past can anyone help me with this I have now studied what many people have said about listening to bbc radio using hardy heron and what is  needed has anyone easy instruction on what I have to do nothing I have tried so far has worked
thanks in anticipation

Have you got realplayer installed? All I do is click on the station and select "Listen using stand-alone Real Player".

---

### Post by irishy on 2008-07-02
thanks for your reply I haven't realplayer installed I had been looking at posts saying how difficult it was to install and me being new to ubuntu I'm still waiting for inspiration
thanks

---

### Post by gtdaqua on 2008-07-02
Install the requirements first. Open terminal and type this:


```

sudo apt-get install helix-player mozilla-helix-player

```

Restart Firefox.

Then goto BBC Radio 1/2/3/4 and start listening. If sound doesnt come, then simply choose the "standalone realplayer" option in the listening window. It will open a newtab in firefox where you can listen to it!

Thanks for reminding me of BBC, I am listening to Radio 1 right now!!

Its classic!

---

### Post by munkyboy on 2008-07-02
Or install Screenlets from the repos and with that you'll find a desktop widget that plays BBC Radio.

---

### Post by silkstone on 2008-07-02
The following is taken from one of the tutorials in this forum, and it worked fine for me...

The following steps show how to install Real Player 11 and Mozilla Plugin for Firefox 3.0 browsers running on Hardy Heron.

Download Real Player 11 from:

  [www.real.com](www.real.com)

Open a terminal and change to the directory where the file was downloaded. Grant execute permissions and run the setup using the following commands:

  ```
chmod 770 RealPlayer11GOLD.bin
  sudo ./RealPlayer11GOLD.bin
```
  

Use the following default installation directory during the installation:

  /opt/real/RealPlayer

The installer will copy the files and create menu shortcuts. Then run the following commands.

  ```
cd /usr/lib/firefox-addons/plugins
  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.xpt nphelix.xpt
  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.so nphelix.so
  sudo mv /usr/lib/totem/gstreamer/libtotem-complex-plugin.so ~/.
```

[Note that the old gstreamer plugin is no longer needed, and is moved to your home folder in case you ever want to reinstall it.]

Open Firefox and type...
 ```
about:plugins
```
...in the address bar. Scroll down and look for the following entry.

  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
  File name: /opt/real/RealPlayer/mozilla/nphelix.so
  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.4005 built with gcc 3.4.3 on Feb 25 2008

If found, your Real Plugin is installed properly!

---

### Post by irishy on 2008-07-02
I had studied this info but could not follow it can you help me out please in the following statement
how do I find out where it is downloaded
 then when I am typing in the terminal do I type all displayed and press enter

Open a terminal and change to the directory where the file was downloaded. Grant execute permissions and run the setup using the following commands:

Code:

chmod 770 RealPlayer11GOLD.bin
  sudo ./RealPlayer11GOLD.bin


I really am new to this 
thanks again

---

### Post by irishy on 2008-07-02
> **munkyboy said:**
> Or install Screenlets from the repos and with that you'll find a desktop widget that plays BBC Radio.
sory for being so thick but can you explain how to do what you are asking 
thanks

---

### Post by Xerp on 2008-07-02
+1 for the screenlets! :)

Just install them, thats what Munkyboy means.

[https://help.ubuntu.com/community/SynapticHowto#Adding%20or%20Removing%20Software](https://help.ubuntu.com/community/SynapticHowto#Adding%20or%20Removing%20Software)

---

### Post by silkstone on 2008-07-02
> **irishy said:**
> I had studied this info but could not follow it can you help me out please in the following statement
how do I find out where it is downloaded
 then when I am typing in the terminal do I type all displayed and press enter

Open a terminal and change to the directory where the file was downloaded. Grant execute permissions and run the setup using the following commands:

Code:

chmod 770 RealPlayer11GOLD.bin
  sudo ./RealPlayer11GOLD.bin


I really am new to this 
thanks again

Open a terminal from Applications > Accessories > Terminal

Enter the commands one line at a time, and press Enter after each one. When asked for your password, enter it carefully - it will NOT appear on the screen, and it will look as if nothing is happening when you type it in! That's fine - just type it in and press Enter.

You'll have downloaded the Realplayer installation file to somewhere in your filesystem - wherever you've chosen. You have to navigate to there in the terminal using the cd command. So if you've downloaded it to a folder called Downloads in your home folder, you get there by...

cd /home/YourUserName/Downloads

Hope that helps!

---

