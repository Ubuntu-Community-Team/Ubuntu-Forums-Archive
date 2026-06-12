---
title: "How do I save a service file in 20.04?"
date: 2020-10-21
forum: New to Ubuntu
---

### Post by wmrp on 2020-10-21
I am supposed to save a service file that I entered in the Terminal, but I have no idea how to do this. Would anyone please be so kind as to let me know? Thank you!

---

### Post by ajgreeny on 2020-10-21
We need to know much more if we are to help you.

Did you create a file using a terminal text editor such as nano?
If not, what is this service file you're asking about; where did it come from and how do you know it needs saving?

---

### Post by wmrp on 2020-10-21
It is a service file I was directed to enter in the Terminal by protonvpn tech support to set up autoconnect.

"Afterward, save the service file with this information contained in it:
[Unit]
Description=ProtonVPN-CLI auto-connect
Wants=network-online.target

[Service]
Type=forking
ExecStart=/usr/local/bin/protonvpn connect -f
Environment=PVPN_WAIT=300
Environment=PVPN_DEBUG=1
Environment=SUDO_USER=wim

[Install]
WantedBy=multi-user.targetAfter saving this file, enter the following commands in a new Terminal window **(after saving and closing the Auto-Connect service file)**:........"

My question is: how does one save such a file? Since I am new to Linux I just have no idea. Internet search, nor terminal itself give me any clue. So I was hoping someone here would brief me.

---

### Post by ajgreeny on 2020-10-21
Well, I know nothing about VPNs but this sounds as if it's a text configuration file that you could create in any text editor.

However, config files must be saved to a specific location in the filesystem if they're to do whaat they should, and without that knowledge I can't help you any more.
Was there any information telling you where it should be saved or created?

---

### Post by TheFu on 2020-10-21
Use **sudoedit /path/to/location/required**.  sudoedit was created to be a safe method to edit system files. By default, it uses nano as the editor, but you can configure any editor that you like by using the EDITOR= environment variable.  gedit looks much like notepad, but is very powerful with lots of options. Same for Kate.  Old timers like me would use vi or vim, but if you don't know those and don't want to be a Linux admin, probably best to use gedit or nano.

Or you can copy paste from stdin through a tool with elevated permissions to the output file location. This is one of those techniques that are hard to describe, but easy to accomplish.

---

### Post by ActionParsnip on 2020-10-22
Or:
```

sudo vi /path/to/filename 

```

---

### Post by wmrp on 2020-10-22
Sorry, but none of this is helping. I was pretty sure I posted my inquiry in the "New to Ubuntu" category...

Following the instructions posted above there is this:  After entering these commands in your protonvpn-autoconnect.service file, press **CTRL+X -> Y -> Enter -> ****Enter&#8203;**
 
That should lead one to the option to save the file, but to me it is too ambiguous as to how to enter the line correctly. 
Really feel like giving up (been with this also some months ago, on an off for weeks on end, trying in vain to accomplish the same set up, and picking it up again now with the same frustrating result).
I have 3 computers of family members that all need this set up, but it so far it is beyond me. 
Sorry for the rant!

---

### Post by TheFu on 2020-10-22
Perhaps protonvpn tech support can provide clearer details to help you?  
For the information provided, we can only guess at answers which are just as likely to cause problems as to make stuff work.  I use a few VPNs, but not the same that you use. Also, I don't have it setup like this.  I have to manually enable/disable the VPN.

Learning any new OS can be frustrating. Time, experience and practice are the solution.

---

### Post by ActionParsnip on 2020-10-22
Do you have a link to the guide you are using please?

---

### Post by SeijiSensei on 2020-10-22
Sounds like you're using nano.  When you're done editing, hit Ctrl+X, then follow the prompts to save the file and exit the editor.

I'm hardly an expert when it comes to systemd, but it's likely the file you created goes in /etc/systemd/system/multi-user.target.wants/.  You'll need to use sudo to copy it there.  You'll also need to use the command "sudo systemctl enable servicename" to tell the system to launch the program at boot. Replace "servicename" with the corresponding name of the program, e.g, "apache2" tells the system to use the apache2.service file to manage the apache2 web server.

---

### Post by wmrp on 2020-10-25
I was able to get it set up. Thank you all for the suggestions!

---

### Post by ajgreeny on 2020-10-25
Great!

Having gone round in circles with this problem for quite some time, please now tell us what the solution turned out to be.

Please also mark the thread as SOLVED from Thread Tools  up top.

---

