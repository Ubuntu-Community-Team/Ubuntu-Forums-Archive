---
title: "Launching DB (.odb) File from Panel?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by jamere on 2008-05-26
Hi, 
Am having trouble getting my small DB to launch from the Panel. I think permissions for the file are OK. I can double-click on the file in my home directory and it launches OK, but launching from the Panel, it doesn't appear to even try to launch...any ideas?

Thanks much!
Jim M

---

### Post by drs305 on 2008-05-26
This is what my panel shortcut has in the launcher command window, and it works fine:
```
ooffice /home/username/docs/filename.odb
```

---

### Post by jamere on 2008-05-26
drs305,

Thanks for the quick reply... the "ooffice" did the trick in the command line! Not sure where this came from for your launcher. I manually created my launcher and just pointed to my file using the "browse" button for the command line. The "ooffice" was not generated in my command line. Have any idea where the "ooffice" came from in your command line? Just curious. I just know enough to be dangerous when it comes to Openoffice DB's.

Regardless...thanks again for your reply...it worked!

---

### Post by drs305 on 2008-05-26
> **jamere said:**
> drs305,

Have any idea where the "ooffice" came from in your command line? Just curious. I just know enough to be dangerous when it comes to Openoffice DB's.

Regardless...thanks again for your reply...it worked!

I just made it up. I created the shortcut from the custom launcher option. It was a while ago and I'm sure I experimented a bit before I came upon the solution. Many linux commands operate the same way. Actually, if you aren't sure of the command to launch an app, you might find it in the /usr/bin folder. Look around and you may be able to guess which one is for the program you want. The names in the /usr/bin folder are the actual command names used to start the program.

Glad it worked for you!

(You can mark this solved by clicking on the thread tools at the upper right of the original post.)

---

