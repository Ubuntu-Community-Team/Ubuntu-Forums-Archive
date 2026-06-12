---
title: "Help!! Can't Login!!!"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by lastelement0 on 2008-06-02
hi all i have hardy installed on my dell inspiron e1505. i just finished the fix in order to get usb devices to work within virtualbox.  however following my necessary restart, and login with my username and password it just hangs following pressing enter to finish the login.  it's not like it froze either because i can still click sessions and actions on the login screen and those actions take.  however nothign is being done in regards to my login attempt. any help is appreciated!

---

### Post by sayakb on 2008-06-02
Try accessing the Failsafe mode sessions from the available sessions.

---

### Post by lastelement0 on 2008-06-02
i tried those but nothing seems to happen when i select them

---

### Post by sayakb on 2008-06-02
Does Ctrl+Alt+1(to 6) take you to tty1(to 6)? If yes, try adding a new user from the tty. Read here:
[http://www.cyberciti.biz/faq/howto-linux-add-user-use-adduser-command/](http://www.cyberciti.biz/faq/howto-linux-add-user-use-adduser-command/)
Now try logging in with the new user.

---

### Post by lastelement0 on 2008-06-02
this doesn't change anything. same thing happens with the new user.  i think i need to add root to a group which i forgot to do. what would i do to add root to a group via terminal?

---

### Post by lastelement0 on 2008-06-02
hey all i just recently tried to get USB access in my virtualbox xp guest and after following this tutorial ([http://forum.notebookreview.com/showthread.php?t=242936)and](http://forum.notebookreview.com/showthread.php?t=242936)and) reboot i was unable to login. i commented all the changes i made and was able to get back in. however i still dont have usb support.  any help would be great.

this is just my copy and pasted help request i sent on IRC just easier to do this than type it all over

---

### Post by shifty_powers on 2008-06-02
[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

worked perfectly for me to get usb support, and i don't even have a dell ;)

---

