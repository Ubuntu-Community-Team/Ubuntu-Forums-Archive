---
title: "Password from keyring in shell script"
date: 2009-03-04
forum: Programming Talk
---

### Post by inzpektor on 2009-03-04
In a nutshell:  I'd like to retrieve a password from the keyring (~/.gnome2/keyring/*) within a shell-script.

[SIZE="5"]The Situation[/SIZE]
I have a program that needs to authenticate to a server.  The password that this program needs is force-changed every month, and is already used in Evolution - why it is always updated to the latest password in the keyring.

The program that needs this password reads it from a credentials-file upon startup, and I would like to make a wrapper-shell-script for this program that always updates this credentials file to the latest password from the keyring.

If I look in Seahorse, I can see that the password is stored under a key that begins with "exchange://"

So, how do I get the password for that key in the keyring from within a shell-script?

**EDIT: I forgot to state that I'll be running this script from Gnome, so it's ok that the dialog box pops up asking whether I'd like to grant access from the script to the keyring-entry.  In fact, that's how I'd like it to be, but I just don't know the command for querying the keyring using this functionality.**

---

### Post by albandy on 2009-03-04
I'm in the same situation, but I received no answer.

If is same password as the login password you can retrieve it using pam_script 
[http://linux.bononline.nl/linux/pamscript/01/build.html](http://linux.bononline.nl/linux/pamscript/01/build.html)

---

### Post by inzpektor on 2009-03-04
> **albandy said:**
> If is same password as the login password you can retrieve it using pam_script

Thanks, that might be a last resort solution.  The login password is not the same because I turned off pam_winbind authentication (using Likewise) because it's very buggy and screws things up in Nautilus when accessing smb/cifs "shares".  (But otherwise yes, it's my Active Directory password that I'm trying to get from the keyring).

There must be a way of getting hold of a password from the keyring from within a shell-script.?.

---

### Post by albandy on 2009-03-04
I use likewise too, but not from the repositories, from the repositories I had the same problems, using the version from the likewise site works well.

Also if you can talk with the admins they can install the likewise manager to the AD server.

---

### Post by inzpektor on 2009-03-04
> **albandy said:**
> using the version from the likewise site works well.

Ok, thanks - I might give it a shot!

**But I would still like to know how to retrieve a password from the keyring from within a shell-script.  It must be possible.**

> **albandy said:**
> Also if you can talk with the admins they can install the likewise manager to the AD server.

If Likewise was produced by a certain company in Redmond, WA, they'd install it just like that.  Since it's not, they'd have to do all kinds of security-risk analyses and stuff, and it would take years (literally) before that could be installed.  Don't you just love it? :-)

---

### Post by inzpektor on 2009-03-04
I just found this site that contains the source for a program called gnome-keyring-query:

