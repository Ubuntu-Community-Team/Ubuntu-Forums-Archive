---
title: "Hp mini software installation problems - numerous"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by Tonyefc1989 on 2012-05-10
Honestly this is my first go with Linux so any help would be much appreciated!
I installed Ubuntu onto my girlfriends hp mini 210 as she was having problems with win7. 
I used a howtogeek.com guide and installation went well. 
I got it going including the wifi...then I hit problems. 

1) tried to install Skype, I can't find it on the Linux store so went off the site. Programme goes to download but stops just before installation. - help on this as I'm not sure where I'm going wrong would be great!
2) I couldn't get flash player to download at all. I searched the net. Found how to command prompt and enter code through the terminal but I'm going wrong somewhere. 

If anyone has the time to give me some simple new guy steps I could follow it would be much appreciated as Ubuntu looks great so I don't want to have to revert to expensive virus filled windows! 

Thank you.

---

### Post by coffeecat on 2012-05-10
> **Tonyefc1989 said:**
> 
1) tried to install Skype, I can't find it on the Linux store so went off the site.

If you mean Ubuntu Software Centre for Linux store, yes the Skype client is there for installation, at least in Ubuntu 12.04.  Open the Software Centre, search for Skype and you should be offered VOIP and instant messaging client - skype. I think this is what you want, but as I don't use skype myself, perhaps someone else might confirm.

> **Tonyefc1989 said:**
> 2) I couldn't get flash player to download at all.

The easiest way for flash is to search for and install the package "ubuntu-restricted-extras" in the Ubuntu Software Centre. This will give you flash, java, most of the video and audio codecs you'll need as well as Microsoft Core Fonts which are desirable for correct font rendering of some websites. During the installation of restricted extras you'll be prompted to agree to a EULA for the MS fonts.

---

### Post by Tonyefc1989 on 2012-05-10
Thank coffe cat! I'll give that a go when I get home tonight!

---

### Post by mastablasta on 2012-05-10
Skype might be in partner repository (not sure at the moment), which might be disabled by deafult. In software sourcces they can be enabled.
 
if all fails you go to this site:
[http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/)
 
and download Ubuntu 10.4  (32 or 64 bit depending on your OS). then you double click it and it should install.
 
note that Linux skype is missing various features available in windows skype (it's also missing the ads!!!). and don't be fooled by 2.2 version (versions are numbered differently). it will  work both voice and video. and is compatible with win version of skype.

---

### Post by coffeecat on 2012-05-10
> **mastablasta said:**
> Skype might be in partner repository (not sure at the moment), which might be disabled by deafult. In software sourcces they can be enabled.

Yes, it is. Thanks for pointing that out.

@Tonyefc1989, I'd forgotten that I'd enabled the partner repository which explains why I saw skype in Software Centre and you didn't. Apologies for the absent-mindedness. If you can't work out how to enable the partner repo, this is how you do it. From Ubuntu Software Centre Edit menu -> Software Sources -> Other Software Tab -> tick the Canonical Partners box.

---

### Post by Tonyefc1989 on 2012-05-10
Thanks for your help. I found skype. Now a latest issue


Package dependencies could not be resolved. 

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time. 

I just clicked install the one time and waited patiently. 

If you can then anymore help would be great!  

Thank you

---

### Post by coffeecat on 2012-05-10
First - which version of Ubuntu are you running?

Next, close Software Centre if it is open and open a terminal. Ctrl-Alt-T is the keyboard shortcut, but it's easily found in the dash. Run these two commands in the terminal:

```
sudo apt-get update
sudo apt-get install skype
```

After the first command, you will be prompted for your login password. You won't see anything echoed to the screen when you type it in, which is disconcerting if you've not experienced this before, but just keep on typing. It is going in. After the second command, you will either be prompted with a "Do you want to continue [Y/n]?" message, or a dependency error message similar to what you got with Software Centre. If the former, just type y and enter and skype will install. If the latter, highlight the whole of the error message with the mouse, right-click -> copy and then paste the error message into your post.

---

### Post by Tonyefc1989 on 2012-05-11
I'm using 12.0.4 on the windows installer. 

Thanks again I'll give it another go tonight!

---

