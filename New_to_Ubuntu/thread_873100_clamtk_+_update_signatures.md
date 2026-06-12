---
title: "clamtk + update signatures"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-07-28
I am trying to update ClamTk signatures but it says that I must be root to install updates.

What should I do?

How do I tell it that I am root?

---

### Post by t0p on 2008-07-28
> **saskatchewan said:**
> I am trying to update ClamTk signatures but it says that I must be root to install updates.

What should I do?

How do I tell it that I am root?

Can't you do it by running the update with gksudo? (or sudo)

---

### Post by sydbat on 2008-07-28
```
sudo clamtk
```opens clam with root privalages. Also, you can ```
sudo freshclam
```In either circumstance, you will have to put in your password, although you will not see it as you type.

---

### Post by ozPATT on 2008-09-10
hello, I have also had the above problem, so thanks for the resolution. My question now though, is that every time I start the application, it says that my signatures are 212 days old, despite me having clicked on update signatures, and it then tells me that they are up to date.. 

any ideas how i can keep it updated every time i need to use it? Or even automatic updates? 

Thanks

Patrick

---

### Post by hyper_ch on 2008-09-10
do you even need clamtk?

---

### Post by ozPATT on 2008-09-10
well, I am a website developer, and someone has just come to me telling me that a file on a website I build is corrupt, and could be infecting people when they visit the site. So I have had to download it and then check it for viruses, but as I am using linux, i wasn't sure which virus scanner to use. So I just searched in the ad remove programs and found this one. 

so i do need to use some virus scanner...

---

### Post by hyper_ch on 2008-09-10
generally you don't need AV... however sometimes you need - like your case ;)

prepend the command to install the updates or run updates with "sudo" (do as superuser)

---

### Post by ozPATT on 2008-09-10
how do you mean? i launch it in the terminal using sudo, then when it opens, i do the updates... is there a way to update the sigs using the terminal?

---

### Post by hyper_ch on 2008-09-10
dunno, I don't use any av on linux.

---

