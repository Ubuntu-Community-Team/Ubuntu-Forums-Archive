---
title: "Unity dash crashes when deleting whatever was written using backspace"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ValdrGalga on 2011-09-12
Well, this is a bug I'm having. I reported it in Launchpad but was warned that I should update the packages. I did apt-get update and upgrade and I'm, apparently, up to date, but I keep having this bug, so I decided to share it here.

The topic says it all. I open the dash, I write something in the search field, I delete it using backspace (all of the characters written)-> crash. Well, better said, not a crash, the dash reboots itself.

And now that I'm writing, I'm going to list another couple of bugs:
· Skype and Wi-Fi passwords are not stored, I have to type them every time I switch the laptop on.
· Ibus-m17n translit table has problems when writing a character and pressing space afterwards (reported in the ibus project website)

Thank you!

---

### Post by cariboo on 2011-09-12
You have to enter your skype and wifi passwords, because you are using auto-login, this has been a common problem for the last several releases. Just create a blank gnome-keyring password, and the problem should go away.

---

### Post by ValdrGalga on 2011-09-13
Thank you very much, I appreciate your help.

It looks like the password and dash things have been fixed with the last update I made. Not the ibus thing, though, but well, I reported it in the development website.

Thanks!

---

