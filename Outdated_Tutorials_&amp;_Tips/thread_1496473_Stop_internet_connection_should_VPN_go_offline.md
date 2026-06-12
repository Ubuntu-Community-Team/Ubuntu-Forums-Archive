---
title: "Stop internet connection should VPN go offline"
date: 2010-05-29
forum: Outdated Tutorials &amp; Tips
---

### Post by rock_fredde on 2010-05-29
**DISCLAIMER**
I do NOT guarantee that this will work. Try this on your own risk. You alone are responsible for finding out whether this solution works and is satisfactory for you, and does whatever you may think or hope that it does.

**Guide**
**10 step guide to shutting down the internet connection should you VPN connection die.**

A VPN connection is a way of using the internet anonymously. If you are reading this, chances are you already know what VPN is and what it is used for.

A problem with VPN is that the connection sometimes dies. There are various ways of dealing with this- most of which are based on simply attempting to reconnect as soon as a connection dies. However, during the time that you are unconnected, whatever you are doing on the internet is no longer being done anonymously, and anyone will be able to see and store your REAL IP address. This guide will attempt to describe how to attempt to avoid that leaking of your real IP address by shutting down your internet connection as soon as your VPN connection dies.

1. Set up a working VPN connection. There are other guides for doing this elsewhere. Some providers give you a guide for doing this when you sign up, others dont. Regardless, this is not the purpose of this guide. Google "How to VPN Ubuntu" for instructions.
2. Ubuntu comes with a firewall called UFW. There is a GUI for this firewall called "GUFW. Press Applications>Ubuntu Software Center (or Applications>Add/remove applications) and type GUFW in the search field. Install the program.
3. Connect to your VPN. Make sure the connection is successful and active, alive.
4. Find out your IP ([http://www.whatismyip.com](http://www.whatismyip.com)) OR, even better, find out the whole IP range of your VPN provider. 

What is the difference between using your IP as provided by whatismyip.com and the whole IP range of you VPN provider? The difference is that if you use only the IP provided by whatismyip, all the setup we will do in the next steps will be valid for that IP only (and hence, probably also only that single connection). This means that the next time you connect to your VPN, your single IP as provided by whatismyip may differ from the one you have right now, and you will have to change the setup every time you connect to your VPN. On the other hand, if you have the whole IP range of your VPN provider, you can enter it once when making this setup and it will probably still work for your next connection, and your next, and your next and so on.

5. Go to System>Administration>Firewall Configuration. This is the GUFW program.
6. There are different versions of this program, and the GUI has changed recently in the newer versions. However, you should be able to understand what to do from the next steps regardless.
7. Select Reject on both Incoming and Outgoing, or, for the old GUI, By default Reject.
8. Now comes the fun part. Press Add to add a new rule. Switch to the Advanced tab (dont worry- its not that advanced). We will make two rules here. First, you want to

Allow In Both To (Your IP, that you collected from whatismyip.com, OR, your IP range, that you collected from your VPN provider or a trusted source that knows the IP range of your provider). Leave the rest of the fields blank.

Next, you want to

Allow Out Both From (The same IP again). Leave the rest of the fields blank.

9. Make sure that everything is correct, and try to surf around. You should be able to surf and go about your internet business as usual.
10. Now disconnect you VPN connection. Try to surf again. IMPORTANT: You MUST try to visit pages that you have not visited before, to ensure that your browser doesnt display cached versions of pages you often visit.

**Hopefully, you will have problems surfing. It should be impossible. This is the whole point.** 

We told the firewall to only allow your computer to do stuff on the internet as long as your VPN connection is alive. Should it die, you should no longer be able to connect to the internet, download or upload anything.

A problem here is that, as long as your firewall is Enabled, your computer will be unable to reconnect to the VPN, let alone do anything at all on the internet (since this is what we ordered the firewall to do- forbid any connection unless it goes through the VPN). So in order to get back online you need to disable the firewall. **Again, note that as soon as the firewall is disabled, whatever programs you are running, whatever you are doing with them on the internet- will LEAK you IP.** It is not until you reconnect to your VPN, and then turn the firewall back on, that your real IP will be protected. So, should you VPN connection die, and your firewall block internet access -in order to stay anonymous, you must first turn off all programs that are attempting to connect to the internet, then reconnect to your VPN, then re-enable the firewall.

Some people may wish to specify these rules only for certain ports or programs rather than all access to the internet from/to any port and any program. As you may already have noticed, this is possible. When you add rules, to the right of the field where you enter your IP, there is a blank textfield where you can specify a port that the rule should apply for.

So for example, if you want to make sure that all your browsing is done anonymously, but let all other programs communicate freely, you must specify rules specifically for the port that your browser uses (in most cases, ONE of these ports is port nr 80- however be aware that any number of ports with any id nr can be used). Assuming that we know for sure that our browser only uses port nr 80, this is how we would do it:

1. Specify two new rules (again, using the Advanced tab, but now, you also need to select "Show extended actions". If you do, to the farthest left, you will now get a field where you can specify what rank the rule shall have):

Allow In Both (leave the rest blank)

and

Allow Out Both (leave the rest blank)

2. Specify two port-specific rule, e.g. 

Allow In Both To (Your IP) (80)

and

Allow Out Both From (Your IP) (80)

3. Now, make sure that the last two rules have a HIGHER rank than the other two.

This should mean that the firewall will allow any program to do anything on the internet, except for all programs that communicate on port 80- they need an alive VPN connection in order to use the internet. Hence, should the VPN connection die, all other programs should function fine, and you should be able to reconnect to your VPN provider without having to turn off the firewall.

I hope that you will get this to work. **Again, NOTE that I in no way guarantee that this will work,** even if you succeed in performing all these steps and it seems like they do work. Your real IP may still leak, and it is up to you to decide whether to trust UFW and this solution or not. Everything you do on the internet is your own responsibility, not mine.

---

### Post by rock_fredde on 2010-05-31
double post

---

### Post by K.Mandla on 2010-06-01
Similar threads merged.

---

### Post by rock_fredde on 2010-06-01
Sorry about the double post. I didnt realize that the post needed to be approved by moderators before becoming public!

Anyway people, enjoy your private browsing.

---

### Post by abexs on 2010-12-24
I can't get back online after I enable the firewall.
I followed every step, this is not working ...

---

### Post by landstander on 2012-04-15
**Note:** I can not be completely sure if this will work to keep you 100% safe since testing it is beyond the scope of my current knowledge base and abilities.

I wrote a bash script to check the VPN status and do stuff if the connection is lost. Please feel free to edit this script and use it to your advantage. This script was written and tested on Ubuntu 11.04, but should work on other versions of Ubuntu.

**The script does the following 3 steps:**
(script link at bottom of this post)
**1.)** Starts up a VPN and checks if it is active,
**Note:**
[INDENT]You will need to change the UUID listed on line 15 to match the UUID of your VPN connection. To obtain your VPN connections UUID, manually connect your VPN, make sure its connected, then enter the following on a command line:
nmcli -p con status
The long string of numbers and digits under the title UUID and next to your VPN connection name is the UUID of your VPN connection. Use this number to replace the one on line 15 of the script.
[/INDENT] 
**2.)** If the VPN connection is active it start a program of the users choice 
**Note:** 
[INDENT](You choose a program by replacing line 21 where it states:
"myprogram01 &" 
with a program of your choice such as 
"qbittorrent &" 
or whatever program you want the script to run. Note the "&" symbol is necessary for the script to keep running after starting your program)
[/INDENT]
**3.)** Continuously checks the VPN state. If the connection is broken then it pauses the program chosen by the user in step 2 above, reconnects the VPN, then restarts the program chosen by the user in step 2 above, if the VPN connection is not broken then it just keeps checking the status of the VPN connection.

