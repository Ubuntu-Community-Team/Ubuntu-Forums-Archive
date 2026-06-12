---
title: "advanced lightdm help"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by rburkartjo on 2011-10-14
i had this problem when testing 11.10. when i set my login window to lightdm i cant log in. however i can log my daughter in no problem. have repeatedly tried to run sudo dpkg-reconfigure gdm and ditto lightdm. i have even removed lightdm which also uninstalled the ubuntu desktop and reinstall and this doesnot do it. note if i set to gdm works fine. must of been something i did when testing but have no idea how to fix. any ideas. not a big thing but work like to fix.

---

### Post by rburkartjo on 2011-10-14
also just trying reinstalling both lightdm and lightdm-gtk-greeter from spm. no luck didnt fix issue

---

### Post by rburkartjo on 2011-10-15
i noted some others also had this problem while testing 11.10. going to give a bump to this thread couple times a week so it doesnt get buried.
got to be an answer. it might have somthing to do with permission in lightdm but cant figure out why gdm still works fine.

---

### Post by rburkartjo on 2011-10-16
here is how i fixed.  i apparently had a corrupt file
.Xauthority backup in my home folder. so i deleted. open a virtual termnal and ran sudo dpkg-reconfigure gdm set it to lightdm and rebooted.

---

