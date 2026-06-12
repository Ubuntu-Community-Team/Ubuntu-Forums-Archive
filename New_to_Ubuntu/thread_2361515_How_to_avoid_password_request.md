---
title: "How to avoid password request?"
date: 2017-05-17
forum: New to Ubuntu
---

### Post by ermjunor on 2017-05-17
Is there a way to tell Ubuntu 16.04 not to ask me for the password every time I want to do something more or less important? I work at home, not at NASA or similar ... Thanks...

---

### Post by TheFu on 2017-05-17
Something "More or less"?  Please explain, exactly, what you mean by this.  It isn't clear, since there are multiple places where different passwords are necessary.

---

### Post by ajgreeny on 2017-05-17
Your request is, and has been, repeatedly made over many years by new users of Ubuntu, and I suspect all other Linux distros and I am assumiong you are also a new Linux user.

How do you use your computer; how often do you have to give your password?
It is only required if you are attempting to do something that affects the operating system itself such as editing root-owned configuration files, or more commonly just updating the OS.  There are many users who might go a whole week without needing to use their password other than logging in, but if that is what you want to avoid you can simply use autologin.

A password is there for your own security and to make sure you do not do something silly without realising it might be dangerous to the OS

I suggest you simply learn to live with the request, or if you have a long series of terminal commands that all have to be run as administrator and therefore need a password for each, make the first command **sudo -i** to get a root terminal.  
Other than the applications that obviously need root permissions such as the update-manager or synaptic, you should try not to use GUI applications with root permissions.

---

### Post by HermanAB on 2017-05-17
It is not just for your security.  If that was the case, other's would not care.  You are free to mess up your own machine just as badly as you would like to.

Strong security is for everybody else's benefit also.  It helps to ensure that your machine doesn't become a spam spewing robot, making life unpleasant for everyone else on the planet.

The present MS Windows ransomware nonsense is a good example of how people with badly secured machines can cause trouble for everybody else.

We have only one planet and everybody is connected to one network.  Therefore everyone should act responsibly.  We depend on each other.

---

### Post by leunam12 on 2017-05-17
Do what I did: buy a fingerprint reader.

---

### Post by TheFu on 2017-05-17
> **leunam12 said:**
> Do what I did: buy a fingerprint reader.