**To run the script:**
After you name and save it to a location of your choice (see: final note of this post below), you must:
**1.)** Make it executable by right clicking on the script file and selecting "properties" -> "permissions" -> then place a check mark in the check-box labelled "Execute [x] Allow executing file as program", then close the properties window. 
**2.)** At this point you can optionally create a launcher icon for it from the main menu by:
**2.a)** selecting "system" -> "preferences" -> "main menu". 
**2.b)** From here, select "Internet" from the list of Menus in the left hand pain. 
**2.c)** Then select "new item" on the upper right, and fill in the following:
[INDENT]**Type:** Application in Terminal
**Name:** VPN and application monitor
**Command:** the name of the file and location where you saved the script
(Example: in my case the command is "~/Archives/OS.Scripts.Bash/vpn1.sh")
[/INDENT]
**3.)** Optionally you can select an icon for the launcher by clicking on the icon. (either create one, choose one from some source, or download one)
**4.)** Then close this window, and go to the main menu -> "internet" -> "VPN and application monitor" to start the script.
**5.)** Alternatively you could just run it from the command line, but I like having the icon to click on.

**Caveats:** 
To shut down the script, you'll have to do the following in this order:
**1.)** Manually shut down the application you chose to run (See: the note for Step 2. in the section above titled "I wrote a bash script that does the following:") 
**2.)** Then use CTRL+C to exit the script in the terminal window.
**3.)** Then manually disconnect your VPN.

