---
title: "Unlock your keyring"
date: 2015-02-01
forum: New to Ubuntu
---

### Post by bodhi3 on 2015-02-01
I got service through IPVanish set up a PPTP vpn connection and when it connects now, it throws a unlock keyring. Although it give a slightly odd message saying "The password you use to log in to you computer no longer matches that of your login keyring." Well I never changed it and when I go into passwords and keys to change it I am not allowed because I dont know what(or why) the password for my keyring was changed to. I am sure there is a way to forceably change it from with in the terminal, but I just cannot find it as I am not quite sure what to search for. Any and all help is greatly appreciated!

***edit***
The VPN connection works just fine, although I had to disconnect it to log in to ubuntuforums.com.



Bodhi

---

### Post by whitesmith on 2015-02-01
This question seems like it should be directed to your ISP, unless you can tell us how Ubuntu software is involved in the issue.

---

### Post by ian-weisser on 2015-02-02
Change your keyring password to something you *do* know.
See [http://askubuntu.com/questions/65281/how-to-recover-reset-forgotten-gnome-keyring-password](http://askubuntu.com/questions/65281/how-to-recover-reset-forgotten-gnome-keyring-password)

Yes, it involves few shell commands. Sorry, no way around it.

---

### Post by bodhi3 on 2015-02-04
I should have been more specific I was looking for the shell commands! Thank you very much!

***edit***
I seem to have deleted my login keyring as it no longer appears in seahorse. I imagine I will have to delete the Gmone 2 KeyStorage as well since that password was changed as well. Any ideas on what will happen if I delete and start again?

---

