---
title: "Can't logon to my Ubuntu user account"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by NicOTeen on 2012-06-16
From the startup page when your computer boots and asks you to enter your password, I'm unable to get into my account. My password is correct - when it's not, I still get the "wrong password" message in red letters. What happens when I enter my correct password is that the screen turns to a black screen with white letters for less than a second, and then I hear the alarm (sounds like drums or something) and then it kicks me back to the page that asks for my password.

I can't really make out what the white letters say - there's a lot of writing, but I tried to catch a few words, and there was something about a maximum amount of file descriptors, the word "peech" (possibly more before or after), and the first sentence was something about /etc/

Does anyone know how I can log back onto that account? Thanks!

---

### Post by MG&amp;TL on 2012-06-16
Okay, what happens when you press Ctrl-Alt-F1, then (try to) login there? (you won't be able to see your password). You can get back to the GUI by pressing Ctrl-Alt-F7.

---

### Post by NicOTeen on 2012-06-16
ctrl alt f1 doesn't do anything (while logged in as guest or at the startup login screen), but that may be because my F# buttons don't seem to do what others' do. What should that do? Are you trying to get the terminal up?

---

### Post by MG&amp;TL on 2012-06-16
> **NicOTeen said:**
> ctrl alt f1 doesn't do anything (while logged in as guest or at the startup login screen), but that may be because my F# buttons don't seem to do what others' do. What should that do? Are you trying to get the terminal up?

A login terminal, yes. I'm hoping that will give us some more information.

FWIW, Ctrl-Alt- F1-F6 gives you a fullscreen login terminal. I'm googling to see a manual way to get to that.

---

### Post by NicOTeen on 2012-06-16
Oh, control + alt + t is a terminal, not sure about a login terminal. I'll try to figure out why my keys are mapped strangely - I'm on a ThinkPad Edge, so the F buttons tend to do stuff for the sound or screen or videos.

---

### Post by MG&amp;TL on 2012-06-16
> **NicOTeen said:**
> Oh, control + alt + t is a terminal, not sure about a login terminal. I'll try to figure out why my keys are mapped strangely - I'm on a ThinkPad Edge, so the F buttons tend to do stuff for the sound or screen or videos.

Yup, Ctrl-Alt-T give you a  terminal emulator (windows with a terminal in them), usually gnome-terminal.

Ctrl-Alt-F# gives you a fullscreen terminal.

Wait, you say you can login as a guest? What about anybody else (other than you)?

---

### Post by NicOTeen on 2012-06-16
I was just able to create a 2nd account from the guest account (using my admin root pass) and login to that, so yeah. That seems to work, but I'd like to access my main account.

---

### Post by MG&amp;TL on 2012-06-16
> **NicOTeen said:**
> I was just able to create a 2nd account from the guest account (using my admin root pass) and login to that, so yeah. That seems to work, but I'd like to access my main account.

Ahah, found a way to get what I wanted. Login as a guest, open a terminal, then run:

```
sudo login
```

and type your login and password. And obviously post output. :)

---

### Post by SDX0 on 2012-06-16
Have you tried resetting your password and then logging in?  You can use "sudo passwd *[name of your account]*" to do so.

---

### Post by NicOTeen on 2012-06-16
Tried that, it got mad about sudo (here):

sudo: unable to change sudoers gid: Operation not permitted
sudo: setresuid() [0, 0, 0] -> [119, -1, -1]: Operation not permitted

---

### Post by MG&amp;TL on 2012-06-16
> **SDX0 said:**
> Have you tried resetting your password and then logging in?  I'm not sure it's possible to do this without access to either sudo or su, but if you do have an account with those permissions you can use "passwd* [name of account]*".

The OP could, but as unity-greeter is rejecting wrong passwords, but erroring on the right ones, I think that is a tad unlikely. Just sayin'. :)

---

### Post by steeldriver on 2012-06-16
one possible cause is if your ~/.Xauthority or ~/.ICEauthority file becomes root owned (sometimes this happens if you are messing with startx as root for example) - if you can log in to a real terminal like MG&TL describes you can just remove those files and try again  (or likewise from the recovery console as root - or possibly from your guest account using sudo rm /home/yourusername/.Xauthority)

---

### Post by SDX0 on 2012-06-16
> **MG&TL said:**
> The OP could, but as unity-greeter is rejecting wrong passwords, but erroring on the right ones, I think that is a tad unlikely. Just sayin'. :)
Ah.  I was under the impression it was saying "Wrong password" and then giving an error after two login attempts.  Apologies.

---