**Notes:** The script waits 5 seconds after the connection is established before it starts the application chosen by the user, there is another 5 second delay between connection attempts so the script isn't blasting the VPN with connection requests. So please be patient if you choose to use this script.

There are also a few other programs and things you can do to make your VPN a little more secure depending on how paranoid you are. You can read about them here:
[http://torrentfreak.com/how-to-make-vpns-even-more-secure-120419/](http://torrentfreak.com/how-to-make-vpns-even-more-secure-120419/)

Script Link (See the last post on this thread):
[http://ubuntuforums.org/showthread.php?t=1941380&page=2](http://ubuntuforums.org/showthread.php?t=1941380&page=2)

**Note:** Just copy the contents of the code window and save it to a file called "vpn.sh" or whatever you want to call it noting that the extension ".sh" is important for the OS to recognise this file as a bash script.

I hope this was helpful and if not, then at least somewhat informative.

---

### Post by Bufeu on 2012-11-13
Thanks!

---

### Post by abexman on 2013-01-05
> **landstander said:**
> 
I wrote a bash script to check the VPN status and do stuff if the connection is lost. Please feel free to edit this script and use it to your advantage. This script was written and tested on Ubuntu 11.04, but should work on other versions of Ubuntu.


Mine works, BUT....
It seems when I leave my computer overnight, and it goes into suspend mode, and then I wake it up - it seems that my VPN connection switches back to a standard non-VPN connection and the GUFW/UFW turns off. Would this script or some other setting prevent this?

Im a little concerned I will forget to turn the VPN/firewall back on.

---

### Post by CVGH on 2013-05-10
Was looking around to see if this was possible and I found this thread.
Using Gufw, this method does nothing....
What am doing wrong?

Sorry for the thread "necromancy"....

---

### Post by Nasair on 2013-07-01
bump...I don't want to use the bash script mentioned here but I tried using the Firewall in the first post and a few others. I don't understand why all traffic is blocked. Anyone else have a simple solution to using a firewall? I'm trying this in Lubuntu 12.04.

---

### Post by rsmith317in on 2013-11-30
In case anyone finds this, you might look at ipcheck:

[http://code.google.com/p/ipcheck/source/browse/ipcheck.sh](http://code.google.com/p/ipcheck/source/browse/ipcheck.sh)

I wrote it for a CentOS system but it wouldn't take much to adapt it to Debian and it's children. A friend of mine just convinced me to put it up on Google Code, so I'll probably add more features to it as time goes on since it supports SVN. Feedback is welcome.

---

### Post by Derek_Foulk on 2014-07-10
Yeah, I attempted this to the "T" and it just kept me from accessing anything online. I guess I am misunderstanding the "Allow In Both To" and the "Allow Out Both From". Either that or there are some instructions missing. This post is a few years old now, so I am assuming the GUI of the firewall config app has changed, thus shorthand instructions do not work. Can anybody give insight into how to do this with the current version of the firewall config interface?

---

### Post by coffeecat on 2014-07-10
Moved to Outdated Tutorials & Tips since the OP hasn't logged in for nearly three years and the posting guidelines require that tutorials are supported.

@Derek_Foulk, I suggest starting a new thread in a support area of the forum if you need help. You are more likely to attract attention with a fresh thread than with an old, abandoned tutorial.

---

