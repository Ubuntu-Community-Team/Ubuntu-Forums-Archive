---
title: "My first bash script-check my work and make a suggestion please"
date: 2017-04-13
forum: New to Ubuntu
---

### Post by nojimon on 2017-04-13
Hi all
I'm a noob at terminal, linux and bash scripting. I have no programing language knowledge either-keep it simple please.
I'm reading two books on the subject so i have limited knowledge. Please assume i require an explanation with context and examples, even if it seems blatantly obvious I'm using nano, I know how to modify permissions on my script when its finished and how to run it but i don't know how to supply the passwords and usernames automatically in a couple of lines of code. thats where i need ur help and suggestions. heres my work so far 

VPNSCRIPT
#change to directory with my ipvanish config files 
cd vpn/

#run command that starts the vpn service connection
sudo openvpn --config ipvanish-SG-Singapore-sin-a01.ovpn

#sudo password prompt
how can i automate entry here?

#vpn username prompt 
how can i automate entry here?

#vpn password prompt 
how can i automate entry here?


I know its a security risk but i am not super concerned. your thoughts guys thank in advance.

---

### Post by TheFu on 2017-04-13
a) please use "code tags" when posting code. We are used to those fonts and prefer the look.
b) don't use relative paths. This will prevent the script from running if ever run from a different account or different directory. Fully specify all paths for **cd** and all programs. /usr/sbin/openvpn is probably what you want, for example.
c) using sudo _inside_ a script is poor form.  Run the entire script under it or from an the root account. This would be a **sudo /path/to/script** example.
d) You are missing the required, 1st, line.  #!/bin/sh (or whatever interpreter you want) That is important.  This is now the interpreter is selected - bash, sh, zsh, perl, python, whatever ... 

Google - "ABSG bash" to find the "advanced bash scripting guide".  Lots of examples.  If you want to get input, use 'read'. It is a bash built-in. You can look up what that means in the guide.

However, you can place vpn credentials into a file and use those directly.  Just lock down the file to 400 permissions for root only. login.cf is the usual file for that from my openvpn knowledge. This is how I do it, BTW.

---

