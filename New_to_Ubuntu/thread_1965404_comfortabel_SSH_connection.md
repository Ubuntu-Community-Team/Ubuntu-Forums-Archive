---
title: "comfortabel SSH connection"
date: 2012-04-25
forum: New to Ubuntu
---

### Post by cheatos on 2012-04-25
Hi,
is there an easier way of using ssh than with the terminal?
Like inside of the filemanager (pcmanfm in my case) so that you can see the folder hierarchy?
Because its pretty annoying to always cd through directories and then use ls to display the next instance...

Is there a program specifically designed to do that, or maybe even a plugin for the filemanager?

Thanks for your help!

---

### Post by cmont899 on 2012-04-25
You can use nautilus for ssh/scp,

In nautilus navigate to File -->"Connect To Server..." and select ssh under the "Type" dropdown.

Also, from the terminal you can use the command "tree" to see the folder hierarchy.

---

### Post by cheatos on 2012-04-25
oh thanks, didn't know of the tree command, I suppose this works in a local filesystem as well?
And I'll give nautilus a try.

---

### Post by MG&amp;TL on 2012-04-25
[LEFT]You can also _[forward X]("http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html") _, or use one of the Remote Desktop solutions.
[/LEFT]

---

### Post by cheatos on 2012-04-25
Ok, so I've tried using the tree command now on the remote machine i would like to access, but it said it has to be installed first. As I am not the owner of that machine and don't have root privileges, I'll try it with nautilus soon.
What exactly is that forward X going to do?
And wouldn't remote desktop stuff need some software on the other side too?

---

### Post by MG&amp;TL on 2012-04-25
Unfortunately, it would indeed need software on the other side, or at least root access. Short of contacting the system administrator, I think a shell or nautilus may be the best idea.

X.org is the server that manages windows and graphical environments-by default, ssh does not forward X.org, but you can set it up to do just that. Essentially gives you a graphical environment, while encrypted from one machine to the other.

---

