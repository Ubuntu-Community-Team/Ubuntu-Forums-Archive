---
title: "login failure fixed but not blank screen"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by markbuntu on 2008-04-29
I just installed 8.04 on its own 350gb sata hard drive on my HP PC. I just plugged the new drive into port 1 and put the windows drive in port 2 and booted from the cd which I downloaded and burned and sumchecked after the burn and then checked it again at install.

That all went fine but it would not recognize my login or psswd and would restart and when I did it again and then it would tell me the password or login were incorrect and if I put them in again it would recycle back to the login screen. 

I could get gnome up in safe mode and found in the auth log that /lib/security/pam_smbpass.so was missing so I guess pam was having a little problem. I found the file with Synaptic and installed it and now it accepts the login and password and then gives me a blank screen.

I can still get into Gnome in safe mode and so would like to fix it from there if I can. I don't believe I am having any hardware problems it seems to recognize everything and it all seems to work OK so far.

The last Linux I installed was 1.02 or something about a century ago so I could really use a clue here about where to go next.

---

