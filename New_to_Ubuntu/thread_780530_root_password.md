---
title: "root password"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by wordmaster on 2008-05-03
I have downloaded the java plugin for firefox and I am told I have to go to the root by typing su to set it up.

When I type su, it asks for root password. I try the log in password and it does not work.

How do I get there from here?

Please forgive all the questions. I am a newbie trying to get my new install all set up and working. Thank you.

---

### Post by SunnyRabbiera on 2008-05-03
for this use the sudo command instead of su.
also you can get java via the repositories.

---

### Post by wordmaster on 2008-05-03
Thank you very much. If I go to the synaptic manager, it shows a bunch of java stuff. Which one do I need for the basic java environment and Firefox plugin? 

Also, when I type sudo, instead of asking for a password I get a list of options to use with sudo. So what do I do from there to load a program? I have used DOS, RS-DOS, and the old OS9 (not Mac) but linux and its commands and command structure are all new to me. Your help is much needed and much appreciated.

---

### Post by SunnyRabbiera on 2008-05-03
Actually if you have instructions telling you to use su use sudo instead, sudo alone wont do anything unless you tell it to, in this case to install java via the method it gives you (su sh install jre-6u5-linux-i586.bin)
you type in **_sudo_** sh jre-6u5-linux-i586.bin
you get me?
if you get any instructions that tell you to use su, substitute it with sudo.

as for the plugin, make sure to remove the openjdk versions first (they really are not needed) and just install the following:
sun-java6-bin
sun-java6-fonts
sun-java6-jre
sun-java6-plugin
those should do it for you.

---

### Post by Hardrive on 2008-05-03
If you ever do need to have the root password, it's easy to set it.  On a user account that has permissions to administer the system, do this:
```

$ sudo passwd
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully

```

* It may ask you for your account's password

---

### Post by Helios38 on 2008-05-03
the function of doing a single cmd with sudo is


```
sudo (command)
```


you will then be prompted for your root password, which is your admin account pass you use when you installed.

---

### Post by SunnyRabbiera on 2008-05-03
right, but honestly sudo will suit you, its usually just better to substitute su with sudo when it is taught to you in instructions.
that way you dont mess up your system by mistake or anything :D

---

### Post by wordmaster on 2008-05-04
Thank you all for your help. I understand much more now than I did. However, I still don't have java functionality in firefox. I got it to unzip, then I went through what as near as I could tell copied java files to the firefox plugin directory....not real sure, but I think that is what it did. I followed the instructions on the java plugin page.

Now if I go to preferences, enable java and enable javascript are checked, but when I go to a game that requires java, it says java not installed do you want to insall the plugin now?

Any ideas on what i need to do next to get it to actually work? I am trying to use it on pogo.com. Thank you for any help.

---

### Post by sailor2001 on 2008-05-04
did you install 'java-common' ?

---

### Post by wordmaster on 2008-05-04
I downloaded and installed jre-6u5-linux-i586.bin from the Sun site.

---

### Post by forrestcupp on 2008-05-04
You need to install it from the repositories.  Just open a terminal and type
```
sudo apt-get install sun-java6-plugin
```and it will install everything you need for Java to work in your browser.

**Always** check and see if you can install things from the repos before you go downloading files to install.

---

### Post by wordmaster on 2008-05-05
> **forrestcupp said:**
> You need to install it from the repositories.  Just open a terminal and type
```
sudo apt-get install sun-java6-plugin
```and it will install everything you need for Java to work in your browser.

**Always** check and see if you can install things from the repos before you go downloading files to install.

I used the code you gave and it appeared to work great. Everything appeared to complete as it should. However, when I go to Pogo, I still get an error asking would I like to install the Java plugin as it is not installed.

What have I done wrong?

---

### Post by SunnyRabbiera on 2008-05-05
> **wordmaster said:**
> I used the code you gave and it appeared to work great. Everything appeared to complete as it should. However, when I go to Pogo, I still get an error asking would I like to install the Java plugin as it is not installed.

What have I done wrong?

well you may need more plugins... but there might be the fact that Pogo might not work here.
sometimes sites detect what operating system you are on and simply wont allow you to do anything on them unless you use windows XP or something.
I cannot confirm or dent pogo works in linux, I can give it a shot as I installed many plugins and I can also try browser spoofing too.

---

### Post by wordmaster on 2008-05-06
If you would try that I would appreciate it. A few of the games there are rather difficult to get to work without IE, but most work fine with Mozilla or Firefox in 98 and 2000. 

The simple slot games, such as Showbiz Slots have run on whatever I have tried as long as Java was installed. When I try it now, I get the same thing I get in Windoze without java. The error says:

Pogo.com games use the Java plug-in. You either do not have Java installed or you have a version that is incompatible with our games. It does not cost you anything to install Java.
Do you want to install the Java plug-in now?


I would like to change my wife's machine to Ubuntu, but she plays the games here on a regular basis and the change would not work if she were unable to use this site.

Thank you for any help you can give.

---

### Post by wordmaster on 2008-05-07
bump

---

### Post by mister_pink on 2008-05-07
I just tried to play a random game on there and it worked fine. I'd guess the problem is that the version you installed from the sun site and the repo one are interfering with eachother. 

I'd uninstall the one from the repo, and try and find some uninstall instructions for the other one. Once youve got rid of both, reinstall the repo one.

As for sudo vs su, the difference is you type "su" to change to the user "root" (the system admin) temporarily to change things. Ubuntu does away with this in favour of a different security model, sudo, which rather than using on its own you place before the command you want to run as root. The sudo equivalent of su is probably running "sudo -i". See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by wordmaster on 2008-05-08
Mister_pink, thank you for the information on su and sudo. It helps me understand.

Thank you also for your remommendation to uninstall and reinstall. However, please remember that I am nothing more than a rank amateur, a total newbie in the fascinating world of linux and ubuntu.

Would you please take the time to give me exact instructions on how to go about finding and uninstalling all these things? At this point in my dealings with Ubuntu, that is the only way I can proceed. I do not yet have enough understanding of the basics to figure it out for myself.

---

### Post by alzie on 2008-05-10
I was having issues with pogo not working.  In my case I needed to install ubuntu-restricted-extras from synaptic and now I've got pogo back.

I hope this helps you.

---

### Post by wordmaster on 2008-05-11
Could you please tell me what those extras were and just how to get and install them? Thank you.

---

### Post by spiderbatdad on 2008-05-11
```
sudo apt-get install ubuntu-restricted-extras
```

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

