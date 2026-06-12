---
title: "Web Admin - Become Root"
date: 2008-09-02
forum: Programming Talk
---

### Post by brentoboy on 2008-09-02
So, I have started a project for small businesses that lets them have a nice little Ubuntu server running a website I am writing that lets them use a web interface for their business contacts and to-do list, as well as a limited amount of bookkeeping.  All in good time.

It is also going to be a simple samba file server, and I want to be able to let them add and remove samba users, and manage passwords and group membership from the website.  Which means I really need to also be able to add linux users (becuase samba users are mapped to linux users in the end).

The problem I am having is that I must choose between running the web server as root (in this case apache2 + django via mod_python if anyone cares) or as some other user with root powers, or I need to be able to accept a password from a web user and use it to "sudo" myself into temporary root privileges while I modify the right files to add users.  I dont want to run apache as an all powerful user (that would be asking for trouble).

I would be happy to get samples or help in either php or django(python) becuase I know enough of both to find a way to convert to the other.  The classic sample of this is SWAT, but it appears to be written in C and I don't see anyplace where it is elevates its privileges, and I am starting to think it might expect to run with full privileges in order to add and modify users, but I haven't confirmed that.

If I can get this sorted out, I intend to ultimately have a nice little small business control panel that lets them completely administer the essentials of a server via a simple web panel.

Does anyone know how I can elevate to root for a single page submit?  If so, are there libs I could link to that let me add and edit users and groups without modifying the password file directly?  Or, can anyone tell me of an existing project that is able to elevate its privileges long enough to add a user from a webpage? -- I  can dig in and see how if I could get an example.

---

### Post by mssever on 2008-09-02
Read man sudoers. You can grant limited sudo priviledges to the web server's user.

---

### Post by brentoboy on 2008-09-02
Sure, but the only way to have sudo help me is to either run sudo, or gksu or something like that.

I either have to give my apache user lots of privileges, or I have to give it sudo privledges.  and if I give it lots of privileges, then if it is compromised... thats bad.  But, if I give it sudo rights, how to effectivly say "sudo" before I start trying to modify system settings?

Is there a sudo api?

---

### Post by mssever on 2008-09-02
> **brentoboy said:**
> But, if I give it sudo rights, how to effectivly say "sudo" before I start trying to modify system settings?
In Python: ```
os.system('sudo some-program')
```I'd recommend writing a script to handle all the privileged stuff, and only allowing the webserver user to use sudo on that one script. That script could then call out to other programs as appropriate.

---

### Post by brentoboy on 2008-09-02
yes, but in python, when I os.system('sudo some-program') it should ask for a password.  even if I pipe the output of some-program to a separate file, so I can parse it and look for errors, it still only pipes the output of that program, not the sudo password request.  when I os.system('sudo some-program') how do I pass the password?  (I hope simply saying sudo from within a python script run by a user who has sudo privileges doesn't just sodo something - that would open up all kinds of security issues in my mind.

Do you see the problem here?  I need the authentication from sudo to be routed back to my application so I can provide the given password and potentially give feedback to the user requesting that they fix it if it didn't work.  I need something like gksu where instead of asking for the password from the command prompt, it asks for it on a graphical prompt, except, I need to ask for it across a webpage.  I need "ajaxsudo" - I can handle the ajax part, I just dont see a way to supply the password to the system running the web service before I start modifying system files.

As a side note, is os.system("sudo adduser joe") honestly the best way to create a user from a python script?  Is there not some lib out there that lets me call a function that does it all and then returns me status codes?  Just curious.  But that isn't my primary concern, as I could do it either way if I must.  I just don't see any way of getting

---

### Post by mssever on 2008-09-02
You don't need to worry about the sudo password. That wouldn't work anyway, since www-data doesn't have a password. Just configure sudo to not require a password.

Basically, what I'm suggesting is this:

[LIST=1]
[*]Write a script that will run as root and either carry out operations that require root access itself or call other programs to do that work. You can include appropriate validation in this script to effectively limit what it can do to the bare minimum required.
[*]Edit the sudoers file to allow www-data (or whatever user the server is running as) to run only the script you wrote in step 1 as root. Configure sudo not to ask for a password in this case. See ```
man sudoers
```for details.
[*]Use os.system or whatever to run your script with sudo, and pass it whatever data may be necessary.
[/LIST]
By the way, if there's a sudo API, I don't know about it. AFAIK, you have to start a separate process to gain root privileges.

---

### Post by brentoboy on 2008-09-02
that sounds like a reasonable approach.  I'll play with that and post up the results after I get it working (or hit rock bottom) whichever comes first. I'll let you know if that does the trick.

---

### Post by forger on 2008-09-02
I also found some alternatives to sudo you might be interested:
[SIZE="1"]> Package: op
Description: sudo like controlled privilege escalation
 The op tool provides a flexible means for system administrators
 to grant access to certain root operations without having to
 give them full superuser privileges. Different sets of users may
 access different operations, and the security-related aspects of
 each operation can be carefully controlled.
 .
 The main attraction of op over sudo is the use of mnemonics
 rather than true commands. This allows an administrator to
 present users with more intuitive commands.
 .
 Other available features are:
 .
  - fine-grained per-command control
  - a really short name
  - host-based access control
  - command expiration
  - variable expansion
  - multi-line arguments
 .
  Homepage: [http://swapoff.org/wiki/op](http://swapoff.org/wiki/op)


Package: chiark-really
Description: really - a tool for gaining privilege (simple, realistic sudo)
 really is a program that allows certain users to become whatever user
 they like on request.  It is a bit like sudo in that respect.
 However, really is simpler than sudo, and doesn't give the system
 administrator any false security promises.  So really is less of a
 general security risk to the system.
 .
 Unlike sudo it does not pretend that the called account can be any
 more secure than the calling account. so there is never a need for a
 password.  If you wanted to restrict which commands and functions the
 called user can perform, use userv, not really or sudo.
 .
 Also unlike sudo, really only works if the calling user is supposed
 to be equivalent to root.  But, really can also be used by
 root-equivalent users to become any user, not just root; in this way
 it can be a replacement for certain uses of su.[/SIZE]

---

### Post by brentoboy on 2008-09-02
I'm happy with sudo, simply becuase it is already installed and supported.  I was hoping to find a lib or an object that lets me switch users for a moment.  But that doesnt seem likely.

I also found libsudo at sourceforge, but again, I would have to spawn another process and let it do its thing rather than do the dirty work inside the script running in the webserver.

Still open to ideas, but I have enough to chew on for now.

---

### Post by forger on 2008-09-03
You can execute a script as another user:
```

echo 'echo $USER $HOME' > /tmp/moo
sudo -u myuser -i /tmp/moo

```
or a command:
```
su -c "echo $USER $HOME" myuser
```

(If you're already logged in as root, you don't have to type the password)

---