[http://www.networkworld.com/article/2293129/data-center/120606-10-ways-to-beat-fingerprint-biometrics.html](http://www.networkworld.com/article/2293129/data-center/120606-10-ways-to-beat-fingerprint-biometrics.html)

Convenience is seldom useful for real security.  Plus whenever some part of a body is used to secure something, there is always the possibility that someone else will **take** that part of the body to be used later.

I've seen so-called secure data centers using fingerprint readers with temperature sensors.  They hoped to prevent some of the more common attacks with gummy, cellophane, by forcing heat from the finger.  Problem was that data centers are netoeriously cold and if you spend more than a few minutes inside, cold fingers are the by-product.  We were routinely trapped inside.  No problem, there was a side door that everyone used for their smoke breaks. It was usually propped open so anyone could get in that way.  After all, the fingerprint reader records needed to match in/out.  If you came in through the front door, then you'd need to leave that way (at least after your shift) that same way.  It was easier to just use the side door.

Using just a fingerprint isn't a good idea.  Using both a fingerprint AND a 13+ character passphrase would be smart.  12 characters can be brute forced in under 24 hrs these days (actually for a few years now).  I use a Yubikey + a 16+ character passphrase for my login to physical systems.  For networked systems, there is U2F. Devices that support that protocol are pretty cheap - $10-ish.  Google, dropbox, lastpass, github and probably 50+ other huge cloudy-services support it too.  It is very convenient to use - just a physical touch is necessary - nothing special.  [https://www.howtogeek.com/232314/u2f-explained-how-google-microsoft-and-others-are-creating-universal-two-factor-authentication-tokens/](https://www.howtogeek.com/232314/u2f-explained-how-google-microsoft-and-others-are-creating-universal-two-factor-authentication-tokens/) - not good enough for local access, but anything over a network, it is excellent security.

---

### Post by ian-weisser on 2017-05-17
Ach, so THAT's why photos of my retinas are so popular!

---

### Post by TheFu on 2017-05-17
> **ian-weisser said:**
> Ach, so THAT's why photos of my retinas are so popular!

A photo is better than the other alternative! I've read somewhere that retina scanners are harmful to eyesight if used all the time. Don't remember where.

---

### Post by HermanAB on 2017-05-18
The trouble with biometrics is that you leave your prints and DNA everywhere you go.

A better idea is an old fashioned one - a USB memory stick with a key in it.

Anyhoo, after a while, one can type a password blindfolded, so it isn't really much of a problem.

---

### Post by mastablasta on 2017-05-18
> **ermjunor said:**
> Is there a way to tell Ubuntu 16.04 not to ask me for the password every time I want to do something more or less important? I work at home, not at NASA or similar ... Thanks...

in other words - when malware wants to run, it needs to first enter your password. no password, no go.

disable the password and you are wide open.

---

### Post by HermanAB on 2017-05-18
...and please don't use a kewl 4 character password.  A proper password is at least 12 characters long.

---

### Post by Topsiho on 2017-05-19
Linux is very safe to use. We, who love using Linux, are quite happy with that, and want to keep it that way.

A real threat is that new users, coming from another OS (welcome, welcome) may bring their bad habits with them to Linux, and may so endanger **our** computers too. Via their compromised computers our Linux machines may be attacked too, as has happened in that other OS. Now it's very difficult to attack our Linux machines, but no one (I hope so) is saying that it is impossible.

One of the ways to keep our Linux machines safe is using root passwords (very strong passwords, that can't be guessed) for any system setting. Using these passwords when installing any program. As most viruses and other malware don't know them, they can not install. Only you can do that on your computer, and please don't do that.

Do that to keep yourself safe, and also to keep US safe.

You can use Linux (Ubuntu) for free, and that is great. It's more than great, it is super. Please acknowledge that, and keep your own computer as safe as possible. Using root passwords where this is necessary, and keeping your systems up to date, if possible on a daily basis (updating Ubuntu is a real pleasure, after the nightmares that the other OS once (long ago :) )  gave me)

Thank you! And again: welcome...

Topsiho

---

### Post by TheFu on 2017-05-19
Don't enable the root login on any Linux.  That solves many security issues.  Ubuntu works that way OUT-OF-THE-BOX.  Having a root login just isn't needed on any Unix-OS.

---

### Post by The Cog on 2017-05-19
After all the lectures, I hope this helps:

Try to mentally separate the two roles of:
* Using the system to do your day-to-day work, and 
* Administering the system, such as system updates, installing software.
It takes a while to come to appreciate the difference if you come from other systems.
Once the PC is reasonably set up, you should only have to do sysadmin work every few days. All your day-to-day stuff should be inside your home directory where you don't have to enter your password again.

I always open a terminal and use the command **sudo -i** to gain a root prompt. I can leave this terminal open for as long as I want, and enter as many commands as I want without having to re-enter a password. Then close the prompt when the admin task is done.

---

### Post by flocculant on 2017-05-19
lots of answers - not one has actually responded to the question.

The answer is actually a question - why do YOU think you can run your system with no password? I suggest that you think Windows is great ...

---

### Post by flocculant on 2017-05-19
> **ermjunor said:**
> Is there a way to tell Ubuntu 16.04 not to ask me for the password every time I want to do something more or less important? I work at home, not at NASA or similar ... Thanks...

Of course.

If you have to ask ...

---

### Post by mastablasta on 2017-05-22
> **flocculant said:**
> lots of answers - not one has actually responded to the question.


that would be irresponsible to the users and others that might later be affected by such decision (removing OS security layers).

---

### Post by again? on 2017-05-22
If typing your password is a chore you can add your password to your login keyring and then access it through a simple python script once logged in.
Bind an xdotool command to a mouse button, mouse gesture or keyboard shortcut.
```
#! /usr/bin/env python

# this is inspired by http://blog.schmichael.com/2008/10/30/listing-all-passwords-stored-in-gnome-keyring/

# place script in ~/bin and check $PATH
# Use seahorse to save your admin password to your login keyring as a "Stored Password"
# Use a UniqueWord for the description.
# gnome-keyring-dumper | awk '/UniqueWord/{print $NF}'
# Use with easystroke or bind keyboard shortcut: xdotool key --delay 50 $(gnome-keyring-dumper | awk '/UniqueWord/{print $NF}' | sed 's/./& /g') Return
 
import pygtk
pygtk.require('2.0')
import gtk # sets app name
import gnomekeyring
 
def hack():
    for keyring in gnomekeyring.list_keyring_names_sync():
        for id in gnomekeyring.list_item_ids_sync(keyring):
            item = gnomekeyring.item_get_info_sync(keyring, id)
            attr = gnomekeyring.item_get_attributes_sync(keyring, id)
            if attr and attr.has_key('username_value'):
                print '[%s] %s: %s = %s' % (
                    keyring,
                    item.get_display_name(),
                    attr['username_value'],
                    item.get_secret()
                )
            else:
                print '[%s] %s = %s' % (
                    keyring,
                    item.get_display_name(),
                    item.get_secret()
            )
        else:
            if len(gnomekeyring.list_item_ids_sync(keyring)) == 0:
                print '[%s] --empty--' % keyring
 
if __name__ == '__main__':
    hack()
```

---