[http://www.gentoo-wiki.info/Store_SSH_passphrases_in_gnome-keyring](http://www.gentoo-wiki.info/Store_SSH_passphrases_in_gnome-keyring)

However, I tried to compile it, but it says that the package glib-2.0 could not be found, and that package is not in the Ubuntu repositories.

Anyway, the existence of such an experimental program suggests to me that the keyring-developers never thought of making it possible to get keyring-passwords from the command line - or deliberately made it impossible, perhaps for security-reasons?

Can that really be true?

---

### Post by inzpektor on 2009-03-04
I also found this site that contains a small program to access keyring-passwords from shell:

[http://blogs.sun.com/chrisg/entry/ssh_add_meets_gnome_keyring](http://blogs.sun.com/chrisg/entry/ssh_add_meets_gnome_keyring)

It seems to be exactly what I'm looking for, but again I can't compile the program.  I'm a Java-developer and I don't know the first thing about C :-)

But obviously, since people are creating these programs, it must be because this functionality does not exist in the official gnome-keyring package.

Can somebody get this program to compile?

---

### Post by albandy on 2009-03-04
gcc `pkg-config --cflags --libs gnome-keyring-1 glib-2.0` -o gnome-keyring-query gnome-keyring-query.c

but dont work well, you can only retrieve the passwords added with gnome-keyring-query

---

### Post by inzpektor on 2009-03-04
> **albandy said:**
> gcc `pkg-config --cflags --libs gnome-keyring-1 glib-2.0` -o gnome-keyring-query gnome-keyring-query.c

Yes, I tried that command, and that gave me:

```
Package gnome-keyring-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gnome-keyring-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gnome-keyring-1' found
Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
```

Plus a lot of errors.  But of course, if it can only access keys that have been inserted by this program anyway, it's to no use.

---

### Post by albandy on 2009-03-04
you need libglib2.0-dev  libgnome-keyring-dev

---

### Post by inzpektor on 2009-03-04
> **albandy said:**
> you need libglib2.0-dev  libgnome-keyring-dev

Ahh, yes - now it compiles.  And it works, but only for keys that have been inserted into the keyring from this program, as you stated.

I get the feeling that we're getting awfully close to a solution now.  How can we get this program to query password-keys that have not been inserted by the program itself?

---

### Post by albandy on 2009-03-04
we need a way to indicate seahorse that gnome-keyring-query can use the passwords

---

### Post by inzpektor on 2009-03-04
> **albandy said:**
> we need a way to indicate seahorse that gnome-keyring-query can use the passwords

Well, the gnome-keyring API must support adding a trusted application to the list of applications that can read a key, cause that's exactly what the other programs do.

For instance, the gnome-panel (in fact, it's the gnome-panel on behalf of the Clock-app) asks for access to the evolution calendar password when you click on Clock. :-)

You can also see in seahorse that seahorse adds itself to the list of trusted apps.

I tried, just for the fun of it, to revoke read-, write-, and delete-rights from gnome-keyring-query on a key (in seahorse) to see what happens when the program then tries to get the key.  It then displays the dialog box "Allow application access to keyring?", which is good, but it should ofcourse also pop up if the application is not even in the list of trusted apps.

Any ideas/clues?

---

### Post by inzpektor on 2009-03-04
I looked into the API-docs for gnome-keyring and found this method:

[http://library.gnome.org/devel/gnome-keyring/stable/gnome-keyring-gnome-keyring-acl.html#gnome-keyring-application-ref-new](http://library.gnome.org/devel/gnome-keyring/stable/gnome-keyring-gnome-keyring-acl.html#gnome-keyring-application-ref-new)

Again, I'm no good at developing C, but it seems like this (gnome-keyring-application-ref-new) is the method to call if the lookup throws an Exception/returns null/etc in order to have the caller-program (gnome-keyring-query) added to the list of trusted apps for this key.

---

### Post by albandy on 2009-03-04
I'll read it.

---

### Post by inzpektor on 2009-03-09
[SIZE="5"]We are not alone![/SIZE]

Found this bugreport on gnome.org: [http://bugzilla.gnome.org/show_bug.cgi?id=561582](http://bugzilla.gnome.org/show_bug.cgi?id=561582)

Stef Walter points out (Comment #2) that for it to work properly they need some architecture changes in gnome-keyring with regard to ACLs.  That's exactly what I suspected, that it uses the call-stack to identify which program is requesting access to a key.  So, if a generic query-program calls on behalf of a shell-script, then it'll always be the query-program which is identified as the caller, which is probably not what we or anybody else want.

Oh well, at least somebody's working on it.

OBTW, he also mentions that gnome-keyring got a query tool in 2.24 which is really strange cause I got 2.24.1 and I don't see any query tool.?.

---

### Post by albandy on 2009-03-09
a pam_module for evolution could work too, I'll try to find something

---

### Post by Kamil Páral on 2009-09-27
I have created a small project for accessing gnome-keyring from Python. It can be used as a Python module or from shell:
[https://launchpad.net/gkeyring](https://launchpad.net/gkeyring)

---

### Post by albandy on 2009-09-30
> **Kamil Páral said:**
> I have created a small project for accessing gnome-keyring from Python. It can be used as a Python module or from shell:
[https://launchpad.net/gkeyring](https://launchpad.net/gkeyring)

Thanks a lot, it does what I need.

---

### Post by led_belly on 2009-11-12
Hello!

Regarding the gkeyring.py script... is there a way to run this w/ sudo or su -c? I tried the following but received an error (the second attempt just adds a '-' before username 'greywood' at the end):

```
root@blake:~# su -c "/prime/scripts/gkeyring.py -k login -p user=root,type=password --output secret" greywood
GNOME keyring is not available!
root@blake:~# su -c "/prime/scripts/gkeyring.py -k login -p user=root,type=password --output secret" - greywood
/var/lib/python-support/python2.6/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
GNOME keyring is not available!

```

Any suggestions? thanks!

---

### Post by Kamil Páral on 2009-11-13
I will reply to all questions regarding gkeyring in its own forum:
[https://answers.launchpad.net/gkeyring](https://answers.launchpad.net/gkeyring)

---

### Post by led_belly on 2009-11-13
> **Kamil Páral said:**
> I will reply to all questions regarding gkeyring in its own forum:
[https://answers.launchpad.net/gkeyring](https://answers.launchpad.net/gkeyring)

[https://answers.launchpad.net/gkeyring/+question/90029](https://answers.launchpad.net/gkeyring/+question/90029)

done.

---