### Post by MG&amp;TL on 2012-06-16
> **NicOTeen said:**
> Tried that, it got mad about sudo (here):

sudo: unable to change sudoers gid: Operation not permitted
sudo: setresuid() [0, 0, 0] -> [119, -1, -1]: Operation not permitted

Okay, login as the other user you created, then use the command I gave ~6 posts back to try and login from the terminal.

Guest can't use sudo, it would appear. :)

---

### Post by NicOTeen on 2012-06-16
> **SDX0 said:**
> Have you tried resetting your password and then logging in?  You can use "sudo passwd *[name of your account]*" to do so.

I can't sudo, so that gave the same error as above.

Edit: i'm an idiot - just created another admin account to try this stuff.

---

### Post by NicOTeen on 2012-06-16
OK, I have a login terminal. i entered my real account name, then the pass for THAT account (not the one I'm currently on, but the one I had to enter to create this new admin account) and it says the pass is incorrect. Is that what I'm supposed to do at the dialog?

it says

my-book login: (cursor - enter my main acct name here)
Password: (enter my password here)

Login incorrect
my-book login: (again)

---

### Post by MG&amp;TL on 2012-06-16
> **NicOTeen said:**
> OK, I have a login terminal. i entered my real account name, then the pass for THAT account (not the one I'm currently on, but the one I had to enter to create this new admin account) and it says the pass is incorrect. Is that what I'm supposed to do at the dialog?

it says

my-book login: (cursor - enter my main acct name here)
Password: (enter my password here)

Login incorrect
my-book login: (again)

Nope, try and login as you normally would. So, if your login was "nicoteen" and your pass was "pass", you'd login with those. 

I just want to see what the login manager's hiding.

---

### Post by NicOTeen on 2012-06-16
> **MG&TL said:**
> Nope, try and login as you normally would. So, if your login was "nicoteen" and your pass was "pass", you'd login with those. 

I just want to see what the login manager's hiding.

Sorry, I'm confused about where the output should be - I opened a login  terminal on the temp admin account, then hit "switch users" which took  me back to the first screen and had the same problem at my original  account. Switching back to this admin account, there's  no new data in  the login terminal.

---

### Post by MG&amp;TL on 2012-06-16
> **NicOTeen said:**
> Sorry, I'm confused about where the output should be - I opened a login  terminal on the temp admin account, then hit "switch users" which took  me back to the first screen and had the same problem at my original  account. Switching back to this admin account, there's  no new data in  the login terminal.


Oh, sorry. Really bad at explaining stuff.

1. Log in as temp admin.

2. Open terminal, run:

```
sudo login
```

3. Login with your *normal* admin details in the terminal.

4. Paste output here.

---

### Post by NicOTeen on 2012-06-16
> **MG&TL said:**
> Oh, sorry. Really bad at explaining stuff.

1. Log in as temp admin.

2. Open terminal, run:

```
sudo login
```3. Login with your *normal* admin details in the terminal.

4. Paste output here.


OK, that's what I did before - entered my normal admin details at the login and password prompts. It gives me 

Login incorrect

Even though it will take that password for all the admin stuff (like creating new users).

Edit: but when you do that from the GUI login screen, it does not say that - it just goes black and comes back. It says that when I enter a wrong pass in the GUI, though.

Edit 2: It appears that my computer can't play sound anymore (?). This sucks. Never drink and sudo.

---

### Post by MG&amp;TL on 2012-06-16
> **NicOTeen said:**
> OK, that's what I did before - entered my normal admin details at the login and password prompts. It gives me 

Login incorrect

Even though it will take that password for all the admin stuff (like creating new users).

Edit: but when you do that from the GUI login screen, it does not say that - it just goes black and comes back. It says that when I enter a wrong pass in the GUI, though.

Edit 2: It appears that my computer can't play sound anymore (?). This sucks. Never drink and sudo.

...I guess you could try what SDX0 said. Sorry SDX0, seems you are right!

Don't know why it's doing that, really odd.

---

### Post by NicOTeen on 2012-06-16
Um. I tried restarting and now my computer is totally screwed.  It takes me to a boot menu and mu hard drive isn't listed as an option to boot from. I was deleting stuff related to privoxy. Guess I need to reinstall and start over.

---

### Post by MG&amp;TL on 2012-06-16
> **NicOTeen said:**
> Um. I tried restarting and now my computer is totally screwed.  It takes me to a boot menu and mu hard drive isn't listed as an option to boot from. I was deleting stuff related to privoxy. Guess I need to reinstall and start over.

Okay, well, sorry we couldn't get it fixed. Hope this install serves you better. :)

---

