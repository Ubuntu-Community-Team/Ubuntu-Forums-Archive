---
title: "Is it possible to disable command line terminal in clients?"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by dynastywarrior on 2008-10-15
hello everybody.... can anyone pls help me on how i can disable the command line terminal in client pc's.

i am planning to network around 20 client pc's with 1 server all running ubuntu in them...

i don't want anybody tinkering thru the client pc's command terminal with my set-up...

---

### Post by Pro-reason on 2008-10-16
I think what you're talking about is enabling Kiosk mode, although I have never tried it myself.

The command line is not the only thing to disable.  They can also tinker with KDE System Settings, or GNOME Control Centre.

---

### Post by Keen101 on 2008-10-16
Applications->Accessories->Alacarte Menu Editor

you can remove the shortcut to the terminal...

---

### Post by Pro-reason on 2008-10-16
> **Keen101 said:**
> Applications->Accessories->Alacarte Menu Editor

you can remove the shortcut to the terminal...

As I said before, that is hardly a solution.  What is to stop them just running Alacarte again to restore it?  What is stopping them pressing Alt-F2 for the run dialogue?  What is stopping them going to TTY1 with Ctrl-Alt-F1?

This isn't about the terminal.  It's about restricting a user's access down to a few pre-approved apps.

---

### Post by pak33m on 2008-10-16
Maybe you could go to System -> Administration -> Users and Groups and edit the User Permissions and not provide a shell in Advanced for each user.  Or put your users in a Group and limit the permissions that way.

Just a few cents :)

---

### Post by dynastywarrior on 2008-10-16
> **Pro-reason said:**
> I think what you're talking about is enabling Kiosk mode, although I have never tried it myself.

The command line is not the only thing to disable.  They can also tinker with KDE System Settings, or GNOME Control Centre.

so if i enable **kiosk** mode, all those sensitive programs that you mentioned can't be accessed anymore?

or is there a better way of securing our ubuntu system from within?

is there any tutorial regarding limiting user permissions in ubuntu?

thank you all guys for your replies....**this is what makes the** **Ubuntu Community great !!!**

---

### Post by Pro-reason on 2008-10-16
Well, first and foremost, you ought to make sure that the user in question is not in the “admin” group, which allows it to run programs as root with “sudo”.

Beyond that, I advise you to google for tutorials on setting up Ubuntu to function as a cybercafé-style kiosk.  I've never done it myself.

---

### Post by mjwhitfield on 2008-10-16
There was a really good post from a guy who set up Ubuntu in is library and disabled all sorts to make it secure, lemme find the post........

[http://ubuntuforums.org/showthread.php?p=4404000#post4404000](http://ubuntuforums.org/showthread.php?p=4404000#post4404000)

---

### Post by Kellemora on 2008-10-16
Hi DW

Head over to Edubuntu and read some of the documents over there.
I think you may find them quite helpful.
Thinclients only have access to what you allow them to via permissions.

It's still Ubuntu Server, just comes pre-set-up is all for classroom use.

I just started reading and trying Edubuntu myself so don't know enough about it yet, other than Nothing much works UNTIL you allow that workstation access to it.  You definitely cannot get to command line stuff at all as a client User.

TTUL
Gary

---

### Post by dynastywarrior on 2008-10-19
To all of you who made effort to help people in need like me...thanks!
You are all the reason that makes the **Ubuntu Community** great!

Special thanks to** mjwhitfield**, the link you gave is the answer to all my questions....

**Kellemora** thanks for that alternative...i would try edubuntu eventually....

**Pro_reason** thanks for continously providing ideas for a solution...

**LONG LIVE UBUNTU !!!!**

---

### Post by Paqman on 2008-10-19
Intrepid comes with a guest account, that has fairly limited priviledges. If you restrict them to that, there's not a lot they can do.

Otherwise, any account that lacks admin rights (which new accounts do by default) can't really make any changes to the system. They can't install software and have no sudo privileges, so can't affect anything outside their /home.

---

### Post by dynastywarrior on 2008-10-19
I hope so paqman...if that's the case with intrepid then we'll have a lot to look forward to with this new release!

Thanks man!

---

### Post by Pro-reason on 2008-10-19
> **Paqman said:**
> 
Otherwise, any account that lacks admin rights (which new accounts do by default) can't really make any changes to the system. They can't install software and have no sudo privileges, so can't affect anything outside their /home.

Yes, we've already covered that.  The point is that they can still mess up the home directory for the next user.

The solution is a program that re-creates a default home directory for that user account every time someone logs in.  I believe that the Intrepid guest account that you mentioned works somewhat like that.  Alternatively, you can lock things down, as we have been discussing.

---

### Post by dash86no on 2008-10-19
> **dynastywarrior said:**
> hello everybody.... can anyone pls help me on how i can disable the command line terminal in client pc's.

i am planning to network around 20 client pc's with 1 server all running ubuntu in them...

i don't want anybody tinkering thru the client pc's command terminal with my set-up...

I usually set the shell path to: /bin/false for clients who should now have access to a shell.

---

### Post by Paqman on 2008-10-19
> **Pro-reason said:**
> Yes, we've already covered that.  The point is that they can still mess up the home directory for the next user.


They'd really only be able to mess up their own home directory, as it's the only one they have write permissions on.

---

### Post by Pro-reason on 2008-10-19
> **Paqman said:**
> They'd really only be able to mess up their own home directory, as it's the only one they have write permissions on.

You're not listening.

---

### Post by dynastywarrior on 2008-10-22
> **Pro-reason said:**
> 
The solution is a program that re-creates a default home directory for that user account every time someone logs in.  I believe that the Intrepid guest account that you mentioned works somewhat like that.  Alternatively, you can lock things down, as we have been discussing.

Actually there's a program that can do this...every time you want to restore everything to its exact original state can be done with just a reboot.But it's a proprietary software and it doesn't come cheap. The name is*** Deep Freeze*** and it works well with Linux.

But if*** Intrepid*** can do all of these with a guess account then it'll be perfect!

Hey **dash86no** thanks for the tip man!!

---

### Post by Pro-reason on 2008-10-22
The annoying thing about the Intrepid guest account for us Kubuntu users is that, for the moment, it requires GDM, and we use KDM.

---

