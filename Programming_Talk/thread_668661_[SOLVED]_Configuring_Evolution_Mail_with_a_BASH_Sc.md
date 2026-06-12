---
title: "[SOLVED] Configuring Evolution Mail with a BASH Script?"
date: 2008-01-15
forum: Programming Talk
---

### Post by oodlesOfmoodles on 2008-01-15
Hey all!

I go to a boarding school that is predominantly windows based. I am the only student to use Ubuntu or( Linux for that matter), besides the two members of the IT department. I have managed to convince my a few of my friends to install Ubuntu, but because of a difficulties involved with configuring certain elements (wireless - the school uses open algorithm MSCHAPV2 security which took a month to figure out), many would-be converts are deterred from using it.

My goal is create a Bash script that configures it all for them. 


I have figured out how to configure the wireless but I was wondering if was possible to configure an Evolution Mail account based upon the username and password variable they supply in the beginning of the script.

Any help with this would be great. Thanks!

---

### Post by oodlesOfmoodles on 2008-01-16
bump?

---

### Post by PaulFr on 2008-01-16
For setting up the account, you should look at **[http://live.gnome.org/Evolution/GConfTools](http://live.gnome.org/Evolution/GConfTools)** - this will allow you to create the gconf settings needed.

For Evolution passwords, please see the answer to **[http://www.go-evolution.org/FAQ#Where_does_Evolution_store_my_data.3F](http://www.go-evolution.org/FAQ#Where_does_Evolution_store_my_data.3F)**. Your script can create the appropriate Evolution file for each user.

---

### Post by oodlesOfmoodles on 2008-01-17
Thanks! I'll look into it.

---

