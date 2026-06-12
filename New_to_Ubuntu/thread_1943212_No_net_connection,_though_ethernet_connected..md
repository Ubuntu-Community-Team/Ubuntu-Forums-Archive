---
title: "No net connection, though ethernet connected."
date: 2012-03-19
forum: New to Ubuntu
---

### Post by mishasibirsk on 2012-03-19
Installed via Wubi. Though information from button in top R corner of desktop shows wired connection connected, firefox says: firefox is unable to locate server at start.ubuntu.com. Substituted google.com, firefox says same thing, but for google. Tried other browsers in the list; no go. firefox works OK in Windows. I notice that similarish posts largely go unanswered, but decided to give it a go anyway. Any suggestions? "Give up on Linux" looks like the obvious one.

---

### Post by Frogs Hair on 2012-03-19
Hello and Welcome

Open system settings > network  and make sure the wired connection is on .  Enter configure and see if the connection is automatic . Some people have had to ignore or enable IPV 6. You may also get a dialog box with an option to add a connection.

---

### Post by malsha on 2012-03-19
I am leaning towards the same conclusion Malsharibrisk. Having the same issue but this didn't start until I changed the settings in the 'login screen' (Configure login screen behavior)located in System>Administration. In the Login screen Settings dialog box it won't unlock so I can come out of "Failsafe GNOME (this session logs you into GNOME without user applications). The 'unlock' won't unlock so the box stays greyed out. This operating system is for programers who know what they are doing, not for you and I who are very limited in knowledge about all the computer jargon people speak here. I only am using this OP because MS doesn't read damaged HD. Linux finds a readable area and runs from there with MS I'll have to buy a new hard drive and start from scratch. Hope we get this solved and soon.

---

### Post by tbhatia4 on 2012-03-19
> **mishasibirsk said:**
> Installed via Wubi. Though information from button in top R corner of desktop shows wired connection connected, firefox says: firefox is unable to locate server at start.ubuntu.com. Substituted google.com, firefox says same thing, but for google. Tried other browsers in the list; no go. firefox works OK in Windows. I notice that similarish posts largely go unanswered, but decided to give it a go anyway. Any suggestions? "Give up on Linux" looks like the obvious one.

mention your ubuntu version

if you are connected to internet then just run update manager and check whether your system is up to date or not 

if not update that first 

then reboot and uninstall chrome from synaptic package manager
mark that for complete removal
then reinstall chrome

post here if that works

---

### Post by malsha on 2012-03-19
HEY DON'T GIVE UP YET! 
I got some info from another forum thread that lead me to go search googlebuntu.com (which I didn't know existed) I typed in 'how to unlock failsafe GNOME' (this mode messed up my ability to access the internet). From the list I chose '[[SOLVED] disable **Failsafe Gnome** and/or **unlock** login preference **...**]("http://www.google.com/url?q=http://ubuntuforums.org/showthread.php%3Ft%3D1527773&sa=U&ei=GGVnT8eWMfHisQL_p-G2Dw&ved=0CAQQFjAA&client=internal-uds-cse&usg=AFQjCNH46byffCjdq8a5MCW1XScu2-5udw") I followed thread #10 and Problem solved! Now my internet icon is back and it's automatically looking for wireless signal as before....if you only know how happy I am right now. Hope this helps you too.
Best wishes

---

### Post by mishasibirsk on 2012-03-20
Thanks, rebyata. There are some useful-looking ideas in there, albeit nemnozhko recondite pour moi. I will have to log out of Windows to try them, so I will print out the page first, which will require addressing that pile of books on top of the printer. I might also try installing on the old computer, which runs xp. Call me a conspiracy theorist, but I am inclined to think that among those updates I get for Windows 7 there might be the odd trip-wire to derail any attempt to break out of the cattle-yand. It is unfortunate that their is no half-way house to Linux. There are the cognoscenti, with the handshake and the ear-waggle, and then there are the plebs. But I will persevere, if not immediately. The capture of the "democratic"/"anarchistic" internet, by Microsoft, and also Google, has happened so fast that no-one's had time to get out of bed. One thing I will say for Microsoft: they have caught up with Apple in terms of reliability. If I think back to Internet half-hours on the radio of the early-mid nineties, the basic connection and system problems people were having were similar to Linux forums of today. If I were prepared to be funnelled through their advertising, their preferences, their defaults, Windows-land would be a kind of existence, but it's not citizenship you can have there, but "poddanstvo."

---

