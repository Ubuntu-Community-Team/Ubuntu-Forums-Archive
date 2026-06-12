---
title: "ssh in and run command in pre-existing session?"
date: 2013-05-12
forum: Programming Talk
---

### Post by Merrattic on 2013-05-12
I think this is what I need to do in order to run my script! This is not a gnu-screen question, more a ssh session question (I think?)

Remote machine is a cli only digital picture frame. I use a script on start up to login automatically and then run a script which starts a gnu-screen, inside of which runs the image display and a clock (split gnu-screen ;))

I can ssh in as the same user and kill the gnu-screen session (screen -x) and the running script, but if I try to run the script again, it doesn't work because I am on the wrong screen/display/tty in my ssh session.

How do I run the script as the pre-existing logged in user (can be the same as the ssh'd user) so that the gnu-screen session appears on the screen/display/tty of the remote machine?

---

### Post by Lars Noodén on 2013-05-12
*screen -x* will only attach to an existing screen session.   If there is no session to attach to, it will fail.  What you could try in that case would be *screen -d -RR* which will detach an existing session if there is one but create a new session if none exists.  Would that do it for you?

---

### Post by Merrattic on 2013-05-12
Thanks

My issue is starting gnu-screen in a different session (login) to the one I am ssh-ing in with.

When PC boots up it logs in automatically to user A then runs a script to start gnu-screen with a specific screenrc setup.

If I need to restart all this remotely (without rebooting the PC) I can ssh in as user A again (or user B if needed) kill gnu-screen and the script.

But need to restart the script and gnu-screen I cannot start the script in the correct session/tty/(physical) terminal.

The script inside the gnu-screenrc uses mplayer and the frame buffer, so it needs the physical display/terminal to run.

Hope this makes sense?

---

### Post by Lars Noodén on 2013-05-12
So you're logging in as User A, but would like screen (and the script) to run as User B?

---

### Post by Merrattic on 2013-05-12
I think I have introduced too many "variables"!

At the remote machine if I run the **tty** command I get **/dev/tty1**.

If I ssh into the remote machine and run **tty** I get **/dev/pts/1**

So if I then run the command that calls up gnu-screen, it tries to run on **/dev/pts/1** instead of **/dev/tty1**, when it needs to run on **/dev/tty1** to access the frame buffer.

I know stuff like:
```
 ls > /dev/tty1
``` works but this doesn't seem to help in my case, as it sends the output of ls from the originating terminal ?

Found this though:
[http://www.humbug.in/2010/utility-to-send-commands-or-data-to-other-terminals-ttypts/#.UY-lONdCMmk](http://www.humbug.in/2010/utility-to-send-commands-or-data-to-other-terminals-ttypts/#.UY-lONdCMmk)

which might be a solution?

---

### Post by Lars Noodén on 2013-05-12
According to the manual page for ssh, "Multiple -t options force tty allocation, even if ssh has no local tty."  Have you tried that yet?  It makes no difference on the machines I've tried it on, but it might work for you.

---

### Post by Merrattic on 2013-05-12
Found the solution!!

Needed to use **openvt** with sudo.

I can stop the existing running gnu-screen with:

```
screen -X quit
```

then restart with:

```
sudo openvt -f -c 1 ./myscript.sh
```

given I know that I want to run on tty1 = 1

:D

This command is also needed in order to restart the script from a crontab job

Thanks for your help and encouragement Laars

---

