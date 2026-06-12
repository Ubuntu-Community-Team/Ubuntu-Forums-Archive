---
title: "HOWTO: Get gmail notifier working in a hurry."
date: 2006-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by anasofiapaixao on 2006-08-04
**NOTE:** Altough some bits were figured out by me (last part about evolution, hehe), I am just transforming [this thread]("http://www.ubuntuforums.org/showthread.php?t=68744") into an HOWTO in order to get things more organized and accessible... all credit for its contents should go to the people there ;)

This HOWTO intends to help out people having trouble with the Gmail notifier (which, as you probably know already, has currenly a bug which makes you unable to enter your login information, printing out the "Login appears to be invalid" message).

So, open a terminal (Applications-- Accessories-- Terminal) and copy-paste this bunch of commands:

```
sudo apt-get install gmail-notify
wget http://switch.dl.sourceforge.net/sourceforge/gmail-notify/gmail-notify-1.6.1.tar.gz 
tar -xzvf gmail-notify-1.6.1.tar.gz gmail-notify
sudo mv /usr/lib/gmail-notify/ /usr/lib/gmail-notify.old
sudo mv gmail-notify/ /usr/lib/gmail-notify
rm gmail-notify-1.6.1.tar.gz
sudo gedit /usr/lib/gmail-notify/GmailConfig.py
```
On the text file you just opened, look for this bit of code, it should be on the beginning of the file:
```
# Declare global variables for configuration as dictionary
	options = { "gmailusername":None, "gmailpassword":None, "browserpath":"firefox", "lang":"English",   
				"voffset":0, "hoffset":0, "checkinterval":20000, 
				"animationdelay":15, "popuptimespan":5000}
```
And replace:
- In "gmailusername", None for your Gmail login (***_with quotation marks_***);
- In "password", same thing but with your pass (duh :P).

Then save and exit.

Now go to System-- Preferences-- Sessions, then to the third tab "Startup Apps" (or something like that), click the "Add" button and type "gmail-notify" (**without** quotes).

Et voilá!


(**NOTE:** If you want to use your e-mail client instead of the web browser, on the above text file replace "firefox" with e.g. "evolution" or "thunderbird" or whatever you use, save and exit and type this last command line:

sudo gedit /usr/lib/gmail-notify/notifier.py

Use the search button and look for [http://gmail.google.com](http://gmail.google.com). You're likely to find this piece of code:

```
print "launching browser "+self.options['browserpath']+" http://gmail.google.com"
		os.system(self.options['browserpath']+" http://gmail.google.com &")
```

Just replace with this:

```
print "launching browser "+self.options['browserpath']#+" http://gmail.google.com"
		os.system(self.options['browserpath']#+" http://gmail.google.com &"
)
```

Then save and exit.

**EDIT:** This HOWTO was tested on a (almost) fresh Dapper install, everything is working.

---

