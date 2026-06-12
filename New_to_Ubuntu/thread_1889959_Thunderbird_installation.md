---
title: "Thunderbird installation"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by flyfishingphil on 2011-12-02
Tis a wise man that seeks assistance when needed.

Notice I said wise, not smart!

In looking for a way to get my email from my site provider and have it available at desktop so it takes up less space at the site. I have looked at several email programs and, based on ratings, decided to try Thunderbird. My hopes for this are to be able to "download" the email and remove it from the site email address at the same time.

Went to Software Center, downloaded, installed following instructions, and set it up. Tried to do a mail check and get this message:
[B][I][U]
Unable to locate mail spool file.[/U][/I][/B]

What is wrong with this picture and how do I correct it to operational. Please keep in mind that I need instructions like:

Applications > Accessories > Terminal > Sudo

so I can follow them.

Searched lots of areas for "mail spool" but found nothing of assistance. Any help greatly appreciated.

flyfishingphil

---

### Post by BC59 on 2011-12-02
The problem with Thunderbird is that is trying to "help" you and is assuming your email provider address SMTP, ports, security configuration etc.

Usually it's not working so you have to do it manually.

You need some data from your provider.

You have to know if the service is POP or IMAP. Should be IMAP to have the ability to communicate with the server, and download (move not copy) the messages.

So when you have all this data, introduce them manually to configure the connection.

---

### Post by flyfishingphil on 2011-12-02
Did the checking and have everything entered, I think, as it should be.

POP3-outgoing. SMTP-incoming. Entered user name they require. Entered Ports required. Set security as required. Put in password as required. Still getting the "Unable to locate mail spool file" notice when trying to get email.

Tried unistalling, shut down, restart and reinstall but it came up with all of the info I had already entered. It appears that uninstall, using Synaptic, doesn't actually uninstall and clear out everything. 

Any other suggestions?

---

### Post by Frogs Hair on 2011-12-02
Open the file browser and select Ctrl + H to show hidden folders and remove the .thunderbird folder to remove the old configuration and reinstall from scratch .

---

### Post by BC59 on 2011-12-02
Even if you uninstall Thunderbird, the data of your account are stored on a hidden .thunderbird folder in Home. If you go to Home and hit CTRL+H you can see the hidden folders. 

So if you like to get rid of your account, just delete, or rename if you are not sure the .thunderbird folder.

---

### Post by dave0109 on 2011-12-02
It sounds like an error being reported from the server, that is, when the connection is made and logs in, the POP3 server is trying to locate the file containing your mail and it can't find it.  This could be due to permissions on the server, configuration of the server, or configuration of Thunderbird.

Is the connection to the POP3 server secured with SSL or TLS?

---

### Post by pretty_whistle on 2011-12-02
I saw several people who had trouble with Thunderbird.  I, however, have had no trouble because I downloaded Thunderbird directly from their site and not through the software center.

Perhaps you should consider getting Thunderbird directly from them.

---

### Post by flyfishingphil on 2011-12-02
Followed delete instructions and got rid of it. Reinstalled and found where the problems were. Now working fine.

Another problem developed tho and any assist here would be greatly appreciated.

No longer have the Close, minimize, size select options available at the top of anything I have open. Any suggestions on this? Have no idea what happened.

---

### Post by BC59 on 2011-12-02
> **flyfishingphil said:**
> No longer have the Close, minimize, size select options available at the top of anything I have open. Any suggestions on this? Have no idea what happened.

Install from the Ubuntu Software Center, if you already don't have it, the Advanced Settings. Then Open it and from the left panel choose Shell and at the right change the Arrangement of the buttons on the titlebar.

If this is not working do a Compiz reset:
```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```

sometimes after running you may still have problem and you need to run this command again
```
compiz --replace & disown
```

---

### Post by flyfishingphil on 2011-12-02
[QUOTE=BC59;11507242]Install from the Ubuntu Software Center, if you already don't have it, the Advanced Settings. Then Open it and from the left panel choose Shell and at the right change the Arrangement of the buttons on the titlebar.

Have the Compiz under System/Preferences but don't see anything labeled "shell" in the left panel and don't see anything with Arrangement on the right panel bar.

---

### Post by BC59 on 2011-12-02
OOps! I thought you were using Ubuntu 11.10.

Then for 11.04 which I see you are using:

```
killall gnome-panel
```

then if it's not working

> gconftool-2 --recursive-unset /apps/panel
killall gnome-panel

and if not

> gconftool-2 --recursive-unset /apps/compiz
compiz --replace

---

### Post by flyfishingphil on 2011-12-02
Sudo accepted the first one but not the 2nd or 3rd one on your steps. Apparently errorneous.

---

### Post by BC59 on 2011-12-02
Try to copy and paste the command opening a box with Alt + F2.

---

### Post by flyfishingphil on 2011-12-02
Did that and lost my access to everything on the top bar. No net access or anything Bar is gone. Doing this on my phone. How do I get in and restore my ability to get on line.

Pushed some buttons and managed to open Firefox and get back to here. Now, how do I restore that upper toolbar that has everything listed on it like Firefox, Thunderbird, time, Access tabs for Ubuntu, etc?

---

### Post by BC59 on 2011-12-02
From a terminal CTRL+ALT+T run the command.

```
unity --reset
```

---

### Post by flyfishingphil on 2011-12-02
Had me a little worried there for a bit! Got back most of it now just need to take the time to remember how I went from the side bar to the top bar and get rid of the side bar system.

Noticed somethings missing like Skype.Doesn't show it anywhere as installed, from what I can find.

---

### Post by BC59 on 2011-12-02
You could use this tweak:

[http://ubuntuguide.net/use-classic-menu-in-ubuntu-11-04-unity-launcher](http://ubuntuguide.net/use-classic-menu-in-ubuntu-11-04-unity-launcher)

---

### Post by flyfishingphil on 2011-12-02
Will work on that then figure out how to get stuff like Thunderbird and Skype back available.

Just realized I don't see any access to Ubuntu Accessories so I can get to Sudo and run the Terminal as advised in above.

EDIT: Attempting Unity as above but not getting past the Nautilus portion. Cannot find the .loca/share/applications it refers to.

---

